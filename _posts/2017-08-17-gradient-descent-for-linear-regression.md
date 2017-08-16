---
layout: post
title: Gradient Descent for Linear Regression
categories: []
tags: [machine learning andrew ng]
description:
comments: true
mathjax: true
---

### Introduction
The posts [Cost Function of Linear Regression]({% post_url 2017-08-11-cost-function-of-linear-regression %}){:target="_blank"} and [Gradient Descent]({% post_url 2017-08-15-gradient-descent %}){:target="_blank} introduced the linear regression cost function and the gradient descent algorithm individually. If the gradient descent is applied to the linear regression cost function would help reach an optimal solution without much manual intervention.

### [Gradient Descent]({% post_url 2017-08-15-gradient-descent %}){:target="_blank}
Gradient descent algorithm can be summarized as, 

$$
\text{repeat until convergence} \{ \theta_j := \theta_j - \alpha \frac {\partial} {\partial \theta_j} J(\theta_0, \theta_1)\, \forall j \in \{0, 1\} \} \tag{1}
$$

* Where 
  * := is the assignment operator
  * \\(\alpha\\) is the **learning rate** which basically defines how big the steps are during the descent
  * \\( \frac {\partial} {\partial \theta_j} J(\theta_0, \theta_1)\\) is the **partial derivative** term
  * j = 0, 1 represents the **feature index number**

### [Linear Regression]({% post_url 2017-08-11-cost-function-of-linear-regression %}){:target="_blank"}
Linear regression hypothesis is given by, 

$$h_\theta (x) = \theta_0 + \theta_1\,x \tag{2}$$

And the corresponding cost function is given by,

$$J(\theta_0, \theta_1) = {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2 \tag{3}$$

### Gradient Descent for Linear Regression
Gradient descent is applied to the optimazation problem of the cost function of the linear regression given in (2) in order to find parameters that minimize the cost.

In order to apply gradient descent, the derivative term i.e. \\(\frac {\partial} {\partial \theta_j} J(\theta_0, \theta_1)\\) needs to be calculated.

$$
  \begin{align}
    \frac {\partial} {\partial \theta_j} J(\theta_0, \theta_1) & = \frac {\partial} {\partial \theta_j} \left( {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2 \right) \\
    & = {1 \over 2m} \left( \frac {\partial} {\partial \theta_j} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2 \right) \\
    & = {1 \over 2m} \left( \frac {\partial} {\partial \theta_j} \sum_{i=1}^m \left( \theta_0 + \theta_1\,x^{(i)} - y^{(i)} \right)^2 \right) \\
    & = 
    \begin{cases}
      {1 \over m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)}) \text{ for j = 0} \\
      {1 \over m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)}) x^{(i)} \text{ for j = 1}
    \end{cases}
  \end{align}
$$

Updating the values of the derivative term in the gradient descent algorithm given in (1) where the update must be done simultaneously, 

$$
  \begin{align}
    \text{repeat until convergence}
    \begin{cases}
      \theta_0 := \theta_0 - \alpha {1 \over m} \sum_{i=1}^m (h(x^{(i)} - y^{(i)})) \\
      \theta_1 := \theta_1 - \alpha {1 \over m} \sum_{i=1}^m (h(x^{(i)} - y^{(i)})) \cdot x^{(i)}
    \end{cases}
  \end{align}
$$

**The cost function for a linear regression is a convex function i.e. a bow-shaped function and has only one global minimum and no local minima. So it does not face the issue of getting stuck in local minima**. It can be understood better with the below plots.

![Convex Function](/assets/2017-08-17-gradient-descent-for-linear-regression/fig-1-convex-function.png?raw=true)

The gradient descent technique that uses all the training examples in each step is called **Batch Gradient Descent**. This is basically the calculation of the derivative term over all the training examples as it can be seen it the equation above.

The equation of linear regression can also be solved using **Normal Equations** method, but it poses a disadvantage that it does not scale very well on larger data while gradient descent does.


## REFERENCES:

<small>[Machine Learning: Coursera - Gradient Descent for Linear Regression](https://www.coursera.org/learn/machine-learning/lecture/kCvQc/gradient-descent-for-linear-regression){:target="_blank"}</small>