---
tags: [Notebooks/SQL]
title: FROM
created: '2022-07-16T11:10:46.774Z'
modified: '2022-07-18T10:55:37.072Z'
---

# FROM

### Tabular result set
The FROM clause retrieves data from one or more tables. The product is called the **result set** of the FROM clause or an intermediate tabular result.

### Rationale behind starting with the FROM clause
Start by thinking of the FROM clause because if you get this wrong the whole query would be wrong. It's the first clause that's parsed and executed by SQL. 

### Selecting FROM one table
```sql
SELECT *
FROM table_name;
```

### Selecting FROM more than one table using JOINs (see JOIN)
```sql
SELECT *
FROM 
  left_table INNER JOIN right_table
    ON left_table.id = right_table.id; 
```
