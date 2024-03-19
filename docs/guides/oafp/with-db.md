---
layout: default
title: oafp with DB
parent: oafp
grand_parent: Guides
---

# oafp with DB

List of examples of use of oafp with databases:

## H2

### Store the json result of a command into a H2 database table

```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:h2:./data" dbuser=sa dbpass=sa dbtable=data
```

### Perform a SQL query over a H2 database

```bash
echo "select * from \"data\"" | oafp in=db indbjdbc="jdbc:h2:./data" indbuser=sa indbpass=sa out=ctable
```

## SQLite

Retrieve and install the JDBC driver for SQLite

```bash
ojob ojob.io/db/getDriver op=install db=sqlite
```

### Store the json result on a SQLite database table
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:sqlite:data.db" dbtable=data dblib=sqlite
```

### Perform a query over a database using JDBC

```bash
echo "select * from data" | oafp in=db indbjdbc="jdbc:sqlite:data.db" indbtable=data indblib=sqlite out=ctable
```