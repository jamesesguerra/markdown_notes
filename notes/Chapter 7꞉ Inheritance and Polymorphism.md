---
attachments: [Clipboard_2022-07-23-13-31-57.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 7: Inheritance and Polymorphism'
created: '2022-07-23T02:01:06.972Z'
modified: '2022-07-23T07:11:56.270Z'
---

# Chapter 7: Inheritance and Polymorphism

__Rationale:__ Planning programs with the future in mind. Writing more extensible and flexible code.

### Inheritance

Designing with inheritance: you put __common code__ in a class and then tell other _more specific_ classes that the common (more abstract) class is their _superclass_. That is, the __subclass__ _extends_ the __superclass__. This relationship means that the subclass inherits all the members (instance variables and methods) of the superclass.

Apart from the members that the subclass inherits from its superclass, it can also add instance variables and methods of its own. It can also __override__ the methods it inherits from the superclass to change or extend its behavior. On the other hand, instance variables don't need to be overriden because they don't define any special behavior. 

#### Designing an inheritance tree (using the _Animal Simulation Program_ as an example)

We want to design the tree in a way that other programmers can easily add new classes to the program at any time.

1. Look for objects that have common attributes and behaviors (extracting out common behavior).
  - What does a tiger, lion, hippo, dog, bird, wolf, cat have in common? How are these types related?
2. Design a class that represents the common state and behavior.
  - The types are all animals, so the common superclass would be `Animal`. Define all the instance variables and methods all subclasses of `Animal` might need.
3. Decide if a subclass needs behaviors (method implementations) that are specific to that particular subclass type. See if there are methods that should be overriden by individual subclasses. 
  - All animals will need an `eat()` method. However, not all animals eat the same way. You _can_ define the `eat()` method to use one of its instance variables to customize its behavior for every animal, but that's not very specialized. These methods should be overriden by the individual subclasses of `Animal`. For example, a `Lion` subclass should override the `eat()` method to get more lion-specific behavior.
4. Look for more opportunities for abstraction by finding two or more subclasses that might need common behavior. In other words, group together subclasses that have common behavior.
  - A lion, tiger, and cat are all felines, maybe there are instance variables or methods that all three subclasses could use. 
5. Finish the class hierarchy.
  - `Feline`s and `Canine`s could use a common `roam()` method that they inherit from the `Animal` superclass. These `roam()` methods are overridden in each subclass since felines and canines roam differently.

  ![](@attachment/Clipboard_2022-07-23-13-31-57.png)

#### Which method is called?

When you call a method on an object reference, you're calling the most specific version of the method for that object type. In other words, the method that is lowest on the class hierarchy / inheritance tree wins. If the JVM doesn't find a version of the method being called on a subclass, it starts walking back up the inheritance tree until it finds a match. 


#### IS-A and HAS-A tests

When you want to know if one class extends another, apply the __IS-A__ test. Ask the question, __"Does it make sense to say type x IS-A type y?"__

```sh
✔️ Cat is a feline.
❌ Tub is a bathroom.
```

Although `Tub` doesn't extend `Bathroom`, they _are_ related. `Tub` and `Bathroom` are joined by a __HAS-A__ relationship. Does it make sense to say "Bathroom has a tub?" If yes, `Bathroom` has a `Tub` instance variable. 

- __IS-A__ - for testing whether one class extends another
- __HAS-A__ - for testing whether one class should be an instance variable of another

If your inheritance tree is well-designed, the IS-A test should work anywhere in the inheritance tree. That is, the IS-A test should work when you ask any subclass if it IS-A any of its superclasses. If the test passes, that simply means the subclass can do anything the superclass can do, and possibly more. It isn't important that a subclass possibly overrides some of the behavior of the superclass, what matters is that it _can_ do that particular behavior.

#### Using both the superclass and subclass version of a method

If you don't want to completely replace/override a method of a superclass and you just want to add more stuff to it, use the keyword `super`. This keyword calls the superclass version of the method. It's like saying "first go run the superclass version, then come back and finish with my own code". 

This makes it so that you can design your superclasses in a way that they can work for any subclass, even if they may need to append more code to it. 

```java
public void roam() {
  super.roam(); // calls the inherited version of roam()
  // my own roam stuff
}
```

#### How to know what a subclass can inherit from its superclass

A subclass can inherit members of the superclass. These members include instance variables and methods. A superclass can choose whether or not it wants a subclass to inherit a particular member. This is done through access modifiers:

__Access Level Modifiers (from most to least restrictive):__
- `private`
- `default`
- `protected`
- `public`

Access levels control who sees what. 

__public__ members are inherited
__private__ members are not inherited

* When a subclass inherits a member, __it's as if the subclass defined the member itself__.


