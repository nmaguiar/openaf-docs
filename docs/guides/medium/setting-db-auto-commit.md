---
layout: default
title: "Medium: Setting DB auto commit"
parent: Guides
grand_parent: OpenAF docs
---

# Setting DB auto commit

By default OpenAF opens all database connections in *"autocommit=false"* mode. But in some special cases you might need to turn it on. Let's see one of those cases:

## Creating a PostgreSQL tablespace example

If you open a PostgreSQL connection and try to create a tablespace "TEMP" as you would usually do, this will happen:

````javascript
> var db = new DB("jdbc:postgresql://some.host:5432/postgres", "adminUser", "adminPass");
> db.u("create tablespace temp location '/data'");
-- JavaException: org.postgresql.util.PSQLException: ERROR: CREATE TABLESPACE cannot run inside a transaction block
````

That's because PostgreSQL considers anything with *"autocommit=false"* to be a transaction block. 

## How to set auto commit to on?

To bypass this situation, on a dedicated DB connection, execute the following:

````javascript
> var db = new DB("jdbc:postgresql://some.host:5432/postgres", "adminUser", "adminPass");
> db.getConnect().setAutoCommit(true);
> db.u("create tablespace temp location '/data'");
1
````

The *getConnect* method will return you the JDBC connection instance object which, among [others](https://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html), allows you to execute the *setAutoCommit* method. That's enough to then execute the *"create tablespace"* statement without being in a transaction block.