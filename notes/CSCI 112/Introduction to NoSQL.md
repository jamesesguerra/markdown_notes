---
tags: [Notebooks/CSCI 112]
title: Introduction to NoSQL
created: '2022-08-15T13:15:34.248Z'
modified: '2022-08-15T13:47:55.281Z'
---

# Introduction to NoSQL

### History

__Rise of Relational DBs__
- benefits - persistence of data, manages concurrency through transactions
- SQL - standard to talking to DBs
- the problem: __impedence mismatch__
  - cohesive objects are assembled but when saved to the DB, you have to strip it into bits so that they go into individual rows and tables
  - a single logical structure in UI/memory ends up being splattered

__Rise of Object DBs__
- save in-memory data structures directly to disk without mapping between the 2

> SQL became an integration system. This made it hard for other technologies to come in.

__What changed__

Rise of the internet and sites with a lot of traffic (Google, Amazon). With more traffic coming in, you need to scale things. One obvious route is to scale things up: buy bigger boxes. The problem with this is that it costs a lot. The solution to this is to split a big box (computer) into little boxes. The problem with this is that SQL was designed to run as a single system and does not work well with large clusters of little boxes.

Google and Amazon recognized this problem and developed their own data storage system that were different from relational database systems. This started a whole new movement of databases -> NoSQL movement.

### Definition of NoSQL

You cannot define it because of its odd history. What you can do is identify common characteristics of NoSQL DBs.
- non-relational
- mostly open-source and cluster-friendly
- schema-less (schema = blueprint of how the DB is constructed)

### Data models

1. __Key-value store__
Basic idea: you have a key, you go to the DB, and say "grab me the value of this key" The DB knows absolutely nothing about what's in that value. It could be a single number, a complex document, image. Basically a hashmap but persistent in the disk.

2. __Document__

The database is composed of documents wherein each document is some complex data structure. Usually, the data structure is in JSON. You can query it (or parts of it), update. It's more transparent than a key-value store. 

They don't have a set schema as opposed to SQL DBs wherein you can only insert data into the DB as long as it fits the schema that you've defined for that DB. This seems more flexible, but you're always dealing with an implicit schema. The only time you don't use an implicit schema is when you retrieve all data.

__Aggregate-Oriented__

Don't worry about their differences. They have this common notion that you're taking some complex structure that you can save as a single unit into the DB -> Aggregate-Oriented.

Term "aggregate" comes from one of the key concepts of domain-driven design that often when we want to model things, we have to group things together into natural aggregates. Because when we're talking to a DB (even a relational one), it makes sense to think of those aggregates storing and retrieving data. You think of it as a single unit. 



