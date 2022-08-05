---
tags: [Notebooks/SQL]
title: DML Statements
created: '2022-07-15T13:37:13.264Z'
modified: '2022-07-16T00:03:25.302Z'
---

# DML Statements

## INSERT (create)
Creates a new row in the database.
```sql
INSERT INTO teams
  (id, name, conference)
VALUES
  (1, 'Chicago Bulls', 'E');
```

Using the constructor function:
```sql
INSERT INTO teams
  (id, name, conference)
VALUES 
  (1, 'Chicago Bulls', 'E'),
  (2, 'Golden State Warriors', 'W'),
  (3, 'Orlando Magic', 'E');
```

## UPDATE (update)
Changes the data within the table.
```sql
UPDATE teams
SET conference = 'W'
WHERE id = 1;
```

## DELETE (delete)
Removes a row or set of rows from the table.
```sql
DELETE FROM teams
WHERE id = 1;
```

## SELECT (read)
Retrieves data from __one or more__ tables; produces a tabular result set (another table derived from the table objects in the database).
- SELECT clause specifies what you want to retrieve
- FROM clause specifies the tabular structure(s) to retrieve it from 
```sql
SELECT *
FROM teams;
```

Optional clauses of the SELECT statement:
```sql
SELECT expression(s)
FROM tabular structure(s)
[WHERE clause]
[GROUP BY clause]
[HAVING clause]
[ORDER BY clause]
```
