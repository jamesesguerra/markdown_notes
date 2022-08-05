---
tags: [Notebooks/Interview]
title: An interview problem
created: '2022-08-05T03:05:12.593Z'
modified: '2022-08-05T03:28:54.055Z'
---

# An interview problem

### Sample problem: Best Time to Buy and Sell Stock

A chart depicts movements in the share price of a company over 40 days. Specifically, for each day, the chart shows the daily high and low, and the price at the opening bell. Suppose you were asked to design an algorithm that determines the max profit that could have been made by buying and then selling a single share over a given day range, subject to the constraint that the buy and sell have to take place at the start of the day.

First, clarify the problem. For example, you should ask for the input format.
- The input consists of 3 arrays: `L`, `H`, and `S`, of nonnegative floating point numbers, representing the low, high, and starting prices for each day. 

The constraint suffices to consider `S`. You may be tempted to simply return the difference of the minimum and maxmimum elements in `S`. But this violates the requirement in the problem statement that you have to buy before you can sell since the minimum can occur after the maximum.

#### Brute-force algorithm

For each pair of indices `i` and `j > i`, if `S[j]` and `S[i]`is greater than the largest difference seen so far, update the largest difference to `S[j] - S[i]`. This can be coded with a pair of nested for-loops. __You should also derive its time complexity as a function of the length `n` of the input array.__ The outer loop is invoked `n - 1` times, and the `i`th iteration processes `n - 1 - i` elements. Processing an element entails computing a difference, performing a compare, and possibly updating a variable, all of which take constant time. Hence, the runtime is `O(n^2)`. __You should also consider the space complexity, ie., how much memory your algorithm uses.__ The array itself takes memory proportional to `n`, and the additional memory used by the brute-force algorithm is a constant independent of `n` - a couple of iterators and one floating point variable. 

#### Improvement

__Once you have a working algorithm, try to improve upon it.__ An `O(n^2)` algorithm is usually not acceptable when faced with large arrays


#### Key skills

You have to demonstrate to your interviewer that you possess several key skills:
- The ability to formulate real-world problems.
- The ability to solve problems and design algorithms.
- The tools to go from an algorithm to a tested program.
- The analytical techniques required to determine the computational complexity of your solution.

__main point:__ model real-world problem, intelligently select data structures and algorithms, code the algorithm, and determine its computational complexity (in terms of time and space).


