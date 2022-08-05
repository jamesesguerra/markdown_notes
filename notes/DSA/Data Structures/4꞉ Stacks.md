---
tags: [Notebooks/Data Structures]
title: '4: Stacks'
created: '2022-08-05T08:29:01.036Z'
modified: '2022-08-05T08:34:27.436Z'
---

# 4: Stacks

_"Linear lists in which insertions,deletions,and accesses to values occur almost always at the first or the last node are very frequently encountered, and we give them special names . . ." - D.E. Knuth_

A stack supports two basic operations—push and pop. Elements are added (pushed) and removed (popped) in last-in, first-out order. If the stack is empty, pop typically returns null or throws an exception.

When the stack is implemented using a linked list these operations have O(1) time complexity. If it is implemented using an array, there is maximum number of entries it can have—push and pop are still O(1). If the array is dynamically resized, the amortized time for both push and pop is O(1). A stack can support additional operations such as peek, which returns the top of the stack without popping it.


