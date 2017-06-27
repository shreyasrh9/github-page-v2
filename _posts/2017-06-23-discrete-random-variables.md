---
layout: post
title: Discrete Random Variables
categories: []
tags: [probability]
description:
comments: true
mathjax: true
---

* **Discrete Random Variables**: A function that maps the sample space to a set of discrete real values.
\\[X : S \rightarrow R\\]
  * Where
    * X is the random variable
    * S is the sample space
    * R is the set of real numbers

* **Probability Mass Function**: Probability defined over a give random variable. 
  * For a random variable X, \\(p(X=c\\) is denoted as \\(p(c)\\) and the mapping of each value in sample space to their respective probabilities is known as **pmf**
  * For all values c that are not is sample space \\(p(c) = 0\\) because it is pointing to an empty set.
  * Also, \\(0 \leq p(c) \leq 1\\)

* **Commutative Distribution Function**: Probability defined over an inequality such as \\(X \leq c\\) gives probabilities of all the events that satisfy the condition from \\(-\infty\\) to c i.e. the probability value estimate for X less than or equal to c. Mathematically,
\\[CD(c) = \sum_b p(b)\text{ for all } -\infty \leq b \leq c \\]

* **Explaination**:
  * Set has 5 boys and 5 girls.
  * 3 kids selected at random but gender not known.
  * X is the random variable that denotes number of girls selected.
  * Event c such that \\(X(c) = 3\\) is given by set \\(c = \\{(GGG)\\}\\) i.e. all three girls selected are girls.
  * The pmf for random variable X will be as follows:

| a | p(a)| CD(a) |
|:-:|:-:|:-:|
| 0 | 1/12  | 1/12 |
| 1 | 5/12  | 6/12 |
| 2 | 5/12  | 11/12 |
| 3 | 1/12  | 1 |

  * Calculations:
    * Number of ways of selecting k kids from total of N kids is given by \\(C_k^N = \frac{N!}{k! (N-k)!}\\) implies \\(C_3^{10} = \frac{10!}{3! (10-3)!} = 120\\) for N = 10 and k = 3.
    * value 1 : a = 0 means that no girl is selected which implies that k boys are selected out of the total B boys. The number of ways this can be accomplished is given by \\(C_k^B = \frac{B!}{k! (B-k)!}\\) implies \\(C_3^5 = \frac{5!}{3! (5-3)!} = 10\\) for B = 5 and k = 3.
    * For commutative distribution \\(CD(2) = p(0) + p(1) + p(2) = 11/12\\).
    * Similarly the value of \\(p(a)\\) and \\(CD(a)\\) at other values of \\(a\\) can be calculated.

* **Some Specific Distributions**:

  * **Uniform Distribution**: 
    * All outcomes are eqully possible. 
    * Eg: Probability of getting a heads or tails for a fair coin. 
    * Uniform(N) implies N outcomes and each has probability 1/N.

  * **Bernoulli Distribution**: 
    * Used to model the random experiment where each trail has exactly 2 possible outcomes.
    * One possible outcome is termed as success and other as failure.
    * Parameter \\(p\\) is the probability of success in an experiment.
    * Random variable \\(X \in \\{0, 1\\}\\).
    * X = 1 has probability \\(p\\) and X = 0 has probability \\(1-p\\) where 0 is denoting failure and 1 denoting success.

  * **Binomial Distribution**:
    * Used to model \\(n\\) independent traits of Bernoulli Distribution.
    * If X follows Binomial(n, p) then, X = k implies, the event of k successes in n independent Bernoulli trials.
    \\[P(X=k) = C_k^n * (p^k) * ((1-p)^{n-k})\\]
    * \\(C_k^n\\) is the number of ways of picking k success events in n total trials.
    * \\((p^k) * ((1-p)^{n-k})\\) gives the combined probability of the n Bernoulli trails.

  * **Geometric Distribution**:
    * Also defined over Bernoulli distribution.
    * Models the event of k failures before first success.
    * geometric(p) is given by 
    \\[P(X=k) = (1-p)^k * p\\]
    where X = k is the event where first success occured after k failures.




## REFERENCES:

<small>[Discrete Random Variables](https://www.hackerearth.com/practice/machine-learning/prerequisites-of-machine-learning/discrete-random-variables/tutorial/){:target="_blank"}</small>
