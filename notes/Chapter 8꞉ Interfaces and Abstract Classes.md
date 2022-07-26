---
attachments: [Clipboard_2022-07-26-10-39-41.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 8: Interfaces and Abstract Classes'
created: '2022-07-25T03:13:54.580Z'
modified: '2022-07-26T02:39:41.525Z'
---

# Chapter 8: Interfaces and Abstract Classes

__Rationale:__ To exploit polymorphism, we need interfaces and to go beyond simple inheritance. 


### Abstract classes: what we missed when designing the inheritance tree

The class structure was designed so that duplicate code is kept to a minimum and there is a common protocol enforced. However, __some classes are not meant to be instantiated.__ That is, we can imagine what a `Hippo` or `Dog` object looks like, but what does an `Animal` object look like?

We need the `Animal` class for inheritance and polymorphism, but we only want to instantiate the less abstract classes of `Animal`. To prevent anyone from instantiating (saying `new`) on that type, we can mark the class as __abstract__. The compiler will stop any code from instantiating an abstract class. 

```java
public abstract class Animal {
  ...
}
```

You can still use the abstract class as reference types, polymorphic arguments, or polymorphic return types.

When designing an inheritance tree, you have to decide which classes are _abstract_ and which classes are _concrete_. __Concrete classes_ are classes that are specific enough to be instantiated ie. it's OK to make objects of this type. 

* an abstract class has no value unless it is extended, the guys doing the work for abstract classes at runtime are the instances of a subclass of the abstract class

#### Deciding whether a class should be abstract or concrete

This very much depends on the application/project specifications. Tips in general:

- A class would be abstract if it _must_ be extended. That is, there is definitely going to be more specific types of this class in the application. An example would be a `BasketballPlayer` class in an NBA2k game. A `BasketballPlayer` class would be too general for this application.
- A class would be concrete if it is specific enough to be instantiated. There is no more need to extend a concrete class, the inheritance line for it ends there. The same `BasketballPlayer` class can be specific enough in an application like The Sims.


### Abstract methods

Methods can be marked as `abstract` too. An abstract class means that it must be _extended_; an abstract method means the method must be _overridden._ You would want to do this if a certain method won't make sense unless it is implemented by a more specific subclass. In other words, make a method abstract if you can't think of any generic method implementation that could be useful for subclasses. 

#### An abstract method has no body

Because nothing would make sense in the abstract method, it does not contain a body:
```java
public abstract void eat();
```
If you declare an abstract method in a class, you MUST mark the class abstract as well. You can also mix abstract and non-abstract methods in the abstract class.

#### The point of abstract methods

The point of abstract methods is that even though you aren't giving any useful code for the subclasses to extend, you're still defining a protocol. And this matters because of polymorphism. Remember, with polymorphism, what you want to do is use the superclass as a reference type, polymorphic argument, return type, or array, so your code is more flexible. Without this, you'd have to make a subclass-specific method for every subclass. So with abstract classes, you are able to define the protocol which says that "If this superclass reference type has this method, then ALL subtypes have it as well, so allow me to use this subtype in the place of the supertype".

#### All abstract methods have to be implemented

The first concrete class in the inheritance must implement all abstract methods. If the abstract method is passed down to another abstract class, it does not have to implement it, but it can. If the abstract class `Canine` implements an abstract method that is inherited from `Animal`, then `Dog` does not need to implement it anymore. But if `Canine` says nothing about the abstract methods from `Animal`, `Dog` has to implement all of its abstract methods.

### `Object`: the ultimate superclass

Every class in Java extends class `Object`. This is how the developer of Java made the `ArrayList` take in objects they didn't even know about as arguments to `ArrayList` methods. Any class that doesn't explicitly extend another class, extends `Object`. 

The `Object`class serves two main purposes: to act as a polymorphic type for methods that need to work on any class, and to provide real method code that all Java objects need at runtime. 

#### `Object` methods
These are methods that EVERY object has.

1. `equals(Object o)` - tells you if two objects are considered 'equal'

```java
Dog d = new Dog();
Cat c = new Cat();

d.equals(c); // false
```

2. `getClass()` - gives you back the class that object was instantiated from
```java
Cat c = new Cat();
c.getClass(); // Cat
```

3. `hashCode()` - prints out a hashcode for the object (a unique ID)
```java
Cat c = new Cat():
c.hashCode(); // 8202111
```

4. `toString()` - prints a string message with the name of the class and some other number 
```java
Cat c = new Cat();
c.toString(); // Cat@7d277f
```

### `Object` instances

It's acceptable to make `Object` instances because there are times when you'd want a generic object to use. A lightweight object. The most common use of an instance of type `Object` is for thread synchronization. 

### The price of using polymorphic references of type `Object`

You can't simply use `Object` for all your ultra-flexible polymorphic arguments and return types. `ArrayList` example of why:

```java
ArrayList<Dog> dogList = new ArrayList<Dog>();
Dog aDog = new Dog();
dogList.add(aDog);
Dog anotherDog = dogList.get(0); // this works
```

```java
ArrayList<Object> dogList = new ArrayList<Object>();
Dog aDog = new Dog();
dogList.add(aDog);
Dog anotherDog = dogList.get(0);
// won't compile because the ArrayList is designed to hold any type of Object, the get() methods returns type Object and not Dog
// objects come out of the list as generic instances of class Object, the compiler cannot assume things
```

![](@attachment/Clipboard_2022-07-26-10-39-41.png)




