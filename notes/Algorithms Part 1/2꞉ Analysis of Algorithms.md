---
tags: [Notebooks/Algorithms Part 1]
title: '2: Analysis of Algorithms'
created: '2022-08-06T05:47:10.436Z'
modified: '2022-08-07T04:35:10.209Z'
---

# 2: Analysis of Algorithms

### Running time

_Whenever any result is sought from an Analytic Engine, the question will arise -- By what course of calculation can these results be arrived at by the machine in the shortest time?_

#### reasons for analyzing algorithms
- performance prediction
- to compare algorithms that do the same thing
- provide guarantees 
- __primary practical reason:__ avoid performance bugs

### Scientific method applied

- Observe the computer itself
- Hypothesize a model that is consistent with the observations
- Predict events using the hypothesis
- Verify the predictions by making further observations


### Observations

#### Example: 3-SUM

Given N distinct integers, how many triples sum to exactly zero?

__brute-force algorithm:__
```java
public static count(int[] a) {
  int N = a.length;
  int count = 0;
  for (int i = 0; i < N; i++) {
    for (int j = i+1; j < N; j++) {
      for (int k = j+1; k < N; k++) {
        if (a[i] + a[j] + a[k] == 0) {
          count++;
        }
      }
    }
  }
  return count;
}
```

Observe that it is O(n^3).

### Mathematical Models

__Total running time:__ sum of cost x frequency for all operations
- need to analyze program to determine set of operations
- cost depends on machine, compiler
- frequency depends on algorithm, input data 

![image](https://user-images.githubusercontent.com/68677613/183240039-9703ffdc-d0b0-4c3e-963a-5a690cc8bb2b.png)

![image](https://user-images.githubusercontent.com/68677613/183240045-7154f458-fcca-4ece-94d4-a5543145c2fa.png)

#### Binary search: mathematical analysis

Proposition: Binary search uses at most `1 + log N` compares to search in a sorted array of size N

__implementation:__

```java
public static int binarySearch(int x, int[] arr) {
    int low = 0;
    int high = arr.length - 1;
    int i = 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        int guess = arr[mid];

        if (x == guess) {
            System.out.println("Element found at index " + mid);
            return 1;
        } else if (x > guess) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
        i++;
    }
    System.out.println("Element not found");
    return -1;
}
```

### Theory of Algorithms

__Best case__
- lower bound on cost 
- determined by "easiest" input
- provides a goal for all inputs

__Worst case__
- upper bound on cost 
- determined by "most difficult" input
- provides guarantee for all inputs

__Average case__
- expected cost for random input
- provides a way to predict performance

### Memory

__Bit:__ 0 or 1
__Byte:__ 8 bits.

__Old machine:__ We used to assume a 32-bit machine with 4 byte pointers.

__Modern machine:__ We now assume a 64-bit machine with 8 byte pointers
- can address more memory
- pointers use more space


### Summary

- analyze algorithm to count frequency of operations
- use tilde notation to simplify analysis
- model enables us to explain behavior
