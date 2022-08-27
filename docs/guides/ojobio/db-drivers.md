---
layout: default
title: DB JDBC drivers
parent: oJobIO
grand_parent: Guides
---

# DB JDBC drivers

Since OpenAF runs on Java it can connect to databases that have a JDBC driver. Besides the included JDBC drivers (e.g. PostgreSQL, H2, ...) you might need to add other non-included databases. 

To make this process easier you can use the following ojob.io job that can quickly build an OpenAF oPack to include the JDBC driver you need plus a simple wrapper to quickly use it.

## Listing

First to list the supported JDBC drivers just execute:

````bash
$ ojob ojob.io/db/getDriver op=list
    db    
──────────
csv       
db2       
drill     
h2        
hsqldb    
mariadb   
mdb       
mysql     
opendistro
oracle    
paradox   
postgresql
sqlite    
sqlserver 
yugabytedb
````

## Building

To build the oPack for the database you need just execute (for example, for sqlite):

````bash
$ ojob ojob.io/db/getDriver op=build db=sqlite

Downloading org.xerial.sqlite-jdbc...
Generating helper lib jdbc-sqlite.js ...
Generating opack...
Writing jdbc-sqlite-20220102.opack
To use it just:

        loadLib("jdbc-sqlite.js");
        var db = new DB("jdbc:sqlite:{{file}}", ...)
````

On the end of the process of building the oPack the "To use it just" shows an example of how you can use the built opack after installation.

## Installing

To install in your local machine you can just use _"op=install"_ instead of _"op=build"_.

If you want to install in another OpenAF installation just take the resulting opack file resulting from _"op=build"_.

## Using it

After installing the opack built previously you can use like this: 

````javascript
loadLib("jdbc-sqlite.js")
var db = new DB("jdbc:sqlite:test.db")

// Creating a table
db.u("create table test (k varchar, v number)")

// Putting some records there
ow.loadObj()
ow.obj.fromArray2DB([
    { k: 'a', v: 1 },
    { k: 'b', v: 2 },
    { k: 'c', v: 3 }
], db, "test")

// Retrieving data from the table
sprint(db.q("select * from test"))
````

## If the database you want is not available

If the database you want is not listed and it has a JDBC driver just submit the request in [oJob.io GitHub issues](https://github.com/OpenAF/oJob.io/issues) or directly contribute to the [oJob.io project](https://github.com/OpenAF/oJob.io).