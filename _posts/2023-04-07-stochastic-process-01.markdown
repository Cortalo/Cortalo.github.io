---
title:  "Stochastic Process 01"
date:   2023-04-07 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 01](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

# Introduction

In stochastic process we study when there are multiple (possibily infinite) random variables.

For example, two random variables $$X, Y$$. For random variables, if we know their joint-pdf, we know everything (or it is impossible to know more).

$$
\begin{align}
f_{X,Y}(x,y) &= \dfrac{\partial^2}{\partial x \partial y} F_{X,Y}(x,y)\\
F_{X,Y}(x,y) &= P(X \le x, Y \le Y)
\end{align}
$$

## Correlation

Before we define correlation, let's do some examples.

- Example 01

Assume two random variables $$X,Y$$, the joint-pdf is spindle-shape, we can draw a line pass the origin, such that the joint-pdf fits the line best. The definition of the best fit is

$$
\alpha_{opt} = \min E ((Y-\alpha X)^2)
$$

we can do the calculation

$$
\begin{align}
E((Y-\alpha X)^2) &= E(Y^2) + \alpha^2 E(X^2) - 2 \alpha E (XY)
\end{align}
$$

take the derivate w.r.t $$\alpha$$

$$
2\alpha E(X^2) - 2 E(XY) = 0
$$

thus

$$
\alpha_{opt} = \dfrac{E(XY)}{E(X^2)}
$$

A quick note here, in this course we typically assume random variables on $$\mathbb{R}$$. If to deal with random variable on $$\mathbb{C}$$, it will be something similar to $$\dfrac{E(X \overline{Y})}{E(X^2)}$$.

- Example 01 Finish

Review inner product: an inner product $$\langle x, y \rangle \to \mathbb{R}$$ if and only if it satisfies

1. &nbsp; $$\langle x, y \rangle = \langle y, x \rangle$$

2. &nbsp; $$\langle x, x \rangle \ge 0$$

3. &nbsp; $$\langle x, x \rangle = 0 \quad \implies \quad x = 0$$

4. &nbsp; $$\langle x, \alpha y + \beta z \rangle = \alpha \langle x, y \rangle + \beta \langle x, z \rangle$$

5. &nbsp; $$\langle \alpha x + \beta y, z \rangle = \alpha \langle x, z \rangle + \beta \langle y, z \rangle$$

We can calculate the angle between two vectors

$$
\cos \theta = \dfrac{\langle x, y \rangle}{\sqrt{\langle x, x \rangle \langle y, y \rangle}}
$$

Is it always well defined? Inner product has Cauchy-Schwarz

$$
\vert \langle x, y \rangle \vert \le \sqrt{\langle x, x\rangle \langle y, y \rangle}
$$

Let's quickly prove Cauchy-Schwarz. We can define a function

$$
g(\lambda) = \langle \lambda x + y, \lambda x + y \rangle = \lambda^2 \langle x,x \rangle + 2 \lambda \langle x, y \rangle + \langle y, y \rangle \ge 0
$$

it is a quadratic equation with 1 or zero real root. Thus its discriminate $$b^2 - 4 ac < 0$$

$$
(2\langle x, y \rangle )^2 - 4 \langle x, x \rangle \langle y, y \rangle \le 0
$$

it gives

$$
\vert \langle x, y \rangle \vert \le \sqrt{\langle x, x\rangle \langle y, y \rangle}
$$

We can verify $$E(XY)$$ is an inner product. There may have some concern with rule 3.

We can somehow view random variable as vector, and the angle is calculated as

$$
\cos \theta = \dfrac{E(XY)}{\sqrt{E(X^2)E(Y^2)}}
$$

If $$\theta = 0$$, means the two random variable are complete linear correlated. If $$\theta = \pi/2$$, the two random variable are not linear correlated. If $$\theta = \pi$$, they are complete inverse linear correlated.


The formal definition of correlation coefficient shows the linear relationship between two random variables.

$$
\rho_{X,Y} = \dfrac{E((X-\mu_X)(Y-\mu_Y))}{\sigma_{X} \sigma_{Y}}
$$

in this course most random variabel is zero mean, then

$$
\rho_{X,Y} = \dfrac{E(XY)}{\sqrt{E(X^2)E(Y^2)}} = \cos \theta
$$

we can do example 01 again using the view of vector

$$
\begin{align}
\alpha_{opt} &= \dfrac{\vert \vert Y \vert \vert \cdot \cos \theta}{\vert \vert X \vert \vert}\\
&= \dfrac{\sqrt{E(Y^2)} \cdot \dfrac{E(XY)}{\sqrt{E(X^2)E(Y^2)}}}{\sqrt{E(X^2)}}\\
&= \dfrac{E(XY)}{E(X^2)}
\end{align}
$$

## Stochastic Process

Stochastic process is many (possibly infinite) random variables with index.
For example, we denote $$X(t)$$ as a stochastic process, meaning $$\forall t_0 \in R$$, $$X(t_0)$$ is a random variable.

Auto-correlation function: $$ R_X(t,s) = E(X(t)X(s)) $$.

Auto-covariance function: $$K_X(t,s) = E((X(t)-\mu_t) (X(s) - \mu_s))$$

Stationary: some statistic property doesn't change with time.
There are many different kind of stationary. One popular one is wide-sense stationary

1. &nbsp; $$E(X(t)) = m$$

2. &nbsp; $$R_X(t,s) = R_X (t+d, s+d)$$

- Example 02

The stochasitc process $$X(t) = A(t) \cos( \omega_0 t + \theta)$$, and $$A, \theta$$ are independent. And $$\theta \sim U(0, 2\pi)$$.

$$
\begin{align}
E(X(t)) &= E(A(t)) E(\cos(\omega_0 t + \theta)) = E(A(t)) \cdot 0 = 0
\end{align}
$$

$$
\begin{align}
R_X(t,s) &= E(X(t)X(s)) \\
&= E(A(t)\cos(\omega_0 t + \theta) A(s) \cos(\omega_0 t + \theta))\\
&= E(A(t)A(s)) \cdot E(\cos(\omega_0 t + \theta)\cos(\omega_0 s + \theta))\\
&= \dfrac{1}{2} \cdot E(A(t)A(s)) \cdot (E(\cos(\omega_0 (t+s) + 2 \theta)) + E(\cos(\omega_0 (t-s))))\\
&= \dfrac{1}{2} \cdot E(A(t)A(s)) \cdot \cos(\omega_0 (t-s))
\end{align}
$$

So it is W.S.S. if $$A(t)$$ is W.S.S.
