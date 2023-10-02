---
title:  "High Frequency Design Technique Explanation"
date:   2023-09-27 08:00:00 +0200
categories: EM
tags: EM
math: true
---

# Introduction

## AC Analysis

For a total impedance $$Z(s)$$ consists of $$R, L$$ and $$C$$, assume all the initial conditions of $$L$$ and $$C$$ are $$0$$, then

$$
V(s) = I(s)Z(s)
$$

assume when $$t\ge 0$$, we apply current $$i(t)=I \cos(\omega t + \varphi)$$, then the voltage response can be calculated by

$$
v(t) = \int_0^t z(\tau) I \cos\left(\omega(t-\tau) + \varphi\right)d\tau
$$

we are interested in the response when $$t\to\infty$$.
Instead of directly calculating the above integration, we calculate

$$
y(t) = I \int_0^t z(\tau)e^{j\omega(t-\tau)+\varphi}d\tau = e^{j\omega t} I e^{j\varphi} \int_0^t z(\tau)e^{-j\omega \tau} d\tau
$$

when $$t \to \infty$$

$$
y(t) \to e^{j\omega t} I e^{j\varphi} \int_0^\infty z(\tau)e^{-j\omega \tau}d\tau = e^{j\omega t} I e^{j\varphi} Z(j\omega)
$$

then

$$
\begin{cases}
v(t) = \mathrm{Re}\left(y(t)\right) \to V \cos(\omega t + \theta)\\
V e^{j\theta} = I e^{j\varphi} \cdot Z(j\omega)
\end{cases}
$$

### Average Power Consumption

Assume

$$
\begin{cases}
v(t) = V \cos(\omega t)\\
i(t) = I \cos(\omega t + \theta)
\end{cases}
$$

$$
\overline{P} = \dfrac{1}{T} \int_0^{T} VI\cos(\omega t) \cos(\omega t + \theta) dt =
$$
