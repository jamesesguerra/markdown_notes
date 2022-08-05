---
tags: [Notebooks/SQL]
title: SQL SNIPPETS
created: '2022-07-18T11:25:35.509Z'
modified: '2022-07-19T14:59:12.172Z'
---

# SQL SNIPPETS

```sql
CREATE TABLE entries (
	category TEXT,
  	title TEXT,
  	created TEXT
);

CREATE TABLE categories (
	category TEXT,
  	name TEXT
);

INSERT INTO entries
	(category, title, created)
VALUES
	('angst', 'What if i get sick and die?', '2008'),
    ('humor', 'uncle karl and the gasoline', '2009'),
    ('advice', 'be nice to everybody', '2010'),
    ('humor', 'hello statue', '2009'),
    ('science', 'the size of our galaxy', '2011');
    
INSERT INTO categories 
	(category, name)
VALUES
	('advice', 'gentle words of advice'),
    ('angst', 'stories from the id'),
    ('blog', 'log on to my blog'),
    ('humor', 'humorous anecdotes'),
    ('science', 'our spectacular universe');
```

WHERE Shopping Carts
```sql
CREATE TABLE items (
	name TEXT,
  	type TEXT,
  	price FLOAT
);

INSERT INTO items
	(name, type, price)
VALUES
	('thingie', 'widgets', 9.37),
    ('gadget', 'doodads', 19.37),
    ('dingus', 'gizmos', 29.37),
    ('gewgaw', 'widgets', 5.00),
    ('knickknack', 'doodads', 10.00),
    ('whatnot', 'gizmos', 15.00),
    ('bric-a-brac', 'widgets', 2.00),
    ('folderol', 'doodads', 4.00),
    ('jigger', 'gizmos', 6.00),
    ('doohickey', 'widgets', 12.00),
    ('gimmick', 'doodads', 9.37), 
    ('dingbat', 'gizmos', 9.37),
    ('thingamajig', 'widgets', null),
    ('thingamabob', 'doodads', null),
    ('thingum', 'gizmos', null),
    ('contraption', 'widgets', 49.95),
    ('whatchamacallit', 'doodads', 59.95),
    ('whatsis', 'gizmos', null);
```
