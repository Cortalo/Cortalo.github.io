---
title:  "Engineering Mathematics 006"
date:   2023-06-11 08:00:00 +0200
categories: math
tags: math
math: true
---

From [Dr. Chun-Yao Wang' Lecture 006](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1855)

Linearlized ODEs

- Bernoulli Equation
- &nbsp; $$\dfrac{dv}{dy} y' + P(x)v(y) = Q(x)$$
- Riccati Equation

## Bernoulli Equation

$$
y'+P(x)y = Q(x) \cdot y^n
$$

when $$n\ne 0, 1$$, it is not linear ODE.

$$
y^{-n}y' + P(x)y^{1-n} = Q(x)
$$

Let $$u = y^{1-n}$$

$$
\dfrac{du}{dx} = (1-n)y^{-n} \cdot \dfrac{dy}{dx}
$$

$$
\dfrac{1}{1-n} \cdot \dfrac{du}{dx} + P(x) \cdot u = Q(x)
$$

$$
\dfrac{du}{dx} + (1-n)P(x) \cdot u = (1-n)Q(x)
$$

## Another Equation

$$
\dfrac{dv}{dy}y' + P(x)v(y) = Q(x)
$$

$$
\dfrac{dv}{dy}y' = \dfrac{dv}{dy} \dfrac{dy}{dx} = \dfrac{dv}{dx}
$$

then it becomes linear.

## Riccati Equation

$$
y' = P(x)y^2 + Q(x)y + R(x)
$$

If we have found a solution (by any possibel ways), $$s(x)$$, such that

$$
s' = P(x)s^2 + Q(x)s + R(x)
$$

Then the general soluton is

$$
y = s + \dfrac{1}{z}
$$

and the functin $$z$$ can be found as

$$
0 = z' + (2P(x)s(x) + Q(x)) \cdot z + P(x)
$$

which is an linear ODE for $$z$$.
