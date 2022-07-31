---
tags: [Notebooks/Head First Java]
title: 'Extra 1: Inner Classes'
created: '2022-07-31T05:42:23.444Z'
modified: '2022-07-31T06:24:15.675Z'
---

# Extra 1: Inner Classes

You can have one class nested inside another. Just make sure that the definition for the inner class is inside the curly braces of the outer class. 

__Simple inner class:__
```java
class MyInnerClass {
  
  class MyInnerClass {
    void go() {
      ...
    }
  }

}
```

An inner class gets a special pass to use the outer class's stuff. Even the private stuff. The inner class can use those private members of the outer class as if the members were defined in the inner class. This is what's handy about inner classes: they have most of the benefits of a normal class, but with special access rights.

__Inner class using an outer variable:__

```java
class MyOuterClass {
  private int x;

  class MyInnerClass {
    void go() {
      // use 'x' as if it were a variable of the inner class
      x = 42;
    }
  }
}
```

__An inner class must be tied to an outer class instance__

An inner object must be tied to a specific outer object on the heap. An arbitrary instance of the inner class cannot access the methods and variables of any instance of the outer class.

1. Make an instance of the outer class
2. Make an instance of the inner class, by using the instance of the outer class.
3. The outer and inner objects are now intimately linked.

__Making an instance of an inner class__
If you instantiate an inner class from code within an outer class, the instance of the outer class is the one that the inner object will 'bond' with. 

Code in an outer class can instantiate one of its own inner classes, in exactly the same way it instantiates any other class -- `new Inner()`.

```java
class MyOuter {
  private int x;

  MyInner inner = new MyInner();

  public void doStuff() {
    inner.go();
  }

  class MyInner {
    void go() {
      x = 42;
    }
  }
}
```




