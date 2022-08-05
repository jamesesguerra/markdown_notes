---
tags: [Notebooks/Data Structures]
title: '7: Heaps'
created: '2022-08-05T08:46:16.525Z'
modified: '2022-08-05T08:53:07.075Z'
---

# 7: Heaps

_"Using F-heaps we are able to obtain improved running times for several network optimization algorithms."_ - M.L. Fredman and R.E. Tarjan

A heap (also referred to as a priority queue) is a specialized binary tree. Specifically, it is a complete binary tree as defined in the binary trees chapter. The keys must satisfy the heap property—the key at each node is at least as great as the keys stored at its children. See the figure below for an example of a max-heap. A max-heap can be implemented as an array; the children of the node at index i are at indices 2i +1 and 2i + 2. The array representation for the max-heap in Figure 11.1(a) is (561, 314, 401, 28,156,359, 271,11,3).

A max-heap supports 0(log n) insertions, 0(1) time lookup for the max element, and 0(log n) deletion of the max element. The extract-max operation is defined to delete and return the maximum element. See Figure11.1(b) for an example of deletion of the max element. Searching for arbitrary keys has 0(n) time complexity.

The min-heap is a completely symmetric version of the data structure and supports 0(1) time lookups for the minimum element.
