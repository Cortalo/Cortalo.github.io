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
