---
tags: [Notebooks/Head First Java]
title: 'Chapter 11: Exception Handling'
created: '2022-07-29T02:36:53.107Z'
modified: '2022-07-29T12:13:46.094Z'
---

# Chapter 11: Exception Handling

__Rationale:__ No matter how good a programmer you are, you can't control everything. 

We've had things go wrong at runtime, but the problems were mostly flaws in our own code. And those we should fix in development time. The problem-handling code here is for code that you _can't_ guarantee will work at runtime. 

### When you want to call a method that's risky

1. Let's say you want to call a method in a class that you didn't write.
2. That method does something risky, something that might not work at runtime.
3. You need to know that the method you're calling is risky.
4. You then write code that can handle failure if it _does_ happen. You need to be prepared, just in case.

### Exceptions

Methods in Java use exceptions to tell the calling code, "Something bad happened. I failed." Java lets you put all your error-handling code in one easy-to-read place. It's based on you knowing that the method you're calling is risky, so that you can write code to deal with that possibility. 

#### The compiler needs to know that YOU know you're calling a risky method

If you wrap the risky code in something called a __try/catch__, the compiler will relax. A try/catch block tells the compiler that you _know_ an exceptional thing could happen in the method you're calling, and that you're prepared to handle it. The compiler doesn't care how you handle it; it cares that you say you're taking care of it.

#### An exception is an object of type `Exception`

Because an `Exception` is an object, what you catch is an object. In the following code, the catch argument is declared as type `Exception`, and the parameter reference variable is `ex`.

```java
try {
  // do risky thing
} catch (Exception e) {
  // try to recover
}
```

#### `Exception` class hierarchy

All the different types of `Exception`s and the `Exception` class itself extend class `Throwable` and inherit two key methods: `getMessage()` and `printStackTrace()`.

#### Checked and Unchecked Exceptions

The compiler checks for everything except `RuntimeException`s. The compiler guarantees:
1. If you throw an exception in your code, you must declare it using the `throws` keyword in your method declaration.
2. If you call a method that throws an exception (in other words, a method that declares it throws an exception), you must _acknowledge_ that you're aware of the exception possibility. One way to satisfy the compiler is to wrap the call in a try/catch block.

- __checked exceptions:__ Exceptions that are NOT subclasses of `RuntimeException` are checked for by the compiler.
- __unchecked exceptions:__ `RuntimeException`s are NOT checked by the compiler.

The compiler cares about all subclasses of `Exception` unless they are a special type, `RuntimeException`. Any exception class that extends `RuntimeException` gets a free pass. 

The compiler doesn't care about these exceptions because most `RuntimeException`s come from a problem in your code logic, rather than a condition that fails at runtime in ways that you cannot predict or prevent. You _cannot_ guarantee the server is up. But you _can_ make sure your code doesn't index off of the end of an array.

You WANT `RuntimeException`s to happen at development and testing time. You want to catch something that shouldn't happen in the first place. A try/catch is for handling exceptional situations, not flaws in your code. Use catch blocks to try to recover from situations you can't guarantee will succeed. Or at least, print out a message to the user.

### Handle or Declare

There are two ways to satisfy the compiler when you call a risky (exception-throwing) method.

1. __Handle__ - wrap the risky call in a try/catch
```java
try {
  // risky method
} catch(Exception e) {
  // recovery code
}
```

2. __Declare (duck it)__ - declare that your method throws the same exceptions as the risky method you're calling
```java
void foo() throws Exception {
  // risky method
}
```
But now this means that whoever calls `foo()` has to follow the "Handle or Declare" law.
