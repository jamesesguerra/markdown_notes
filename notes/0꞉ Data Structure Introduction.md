---
tags: [Notebooks/Data Structures]
title: '0: Data Structure Introduction'
created: '2022-08-05T04:47:38.221Z'
modified: '2022-08-05T06:47:17.867Z'
---

# 0: Data Structure Introduction

A data structure is a particular way of storing and organizing related data items so that they can be manipulated efficiently. Usually, the correct selection of data structures is key to designing a good algorithm. Different data structures are suited to different applications. 

Solutions often require a combination of data structures. For example, tracking the most visited pages on a website involves a combination of a heap, a queue, a binary search tree, and a hash table. 

### Commonly used data structures

| Data structure | Key points | 
| ------ | --- |
| Primitives | Know how `int`, `char`, `double`, etc. are represented in memory and the primitive operations on them  |
| Arrays     | Fast access for element at an index, slow lookups (unless sorted) and insertions. Be comfortable with notions of iterations, resizing, partitioning, merging, etc.   |
| Strings | Know how strings are represented in memory. Understand basic operators such as comparison, copying, joining, matching, splitting, etc.
| Lists | Understand trade-offs with respect to arrays. Be comfortable with iteration, insertion, and deletion within singly and doubly linked lists. Know how to implement a list with dynamic allocation, and with arrays.
| Stacks and queues | Recognize where LIFO and FIFO semantics are applicable. Know array and linked list implementations.
| Binary trees | Use for representing hierarchical data. Know about depth, height, leaves, search path, traversal sequences, successor/predecessor operations.
| Heaps | Key benefit: `O(1)` lookup find-max, `O(log n)` insertion, and `O(log n)` deletion of max. Node and array representations. Min-heap variant.
| Hash tables | Key benefit: `O(1)` insertions, deletions, and lookups. Key disadvantages: not suitable for order-related queries; need for resizing; poor worst-case performance. Understand implementation using array of buckets and collision chains. Know hash functions for integers, strings, objects.
| Binary search trees | Key benefit: `O(log n)` insertions, deletions, lookups, find-min, find-max, successor, predecessor when tree is height-balanced. Understand node fields, pointer implementation. Be familiar with notion of balance, and operations maintaining balance.
