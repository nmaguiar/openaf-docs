---
layout: default
title: "Advanced: How to copy CLOBs between two databases"
parent: Guides
grand_parent: OpenAF docs
---

# How to copy CLOBs between two databases

Specially in Oracle is not very easy to get the CLOB field value from a source database and insert/update it on another CLOB field on a target database.

In OpenAF the _DB.q*_ and _DB.u*_ functions are "CLOB/BLOB" aware and will try to convert them to strings to make it seamless. But there is the _DB.*Lob*_ functions to handle them in particular.

The next example shows how to retrieve CLOB values from one database and inserting them on a temporary table on a target database:

````javascript
log("Connecting...");
 
var db1 = new DB("jdbc:oracle:thin:@//1.2.3.1:1521/SOURCE", "loginSOURCE", "passwordSOURCE");
var db2 = new DB("jdbc:oracle:thin:@//1.2.3.2:1521/TARGET", "loginTARGET", "passwordTARGET");
 
log("Retrieving data...")
 
var res = db1.q("select obj_uuid, obj_definition from objects_table");
 
log("#" + res.results.length + " records retrieved");
 
log("Copying data...");
db2.u("truncate table TEMP_TABLE"); // Assuming you have a TEMP_TABLE already created on db2
 
var c = 0;
for(i in res.results) {
   var line = res.results[i];
   c += db2.uLobs("insert into TEMP_TABLE (OBJ_UUID, OBJ_DEFINITION) values (:1, :2)", [ line.OBJ_UUID, line.OBJ_DEFINITION ]);
}
 
log("#" + c + " records copied.");
 
db2.commit();
db2.close();
db1.close();
 
log("Done");
````

The result will be similar to:

````bash
Thu Apr 15 2015 12:32:25 GMT-0400 (EDT) | INFO | Connecting...
Thu Apr 15 2015 12:32:25 GMT-0400 (EDT) | INFO | Retrieving data...
Thu Apr 15 2015 12:32:26 GMT-0400 (EDT) | INFO | #3497 records retrieved
Thu Apr 15 2015 12:32:26 GMT-0400 (EDT) | INFO | Copying data...
Thu Apr 15 2015 12:32:30 GMT-0400 (EDT) | INFO | #3497 records copied.
Thu Apr 15 2015 12:32:30 GMT-0400 (EDT) | INFO | Done
````