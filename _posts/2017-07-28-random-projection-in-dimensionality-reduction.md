---
layout: post
title: Random Projection in Dimensionality Reduction
categories: []
tags: [01. Concepts]
description:
comments: true
mathjax: true
---

### Introduction
Random Projections have emerged as a powerful method for dimensionality reduction. Theoretical results indicate that it **preserves distances** quite nicely but empirical results are **sparse**. It is often employed in dimensionality reduction in both **noisy and noiseless data** especially image and text data. Results of projecting on **random lower-dimensional subspace** yields results comparable to conventional methods like PCA etc but using it is **computationally less expensive** than the traditional alternatives.

### Curse of Dimensionality

* High dimensional data **restricts the choice** of data processing methods.
* A statistically optimal way of dimensionality reduction is to project the data onto a lower-dimensional orthogonal subspace that **captures as much of the variations of the data as possible**. The most widely used method of this sort is PCA (**Principal Component Analysis**).
* Drawback of PCA is however that it is computationally expensive to calculate as the dimensions of data increases.

### Johnson-Lindenstrauss Lemma

**If points in vector space are projected onto a randomly selected subspace of suitably high dimensions, then the distances between the points are approximately preserved.**

### Random Projection (RP)

* In RP, a higher dimensional data is projected onto a lower-dimensional subspace **using a random matrix whose columns have unit length**.
* RP is computationally efficient, yet accurate enough for this purpose as it does not introduce a significant distortion in the data.
* It is not sensitive to impulse noise. So RP is promising alternative to some existing methods in **noise reduction** (like mean filtering) too.

* The original d-dimensional data is projected to a k-dimensional \\((k \lt \lt d)\\) through the origin, using a random \\(k * d\\) matrix R whose columns have unit lengths. It is given by

$$X_{k*N}^{RP} = R_{k*d} \, X_{d*N} \tag{1}$$

  * Where 
    * \\(X_{k*N}^{RP}\\) is the k-dimensional random projection
    * \\(R_{k*d}\\) is the random matrix used for transformation
    * \\(X_{d*N}\\) are the original set of N d-dimensional observations

* The key idea of random mapping arises from **Johnson-Lindenstrauss Lemma**

* **Complexity**
  * Forming a random matrix R and projecting d * N data matrix X into k dimensions is of the order **O(dkN)**
  * If X is a sparse matrix with c non-zero values per column, then the complexity is **O(ckN)**

* Theoretically, equation (1) is not a projection because R is generally not orthogonal. A linear mapping like (1) can cause significant distortion in data if R is not orthogonal. **Orthogonalizing R is computationally expensive.**

* Instead of orthogonalizing, RP relies on the result presented by Hecht-Neilsen i.e. **In a high dimensional space, there exists a much larger number of almost orthogonal than orthogonal directions.** Thus the vectors with random directions might be sufficiently close to orthogonal, and equivalently \\(R^TR\\) would approximate an identity matrix.

* Experimental results show the mean squared difference between \\(R^TR\\) and identity matrix is around **1/k per element**.

* Euclidean distances between \\(x_1\\) and \\(x_2\\) in the original large-dimensional space is given by

$$||x_1 - x_2||$$

* After RP, this distance can be approximated by **scaled Euclidean distance** of these vectors in reduced spaces:

$$\sqrt{d \over k} || Rx_1 - Rx_2 ||$$

  * Where d is the original and k is the reduced dimensionality of the data set and **scaling factor** \\(\sqrt{d \over k}\\) takes into account the decrease in dimensionality of the data set.

* According to **Johnson-Lindenstrauss Lemma**, the expected norm of a projection of unit vector onto a random subspace through origin is \\(\sqrt{k \over d}\\).

* The choice of R matrix is generally such that \\(r_{ij}\\) of R are often **Gaussian Distributed** although many other choices are available. There is a peculiar result which says one can use the following distribution which is much simpler.

$$
  \begin{equation}
    X= \sqrt{3} * 
    \begin{cases}
      +1 & \text{ with probability }\ {1\over6} \\
      0 & \text{ with probability }\ {2\over3} \\
      -1 & \text{ with probability }\ {1\over6}
    \end{cases}
    \tag{2}
  \end{equation}
$$

* Practically, all zero mean, unit variance distributions of \\(r_{ij}\\) would give a mapping that satisfies the Johnson-Lindenstrauss Lemma.

* Equation (2) helps reduce the computational expense even further.

## REFERENCES

<small>[Random projection in dimensionality reduction: Applications to image and text data](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.24.5135&rep=rep1&type=pdf){:target="_blank"}</small>

<small>[Various Embeddings on Digits Data - Python Sklearn](http://scikit-learn.org/stable/auto_examples/manifold/plot_lle_digits.html#sphx-glr-auto-examples-manifold-plot-lle-digits-py){:target="_blank"}</small>