---
title:  "Stochastic Process 08"
date:   2023-05-04 12:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 08](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

# Nonlinear vs. Gaussian

## One Random Variable


For $$Y \sim N(0, \sigma^2)$$, let's calculate $$E(Y^n)$$

$$
E(Y^n) =
\begin{cases}
0, \quad n = 2k-1\\
(2k-1)!! \sigma^{2k}, \quad n = 2k
\end{cases}
$$

$$
\begin{align}
&\int_{-\infty}^{\infty} y^{2k} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) dy\\
=& -\sigma^2 \int_{-\infty}^{\infty} y^{2k-1} d\Big( \exp\big( - \dfrac{y^2}{2\sigma^2}\big) \Big)\\
=& -\sigma^2 y^{2k-1} \exp \big( -\dfrac{y^2}{2\sigma^2} \big) \Big\vert_{-\infty}^{\infty} + (2k-1)\sigma^2 \int_{-\infty}^{\infty} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) y^{2k-2} dy\\
=& (2k-1)\sigma^2 \int_{-\infty}^{\infty} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) y^{2k-2} dy
\end{align}
$$

Thus

$$
E(Y^{2k}) = (2k-1)\sigma^2 E(Y^{2k-2})
$$

Thus

$$
E(Y^{2k}) = (2k-1)!! \sigma^{2k}
$$

where

$$
(2k-1)!! = (2k-1) (2k-3) \dots 1
$$

$$
\begin{align}
E(Y^2) &= \sigma^2\\
E(Y^4) &= 3 \sigma^4\\
E(Y^6) &= 15 \sigma^6
\end{align}
$$

## Multiple Random Variables

$$
(X_1, X_2, X_3, X_4) \sim N(0, \Sigma), X \in \mathbb{R}
$$

then

$$
E(X_1 X_2 X_3 X_4) = E(X_1 X_2) E(X_3 X_4) + E(X_1 X_3) E(X_2 X_4) + E(X_1 X_4) E(X_2 X_3)
$$

This is for real variables.
For complex variables it is slightly different.

To prove this we use characteristic function

$$
E(X_1^{\alpha_{1}} \dots X_n^{\alpha_n}) = \dfrac{1}{j^{\alpha_1 + \dots + \alpha_n}} \frac{\partial^{\alpha_1 + \dots + \alpha_n}}{\partial \omega_1^{\alpha_1} \dots \partial \omega_n^{\alpha_n}} \Phi_{X_1, \dots, X_n}(\omega_1, \dots, \omega_n) \Big\vert_{\omega_1=\dots=\omega_n = 0}
$$

this is because

$$
\Phi_{X_1,\dots,X_n}(\omega_1, \dots, \omega_n) = E(\exp(j(\omega_1 X_1 + \dots + \omega_n X_n)))
$$

If we have 5 random variables with $$N(0, \Sigma)$$, we will have

$$
E(X_1 X_2 X_3 X_4 X_5) = 0
$$

If we have 6 random variables with $$N(0, \Sigma)$$, we will have 15 terms, as in the one random variable cases.

## Square Device

For W.S.S. Gaussian process $$X(t)$$, if $$Y(t) = (X(t))^2$$. How to compute $$R_Y(t,s)$$?

$$
R_Y(t,s) = E(Y(t)Y(s))= E(X^2(t)X^2(s))
$$

Since we know $$(X(t), X(t), X(s), X(s))$$ is Gaussian

$$
\begin{align}
R_Y(t,s) &= E(X(t)X(t))E(X(s)X(s)) + E(X(t)X(s))E(X(t)X(s)) + E(X(t)X(s)) + E(X(t)X(s))\\
&= (R_X(0))^2 + 2 (R_X(t-s))^2
\end{align}
$$

## Hard Limiter

$$
g(x) = \mathrm{sgn}(x) =
\begin{cases}
1, \quad x > 0\\
0, \quad x = 0\\
-1, \quad x < 0
\end{cases}
$$

We want to calculate $$R_Y(t,s)$$ for $$Y = g(X)$$, assuming $$X(t)$$ is a Gaussian process with zero mean.

