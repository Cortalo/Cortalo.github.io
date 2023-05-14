---
title:  "Stochastic Process 15"
date:   2023-05-13 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 15](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

Markov chain

$$
\{X_n\}_{n=0}^{\infty}, \quad X_k \in S = \{x_1, x_2, \dots \} \text{ (finite or countably infinite) }
$$

C-K equatoin

$$
\forall m < n, \quad P_{ij}(n) = \sum_{k} P_{ik}(m)P_{kj}(n-m)
$$

First passage probability


$$
P_{ij}(n) = \sum_{k=1}^n f_{ij}(k) P_{jj}(n-k)
$$

## Recurrent States

&nbsp; state $$i$$ is recurrent $$\iff \sum_{k=1}^{\infty} f_{ii}(k) = 1$$

&nbsp; state $$i$$ is non-recurrent $$\iff \sum_{k=1}^{\infty} f_{ii}(k) < 1$$

Confusion: how to show $$\sum_{k=1}^{\infty} \le 1$$?

$$
P_{ij}(n) = \sum_{k=1}^n f_{ij}(k) P_{jj}(n-k)
$$

The equation above is in convolution form. We define

$$
\begin{align}
P_{ij}(z) &= \sum_{n=0}^{\infty} P_{ij}(n) z^{n}\\
f_{ij}(z) &= \sum_{n=1}^{\infty} f_{ij}(n) z^{n}
\end{align}
$$

we use the convention

$$
\begin{align}
P_{ij}(0) &= \delta_{ij}\\
f_{ij}(0) &= 0
\end{align}
$$

we have

$$
\begin{align}
P_{ij}(z)=&\sum_{n=0}^{\infty} P_{ij}(n) z^n = P_{ij}(0) + \sum_{n=1}^{\infty} \Big( \sum_{k=1}^{n} f_{ij}(k) P_{jj}(n-k) \Big) z^{n}\\
=& P_{ij}(0) + \sum_{k=1}^{\infty} \sum_{n=k}^{\infty} f_{ij}(k) z^{k} P_{jj}(n-k) z^{n-k}\\
=& P_{ij}(0) + \sum_{k=1}^{\infty} f_{ij}(k) z^k \sum_{n=k}^{\infty} P_{jj}(n-k)z^{n-k}\\
=& P_{ij}(0) + \sum_{k=1}^{\infty} f_{ij}(k) z^k P_{jj}(z)\\
=& \delta_{ij} + F_{ij}(z)P_{jj}(z)
\end{align}
$$

if $$i=j$$

$$
P_{ii}(z) = 1 + F_{ii}(z)P_{ii}(z)
$$

$$
P_{ii}(z) = \dfrac{1}{1-F_{ii}(z)}
$$

thus criterion for recurrent:

&nbsp; state $$i$$ is recurrent $$\iff \sum_{k=0}^{\infty} P_{ii}(k) = \infty$$

&nbsp; state $$i$$ is non-recurrent $$\iff \sum_{k=0}^{\infty} P_{ii}(k) < \infty$$

- If $$i \leftrightarrow j$$, then $$i, j$$ are both recurrent or non-recurrent.

$$
\exists m, n, \quad P_{ij}(m) > 0, P_{ji}(n) > 0
$$

$$
\begin{align}
&\sum_{k=0}^{\infty} P_{ii}(k) \ge \sum_{k=0}^{\infty} P_{ii}(m+n+k)\\
\ge & \sum_{k=0}^{\infty} P_{ij}(m) P_{jj}(k) P_{ji}(n)\\
\ge & P_{ij}(m) \Big( \sum_{k=0}^{\infty} P_{jj}(k) \Big) P_{ji}(n)
\end{align}
$$

- If $$i$$ is non-recurrent, $$P_{ii}(n) \to 0 (n \to \infty)$$.

- If $$i$$ is non-recurrent, $$\forall k , P_{ki}(n) \to 0 (n \to \infty)$$.

This is because

$$
P_{ki}(z) = \delta_{ki} + F_{ki}(z)P_{ii}(z)
$$

and for non-recurrent $$i$$, both $$F_{ki}(0)$$ and $$P_{ii}(0)$$ converges.

- If finite states, there must be recurrent state.

This is because the summation of row is 1: $$\sum_{j} P_{ij}(n) = 1$$, for finite states, it is impossible for all $$i$$ to be non-recurrent states.

$$
\lim_{n\to \infty} \sum_{j}^{N} P_{ij}(n) = 0 = 1
$$

- Finite states + irreducible: all states are recurrent.

This is because if it is irreducible, all states are commutatable.

Example: random walk with equal probability. For 1-d and 2-d, all the states are recurrent; for 3-d and more, all the states are non-recurrent.

- &nbsp; If $$i$$ is recurrent, and $$i \to j$$, then $$j \to i$$. Thus $$j$$ is recurent states. Recurrent states only goes to recurrent states.

To prove that, we first define the probability, starting from $$i$$, then come back to $$i$$ at least $$m$$ times

$$
g_{ii}(m) = P(\#\{k: X_k=i, k \ge 1\} \ge m \vert X_0 = i)
$$

we want to find how to derive $$g_{ii}(m)$$ from $$g_{ii}(m-1)$$

$$
g_{ii}(m) = \sum_{k=1}^{\infty} f_{ii}(k) g_{ii}(m-1) = g_{ii}(m-1) \Big( \sum_{k=1}^{\infty} f_{ii}(k) \Big)
$$

$$
g_{ii}(1) = F_{ii}(0) = f_{ii}
$$

$$
g_{ii}(m) = (f_{ii})^m
$$

$$
g_{ii} = \lim_{m \to \infty} g_{ii}(m) =
\begin{cases}
1& \quad i \text{ recurrent }\\
0& \quad i \text{ non-recurrent }
\end{cases}
$$

We define

$$
g_{ij}(m) = P(\#\{k: X_k=j, k \ge 1\} \ge m \vert X_0 = i)
$$

- If $$i$$ is recurrent, and $$\exists m \ge 1, P_{ij}(m) > 0$$, then $$\lim_{n \to \infty} g_{ji}(n) = 1$$

$$
1 = g_{ii} = \sum_{j} P_{ij}(m) g_{ji}
$$

$$
1 = \sum_{j} P_{ij}
$$

$$
0 = \sum_{j} P_{ij}(m)(g_{ji} - 1)
$$

We not only know $$j \to i$$, we even know $$\lim_{n\to \infty} g_{ji} = 1$$
