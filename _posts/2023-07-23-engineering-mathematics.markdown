---
title:  "Engineering Mathematics"
date:   2023-07-23 09:00:00 +0200
categories: math
tags: math
math: true
---

From [Dr. Chun-Yao Wang' Lecture](https://ocw.nthu.edu.tw/ocw/index.php?page=course&cid=145)

## Integration Formulas

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


## Ordinary, Partial, Order, Degree And More

Ordinary differential equation.

Partial differential equation.

Order of the differential equation.

Degree of the differential equation.

Linear differential equation.

General solution.

Particular solution.

Singular solution.

## First-Order First-Degree ODE

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

10G
