---
attachments: [Clipboard_2022-07-19-21-46-53.png]
tags: [Notebooks/Head Start Java]
title: Chapter 1
created: '2022-07-19T13:41:53.167Z'
modified: '2022-07-19T13:53:00.333Z'
---

# Chapter 1

#### Write once run anywhere
Type source code -> Compiler compiles the code -> Java bytecode is produced -> JVM reads and runs the bytecode

#### Code structure in Java
![](@attachment/Clipboard_2022-07-19-21-46-53.png)

- Classes go in the source file, methods go in classes, statements go in methods

#### Anatomy of a class
The JVM looks at the class you provide it at the command line. Then it looks for the main method and runs everything inside it. Every Java application has to have at least one class, and one main method per application.
```java
public class MyFirstApp {
  public static void main (String[] args) {
    System.out.println("I Rule!);
  }
}
```
