---
tags: [Notebooks/SQL]
title: SQL SNIPPETS
created: '2022-07-18T11:25:35.509Z'
modified: '2022-07-18T11:52:21.226Z'
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
