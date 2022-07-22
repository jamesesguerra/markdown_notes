---
attachments: [Clipboard_2022-07-19-21-46-53.png]
tags: [Notebooks/Head First Java]
title: Chapter 1
created: '2022-07-19T13:41:53.167Z'
modified: '2022-07-20T02:50:46.019Z'
---

# Chapter 1

#### Write once run anywhere
Type source code -> Compiler compiles the code -> Java bytecode is produced -> JVM reads and runs the bytecode

#### Code structure in Java
![](@attachment/Clipboard_2022-07-19-21-46-53.png)

- Classes go in the source file, methods go in classes, statements go in methods

#### Anatomy of a class
The JVM looks at the class you provide it at the command line. Then it looks for the main method and runs everything inside it. Every Java application has to have at least one class, and one main method per application. Regardless of the size of your application, there has to be a main method to get the ball rolling. 
```java
public class MyFirstApp {
  public static void main (String[] args) {
    System.out.println("I Rule!);
  }
}
```

#### JVM vs. The Compiler
JVM
- runs bytecode
- ensures the bytecode hasn't changed before running it

The Compiler
- converts source code into bytecode, making Java a compiled language (faster than interpreted languages which does the translation at runtime)
- enforces safety features: not allowing variables to hold data of the wrong type, access violations, syntax checking
- has to allow flexibility for dynamic binding (introducing new objects that weren't know to the programmer), therefore some exceptions can still be thrown at runtime
