---
title:  "Engineering Mathematics 001"
date:   2023-06-02 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Junyao Wang' Lecture 001](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1775)

## Integration Formulas

$$
\begin{align}
& \int x^n dx = \dfrac{x^{n+1}}{n+1} + C\\
& \int \dfrac{1}{x} dx = \ln \vert x \vert + C\\
& \int \frac{1}{x+a} dx = \ln \vert x+a \vert + C\\
& \int \dfrac{dx}{\sqrt{x^2+a^2}} = \ln \vert x + \sqrt{x^2 + a^2} \vert + C\\
& \int \cos x dx = \sin x + C
\end{align}
$$

## Ordinary Differential Equation

Ordinary differential equation (ODE)

$$
y' + 5y = 3x
$$

## Partial Differential Equation

$$
\dfrac{\partial^2 u}{\partial x^2} + \dfrac{\partial^2 u}{\partial y^2} = 0
$$

## Order

$$
ay'' + by' + cy = f(x) \quad \text{ (second-order)}
$$

## Degree

$$
(y')^2 + y = e^x \quad \text{ (degree of 2) }
$$

## Linear Differential Equation

$$
a_n(x) y^{(n)} + a_{n-1}(x)y^{(n-1)} + \dots + a_1(x)y' + a_0(x)y = f(x)
$$

## Solutions

- General solution
- Particular solution
- Singular solution

## First-Order First-Degree Differential Equation

$$
y' = f(x,y)
$$

$$
M(x,y)dx + N(x,y)dy = 0 \implies y' = -\dfrac{M(x,y)}{N(x,y)}
$$

- Direct Integral.
- Seperable Equation.
  - Direct seperable.
  - After chaning the variable
- Exact differential equations

## Direct Integral

$$
y'=x
$$

$$
y = \dfrac{1}{2}x^2 + C
$$

## Seperable Equation

$$
y' = f(x,y) = f_1(x)f_2(y) \implies \dfrac{dy}{f_2(y)} = f_1(x)dx \implies \int \dfrac{dy}{f_2(y)} = \int f_1(x)dx + C
$$

$$
M_1(x)M_2(y)dx + N_1(x)N_2(y)dy = 0 \implies \int \dfrac{M_1(x)}{N_1(x)}dx + \int \dfrac{N_2(y)}{M_2(y)} dy = C
$$

Exercise 3:

$$
y' = y^2 e^{-x}
$$

$$
\dfrac{dy}{y^2} = e^{-x}dx
$$

$$
-\dfrac{1}{y} = -e^{-x} + C
$$

Exercise 4:

$$
(1+x^2)y' + 2xy\ln y = 0
$$

$$
\dfrac{dy}{y\ln y} + \dfrac{2x dx}{1+x^2} = 0
$$

$$
u = \ln y, v = 1+x^2
$$

$$
\dfrac{du}{u} + \dfrac{dv}{v} = 0
$$

$$
\ln \vert u \vert + \ln \vert v \vert = C
$$

$$
\ln \vert \ln y \vert + \ln(1+x^2) = C
$$

Exercise 5:
