---
title:  "Advanced Differential Equations 003"
date:   2023-07-23 08:00:00 +0200
categories: math
tags: math
math: true
---


From [Prof. J. Nathan Kutz' Lecture 003](https://faculty.washington.edu/kutz/am568/am568.html)

## Linear Operators And Thier Adjoints

### Fredholm Alternative Theorem

Given a matrix $$\mathbf{A} \in \mathbb{C}^{m\times n}$$, then the vector $$\mathbf{Ax}$$, where $$x \in \mathbb{C}^n$$ must be orthogonal to the null space of $$\mathbf{A}^{\mathsf{H}}$$. First recall the definition of inner product is

$$
\braket{\mathbf{a},\mathbf{b}} = \mathbf{b}^{\mathsf{H}} \mathbf{a}
$$

thus

$$
\begin{align}
\braket{\mathbf{Ax}, \mathbf{y}} &= \braket{\mathbf{x},\mathbf{A}^{\mathsf{H}}\mathbf{y}}\\
\braket{\mathbf{x},\mathbf{Ay}} &= \braket{\mathbf{A}^{\mathsf{H}}\mathbf{x}, \mathbf{y}}
\end{align}
$$

Assume $$\mathbf{A}^{\mathsf{H}} \mathbf{y}=0$$, then

$$
\braket{\mathbf{Ax},\mathbf{y}} = \braket{\mathbf{x},\mathbf{A}^{\mathsf{H}}\mathbf{y}} = 0
$$

### Linear Operators


$$
Lu=f
$$

where $$L$$ will be a linear, differential operator on the domain $$x\in [0,l]$$ and with boundary conditions specified at $$x=0$$ and $$x=l$$ which will be specified shortly.
The definition of inner product is given by

$$
\braket{u,v} = \int_{0}^{l} uv^{*}dx
$$

we want to find the adjoint operator such that

$$
\braket{v,Lu}=\braket{L^{\dagger}v,u}
$$

For example

$$
L = a(x)\dfrac{d^2}{dx^2} + b(x)\dfrac{d}{dx} + c(x)
$$

on the domain $$x\in[a,b]$$ with boundary conditions

$$
\begin{align}
\alpha_1 u(a) + \beta_1 \dfrac{d u(a)}{dx} &= 0\\
\alpha_2 u(b) + \beta_2 \dfrac{d u(b)}{dx} &= 0
\end{align}
$$

assume we are working on real functions $$u,v$$ we can calculate

$$
\begin{align}
\braket{v,Lu} &=\int_{a}^b v \bigg( a(x)\dfrac{d^2 u}{dx^2} + b(x)\dfrac{du}{dx} + c(x)u \bigg)dx\\
&=\int_a^b \bigg( a(x)v\dfrac{d^2 u}{dx^2} + b(x)v\dfrac{du}{dx} + c(x)vu \bigg)dx
\end{align}
$$

using integration by part

$$
\int udv = uv - \int vdu
$$

$$
u= av, \quad v =u_x
$$

$$
du = (av)_x dx, \quad dv = u_{xx}dx
$$

$$
\begin{align}
\int_{a}^b avu_{xx}dx &= avu_x\vert_{a}^b - \int_a^b u_x (av)_x dx\\
&= avu_x\vert_{a}^b - (av)_x u\vert_{a}^b + \int_a^b u(av)_{xx} dx
\end{align}
$$

$$
\int_a^b bvu_x dx = buv\vert_a^b - \int_a^b u(bv)_x dx
$$

$$
\braket{v,Lu} = (avu_x - (av)_x u + uvb)\vert_a^b + \int_a^b [(av)_{xx} u - (bv)_x u + cvu] dx
$$

Thus the formal adjoint is given by

$$
L^{\dagger}v = \dfrac{d^2}{dx^2}(a(x)v) - \dfrac{d}{dx}(b(x)v) + c(x)v
$$

also the boundary condition for operator $$L^{\dagger}$$ can be given by

$$
(avu_x - (av)_x u + uvb)\vert_a^b = 0
$$
