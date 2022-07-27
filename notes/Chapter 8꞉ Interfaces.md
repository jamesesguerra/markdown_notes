---
tags: [Notebooks/Head First Java]
title: 'Chapter 8: Interfaces'
created: '2022-07-26T13:36:13.221Z'
modified: '2022-07-27T11:50:44.044Z'
---

# Chapter 8: Interfaces

## Interfaces: the key to allowing subclasses to inherit from multiple superclasses

### What if you want to change the contract?

How would you reuse the `Dog` class in the Animal Simulation Program for a Pet Shop Program?

#### Option 1: Put "pet" methods into the `Animal` class.

The downside to this is that although pet classes would be able to take advantage of inheritance and polymorphism, there are some `Animal` subclasses that don't need the pet methods. It wouldn't make sense for a `Lion` or a `Hippo` subclass to have those pet methods.

#### Option 2: Put "pet" methods into the `Animal` class but make them abstract, forcing the pet classes to override them

The downside to this is that even though the non-pet subclasses have the option to implement an empty method for those pet methods, they will still have the pet methods.

#### Option 3: Put "pet" methods only in the subclasses that need them

The downside to this is that there is no protocol enforced because the subclasses aren't inheriting the methods. They are each implementing the same method signature but programmers could get this wrong (the return type, arguments, method name, etc.). You also cannot take advantage of polymorphism since the `Animal` superclass wouldn't know about the pet methods.

##### What we really need:
- A way to have pet behavior in __just__ the pet classes.
- A way to guarantee that all pet classes have the same method defined.
- A way to take advantage of polymorphism so that pets can have their pet methods called.

#### The Deadly Diamond of Death

This can be solved by having two superclasses at the top which the pet classes can inherit from. However, the problem with this "two superclasses" approach is the DDD. If a subclass inherits from two superclasses that each have an overridden method of the same name, if this inherited method is called by an instance of the subclass, Java wouldn't know which inherit method should be run.

### `interface`: a 100% pure abstract class

Java interface's solve the problem of the DDD while giving you the polymorphic benefits of multiple inheritance. The way it side-steps the DDD is simple: __it makes all the methods abstract.__ That way, the subclass __must__ implement the methods, so at runtime the JVM won't be confused about which of the two inherited versions it's supposed to call.

To define an interface:
```java
public interface Pet {...}
```

To implement an interface:
```java
public class Dog extends Canine implements Pet {...}
```

Making the `Pet` interface:
```java
public interface Pet {
  public abstract void beFriendly();
  public abstract void play();
}

// interface methods are implicitly already public and abstract

// good practice:
public interface Pet {
  void beFriendly();
  void play();
}
```

### The benefits of interfaces

Even though interfaces don't buy you the benefits of multiple inheritance because it does not provide method implementation, what it buys you is the protocol you can use for polymorphism. You can use interface reference types and pass it any object that implements the interface just like how you'd pass an object to a reference variable that is its superclass. That is, when you use an interface as a polymorphic type, the objects can be _anywhere_ in the inheritance tree. When using abstract classes as a polymorphic type, the objects have to be one of its subclasses in the inheritance tree. 

Moreover, with interfaces, a class doesn't have to come from just one inheritance tree. A class can extend one class and implement an interface. And then another class might implement the same interface but come from a completely different inheritance tree. You get to treat objects by the role they play and not by the parent class that defines them. 

### Multiple interfaces

A class can implement multiple interfaces:
```java
public class Dog extends Canine implements Pet, Saveable, Paintable {...}
```

### Subclass, abstract class, or interface?

- __subclass:__ make a subclass only when you need to make a __more specific__ version of a class and need to override or add new behavior
- __abstract class:__ use an abstract class if you want to define a __template__ for a group of subclasses, and you have at least some implementation code that all subclasses could use
- __interface:__ use an interface when you want to define a __role__ that other classes can play, regardless of where those classes are on the inheritance tree

### Family values
 
 Java weighs in on family values: single parents only. __A Java class can only have one parent and that parent defines who you are. But you can implement multiple interfaces, and those interfaces define roles you can play.__