$$
\begin{align}
R_Y(t,s) &= E(Y(t)Y(s)) = E(g(X(t)) \cdot g(X(s)))\\
&= 1 \cdot P(X(t)X(s) > 0) + (-1) \cdot P(X(t)X(s)) < 0
\end{align}
$$

we only need to calculate $$P(X(t)X(s) > 0)$$

$$
\begin{align}
&\Big( \int_{0}^{\infty}\int_{0}^{\infty} + \int_{-\infty}^{0} \int_{-\infty}^{0} \Big) f(x_1, x_2) d x_1 d x_2\\
=& \dfrac{1}{2\pi \sigma_1 \sigma_2 \sqrt{1 - \rho^2}} \Big( \int_{0}^{\infty}\int_{0}^{\infty} + \int_{-\infty}^{0} \int_{-\infty}^{0} \Big) \exp \bigg( -\dfrac{1}{2(1-\rho^2)} \Big(\big(\dfrac{x_1}{\sigma_1}\big)^2 + \big(\dfrac{x_2 }{\sigma_2}\big)^2 - 2\rho \big( \dfrac{x_1}{\sigma_1} \big) \big( \dfrac{x_2}{\sigma_2} \big) \Big) \bigg) d x_1 d x_2\\
=& \dfrac{1}{\pi \sigma_1 \sigma_2 \sqrt{1 - \rho^2}} \int_{0}^{\infty}\int_{0}^{\infty} \exp \bigg( -\dfrac{1}{2(1-\rho^2)} \Big(\big(\dfrac{x_1}{\sigma_1}\big)^2 + \big(\dfrac{x_2 }{\sigma_2}\big)^2 - 2\rho \big( \dfrac{x_1}{\sigma_1} \big) \big( \dfrac{x_2}{\sigma_2} \big) \Big) \bigg) d x_1 d x_2
\end{align}
$$

Let $$y_1 = x_1/\sigma_1, y_2 = x_2/\sigma_2$$

$$
\dfrac{1}{\pi \sqrt{1 - \rho^2}} \int_{0}^{\infty}\int_{0}^{\infty} \exp \Big( -\dfrac{1}{2(1-\rho^2)} (y_1^2 + y_2^2 - 2\rho y_1 y_2 ) \Big) d y_1 d y_2
$$

Let $$y_1 = u_1 + u_2, y_2 = u_1 - u_2$$

$$
\begin{align}
&(u_1 + u_2)^2 + (u_1 - u_2)^2 - 2 \rho (u_1 + u_2)(u_1 - u_2)\\
=& 2 (u_1^2 + u_2^2) - 2 \rho(u_1^2 - u_2^2)
\end{align}
$$

$$
d y_1 d y_2 = \big \vert \mathrm{det} \dfrac{\partial y}{\partial u} \big\vert d u_1 d u_2 = 2 d u_1 d u_2
$$

integration region becomes a right angle.

$$
\begin{align}
&\dfrac{2}{\pi \sqrt{1 - \rho^2}} \int\int \exp \Big( -\dfrac{1}{2(1-\rho^2)} (2(u_1^2 + u_2^2) - 2\rho (u_1^2 - u_2^2)) \Big) d u_1 d u_2\\
=&\dfrac{2}{\pi \sqrt{1 - \rho^2}} \int\int \exp \Big(- \big( \dfrac{u_1^2}{1+\rho}  + \dfrac{u_2^2}{1-\rho}\big) \Big) d u_1 d u_2
\end{align}
$$

Let $$u_1' = u_1/\sqrt{1+\rho}, u_2' = u_2/\sqrt{1-\rho}$$

$$
d u_1 d u_2 = \sqrt{1-\rho^2} d u_1' d u_2'
$$

integration region becomes a slightly modified angle, with points $$(1/\sqrt{1+\rho},1/\sqrt{1-\rho}), (1/\sqrt{1+\rho}, -1/\sqrt{1-\rho})$$

