---
tags: [Notebooks/Python API Dev]
title: '4: Database'
created: '2022-08-09T14:04:00.842Z'
modified: '2022-08-10T05:22:15.210Z'
---

# 4: Database

A collection of organized data that can be easily accessed and managed.

### DBMS

- We don't interact with the database directly
- DBMS sits in the middle and performs operations and sends results back

#### Postgres

Each instance of postgres can be carved into multiple separate databases.

#### pgAdmin

1. Create Server
2. Create DB
3. Create Tables
4. Create Columns
  - __text__ = character varying
  - __number__ = integer
  - __is_condition__ = boolean, default = False
  - __id__ = serial
  - __created_at__ = time stamp with timezone, default = NOW()


#### returning rows right after insert
```sql
INSERT INTO table_name
  (column_name)
VALUES
  (value_name)
RETURNING columns;
```

```sql
UPDATE table_name
SET column_name = value
WHERE condition = TRUE
RETURNING columns;
```

```sql
DELETE FROM table_name
WHERE condition = TRUE
RETURNING columns;
```

