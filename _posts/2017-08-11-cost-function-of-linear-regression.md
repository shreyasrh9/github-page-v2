---
layout: post
title: Cost Function of Linear Regression
categories: []
tags: [machine learning andrew ng]
description:
comments: true
mathjax: true
---

### Linear Regression
Linear regression is an approach for modeling the relationship between a **scalar dependent variable** y and one or more **explanatory variables** (or **independent variables**) denoted X. The case of one explanatory variable is called **simple linear regression** or **univariate linear regression**. For more than one explanatory variable, the process is called **multiple linear regression**.
In linear regression, the relationships are modeled using **linear predictor functions** whose unknown model parameters are estimated from the data. Such models are called linear models.


### Hypothesis
The hypothesis for a univariate linear regression model is given by, 
$$h_\theta (x) = \theta_0 + \theta_1\,x$$

* Where 
  * \\(h_\theta (x)\\) is the hypothesis function, also denoted as \\(h(x)\\) sometimes
  * \\(x\\) is the independent variable
  * \\(\theta_0\\) and \\(\theta_1\\) are the parameters of the  linear regression that need to be learnt

### Parameters of the Hypothesis
In the above case of the hypothesis, \\(\theta_0\\) and \\(\theta_1\\) are the parameters of the hypothesis. In case of a univariate linear regression, \\(\theta_0\\) is the **y-intercept** and \\(\theta_1\\) is the **slope** of the line.

Different values for these parameters will give different hypothesis function based on the values of slope and intercepts.

### Cost Function of Linear Regression

![Linear Regression](/assets/2017-08-11-cost-function-of-linear-regression/fig-1-linear-regression.png?raw=true){:height="300px" width="450px"}

Assume we are given a dataset as plotted by the 'x' marks in the plot above. The aim of the linear regression is to find a line similar to the blue line in the plot above that fits the given set of training example best. Internally this line is a result of the parameters \\(\theta_0\\) and \\(\theta_1\\). So the objective of the learning algorithm is to find the best parameters to fit the dataset i.e. **choose \\(\theta_0\\) and \\(\theta_1\\) so that \\(h_\theta (x)\\) is close to y for the training examples (x, y)**. This can be mathematically represented as,

$$minimize_{\theta_0, \theta_1} {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2$$

* Where
  * \\(h_\theta(x^{(i)}) = \theta_0 + \theta_1\,x^{(i)} \\)
  * \\((x^{(i)},y^{(i)})\\) is the \\(i^{th}\\) training data
  * m is the number of training example
  * \\({1 \over 2}\\) is a constant that helps cancel 2 in derivative of the function when doing calculations for gradient descent

So, **cost function** is defined as follows, 

$$J(\theta_0, \theta_1) = {1 \over 2m} \sum_{i=1}^m \left( \hat{y^{(i)}} - y^{(i)} \right)^2 = {1 \over 2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2$$

which is basically \\( {1 \over 2} \bar{x}\\) where \\(\bar{x}\\) is the mean of squares of \\(h_\theta(x^{(i)}) - y^{(i)}\\), or the difference between the predicted value and the actual value.

And **learning objective is to minimize the cost function** i.e.

$$minimize_{\theta_0, \theta_1} J(\theta_0, \theta_1)$$

This cost function is also called the **squared error function** because of obvious reasons. It is the most commonly used cost function for linear regression as it is simple and performs well.


## REFERENCES:

<small>[Machine Learning: Coursera - Cost Function](https://www.coursera.org/learn/machine-learning/lecture/rkTp3/cost-function){:target="_blank"}</small>

<small>[Linear Regression: Wikipedia - Cost Function](https://en.wikipedia.org/wiki/Linear_regression){:target="_blank"}</small>