$$
\dfrac{2}{\pi} \int\int \exp \big(- (u_1'^2 + u_2'^2) \big) d u_1' d u_2'
$$

then change to polar axis

$$
\dfrac{2}{\pi} \int_{0}^{\infty}\int_{-\phi}^{\phi} \exp \big(- r^2 \big) r dr d \theta = \dfrac{2\phi}{\pi}
$$

$$
\tan \phi = \dfrac{1/\sqrt{1-\rho}}{1/\sqrt{1+\rho}} = \sqrt{\dfrac{1+\rho}{1-\rho}}
$$

$$
P(X(t)X(s) > 0) = \dfrac{2}{\pi} \arctan \sqrt{\dfrac{1+\rho}{1-\rho}}
$$

use tangent half-angle formula

$$
\cos(2\phi) = \dfrac{1 - \tan^2\phi}{1 + \tan^2\phi} = \dfrac{1 - \dfrac{1+\rho}{1-\rho}}{1 + \dfrac{1+\rho}{1-\rho}} = -\rho
$$


$$
P(X(t)X(s) > 0) = \dfrac{2}{\pi} \arctan \sqrt{\dfrac{1+\rho}{1-\rho}} = \dfrac{1}{\pi} \arccos(-\rho)
$$

using $$ \arcsin(x) + \arccos(x) = \dfrac{\pi}{2} $$

$$
P(X(t)X(s) > 0) = \dfrac{1}{\pi} \arccos(-\rho) = \dfrac{1}{\pi} (\dfrac{\pi}{2} - \arcsin(-\rho)) = \dfrac{1}{2} + \dfrac{1}{\pi} \arcsin(\rho)
$$

$$
P(X(t)X(s) < 0) = \dfrac{1}{2} - \dfrac{1}{\pi} \arcsin(\rho)
$$

$$
R_Y(t,s) = \dfrac{2}{\pi} \arcsin(\rho) = \dfrac{2}{\pi} \arcsin \Big( \dfrac{R_X(t-s)}{R_X(0)} \Big)
$$

It is easy to see $$Y$$ is W.S.S.

## Price's Theorem

&nbsp; $$ (X_1, X_2) \sim N(0, 0, \sigma_1^2, \sigma_2^2, \rho) $$.

$$
\dfrac{\partial E(g(X_1, X_2))}{\partial \rho} = \sigma_1 \sigma_2 E \Big( \dfrac{\partial^2 g(X_1, X_2)}{\partial X1 \partial X_2} \Big)
$$

### Price's Theorem for Hard Limiter

$$
g(X_1, X_2) = \mathrm{sgn}(X_1) \mathrm{sgn}(X_2)
$$

$$
E(g(X_1, X_2)) = E(\mathrm{sgn}(X_1) \mathrm{sgn}(X_2))
$$

$$
\dfrac{\partial^2 g(X_1, X_2)}{\partial X1 \partial X_2} = 4 \delta(X_1) \delta(X_2)
$$

$$
\dfrac{\partial E}{\partial \rho} = 4\sigma_1 \sigma_2 E(\delta(X_1) \delta(X_2))
$$

$$
\begin{align}
E(\delta(X_1) \delta(X_2)) &= \dfrac{1}{2\pi \sigma_1 \sigma_2 \sqrt{1 - \rho^2}} \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} \exp \bigg( -\dfrac{1}{2(1-\rho^2)} \Big(\big(\dfrac{x_1}{\sigma_1}\big)^2 + \big(\dfrac{x_2 }{\sigma_2}\big)^2 - 2\rho \big( \dfrac{x_1}{\sigma_1} \big) \big( \dfrac{x_2}{\sigma_2} \big) \Big) \bigg) \delta(x_1) \delta(x_2) d x_1 d x_2\\
&= \dfrac{1}{2\pi \sigma_1 \sigma_2 \sqrt{1 - \rho^2}}
\end{align}
$$

$$
\dfrac{\partial E}{\partial \rho} = \dfrac{2}{\pi} \dfrac{1}{\sqrt{1-\rho^2}}
$$

1hr 34min
