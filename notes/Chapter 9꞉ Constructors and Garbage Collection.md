---
tags: [Notebooks/Head First Java]
title: 'Chapter 9: Constructors and Garbage Collection'
created: '2022-07-27T11:52:19.360Z'
modified: '2022-07-27T13:24:01.568Z'
---

# Chapter 9: Constructors and Garbage Collection

### The Stack and the Heap: where things live

We care about two areas of memory: the one where objects live (the heap), and the one where method invocations and local variables live (the stack). When a JVM starts up, it gets a chunk of memory from the underlying OS and uses it to run your program. With good programming, you won't have to care about this.

### The two kinds of variables we care about

- __Instance Variables__
These are variables declared inside a class but not inside a method. They represent the "fields" that each individual object has. Instance variables live inside the object they belong to.

- __Local Variables__
Local variables are declared inside a method, including method parameters. They're temporary, and live only as long as the method is on the stack (in other words, as long as the method hasn't reached the closing curly brace).

### Methods are stacked

When you call a method, the method lands on the top of the call stack. The new thing that's pushed onto the stack is the __stack frame__, and it holds the state of the method including which line of code is executing, and the values of all local variables.

The method at the top of the stack is always the currently-running method for that stack. There's only one stack, but you can add more. A method stays on the stack until the method hits its closing curly brace.

### Local variables that are objects

If the local variable is a reference to an object, only the variable (the remote control) goes on the stack. The object itself still goes on the heap.

### Instance variables on the heap

When you say `new Dog()`, Java has to make space on the Heap for that `Dog`. But how much space? Enough to house all of the object's instance variables. Instance variables live inside the object they belong to.

The values of an object's instance variables live inside the object. If the variables are all primitive, Java makes space for the instance variables based on the primitive type. 

But what if the instance variables are objects? When the new object has instance variables that are object references rather than primitives, does the object need space for all the objects it holds references to? Not exactly. While Java has to make space for the instance variable values, the values that the object references hold are just bits representing a way to get to the object itself, ie. the remote control. 

When does the `Owner` object get space on the heap? Only when the reference variable is assigned a new `Owner` object.

```java
private Owner o; // no object is made yet
private Owner o = new Owner(); // object is made on the heap now
```

### Object creation & constructors

Step 2 of object declaration and assignment (`new Dog()`) has remained a mystery. 

When we say `new Dog();`, we're calling the `Dog` constructor. A constructor has the code when you say `new`. Or in other words, the code that runs when you instantiate an object.

The only way to invoke a constructor is with the keyword `new` followed by the class name. The JVM finds that class and invokes its constructor.

If you don't write a constructor for your class, the compiler writes one for you. Default constructor:

```java
public Dog() {
  
}
```

It's different from a method because it's name is the same as the class name and there is no return type. Constructors cannot have a return type.

#### More on constructors

The key feature of a constructor is that it runs _before_ the object can be assigned to a reference. This means that you get a chance to step in and do things before the object is ready for use. In other words, before anyone can use the remote control for an object, the object has a chance to help construct itself. So even though the compiler already writes one for you, you can write code to help get your object ready for use.

#### Initializing the state of a new `Dog`

Constructors are commonly used to initialize the state of an object. In other words, to make and assign values to the object's instance variables,
```java
public Dog() {
  size = 30;
}
```

Initilalizing the object with state using a constructor with arguments:
```java
public class Dog {
  int size;

  public Dog(int dogSize) {
    size = dogSize;
  }
}
```
This is better than instantiating the object and then setting its size after with a setter method.

```java
// bad, the Dog object is alive at one point in the code but without a size
Dog d = new Dog();
dog.setSize(30) 

// good, size is already set upon creation
Dog d = new Dog(30);
```

### Overloaded constructors

What if you initially don't know what the size of the `Dog` should be? You need to provide two options for making a `Dog` -- one where you supply a size and one where you don't supply a size and get a default `Dog` size. 

You can do this with overloaded constructors:
```java
public class Dog {
  int size;

  public Dog() {
    // supply default size
    size = 10;
  }

  public Dog(int dogSize) {
    // use dogSize parameter
    size = dogSize;
  }
}
```

The compiler will only create a no-arg constructor for you if you don't say anything at all about constructors. So you'll still have to write a no-arg constructor if you write a constructor that takes arguments. 

Also, if you have more than one constructor in a class, the constructors MUST have different argument lists. It's the variable type (int, Dog, etc.) and order that matters, not the name of the parameters. You _can_ have two constructors that have identical types as long as the order is different.






