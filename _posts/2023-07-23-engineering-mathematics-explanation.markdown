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


### Seperable After Changing Variable

- First-Order First-Degree Homogeneous ODE, $$y'=f(y/x)$$


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


Exercise 10:

$$
\dfrac{dy}{dx} = \dfrac{vy-s\sqrt{x^2+y^2}}{vx}
$$

$$
y(w) = 0
$$

$$
udx + xdu = udx - (s/v) \sqrt{1+u^2} dx = udx - r\sqrt{1+u^2} dx
$$

$$
\dfrac{du}{\sqrt{1+u^2}} + r \dfrac{dx}{x} = 0
$$

$$
\ln \vert u + \sqrt{1+u^2} \vert + r \ln \vert x \vert = C
$$

$$
(u + \sqrt{1+u^2})x^r = k
$$

$$
(\dfrac{y}{x} + \sqrt{1+(\dfrac{y}{x})^2})x^r = k
$$

$$
k = w^{s/v}
$$

- &nbsp; $$(a_1 x + b_1 y + c_1)dx + (a_2 x  +b_2 y + c2)dy = 0$$

First case: if $$\dfrac{a_1}{a_2} \ne \dfrac{b_1}{b_2}$$


$$
\begin{cases}
a_1 x + b_1 y + c_1 = 0\\
a_2 x + b_2 y + c_2 = 0
\end{cases}
$$

the two lines cross at the point $$(x,y)=(\alpha,\beta)$$.
Let

$$
\begin{cases}
x = u+\alpha\\
y = v + \beta
\end{cases}
$$


$$
[a_1(u+\alpha) + b_1(v + \beta) + c_1] du + [\alpha_2 (u+\alpha) + b_2(v+\beta) + c_2] dv = 0
$$


$$
(a_1 u + b_1 v) du + (a_2 u + b_2 v) dv = 0
$$

Exercise 11:

$$
(-3x + y + 6)dx + (x+y+2)dy = 0
$$

$$
(x,y) = (1, -3)
$$

$$
\begin{cases}
x = u+1\\
y = v-3
\end{cases}
$$

$$
(-3u+v)du + (u+v)dv = 0
$$

Let $$s = u/v, du = sdv + vds$$

$$
(\dfrac{-3s+1}{s+1})(sdv + vds) + dv = 0
$$

$$
\dfrac{dv}{v} + \dfrac{3s-1}{(3s+1)(s-1)}ds
$$

$$
\dfrac{dv}{v} + \dfrac{1}{2}\dfrac{1}{s+\dfrac{1}{3}} ds + \dfrac{1}{2}\dfrac{1}{s-1} ds = 0
$$

$$
\ln \vert v \vert + \dfrac{1}{2} \ln \vert s + \dfrac{1}{3} \vert + \dfrac{1}{2} \ln \vert s - 1 \vert = C
$$

$$
v^2 \vert (s+\frac{1}{3})(s-1) \vert = C
$$

$$
\vert (3u + v)(u - v) \vert = C
$$

$$
\vert (3x+y)(x-y-4) \vert = C
$$

Second case:


$$ (a_1 x + b_1 y + c_1) dx + (a_2 x  +b_2 y + c_2) dy = 0 $$

$$
\dfrac{a_1}{a_2} = \dfrac{b_1}{b_2} = m \ne \dfrac{c_1}{c_2}
$$

Let $$a_2 x + b_2 y = z$$

$$
dy = \dfrac{dz - a_2 dx}{b_2}
$$

$$
(mz + c_1) dx + (z + c_2) \dfrac{dz - a_2 dx}{b_2}
$$

$$
dx + \dfrac{(z+c_2)dz}{(b_2 m - a_2)z + (b_2 c_1 - a_2 c_2)} = 0
$$

Exercise 12:

$$
(x+y)dx + (3x + 3y - 4)dy = 0
$$

Let $$z = x+y$$

$$
zdx + (3z-4)(dz - dx) = 0
$$

$$
dx - \dfrac{3}{2}dz - \dfrac{dz}{z-2} = 0
$$

$$
x - \dfrac{3}{2}z - \ln \vert z-2 \vert = C
$$

- &nbsp; $$y'=f(ax+by+c)$$

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

### Exact Differential Equations


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

### Integrating Factors


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

- &nbsp; $$I(x+y)$$:

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


### First Order Linear ODE


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

### Linearized ODE

- Bernoulli Equation: $$y' + P(x)y = Q(x) \cdot y^n$$. Let $$u=y^{1-n}$$


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

- &nbsp; $$\dfrac{dv}{dy}y' + P(x)v(y)=Q(x)$$


$$
\dfrac{dv}{dy}y' + P(x)v(y) = Q(x)
$$

$$
\dfrac{dv}{dy}y' = \dfrac{dv}{dy} \dfrac{dy}{dx} = \dfrac{dv}{dx}
$$

then it becomes linear.

- Riccati Equation: $$y'=P(x)y^2 + Q(x)y + R(x)$$


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
