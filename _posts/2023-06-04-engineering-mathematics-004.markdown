---
title:  "Engineering Mathematics 004"
date:   2023-06-04 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Dr. Chun-Yao Wang' Lecture 004](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1832)

$$
y' = f(ax + by + c)
$$

$$
t = ax + by + c
$$

$$
dt = adx + bdy
$$

Exercise 13:

$$
y' = \tan^2(x+y)
$$

$$
u=x+y
$$

$$
du - dx = \tan^2(u) dx
$$

$$
\dfrac{du}{1+\tan^2 u} - dx = 0
$$

$$
\cos^2(u)du - dx = 0
$$

$$
(1+\cos(2u))du - 2dx = 0
$$

$$
u + \dfrac{1}{2}\sin u - 2x = C
$$

## Exact Differential Equations

$$
xy = 10
$$

$$
ydx + xdy = 0
$$

How to determine if some ODE is exact differential equation?

$$
M(x,y)dx + N(x,y)dy = 0
$$

$$
M(x,y) = \dfrac{\partial \phi}{\partial x}
$$

$$
N(x,y) = \dfrac{\partial \phi}{\partial y}
$$

if $$\phi$$ has continuous second order partial derivatives, then

$$
\dfrac{\partial^2 \phi}{\partial y \partial x} = \dfrac{\partial^2 \phi}{\partial x \partial y}
$$

$$
\dfrac{\partial M}{\partial y} = \dfrac{\partial N}{\partial x} \iff \text{ it is an exact differential equation}
$$

$$
\phi(x,y) = \int^x M d x + f(y) = \int^y N d y + g(x)
$$

Exercise 14:

$$
(3x^2 y^2 + e^y) \dfrac{dy}{dx} + 2(xy^3 + 1) = 0
$$

$$
2(xy^3 + 1) dx + (3x^2 y^2 + e^y) dy  = 0
$$

$$
\dfrac{\partial}{\partial y} 2(xy^3 + 1) = 6xy^2
$$

$$
\dfrac{\partial}{\partial x} (3x^2 y^2  +e^y) = 6xy^2
$$

$$
\phi(x,y) = \int^x 2(xy^3+1) dx + f(y) = x^2y^3 + 2x + f(y)
$$

$$
\phi(x,y) = \int^y (3x^2 y^2 + e^y)dy + g(x) = x^2y^3 + e^y + g(x)
$$

$$
\phi(x,y) = x^2y^3 + 2x + e^y = C
$$

Exercise 15:

$$
(x^2-4xy-y^2)dx + (y^2-2xy-2x^2)dy = 0
$$

$$
\dfrac{\partial}{\partial y} (x^2 - 4xy - y^2) = -4x - 2y
$$

$$
\dfrac{\partial}{\partial x} (y^2-2xy-2x^2) = -2y - 4x
$$


$$
\phi(x,y) = \int^x (x^2-4xy-y^2)dx = \dfrac{x^3}{3} - 2x^2y - xy^2 + f(y)
$$

$$
\phi(x,y) = \int^y (y^2-2xy-2x^2)dy = \dfrac{y^3}{3} - xy^2 - 2x^2 y + g(x)
$$

$$
\phi(x,y) = \dfrac{x^3}{3} - 2x^2y - xy^2 + \dfrac{y^3}{3} = C
$$

## Integrating Factors

$$
M(x,y)dx + N(x,y)dy = 0
$$

$$
I(x,y)M(x,y)dx + I(x,y)N(x,y)dy = 0
$$

$$
IMdx + INdy = 0
$$

$$
\dfrac{\partial}{\partial y} (IM) = \dfrac{\partial I}{\partial y} M + \dfrac{\partial M}{\partial y} I
$$

$$
\dfrac{\partial}{\partial x} (IN) = \dfrac{\partial I}{\partial x} N + \dfrac{\partial N}{\partial x} I
$$

$$
I \dfrac{\partial M}{\partial y} + M \dfrac{\partial I}{\partial y} = I \dfrac{\partial N}{\partial x} + N \dfrac{\partial I}{\partial x}
$$

$$
(\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}) I = N \dfrac{\partial I}{\partial x} - M \dfrac{\partial I}{\partial y}
$$

If $$I$$ is only function of $$x$$, then

$$
\dfrac{dI}{I} = \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N} dx
$$

the right side must be only function of $$x$$.

$$
I(x) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N} dx )
$$

If $$I$$ is only function of $$y$$, then

$$
\dfrac{dI}{I} = \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{-M} dy
$$

the right side must be only function of $$y$$.

$$
I(y) = \exp(\int \dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{-M} dy )
$$

Exercise 16:

$$
(4x+3y^2)dx + 2xydy=0
$$

$$
M = 4x + 3y^2, \quad N = 2xy
$$

$$
\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x} = 6y - 2y = 4y
$$

$$
\dfrac{\dfrac{\partial M}{\partial y} - \dfrac{\partial N}{\partial x}}{N} = \dfrac{4y}{2xy} = \dfrac{2}{x}
$$

$$
I(x) = \exp(\int \dfrac{2}{x}dx) = x^2
$$

$$
(4x^3+3x^2y^2)dx + 2x^3ydy=0
$$

$$
\phi(x,y) = \int^x (4x^3 + 3x^2y^2)dx = x^4 + x^3y^2 + f(y)
$$

$$
\phi(x,y) = \int^y 2x^3ydy = x^3y^2 + f(x)
$$

$$
\phi(x,y) = x^4 + x^3y^2 = C
$$
