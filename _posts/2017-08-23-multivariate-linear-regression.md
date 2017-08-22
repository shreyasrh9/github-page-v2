---
layout: post
title: Multivariate Linear Regression
categories: []
tags: [machine learning andrew ng]
description:
comments: true
mathjax: true
---

### Introduction
Multivariate linear regression is the generalization of the univariate linear regression seen earlier i.e. [Cost Function of Linear Regression]({% post_url 2017-08-11-cost-function-of-linear-regression %}){:target="_blank"}. As the name suggests, there are more than one independent variables, \\(x_1, x_2 \cdots, x_n\\) and a dependent variable \\(y\\). 

### Notation

* \\(x_1, x_2 \cdots, x_n\\) denote the n features
* \\(y\\) denotes the output variable to be predicted
* \\(n\\) is number of features
* \\(m\\) is the number of training examples
* \\(x^{(i)}\\) is the \\(i^{th}\\) training example
* \\(x_j^{(i)}\\) is the \\(j^{th}\\) feature of the \\(i^{th}\\) training example

### Hypothesis

The hypothesis in case of univariate linear regression was,

$$h_\theta(x) = \theta_0 + \theta_1\,x$$

Extending the above function to multiple features, hypothesis of multivariate linear regression is given by,

$$
  \begin{align}
    h_\theta(x) &= \theta_0 + \theta_1\,x_1 + \theta_2\,x_2 + \cdots + \theta_n\,x_n \\
    &= \theta_0\,x_0 + \theta_1\,x_1 + \theta_2\,x_2 + \cdots + \theta_n\,x_n \text{, where }x_0 = 1 \\
    &= \theta^T x \text{, vectorizing above equation}
  \end{align}
   \tag{1}
$$

* Where,
    * \\(\theta = \begin{bmatrix} \theta_0 \\\\ \theta_1 \\\\ \vdots \\\\ \theta_n \\\\ \end{bmatrix} \in \mathbb{R}^{n+1}\\) and \\(x = \begin{bmatrix} x_0 \\\\ x_1 \\\\ \vdots \\\\ x_n \\\\ \end{bmatrix} \in \mathbb{R}^{n+1} \\)

### Cost Function

The cost function for univariate linear regression was,

$$J(\theta_0, \theta_1) = {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2$$

Extending the above function to multiple features, the cost function for multiple features is given by,

$$
  \begin{align}
    J(\theta) &= {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2 \\
    &= {1 \over 2m} \sum_{i=1}^m \left( \theta^T x^{(i)} - y^{(i)} \right)^2 \\
    &= {1 \over 2m} \sum_{i=1}^m \left( \left( \sum_{j=0}^n \theta_j x_j^{(i)} \right) - y^{(i)} \right)^2 \\
  \end{align}
  \tag{2}
$$

* Where \\(\theta\\) is a vector give by \\(\theta = \begin{bmatrix} \theta_0 \\\\ \theta_1 \\\\ \vdots \\\\ \theta_n \\\\ \end{bmatrix} \\)

### Gradient Descent

$$
  \begin{align}
    \text{repeat until convergence}
    \begin{cases}
      \theta_j := \theta_j - \alpha {\partial \over \partial \theta_j} J(\theta) \\
    \end{cases}
  \end{align}
  \tag{3}
$$

**Note: simultaneous update only**

Evaluating the partial derivative \\({\partial \over \partial \theta_j} J(\theta)\\) gives, 

$${\partial \over \partial \theta_j} J(\theta) = {1 \over m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right) x_j^{(i)} \tag{4}$$

It can be easily seen that (4) is generalization of the update equation for univariate linear regression, because if we take only two features \\(\theta_0\\) and \\(\theta_1\\) and substitute in (4) the values, it results in the same equations as in [Univariate Linear Regression]({% post_url 2017-08-17-gradient-descent-for-linear-regression %}){:target="_blank"}

## REFERENCES:

<small>[Machine Learning: Coursera - Multivariate Linear Regression](https://www.coursera.org/learn/machine-learning/lecture/6Nj1q/multiple-features){:target="_blank"}</small>

<small>[Machine Learning: Coursera - Gradient Descent for Multiple Variables](https://www.coursera.org/learn/machine-learning/lecture/Z9DKX/gradient-descent-for-multiple-variables){:target="_blank"}</small>
