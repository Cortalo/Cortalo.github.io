---
title:  "Advanced Differential Equations 001"
date:   2023-07-22 07:00:00 +0200
categories: math
tags: math
math: true
---


From [Prof. J. Nathan Kutz' Lecture 001](https://faculty.washington.edu/kutz/am568/am568.html)

## Phase-Plane Analysis For Nonlinear Dynamics

We begin by reviewing linear system

$$
\mathbf{x}'=\mathbf{Ax}
$$

where

$$
\mathbf{x} \in \mathbb{R}^{2}, \mathbf{A} \in \mathbb{R}^{2 \times 2}
$$

The equilibrium points of this system are determined by setting $$\mathbb{x}'=0$$.

$$
\mathbf{x}'=\mathbf{Ax}=0 \implies \mathbf{x}=0
$$

Here we assume $$A$$ is not singular.
The differential equation can be solved by

$$
\mathbf{x}=\mathbf{v}e^{\lambda t} \implies (\mathbf{A}-\lambda \mathbf{I})\mathbf{v}=0
$$

There are five cases

- Cases 1: eigenvalues are real, unequal, same sign

$$
\mathbf{x} = c_1 \mathbf{v}^{(1)}e^{\lambda_1 t} + c_2 \mathbf{v}^{(2)} e^{\lambda_2 t}
$$

- Cases 2: eigenvalues are real, opposite sign

$$
\mathbf{x} = c_1 \mathbf{v}^{(1)}e^{\lambda_1 t} + c_2 \mathbf{v}^{(2)} e^{-\lambda_2 t}
$$

- Cases 3: eigenvalues are real and equal

For the case of a double root, two possibilities exist: either we can find two linearly independent eigenvectors so that our solution is

$$
\mathbf{x} = c_1 \mathbf{v}^{(1)}e^{\lambda_1 t} + c_2 \mathbf{v}^{(2)} e^{\lambda_1 t}
$$

or, there is only one eigenvector, and we must generate a generalized eigenvector via the methods

$$
\mathbf{x} = c_1 \mathbf{v}^{(1)}e^{\lambda_1 t} + c_2 [\mathbf{v}^{(1)}t e^{\lambda_1 t}+\boldsymbol{\eta}e^{\lambda_1 t}]
$$

- Cases 4: eigenvalues are complex eigenvalues

$$
\lambda_{\pm} = \beta \pm i\mu
$$

- Cases 5: eigenvalues are purely imaginary

$$
\lambda_{\pm} = \pm i\mu
$$
