---
title:  "Engineering Mathematics 005"
date:   2023-06-11 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Junyao Wang' Lecture 005](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1851)

## Integrating Factors

$$
I(x), I(y), I(x+y), I(xy)
$$

Exercise 17:

$$
(y^4+2y)dx + (xy^3+2y^4-4x)dy = 0
$$

$$
M = y^4+2y, \quad N = xy^3 + 2y^4 - 4x
$$

$$
\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x} = 4y^3 + 2 - (y^3 -4) =3y^3 + 6
$$

$$
\dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{-M} = \dfrac{3y^3+6}{-(y^4 + 2y)} = -\dfrac{3}{y}
$$

$$
I(y) = \exp(\int - \dfrac{3}{y}dy) = y^{-3}
$$

$$
(y+2y^{-2})dx + (x+2y-4x y^{-3})dy = 0
$$

$$
\phi(x,y) = \int^x (y + 2y^{-2}) dx = xy + 2xy^{-2} + f(y)
$$

$$
\phi(x,y) = \int^y (x+2y - 4xy^{-3})dy = xy + y^2 +2xy^{-2} + g(x)
$$

$$
\phi(x,y) = xy + y^2 + 2xy^{-2} = C
$$

## $$I(x+y)$$

$$
\dfrac{\partial}{\partial x} (x^2+y)^2 = 2(x^2+y) \cdot 2x
$$

$$
\dfrac{\partial}{\partial x} f(u(x,y)) = \dfrac{df}{du} \cdot \dfrac{\partial u}{\partial x}
$$

$$
(\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}) I = N \dfrac{\partial I}{\partial x} - M \dfrac{\partial I}{\partial y}
$$


$$
I(x) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N} dx )
$$

$$
I(y) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{-M} dy )
$$

$$
I(x+y) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N-M} d(x+y))
$$


$$
I(xy) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{Ny-Mx} d(xy))
$$


$$
I(x-y) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N+M} d(x+y))
$$

Exercise:

$$
3xydx + 2x^2 dy = 0
$$

$$
\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x} = 3x - 4x = -x
$$

$$
I(x) = \exp(\int \dfrac{-x}{2x^3} dx) = x^{-1/2}
$$

$$
3x^{1/2}ydx + 2x^{3/2}dy = 0
$$

$$
\phi(x,y) = 2 x^{3/2} y + f(y)
$$

$$
\phi(x,y) = 2x^{3/2} y + g(x)
$$

$$
\phi(x,y) = 2x^{3/2}y = C
$$

$$
I(xy) = xy
$$

$$
3x^2y^2 dx + 2x^3y dy = 0
$$

$$
\phi(x,y) = x^3y^2 = C
$$

Exercise F.1:

$$
(3xy+y^2)dx + (x^2+xy)dy = 0
$$

$$
M = 3xy+y^2, \quad N = x^2+xy
$$

$$
\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x} = 3x + 2y - (2x + y) = x +y
$$

$$
I(x) = \exp(\int \dfrac{dx}{x}) = x
$$

$$
(3x^2 y + xy^2)dx + (x^3 + x^2y)dy = 0
$$

$$
\phi(x,y) = x^3y + \dfrac{1}{2}x^2y^2 + f(y)
$$

$$
\phi(x,y) = x^3y + \dfrac{1}{2}x^2y^2 + g(x)
$$

$$
\phi(x,y) = x^3y + \dfrac{1}{2}x^2 y^2 = C
$$

Exercise F.2:

$$
2xydx + (4y+3x^2)dy = 0; y(1) = 1
$$

$$
\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x} = 2x - 6x = -4x
$$

$$
I(y) = \exp(\int \dfrac{-4x}{-2xy} dy) = y^2
$$

$$
2xy^3 dx + (4y^3 + 3x^2 y^2)dy = 0
$$

$$
\phi(x,y) = x^2y^3 + f(y)
$$

$$
\phi(x,y) = y^4 + x^2y^3 + g(x)
$$

$$
\phi(x,y) = y^4 + x^2 y^3 = C = 2
$$

## First Order Linear ODE

$$
y' + P(x)y = Q(x)
$$

$$
(P(x)y - Q(x))dx + dy = 0
$$

$$
\dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N} = P(x)
$$

$$
I(x) = \exp(\int P(x) dx)
$$

$$
I(x) \dfrac{dy}{dx} + P(x) I(x) y = Q(x) I(x)
$$

$$
\dfrac{d}{dx}[y \exp(\int P(x) dx)] = Q(x)I(x)
$$

$$
y = \dfrac{1}{I(x)} \int Q(x) I(x) dx + \dfrac{C}{I(x)}
$$

Exercise 18:

$$
y' + y = \sin(x)
$$

$$
P(x) = 1, \quad Q(x) = \sin(x)
$$

$$
I(x) = \exp(x)
$$

$$
\int Q(x) I(x) dx = \int \sin(x)\exp(x)dx
$$

$$
\sin(x) = \dfrac{\exp(ix) - \exp(-ix)}{2i}
$$

$$
\begin{align}
&\int Q(x) I(x) dx = \int \sin(x)\exp(x)dx\\
=& \dfrac{\exp(x)}{2}(\sin x - \cos x)
\end{align}
$$

$$
y = \dfrac{1}{2}(\sin x - \cos x) + C \exp(-x)
$$

Exercise 19:

$$
y' = \dfrac{y}{2x+y^3 \exp(y)}
$$

$$
\dfrac{dx}{dy} = \dfrac{2x+y^3 \exp(y)}{y}
$$

$$
x' - \dfrac{2}{y}x = y^2 \exp(y)
$$

$$
I(y) = \exp(\int -\dfrac{2}{y} dy) = y^{-2}
$$

$$
\int y^2\exp(y) y^{-2} dy = \exp(y)
$$

$$
x = y^2 \exp(y) + C y^2
$$
