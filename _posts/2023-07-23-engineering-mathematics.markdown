---
title:  "Engineering Mathematics"
date:   2023-07-23 09:00:00 +0200
categories: math
tags: math
math: true
---

From [Dr. Chun-Yao Wang' Lecture](https://ocw.nthu.edu.tw/ocw/index.php?page=course&cid=145)


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


### Ordinary, Partial, Order and Degree

Ordinary differential equation.

Partial differential equation.

Order of the differential equation.

Degree of the differential equation.

Linear differential equation.

General solution.

Particular solution.

Singular solution.

$$
y'=f(x,y)
$$

or

$$
M(x,y)dx + N(x,y)dy = 0
$$

### Direct Integral

### Seperable Equation

### Seperable After Changing Variable

- First-Order First-Degree Homogeneous ODE, $$y'=f(y/x)$$
- &nbsp; $$(a_1 x + b_1 y + c_1)dx + (a_2 x  +b_2 y + c2)dy = 0$$
- &nbsp; $$y'=f(ax+by+c)$$

### Exact Differential Equations

$$
\begin{align}
& M(x,y)dx + N(x,y)dy = 0\\
& \dfrac{\partial M}{\partial y} = \dfrac{\partial N}{\partial x}
\end{align}
$$

### Integrating Factors

$$
I(x,y)M(x,y)dx + I(x,y)N(x,y)dy = 0 \quad \text{ is exact differential equation}
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

### First Order Linear ODE

$$
y'+P(x)y = Q(x)
$$

$$
I(x) = \exp(\int P(x)dx)
$$

$$
y = \dfrac{1}{I(x)} \int Q(x) I(x) dx + \dfrac{C}{I(x)}
$$

### Linearized ODE

- Bernoulli Equation: $$y' + P(x)y = Q(x) \cdot y^n$$. Let $$u=y^{1-n}$$
- &nbsp; $$\dfrac{dv}{dy}y' + P(x)v(y)=Q(x)$$
- Riccati Equation: $$y'=P(x)y^2 + Q(x)y + R(x)$$

## Linear ODE

We concentrate on linear ODE

$$
y'' + p(x)y' + q(x)y = f(x)
$$

If $$f(x)=0$$, we call it homogeneous equation.
Otherwise non-homogeneous equation.

### Linear ODE Theory

#### Homogeneous Equation

- Theorem 2.2:

Let $$y_1(x)$$ and $$y_2(x)$$ be solutoins of $$y''+p(x)y'+q(x)y = 0$$.
Then any linear combination of these solutions, e.g., $$c_1 y_1(x) + c_2 y_2(x)$$, is also a solutoin.

- Definition 2.1: Linear Dependence/Independence

$$
c_1 y_1 + c_2 y_2 + \dots + c_n y_n = 0
$$

only when

$$
c_1 = c_2 = \dots = 0
$$

- Wronskian

$$
\begin{equation}
W(x) = \left|\begin{array}{rr}
y_1 & y_2 \\
y_1' & y_2'
\end{array}\right| = y_1(x)y_2'(x) - y_1'(x)y_2(x)
\end{equation}
$$

If $$W(x) = 0$$, they are linear dependent. Otherwise L.I.
The Wronskian also apply for more than two functions.

$$
\begin{equation}
W(x) = \left|\begin{array}{rr}
y_1 & y_2 & y_3\\
y_1' & y_2' & y_3'\\
y_1'' & y_2'' & y_3''
\end{array}\right|
\end{equation}
$$

- Abel's Identity

$$
y'' + P(x)y' + Q(x)y = 0
$$

&nbsp; $$y_1, y_2$$ are solutions. Then

$$
W(x) = C \cdot \exp(-\int P(x)dx)
$$

- Theorem 2.4 (YouTube 8C):

Let $$y_1, y_2$$ be linearly independent solutions of $$y'' + P(x)y' + Q(x)y = 0$$.
Then every solution is a linear combination of $$y_1$$ and $$y_2$$.


$$
y'' + p(x)y' + q(x)y = 0
$$

with initial conditon $$y(x_0)=A, y'(x_0)=B$$

$$
y = C_1 y_1 + C_2 y_2
$$

#### Cramer's rule

$$
\begin{bmatrix}
y_1(x_0) & y_2(x_0)\\
y_1'(x_0) & y_2'(x_0)
\end{bmatrix}
\begin{bmatrix}
C_1\\
C_2
\end{bmatrix}=
\begin{bmatrix}
A\\
B
\end{bmatrix}
$$

$$
\begin{equation}
C_1 = \dfrac{1}{W(x_0)} \left|\begin{array}{rr}
A & y_2(x_0)\\
B & y_2'(x_0)\\
\end{array}\right|
\end{equation}
$$


$$
\begin{equation}
C_2 = \dfrac{1}{W(x_0)} \left|\begin{array}{rr}
y_1(x_0) & A\\
y_1'(x_0) & B\\
\end{array}\right|
\end{equation}
$$


#### Nonhomogeneous Equation

$$
y''+p(x) + q(x)y = f(x)
$$

Theorem 2.5:

&nbsp; $$y_1, y_2$$ is linearly independent solutions for $$y''+p(x)y'+q(x)y=0$$.
If $$y_p$$ is solution for the nonhomogeneous equation, then any solution can be given by

$$
c_1 y_1 + c_2 y_2 + y_p
$$

### Linear Constant Coefficient ODE

$$
y'' + a_1 y' + a_0 y =R(x)
$$

### Homogeneous Solutions

$$
\lambda^2 + a_1 \lambda + a_0 = 0
$$

$$
\lambda = \dfrac{-a_1 \pm \sqrt{a_1^2 - 4a_0}}{2}
$$

Case 1: $$a_1^2 - 4a_0 > 0$$

$$
\begin{align}
\lambda_1 &= \dfrac{-a_1 + \sqrt{a_1^2 - 4a_0}}{2}\\
\lambda_2 &= \dfrac{-a_1 - \sqrt{a_1^2 - 4a_0}}{2}
\end{align}
$$

$$
y_h(x) = C_1 \exp(\lambda_1 x) + C_2 \exp(\lambda_2 x)
$$

Case 2: $$a_1^2 - 4a_0 = 0$$

$$
\begin{align}
\lambda &= \dfrac{-a_1}{2}
\end{align}
$$

$$
y_h(x) = C_1 \exp(\lambda x) + C_2 x\exp(\lambda x)
$$

Case 3: $$a_1^2 - 4a_0 < 0$$

$$
\lambda = \alpha \pm i\beta
$$

$$
y_h(x) = C_1 \exp(\alpha x) \cos(\beta x) + C_2 \exp(\alpha x) \sin(\beta x)
$$


### Method of Undetermined Coefficient


$$
y^{(n)} + a_{n-1} y^{(n-1)} + \dots + a_1 y^{(1)} + a_0 y =R(x)
$$

| $$R(x)$$                                           | $$y_p(x)$$                                                                      |
|----------------------------------------------------|---------------------------------------------------------------------------------|
| $$R_1(x)+R_2(x)$$                                  | $$y_{p1}(x)+y_{p2}(x)$$                                                         |
| $$k$$                                              | $$A$$                                                                           |
| $$e^{ax}$$                                         | $$Ae^{ax}$$                                                                     |
| $$\cos ax$$                                        | $$A\cos ax + B\sin ax$$                                                         |
| $$\sin ax$$                                        | $$A\cos ax + B\sin ax$$                                                         |
| $$a_n x^n + \dots + a_1 x + a_0$$                  | $$A_n x^n + \dots + A_1 x + A_0$$                                               |
| $$e^{ax}\cos bx \quad$$ or $$\quad e^{ax}\sin bx$$ | $$e^{ax}(A\cos bx + B\sin bx)$$                                                 |
| $$e^{ax}(a_n x^n + \dots + a_1 x + a_0)$$          | $$e^{ax}(A_n x^n + \dots + A_1 x + A_0)$$                                       |
| $$\cos bx (a_n x^n + \dots + a_1 x + a_0)$$        | $$(A_n x^n + \dots + A_0)\cos bx + (B_n x^n + \dots + B_0)\sin bx$$             |
| $$e^{ax} \cos bx (a_n x^n + \dots + a_0)$$         | $$e^{ax}(A_n x^n + \dots + A_0)\cos bx + e^{ax}(B_n x^n + \dots + B_0)\sin bx$$ |

Theorem: If the $$y_p(x)$$ in the table is in the homogeneous solution, we should use $$x^m y_p(x)$$, where $$m$$ is the minimum positive integer such that $$x^m y_p(x)$$ is not in the homogeneous solution.
This claim can be proved by the method of variation of parameters.

### Method of Variation Parameter

$$
y'' + a_1(x)y' + a_0(x)y = R(x)
$$

$$
y_h(x) = C_1 y_1(x) + C_2 y_2(x)
$$

$$
y_p(x) = \phi_1(x)y_1(x) + \phi_2(x)y_2(x)
$$

$$
\begin{bmatrix}
y_1 & y_2\\
y_1' & y_2'
\end{bmatrix}
\begin{bmatrix}
\phi_1'\\
\phi_2'
\end{bmatrix}
=\begin{bmatrix}
0\\
R(x)
\end{bmatrix}
$$

$$
\phi_1(x) = \int \dfrac{-R(x)y_2(x)}{W(y_1,y_2)}dx
$$

$$
\phi_2(x) = \int \dfrac{R(x)y_1(x)}{W(y_1,y_2)}dx
$$

If third order

$$
\begin{bmatrix}
y_1 & y_2 & y_3\\
y_1' & y_2' & y_3'\\
y_1'' & y_2'' & y_3''
\end{bmatrix}
\begin{bmatrix}
\phi_1'\\
\phi_2'\\
\phi_3'
\end{bmatrix}
=\begin{bmatrix}
0\\
0\\
R(x)
\end{bmatrix}
$$

### Cauchy-Euler Equation

$$
a_n x^n y^{(n)} + \dots + a_1 x y^{(1)} + a_0 y = R(x)
$$

Let $$x = \exp(u)$$, $$u = \ln x$$ , $$D_u = \dfrac{d}{du}$$

$$
x^n \dfrac{d^n y}{dx^n} = x^n (D_x)^n y = D_u (D_u - 1) (D_u - 2) \dots (D_u - n + 1)y
$$

### Legendre ODE

$$
a_n (bx + c)^n y^{(n)} + \dots + a_1 (bx+c) y^{(1)} + a_0 y = R(x)
$$

Let $$z = bx + c$$

$$
\dfrac{d^n y}{dx^n} = b^{n} \dfrac{d^n y}{dz^n}
$$

### Reduction of Order (13A)

$$
y'' + P(x)y' + Q(x)y = R(x)
$$

if $$u(x)$$ is a homogenuous solution

$$
u'' + P(x)u' + Q(x)u = 0
$$

Let

$$
y(x) = u(x)v(x)
$$

## The Laplace Transform

### The Laplace Transform

$$
F(s) = \int_{0}^{\infty} f(t)e^{-st}dt
$$

The Laplace transform table

| $$f(t)$$      | $$F(s)$$                | Notes                 |
|---------------|-------------------------|-----------------------|
| $$t^{n}$$     | $$\dfrac{n!}{s^{n+1}}$$ | $$n = 0,1,2,3,\dots$$ |
| $$e^{at}$$    | $$\dfrac{1}{s-a}$$      |                       |
| $$\sin(at)$$  | $$\dfrac{a}{s^2+a^2}$$  |                       |
| $$\cos(at)$$  | $$\dfrac{s}{s^2+a^2}$$  |                       |
| $$\delta(t)$$ | $$1$$                   |                       |

The inverse Laplace transform table

| $$F(s)$$               | $$f(t)$$                 | Notes                 |
|------------------------|--------------------------|-----------------------|
| $$\dfrac{1}{s^{n+1}}$$ | $$\dfrac{t^n}{n!}$$      | $$n = 0,1,2,3,\dots$$ |
| $$\dfrac{1}{s-a}$$     | $$e^{at}$$               |                       |
| $$\dfrac{1}{s^2+a^2}$$ | $$\dfrac{1}{a}\sin(at)$$ |                       |
| $$\dfrac{s}{s^2+a^2}$$ | $$\cos(at)$$             |                       |


$$
\mathscr{L}\{c_1 f(t) + c_2 g(t)\} = c_1 F(s) + c_2 G(s)
$$


$$
\mathscr{L}\{f(t)e^{at}\} = F(s-a), \quad a \in \mathbb{R}
$$

$$
\mathscr{L}\{f(t-a)u(t-a)\} = e^{-as}F(s), \quad a > 0
$$


$$
\mathscr{L}\{f(at)\} = \dfrac{1}{a}F(\dfrac{s}{a}), \quad a > 0
$$

$$
\mathscr{L}\{\int_0^t f(\tau)d\tau\} = \dfrac{1}{s}F(s)
$$

$$
\mathscr{L}\{\dfrac{f(t)}{t}\} = \int_{s}^{\infty} F(u)du
$$


$$
f(t)*g(t) = \int_0^t f(\tau)g(t-\tau) d\tau
$$


$$
\mathscr{L}\{f(t)*g(t)\} = F(s)G(s)
$$

### Heaviside Expansion

$$
F(s) = \dfrac{P(s)}{Q(s)}
$$

Assume $$P(s), Q(s)$$ are real polynomials, they have no common factors, and the order of $$Q(s)$$ is higher than $$P(s)$$.

Case 1: $$Q(s)=0$$ has $$n$$ distinct roots.

$$
\dfrac{P(s)}{Q(s)} = \dfrac{A_1}{s-a_1} + \dfrac{A_2}{s-a_2} + \dots + \dfrac{A_n}{s-a_n}
$$

$$
A_k = \dfrac{P(s)}{Q(s)} \cdot (s-a_k)
$$

Case 2: $$Q(s)=0$$ has repeated roots, e.g., $$m$$-repeated $$a_k$$.

$$
\dfrac{P(s)}{Q(s)} = \dfrac{A_1}{s-a_1} + \dots + \dfrac{C_m}{(s-a_k)^m} + \dfrac{C_{m-1}}{(s-a_k)^{m-1}} + \dots \dfrac{C_1}{s-a_k} + \dots
$$

$$
C_m = \lim_{s\to a_k} [\dfrac{P(s)}{Q(s)} (s-a_k)^m ]
$$

$$
C_{m-1} = \lim_{s\to a_k} \{ \dfrac{d}{ds}[\dfrac{P(s)}{Q(s)} (s-a_k)^m]\}
$$

$$
C_{m-1} = \dfrac{1}{2!} \lim_{s\to a_k} \{ \dfrac{d^2}{ds^2}[\dfrac{P(s)}{Q(s)} (s-a_k)^m]\}
$$

Case 3: complex conjugate roots

$$
\dfrac{As + B}{(s-a)^2+b^2}
$$

$$
\lim_{s\to a+b j} \{\dfrac{P(s)}{Q(s)}[(s-a)^2+b^2]\} = A(a+bj) + B
$$

### Solution of Initial Value Problems

$$
\mathscr{L}\{f^{(n)}(t)\} = s^n F(s) - s^{n-1} f(0) - s^{n-2}f'(0) - \dots - f^{(n-1)}(0)
$$

### ODE with Polynomial Coefficients

$$
\mathscr{L}\{t^n f(t)\} = (-1)^n\dfrac{d^n F(s)}{ds^n}
$$

### Systems of Linear ODEs

20E

## Series Solutions

### Power Series

Definition 4.4 (Power Series):

$$
\sum_{n=0}^{\infty} a_n (x-x_0)^n
$$

It is obvious it converges at $$x = x_0$$.

Theorem 4.5:

If the power series converge at $$x_1$$, then it converges absolutely for all $$x$$ such that $$\vert x-x_0 \vert < \vert x_1 - x_0\vert$$.

Theorem:

There are three possibilities:

- It converges only at $$x_0$$.
- It converges in a finite interval, the endpoints may or may not converge. $$(x_0-r, x_0+r)$$ is called the open interval of the convergence.
- It converges in $$\mathbb{R}$$.

Theorem 4.6:

For series $$\sum_{0}^{\infty} b_n$$, where $$b_n \ne 0$$ for all $$n$$. Then if $$\lim_{n\to\infty} \vert \dfrac{b_{n+1}}{b_n} \vert = L$$ exists,

- if $$L < 1$$, then the series converges absolutely.
- if $$L = 1$$, no conclusion.
- if $$L > 1$$, the series diverges.

Taylor Series:

$$
\sum_{n=0}^{\infty} \dfrac{1}{n!}f^{(n)}(x_0)(x-x_0)^n
$$

Definition 4.1 (Analytic Function):

A function $$f$$ is analytic at $$x_0$$ if $$f(x)$$ has a power series representation

$$
f(x) = \sum_{n=0}^{\infty} a_n (x-x_0)^n
$$

in a non-zero interval $$(x_0-r, x_0+r)$$.

### Solution of IVP (21E)

Theorem 4.1:

Let $$p$$ and $$q$$ be analytic at $$x_0$$. Then the initial value problem

$$
y' + p(x)y + q(x); \quad y(x_0) = y_0
$$

has a solution that is analytic at $$x_0$$.

Theorem 4.2:

Let $$p, q$$ and $$f$$ be analytic at $$x_0$$. Then the initial value problem

$$
y'' + p(x)y' + q(x)y = f(x); \quad y(x_0)=A, y'(x_0) = B
$$

has a unique solution that is also analytic at $$x_0$$.

### Recurrence Relations (22B)

match of terms

### Singular Points (23A)

- Ordinary point:

$$x_0$$ is an ordinary point of equation

$$
P(x)y'' + Q(x)y' + R(x)y = F(x)
$$

if $$P(x_0) \ne 0$$ and $$Q(x)/P(x), R(x)/P(x)$$ and $$F(x)/P(x)$$ are analytic at $$x_0$$.

- Singular point:

If it is not ordinary point, it is singular point.

- Regular singular point:

$$x_0$$ is a regular singular point of equation

$$
P(x)y'' + Q(x)y' + R(x)y = 0
$$

if $$x_0$$ is a singular point, and $$(x-x_0)\dfrac{Q(x)}{P(x)}$$ and $$(x-x_0)^2\dfrac{R(x)}{P(x)}$$ are analytic at $$x_0$$.

- Irregular singular point:

A singular point that is not regular is said to be an irregular singular point.

### Forbenius Series (23C)

$$
y(x) = \sum_{n=0}^{\infty} c_n(x-x_0)^{n+r}
$$

## Fourier Series

### Fourier Series

If function $$f(t)$$ has period $$T$$, then $$\omega = 2\pi/T$$

$$
f(t) \sim A_0 + \sum_{n=1}^{\infty} A_n \sin(n\omega t + \varphi_n)
$$

or

$$
\begin{align}
f(t) &\sim \dfrac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos(n\omega t) + b_n \sin(n\omega t)]\\
a_0 &= 2A_0 = \dfrac{2}{T} \int_T f(t)dt\\
a_n &= A_n \sin\varphi_n = \dfrac{2}{T} \int_T f(t)\cos(n\omega t)dt\\
b_n &= A_n \cos\varphi_n = \dfrac{2}{T} \int_T f(t)\sin(n\omega t)dt
\end{align}
$$

