---
title:  "Stochastic Process 14"
date:   2023-05-10 08:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 14](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

From last time

- Markov property:

&nbsp; $$A: \text{ past } \quad B: \text{ Now } \quad C: \text{ Future }$$

$$
P(C \vert BA) = P(C \vert B) \iff P(CA \vert B) = P(C \vert B) P(A \vert B)
$$

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

The transition probability $$ P(X_n = x_n \vert X_{n-1} = X_{n-1}) $$ is important, more general, for $$n > m$$

$$
P(X_n = x_n \vert X_m = x_{m}) = P(X_n = j \vert X_m = i) = P_{ij}(n, m)
$$

It can be understood as, transit from state $$i$$ to $$j$$, from time $$m$$ to time $$n$$.

## Stationary Assumption

We assume $$\forall n > m \ge 0$$

$$
P_{i,j}(n,m) = P_{i,j}(n-m)
$$

## Chapman-Kolmogorov Equation (C-K)

$$
\forall m < n, \quad P_{ij}(n) = \sum_{k} P_{ik}(m)P_{kj}(n-m)
$$

Proof:

$$
\begin{align}
P_{ij}(n) &= P(X_n = j \vert X_0 = i)\\
&= \sum_{k} P(X_n = j, X_m = k \vert X_0 = i)\\
&= \sum_{k} P(X_n = j \vert X_m = k, X_0 = i) P(X_m=k \vert X_0 = i)\\
&= \sum_{k} P(X_n = j \vert X_m = k) P(X_m = k \vert X_0 = i)\\
&= \sum_{k} P_{kj}(n-m) P_{ik}(m)
\end{align}
$$

Matrix Form

$$
P(n) = P(m)P(n-m) = (P(1))^n
$$

To diagnolize such general matrix, we need to use Jordan canonical form.

## Qualitative Understanding

- Reachable: $$i \to j: \quad \exists n, P_{ij}(n) > 0$$.

- Commutatable: $$i \leftrightarrow j \quad \iff \quad i \to j, j \to i$$

1hr32min
