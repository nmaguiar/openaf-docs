---
layout: default
title: "Medium: Casting values in PostgreSQL and H2 for OpenAF"
parent: Guides
grand_parent: OpenAF docs
---

# Casting values in PostgreSQL and H2 for OpenAF

When performing specific queries in PostgreSQL and H2 although some results are clearly numeric that are returned as strings. This might affect scripts that previously accessed Oracle and now, accessing using the same query in PostgreSQL and H2, have a different behavior.

## Example with PostgreSQL

Let's start with a quick PostgreSQL example:

````javascript
> var db = new DB("jdbc:postgresql://127.0.0.1/postgres", "postgres", "admin")
> db.q("select count(1) from (select 1 a) as a")
{
  "results": [
    {
      "count": "1"
    }
  ]
}
````

The "count" value is returned as a string despite that count is always numeric. To solve this you can cast the specific column on the SQL select:

````javascript
> db.q("select cast(count(1) as integer) from (select 1 a) as a")
{
  "results": [
    {
      "count": 1
    }
  ]
}
>
````

Another option is to cast in javascript:

````javascript
> var res = db.q("select count(1) from (select 1 a) as a")
> var c = Number(res.results[0].count);
1
````

## Example with H2

The same example but with H2:

````javascript
> var db = createDBInMem();
> db.q("select count(1) abc from ( select 1 abc, 'cenas' xpto from dual )")
{
  "results": [
    {
      "ABC": "1"
    }
  ]
}
````

The count field 'abc' is returned as string. But we can cast in the same way it has handled in PostgreSQL:

````javascript
> db.q("select count(1) abc from ( select 1 abc, 'cenas' xpto from dual )")
{
  "results": [
    {
      "ABC": 1
    }
  ]
}
````

Another options is always to cast it in javascript:

````javascript
> var db = createDBInMem();
> var res = db.q("select count(1) abc from ( select 1 abc, 'cenas' xpto from dual )")
> var c = Number(res.results[0].ABC);
1
````