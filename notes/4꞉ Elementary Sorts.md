---
tags: [Notebooks/Algorithms Part 1]
title: '4: Elementary Sorts'
created: '2022-08-08T05:14:48.572Z'
modified: '2022-08-08T07:34:29.515Z'
---

# 4: Elementary Sorts

### Sorting Introduction

1. Figure out what you're sorting. Doubles, Strings, Filenames?
2. What is the property/key in which you want to sort the items?
3. Ascending / descending?


### Selection sort
- __Worst case__ - O(n^2)
- __Best case__ - O(n^2); does not optimize if the array is already/partially sorted

implementation:

```java
public static Integer[] selectionSort(Integer[] arr) {
    for (int i = 0; i < arr.length; i++) {
        int least = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[least]) {
                least = j;
            }
        }
        int current = arr[i];
        arr[i] = arr[least];
        arr[least] = current;
    }
    return arr;
}
```


### Insertion sort
- __Worst case__ - O(n^2)
- __Best case__ - O(n^2); does not optimize if the array is already/partially sorted

implementation:

```java
public static Integer[] insertionSort(Integer[] arr) {
    int j;
    for (int i = 1; i < arr.length; i++) {
        j = i - 1;
        while (j >= 0) {
            if (arr[j+1] < arr[j]) {
                int lesser = arr[j];
                int greater = arr[j+1];
                arr[j+1] = lesser;
                arr[j] = greater;
            }
            j--;
        }
    }
    return arr;
}
```


