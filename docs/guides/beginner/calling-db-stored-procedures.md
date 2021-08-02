---
layout: default
title: Calling DB stored procedures
parent: Beginner
grand_parent: Guides
---

# Calling DB stored procedures

After connecting to a database in OpenAF you might need to execute a function a deal with the result or do the same thing but with a stored procedure (specialy in Oracle). 

For functions, in Oracle and PostgreSQL (or similar) it's pretty straight forward:

````javascript
// Connecting to a postgresql database
var db = new DB("jdbc:postgresql://my.database.server:5432/database", "user", "password");

// Creating a function (if it doesn't exist already)
db.u("CREATE OR REPLACE FUNCTION mySum(a int, b int) RETURNS int AS $$ DECLARE r int; BEGIN SELECT (a+b) INTO r; RETURN r; END; $$ LANGUAGE plpgsql")

// Calling the function
var res = db.q("SELECT mySum(2, 2)");

// Displaying the result
print("The results is: " + res.results[0].mysum)
// 'The result is: 4' 

// Close the access to the database
db.close();
````

In Oracle you would do a similar thing by just adding the reference to DUAL:

````javascript
var res = db.q("SELECT mySum(2, 2) FROM DUAL");
````

## Calling an Oracle stored procedure

But what about stored procedures? Those can not simply be invoked from a select statement since they ae meant to be executed. The trick is to create a temporary inline function to execute them.

Let's start with simple stored procedure as an example:

````sql
CREATE OR REPLACE PROCEDURE MYSUM(a IN NUMBER, b IN NUMBER, r OUT NUMBER) AS 
BEGIN
  SELECT a + b INTO r FROM dual;
END;
````

To call it let's query with a temporary inline function:

````javascript
// Connecting to an oracle database
var db = new DB("jdbc:oracle:thin:@my.server:1521/ORCLCDB", "system", "Oradoc_db1");

// Preparing the initial with statement
var withCallMySum = "\
WITH FUNCTION CALLMYSUM(a INTEGER, b INTEGER) RETURN INTEGER\
AS r INTEGER;\
BEGIN\
  MYSUM(a, b, r);\
  RETURN r;\
END;";

// Calling the function
var res = db.q(withCallMySum + " SELECT CALLMYSUM(2, 2) AS MYSUM FROM DUAL");

// Displaying the result
print("The result is: " + res.results[0].MYSUM);
// 'The result is: 4' 

// Close the access to the database
db.close();
````

That's it. Don't forget to always close the database access when you no longer need it.