---
tags: [Notebooks/Head First Java]
title: 'Chapter 6: The Java API'
created: '2022-07-22T14:21:09.644Z'
modified: '2022-07-23T02:00:56.777Z'
---

# Chapter 6: The Java API

__Rationale:__ You don't have to reinvent the wheel. Java ships with hundreds of pre-built classes. 

### The `ArrayList`

Dynamic-length arrays. Can hold references and generics, but not primitives. A workaround to this is to use the primitive wrapper classes of the primitives ie. `Integer` for `int`s, `Boolean` for `boolean`s, etc.

Better than arrays because it shrinks and grows accordingly. You don't have to specify a size upon initialization, although you can (`ArrayList<>(int size)`). You can also ask it if it contains an element and get elements without having to know what index it's in.

Although both arrays and `ArrayList`s are objects, `ArrayList`s are first-class objects. This is because it has methods. It can also be a tad bit slower than arrays in some situations, but it's usually not worth giving up all the power it gives you.

1. `add(Object elem)` - adds the object parameter to the end of the list
2. `add(int index, Object elem)` - adds the Object to the given index, the Objects after it will then shift to the right by one
3. `set(int index, Object elem)` - adds the object to the given index
4. `remove(int index)` - removes the object at the index parameter
5. `remove(Object elem)` - removes the object (if it's in the `ArrayList`)
6. `contains(Object elem)` - returns `true` if there's a match for the parameter
7. `isEmpty()` - returns `true` if the list has no elements
8. `indexOf(Object elem)` - returns either the index of the parameter, or -1 if it's not in the `ArrayList`
9. `size()` - returns the number of elements currently in the list
10. `get(int index)` - returns the object currently at the index parameter

#### Declaration & Initialization

```java
// necessary imports
import java.util.ArrayList
import java.util.Arrays

// second type declaration is optional
ArrayList<ObjectType> myList = new ArrayList<ObjectType>();
ArrayList<ObjectType> myList = new ArrayList<>();

// initializing with values
ArrayList<Integer> myList = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
```

### API packages

#### Using the library

Classes are grouped into packages. If you want to use a class in the API, you have to know which __package__ the class is in.

examples:
- __javax.swing__ - holds Swing GUI classes
- __java.util__ - holds utility classes
- __java.lang__ - holds essential classes (`String`, `Math`, `System`)

You have to know the full name of the class you want to use in your code:

```java
// packageName.className
// java.util  .ArrayList
java.util.ArrayList;
```

Import it at the top of your source code so you don't have to type the full name everywhere you use it.
```java
import java.util.ArrayList

ArrayList<Integer> myList = new ArrayList<>();

// instead of 

java.util.ArrayList<Integer> myList = new java.util.ArrayList<>();
```

__main takeaway:__ import or type!

_Extra: [The Java Api Docs](https://docs.oracle.com/javase/7/docs/api/)_ 

