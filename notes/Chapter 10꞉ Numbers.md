---
tags: [Notebooks/Head First Java]
title: 'Chapter 10: Numbers'
created: '2022-07-28T13:39:55.022Z'
modified: '2022-07-28T14:08:24.350Z'
---

# Chapter 10: Numbers

### Wrapping a primitive

There are times when you want to treat a primitive like an object. There's a wrapper class for every primitive type. You can recognize wrapper classes because each one is named after the primitive type it wraps.

#### Wrapping a value
```java
int i = 299;
Integer iWrap = new Integer(i);
```

#### Unwrapping a value
```java
int unWrapped = iWrap.intValue();
```

### Autoboxing

The autoboxing feature converts from primitive to wrapper object automatically.

An `ArrayList` of primitive `int`s:
```java
ArrayList<Integer> myList = new ArrayList<Integer>();
myList.add(3); // you don't have to wrap '3' with its wrapper class
int num = myList.get(0); // you don't have to unwrap it either to assign to an int variable
```

### Wrappers' static utility methods

Besides acting like a normal class, the wrappers have a bunch of useful static methods. 

__parse methods__
This lets you convert a `String` to a primitive value
```java
String s = "2";
int i = Integer.parseInt(s); // 2
double d = Double.parseDouble("42.2");
boolean b = Boolean.parseBoolean("True"); 
```
__turning a number into a String__
There are several ways of turning a number into a `String`:
1. Simply concatenating the number to an existing `String`
```java
double d = 42.5;
String doubleString = "" + d;
```
2. static method in class `Double`
```java
double d = 42.5
String doubleString = Double.toString(d);
```

### Number formatting

In Java, formatting numbers and dates doesn't have to be coupled with I/O (print statements). 


