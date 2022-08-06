---
tags: [Notebooks/Data Structures]
title: '6: Binary Trees'
created: '2022-08-05T08:37:55.057Z'
modified: '2022-08-06T04:29:00.556Z'
---

# 6: Binary Trees

A binary tree is a data structure that is useful for representing hierarchy. Formally a binary tree is either empty or a root node r together with a left binary tree and a right binary tree. The subtrees themselves are binary trees. The left binary tree is sometimes referred to as the left subtree of the root, and the right binary tree is referred to as the right subtree of the root.

![image](https://user-images.githubusercontent.com/68677613/183042515-ef6f3f54-82c1-4095-a4d6-f402681ed3af.png)

Often the node stores additional data. Its prototype is listed as follows:

```java
public static class BinaryTreeNode<T> {
  public T data;
  public BinaryTreeNode<T> left, right;
}
```

Each node, except the root, is itself the root of a left subtree or a right subtree. If l is the root of p's left subtree, we will say / is the left child of p, and p is the parent of l; the notion of right child is similar. If a node is a left or a right child of p, we say it is a child of p. Note that with the exception of the root, every node has a unique parent. Usually, but not universally, the node object definition includes a parent field (which is null for the root). Observe that for any node there exists a unique sequence of nodes from the root to that node with each node in the sequence being a child of the previous node. This sequence is sometimes referred to as the search path from the root to the node.

The parent-child relationship defines an ancestor-descendant relationship on nodes in a binary tree. Specifically, a node is an ancestor of d if it lies on the search path from the root to d. If a node is an ancestor of d, we say d is a descendant of that node. Our convention is that a node is an ancestor and descendant of itself. A node that has no descendants except for itself is called a leaf.

The depth of a node n is the number of nodes on the search path from the root to n, not including n itself. The height of a binary tree is the maximum depth of any node in that tree. A level of a tree is all nodes at the same depth.

As concrete examples of these concepts, consider the binary tree figure. Node I is the parent of J and O. Node G is a descendant of B. The
search path to L is {A, I, J, K, L). The depth of N is 4. Node M is the node of maximum depth, and hence the height of the tree is 5. The height of the subtree rooted at B is 3. The height of the subtree rooted at H is 0. Nodes D, E, H, M, N, and P are the leaves of the tree.

A full binary tree is a binary tree in which every node other than the leaves has two children. A perfect binary tree is a full binary tree in which all leaves are at the same depth, and in which every parent has two children. A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible. (This terminology is not universal, e.g., some authors use complete binary tree where we write perfect binary tree.) It is straightforward to prove using induction that the number of nonleaf nodes in a full binary tree is one less than the number of leaves. A perfect binary tree of height h contains exactly `2^h+1 - 1` nodes, of which 2^h are leaves. A complete binary tree on n nodes has height `[lg n]`. A left-skewed tree is a tree in which no node has a right child; a right-skewed tree is a tree in which no node has a left child. In either case, we refer to the binary tree as being skewed.

A key computation on a binary tree is traversing all the nodes in the tree. (Traversing is also sometimes called walking.) Here are some ways in which this visit can be done.









