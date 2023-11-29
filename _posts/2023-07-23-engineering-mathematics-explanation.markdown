---
title:  "Engineering Mathematics Explanation"
date:   2023-07-23 10:00:00 +0200
categories: math
tags: math
math: true
---


## First-Order First-Degree ODE

### Useful Formulas

#### Integrations

$$
\begin{align}
& \int x^n dx = \dfrac{x^{n+1}}{n+1} + C\\
& \int \dfrac{1}{x} dx = \ln \vert x \vert + C\\
& \int \frac{1}{x+a} dx = \ln \vert x+a \vert + C\\
?& \int \dfrac{dx}{\sqrt{x^2+a^2}} = \ln \vert x + \sqrt{x^2 + a^2} \vert + C\\
& \int \cos x dx = \sin x + C\\
& \int \exp(x)\sin x = \dfrac{1}{2}\exp(x)(\sin x - \cos x) + C\\
& \int \dfrac{1}{1+x^2}dx = \tan^{-1}x + C\\
& \int_{-\infty}^{\infty} e^{-a x^2} dx = \sqrt{\dfrac{\pi}{a}}, \quad a > 0\\
& \int_0^\infty \dfrac{\sin x}{x} dx = \dfrac{\pi}{2}\\
& \int_{-\infty}^\infty \dfrac{\sin x}{x} dx = \pi\\
& \int_{-\infty}^{\infty} \exp(j\omega t) d\omega = 2\pi \delta(t)
\end{align}
$$

#### Others

$$
\begin{align}
& \lim_{A\to\infty} \dfrac{\sin(Ax)}{\pi x} = \delta(x)\\
& \delta(ax + b) = \dfrac{1}{\vert a \vert} \delta\left(x + \dfrac{b}{a}\right)
\end{align}
$$


### Integration by Parts

$$
\int u dv = uv - \int vdu
$$

Exercise:

$$
\int \exp(x)  x dx
$$

$$
u = x, \quad v = \exp(x)
$$

$$
du = dx, \quad dv = \exp(x)dx
$$

$$
\int \exp(x) x dx = x \exp(x) - \int \exp(x) dx = x \exp(x) - \exp(x) + C
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

## 3D Vectors

### Polar Coordinates


$$
\begin{cases}
r = \sqrt{x^2+y^2}\\
\theta = \mathrm{atan2}(y,x) \in (-\pi, \pi]
\end{cases}
$$

$$
\mathrm{atan2}(y, x)= \begin{cases}\arctan \left(\frac{y}{x}\right) & \text { if } x>0 \\ \arctan \left(\frac{y}{x}\right)+\pi & \text { if } x<0 \text { and } y \geq 0 \\ \arctan \left(\frac{y}{x}\right)-\pi & \text { if } x<0 \text { and } y<0 \\ \frac{\pi}{2} & \text { if } x=0 \text { and } y>0 \\ -\frac{\pi}{2} & \text { if } x=0 \text { and } y<0 \\ \text { undefined } & \text { if } x=0 \text { and } y=0 .\end{cases}
$$


## Field Theory


### Combination and Laplacian



$$
\nabla \cdot (u \vec{v}) = \nabla u \cdot \vec{v} + u \nabla \cdot \vec{v}
$$

*Proof:*

$$
\begin{align}
&(\dfrac{\partial}{\partial x}\hat{i} + \dfrac{\partial}{\partial y}\hat{j} + \dfrac{\partial}{\partial z}\hat{k}) \cdot (u v_x \hat{i} + uv_y \hat{j} + uv_z \hat{k})\\
=& \dfrac{\partial (u v_x)}{\partial x} + \dfrac{\partial (u v_y)}{\partial y} + \dfrac{\partial (u v_z)}{\partial z}\\
=& \dfrac{\partial u}{\partial x} v_x + \dfrac{\partial u}{\partial y} v_y + \dfrac{\partial u}{\partial z} v_z + u \dfrac{\partial v_x}{\partial x} + u \dfrac{\partial v_y}{\partial y} + u \dfrac{\partial v_z}{\partial z}
\end{align}
$$

### Non-Cartesian Coordinates

#### Cylindrical Coordinates

