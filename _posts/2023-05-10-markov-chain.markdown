---
title:  "Markov Chain"
date:   2023-05-10 09:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 13-18](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

# Markov Chain

## Markov property:


We discuss Distrete time, discrete states random process

$$
\{X_n\}_{n=0}^{\infty}, \quad X_k \in S = \{x_1, x_2, \dots \} \text{ (finite or countably infinite) }
$$

Markov property assumes

$$
P(X_n = x_n \vert X_{n-1} = x_{n-1}, \dots, X_0 = x_0) = P(X_{n}=x_n \vert X_{n-1}=x_{n-1})
$$

then


$$
\begin{align}
&P(X_n=x_n, \dots, X_0=x_0) = P(X_n=x_n \vert X_{n-1}=x_{n-1}, \dots, X_0=x_0) P(X_{n-1}=x_{n-1}, \dots, X_0=x_0)\\
=& P(X_n=x_n \vert X_{n-1}=x_{n-1}, \dots, X_0=x_0) P(X_{n-1}=x_{n-1} \vert X_{n-2}=x_{n-2}, \dots, X_0=x_{0}) P(X_{n-2}=x_{n-1}, \dots, X_0=x_0)\\
=& \Big( \prod_{k=1}^n P(X_k=x_k \vert X_{k-1}=x_{k-1}, \dots, X_0=x_0) \Big) P(X_0 = x_0)\\
=& \Big(\prod_{k=1}^n P(X_k = x_k \vert X_{k-1} = x_{k-1})\Big) P(X_0=x_0)
\end{align}
$$
