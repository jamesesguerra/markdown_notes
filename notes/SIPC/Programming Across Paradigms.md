---
tags: [Notebooks/SIPC]
title: Programming Across Paradigms
created: '2022-08-11T11:47:30.964Z'
modified: '2022-08-12T01:40:30.360Z'
---

# Programming Across Paradigms

### What is a paradigm?

- A paradigm is a worldview, a way of understanding the universe e.g. Geocentrism.
- It enables progress. It's not possible to advance our understanding of the universe if there isn't a model we all agree upon. 

> _"In learning a paradigm, the scientist acquires **theory**, **methods**, and **standards** together, usually in an extricable mixture."_

- __theory__ - what entities make up the universe; how they behave and interact (what makes up a program and how do they interact)
- __methods & standards__ - which problems are worth solving; which solutions are legitimate (which problems we need to address as programmers)

## 1. imperative programming

We conceive of programs as made up of statements and expressions and those combine to create commands that we give to the computer. The crucial entity of this paradigm is the imperative statement or command -- _"do this, then do that"_, _"Hey you, computer, do what I say. Follow them in the order that I give them"_. Time is important, and this is where state comes in. State is essentially remembering values over time, how they change over time. Linear way of thinking.

### a complex clock; machinery; clockwork

It's very intricate, very precise, and amazing to think about how tiny pieces fit together. You have to pay attention to every little thing in that machine. Precision becomes important. So as soon as one little thing breaks, the whole thing freezes. 

__Anomaly:__ As programs get larger and more complex, they become much harder to manage. In comes OOP.

## 2. object-oriented programming

Still sort of imperative in that we're still telling the computer what to do, and we're still paying attention to state, but we're breaking it up into little chunks. So that now, the universe of programs is no longer comprised of commands, it's comprised of objects. Objects are little units that keep a little portion of state to themselves. So we say _"you, object, remember your little portion of the state of the world"_. These little objects interact by sending messages to each other (equivalent to calling a method on an object). We say _"hey object, you have some state, here's a method that I want you to run on whatever state you have and then give me some response back; do something based on my message; do something based on how your internals tell you to respond"_

### biological analogy

Each object can be thought of as a cell in a larger tissue. A cell has its own internal structure that make it whatever type of cell it is. It also has a membrane that protects whatever is inside it, and in that membrane it has a receptor that receives molecules that are floating around. This makes a larger system function. 

## 3. functional programming

Let's do things in a completely different way. Let's forget about all these commands and saying _"do this, do that"_. Let's forget about time and mutable state. 

### Pure functions

Let's conceive of the universe in terms of pure functions. Pure functions are safe because all they do is take in some input, do computations, and then spit out their output. All they look at is the arguments that go in, they don't look at anything else about the rest of the world. And all they do is return a value; they don't make any other changes. They are like transformers of data -- data goes in, data comes out. And you can hook them all up together so that you can flow data through your program. 

### factory

Pure functions are like factories in that factories receive raw materials trucks and then at the end of the day, something is assembled and trucks bring them out. Assembly lines do one specialized task and the raw materials flow through them and gets transformed in little ways.

## 4. declarative programming

Functional programming falls under declarative programming. If imperative programming thinks of the universe as being made up of commands that we give the computer, declarative programming says it's made up of declarative statements. Instead of _"do this, do that"_, it's made up of statements like _"these are the facts, this is what I know, this is what I want from you, computer, and I don't care how you're gonna give it to me, I don't care how you do it, I'm not gonna give you explicit instructions"_

### logic puzzle

It's like sudoku. You have constraints, you have rules about the world e.g. _"every 3x3 square has to have the numbers 1-9"_. You are the computer trying to complete the puzzle.

-----

### What do paradigms have in common?

#### Shared mutable state

One of the problems functional and object-oriented programming was trying to solve is the rigidity of the imperative paradigm. Both of them reject this notion that we should have shared mutable state, they just do it in different ways. 

Functional programming says forget mutating everything, just make everything immutable, forget state, forget time, and then you can share as much as you want as long as nobody's changing anything. Each function is just churning out new data that replaces the old. 

OOP says lets divide the state into little chunks that keep to themselves so that we're not sharing any of it. The big idea isn't objects, it's messaging. Cells send messages back and forth and that's how we get a larger system. 

They're both similar in code implementation. It just depends on your frame of mind.

### Which paradigm is the best?

> _"All models are wrong, but some are useful."_

Paradigms are useful in different ways. Each paradigm supports a set of concepts that makes it the best for a certain kind of problem. It's just a matter of matching your problem with the best paradigm for solving it. 

> _"Is the model **illuminating** and **useful**."_

Does the paradigm tell us something new? Does it give us some insight into the particular problem that makes it easier to solve. 

### What can a paradigm teach us?

- __imperative programming__ - good teacher of how to be explicit and how to focus on and understand the implementation as being crucial to the particular program. Forces you to focus on the small changes that need to be made in order for the program to work. 

- __declarative programming__ - teaches us to get really abstract, to think more about the domain and the big picture of the ideas that we're trying to represent in our program and not how they're implemented. This can be easier when thinking about certain problems when we can change the implementation, but the big picture stays the same. 

- __OOP__ - encapsulate, communicate
- __FP__ - specialize, transform data





