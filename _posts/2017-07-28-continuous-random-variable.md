---
layout: post
title: Continuous Random Variables
categories: []
tags: [03. probability]
description:
comments: true
mathjax: true
---

### Continuous Random Variables
A continuous random variable is a function that maps the sample space of a random experiment to an interval in real value space. A random variable is called continuous if there is an underlying function f(x) such that 

$$P(p \leq X \leq q) = \int_p^q f(x) dx$$

  * Where f(x) is a non negative function  called **probability density function (pdf)**

* Probability Density funtion can be considered analogous to Probability Mass function of Discrete random variable but differs in that pdf does give probability directly at a value like in case of pmf. Hence the rules of probability do not apply to f(x).

* Pdf takes value 0 for values outside range(X).

* Also the following property can be inferred from rules of probability, 

$$P(-\infty \leq X \leq \infty) = \int_{-\infty}^\infty f(x) dx = 1$$

* Probability of a continuous random variable taking a range of values is given by the area under the curve of f(x) for that range.

### Cumulative Distribution Function (cdf)
Cdf for continuous random variable is same as the one for discrete random variable. It is given by, 

$$cdf(X \leq c) = \int_{-\infty}^c f(x) dx$$

* **Properties of cdf:**
  * Unlike f(x), cdf(x) is probability and follows the laws and hence,

  $$0 \leq cdf(x) \leq 1$$
  
  * As probability is **non-negative**, cdf is a **non-decreasing** function.
  * Differential of cdf is given by 

  $$cdf'(x) = f(x)$$

  * Limits of cdf are given by

  $$cdf(x) \to 0 \text{ as } x \to -\infty$$

  $$cdf(x) \to 1 \text{ as } x \to \infty$$

### Some Specific Distributions

* **Uniform Distribution**

\\(X = Uniform(N)\\) is used to model a scenario where all outcomes are equally likely. Uniform([c, d]) is when all the values of \\(x\(c \leq x \leq d\)\\) are equally probable. It is given by

$$ Uniform([c, d]) = {1 \over (d-c)}$$

* **Exponential Distribution**

  * Defined using a parameter \\(\lambda\\) and has the pdf given by

  $$f(x) = \lambda e^{-ex}, \, x \geq 0$$.
  * It is used to model the waiting time for an event to occur eg. waiting time for nuclear decay of radioactive isotope distributed exponentially and \\(\lambda\\) is known as the half life of the isotope.

  * This distribution exhibits lack of memory i.e. when waiting time is modeled using exponential distributions, the probability of it happening in next N minutes remains same irrespective of the time passed.

* **Proof**

According to lack of memory property, prove \\(P(X \gt n+w \| X \gt w ) = P(X \gt n)\\) holds true.

$$P(X \gt n+w | X \gt w) = \frac {P(X \gt n+w)} {P(X \gt w)}$$

$$ \frac {P(X \gt n+w)} {P(X \gt w)} = \frac {e^{- \lambda (n+w)}} {e^{- \lambda w}} = e^{- \lambda n}$$

* **Normal Distribution**
  * Most commonly used distribution
  * Also known as Gaussian distribution
  * It is denoted by \\(N(\mu, \sigma^2))\\) where \\(\mu\\) is the mean and \\(\sigma^2\\) is the variance fo the given distribution.
  * Standard Normal Distribution, denoted by Z is a normal distribution with mean = 0 and variance = 1.
  * It is symmetric about the y-axis and follows the bell-curve.



## REFERENCES:

<small>[Continuous Random Variables](https://www.hackerearth.com/practice/machine-learning/prerequisites-of-machine-learning/continuous-random-variables/tutorial/){:target="_blank"}</small>
