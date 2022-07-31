---
tags: [Notebooks/Head First Java]
title: 'Chapter 13: Threads'
created: '2022-07-31T14:00:37.051Z'
modified: '2022-07-31T14:23:14.261Z'
---

# Chapter 13: Threads

__Rationale:__ In Java, you can walk and chew gum at the same time.

### Chat App Option Three

You want something to run continuously, checking messages from the server but without interrupting the user's ability to interact with the GUI (send messages). You want something behind the scenes to keep reading in new input from the server.

This means you need a new thread, a new, separate stack. You want everything you did in the send-only version to work the same way, while a new process runs along side that reads information from the server.

Well, not quite. Unless you have multiple processors on your computer, each new Java thread is not actually a separate process running on the OS. But it almost _feels_ as though it is.

### Multithreading in Java

Java has multiple threading built right into the language. It's easy to make a new thread of execution:
```java
Thread t = new Thread();
t.start();
```
By creating a new `Thread` object, you've launched a separate thread of execution with its very own call stack.

__The problem:__ that thread doesn't actually do anything, so the thread dies virtually the instant it's born. When a thread dies, it's new stack disappears again.

The key component that's missing is the thread's job. You need the code that you want to have run by a separate thread. Multiple threading in Java means that you have to look at both the _thread_ and the _job_ that's run by the thread. And also the `Thread` class in the `java.lang` package.

### threads and `Thread`

A thread is a separate thread of execution. That means a separate call stack. Every Java application starts up a main thread -- the thread that puts the `main()` method on the bottom of the stack. The JVM is responsible for starting the main thread. As a programmer, you can write code to start other threads of your own.

`Thread` is a class that represents a thread of execution. It has methods for starting a thread, joining one thread with another, and putting a thread to sleep.

### What it means to have more than one call stack

With more than one call stack, you get the _appearance_ of having multiple things happen at the same time. In reality, only a true multiprocessor system can actually do more than one thing at a time, but with Java threads, it can _appear_ that you're doing several things simultaneously. In other words, execution can move back and forth between stacks so rapidly that you feel as though all stacks are executing at the same time. 

Remember, Java is just a process running on your underlying OS. So first, Java _itself_ has to be the 'currently executing process' on the OS. But once Java gets its turn to execute, exactly what does the JVM run? Whatever is on the top of the currently-running stack. And in 100 milliseconds, the currently executing code might switch to a different method on a different stack.

One of the things a thread must do is keep track of which statement (of which method) is currently executing on the thread's


