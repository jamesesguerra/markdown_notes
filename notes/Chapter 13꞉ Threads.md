---
tags: [Notebooks/Head First Java]
title: 'Chapter 13: Threads'
created: '2022-07-31T14:00:37.051Z'
modified: '2022-08-02T04:58:58.815Z'
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

One of the things a thread must do is keep track of which statement (of which method) is currently executing on the thread's stack. It might look something like this:

1. __The JVM calls the `main()` method.__
```java
// the active thread
public static void main(String[] args) {
  ...
}
```

2. __`main()` starts a new thread. The main thread is temporarily frozen while the new thread starts running.__
```java
Runnable r = new MyThreadJob();
Thread t = new Thread(r);
t.start(); // the thread starts and becomes the active thread
Dog d = new Dog();
```

3. __The JVM switches between the new thread and the original main thread, until both threads complete.__


### Launching a new thread

1. __Make a `Runnable` object (the thread's job)__
Write a class that implements the `Runnable` interface, and that class is where you'll define the work that a thread will perform.
```java
Runnable threadJob = new MyRunnable();
```

2. __Make a `Thread` object (the worker) and give it a `Runnable` (the job)__
This tells the new `Thread` object which method to put on the bottom of the stack -- the `Runnable`'s `run()` method.
```java
Thread myThread = new Thread(threadJob);
```

3. __Start the `Thread`__
Nothing happens until you call the `Thread`'s `start()` method. When the new thread starts up, it takes the `Runnable` object's `run()` method and puts it on the bottom of the new thread's stack.
```java
myThread.start();
```

### A thread needs a job

`Runnable` is to `Thread` what a job is to a worker. A `Runnable` is the job a thread is supposed to run. A `Runnable` holds the method that goes on the bottom of the new stack: `run()`.

The `Runnable` interface defines only one public method: `public void run()`. When you pass a `Runnable` to a `Thread` constructor, you're giving the `Thread` a way to get to a `run()` method. You're giving the `Thread` its job to do.

### `Runnable` interface

To make a job for your thread, implement the `Runnable` interface
```java
public class MyRunnable implements Runnable {
  public void run() {
    // this is where you put the JOB the thread is supposed to run
    go();
  }
}
```

```java
public class ThreadTester {
  public static void main(String[] args) {
    Runnable threadJob = new MyRunnable();
    Thread myThread = new Thread(threadJob);

    myThread.start();
  }
}
```

### The 3 states of a new thread

1. __New__
A `Thread` instance has been created but not started. In other words, there is a `Thread` object, but no _thread of execution_.
```java
Thread t = new Thread(r);
```

2. __Runnable__
When you start the thread, it moves into the runnable state. This means that the thread is ready to run and just waiting for its big chance to be selected for execution. At this point, there is a new call stack for this thread.
```java
t.start();
```

3. __Running__
The thread is now the currently running thread. Only the JVM thread scheduler can make that decision. You can sometimes influence that decision, but you cannot force a thread to move from runnable to running. In the running state, a thread has an active call stack and the method on top is executing.

Once the thread becomes runnable, it can move back and forth between runnable, running, and an additional state: temporarily not runnable (aka 'blocked').

__Typical running/runnable loop__
Typically, a thread moves back and forth between runnable and running, as the JVM thread scheduler selects a thread to run and kicks it backout so another thread gets a chance.

__A thread can be made temporarily not-runnable__
The thread scheduler can move a running thread into a blocked state, for a variety of reasons. For example, a thread might be executing code to read from a Socket input stream, but there isn't any data to read. The scheduler will move the thread out of the running state until something becomes available. Or the executing code might have told the thread to put itself to sleep (`sleep()`). Or the thread might be waiting because it tried to call a method on an object, and that 'object' was locked. In that case, the thread can't continue until the object's lock is freed by the thread that has it.

All of those conditions (and more) cause a thread to become temporarily not-runnable.

### The Thread Scheduler

The thread scheduler makes all the decisions about who moves from runnable to running, and about when a thread leaves the running state. It decides who runs, and for how long, and where the threads go when the scheduler decides to kick them out of the running state.

You can't control the scheduler. Most importantly, there are no guarantees about scheduling.

The bottomline is this: __do not base your program's correctness on the scheduler working in a particular way.__ The scheduler implementations are different for different JVMs, and even running the same program on the same machine can give you different results.

So what does this mean for write-once-run-anywhere? It means to write platform-independent Java code, your multi-threaded program must work no matter how the scheduler behaves. 

The secret to almost everything is __sleep.__ Putting a thread to sleep, even for a few milliseconds, forces the currently-running thread to leave the running state, thus giving another thread a chance to run. The thread's `sleep()` method does come with one guarantee: a sleeping thread will not become the currently-running thread before the length of its sleep time has expired. 

### Putting the thread to sleep

One of the best ways to help your thread take turns (make sure other threads get a chance to run) is to put them to sleep periodically. All you need to do is call the static `sleep()` method.

```java
// sleep for 2 secs
Thread.sleep(2000);
```

The code above will knock a thread out of the running state and keep it out of the runnable state for two seconds. 

The sleep method throws an `InterruptedException` so all calls must be wrapped in a try/catch. So a sleep call really looks like this:
```java
try {
  Thread.sleep(2000);
} catch(InterruptedException ie) {
  ie.printStackTrace();
}
```

When the thread wakes up, it always goes back to the runnable state and waits for the thread scheduler to choose it to run again.

### The dark side of threads: race conditions

One potential scenario: two or more threads have access to a single object's data. In other words, methods executing on different stacks are both calling getters and setters on a single object on the heap.

#### Ryan and Monica race condition problem

Ryan and Monica agreed that neither of them will overdraw the checking account. So the procedure is, whoever wants to withdraw money must check the balance in the account before making the withdrawal. 

Race condition: Ryan needed $50 so he checked the balance in the account and saw that it was $100. No problem. So he plans to withdraw the money, but first he falls asleep. While Ryan's asleep, Monica wants to withdraw $100 and she checks the balance and it's still $100 because Ryan hasn't made his withdrawal. So she thinks no problem and makes the withdrawal. But then Ryan wakes up, completes his withdrawal, and now they're overdrawn. He went ahead and completed his transaction without checking the balance again.

__Solution:__ You can't stop Ryan from falling asleep but you can make sure that Monica can't get her hands on the bank account until after he wakes up.

#### The problem in code

Class `RyanaAndMonicaJob` have an instance variable `BankAccount` which represents the single bank account object that they access. 

The `run()` method of the threads (the job of Ryan and Monica):

```java
public void run() {
  makeWithdrawal(10);
  if (account.getBalance() < 10) {
    System.out.println("Overdrawn!");
  }
}
```

The `makeWithdrawal()` method:
```java
public void makeWithdrawal(int amount) {
  if (account.getBalance >= amount) {
    System.out.println("Withdrawing...");
    // sleep
    // then withdraw amount
  }
}
```

#### Using `synchronized`

You need to make sure that once a thread enters the `makeWithdrawal()` method, it must be allowed to finish the method before any other thread can enter. In other words, you must make sure that a thread that accesses the bank account locks it and keeps the key until they finish the transaction. You don't put a lock on the bank account itself, you lock the method that does the banking transaction. You `synchronize` the method that acts on that data. Just add the `synchronized` modifier to the method declaration:

```java
private synchronized void makeWithdrawal(int amount) {...}
```


#### Using an object's lock

Every object has a lock. Most of the time, the lock is unlocked and you can imagine a virtual key sitting with it. They only come into play with synchronized methods. When an object has one or more synchronized methods, a thread can enter a synchronized method only if the thread can get the key to the object's lock.

Locks aren't per method, they're per object. It means you can't have two threads entering any of the synchronized methods. 

The goal of synchronization is to protect critical data. You don't lock the data itself, you synchronize the methods that access that data.

When a thread goes through its call stack and hits a synchronized method, it recognizes that it needs a key for that object before it can enter the method. It looks for the key, and if the key is available, the thread grabs the key and enters the method. From then on, it hangs on to the key and won't give it up until it completes the synchronized method. 

__Synchronizing methods that act on the shared data keeps the steps in the method as one unbreakable unit.__







