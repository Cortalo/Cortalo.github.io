---
title:  "Fourier Analysis 002 Proof of Fejer's Theorem"
date:   2022-10-31 16:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---


From [book Fourier Analysis](https://www.cambridge.org/core/books/fourier-analysis/132E61BE81FD1190F35F9631089CA132)

## Proof of Fejer's Theorem

### Theorem 1.5

(i)
*If $$f: \mathbb{T} \to \mathbb{C}$$ is Riemann integrable then, if $$f$$ is continuous at $$t$$,*

$$
\sigma_{n}(f,t) = \sum_{r=-n}^{n} \frac{n+1-|r|}{n+1} \hat{f}(r) \exp irt \to f(t)
$$

(ii)
*If $$f:\mathbb{T} \to \mathbb{C}$$ is continuous then*

$$
\sigma_{n}(f,t) = \sum_{r=-n}^{n} \frac{n+1-|r|}{n+1} \hat{f}(r) \exp irt \to f(t)
$$

*uniformly on $$\mathbb{T}$$.*


We start with the following remark.
Suppose $$f: \mathbb{T} \to \mathbb{C}$$ is Riemann integrable.
Then

$$
\begin{align}
\sigma_{n}(f,t) &= \sum_{r=-n}^{n} \frac{n+1-|r|}{n+1} \hat{f}(r) \exp irt\\
&= \sum_{r=-n}^{n} \frac{n+1-|r|}{n+1}\frac{1}{2\pi} \bigg(\int_{\mathbb{T}} f(x)\exp(-irx)dx\bigg) \exp irt\\
&= \frac{1}{2\pi}\int_{\mathbb{T}} f(x)\sum_{r=-n}^{n}\frac{n+1-|r|}{n+1} \exp(ir(t-x))dx\\
&= \frac{1}{2\pi} \int_{\mathbb{T}} f(x)K_n(t-x)dx
\end{align}
$$

where

$$
K_n(s) = \sum_{r=-n}^{n} \frac{n+1 - |r|}{n+1} \exp irs
$$

Further, making the substitution $$y = t-x$$, we have

$$
\begin{align}
\sigma_{n}(f,t) &= \frac{1}{2\pi} \int_{-\pi}^{\pi} f(x)K_n(t-x)dx\\
&= -\frac{1}{2\pi} \int_{t+\pi}^{t-\pi} f(t-y)K_n(y)dy\\
&= \frac{1}{2\pi} \int_{t-\pi}^{t+\pi}f(t-y)K_n(y)dy\\
&= \frac{1}{2\pi}\int_{\mathbb{T}}f(t-y)K_n(y)dy
\end{align}
$$

We are therefore led to examine the structure of $$K_n$$ in some detail.

### Lemma 2.1.


$$
\begin{align}
K_n(s) &= \frac{1}{n+1} \Bigg( \frac{\sin \frac{(n+1)s}{2}}{\sin \frac{s}{2}} \Bigg)^2 \quad \quad [s \ne 0]\\
K_n(0) &= n+1
\end{align}
$$


*Proof.*

If $$s \ne 0 $$ then

$$
\begin{align}
&\sum_{r=-n}^{n} (n+1-|r|) \exp irs\\
=& \bigg(\sum_{k=0}^{n} \exp i (k - \frac{n}{2})s\bigg)^2
\end{align}
$$


> Considering the number of situations of drawing two cards individually from two decks, the sum of two number gives $$x$$.
{: .prompt-tip }
