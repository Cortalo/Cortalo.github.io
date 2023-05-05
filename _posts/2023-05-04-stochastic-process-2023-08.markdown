---
title:  "Stochastic Process 2023 08"
date:   2023-05-04 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's 2023 Lecture 08](https://v.ucas.ac.cn/course/CourseIndex.do?menuCode=2&courseid=456bd6a25b7046d4a0482cddf1a285bb)

# Gaussian Processes

## Sample Mean and Variance

&nbsp; $$ X_1, X_2, \dots, X_n \overset{\text{i.i.d.}}{\sim} N(\mu, \sigma^2)$$, we look at $$\overline{X} = \dfrac{1}{n} \sum_{k=1}^{n} X_k, \quad \overline{S} = \dfrac{1}{n-1} \sum_{k=1}^n (X_k - \overline{X})^2$$, we will prove $$\overline{X}, \overline{S}$$ are independent.

$$
\begin{align}
& (n-1) \overline{S} = \sum_{k=1}^n (X_k - \overline{X})^2\\
=& \sum_{k=1}^n (X_k^2 - 2X_k \overline{X} + (\overline{X})^2)\\
=& \sum_{k=1}^n X_k^2 - n (\overline{X})^2
\end{align}
$$

we design a matrix

$$
A =
\begin{pmatrix}
\frac{1}{\sqrt{n}} & \frac{1}{\sqrt{n}} & \dots & \frac{1}{\sqrt{n}}\\
\dots & \dots & \dots & \dots\\
\vdots & \vdots & \ddots & \vdots\\
\dots & \dots & \dots & \dots
\end{pmatrix}
$$

such that $$A A^{\intercal} = A^\intercal A = I$$

Then, for $$Y = AX$$, we know $$Y \sim N(A \mu, A \sigma^2 I A^\intercal) = N(A \mu, \sigma^2 I)$$ $$Y_1 = \sqrt{n}\cdot\overline{X}$$. Also

$$
X = A^\intercal Y
$$

$$
\begin{align}
& (n-1) \overline{S} = \sum_{k=1}^n X_k^2 - n(\overline{X})^2\\
=& X^\intercal X - n(\overline{X})^2\\
=& Y^\intercal A A ^\intercal Y - Y_1^2\\
=& \sum_{k=2}^n Y_k^2
\end{align}
$$

Thus we know $$(n-1) \overline{S}$$ are independent with $$Y_1$$

## Conditional Distribution

$$
(X_1, X_2) \sim N\Bigg(
\begin{pmatrix}
\mu_1\\
\mu_2
\end{pmatrix},
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}
\Bigg), \quad
X_1 \in \mathbb{R}^m, X_2 \in \mathbb{R}^n
$$

We want to find the distribution $$f_{X_2 \vert X_1} (x_2 \vert x_1) = f_{X_1, X_2}(x_1, x_2) / f_{X_1}(x_1)$$, we need to deal with the following

$$
\exp \Bigg( -\frac{1}{2}
\begin{pmatrix}
x_1 - \mu_1\\
x_2 - \mu_2
\end{pmatrix}^\intercal
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}^{-1}
\begin{pmatrix}
x_1 - \mu_1\\
x_2 - \mu_2
\end{pmatrix}
- \frac{1}{2} (x_1^\intercal - \mu_1^\intercal) \Sigma_{11}^{-1} (x_1 - \mu_1)
\Bigg)
$$

First we need to calculate the inverse

$$
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}
\begin{array}{c}
  \begin{pmatrix}
    I & 0 \\
    -\Sigma_{21} \Sigma_{11}^{-1} & I
  \end{pmatrix} \\
  \xrightarrow[\text{left}]{\hspace{3cm}}
\end{array}
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
0 &  \Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12}
\end{pmatrix}
$$

$$
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
0 &  \Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12}
\end{pmatrix}
\begin{array}{c}
  \begin{pmatrix}
    I & -\Sigma_{11}^{-1} \Sigma_{12} \\
    0 & I
  \end{pmatrix} \\
  \xrightarrow[\text{right}]{\hspace{3cm}}
\end{array}
\begin{pmatrix}
\Sigma_{11} & 0\\
0 &  \Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12}
\end{pmatrix}
$$

Thus

$$
\begin{pmatrix}
  I & 0 \\
  -\Sigma_{21} \Sigma_{11}^{-1} & I
\end{pmatrix}
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}
\begin{pmatrix}
  I & -\Sigma_{11}^{-1} \Sigma_{12} \\
  0 & I
\end{pmatrix}=
\begin{pmatrix}
\Sigma_{11} & 0\\
0 &  \Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12}
\end{pmatrix}
$$

we know

$$
\begin{pmatrix}
I & 0\\
A & I
\end{pmatrix}^{-1} =
\begin{pmatrix}
I & 0\\
-A & 0
\end{pmatrix}
$$

$$
\begin{pmatrix}
I & A\\
0 & I
\end{pmatrix}^{-1} =
\begin{pmatrix}
I & -A\\
0 & 0
\end{pmatrix}
$$

thus

$$
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}=
\begin{pmatrix}
  I & 0 \\
  \Sigma_{21} \Sigma_{11}^{-1} & I
\end{pmatrix}
\begin{pmatrix}
\Sigma_{11} & 0\\
0 &  \Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12}
\end{pmatrix}
\begin{pmatrix}
  I &\Sigma_{11}^{-1} \Sigma_{12} \\
  0 & I
\end{pmatrix}
$$

thus

$$
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}^{-1}=
\begin{pmatrix}
  I &-\Sigma_{11}^{-1} \Sigma_{12} \\
  0 & I
