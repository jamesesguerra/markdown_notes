---
tags: [Notebooks/Algorithms Part 1]
title: '1: Union Find'
created: '2022-08-06T04:36:40.132Z'
modified: '2022-08-06T05:47:22.138Z'
---

# 1: Union Find

### The dynamic connectivity problem

Given a set of N objects.
- __Union command__ - connect two objects
- __Find/connected query__ - is there a path connecting the two objects?

#### Modeling the objects

Applications mainly involve manipulating objects of all types.

### Union-find data type (API)

Goal: Design an efficient data structure for union-find
- Number of objects N can be huge
- Number of operations M can be huge

```java
public class UF {
  public UF(int n) {} // init data type with N objects (0 to N - 1)
  void union(int p, int q) // add connection between p and q
  boolean connected(int p, int q) // are p and q connected
}
```

### Quick-find approach (eager approach)

Data structure: 
- `int` array `id[]` of length N
- p and q are connected iff they have the same id

__implementation:__
```java
boolean connected(int p, int q) {
  return id[p] == id[q];
}

void union(int p, int q) {
  int pid = id[p];
  int qid = id[q];
  for (int i = 0; i < id.length; i++) {
    if (id[i] == pid) id[i] = qid;
  }
}
```
__Quadratic algorithms do not scale.__
The union operation is too expensive. It has a time complexity of O(n). Therefore, n union operations would take O(n^2) time. 

### Quick-union approach (lazy approach)
Data structure:
- `int` array `id[]` of length N
- `id[i]` is parent of `i`
- root of `i` is `id[id[id[...id[i]...]]]`

__find:__ check if p and q have the same root
__union:__ set the id of p's root to the id of q's root

__implementation:__
```java
private int root(int i) {
  while (i != id[i]) {
    i = id[i];
  }
  return i;
}

public boolean connected(int p, int q) {
  return root(p) == root(q);
}

public void union(int p, int q) {
  // change root of p to point to root of q
  id[root(p)] = root(q);
}
```

#### Cost models so far 
| algorithm | initialize | union | find |
| ------ | --- | ----- | ------- | ----- |
| quick-find     | O(n)   | O(n)    | O(1) |
| quick-union      | O(n)   | O(n)    | O(n) |

Quick-find defect:
- union is too expensive (N array accesses)
- trees are flat, but too expensive to keep them flat

Quick-union defect:
- trees can get tall
- find too expensive (could be N array accesses)

### Improvements

#### Improvement 1: weighting

Weighted quick-union:
- modify quick-union to avoid tall trees
- keep track of size of each tree (number of objects)
- balance by linking root of smaller tree to root of larger tree

__implementation:__
Data structure: same as quick-union but maintain an extra array `sz[i]` to count number of objects in the tree rooted at `i`

union: modify quick-union to:
```java
public void union(int p, int q) {
  int i = root(p);
  int j = root(q);
  if i == j return; // if already under the same root, already connected
  if (sz[i] < sz[j]) { 
    id[i] = j; // make parent of root of p equal to root of q
    sz[j] += sz[i];
  } else {
    id[j] = i;
    sz[i] += sz[j];
  }
}
```

#### Cost model
| algorithm | initialize | union | find |
| ------ | --- | ----- | ------- | ----- |
| weighted-QU     | O(n)   | O(log n)    | O(log N) |

#### Improvement 2: path compression

Just after computing the root of p, set the id of each examined note to point to that root

__implementation:__ make every other node in path point to its grandparents (thereby halving path length)

```java
private int root(int i) {
  while (i != id[i]) {
    id[i] = id[id[i]];
    i = id[i];
  }
  return i;
}
```



 

