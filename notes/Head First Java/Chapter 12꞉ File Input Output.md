---
tags: [Notebooks/Head First Java]
title: 'Chapter 12: File Input Output'
created: '2022-07-29T14:26:24.846Z'
modified: '2022-07-30T11:52:45.662Z'
---

# Chapter 12: File Input Output

### Saving data to a text file

Saving objects through serialization is the easiest way to save and restore data between runnings of a Java program. But sometimes you need to save data to a plain old text file.

Writing text data is similar to writing an object, except you write a `String` instead of an object, and you use a `FileWriter` instead of a `FileOutputStream`.

__To write a `String`:__
```java
fileWriter.write("My First string to save.");
```

```java
import java.io.*;

class WriteAFile {
  public static void main (String[] args) {
    
    try {
      FileWriter writer = new FileWriter("Foo.txt");
      writer.write("Hello World!");
      writer.close();
    } catch(IOException e) {
      e.printStackTrace();
    }
  }
}
```

### The `java.io.File` class

This class represents a file on disk, but doesn't actually represent the contents of the file. Think of a `File` object as something more like a pathname of a file rather than the actual file itself. The `File` class does not have methods for reading or writing. One very useful thing about a `File` object is that it offers a much safer way to represent a file than just using a `String` file name. For example, most classes that take a `String` file name in their constructor can take a `File` object instead. You can then verify that you've got a valid path, etc.

__A `File` object represents the name and path of a file or directory on disk, for example: /Users/James/gameFile.txt. But it doesn't represent or give access to the data in the file.__

__Some things you can do with a `File` object:__

1. Make a `File` object representing an existing file
```java
File f = new File("MyCode.txt");
```

2. Make a new directory 
```java
File dir = new File("Chapter 8");
dir.mkdir();
```

3. List the contents of a directory
```java
String [] dirContents = dir.list(); // loop through dirContents
```

4. Get the absolute path of a file or directory 
```java
System.out.println(dir.getAbsolutePath());
```

5. Delete a file or directory 
```java
boolean isDeleted = f.delete();
```

### buffers

If there were no buffers, it would be like shopping without a shopping cart. You'd have to carry each thing to your car one at a time.

Buffers give you a temporary holding place to group things until the holder (like the cart) is full. You get to make fewer trips when you use a buffer. 

A string is written to a `BufferedWriter` (a chain stream that works with characters) and then the connection is made to a file with the `FileWriter` (a connection stream that writes characters as opposed to bytes).

There's much less overhead with using buffers since it will hold all the stuff you write until it's full. Using a `FileWriter` alone writes each and every thing you pass to a file each and every time. 

```java
BufferedWriter writer = new BufferedWriter(new FileWriter(aFile));

// sending data before it's full
writer.flush();
```

### Reading from a text file

```java
import java.io.*;

class ReadAFile {
  public static void main (String[] args) {

      try {
        File myFile = new File("MyText.txt");
        FileReader fileReader = new FileReader(myFile);

        BufferedReader reader = new BufferedReader(fileReader);
      
        // variable to hold each line as it is read
        String line = null;

        while ((line = reader.readLine()) != null) {
          System.out.println(line);
        }
        reader.close();
      } catch(IOException ioe) {
          ioe.printStackTrace();
      }
  }
}
```

### `split()`

Splitting a string using a delimiter.

```java
String toTest = "What is blue + yellow?/green";
String[] result = toTest.split("/");
```
