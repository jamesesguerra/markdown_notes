---
tags: [Notebooks/Head First Java]
title: 'Chapter 10: Numbers'
created: '2022-07-28T13:39:55.022Z'
modified: '2022-07-29T02:36:01.699Z'
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

This also means you don't have to use methods for wrapping and unwrapping primitives:
```java
Integer x = 3;
int y = x;
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

In Java, formatting numbers and dates doesn't have to be coupled with I/O (print statements). It's a simple matter of calling a static `String.format()` method and passing it the thing you want to be formatted along with the formatting instructions.

#### Formatting a number to use commas

```java
String s = String.format("%, d", 1000000000);
System.out.println(s) // 1,000,000,000
```

### Formatting deconstructed

At the most basic level, formatting consists of two main parts:

1. __Formatting instructions__
You use special format specifiers that describe how the argument should be formatted.

2. __The argument to be formatted__
Although there can be more than one argument, you can start with just one. The argument type has to be something that can be formatted using the format specifiers in the formatting instructions.

example:

```java
String.format("%, d", 1000000000);
```
The instructions above say: "Take the second argument to this method, and format it as a **d**ecimal integer and insert __commas.__"

Any time you see the percent sign (%) in a format `String`, think of it as representing a variable, and the variable is the other argument to the method. The rest of the characters after the percent sign describe the formatting instructions for the argument. 

### The `%` says, "insert argument here" (and format it using these instructions)

The first argument to a `format()` method is called the format `String`, and it can include characters that you just want printed as-is, without extra formatting. When you see the `%` sign, think of it as a variable that represents the other argument to the method. 

```java
String.format("%.2f", 476578.09876); 
// 476578.10
```
The `%` sign tells the formatter to insert the other method argument (the number) here, AND format it using the ".2f" characters after the percent sign. 

__Adding a comma__

```java
String.format("%,.2f", 476578.09876);
// 476,578.10
```

### Common type modifiers

- `%d`- decimal
- `%f` - floating point
- `%x` - hexadecimal
- `%c` - character


