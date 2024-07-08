---
title:  "Signal And System 01"
date:   2022-12-10 05:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

# Signal and System

**convolution is commutative: proof**

from

$$
\sum_{k=-\infty}^{\infty} x[k]h[n-k]
$$

let $$k=n-r$$

$$
\sum_{r=-\infty}^{\infty} x[n-r]h[r]
$$

**LTI system eigen function: proof**

$$
\begin{align}
y(t) &= \int_{-\infty}^{\infty} h(\tau) x(t-\tau) d\tau\\
&= \int_{-\infty}^{\infty} h(\tau) e^{s(t-\tau)} d\tau\\
&= e^{st} \int_{-\infty}^{\infty} h(\tau)e^{-s\tau} d\tau
\end{align}
$$

$$
\begin{align}
y[n] &= \sum_{k=-\infty}^{\infty} h[k]x[n-k]\\
&= \sum_{k=-\infty}^{\infty} h[k]z^{n-k}\\
&= z^n \sum_{k=-\infty}^{\infty} h[k]z^{-k}
\end{align}
$$
