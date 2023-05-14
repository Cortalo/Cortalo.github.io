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

- Closed Set: let $$S$$ be the set of all states. $$C \subseteq S$$ is closed set $$\iff $$ $$i \in C, j \not\in C \implies i \not\to j$$.

After it goes into $$C$$, it will never left $$C$$. Recude $$S$$ to $$C$$ is called reduction. It is a complete Markov chain in $$C$$. However, it is possible for $$S$$ to have several non-overlaping closed sets.

- Irreducible $$S$$: no closed true subsets.

**Theorem:** Irreducible $$\iff \forall i, j, i \leftrightarrow j$$.

&nbsp; $$\Leftarrow$$ is trival.

To prove $$\implies$$. We define $$\forall i, A_i = \{j: i \to j\}$$. First we prove $$A_i$$ is closed. If this is true, for irreducible $$S$$, we know any $$A_i$$ should be $$S$$, thus any two states are commutatable.

If $$A_i$$ is not closed, then $$\exists j \in A_i, k \not\in A_i$$ such that $$j \to k$$. Then we know $$i \to j, j \to k$$, thus $$i \to k$$, thus $$k \in A_i$$, we have the contracdiction.

$$
P(1) =
\begin{pmatrix}
P_{11} & \dots & P_{1n}\\
\dots & \dots & \dots\\
P_{n1} & \dots & p_{nn}
\end{pmatrix}
$$

If it is reductable, we can convert $$P(1)$$ by interchange rows and columns (by label states by different numbers)

$$
\to
\begin{pmatrix}
A & B\\
0 & C
\end{pmatrix}
$$

$$
P(1)^n =
\begin{pmatrix}
* & *\\
0 & C^n
\end{pmatrix}
$$

Then similarly, $$C$$ may be convert to the form if $$C$$ is reductable.

Currently people didn't have easy ways to determine if $$P$$ is reductable or not, we need to traverse all the possible interchanging.

## First Passage

- First passage: $$f_{ij}(n) = P(X_n=j, X_{n-1}\ne j, X_{n-2}\ne j, \dots, X_1\ne j \vert X_0 = i)$$

We have

$$
P_{ij}(n) = \sum_{k=1}^n f_{ij}(k) P_{jj}(n-k)
$$

To prove it we first define first passage time: $$T = \min_{r} \{X_r = j \vert X_0 = i\}$$. $$T = k$$ means $$\{X_k=j, X_{k-1} \ne j, \dots X_{1} \ne j \vert X_0=i\}$$.


$$
\begin{align}
P_{ij}(n) &= P(X_n=j \vert X_0 = i)\\
&= \sum_{k=1}^{n} P(X_n=j, T=k \vert X_0=i)\\
&= \sum_{k=1}^{n} P(X_n=j \vert T=k, X_0=i) P(T=k \vert X_0=i)\\
&= \sum_{k=1}^{n} P(X_n=j \vert X_k=j, X_{k-1} \ne j, \dots, X_{1} \ne j , X_0 = i) P(X_k=j, X_{k-1}\ne j, \dots, X_{1}\ne j \vert X_0 = i)\\
&= \sum_{k=1}^n P(X_n=j \vert X_k = j) f_{ij}(k)\\
&= \sum_{k=1}^n f_{ij}(k)P_{jj}(n-k)
\end{align}
$$
