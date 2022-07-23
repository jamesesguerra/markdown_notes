---
tags: [Notebooks/Head First Java]
title: 'Chapter 4: Methods Use Instance Variables'
created: '2022-07-21T15:17:01.410Z'
modified: '2022-07-23T01:10:32.905Z'
---

# Chapter 4: Methods Use Instance Variables

__Main idea:__ methods use instance variables and so the state affects the behavior of the object; similarly, methods change the state as well; each object behaves differently based on what they know

### Parameters and Arguments

__important part:__ If a method takes a parameter, you _must_ pass it something. 

A parameter is just another cup or remote in a cup that the will be filled with the argument you pass to the method. 

```java
public class Song {
  String title;

  // titleArg is just a cup 
  public void setTitle(String titleArg) {
    title = titleArg;
  }
}

Song newSong = new Song();

// "Positions" fills the titleArg cup
newSong.setTitle("Positions");
```

### Return values 

Every method is declared with a __return type__. `void` means it won't give anything back. 

If you declare a method with a return type, you _must_ return a value of the declared type (or a value that is _compatible_ with the declared type).

```java
public class Song {
  String title;

  public String getTitle() {
    return title;
  }
}
```

### Java is pass-by-value

This means __pass-by-copy__. That is, if you declare an `int` variable `x` with the value 5, and then you pass this variable to a method which takes in a `y` `int` variable, the value that's passed into `y` is a mere copy of the value of `x`. Making changes to `y` won't affect the value of `x`.

The case would be different if you were to pass a reference variable to a method. In this case, the value that would be passed to the local reference variable are the bits representing a way to get to the object itself. If the local reference variable makes changes to this object, the object the original reference variable was pointing to would be changed as well. This is because the two reference variables are pointing to the same object.

### Encapsulation - Getters and Setters

Without encapsulation, the state of objects would be exposed to all other parts of our code. That is, reachable with the dot operator: 

```java
obj.name = "James";
```

#### Why Encapsulation is bad

In the hands of the wrong person, the remote in a cup could be dangerous. Nothing would stop them from setting unacceptable changes to the instance variables of the object.

#### The solution

Make instance variables `private` and getters and setters `public`. That way, you're forcing other code to go through the setters. You can put in checks to guarantee that the value is valid.

```java
public class Dog {
  private int size;

  public void setSize(int sz) {
    if (sz < 0) {
      System.out.println("invalid size");
    } else {
      size = sz;
    }
  }
}
```

### Declaring and Initializing Instance Variables

Unlike local variables, instance variables get default values. `int`s equal 0, `float`s equal 0, `boolean`s equal `false`, and objects equal `null`.

### Comparing values

#### Primitives and References

To compare the values of two primitives, simply use `==`. The `==` simply __compares the bit or bit patterns__. Using this on two reference variables with the same bits (they're both representing the same object) would equal `true`
```java
int x = 4;
int y = 4;

x == y; // true

Obj o1 = new Object();
Obj o2 = o1;

o1 == o2; // true

```

#### Actual objects

Sometimes, you want to know if two _objects_ are equal, and not just two object references. To compare the equality of reference variables, use `.equals()`. Whether two objects should be treated equal depends on what makes sense for that object type.

Example for `String`s:

```java
String s1 = "Hello World";
String s2 = "Hello World";

s1.equals(s2); // true
```


