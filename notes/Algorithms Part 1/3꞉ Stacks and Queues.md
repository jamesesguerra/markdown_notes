---
tags: [Notebooks/Algorithms Part 1]
title: '3: Stacks and Queues'
created: '2022-08-07T05:26:47.058Z'
modified: '2022-08-07T06:05:31.997Z'
---

# 3: Stacks and Queues

These are fundamental data types (ADT). They don't necessarily care about how they're implemented. It doesn't matter whether you implement them with arrays or linked lists. What matters is that their behavior (FIFO & LIFO) is implemented.

- value: collection of objects
- operations: __insert__, __remove__, __iterate__, test if empty

![image](https://user-images.githubusercontent.com/68677613/183276940-c0a8b2ab-a8da-4841-b1f2-ec40f165642e.png)

__Stack -__ remove the most recently added item
__Queue -__ remove the least recently added item

#### Modular Programming

The act of separating interface and implementation.
- client can't know details of the implementation - client has many implementations from which to choose
- implementation can't know details of client needs - many clients can reuse the same implementation
- __design:__ creates modular, reusable libaries

### Stack API

A warmup stack API of a string data type.

```java
public class StackOfStrings {
  StackOfStrings(); // init
  void push(String item); // insert a string onto the stack
  String pop(); // remove and return the string of the most recently added
  boolean isEmpty(); // is the stack empty?
  int size(); // number of strings on the stack
}
```

linked-list implementation in Java:
```java
public class LinkedStackOfStrings {
  private Node first = null;

  private class Node {
    String item;
    Node next;
  }

  public boolean isEmpty() {
    return first == null;
  }

  public void push(String item) {
    Node oldFirst = first;
    first = new Node();
    first.item = item;
    first.next = newNode;
  }

  public String pop() {
    String item = first.item;
    first = first.next;
    return item;
  }
}
```

array implementation:
- use array `s[]` to store N items on stack
- `push()` - add new item at `s[N]`
- `pop()` - remove item from `s[N-1]`
- defect - stack overflows when N exceeds capacity

```java
public class FixedCapacityStackOfStrings {
  private String[] s;
  private int N = 0;

  public FixedCapacityStackOfStrings(int capacity) {
    s = new String[capacity];
  }

  public boolean isEmpty() {
    return N == 0;
  }

  public void push(String item) {
    s[N++] = item;
  }

  public String pop() {
    return s[--N];
  }
}
```

#### Stack considerations

__Overflow and underflow__
- underflow - throw exception if pop from an empty stack
- overflow - use resizing array for array implementation

__Null items__ - we allow `null` items to be inserted

__Loitering__ - holding a reference to an object when it is no longer needed

loitering:
```java
public String pop() {
  return s[--N];
}
```

avoids loitering; GC can claim memory only if no outstanding references:
```java
public String pop() {
  String item = s[--N];
  s[N] = null;
  return item;
}
```


