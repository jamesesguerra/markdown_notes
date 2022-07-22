---
tags: [Notebooks/SQL]
title: WHERE
created: '2022-07-19T14:09:51.651Z'
modified: '2022-07-22T04:00:26.596Z'
---

# WHERE

### Filtering
The WHERE clause is an optional clause that filters out the result set produced by the FROM clause. It allows us to obtain a result set containing only the data we're interested in.

### Conditions
It's all about true conditions. It's basic syntax is:
```sql
WHERE --condition that evaluates AS true--
```

The result of the evaluation of the condition will be one of `TRUE`, `FALSE`, or `UNKNOWN`.

#### Conditions that are TRUE
A typical WHERE condition:
```sql
SELECT *
FROM table_name
WHERE id = 10;
```
The WHERE clause filters out the result set rows using the `id = 10` condition. It evaluates the truth of the condition for every row.

#### When you want "false" values
What if you want the rows where id is not equal to 10?

Two approaches:

1. WHERE NOT id = 10
2. WHERE id <> 10

#### UNKNOWN
A condition evaluates as UNKNOWN if the db system is unable to figure out whether it's TRUE or FALSE. This happens on operations on columns that have `null` values.

* `NULL` is not equal to anything, not even another `NULL`.


### Operators

#### Comparison Operators
- less than
```sql
SELECT *
FROM table_name
WHERE id < 10;

-- comparing character strings --
WHERE name < 'C' -- returns all names that start with 'A' or 'B'

-- comparing dates --
WHERE published < '2000-01-01'; -- returns rows with published date earlier than January 1, 2001 -- 
```

#### The `LIKE` Operator
Implements pattern-matching: allows you to search for a pattern in a string. 

__Two wildcards:__
- `%` 0 or more characters
- `_` exactly one character

#### The `BETWEEN` Operator
Enables a range test to see if a value is _between_ two other values. 

__NOTE:__ The smaller value has to come first, and the larger value has to come last.
```sql
-- with ints --
SELECT *
FROM table_name
WHERE price BETWEEN 5 AND 10;

-- with dates -- 
SELECT *
FROM table_name
WHERE created BETWEEN CURRENT_DATE - INTERVAL 5 DAY AND CURRENT_DATE; -- returns entries from the last 5 days -- 
```

Use compound conditions with dates:
```sql
-- ❌ using BETWEEN is hardcoded --
SELECT *
FROM table_name
WHERE created BETWEEN '2009-02-01' AND '2009-02-28';

-- preferred way --
SELECT *
FROM table_name
WHERE created >= '2009-02-01' AND created < '2009-02-28';
```

#### IN Condition

If any of the values in the list of the `IN` condition is equal to the expression that comes before the `IN` condition, the `IN` evaluates to `TRUE`. Helpful for avoiding multiple `OR` compound conditions.

```sql
-- returns rows that have a category name in the list
SELECT *
FROM category
WHERE category.name IN ('Humor', 'Comedy');

-- returns rows that have a category name that is not in the list --
SELECT *
FROM category
WHERE category.name NOT IN ('Humor', 'Comedy');
```








