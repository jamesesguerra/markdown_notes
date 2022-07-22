---
tags: [Notebooks/Head First Java]
title: 'Chapter 2: Classes and Objects'
created: '2022-07-20T02:53:42.211Z'
modified: '2022-07-20T13:17:31.966Z'
---

# Chapter 2: Classes and Objects

#### Chair Wars story takeaways
- Think of what are the __things__ in the program, who are the __key players__
- Look at what the __key players__ have in common and __abstract__ out their common features into a class which you inherit from.
  - the __subclasses__ inherit from a __superclass__ in a relationship called inheritance
  - the subclasses automatically get the same functionality of the superclass
  - subclasses override inherited functionality when they need to change or extend the behavior of that functionality
- object-oriented programming is more flexible, scalable, and extensible
  - the project spec kept changing and the procedural programmer had to keep modifying the code that was already working
  - the OOP programmer just had to make a new class without the need to touch the other classes
- objects don't know or care how other objects do things


#### Desigining a class
- __Think about the objects that will be created from that class type__
  - things the object knows (instance variables / properties)
  - things the object does (methods)
- It's common to have methods that get and set its instance variables

#### Creating and Using Classes
- Make a class for the type of object you want to use
- Make another tester class that has a main method and create objects of your new class type inside it

#### Getting out of `main`
- In true OO applications, objects are talking to other objects, as opposed to a static `main()` method creating and testing objects.
- The two uses of main:
  - testing your _real_ classes
  - to launch/start your Java application
- A real java application: `main` gets the balling rolling by creating objects and turning them loose to interact with other objects

_extra: [Java Class Design](https://eherrera.net/ocpj8-notes/01-java-class-design)_

#### Garbage-Collectible Heap

- Every time an object is created it goes into __the heap__
- Java heap is called the __Garbage Collectible Heap__ 
  - Java allocates memory on the heap according to how much an object needs
- Automatic GC
  - JVM manages memory for you -- when it can see that an object can never be used again, it becomes elligible for GC
