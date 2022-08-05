---
tags: [Notebooks/SQL]
title: Overview of optional clauses for the SELECT statement
created: '2022-07-16T04:47:16.946Z'
modified: '2022-07-16T05:22:33.097Z'
---

# Overview of optional clauses for the SELECT statement

## WHERE
Filters out table rows based on the given condition.
```sql
SELECT * 
FROM table_name
WHERE condition=1;
```

## GROUP BY
Groups table rows into group rows based on the values of the specified column(s). Think of this as table rows having the same values in the column(s) collapsing into one row. It's important to note that you don't have access to table rows anymore after aggregating them into group rows.
* A __group row__ is a new row used to represent each group of rows found during the aggregation process.
```sql
SELECT column
FROM table_name
GROUP BY column
```

## HAVING
Essentially a WHERE clause for group rows. Instead of filtering table rows, it filters the group rows produced by the GROUP BY clause.
```sql
SELECT column, COUNT(*) as another_column
FROM table_name
GROUP BY column
HAVING COUNT(*) > 1
```

## ORDER BY 
Returns the tabular set in a specific sequence. DESC determines that it's a descending sequence while ASC is an ascending sequence.
```sql
SELECT *
FROM table_name
ORDER BY column;
```




