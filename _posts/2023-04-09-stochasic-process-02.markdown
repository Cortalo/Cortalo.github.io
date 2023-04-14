---
title:  "Stochastic Process 02"
date:   2023-04-09 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's Lecture 02](https://v.ucas.ac.cn/course/CourseIndex.do?courseid=b917aacfcbfe4649aaec1d46bb8edd51)

# Correlation Functions

Correlation functions are special functions, they have many interesting and good properties.

$$
R_{X}(t,s) = E(X(t)X(s))
$$

as we know correlation is an inner product, we can have, where we denote $$R_X$$ as $$R$$

- &nbsp; $$R(t,s) = R(s,t)$$
- &nbsp; $$\vert R(t,s) \vert \le \sqrt{R(t,t)R(s,s)}$$, from Cauchy

If it is W.S.S., $$R(t,s) = R(t-s)$$

- &nbsp; $$R(\tau) = R(-\tau)$$
- &nbsp; $$\vert R(\tau) \vert \le R(0)$$
- &nbsp; $$R(\tau)$$ is positive definite.

## Positive Definite Function

$$
f(x) \text{ is P.D.} \quad \iff \quad \forall x_1, x_2, \dots, x_n, \text{ the matrix } (f(x_i-x_j))_{ij} \text{ is P.D. }
$$

where it means put it in $$i$$ row and $$j$$ column.

Remember the P.D. matrix is defined as, for a $$n \times n$$ symmetry matrix, if $$\forall \alpha \in \mathbb{R}^n, \alpha^{T}A\alpha \ge 0$$, then matrix $$A$$ is P.D.

For P.D. matrix, all the leading principal minors are $$\ge 0$$.

### Some properties of P.D. function

If function $$f(x)$$ is P.D.

- &nbsp; $$f(0) \ge 0$$.

we take $$n = 1$$, then the matrix $$f(0)$$ is P.D.

- &nbsp; $$f(x)$$ is an even function.
- &nbsp; $$f(0) \ge \vert f(\tau) \vert, \forall \tau \in \mathbb{R}$$.

we take $$n = 2$$, where $$x_1 = 0, x_2 = \tau$$

$$
\begin{bmatrix}
f(x_1 - x_1) & f(x_1 - x_2) \\
f(x_2 - x_1) & f(x_2 - x_2) \\
\end{bmatrix}
=
\begin{bmatrix}
f(0) & f(-\tau)\\
f(\tau) & f(0)
\end{bmatrix}
$$

it is P.D., thus it is symmetry, $$f(\tau) = f(-\tau)$$. Also its determinant is positive, thus $$f(0) \ge \vert f(\tau) \vert$$.

### Prove $$R(\tau)$$ is P.D.

Let

$$
X = (X(\tau_1, \dots, \tau_n))^{\mathrm{T}}
$$

then

$$
(R(\tau_i - \tau_j))_{ij} = E(X X^{\mathrm{T}})
$$

$$
\begin{align}
\alpha^{\mathrm{T}} E(X X^{\mathrm{T}}) \alpha = E(\alpha^{\mathrm{T}} X X^{\mathrm{T}} \alpha) = E((\alpha^{\mathrm{T}}X) (\alpha^{\mathrm{T}} X)^{\mathrm{T}}) = E((\alpha^{\mathrm{T}} X)^2) \ge 0
\end{align}
$$

## More $$R(\tau)$$ Properties: Local to Global

Let $$R(\tau)$$ be the auto-correlation of a W.S.S. process.

- &nbsp; if $$\exists T > 0, R(T) = R(0)$$, then $$R(\tau) = R(\tau + T) \quad \forall \tau$$

We will go through

$$
R(0) = R(T) \quad  \implies \quad E|X(\tau + T) - X(\tau)|^2 = 0 \quad \implies \quad R(\tau) = R(\tau + T)
$$

first

$$
\begin{align}
&E|X(\tau + T) - X(\tau)|^2 \\
=& E(X^2(\tau+T)) + E(X^2(\tau)) - 2 E(X(t+T)X(\tau)) \\
=& R(0) + R(0) - 2R(T) = 0
\end{align}
$$

then

$$
\begin{align}
&\vert R(\tau + T) - R(\tau) \vert \\
=& \vert E(X(0)X(\tau+T)) - E(X(0)X(\tau)) \vert\\
=& \vert E[X(0)(X(\tau+T) - X(\tau))] \vert
\end{align}
$$

use Cauchy

$$
\begin{align}
& \vert E[X(0)(X(\tau+T) - X(\tau))] \vert\\
\le & \sqrt{E\vert X(0)\vert^2 \cdot E \vert X(\tau+T) - X(\tau) \vert^2} = 0
\end{align}
$$

- &nbsp; if $$R(\tau)$$ is continuous at 0, then it is continuous at all $$\tau \in \mathbb{R}$$.

Similar, we prove in the middle

$$
E|X(\tau + \Delta) - X(\tau)|^2 \to 0 \text{ when } \Delta \to 0
$$

Proof in the video.

## P.D. Function Criterion

From Bochner's result. A function $$f(x)$$ is P.D., if and only if its Fourier transform is always $$\ge 0$$.

$$
\int_{-\infty}^{\infty} f(x) e^{j\omega x} dx \ge 0
$$

Some where in the video, any W.S.S. auto-correlation function is P.D.. For any P.D. function, you can find an W.S.S. process such that is auto-correlation is that P.D. function. P.D. is the characteristic property of W.S.S. auto-correlation function.

- Prove $$\int_{-\infty}^{\infty} f(x) e^{j\omega x} dx \ge 0 \quad \implies \quad f(x)$$ is P.D.
