---
title:  "Stochastic Process 13"
date:   2023-05-10 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 13](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

1 hr 33 min

# Markov Property

We know

$$
\begin{align}
&P(X_n=x_n, \dots, X_0=x_0) = P(X_n=x_n \vert X_{n-1}=x_{n-1}, \dots, X_0=x_0) P(X_{n-1}=x_{n-1}, \dots, X_0=x_0)\\
=& P(X_n=x_n \vert X_{n-1}=x_{n-1}, \dots, X_0=x_0) P(X_{n-1}=x_{n-1} \vert X_{n-2}=x_{n-2}, \dots, X_0=x_{0}) P(X_{n-2}=x_{n-1}, \dots, X_0=x_0)\\
=& \Big( \prod_{k=1}^n P(X_k=x_k \vert X_{k-1}=x_{k-1}, \dots, X_0=x_0) \Big) P(X_0 = x_0)
\end{align}
$$

If we assume

$$
P(X_n = x_n \vert X_{n-1} = x_{n-1}, \dots, X_0 = x_0) = P(X_{n}=x_n \vert X_{n-1}=x_{n-1})
$$


$$
\begin{align}
P(X_n=x_n, \dots, X_0=x_0) = \Big(\prod_{k=1}^n P(X_k = x_k \vert X_{k-1} = x_{k-1})\Big) P(X_0=x_0)
\end{align}
$$

Random process can be catagorized as discrete time or continuous time; discrete states or continuous states

First we discuss discrete-time Markov chain (discrete-time and discrete states)

Formally, Markov property can be state as

$$
\forall n \in \mathbb{N} \quad P(X_n=x_n \vert X_{n-1}=x_{n-1}, \dots, X_1 = x_1, X_0 = x_0) = P(X_{n}=x_n \vert X_{n-1}=x_{n-1})
$$

If we note $$A, B, C$$ to be past, current, future, then

$$
\begin{align}
A &= X_{n-2}, \dots X_{1}\\
B &= X_{n-1}\\
C &= X_{n}
\end{align}
$$

Then Markov property is

$$
P(C \vert B A) = P(C \vert B)
$$

It is equivalent to

$$
P(CA \vert B) = P(C \vert B) P(A \vert B)
$$

with the interpretation of when current is known, past and future are independent.

$$
[P(C \vert B A) = P(C \vert B)] \implies  P(CA \vert B) = P(C \vert B) P(A \vert B)
$$

$$
\begin{align}
&P(C A \vert B) = \dfrac{P(CAB)}{P(B)} = \dfrac{P(CAB)}{P(AB)} \dfrac{P(AB)}{P(B)}\\
=& \dfrac{P(CBA)}{P(BA)} \dfrac{P(AB)}{P(B)} = P(C \vert BA) P(A \vert B)\\
=& P(C \vert B) P(A \vert B)
\end{align}
$$

$$
[P(CA \vert B) = P(C \vert B) P(A \vert B)] \implies [P(C \vert B A) = P(C \vert B)]
$$

$$
\begin{align}
&P(C \vert B A) = \dfrac{P(CBA)}{P(BA)} = \dfrac{P(CAB)}{P(B)} \dfrac{P(B)}{P(BA)}\\
=& P(CA \vert B) / P(A \vert B) = P(C \vert B)
\end{align}
$$

## Other Equations

Obviously

$$
P(X_n \in A \vert X_{n-1}=x_{n-1}, \dots, X_1 = x_1) = P(X_n \in A \vert X_{n-1}=x_{n-1})
$$

$$
\sum_{x_n \in A} P(X_n = x_n \vert X_{n-1}=x_{n-1}, \dots, X_{1} = X_1) = \sum_{x_n \in A} P(X_n = x_n \vert X_{n-1}=x_{n-1}) = P(X_n \in A \vert X_{n-1}=x_{n-1})
$$

We also have

$$
P(X_{n}=x_n \vert X_{n-1}=x_{n-1}, X_{n-2}\in S_{n-2}, \dots, X_{1} \in S_1) = P(X_n = x_n \vert X_{n-1}=x_{n-1})
$$

using the equivalence of $$P(C \vert BA) = P(C \vert B) \iff P(CA \vert B) = P(C \vert B) P(A \vert B)$$, we only need to show

$$
P(X_n = x_n, X_{n-2}\in S_{n-2}, \dots X_{1} \in S_1 \vert X_{n-1} = x_{n-1}) = P(X_n=x_n \vert X_{n-1}=x_{n-1} ) P(X_{n-2} \in S_{n-2} \dots X_{1} \in S_1 \vert X_{n-1}=x_{n-1})
$$

The importance thing is we must exactly know $$X_{n-1}=x_{n-1}$$, this cannot be a set.
