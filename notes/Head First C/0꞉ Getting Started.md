---
tags: [Notebooks/Head First C]
title: '0: Getting Started'
created: '2022-08-12T01:14:13.607Z'
modified: '2022-08-12T01:40:17.091Z'
---

# 0: Getting Started

### How C works

The C language is for small, fast programs. It's used where speed, space, and portability are important. It's also lower-level than most programs in that it creates code that's a lot closer to what machines understand. You convert your C code into machine code with the help of a compiler.

#### What a C program looks like

1. __C programs usually begin with a comment that describes the purpose of the code.__
2. __The include section__
  - C is a very small language and it can do almost nothing without the use of external libraries
  - You need to tell the compiler what external code to use by including header files
```c
/* stdio lib contains code that allows you to read
and write data to and from the terminal*/
#include <stdio.h>
```
3. __The last thing you'll find in a source file are the functions__
  - The most important function is the `main()` function, the starting point for all code.
```c
int main()
{
  /* some code */
}
```

#### main()

The `main()` function has a return type of `int`. When the computer runs the program, it checks the return value of the `main()` function to decide whether the function ran successfully or not. If you return 0, this means that the program was successful. Any other value means there was a problem.

#### string theory

Because C is more low-level than most languages, it uses an array of single characters instead of strings. But there are a number of C extensions that _do_ give you strings.

Strings are just character arrays. When C sees a string like this:
```
s = "Shatner"
```

it reads like it was just an array of separate characters:
```c
s = {'S', 'h', 'a', 't', 'n', 'e', 'r'}
/* s[0] = 'S', s[1] = 'h'... */
```

#### sentinels

C also can't always work out how long an array is and keep track of its size like in a lot of languages. If C is going to display a string on the screen, it needs to know when it gets to the end of the character array. It does this by adding a __sentinel character__. A sentinel is an additional character at the end of the string that has the value `\0`

So when the computer sees the string `s = "Shatner"`, it stores it in memory like this:

