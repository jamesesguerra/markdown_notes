---
tags: [Notebooks/Data Structures]
title: '5: Queues'
created: '2022-08-05T08:34:38.500Z'
modified: '2022-08-05T08:37:13.177Z'
---

# 5: Queues

A queue supports two basic operations—enqueue and dequeue. (If the queue is empty, dequeue typically returns null or throws an exception.) Elements are added (enqueued) and removed (dequeued) in first-in, first-out order. The most recently inserted element is referred to as the tail or back element, and the item that was inserted least recently is referred to as the head or front element. 

A queue can be implemented using a linked list, in which case these operations have 0(1) time complexity. The queue API often includes other operations, e.g., a method that returns the item at the head of the queue without removing it, a method that returns the item at the tail of the queue without removing it, etc. A queue can also be implemented using an array.

A deque, also sometimes called a double-ended queue, is a doubly linked list in which all insertions and deletions are from one of the two ends of the list, i.e., at the head or the tail. An insertion to the front is commonly called a push, and an insertion to the back iscommonly called an inject. A deletion from the front iscommonly called a pop, and a deletion from the back is commonly called an eject. (Different languages and libraries may have different nomenclature.)
