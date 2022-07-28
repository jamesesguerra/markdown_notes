---
attachments: [Clipboard_2022-07-27-23-11-20.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 9: Constructors and Garbage Collection'
created: '2022-07-27T11:52:19.360Z'
modified: '2022-07-28T06:30:50.812Z'
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

### Space for an object's superclass parts

Every object holds not just its own declared instance variables, but also everything from its superclasses (which, at a minimum, means class `Object` since every class extends `Object`).

So when an object is created, the object gets space for _all_ the instance variables, from all the way up the inheritance tree. A superclass might have setter methods encapsulating a private variable, but that variable has to live somewhere. When an object is created, it's almost as though multiple object materialize -- the object being `new`'d and one object per each superclass. It's better to think of it as the object being created having layers of itself representing each superclass. There is only one object on the heap, but it contains its subclass parts and all the parts of its superclass/es.

![](@attachment/Clipboard_2022-07-27-23-11-20.png)

### The role of superclass constructors

_All the constructors in an object's inheritance tree must run when you make a new object._ That means every superclass has a constructor, and each constructor up the hierarchy runs at the time an object of a subclass is created. 

Saying `new` on a subclass starts the whole constructor chain reaction. Even abstract classes have constructors. The super constructors run to build out the superclass parts of the object. A subclass might inherit methods that depend on superclass state (the value of instance variables in the superclass). For an object to be fully-formed, all the superclass parts of itself must be fully-formed, so that's why the superclass constructors must run. Even if the superclass has instance variables that the subclass doesn't inherit (if the variables are private), the subclass still depends on superclass methods (superclass getters and setters) that _use_ those variables.

### Invoking a superclass constructor

The only way to call a super constructor is by calling `super()`. The compiler will put in a call to `super()` if you don't in one of two ways:

1. If you don't provide a constructor, the compiler puts in one that looks like this:
```java
public className() {
  super();
}
```

2. If you _do_ provide a constructor but don't put in a call to `super()`, the compiler will put a call to `super()` in each of your overloaded constructors. The compiler-inserted call to `super()` is always a no-arg constructor. 

A call to `super()` in your constructor puts the superclass constructor on the top of the stack. That superclass constructor will then call its superclass constructor as well until the `Object` constructor is on the top of the stack.

The superclass parts of an object have to be fully-formed before the subclass parts can be constructed. A subclass object might depend on things it inherits from the superclass, so it's important that those things be finished.

__The call to `super()` must be the first statement in each constructor:__
```java
public className() {
  super();
  // some code
}
```

__Superclass constructors with arguments__

You can use a subclass constructor to call the superclass constructor with arguments. You can do this if you want to set the instance variables of the superclass from the arguments received by the subclass constructor.

```java
// subclass constructor
public Dog(String name) {
  super(name);
}

// superclass constructor
public Canine(String name) {
  dogName = name;
}
```

### Invoking one overloaded constructor from another 

If you have overloaded constructors that basically do the same thing, you can use `this()` to call a constructor from another overloaded constructor in the same class. This reduces duplicate code by having the initially-invoked constructor to call "The Real Constructor" with the bulk of the constructor code (possibly including the call to `super()`) and let it finish the job of construction.

__Every constructor can have a call to `super()` or `this()`, but never both. Both of them have to be the first statement in a constructor.__

```java
// duplicate code

public Dog() {
  // set default values
  size = 25;
  name = "Fido";
}

public Dog(int s, String n) {
  size = s;
  name = n;
}
```

```java
// no duplicate code with this()

public Dog() {
  this(25, "Fido"); // calls the overloaded constructor with the signature 'Dog(int, String)'
}

public Dog(int s, String n) {
  size = s;
  name = n;
}
```

### Object lifespan

An object's life depends on the life of references referring to it. If the reference is "alive", the object is still on the heap. If the reference dies, the object will die.

1. A __local variable__ lives only within the method that declared the variable.
```java
public void methodName() {
  int s = 30;
  // 's' can only be used within this method
  // when this method ends, 's' disappears completely
}
```

2. An __instance variable__ lives as long as the object does. If the object is still alive, so are its instance variables.

#### Reference variables

A reference variable can be used only when it's in scope, which means you can't use an object's remote control unless you've got a reference variable that's in scope.

__How variable life affects object life__

An object is alive as long as there are live references to it. If the stack frame holding the reference gets popped off the stack, the object it's programmed to control is abandoned on the heap if that was the _only_ live reference to it. 

Once an object is eligible for GC, you don't have to worry about reclaiming the memory that object was using. If your program gets low on memory, GC will destroy some or all of the eligible objects. Your job is to make sure that you abandon objects when you're done with them.

3 ways to get rid of an object's reference:

1. The reference goes out of scope, permanently: 
```java
void go() {
  Life z = new Life(); // reference 'z' dies at the end of the method
}
```

2. The reference is assigned another object:
```java
Life z = new Life(); // this object is abandoned when 'z' is reprogrammed to another object
z = new Life();
```

3. The reference is explicitly set to `null`:
```java
Life z = new Life(); // this object is abandoned when 'z' is deprogrammed
z = null; 
```



 
