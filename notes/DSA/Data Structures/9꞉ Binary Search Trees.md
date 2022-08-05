---
tags: [Notebooks/Data Structures]
title: '9: Binary Search Trees'
created: '2022-08-05T08:54:30.782Z'
modified: '2022-08-05T08:56:02.415Z'
---

# 9: Binary Search Trees

Adding and deleting elements to an array is computationally expensive, when the array needs to stay sorted. BSTs are similar to arrays in that the stored values (the "keys") are stored in a sorted order. BSTs offer the ability to search for a key as well as find the min and max elements, look for the successor or predecessor of a search key (which itself need not be present in the BST), and enumerate the keys in a range in sorted order. However, unlike with a sorted array, keys can be added to and deleted from a BST efficiently.

A BST is a binary tree as defined in Chapter 10 in which the nodes store keys that are comparable, e.g., integers or strings. The keys stored at nodes have to respect the BST property—the key stored at a node is greater than or equal to the keys stored at the nodes of its left subtree and less than or equal to the keys stored in the nodes of its right subtree. Figure 15.1 on the facing page shows a BST whose keys are the first 16 prime numbers.

Key lookup, insertion, and deletion take time proportional to the height of the tree, which can in worst-case be 0(n), if insertions and deletions are naively implemented. However, there are implementations of insert and delete which guarantee that the tree has height 0(log n). These require storing and updating additional data at the tree nodes. Red-black trees are an example of height-balanced BSTs and are widely used in data structure libraries.

A common mistake with BSTs is that an object that's present in a BST is to be updated. The consequence is that a lookup for that object will now fail, even though it's still in the BST.When a mutable object that's in a BST is to be updated, first remove it from the tree, then update it, then add it back. (As a rule, avoid putting mutable objects in a BST.)
