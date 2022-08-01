---
tags: [Notebooks/Backend]
title: Concurrency and Parallelism
created: '2022-08-01T02:49:40.794Z'
modified: '2022-08-01T06:46:24.568Z'
---

# Concurrency and Parallelism

## Parallelism

__"Parallelism is about doing a lot of things at once."__

Parallelism is about execution. Having two things executing simultaneously, not just _having_ two things.

This means that your program leverages the hardware of multi-core machines to execute tasks at the same time by breaking up work into tasks, each of which is executed on a separate core.

Example in real life: following the cake and song example, the rule is still singing and eating, but this time, you play in a team of two. You will probably eat and let your friend do the singing. So this time, the two tasks are really executed simultaneously. In CS, parallelism can only be achieved in multicore environments.

```java
public static void main(String[] args) {
  Thread thread1 = new Thread(task);
  Thread thread2 = new Thread(task);

  thread1.start(); // task 1
  thread2.start(); // task 2

  heavyCalculations(); // task 3 
}
```

If you run this program in a 4-core CPU, then we can run these three tasks in parallel. The scheduler schedules the threads on the CPU. Since none of the tasks are dependent on each other, each thread will run on their own core.


## Concurrency aka Multithreading

__"Concurrency is about dealing with a lot of things at once."__

Concurrency is about structure. Structure your program into independent pieces, but then you'd have to coordinate those pieces. 

Concurrency is a software implementation allowing different threads to be executed concurrently. A multithreaded program appears to be doing several things at once even when it's running on a single-core machine. It's applied when there is a shared resource that two threads have to access or update, or there are multiple tasks that need to coordinate.

Example in real life: There's a challenge that requires you to both eat a whole cake and sing a whole song. You'll win if you're the fastest who sings the whole song and finishes the cake. So the rule is that you sing and eat concurrently. _How_ you do that does not belong to the rule. You can eat the whole cake, then sing the whole song, or you can eat half a cake, the sing half a song, then do that again. The same applies to CS. There are two tasks executing concurrently, but those are run in a 1-core CPU, so the CPU will decide to run a task first then the other task etc., it all depends on the system architecture. 

```java
public static void main(String[] args) throws InterruptedException {
  Thread thread1 = new Thread(() -> {
    if (ticketsAvailable > 0) { // accessing shared variable
      bookTicket();
      ticketsAvailable--;
    }
  });

  Thread thread2 = new Thread(() -> {
    if (ticketsAvailable > 0) { // accessing shared variable
      bookTicket();
      ticketsAvailable--;
    }
  });
  

  thread1.start(); // task 1
  thread2.start(); // task 2

  Thread.sleep(5000); // putting main thread to sleep 
}
```

 The scheduler interleaves threads. It's tricker now because there are no multiple cores so the scheduler will have to do some time-sharing between the threads. How much time each thread gets is non-deterministic. 

 #### Best-case scenario (not guaranteed)
 The best-case scenario would be if `thread1` accomplishes all its instructions in the time the scheduler has given it to run. It checks the shared variable (`ticketsAvailable`), books the ticket, and then updates the shared variable. And then by the time `thread2` runs and it checks the `ticketsAvailable`, `thread1` has already updated it. The program will run correctly in this case. 

 #### Scenario that gives a wrong result

 It's also possible that `thread1` will only be able to execute one operation and then the scheduler has `thread2` run. They first check the shared variable in the time they're given. Both threads will then book the ticket and after that they will update the shared variable count. This is an incorrect program. Because when `thread1` runs, even if the `ticketsAvailable` is equal to 1, both threads will be able to book the ticket. 

 ##### One possible fix for this scenario

Introduce locks. `thread1` will acquire the lock and only then access the tickets and update the tickets. Once completed, it will release the lock and `thread2` will do the same thing. In this case, the two threads are coordinating with each other using the single lock. 



