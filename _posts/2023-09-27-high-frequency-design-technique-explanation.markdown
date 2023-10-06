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



# Plane Wave

## In Lossless Media

### Example 1

assume $$E_y = E_z = \dfrac{\partial E_x}{\partial x} = \dfrac{\partial E_x}{\partial y} = 0$$

$$
\dfrac{d^2 E_x(z)}{dz^2} + k^2 E_{x}(z) = 0
$$

$$
E_x(z) = E_0^+ e^{-jkz} + E_0^{-} e^{jkz}
$$

Then the magnatic filed can be derived from Maxwell's equation, we don't have to solve the differential equation again

$$
\nabla \times \vec{E} = -j\omega\mu \vec{H}
$$

For example, if $$E_x(z) = E_0^+ e^{-jkz} = E_x^+$$

$$
\begin{cases}
H_x^+ = 0\\
H_y^+ = \dfrac{k}{\omega \mu}E_x^+ = \dfrac{1}{\eta} E_x^+\\
H_z^+ = 0
\end{cases}
$$

where

$$
\eta = \sqrt{\dfrac{\mu}{\eta}}
$$
