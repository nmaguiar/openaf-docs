---
layout: default
title: "Medium: Using an in memory DB"
parent: Guides
grand_parent: OpenAF docs
---

# Using an in memory DB

OpenAF comes with the [H2 database](http://www.h2database.com) embeeded. The main objective is, of course, to interact with H2 databases. But it also provides other perks (e.g. like the [MVStore](http://www.h2database.com/html/mvstore.html)). One of them is an "in-memory" H2 database.

Why would you want or need an "in-memory" database? There are a lot of uses that we won't elaborate now but you can read them in [wikipedia](https://en.wikipedia.org/wiki/In-memory_database). But since H2 is also a relational database engine it can be helpful even if it just for testing.

## Creating

Creating the H2 in-memory database it's easy. Just provide a name and execute:

````javascript
> var db = createDBInMem("testDB");
````

Why a name? Because you can have several databases providing you have the memory capacity for them. The OpenAF's _createDBInMem_ function returns an already instatiated _db_ object that you can now use.

## Using it

````javascript
> db.u("CREATE TABLE test (id NUMBER(10), desc VARCHAR2(255))");
0
> db.q("SELECT * FROM test");
{
  "results": []
}
````

Let's insert some data:

````javascript
> db.us("INSERT INTO test (id, desc) VALUES (?, ?)", [ 0, "Result 0" ]);
1
> db.q("SELECT * FROM test")
{
  "results": [
    {
      "ID": 0,
      "DESC": "Result 0"
    }
  ]
}
````

Let's make it a hundred dummy data records:

````javascript
> var ar = []; for(var ii = 1; ii < 99; ii++) { ar.push([ ii, String("Result " + ii)]); }
98
> db.usArray("INSERT INTO test (id, desc) VALUES (?, ?)", ar)
98
> db.commit();
> 
> db.q("SELECT COUNT(1) c FROM test")
{
  "results": [
    {
      "C": "99"
    }
  ]
}
````

## Persisting

If you exit OpenAF the in-memory database will, of course, lose all it's data. But what if you want to persist it? There are some helper functions for that: _persistDBInMem_ and _loadDBInMem_:

````javascript
> persistDBInMem(db, "test.sql");
````

Then on another OpenAF execution:

````javascript
> var db = createDBInMem("testDB");
> loadDBInMem(db, "test.sql")
5
> db.q("select count(1) C from test")
{
  "results": [
    {
      "C": "99"
    }
  ]
}
````

_Note: the generated files are SQL files. There isn't any intention of supporting large volumes of data databases._