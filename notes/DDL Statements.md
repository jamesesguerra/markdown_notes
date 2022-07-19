---
tags: [Notebooks/SQL]
title: DDL Statements
created: '2022-07-15T13:29:53.484Z'
modified: '2022-07-15T13:37:02.458Z'
---

# DDL Statements
DDL statements define the structure of database objects like tables and columns.

## CREATE 
Creates a table in the database while defining the columns.
* order of the columns don't matter
```sql
CREATE TABLE teams (
  id          INTEGER     NOT NULL  PRIMARY KEY,
  name        VARCHAR(37) NOT NULL,
  conference  VARCHAR(2)  NULL
);
```

## ALTER 
Changes an object in the database.
```sql
ALTER TABLE teams
DROP COLUMN conference;
```

## DROP
Deletes an object from the database.
```sql
DROP TABLE teams;
```
