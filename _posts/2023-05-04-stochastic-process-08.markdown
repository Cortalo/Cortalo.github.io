---
title:  "Stochastic Process 08"
date:   2023-05-04 12:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 08](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

# Nonlinear vs. Gaussian

## One Random Variable

For $$Y \sim N(0, \sigma^2)$$, let's calculate $$E(Y^n)$$

$$
E(Y^{2k}) = (2k-1)!! \sigma^{2k}
$$

where

$$
(2k-1)!! = (2k-1) (2k-3) \dots 1
$$

$$
\begin{align}
E(Y^2) &= \sigma^2\\
E(Y^4) &= 3 \sigma^4\\
E(Y^6) &= 15 \sigma^6
\end{align}
$$

## Multiple Random Variables

$$
(X_1, X_2, X_3, X_4) \sim N(0, \Sigma), X \in \mathbb{R}
$$

then

$$
E(X_1 X_2 X_3 X_4) = E(X_1 X_2) E(X_3 X_4) + E(X_1 X_3) E(X_2 X_4) + E(X_1 X_4) E(X_2 X_3)
$$

This is for real variables.
For complex variables it is slightly different.