\end{pmatrix}
\begin{pmatrix}
\Sigma_{11}^{-1} & 0\\
0 &  (\Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12})^{-1}
\end{pmatrix}
\begin{pmatrix}
  I & 0 \\
  -\Sigma_{21} \Sigma_{11}^{-1} & I
\end{pmatrix}
$$

we can continue

$$
\begin{align}
&\begin{pmatrix}
x_1 - \mu_1\\
x_2 - \mu_2
\end{pmatrix}^\intercal
\begin{pmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{pmatrix}^{-1}
\begin{pmatrix}
x_1 - \mu_1\\
x_2 - \mu_2
\end{pmatrix}\\
=&
\big( x_1^\intercal - \mu_1^\intercal \, , \, x_2^\intercal - \mu_2^\intercal - (x_1^\intercal - \mu_1^\intercal)\Sigma_{11}^{-1} \Sigma_{12}\big)
\begin{pmatrix}
\Sigma_{11}^{-1} & 0\\
0 &  (\Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12})^{-1}
\end{pmatrix}
\begin{pmatrix}
x_1 - \mu_1\\
x_2 - \mu_2 - \Sigma_{21}\Sigma_{11}^{-1}(x_1 - \mu_1)
\end{pmatrix}\\
=& (x_1^\intercal - \mu_1^\intercal) \Sigma_{11}^{-1} (x_1 - \mu_1) + \big(x_2 - \mu_2 - \Sigma_{21} \Sigma_{11}^{-1}(x_1-\mu_1) \big)^\intercal (\Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12})^{-1} \big(x_2 - \mu_2 - \Sigma_{21} \Sigma_{11}^{-1} (x_1 - \mu_1)\big)
\end{align}
$$

thus

$$
\exp \Big( -\dfrac{1}{2} \big(x_2 - \mu_2 - \Sigma_{21} \Sigma_{11}^{-1}(x_1-\mu_1) \big)^\intercal (\Sigma_{22} - \Sigma_{21} \Sigma_{11}^{-1} \Sigma_{12})^{-1} \big(x_2 - \mu_2 - \Sigma_{21} \Sigma_{11}^{-1} (x_1 - \mu_1)\big) \Big)
$$

and

$$
f_{X_2 \vert X_1} (x_2 \vert x_1) \sim N(\mu_2 + \Sigma_{21}\Sigma_{11}^{-1}(x_1 - \mu_1), \Sigma_{22} - \Sigma_{21}\Sigma_{11}^{-1}\Sigma_{12})
$$

## Special Cases

If $$X_1, X_2 \in \mathbb{R}$$

$$
E(X_2 \vert X_1) = \mu_2 + \dfrac{\sigma_{21}}{\sigma_{11}}(x_1 - \mu_1)
$$

$$
\mathrm{Var}(X_2 \vert X_1) = \sigma_{22} - \dfrac{\sigma_{21}^2}{\sigma_{11}}
$$

## More Examples

With the conclusion we have, we can do

$$
E(f(X_2) \vert X_1)
$$

for any function $$f$$, since we know it is a normal distribution.

We have conditional pdf, conditional expection, why we didn't have conditional variable?

For $$Y \sim N(0, \sigma^2)$$, let's calculate $$E(Y^n)$$

$$
E(Y^n) =
\begin{cases}
0, \quad n = 2k-1\\
(2k-1)!! \sigma^{2k}, \quad n = 2k
\end{cases}
$$

$$
\begin{align}
&\int_{-\infty}^{\infty} y^{2k} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) dy\\
=& -\sigma^2 \int_{-\infty}^{\infty} y^{2k-1} d\Big( \exp\big( - \dfrac{y^2}{2\sigma^2}\big) \Big)\\
=& -\sigma^2 y^{2k-1} \exp \big( -\dfrac{y^2}{2\sigma^2} \big) \Big\vert_{-\infty}^{\infty} + (2k-1)\sigma^2 \int_{-\infty}^{\infty} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) y^{2k-2} dy\\
=& (2k-1)\sigma^2 \int_{-\infty}^{\infty} \exp\big(-\dfrac{y^2}{2\sigma^2} \big) y^{2k-2} dy
\end{align}
$$

Thus

$$
E(Y^{2k}) = (2k-1)\sigma^2 E(Y^{2k-2})
$$

Thus

$$
E(Y^{2k}) = (2k-1)!! \sigma^{2k}
$$

where

$$
(2k-1)!! = (2k-1) (2k-3) \dots 1
$$

$$
\begin{align}
E(Y^2) &= \sigma^2\\
E(Y^4) &= 3 \sigma^4\\
E(Y^6) &= 15 \sigma^6
\end{align}
$$

For $$Y \sim N(\mu, \sigma^2)$$, how to calculate $$E(\cos(Y))$$?

$$
\cos(Y) = \dfrac{1}{2} \big( \exp(jY) + \exp(-jY) \big)
$$

$$
\begin{align}
E(\cos(Y)) &= \dfrac{1}{2} E\big( \exp(jY) + \exp(-jY) \big)\\
&= \dfrac{1}{2} \big(\Phi_Y(1) + \Phi_Y(-1) \big)\\
&= \dfrac{1}{2} \big( \exp(j \mu - \frac{1}{2}\sigma^2) + \exp(-j\mu - \frac{1}{2} \sigma^2) \big)\\
&= \exp\big(-\frac{1}{2} \sigma^2 \Big) \cos(\mu)
\end{align}
$$

## Bayes

Assume $$X \sim N(\mu, \Sigma_X), \quad Y = B X + Z$$, where $$X, Z$$ are independent, $$Z \sim N(0, \sigma^2 I)$$. We want to investigate $$X \vert Y$$. It can be understand as $$Y$$ is the observed value, $$X$$ is the state.
