---
tags: [Notebooks/SIPC]
title: Programming Paradigms for Dummies
created: '2022-08-11T15:19:42.165Z'
modified: '2022-08-14T12:36:06.976Z'
---

# Programming Paradigms for Dummies

## Introduction

Programming languages are usually complicated, but their important ideas are simple. 

Solving a programming problem requires choosing the right concepts. A _programming paradigm_ is an approach to programming a computer based on a mathematical theory or a set of principles. Each paradigm supports a set of concepts that make it the best for a certain kind of problem. For example, OOP is best for problems with a large number of related data abstractions organized in a hierarchy. 

Different programming languages need different programming concepts to solve problems cleanly. A language should ideally support many concepts in a well-factored way, so that the programmer can choose the right concepts whenever they are needed. This is called _multiparadigm_ programming. Nevertheless, understanding the right concepts can help improve programming style even in languages that do not support them.

## Languages, paradigms, and concepts

Languages realize paradigms that consists of a set of concepts. Many languages implement the same paradigm with only minor differences.

> __kernel language__ - a set of programming concepts organized into a simple core language

![image](https://user-images.githubusercontent.com/68677613/184536037-bafd7f77-559c-4007-92d0-196e77f1a92f.png)

An arrow between two boxes represents the concept/s that have to be added to go from one paradigm to the next. Many paradigms are useless in practice, such as an empty paradigm (no concepts) or paradigms with only one concept. A paradigm always has to be Turing complete to be practical. This is why functional programming is so important: it's based on the concept of first-class function or closure, which makes it == to lambda calculus which is Turing complete.

When a language is mentioned under a paradigm, it means that language is intended to support the paradigm w/o interference from other paradigms. But this doesn't necessarily mean that there is a perfect fit between the language and the paradigm. It isn't enough that libraries have been written in the language to support the paradigm. The language's kernel language must do that.

### Observable nondeterminism

The first key property of a paradigm is whether or not it can express this idea. Nondeterminism is when the execution of a program is not completely determined by its specification, ie., at some point during the execution, the specification allows the program to choose what to do next. During the execution, this choice is made by a part of the run-time system called the _scheduler_. The nondeterminism is observable if a user can see results from executions that start at the same internal configuration. This is highly undesirable since a typical effect is a _race condition_, where the result of a program depends on precise differences in timing between different parts of a program. This can happen when the timing affects the choice made by the scheduler. But paradigms that have the power to express observable nondeterminism can be used to model real-world situations and to program independent activities.

Observable nondeterminism should only be supported only if its expressive power is needed. This is especially true for concurrent programming. For example, Java can express observable nondeterminism since it has both named state and concurrency. This makes concurrent programming in Java quite difficult.

### Named state

The second key property of a paradigm is how strongly it supports state. State is the ability to store information as time passes by. Its expressive power is strongly influenced by the paradigm that contains it. 

3 axes of expresiveness (gives 8 combinations in all):
1. unnamed or named
2. deterministic or nondeterministic
3. sequential or concurrent



