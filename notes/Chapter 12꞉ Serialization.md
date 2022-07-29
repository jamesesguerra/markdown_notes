---
attachments: [Clipboard_2022-07-29-20-41-59.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 12: Serialization'
created: '2022-07-29T12:17:05.240Z'
modified: '2022-07-29T14:26:48.277Z'
---

# Chapter 12: Serialization

__Rationale:__ Object can be flattened and inflated. Objects have state and behavior. Behavior lives in the class, but state lives within each individual object. If your program needs to save state, you can flatten the object itself and inflate it to get it back. 

### Saving Objects

There are a lot of options to save the state of your Java program. Here are two options:

__If your data will be used by only the Java program that generated it:__ Use serialization
Write a file that holds flattened data. Then have your program read the serialized objects from the file and inflate them back into living objects.

__If your data will be used by other programs:__ Write a plain text file
Write a file with delimiters that other programs can parse. For example, a tab-delimited file that a database application can use.

But regardless of the method you use, the fundamental I/O techniques are the same: write some data to something, and usually that something is either a file on a disk or a stream coming from a network connection. Reading the data is the same process in reverse. 

Serialized files are much harder for humans to read, but it's much easier (and safer) for your program to restore objects from serialization thatn from a text file.

#### Writing a serialized object to a file

1. Make a `FileOutputStream`
The `FileOutputStream` object knows how to connect to and create a file. If the file you provide it doesn't exist, it will be created automatically. 
```java
FileOutputStream fileStream = new FileOutputStream("MyFile.ser");
```

2. Make an `ObjectOutputStream`
The `ObjectOutputStream` lets you write objects, but it can't directly connect to a file. It needs to be fed a "helper". This is called "chaining" one stream to another.
```java
ObjectOutputStream os = new ObjectOutputStream(fileStream);
```

3. Write the object
```java
os.writeObject(obj1);
os.writeObject(obj2);
```

4. Close the `ObjectOutputStream`
Closing the stream at the top closes the ones underneath, so the `FileOutputStream` (and the file) will close automatically.
```java
os.close();
```

### Data moves in streams from one place to another

Streams are either connection streams or chain streams.

The Java I/O API has __connection__ streams that represent connections to destinations and sources such as files or network sockets, and __chain__ streams that work only if chained to other streams. 

Often, it takes at least two streams hooked together to do something useful -- one to represent the connection and another to call methods on. You need two because connection streams are usually too low-level. `FileOutputStream` (a connection stream) has methods for writing bytes. But we want to write objects so we need a higher-level chain stream.

![](@attachment/Clipboard_2022-07-29-20-41-59.png)

### Serialized objects

What happens to an object when it's serialized?

1. Objects on the heap save state -- the value of the object's instance variables. These values make one instance of a class different from another instance of the same class. 

2. Serialized objects __save the values of the instance variables__, so that an identical instance (object) can be brought back to life on the heap.

#### Serialization saves the entire object graph

When an object is serialized, all the objects it refers to from instance variables are also serialized. And all those objects those objects refer to are serialized as well and so on...

#### The `Serializable` interface

If you want your class to be serializable, implement `Serializable`. This interface is known as a marker interface because the interface doesn't have methods to implement. Its sole purpose is to announce that the class implementing it is serializable. If any superclass of a class is serializable, the subclass is automatically serializable even if the subclass doesn't explicitly declare it.

```java
import java.io.* // Serializable is in the java.io package

publc class Box implements Serializable {
  public int width; // two variables to be saved
  public int height;

  public static void main (String[] args) {
    Box myBox = new Box();
    myBox.width = 4;
    myBox.height = 4;

    // I/O operations can throw exceptions
    try {
      // write obj
    } catch(Exception e) {
      e.printStackTrace();
    }
  }
}
```

#### All or nothing

Either the entire object graph is serialized correctly or serialization fails. You can't serialize a `Pond` object if its `Duck` instance refuses to be serialized (by not implementing `Serializable`).

#### `transient`

Instance variables should be marked as `transient` if it can't or shouldn't be saved. This instance variable will be skipped by the whole serialization process.

```java
public class Chat implements Serializable {
  transient String currentID;
}
```

### Deserialization

The point of serializing an object is so that you can restore it back to its original state at a later time, in different "run" of the JVM. Deserialization is a lot like serialization in reverse.

1. __Make a `FileInputStream`__
If the filename doesn't exist, you'll get an exception. 
```java
FileInputStream fileStream = new FileInputStream("MyGame.ser");
```

2. __Make an `ObjectInputStream`__
`ObjectInputStream` lets you read objects, but it can't directly connect to a file as well. Hence the need for chaining.
```java
ObjectInputStream os = new ObjectInputStream(fileStream);
```

3. __Read the objects__
Each time you invoke the `readObject()` method, you get the next object in the stream. So you'll read them back in the same order in which they were written. You'll get an exception if you try to read more objects than you wrote.
```java
Object one = os.readObject();
```

4. __Cast the objects__
The return value of `readObject()` is type `Object`, so you have to cast it back to the type you know it really is.
```java
GameCharacter elf = (GameCharacter) one;
```

5. __Close the `ObjectInputStream`__
```java
os.close();
```

#### Deserialization process

1. The object is read from the stream.
2. The JVM determines (through info stored with the serialized object) the object's class type.
3. The JVM attempts to find and load the object's class. If the JVM can't find or load the class, it throws an exception.
4. A new object is given space on the heap, but the serialized object's constructor does not run. If the constructor ran, it would restore the state of the object back to its original state. We want the object to be restored to the state when it was serialized, not when it was first created.
5. If the object has a non-serializable class somewhere up its inheritance tree, the constructor for that non-serializable class will run along with any constructors above that.
6. The object's instance variables are given the values from the serialized state. Transient variables are given a value of `null` for object references and defaults for primitives.

__NOTE:__ Static variables aren't serialized. Static means "one per class" not "one per object".


