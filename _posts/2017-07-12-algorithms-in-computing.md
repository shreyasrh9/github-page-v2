---
layout: post
title: Algorithms and Data Structures
categories: []
tags: [06. CLRS]
description: Any well-defined computational procedure that takes some value, or set of values, as input and produces some value, or set of values, as output. So, algorithm is a sequence of computational steps that transform the input into the output. An algorithm is correct if, for every input instance of a problem, it halts with the correct output.
comments: true
---

### Algorithm

Any well-defined computational procedure that takes some value, or set of values, as **input** and produces some value, or set of values, as **output**. So, algorithm is a sequence of computational steps that transform the input into the output. An algorithm is correct if, for every input instance of a problem, it halts with the correct output.

**Incorrect algorithms can sometimes be useful, if the error rate is controlled.**

Measures of a good algorithm
* **Time Complexity**: Time taken to run.
* **Space Complexity**: Auxilliary space needed to run the algorithm.

### Data Structures

A **data structure** is a way to store and organize data in order to facilitate access and modifications. No single data structure works well for all purposes, and all of them have their strengths and weeknesses.

### Hard Problems

General **measure of efficiency** is speed for all algorithms. But some problems there are no efficient solutions known. A subset of these problems are also known as **NP-complete** problems. These problems have the 3 interesting properties:

* Although no efficient algorithm for an NP-complete problem has been found, its neither been proved that an efficient algorithm for one cannot exist i.e. no one knows whether or not efficient algorithm exist for NP-complete problems.

* If an efficient algorithm exists for any one of them, then efficient algorithms exist for the rest of them.

* Several NP-complete problems are similar, but not identical, to problems for which efficient algorithms are known i.e. small changes in problem statements cause a big change in efficiency of the best known algorithm.

[**Travelling Salesman Problem**](https://www.google.co.in/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0ahUKEwiZ9d7C8IPVAhUDQo8KHTx0ALQQFggvMAI&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FTravelling_salesman_problem&usg=AFQjCNHHeqQL_wgjok2-NTUVuoNOORofXw) is a classic example of a NP-complete problem encountered in everyday application.

### Pseudocode

Logic of algorithms is often expressed as pseudocode which is similar in many respects to languages like C, C++, Java etc. Major difference lies in that pseudocode uses the most **concise and meaningful** way of expressing the algorithm which can be sometimes as simple as plain english.

Also pseudocode does not get into the issues of software engineering like **abstraction, modularity or error handling**.

Pseudocode for insertion sort can be written as:

```
InsertionSort(A):
    for i = 1 to A.length-1
        key = A[i]
        j = i - 1
        while j > 0 and a[j] > key:
            A[j+1] = A[j]
            j--
        A[j+1] = key
```



## REFERENCES:

<small>[Introduction to Algorithms 3rd Edition Chapter 1 & 2](https://web.njit.edu/~wl256/download/cs610/Introduction-to-algorithm-3rdEdition.pdf){:target="_blank"}</small>