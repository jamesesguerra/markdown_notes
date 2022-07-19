---
attachments: [Clipboard_2022-07-18-18-59-38.png, Clipboard_2022-07-18-19-01-38.png, Clipboard_2022-07-18-19-03-50.png, Clipboard_2022-07-18-19-05-58.png, Clipboard_2022-07-18-19-06-17.png, Clipboard_2022-07-18-19-06-42.png, Clipboard_2022-07-18-19-06-59.png, Clipboard_2022-07-18-19-22-22.png]
tags: [Notebooks/SQL]
title: JOIN
created: '2022-07-18T10:56:35.920Z'
modified: '2022-07-18T11:25:20.610Z'
---

# JOIN

### Types of JOINs
- INNER JOIN
- OUTER JOIN
  - LEFT OUTER JOIN
  - RIGHT OUTER JOIN
  - FULL OUTER JOIN
- CROSS JOIN

## INNER JOIN
Only returns the rows that satisfy the conditions in the ON clause.

![](@attachment/Clipboard_2022-07-18-19-05-58.png)

```sql
SELECT *
FROM 
  left_table INNER JOIN right_table
    ON left_table.id = right_table.id;
```

## LEFT OUTER JOIN
Returns the rows that satisfy the conditions in the ON clause plus unmatched rows in the left table. Columns that are in the right table would be null for the unmatched rows.

![](@attachment/Clipboard_2022-07-18-19-06-17.png)

```sql
SELECT *
FROM 
  left_table LEFT OUTER JOIN right_table
    ON left_table.id = right_table.id;
```

## RIGHT OUTER JOIN
Returns the rows that satisfy the conditions in the ON clause plus unmatched rows in the right table. Columns that are in the left table would be null for the unmatched rows.

![](@attachment/Clipboard_2022-07-18-19-06-42.png)

```sql
SELECT *
FROM 
  left_table LEFT OUTER JOIN right_table
    ON left_table.id = right_table.id;
```

## FULL OUTER JOIN
Returns all rows from both tables regardless of whether they have a match in the other table.

![](@attachment/Clipboard_2022-07-18-19-06-59.png)

```sql
SELECT *
FROM 
  left_table FULL OUTER JOIN right_table
    ON left_table.id = right_table.id;
```

## CROSS JOIN
Every row from both tables is returned, joined to every row of the other table, regardless of whether they match. Represents all combinations of two sets of values.

```sql
SELECT *
FROM left_table CROSS JOIN right_table;
```

### The process of a query
-----------------------------
![](@attachment/Clipboard_2022-07-18-19-22-22.png)

* The JOIN produces an intermediate result set. The SELECT statement then operates on this intermediate result set, selecting columns to display.


