---
title:  "Modern Digital Signal Processing"
date:   2024-06-12 05:00:00 +0200
categories: math
tags: math
math: true
---

[video lectures](https://www.bilibili.com/video/BV1ga4y157L5/)

Textbook:

- S.M.kay, fundamental of statistical signal processing vol i ii, this book is easy to understand.
- S. Haykin: adaptive filter theory, fifth edition.
- Petre Stoica and Randolph Moses: spectral analysis of signal
- Murphy, machine learning

probability is defined on the subsets of sample spaces

$$
P(A \cup B) = P(A) + P(B), A \cap B = \emptyset
$$

$$
\begin{align}
& \forall A_1, A_2, \dots, A_k \dots \subseteq \Omega, A_i \cap A_j = \emptyset, \forall i,j\\
& P(\bigcup\limits_{k=1}^{\infty} A_k) = \sum_{k=1}^{\infty} P(A_k), \text{(countable additivity)}
\end{align}
$$

$$
P(\bigcup\limits_{k=1}^{\infty} A_k) = \sum_{k=1}^{\infty} P(A_k) - \sum_{i < j}P(A_i \cap A_j) + \sum_{i<j<k} P(A_i \cap A_j \cap A_k) - \dots \text{(inclusive exclusive)}
$$

example for using inclusive exclusive: assuming n persons has n hats, now they randomly throw the hats and get one, what is the probability such that no one get the correct hat?

Let $$P(A_k)$$ be the probability that person $$k$$ get the correct hat, obviously

$$
P(A_k) = \dfrac{(n-1)!}{n!} = \dfrac{1}{n}
$$

the probability that no one get the correct hat

$$
P(\overline{A_1} \cap \overline{A_2} \cap \dots \cap \overline{A_n})
$$

using De Morgen's law

$$
P(\overline{A_1 \cup A_2 \cup \dots \cup A_n}) = 1 - P(A_1 \cup \dots \cup A_n)
$$

$$
P(A_1 \cup \dots \cup A_n) = \sum_{k=1}^{n} P(A_k) - \sum_{i<j}P(A_i \cap A_j) + \sum_{i<j<k}P(A_i \cap A_j \cap A_k) - \dots
$$

where

$$
\begin{align}
P(A_k) &= \dfrac{(n-1)!}{n!} = \dfrac{1}{n}\\
P(A_i \cap A_j) &= \dfrac{(n-2)!}{n!} = \dfrac{1}{n(n-1)}\\
P(A_i \cap A_j \cap A_k) &= \dfrac{(n-3)!}{n!} = \dfrac{1}{n(n-1)(n-2)}\\
& \vdots
\end{align}
$$

$$
\begin{align}
P(A_1 \cup \dots \cup A_n) &= n \cdot \dfrac{1}{n} - \binom{n}{2} \dfrac{1}{n(n-1)} + \binom{n}{3} \dfrac{1}{n(n-1)(n-2)} - \dots\\
&= 1 - \dfrac{1}{2!} + \dfrac{1}{3!} - \dots
\end{align}
$$

the probability is $$ 1 - P(A_1 \cup \dots \cup A_n )= \dfrac{1}{2!} - \dfrac{1}{3!} + \dfrac{1}{4!} - \dots$$

**independent**

$$
P(AB) = P(A) \cdot P(B)
$$


**conditional probability**

$$
P(B|A) = P(AB)/P(A)
$$

conditional probability is also a probability, defined on a new sample space, the original sample space is $$\Omega$$, the new sample space is $$A$$.
related name for conditional inclusing prior.

if $$A$$ and $$B$$ are independent, $$P(B\vert A) = P(B)$$, meaning knowing $$A$$ doesn't give information regarding $$B$$.


**total probability formula**

if $$A_i \cap A_j = \emptyset$$ and $$\bigcup\limits_{k=1}^n A_k = \Omega$$

$$
P(B) = P(B|A_1)P(A_1) + \dots + P(B|A_n)P(A_n)
$$

p1 2 hours
