---
attachments: [Clipboard_2022-07-20-21-36-01.png, Clipboard_2022-07-20-21-41-18.png, Clipboard_2022-07-21-12-46-20.png, Clipboard_2022-07-21-13-03-26.png, Clipboard_2022-07-21-23-01-51.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 3: Primitives and References'
created: '2022-07-20T13:17:12.223Z'
modified: '2022-07-21T15:04:10.960Z'
---

# Chapter 3: Primitives and References

## Two kinds of variables

1. primitive - hold fundamental values such as integers, booleans, floats
2. reference - hold references to objects

* the type-safety that the compiler employs works because of these variable type declarations

### Primitives

- A  primitive variable is just __a cup__, it holds something. 
- It has a size and a type.

Primitives come in different cup types: short, tall, etc. And those types have sizes. And those sizes have names. The primitive type specifies the cup name and size, while the value you give to the primitive is like the drink that goes in the cup. 
![](@attachment/Clipboard_2022-07-20-21-41-18.png)

Each primitive type has a fixed number of bits (cup size). 

#### Spillage

You can't put a large value into a small cup. The compiler won't allow you to put a big thing into a small container even if it fits, because there's always the possiblity of spillage. The compiler doesn't know the value of your variable and it always errs on the side of safety.

### References

- A reference variable is like a __remote control in a cup__, it points to something -- the object itself.

There's no such thing as object variables, only __object reference__ variables. It doesn't hold the object itself, instead it holds a pointer or a way to access the object. 

There aren't any cups that expand to fit the size of every object. If primitive variables store bits that represent the actual value of the variable, reference variables is merely full of bits representing __a way to get to the object__. Reference variables are like remotes, they are pointers to the objects that are living in the GC heap. And its buttons are methods and instance variables.

#### Dot notation

When you use the dot operator on a reference variable, it's like saying "use the thing before the dot to get me the thing after the dot". Think of it like a pressing a button on a remote. You use it to get the object to do something or get information out of it.

#### Object declaration, creation, and assignment

Program the remote control in a cup (reference variable) to point to or control a TV (the object).

```java
// declare a reference variable
Dog d;

// create the object, linking them together with =
Dog d = new Dog();
```

#### Memory Management

As a programmer, you don't know or care about how the big the bits representing the object are. Your concern should be how many objects you're creating and their size as opposed to how many object references. 

##### Reprogramming remotes

A reference variable with type `Dog` cannot point to a `Cat` object. But it _can_ point to another `Dog` object as long as it isn't marked as `final`.

If the reference variable is reprogrammed to point to `null`, it then becomes eligible for GC. 

In this example, both reference variables `c` and `d` are pointing to the same object.
![](@attachment/Clipboard_2022-07-21-12-46-20.png)

In the example below, the object Book `b` was initially pointing to becomes eligible for GC since there are no more reference variables point to it.

![](@attachment/Clipboard_2022-07-21-13-03-26.png)

#### `null` references
```java
Dog d = new Dog();
d = null; // not pointing to anything, but still a reference variable
```

### Arrays
- An array is like a __tray of cups__. They are also objects that can hold primitives or references. Every element inside it is just a variable. Anything you would put into a _cup_ of that type can be assigned to a _tray_ (array) of that type.  

```java
int[] nums = new int[7];
```

![](@attachment/Clipboard_2022-07-21-23-01-51.png)

