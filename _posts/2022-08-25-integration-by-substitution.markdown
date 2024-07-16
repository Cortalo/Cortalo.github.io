---
title:  "Integration by Subsitution"
date:   2022-08-25 19:30:00 +0200
categories: math
tags: calculus
math: true
---

### Example 01

$$
\begin{aligned}
\int_{1}^{2}xdx &= 4\int_{1}^{2}\frac{1}{2}x \cdot \frac{1}{2} dx \\
&= 4 \int_{1/2}^{1}t dt
\end{aligned}
$$

### Example 02

$$
\begin{aligned}
\int_{-\infty}^{\infty}\frac{dy}{a^2+y^2} &= -j\int_{-\infty}^{\infty}\frac{jdy}{a^2-(jy)^2} \\
&= -j\int_{C}\frac{dz}{a^2-z^2}
\end{aligned}
$$

### Example 03

$$
X(\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t} dt
$$

$$
X(t) = \int_{-\infty}^{\infty} x(u)e^{-jut} du
$$

$$
\omega = -u
$$

san jian shi:
- bei ji han shu
- ji fen bian liang
- shang xia xian

$$
X(t) = \int_{\dots}^{\dots} x(-\omega) e^{j\omega t} d(-\omega)
$$


$$
X(t) = \int_{\dots}^{\dots} x(-\omega) e^{j\omega t} (-1) d\omega
$$


$$
X(t) = \int_{\infty}^{-\infty} x(-\omega) e^{j\omega t} (-1) d\omega
$$
