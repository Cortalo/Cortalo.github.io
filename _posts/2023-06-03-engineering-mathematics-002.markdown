---
title:  "Engineering Mathematics 002"
date:   2023-06-03 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Junyao Wang' Lecture 002](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1776)

Exercise 6:

Exercise 7:

## Seperable After Chaning The Variables

- First-order first-degree homogeneous ODE

## First-Order First-Degree Homogeneous ODE

$$
y' = f(y/x)
$$

if

$$
f(\lambda x, \lambda y) = f(x,y)
$$

$$
M(\lambda x, \lambda y) = \lambda^m M(x,y), \quad N(\lambda x, \lambda y) = \lambda^m N(x,y)
$$

Exercise 8:

$$
(x-\sqrt{xy})y' = y
$$

$$
y' = \dfrac{\dfrac{y}{x}}{1 - \sqrt{\dfrac{y}{x}}}
$$

Let $$v = y/x, \implies y = vx \implies y' = v' x + v$$

$$
v' x + v = \dfrac{v}{1-\sqrt{v}}
$$

$$
\dfrac{1-\sqrt{v}}{v \sqrt{v}} dv = \dfrac{dx}{x}
$$

$$
-2 v^{-1/2} - \ln \vert v \vert = \ln \vert x \vert + C
$$

since $$v \ge 0$$

$$
\vert y \vert = k e^{-2\sqrt{\frac{x}{y}}}
$$

$$
\vert y \vert e^{2\sqrt{\frac{x}{y}}} = k
$$

Exercise 9:

$$
(3xy + y^2) + (x^2 + xy) \dfrac{dy}{dx} = 0
$$

$$
(3 \dfrac{y}{x} + (\dfrac{y}{x})^2) dx + (1 + \dfrac{y}{x})dy = 0
$$

Let $$v=y/x \implies dy = xdv + vdx$$

$$
(3 v + v^2)dx + (1+v)(xdv + vdx) = 0
$$

$$
\dfrac{dx}{x} + \dfrac{1+v}{2v(v+2)}dv = 0
$$

there is a trick to find $$\dfrac{A}{v} + \dfrac{B}{v+2}$$ quickly

$$
\dfrac{dx}{x} + \dfrac{dv}{4v} + \dfrac{dv}{4(v+2)} = 0
$$

$$
\ln\vert x \vert + \dfrac{1}{4} \ln \vert v \vert + \dfrac{1}{4} \ln \vert v + 2 \vert = C
$$

$$
\ln \vert x^4 v (v+2) \vert = C
$$

$$
\vert x^2 y (y+2x) \vert = k
$$
