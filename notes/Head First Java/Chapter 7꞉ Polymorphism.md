---
attachments: [Clipboard_2022-07-24-20-45-34.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 7: Polymorphism'
created: '2022-07-24T12:06:15.284Z'
modified: '2022-07-24T13:03:19.362Z'
---

# Chapter 7: Polymorphism

### Polymorphism

When you define a superclass for a group of subclasses, __any subclass of that superclass can be substituted where the superclass is expected.__ This matters because you get to take advantage of polymorphism. You get to refer to a subclass object using a reference declared as the superclass. 

#### The advantage of polymorphism

You get to write more flexible code. Code that's cleaner and much easier to extend and develop.

#### The way polymorphism works

Step back and look at the way we normally declare a reference and create an object:

1. Declare a reference variable. Tells the JVM to allocate space for a reference variable of type `Dog`. In other words, a remote control that has buttons to control a `Dog` object.
```java
Dog myDog;
```

2. Create an object. Tells the JVM to allocate space for a new `Dog` object on the GC heap.
```java
new Dog();
```

3. Link the reference and the object. Assigns the new `Dog` object to the reference variable `myDog`. In other words, programs the remote control to point to that specific `Dog` object.
```java
Dog myDog = new Dog();
```

__The important point:__ The reference type __AND__ the object type are the same. In the example, both are type `Dog`.

![](@attachment/Clipboard_2022-07-23-20-16-11.png)

__But with polymorphism, the reference and the object can be different:__

```java
Animal myDog = new Dog();
```

__With polymorphism, the reference type can be a superclass of the actual object type.__

When you declare a reference variable, any object that extends it can be assigned to the reference variable. __This lets you create polymorphic arrays:__

```java
// Declare an array that will hold objects of type Animal
Animal[] animals = new Animal[5];

// But with polymorphism, you can put any subclass of Animal in the Animal array
animals[0] = new Dog();
animals[1] = new Cat();
animals[2] = new Lion();
animals[3] = new Wolf();

// The best polymorphic part: you get to loop through the array and call one of the Animal-class methods, 
// and every object will do the right thing
for (int animal : animals) {
  animal.eat(); // first animal is the dog, so you get the Dog's eat() method
  animal.roam();
}
```

You can also have polymorphic arguments and return types:

```java
// the 'a' parameter can take ANY Animal type as the argument
public class Vet {
  public void giveShot(Animal a) {
    a.makeNoise();
  }
}

public class PetOwner {
  public void start() {
    Vet v = new Vet();
    Dog d = new Dog();
    Cat c = new Cat();
    v.giveShot(d); // Dog's makeNoise() runs
    v.giveShot(c); // Cat's makeNoise() runs
  }
}
```

With polymorphism, you can write code that doesn't have to change when you introduce new subclasses. If you declare the reference variable,method parameter, or return type as a superclass, you can pass any subclass object at runtime.

### Extending classes

There's no such thing as a `private` class, except in the very rare case of an _inner class_. There are three things that can prevent a class from being subclassed:

1. Access control - even though a class can't be marked `private`, a class can be non-public (when you don't declare the class as `public`). A non-public class can only be subclassed only by classes in the same package.
2. `final` - a final class means that it's the end of the inheritance line. No one can extend a final class.
3. `private` constructors

* If you want to protect a certain method from being overriden, mark the method with the `final` modifier. Mark the whole class as `final` if you want to guarantee that none of the methods will ever be overriden.

### Overriding methods

When you override a method from a superclass, you're agreeing to fulfill the contract. This contract says that the arguments and return types of your overriding method must look _exactly_ like the overriden method in the superclass. __The methods are the contract.__

For polymorphism to work, the `Toaster`'s version of the overridden method from `Appliance` has to work at runtime. The compiler cares only if `Appliance` has the method you're invoking on an `Appliance` reference. But at runtime, the JVM doesn't look at the reference type, it looks at the actual `Toaster` object on the heap. So if the compiler has already approved the method call, the only way it can work if the overriding method has the same arguments and return types. In other words, the `turnOn(int level)` method in `Toaster` is not an override. The `turnOn` method that is called at runtime is that of the `Appliance` class. 

![](@attachment/Clipboard_2022-07-24-20-45-34.png)]

1. __Arguments must be the same, and return types must be compatible.__

The contract of a superclass defines how other code can use a method. Whatever the superclass method takes as an argument, the subclass overriding method must use that same argument. And whatever the superclass declares as a return type, the overriding method must declare either the same type, or a subclass type. 

2. __The method can't be less accessible.__

The access level must be the same, or friendlier. You can't, for example, override a public method and make it private.

### Overloading methods

An overloaded method is just a different method that happens to have the same name. It has nothing to do with inheritance and polymorphism. Overloading lets you make multiple versions of a method, potentially making it easier for the caller. For example, if you have a method that takes only an `int`, the calling method has to convert from, say, a `double` into an `int` before calling the method. But you can make an overloaded version of a method that takes in a `double` to make things easier for the caller. 

1. __The return types can be different.__
You can change the return types in overloaded methods as long as the argument lists are different.

2. __You can't change only the return type.__
If only the return type is different, it's not a valid overload -- the compiler will assume you're trying to _override_ the method. To overload a method, you MUST change the argument list, although you _can_ change the return type to anything.

3. __You can vary the access levels in any direction.__
You're free to overload a method with a method that's more restrictive. 
