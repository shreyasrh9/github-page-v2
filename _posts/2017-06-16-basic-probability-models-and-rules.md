---
layout: post
title: Basic Probability Concepts
categories: []
tags: [probability]
description:
comments: true
mathjax: true
---

* **Trail or Experiment** - The act that leads to a result with certain possibility.
* **Sample Space**	- Set of all possible outcomes of an experiment.
* **Event** -	Non empty subset of a sample space.

* **Basic probability formula**:
  * \\(P(A) = \sum_{i=1}^n P(E_i)\\)
  * Where
    * A is an event,
    * S is the sample space,
    * \\(E_1 ... E_n\\) are the n outcomes in A.

* If \\(E_1 ... E_n\\) are equally likely to occur, then
    * \\(P(A) = {num(A) \over num(S)}\\)
  * Where
    * num(A) is the number of outcomes in A,
    * num(S) is the number of outcomes in S
  * Hence
    * \\(0 \leq P(A) \leq 1\\),
    * \\(P(S) = 1\\)

* **Complement of A**: All outcomes not in A.
  * \\(P(A^c) = 1 - P(A)\\)
  * Where
    * \\(A^c\\) is the compliment of A

* **Union and Intersection**:
  * \\(P(A \cup B) = P(A) + P(B) + P(A \cap B)\\)

* **Mutually Exclusive**: There are no overlapping outcomes.
  * \\(P(A \cap B) = 0\\)
  * \\(P(A \cup B) = P(A) + P(B)\\)

* **Independent**: Occurence of one event does not effect the occurence of the other.
  * \\(P(A \cap B) = P(A) * P(B)\\)

* **Sum Rule or Marginal Probability**:
  * \\(P(A) = \sum_{B} P(\text{A and B})\\)

* **EXAMPLE**:
  * M wants to go fishing this weekend to nearby lake.
  * His neighbour A is also planing to go to the same spot for fishing this weekend.
  * The probability that it will rain this weekend is \\(p_1\\).
  * There are two possible ways to reach the fishing spot (bus or train).
  * The probability that
    * M will take the bus is \\(p_{mb}\\)
    * A will take the bus is \\(p_{ab}\\).
  * Travel plans of both are independent of each other and rain.
  * What is the probability \\(p_{rs}\\) that M and A meet each other only (should not meet in bus or train) on a lake in rain ?

```python
p_mb = float(input())
p_ab = float(input())
p_1 = float(input())
p_rs = p_1 * (1 - p_ab*p_mb - (1-p_ab)*(1-p_mb))
print("%.6f" % p_rs)
```

## *REFERENCES*:

<small>[*Basic Probability Models and Rules*](https://www.hackerearth.com/practice/machine-learning/prerequisites-of-machine-learning/basic-probability-models-and-rules/tutorial/){:target="_blank"}</small>
