---
tags: [Notebooks/Head First Java]
title: 'Chapter 10: Statics'
created: '2022-07-28T12:24:26.934Z'
modified: '2022-07-28T13:35:11.600Z'
---

# Chapter 10: Statics

### Math methods

The methods in the Java `Math` class don't depend on any instance variables. For example, the `round()` method does the same thing every time -- it rounds a floating point number to the nearest integer. The method acts on the argument, but is never affected by an instance variable state. The only value that changes the way the `round()` method runs is the argument passed to the method.

It's a perfect waste of heap space to make an instance of the `Math` class simply to run the `round()` method. These methods never use instance variables. So there's nothing to be gained by making an instance of class `Math`. 

The methods in the `Math` class are `static` because they don't use any instance variable values. And because they are `static`, you don't need to have an instance of `Math`. All you need is the `Math` class:

```java
int x = Math.round(42.2);
// this method never uses instance variables
// its behavior doesn't need to know about a specific object
```

### The difference between non-static and static methods

The keyword `static` lets a method run _without any instance of the class._ A static method means "behavior not dependent on an instance variable, so no instance/object is required. Just the class."

__Static methods are called using a class name:__
```java
Math.min(88, 86);
```

__Non-static methods are called using a reference variable name:__
```java
Song t2 = new Song();
t2.play();
```

### A class with static methods

Often, a class with static methods isn't meant to be instantiated. But this does not mean that a class with one or more static methods should never be instantiated. 

You're also free to combine static and non-static methods in a class, although even a single non-static methods means there must be some way to make an instance of the class.

### Static methods can't use non-static instance variables

Static methods run without knowing about any particular instance of the static method's class. Since a static method is called using the class as opposed to an instance reference, a static method can't refer to any instance variables of the class. It doesn't know _which_ instance's variable value to use.

```java
public class Dog {
  private int size;

  public static void main (String[] args) {
    System.out.println(size);
  }
}
```
The code above will give you an error because the compiler thinks, "I don't know which object's instance variable you're talking about." If there are 10 objects on the heap, a static method doesn't know about any of them.

### Static methods can't use non-static methods

Because non-static methods usually use instance variable state to affect the behavior of the method, you cannot call non-static methods in a static method. It just postpones the inevitable of the non-static method using an instance variable. But even if the non-static method doesn't use an instance variable, the compiler will still not let you call it from a static method because it knows you _can_ use instance variables.

### Static variables

Static variables are the same for ALL instances of the class. A static variable gives you a value shared by all instances of the class. In other words, one value per _class_, instead of one value per _instance._ Non-static variables give you one variable per instance.

You can think of a static variable that lives in a CLASS instead of in an object:

instance variables: 1 per __instance__
static variables: 1 per __class__

### Initializing a static variable

Static variables are initialized when a class is loaded. A class is loaded when the JVM decides to. Typically, JVM loads a class because somebody's trying to make a new instance of the class.

There are two guarantees about static initialization:

1. Static variables in a class are initialized before any object of that class can be created.
2. Static variables in a class are initialized before any static method of the class runs.

### constants

A variable marked as `final` means that -- once initialized -- it can never change. 

An example of this is the `PI` variable in the `Math` class:
```java
Math.PI; // 3.141592653589793
```
- The variable is marked __public__ so that any code can access it.
- The variable is marked __static__ so that you don't need an instance of class `Math`.
- The variable is marked __final__ because `PI` doesn't change.

There is no other way to designate a variable as a constant, but there is a naming convention to help you recognize one: __constant variable names should be in all caps.__

__Initializing a final static variable:__
```java
public class Foo {
  public static final int FOO = 25;
}
```
If you don't give a value to a final variable, the compiler will throw an error.

### `final` isn't just for static variables...

You can use the keyword `final` to modify non-static variables too, including instance variables, local variables, and even method parameters. In each case, it means the same thing: __the value can't be changed.__

- A final __variable__ means you can't __change__ its value.
- A final __method__ means you can't __override__ the method.
- A final __class__ means you can't __extend__ the class.

