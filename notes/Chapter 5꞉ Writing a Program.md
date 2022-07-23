---
tags: [Notebooks/Head First Java]
title: 'Chapter 5: Writing a Program'
created: '2022-07-22T09:47:33.912Z'
modified: '2022-07-22T14:19:14.324Z'
---

# Chapter 5: Writing a Program

### Tips on developing a class

- Figure out what the class is supposed to do. 
- List the __instance variables__ and __methods__.
- Write __prepcode__ for the methods.
  - a form of pseudocode to help you focus on the logic without stressing about the syntax
- Write __test code__ for the methods.
  - methods that will test the real code and validate if it's doing the right thing
- __Implement__ the class.
- __Test__ the methods.
- __Debug and reimplement__ as needed.

### Converting a `String` to an `int`
```java
int x = Integer.parseInt("3");
```

### Enhanced _for_ loop
```java
for (int num : numArray) {
  System.out.println(num);
}
```

### Type-casting
Forces the thing immediately after it to become the type of the cast i.e. the type in the parentheses. This is for forcing the value of primitives that have a bigger bit range into another primitive with a smaller bit range. Or in simpler terms, force the compiler to jam the value of a bigger primitive variable into a smaller one. 
```java
double d = 3.343;
int x = (int) d;
```

### Generating a random number
Use Java's `Math` class:
```java
// cast into an int because Math.random returns a float
int randomNum = (int) (Math.random() * 5); // num generated is 0 <= num < 1
```
