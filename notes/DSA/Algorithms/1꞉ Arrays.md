---
tags: [Notebooks/Data Structures]
title: '1: Arrays'
created: '2022-08-05T05:40:18.590Z'
modified: '2022-08-05T06:47:06.126Z'
---

# 1: Arrays

The simplest data structure is the array, which is a contiguous block of memory. It's usually used to represent sequences. Given an array `A`, `A[i]` denotes the `(i + 1)`th object stored in the array. Retrieving and updating `A[i]` takes `O(1)` time. Insertion into a full array can be handled by resizing, ie., allocating a new array with additional memory and copying over the entries from the original array. This increases the worst-case time of insertion, but if the new array has, for example, a constant factor larger than the original array, the average time for insertion is constant since resizing is infrequent. Deleting an element from an array entails moving all successive elements one over to the left to fill the vacated space. For example, if the array is `[2, 3, 5, 7, 9, 11, 13, 17]`, then deleting an element at index 4 results in the array `[2, 3, 5, 7, 11, 13, 17, 0]` (we do not care about the last value). The time complexity to delete the element at index `i` from an array of length `n` is `O(n - i)`.
