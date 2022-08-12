---
tags: [Notebooks/The C Programming Language]
title: '1: A Tutorial Introduction'
created: '2022-08-12T02:54:59.372Z'
modified: '2022-08-12T05:48:29.869Z'
---

# 1: A Tutorial Introduction

This section shows the essential elements of the language in real programs, but without getting bogged down in details and rules. To write useful programs, you have to concentrate on the basics: variables and constants, arithmetic, control flow, functions, and the rudiments of input and output. 

### Getting Started

Printing "hello, world!"
```c
#include <stdio.h>

int main()
{
  printf("hello, world\n");
}
```

A C program, whatever its size, consists of _functions_ and _variables_. A function contains _statements_ that specify the computing operations to be done, and variables store values used during the computation. Your program begins executing at the beginning of the `main` function. This means that every program must have a `main` somewhere. `main` will usually call other functions to help perform its job, some that you write yourself and others from libraries that are provided for you.

`#include <stdio.h>` tells the compiler to include information about the standard input/output library.

One method of communicating data between functions is for the calling function to provide a list of values, called _arguments_, to the function it calls. 

A function is called by naming it, followed with by a parenthesized list of arguments. So the `printf` function is called with the argument `"hello, world\n"`. `printf` is a library function that prints output, in this case a string of characters. This function never supplies a newline automatically.

A sequence of characters in double quotes, like `"hello, world\n"`, is called a _character string_ or _string constant_. 

_Escape sequences_ like `\n` provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are `\t` for tab, `\b` for backspace, `\"` for the double quote, and `\\` for the backslash itself. 

### Variables and Arithmetic Expressions

In C, all variables must be declared before they are used, usually at the beginning of a function before any executable statements. A _declaration_ announces the properties of variables; it consists of a type name and a list of variables.

The type `int` means that the variables are listed as integers, by contrast with `float`, which means floating point. The range of both `int` and `float` depends on the machine you are using; 16-bit ints are common, as are 32-bit ints. A float is typically a 32-bit quantity. 

C provides several other basic data types (wherein sizes are also machine-dependent) besides int and float, including:
- __char__ - character-a single byte
- __short__ - short integer
- __long__ - long integer
- __double__ - double-precision floating point

### Symbolic Constants

It's bad practice to bury _"magic numbers"_ like 300 and 20 in a program; they convey little information to others, and they are hard to change in a systematic way. One way to deal with them is to give them meaningful names. A `#define` line defines a symbolic name to be a particular string of characters.

```c
#define name replacement_name
```

### Character I/O

Text I/O, regardles of where it originates or goes to, is dealt with as streams of characters. A _text stream_ is a sequence of characters divided into lines; each line consists of zero or more characters followed by a newline character.

- `getchar()` - reads one character
- `putchar(c)` - writes one character

### Character Counting