$$
\begin{align}
\nabla &= \hat{i} \dfrac{\partial}{\partial x} + \hat{j} \dfrac{\partial}{\partial y} + \hat{k} \dfrac{\partial}{\partial z}\\
&= (c \hat{e_r} - s\hat{e_\theta}) \left(\dfrac{\partial}{\partial r} \dfrac{\partial r}{\partial x} + \dfrac{\partial}{\partial\theta} \dfrac{\partial\theta}{\partial x} + \dfrac{\partial}{\partial z}\dfrac{\partial z}{\partial x}\right) + \dots
\end{align}
$$

Note that from chain rule, it should really be written as $$\dfrac{\partial r}{\partial x} \dfrac{\partial}{\partial r}$$.
The $$\dfrac{\partial r}{\partial x}$$ will not be derivated by $$\dfrac{\partial}{\partial r}$$.


## Fourier Method

### Sturm-Liouville Problem

#### Example 1

$$
\begin{cases}
y'' + \lambda y = 0\\
x \in [0,L]\\
y(0) = y(L) = 0
\end{cases}
$$

$$
y = e^{rx}
$$

$$
r = \pm \sqrt{\lambda} i
$$

$$
y(x) =
\begin{cases}
A\cos\sqrt{\lambda}x + B \sin\sqrt{\lambda}x, \quad \lambda \ne 0\\
C + Dx, \quad \lambda = 0
\end{cases}
$$

&nbsp; $$\lambda=0$$ is not an eigenvalue, since the corresponding solution $$y=0$$ is a trivial solution. The eigenvalue should corresponds to nontrivial solution.

$$
\begin{cases}
0 = A \cdot 1 + B \cdot 0\\
0 = A \cos\sqrt{\lambda}L + B\sin\sqrt{\lambda} L
\end{cases}
$$

The condition for nontrivial solution

$$
\begin{vmatrix}
1 & 0\\
\cos\sqrt{\lambda} L & \sin\sqrt{\lambda} L
\end{vmatrix}
=0
$$

$$
\begin{cases}
\lambda_n = \dfrac{n^2 \pi^2}{L^2}\\
\phi_n = \sin \dfrac{n\pi x}{L}\\
n = 1,2,3,\dots
\end{cases}
$$

#### Example 2

$$
\begin{cases}
y'' - 2y' + \lambda y =0\\
y(0)=0, \quad y(\pi)=0
\end{cases}
$$

multiplying $$\sigma(x)$$

$$
\sigma y'' - 2\sigma y' + \lambda \sigma y = 0
$$

with

$$
\sigma' = -2\sigma
$$

Let's take $$\sigma(x) = e^{-2x}$$, then

