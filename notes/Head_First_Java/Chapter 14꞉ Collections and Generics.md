---
attachments: [Clipboard_2022-08-02-20-31-17.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 14: Collections and Generics'
created: '2022-08-02T04:52:57.750Z'
modified: '2022-08-04T13:08:55.104Z'
---

# Chapter 14: Collections and Generics

__Rationale:__ With Java, you have all the tools for collecting and manipulating your data without having to write your own algorithms. The Java Collections Framework has a data structure that should work for virtually anything you'll need to do.

### Alphabetically sorting a list

__Challenge:__ sort a list of songs in alphabetical order

The `ArrayList` class does not have a `sort()` method. Fortunately, although the `ArrayList` is the one you'll use most often, there are others for special occasions. Some of the key classes include:

- __TreeSet__ - keeps the elements sorted and prevents duplicates
- __HashMap__ - lets you store and access elements as name/value pairs
- __LinkedList__ - makes it easy to create structures like stacks and queues
- __HashSet__ - prevents duplicates in the collection, and given an element, can find that element in the collection quickly
- __LinkedHashMap__ - like a regular `HashMap`, except it can remember the order in which elements (name/value pairs) were inserted, or it can be configured to remember the order in which elements were last accessed.

#### You could use a `TreeSet`...

If you put all the `String`s into a `TreeSet` instead of an `ArrayList`, the `String`s would automatically land in the right place, alphabetically sorted. That's great when you need a _set_ or when you know that the list must _always_ stay sorted automatically.

On the other hand, if you don't need the list to stay sorted, `TreeSet` might be more expensive than you need -- every time you insert into it, it has to take its time figuring out where in the tree the new element must go. With `ArrayList`s, inserts are really fast because the new element just goes in at the end.

#### or you could use `Collections.sort()`

The `Collections.sort()` method sorts a list of `String`s alphabetically. It takes a `List` as an argument, and since `ArrayList` implements the `List` interface, you can pass it into the method.

```java
Collections.sort(songList);
```


### Sorting objects 

Store `Song` objects in an `ArrayList`:
```java
ArrayList<Song> songList = new ArrayList<>();
```

__The problem:__ the `sort()` method doesn't know what makes one `Song` greater or less than another `Song`. You need some way to tell the `sort()` method that it needs to use the title.

But first, let's find out why the compiler won't let us pass a `Song` `ArrayList` to the `sort()` method. 

## Generic types

The `sort()` method of the `Collections` class is declared differently because it makes heavy use of __generics.__

### Generics means more type-safety

All of the code you write that deals with generics will be collection-related code. The main point of generics is to let you write type-safe collections. In other words, code that makes the compiler stop you from putting a `Dog` into a list of `Duck`s.

Before generics, the compiler doesn't care what you put into a collection, because all collection implementations were declared to hold type `Object`. You could put anything in any `ArrayList`. It was like all `ArrayLists` were declared as `ArrayList<Object>`.

__Without generics:__ 
- Objects go IN as a reference to `Fish`, `Dog`, `Cat` and `Lion` objects and come OUT as a reference of type `Object`.
- The compiler would happily let you put a `Fish` into an `ArrayList` that was supposed to hold only `Dog`s.

__With generics:__ 
- Objects go IN as a reference to only `Fish` objects and come out as a reference of type `Fish`.
- You can create type-safe collections where more problems are caught at compile-time instead of runtime. 

### Learning generics

Of the many things you can learn about generics, there are really only three that matter to most programmers:

1. __Creating instances of generified classes (like `ArrayList`)__
When you make an `ArrayList`, you have to tell it the type of objects you'll allow in the list, just as you do with plain old arrays.
```java
new ArrayList<Song>();
```

2. __Declaring and assigning variables of generic types__
How does polymorphism work with generic types? If you have an `ArrayList<Animal>` reference variable, can you assign an `ArrayList<Dog>` to it? What about a `List<Animal>` reference? Can you assign an `ArrayList<Animal>` to it?
```java
List<Song> songList = new ArrayList<Song>();
```

3. __Declaring (and invoking) methods that take generic types__
If you have a method that takes as a parameter an `ArrayList` of `Animal` objects, what does that really mean? Can you also pass it an `ArrayList` of `Dog` objects? 
```java
void foo(List<Song> list) 
x.foo(songList)
```

__NOTE:__ You probably won't need to learn how to create your own generic classes.

### Using generic classes

Generic classes allow you to have the ability to have one class that is flexible for many different types. With generics, you don't need to explicitly say what type are the instance variables of that class in the class definition. You can pass it in instead. 

```java
// whatever type you pass in will be substituted in for all the 'T's in the class
// T can be anything
public class Printer<T> {...}
```

#### Bounded generics
You can restrict the type argument that you pass to the type parameter of the generified class.
```java
// you can only pass in types that are subtypes of Animal
public class Printer<T extends Animal> {...}
```

#### Understanding `ArrayList` documentation

```java
public class ArrayList<E> extends AbstractList<E> implements List<E> ... {
  public boolean add(E o)
  // more code
}
```

- The "E" is a placeholder for the REAL type you use when you declare and create an `ArrayList`.
- `ArrayList` is a subclass of `AbstractList`, so whatever type you specify for the `ArrayList` is automatically used for the type of `AbtractList`
- The type (the value of `<E>`) becomes the type of the `List` interface as well.
- The important part: whatever `E` is determines what kind of things you're allowed to add to the `ArrayList`.

The "E" represents the type used to create an instance of `ArrayList`. When you see an "E' in the `ArrayList` documentation, you can do a mental find/replace to exchange it for whatever `<type>` you use to instantiate `ArrayList`.

So, `new ArrayList<Song>` means that `E` becomes `Song`, in any method or variable declaration that uses `E`.

![](@attachment/Clipboard_2022-08-02-20-31-17.png)

The `E` is replaced by the real type (also called the type parameter) that you use when you create the `ArrayList`. 

__Convention:__ use "T" instead of "E" unless you're specifically writing a collection class, where you'd use "E" to represent the "type of the **E**lement the collection will hold".

### Using generic methods

A generic class means that the class declaration includes a type parameter. A generic method means that the method declaration uses a type parameter in its signature. You can use type parameters in a method in several different ways:

1. __Using a type parameter defined in the class declaration__
```java
public class ArrayList<E> extends AbstractList<E> {
  // you can use E here cause its already been defined as part of the class
  public boolean add(E o)
}
```

2. __Using a type parameter that was not defined in the class declaration__
```java
public <T extends Animal> void takeThing(ArrayList<T> list)
```

This:
```java
public <T extends Animal> void takeThing(ArrayList<T> list) {...}
```

Is not the same as this:
```java
public void takeThing(ArrayList<Animal> list) {...}
```

Both are legal but they're different. 

The first one, where `<T extends Animal>` is part of the method declaration, means that any `ArrayList` declared of a type that is `Animal`, or one of `Animal`'s subtypes, is legal. So you could invoke the top method using an `ArrayList<Dog>`, `ArrayList<Cat>`, etc.

The bottom one means that only an `ArrayList<Animal>` is legal. In other words, while the first version takes an `ArrayList` of any type that is a type of `Animal`, the second version takes only an `ArrayList` of type `Animal`

### `Comparable`
The reason why the `sort()` method of the `Collections` class cannot take in the `ArrayList` of songs is because the method only takes in `List`s that implement the `Comparable` interface.

```java
public interface Comparable<T> {
  int compareTo(T o) {...}
}
```

#### New and improved `Song` class

```java
public class Song implements Comparable<Song> {
  public int compareTo(Song s) {
    return title.compareTo(s.getTitle());
  }
}
```

#### Using a custom comparator

What if you wanted to sort the list by artist as well. The `sort()` method of the `Collections` class has an overloaded method to take something called a Comparator. It's a separate interface:
```java
public interface Comparator<T> {
  int compare(T o1, T o2) {...}
}
```

### Dealing with duplicates

You need a Set instead of a List.

- __LIST__ - when sequence matters; collections that know about index position; you can have more than one element referencing the same object
- __SET__ - when uniqueness matters; collections that do not allow duplicates
- __MAP__ - when finding something by key matters; key-value pairs; you can have to keys referencing the same value, but you cannot have duplicate keys

#### Using a HashSet
```java
HashSet<Song> songSet = new HashSet<>();
songSet.addAll(songList);
```

### Object equality

#### reference equality vs. object equality

- __reference equality__ 
  - two references pointing to one object on the heap 
  - if you call the `hashCode()` method on both references, you'll get the same result
  - use the `==` operator

- __object equality__
  - two references, two objects on the heap, but the objects are considered meaningfully equivalent
  - if you want to treat two different objects as equal, you must override both the `hashCode()` and `equals()` methods inherited from the class `Object`

#### Overriden `equals` and `hashCode` method of `Song`

```java
public boolean equals (Object aSong) {
  Song s = (Song) aSong;
  return getTitle().equals(s.getTitle());
} 

public int hashCode() {
  return title.hashCode();
}
```

### TreeSet: sorted set

If you want a set to stay sorted, use the TreeSet. It prevents duplicates while keeping the list sorted.

It works like the `sort()` method in that if you make it using its no-arg constructor, the TreeSet uses each object's `compareTo()` method for the sort. But you also have the option of passing a Comparator to the TreeSet constructor.

#### TreeSet elements must be comparable

You have to tell the TreeSet how objects should be sorted. One of these things must be true:

- The elements in the list must be of a type that implements `Comparable`
- You use the TreeSet's overloaded constructor that takes a `Comparator`

### Maps

Maps are part of Java collections but they don't implement the Collection interface. Use maps if you want a collection that acts like a property list, where you give it a name and it gives you back the value. Although keys will often be Strings, they can be any Java object. 

HashMaps need two type parameters, one for the key and one for the value:
```java
HashMap<String, Integer> scores = new HashMap<>();
scores.put("Kathy", 42);
scores.put("Jason", 24);

scores.get("Kathy"); // 42
```










