---
title:  "Fourier Analysis 001 Introduction"
date:   2022-10-28 12:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

From [book Fourier Analysis](https://www.cambridge.org/core/books/fourier-analysis/132E61BE81FD1190F35F9631089CA132)

## Introduction

Suppose $$f$$ is a Riemann integrable function from $$0$$ to $$2\pi$$.

$$
\int_{0}^{2\pi} f(t)dt \quad \text{exists}
$$

Then we define the Fourier coefficients of $$f$$ by

$$
\hat{f}(r) = (2\pi)^{-1} \int_{0}^{2\pi} f(t)\exp(-irt)dt
$$

Mathematicians of the eighteenth century (Bernoulli, Euler, Lagrange, etc.) knew 'experimentally' that for some simple functions

$$
S_n(f,t)=\sum_{-n}^{n}\hat{f}(r)\exp irt \to f(t) \quad \text{ as } n \to \infty
$$

Fourier claimed that this was alwaus true and in a book of outstanding importance in the history of physics (*Theorie Analytique de la Chaleur*) showed how formulae of the kind $$\sum_{-\infty}^{\infty} \hat{f}(r)\exp irt$$ could be used to solve linear partial differential equations of the kind which dominated 19th century physics.

After several mathematicians (including Cauchy) has produced more or less fallacious proofs of convergence, Dirichlet took up the problem.
In a paper which set up new and previously undreamed of standards of rigour and clarity in analysis, he was able to prove convergence under quite general conditions.
For example, the following theorem is a consequence of his results.

### Theorem 1.1

*If $$f$$ is continuous and has a bounded continuous derivative except, possibly, at a finite number of points then $$S_n(f,t) = \sum_{-n}^{n}f(r)\exp irt \to f(t)$$ as $$n \to \infty$$ at all points $$t$$ where $$f$$ is continuous.*

However, it turned out that the conditions on $$f$$ could not be relaxed indefinitely for Du Bois-Reymond constructed the following counter example.

### Example 1.2

*There exists a continuous function $$f$$ such that $$\lim \sup_{n \to \infty} S_n (f,0) \infty$$.*

(Theorem 1.1 will be proved in Chapter 15 in the case $$f$$ everywhere continuous and in Chapter 16 in the general case, whilst Example 1.2 will be constructed in Chpater 18.)

A new question was thus posed.

### Question 1.3

*If $$f$$ is a continuous function from $$\mathbb{T}$$ to $$\mathbb{C}$$ then, given the Fourier coefficients $$\hat{f}(r)[r \in \mathbb{Z}]$$ of $$f$$, can we find $$f(t)$$ for $t \in \mathbb{T}$?*

To the surprise of everybody Fejer (then aged only 19) showed that the answer is yes.
He started from the observation that if a sequence $s_0, s_1, \dots$ is not terribly well behaved, its behaviour may be improved by considering averages $s_0, (s_0+s_1)/2, (s_0+s_1+s_2)/3, \dots$
This has, of course, been known since the time of Euler, but the first person to study the phenomenon in detail was Cesaro about then years before Fejer's discovery.

### Lemma 1.4

(i)*If $s_n \to s$ then $(n+1)^{-1}\sum_{j=0}^{n}s_j \to s*.

(ii)*There exist sequences $s_n$ such that $s_n$ does not tend to a limit but $(n+1)^{-1}\sum_{j=0}^{n}s_j$ does.*


<p style="text-align: right"> $\square$ </p>