$$
\left(e^{-2x}y'\right)' + \lambda e^{-2x}y = 0
$$

is a Sturm-Liouville problem.

## Diffusion Equation

### Separation of Variables

#### Example 1

$$
\begin{cases}
L[u] = a^2 u_{xx} - u_t = 0, \quad (0 < x < L, 0 < t < \infty)\\
u(0,t) = u_1, \quad u(L,t) = u_2, \quad (0 < t < \infty)\\
u(x,0) = f(x), \quad (0 < x < L)
\end{cases}
$$

$$
u(x,t) = X(x)T(t)
$$

$$
\dfrac{X''}{X} = \dfrac{1}{a^2} \dfrac{T'}{T} = -k^2
$$

$$
X =
\begin{cases}
A\cos kx + B\sin kx, & \quad k \ne 0\\
D + Ex, & \quad k = 0
\end{cases}
$$

$$
T =
\begin{cases}
F e^{-k^2a^2 t}, & \quad k \ne 0\\
G, & \quad k = 0
\end{cases}
$$

$$
u = H + Ix + (J\cos kx + K \sin kx)e^{-k^2a^2 t}
$$

First apply boundary condition $$u(0,t) = u_1$$.

$$
H + Je^{-k^2 a^2 t} = u_1
$$

Since $$(1, e^{-a^2k^2 t})$$ are linear independent

$$
\begin{cases}
H = u_1\\
J = 0
\end{cases}
$$

$$
u = u_1 + Ix + (K\sin kx) e^{-k^2a^2 t}
$$

Now apply the boundary condition $$u(L,t)=u_2$$

$$
u_1 + I L + (K \sin k L) e^{-k^2 a^2 t} = u_2
$$

$$
\begin{cases}
u_1 + IL = u_2\\
K \sin kL = 0
\end{cases}
$$

To maintain the solution as robust as possible, set $$\sin kL = 0$$

$$
kL = n \pi, \quad (n = 1,2,3,\dots)
$$

$$
k_n = \dfrac{n \pi}{L}, \quad (n = 1,2,3,\dots)
$$

&nbsp; $$n$$ doesn't need to be $$0$$, since that is included when $$K = 0$$.
Also, $$n$$ doesn't need to be negative, since that is included by changing $$K$$.

By superposition

$$
u(x,t) = u_1 + \left(\dfrac{u_2-u_1}{L}\right)x + \sum_{n=1}^{\infty} K_n \sin\dfrac{n\pi x}{L} e^{-(n\pi a/L)^2 t}
$$

now apply initial condition $$u(x,0) = f(x)$$

$$
u_1 + \left(\dfrac{u_2-u_1}{L}\right)x + \sum_{n=1}^{\infty} K_n \sin\dfrac{n\pi x}{L} = f(x)
$$

$$
f(x) -\left[ u_1 + \left(\dfrac{u_2-u_1}{L}\right)x\right] = F(x) = \sum_{n=1}^{\infty} K_n \sin\dfrac{n\pi x}{L}
$$

This is half range sin expansion of $$F(x)$$.

$$
K_n = \dfrac{2}{L}\int_0^L F(x)\sin\dfrac{n\pi x}{L}\, dx
$$

note that if $$f(x)$$ is not continuous, we will not get the solution corresponding to $$f(x)$$.
The value will be different at the discontinuous point.
However, in engineering practice, we didn't care this much.

### Fourier Transform

$$
\begin{cases}
\alpha^2 u_{xx} = u_{t}\\
-\infty < x < \infty, 0 < t < \infty\\
u(\pm \infty, t) = u_{x}(\pm \infty, t) = 0\\
u(x,0) = f(x)
\end{cases}
$$

Let's do FT w.r.t. $$x$$.
Note that when $$u(\pm \infty, t) = u_{x}(\pm \infty, t) = 0$$, $$F\left\{u_{xx}\right\} = (i\omega)^2 \hat{u}(\omega, t)$$

$$
\alpha^2 (i\omega)^2 \hat{u}(\omega, t) = \dfrac{\partial}{\partial t} \hat{u}(\omega,t)
$$

$$
\dfrac{d \hat{u}}{d t} + \alpha^2 \omega^2 \hat{u} = 0
$$

$$
\hat{u} = A \cdot e^{-\alpha^2 \omega^2 t}
$$

$$
A = \hat{f}(\omega)
$$

$$
\hat{u}(\omega,t) = \hat{f}(\omega) e^{-\alpha^2 \omega^2 t} = \hat{f}(\omega) \hat{g}(\omega)
$$

$$
g(x) = \dfrac{1}{2\alpha \sqrt{\pi t}} e^{-x^2/(4\alpha^2 t)}
$$

$$
u(x,t) = \dfrac{1}{2\alpha \sqrt{\pi t}} \int_{-\infty}^{\infty} f(\xi)e^{-(x-\xi)^2/(4\alpha^2 t)} \, d\xi
$$

### Laplace Transform

$$
\begin{cases}
\alpha^2 u_{xx} = u_{t}\\
0 \le x < \infty, \quad 0 \le t < \infty\\
u(0,t) = g(t), \quad 0 \le t < \infty\\
u(\infty, t) = 0, \quad 0 \le t < \infty\\
u(x,0) = 0, \quad 0 \le x < \infty
\end{cases}
$$


Let's do LT w.r.t. $$t$$.
Since $$u(x,0) = 0$$.

$$
\alpha^2 \overline{u}_{xx} = s \overline{u}(x,s)
$$

$$
\overline{u}(x,s) = A e^{\sqrt{s}x/\alpha} + B e^{-\sqrt{s}x/\alpha}
$$

apply $$u(\infty,t) = 0$$.

$$
\overline{u}(\infty, s) = 0
$$

$$
\overline{u}(x,s) = B e^{-\sqrt{s}x/\alpha}
$$

apply $$u(0,t) = g(t)$$

$$
B = \overline{g}(s)
$$

$$
\overline{u}(x,s) = \overline{g}(s) e^{-\sqrt{s}x/\alpha}
$$

$$
\begin{align}
u(x,t) &= g(t) * \dfrac{xe^{-x^2/(4\alpha^2 t)}}{2\alpha \sqrt{\pi} t^{3/2}}\\
&= \dfrac{x}{2\alpha\sqrt{\pi}} \int_0^t g(t-\tau) \dfrac{e^{-x^2/(4\alpha^2 \tau)}}{\tau^{3/2}} \, d\tau
\end{align}
$$

## Wave Equation

$$
c^2 \nabla^2 u = u_{tt}
$$

### Separation of Variable

$$
\begin{cases}
c^2 y_{xx} = y_{tt}\\
0 \le x \le L, \quad 0 \le t < \infty\\
y(0,t) = 0\\
y(L,t) = 0\\
y(x,0) = f(x)\\
y_{t}(x,0) = g(x)
\end{cases}
$$

$$
y(x,t) = X(x)T(t)
$$

$$
c^2 X'' T = X T''
$$

$$
\dfrac{X''}{X} = \dfrac{1}{c^2}\dfrac{T''}{T} = -k^2
$$

$$
X =
\begin{cases}
A + Bx, \quad k = 0\\
D\cos kx + E \sin kx, \quad k \ne 0
\end{cases}
$$

$$
T =
\begin{cases}
H + It, \quad k = 0\\
J\cos kct + K \sin kct, \quad k \ne 0
\end{cases}
$$

$$
y(x,t) = (A+Bx)(H+It) + (D \cos kx + E\sin kx)(J \cos kct + K \sin kct)
$$

First apply boundary condition $$y(0,t) = 0$$

$$
A (H + It) + D (J \cos kct + K\sin kct) = 0
$$

We choose $$A = D = 0$$ so that the solution is as sobust as possible

$$
y(x,t) = x (P + Qt) + \sin kx (R \cos kct + S \sin kct)
$$

apply boundary condition $$y(L,t) = 0$$

$$
L(P+Qt) + \sin kL (R\cos kct + S\sin kct) = 0
$$

$$
\begin{cases}
P = Q = 0\\
\sin kL = 0
\end{cases}
$$

$$
k_n = \dfrac{n\pi}{L}, \quad n = 1,2,3
$$

$$
y(x,t) = \sum_{n=1}^{\infty} \sin \dfrac{n\pi x}{L} \left(R_n \cos\dfrac{n\pi ct}{L} + S_n \sin\dfrac{n\pi ct}{L}\right)
$$

now apply initial condition $$y(x,0) = f(x)$$ and $$y_t(x,0)=g(x)$$

$$
f(x) = \sum_{n=1}^{\infty} R_n \sin\dfrac{n\pi x}{L}
$$

$$
g(x) = \sum_{n=1}^{\infty} \dfrac{n\pi c}{L} S_n \sin \dfrac{n\pi x}{L}
$$

they are half range sin expansion

$$
R_n = \dfrac{2}{L}\int_0^L f(x)\sin\dfrac{n\pi x}{L}\, dx
$$

$$
S_n = \dfrac{2}{n\pi c}\int_{0}^{L} g(x)\sin \dfrac{n\pi x}{L}\, dx
$$

Let's look at

$$
\sin\dfrac{n\pi x}{L}\cos\dfrac{n\pi ct}{L} = \dfrac{1}{2}\left(\sin \dfrac{n\pi (x+ct)}{L} + \sin\dfrac{n\pi (x-ct)}{L}\right)
$$

That is two wave travel to right $$f(x-ct)$$ and left $$f(x+ct)$$, with speed $$c$$.

$$
\begin{cases}
\omega = 2\pi / T\\
k = 2\pi / \lambda\\
c = \dfrac{\omega}{k} = \dfrac{\lambda}{T}
\end{cases}
$$


#### Two Dimentional Case

$$
\begin{cases}
c^2 (w_{xx} + w_{yy}) = w_{tt}\\
0 \le x \le a\\
0 \le y \le b\\
0 \le t < \infty\\
w(0,y,t) = w(a,y,t) = w(x,0,t) = w(x,b,t) = 0\\
w(x,y,0) = f(x,y)\\
w_t(x,y,0) = 0
\end{cases}
$$

$$
w(x,y,t) = X(x)Y(y)T(t)
$$

$$
c^2(X''YT + XY''T) = XYT''
$$

$$
\dfrac{X''}{X}+\dfrac{Y''}{Y} = \dfrac{1}{c^2}\dfrac{T''}{T} = -k^2
$$

$$
\begin{cases}
T'' + k^2 c^2 T = 0\\
X'' + \alpha^2 X = 0\\
Y'' + (k^2 - \alpha^2)Y = 0
\end{cases}
$$

$$
w(w,y;t) = (Ax+B)(Cy+D)(Et+G) + (H \cos\alpha x + I \sin \alpha x)(J \cos \sqrt{k^2-\alpha^2}y + K \sin\sqrt{k^2-\alpha^2}y)(L \sin kct + M \cos kct)
$$

apply $$w(0,y,t) = 0$$

$$
B(Cy+D)(Et+G) + H(J \cos \sqrt{k^2-\alpha^2}y + K \sin\sqrt{k^2-\alpha^2}y)(L \sin kct + M \cos kct) = 0
$$

$$
B = H = 0
$$


$$
w(w,y;t) = x(Cy+D)(Et+G) + \sin \alpha x(J \cos \sqrt{k^2-\alpha^2}y + K \sin\sqrt{k^2-\alpha^2}y)(L \sin kct + M \cos kct)
$$

apply $$w(x,0,t)=0$$

$$
Dx(Et+G) + J \sin \alpha x(L \sin kct + M \cos kct) = 0
$$

$$
D = J = 0
$$

$$
w(w,y;t) = xy(Et+G) + \sin \alpha x \sin\sqrt{k^2-\alpha^2}y(L \sin kct + M \cos kct)
$$

apply $$w(a,y,t)=0$$

$$
ay(Et+G) + \sin \alpha a \sin\sqrt{k^2-\alpha^2}y(L \sin kct + M \cos kct) = 0
$$

$$
E = G = 0
$$

$$
\alpha = \dfrac{m\pi}{a}, \quad m = 1,2,3
$$

apply $$w(x,b,t) = 0$$

$$
\sqrt{k^2-\alpha^2} = \dfrac{n \pi}{b}, \quad n = 1,2,3
$$

$$
k = \pi\sqrt{\dfrac{m^2}{a^2} + \dfrac{n^2}{b^2}}
$$

$$
w(x,y,t) = \sum_{n=1}^{\infty}\sum_{m=1}^{\infty} \sin \dfrac{m\pi x}{a} \sin\dfrac{n\pi y}{b} \left(G_{mn}\sin \omega_{mn} t + H_{mn} \cos \omega_{mn} t \right)
$$

$$
\omega_{mn} = \pi c\sqrt{\dfrac{m^2}{a^2} + \dfrac{n^2}{b^2}}
$$

apply $$w_t(x,y,0) = 0$$

$$
G_{mn} = 0
$$

$$
w(x,y,t) = \sum_{n=1}^{\infty}\sum_{m=1}^{\infty} H_{mn} \sin \dfrac{m\pi x}{a} \sin\dfrac{n\pi y}{b}  \cos \omega_{mn} t
$$

apply $$w(x,y,0) = f(x,y)$$

$$
f(x,y) = \sum_{n=1}^{\infty}\sum_{m=1}^{\infty} H_{mn} \sin \dfrac{m\pi x}{a} \sin\dfrac{n\pi y}{b}
$$

This is a double Fourier series.

$$
H_{mn} = \dfrac{4}{ab} \int_0^b \int_0^a f(x,y) \sin\dfrac{n\pi x}{a} \sin \dfrac{n\pi y}{b} \, dx dy
$$