### Convergence (25C)

## Multi-Variable Functions


From [Prof. Yen's Lecture](https://ocw.nthu.edu.tw/ocw/index.php?page=course&cid=127)

### Partial Derivatives

For function $$f(x,y)$$

$$
f_{xy} = \dfrac{\partial}{\partial y} \Big(\dfrac{\partial f}{\partial x}\Big) = \dfrac{\partial^2 f}{\partial y \partial x}
$$

**Theorem (Equalty of Derivatives):** if $$f_x, f_y, f_{xy}, f_{yx}$$ are all continuous in some neighborhood of $$(x_0,y_0)$$, then $$f_{xy}=f_{yx}$$.

We say $$f$$ is $$C^n$$ if all of the partial derivatives of $$f$$, through $$n$$th order, are continuous.
For example, $$f$$ is $$C^2$$ in $$\mathbb{R}$$ if $$f_x, f_y, f_{xx}, f_{xy}, f_{yy}$$ are continuous in $$\mathbb{R}$$.

### Chain Rule

For function $$f(x(t),y(t)) = R(t)$$

$$
\dfrac{d R}{dt} = \dfrac{\partial f}{\partial x} \dfrac{d x}{dt} + \dfrac{\partial f}{\partial y} \dfrac{d y}{dt}
$$

For function $$f(u,v) = f(u(x,y), v(x,y)) = F(x,y)$$

$$
\dfrac{\partial F}{\partial x} = \dfrac{\partial f}{\partial u} \dfrac{\partial u}{\partial x} + \dfrac{\partial f}{\partial v} \dfrac{\partial v}{\partial x}
$$

Comments: we have to use a different symbol (e.g., $$R$$ or $$F$$) for the composite function, otherwise it is very easy to make mistakes.

### Taylor's Formula

For single variable function

$$
\begin{align}
f(x) &= f(a) + \dfrac{f'(a)}{1!}(x-a) + \dfrac{f''(a)}{2!}(x-a)^2 + \dots + \dfrac{f^{(n-1)}(a)}{(n-1)!}(x-a)^{n-1} + \dfrac{f^{(n)}(\xi)}{n!}(x-a)^n
\end{align}
$$

For multi-variable function

$$
f(x_0,y_0) = f(a,b) + \dfrac{1}{1!}D f\vert_{a,b} + \dots + \dfrac{1}{(n-1)!} D^{n-1} f\vert_{a,b} + \dfrac{1}{n!}D^n f\vert_{\xi,\eta}
$$

$$
D = (x_0-a)\dfrac{\partial}{\partial x} + (y_0-b)\dfrac{\partial}{\partial y}
$$

$$
Df = (x_0-a)f_x + (y_0-b)f_y
$$

$$
D^2 f = (x_0-a)^2f_{xx} + 2(x_0-a)(y_0-b)f_{xy} + (y_0-b)^2 f_{yy}
$$

or if it doesn't cause confusion

$$
f(x,y)=f(x_0,y_0) + f_x(x-x_0) + f_y(y-y_0) + \dfrac{1}{2!}[f_{xx}(x-x_0)^2 + 2f_{xy}(x-x_0)(y-y_0) + f_{yy}(y-y_0)^2]
$$


### Mean Value Theorem

For single variable function

$$
f(x) = f(a) + f'(\xi)(x-a)
$$

For multi-variable function

$$
f(x,y) = f(a,b) + (x-a)f_x(\xi,\eta) + (y-b)f_y(\xi,\eta)
$$

### Implicit Function

For explicit function $$y=y(x)$$, its implicit function counterpart is $$f(x,y)=0$$.

**Theorem:** For implicit function $$f(x,y)=0$$, if it has explicit function $$y=y(x)$$, then the corresponding $$y'=-f_x/f_y$$.

**Theorem (Implicit Function Theorem):** Let $$f(x,y)=0$$ be satisfied by a pair of real numbers $$x_0, y_0$$ so that $$f(x_0,y_0)=0$$, and suppose that $$f(x,y)$$ is $$C^1$$ in some neighborhood of $$(x_0,y_0)$$ with

$$
\dfrac{\partial f}{\partial y}(x_0,y_0) \ne 0
$$

Then $$f(x,y)=0$$ uniquely implies a function $$y(x)$$ in some neighborhood $$N$$ of $$x_0$$ such that $$y(x_0)=y_0$$, where $$y(x)$$ is differentiable in $$N$$.

**Define:** Jacobian

$$
\dfrac{\partial(f,g)}{\partial(u,v)}=
\begin{vmatrix}
f_u & f_v\\
g_u & g_v
\end{vmatrix}
$$

**Theorem:** For implicit function

$$
\begin{cases}
f(x, y; u, v)=0\\
g(x, y; u, v)=0
\end{cases}
$$

the correspond explicit function

$$
\begin{cases}
u=u(x,y)\\
v=v(x,y)
\end{cases}
$$

the derivatives $$u_x,u_y,v_x,v_y$$ can be found by

$$
\begin{bmatrix}
f_u & f_v\\
g_u & g_v
\end{bmatrix}
\begin{bmatrix}
u_x\\
v_x
\end{bmatrix}
=\begin{bmatrix}
-f_x\\
-g_x
\end{bmatrix}
$$

$$
\begin{bmatrix}
f_u & f_v\\
g_u & g_v
\end{bmatrix}
\begin{bmatrix}
u_y\\
v_y
\end{bmatrix}
=\begin{bmatrix}
-f_y\\
-g_y
\end{bmatrix}
$$

$$
u_x = \dfrac{\dfrac{\partial(f,g)}{\partial(-x,v)}}{\dfrac{\partial(f,g)}{\partial(u,v)}}, \quad
u_y = \dfrac{\dfrac{\partial(f,g)}{\partial(-y,v)}}{\dfrac{\partial(f,g)}{\partial(u,v)}}, \quad
v_x = \dfrac{\dfrac{\partial(f,g)}{\partial(u,-x)}}{\dfrac{\partial(f,g)}{\partial(u,v)}}, \quad
v_y = \dfrac{\dfrac{\partial(f,g)}{\partial(u,-y)}}{\dfrac{\partial(f,g)}{\partial(u,v)}}
$$

## 3D Vectors

### Dot Product

$$
\vec{u}\cdot\vec{v} = \left\vert\vec{u}\right\vert \left\vert\vec{u}\right\vert \cos\theta, \quad 0 \le \theta \le \pi
$$

It is projection.

$$
\vec{u}\cdot\vec{v} = \vec{v}\cdot\vec{u}
$$

### Cross Product

$$
\vec{u}\times\vec{v} = \left\vert\vec{u}\right\vert \left\vert\vec{v}\right\vert \sin\theta \,\,\vec{e} , \quad 0 \le \theta \le \pi, \quad \text{right-hand rule}
$$

It is the area of parallelogram.

$$
\vec{u}\times\vec{v} = -\vec{v}\times\vec{u}
$$

### Cartesian Coordinates

$$
\vec{u}=u_i\, \hat{i} + u_j\,\hat{j} + u_k\,\hat{k}
$$

where $$\hat{i},\hat{j},\hat{k}$$ are orthonormal basis.

$$
\hat{i}\times\hat{j}=\hat{k}, \quad \hat{j}\times\hat{k}=\hat{i}, \quad \hat{k}\times\hat{i}=\hat{j}
$$

$$
\vec{u}\times\vec{v}=
\begin{vmatrix}
\hat{i} & \hat{j} & \hat{k}\\
u_i & u_j & u_k\\
v_i & v_j & v_k
\end{vmatrix}
$$

### Multuple Products

$$
\vec{u}\cdot\left(\vec{v}\times\vec{w}\right)=\vec{u}\cdot\vec{v}\times\vec{w}=
\begin{vmatrix}
u_1 & u_2 & u_3\\
v_1 & v_2 & v_3\\
w_1 & w_2 & w_3
\end{vmatrix}=\vec{u}\times\vec{v}\cdot\vec{w}
$$

&nbsp; $$ \left\vert \vec{u}\cdot\vec{v}\times\vec{w}\right\vert $$ is the volume of the parallelepiped.

$$
\vec{u}\times\left(\vec{v}\times\vec{w}\right) = \left(\vec{u}\cdot\vec{w}\right)\vec{v} - \left(\vec{u}\cdot\vec{v}\right) \vec{w}
$$

### Differentiation

$$
\begin{align}
\vec{R}(t) &= x(t)\hat{i} + y(t)\hat{j} + z(t)\hat{k}, \quad \text{in cartesian coordinate}\\
&= r(t)\hat{e_r} + \theta(t)\hat{e_{\theta}} + z(t)\hat{k}, \quad \text{in cylindrical coordinate}\\
&= \rho(t)\hat{e_{\rho}} + \phi(t)\hat{e_\phi} + \theta(t)\hat{e_{\theta}, \quad \text{in spherical coordinate}}
\end{align}
$$

$$
\vec{R}'(t) = x'(t)\hat{i} + y'(t)\hat{j} + z'(t)\hat{k}
$$

&nbsp; $$\vec{R}'(t)$$ is at the tagent direction of the curve.

$$
\text{if } \vert R(t)\vert \text{ is constant}, \vec{R}(t) \cdot \vec{R}'(t) = 0
$$

### Polar Coordinates


<img src="/assets/img/2023-07-23-engineering-mathematics/001.png" style="width:40%;height:40%;">

$$
\begin{cases}
x = r\cos\theta\\
y = r\sin\theta
\end{cases}
$$

$$
\begin{cases}
r = \sqrt{x^2+y^2}\\
\theta = \mathrm{atan2}(y,x) \in (-\pi, \pi]
\end{cases}
$$

$$
\mathrm{atan2}(y, x)= \begin{cases}\arctan \left(\frac{y}{x}\right) & \text { if } x>0 \\ \arctan \left(\frac{y}{x}\right)+\pi & \text { if } x<0 \text { and } y \geq 0 \\ \arctan \left(\frac{y}{x}\right)-\pi & \text { if } x<0 \text { and } y<0 \\ \frac{\pi}{2} & \text { if } x=0 \text { and } y>0 \\ -\frac{\pi}{2} & \text { if } x=0 \text { and } y<0 \\ \text { undefined } & \text { if } x=0 \text { and } y=0 .\end{cases}
$$

$$
\dot{\hat{e_r}} = \dot{\theta} \hat{e_{\theta}}, \quad \dot{\hat{e_\theta}} = - \dot{\theta} \hat{e_r}
$$

$$
\vec{R}(t) = r \hat{e_r}
$$

$$
\vec{R}'(t) = \dot{r} \hat{e_r} + r \dot{\theta} \hat{e_\theta}
$$

$$
\vec{R}''(t) = (\ddot{r} - r\dot{\theta}^2) \hat{e_r} + (2 \dot{r}\dot{\theta} + r\ddot{\theta}) \hat{e_\theta}
$$

$$
\hat{e_r} = \cos\theta \hat{i} + \sin\theta \hat{j}
$$

$$
\hat{e_\theta} = -\sin\theta \hat{i} + \cos\theta\hat{j}
$$

### Cylindrical Coordinates

$$
\vec{R}(t) = r \hat{e_r} + z \hat{e_z}
$$

$$
\vec{R}'(t) = \dot{r} \hat{e_r} + r \dot{\theta} \hat{e_\theta} + \dot{z} \hat{e_z}
$$

$$
\vec{R}''(t) = (\ddot{r} - r\dot{\theta}^2) \hat{e_r} + (2 \dot{r}\dot{\theta} + r\ddot{\theta}) \hat{e_\theta} + \ddot{z} \hat{e_z}
$$

### Spherical Coordinates


<img src="/assets/img/2023-07-23-engineering-mathematics/002.png" style="width:40%;height:40%;">

$$
\begin{cases}
x = \rho\sin\phi\cos\theta\\
y = \rho\sin\phi\sin\theta\\
z = \rho\cos\phi
\end{cases}
$$

$$
\hat{e_\rho} = \hat{e_\rho}(\phi,\theta), \quad \hat{e_\phi} = \hat{e_\phi}(\phi,\theta), \quad \hat{e_\theta} = \hat{e_\theta}(\theta)
$$

$$
\partial \hat{e_\rho} / \partial \rho = 0, \quad \partial \hat{e_\rho} / \partial \phi
$$

Now 4A
