---
title:  "Engineering Mathematics Explanation"
date:   2023-07-23 10:00:00 +0200
categories: math
tags: math
math: true
---


## First-Order First-Degree ODE

### Integration Formulas

$$
\begin{align}
& \int x^n dx = \dfrac{x^{n+1}}{n+1} + C\\
& \int \dfrac{1}{x} dx = \ln \vert x \vert + C\\
& \int \frac{1}{x+a} dx = \ln \vert x+a \vert + C\\
?& \int \dfrac{dx}{\sqrt{x^2+a^2}} = \ln \vert x + \sqrt{x^2 + a^2} \vert + C\\
& \int \cos x dx = \sin x + C\\
& \int \exp(x)\sin x = \dfrac{1}{2}\exp(x)(\sin x - \cos x) + C
\end{align}
$$


### Integration by Parts

$$
\int u dv = uv - \int vdu
$$

Exercise:

$$
\int \exp(x) \sin x dx
$$

$$
u = \exp(x), \quad v = -\cos x
$$

$$
du = \exp(x) dx, \quad dv = \sin x dx
$$

$$
\int \exp(x) \sin x dx = - \exp(x) \cos x - \int -\cos x \exp(x) dx
$$


### Ordinary, Partial, Order and Degree

Ordinary differential equation (ODE)

$$
y' + 5y = 3x
$$


$$
\dfrac{\partial^2 u}{\partial x^2} + \dfrac{\partial^2 u}{\partial y^2} = 0
$$

$$
ay'' + by' + cy = f(x) \quad \text{ (second-order)}
$$

$$
(y')^2 + y = e^x \quad \text{ (degree of 2) }
$$

The degree of an ODE is the degree of the highest order derivative.

$$
a_n(x) y^{(n)} + a_{n-1}(x)y^{(n-1)} + \dots + a_1(x)y' + a_0(x)y = f(x)
$$

Linear ODE has all the derivaties (including zero's derivative) are degree of 1.


- General solution: solutions without specifying initial condition.
- Particular solution: a solution with specifying initial condtion.
- Singular solution: some other solutions cannot get from standard procedures, but they are indeed solutions of differential equation. Usually we are not focusing on such solutions.


## Fourier Series

### Fourier Series

**Example (odd function square wave)**

$$
f(t) =
\begin{cases}
-1, \quad -T/2 < t < 0\\
1, \quad 0 < t < T/2
\end{cases}
$$



$$
\begin{align}
f(t) = \dfrac{4}{\pi} \sum_{n=1,3,5,\dots}^{\infty} \dfrac{1}{n} \sin\left(n\omega t\right)
\end{align}
$$

## Multi-Variable Functions

### Taylor's Formula

For multi-variable function $$f(x,y)$$. To expand it around $$(a,b)$$, let

$$
\begin{cases}
x = a + (x_0-a)t\\
y = b + (y_0-b)t
\end{cases}
$$

then $$f(x(t),y(t))=F(t)$$

$$
F(t) = F(0) + \dfrac{F'(0)}{1!} t + \dfrac{F''(0)}{2!}t^2 + \dots
$$

$$
F'(t) = (x_0-a)f_x + (y_0-b)f_y
$$

$$
F''(t) = (x_0-a)^2f_{xx} + 2(x_0-a)(y_0-b)f_{xy} + (y_0-b)^2 f_{yy}
$$

### Implicit Function

From $$f(x,y)=0$$, we try to find the Taylor series of $$y(x)$$.
Then in a sense that, if we can uniquely determine all the derivatives $$y^{(n)}(x_0)$$, then we can make sure $$y(x)$$ is unique in a neighborhood of $$x_0$$.

$$
y(x) = y(x_0) + \dfrac{y'(x_0)}{1!}(x-x_0) + \dots
$$

Let $$R(x) = f(x,y(x)) = 0$$

$$
\begin{align}
R'(x_0) &= \dfrac{\partial f}{\partial x} \dfrac{dx}{dx} + \dfrac{\partial f}{\partial y} \dfrac{dy}{dx}\\
&= \dfrac{\partial f}{\partial x} + \dfrac{\partial f}{\partial y} \dfrac{dy}{dx}\\
&= 0
\end{align}
$$

$$
y'(x_0) = -\dfrac{\dfrac{\partial f}{\partial x}(x_0,y_0)}{\dfrac{\partial f}{\partial y}(x_0, y_0)}
$$

We can also calculate $$y''(x_0)$$, from

$$
y' = -\dfrac{f_x}{f_y}
$$

$$
\begin{align}
y'' &= -\dfrac{(\dfrac{d}{dx} f_x)f_y - f_x (\dfrac{d}{dx}f_y)}{f_y^2}\\
&= -\dfrac{(f_{xx}+f_{xy}y')f_y - f_x(f_{xy} + f_{yy}y')}{f_y^2}
\end{align}
$$
