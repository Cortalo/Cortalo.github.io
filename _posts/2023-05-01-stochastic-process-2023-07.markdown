---
title:  "Stochastic Process 2023 07"
date:   2023-05-01 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's 2023 Lecture 07](https://v.ucas.ac.cn/course/CourseIndex.do?menuCode=2&courseid=456bd6a25b7046d4a0482cddf1a285bb)

# Gaussian Processes

## Definition

If $$X(t)$$ is a Gaussian Processes, then $$\forall n, \forall t_1, \dots, t_n$$, the $$X = (X(t_1), \dots, X(t_n))^{\mathrm{T}}$$ follows Gaussian distribution. $$X \sim N(\mu, \Sigma)$$, where $$\mu = E(X), \Sigma = E(X-\mu)(X-\mu)^{\mathrm{T}}$$. It has pdf

$$
f(x) = \dfrac{1}{(2\pi)^{n/2} (\mathrm{det} \Sigma)^{1/2}} \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} \Sigma^{-1} (x-\mu) \big)
$$

Let's first do an exercise to be familiar with the notation. Let's verify its integration is 1.


$$
\begin{align}
\int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} \Sigma^{-1} (x-\mu) \big) dx
\end{align}
$$

we need to diagonalize $$\Sigma^{-1}$$. Since $$\Sigma$$ is P.D., we know $$\Sigma = U^{\mathrm{T}} \Lambda U$$, where $$\Lambda = \mathrm{diag}(\lambda_1, \dots, \lambda_n), U^{\mathrm{T}}U = U U^{\mathrm{T}} = I$$. And

$$\Sigma^{-1} = U^{\mathrm{T}} \Lambda^{-1} U = U^{\mathrm{T}} \Lambda^{-\frac{1}{2}} \Lambda^{-\frac{1}{2}}U = B^{\mathrm{T}} B$$

$$
\begin{align}
&\int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} \Sigma^{-1} (x-\mu) \big) dx\\
=& \int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} B^{\mathrm{T}} B (x-\mu) \big) dx
\end{align}
$$

Let $$y = B x$$. We need to calculate

$$
\begin{align}
dx &= \bigg\vert \mathrm{det} \dfrac{\partial x}{\partial y} \bigg\vert dy\\
&= \bigg\vert \mathrm{det} \dfrac{\partial y}{\partial x} \bigg\vert^{-1} dy\\
&= \bigg\vert \mathrm{det} B \bigg\vert^{-1} dy\\
&= \bigg\vert \mathrm{det} \Lambda^{-\frac{1}{2}} \mathrm{det} U \bigg\vert^{-1} dy\\
&= \bigg\vert \mathrm{det} \Lambda \bigg\vert^{1/2} dy\\
&= ( \mathrm{det} \Sigma )^{1/2} dy
\end{align}
$$

$$
\begin{align}
& \int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} B^{\mathrm{T}} B (x-\mu) \big) dx\\
=& ( \mathrm{det} \Sigma )^{1/2}\int \exp \big( -\frac{1}{2} y^{\mathrm{T}} y \big)   dy\\
=& ( \mathrm{det} \Sigma )^{1/2}\bigg(\int_{-\infty}^{\infty} \exp \big( -\frac{\tau^2}{2} \big)   d\tau\bigg)^{n}
\end{align}
$$

we know

$$
\int_{-\infty}^{\infty} \exp \big( -\frac{\tau^2}{2} \big)   d\tau = \sqrt{2\pi}
$$

but let's prove it just for fun. Interestingly its indefinite integral doesn't exist, we can't find its primitive function then use the bounds.

$$
\begin{align}
&\int_{-\infty}^{\infty} \exp \big( -\frac{x^2}{2} \big) dx \int_{-\infty}^{\infty} \exp \big( -\frac{y^2}{2} \big) dy\\
=&\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp \big( -\frac{x^2+y^2}{2} \big) dx dy
\end{align}
$$

we change to polar axis

$$
\begin{align}
&\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp \big( -\frac{x^2+y^2}{2} \big) dx dy\\
=&\int_{0}^{\infty} \int_{2\pi}^{0} \exp \big( -\frac{r^2}{2} \big)r d\theta dr\\
=& 2\pi \int_{0}^{\infty} \exp \big( -\frac{r^2}{2} \big)r dr\\
=& 2\pi \int_{0}^{\infty} \exp ( -u ) d u\\
=& 2\pi \cdot \big(-\exp(-u)\big) \big\vert_{0}^{\infty}\\
=& 2\pi
\end{align}
$$

thus


$$
f(x) = \dfrac{1}{(2\pi)^{n/2} (\mathrm{det} \Sigma)^{1/2}} \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} \Sigma^{-1} (x-\mu) \big)
$$

$$
\begin{align}
&\int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} \Sigma^{-1} (x-\mu) \big) dx\\
=& \int \exp \big( -\frac{1}{2} (x-\mu)^{\mathrm{T}} B^{\mathrm{T}} B (x-\mu) \big) dx\\
=& ( \mathrm{det} \Sigma )^{1/2}\bigg(\int_{-\infty}^{\infty} \exp \big( -\frac{\tau^2}{2} \big)   d\tau\bigg)^{n}\\
=& (2\pi)^{n/2} (\mathrm{det} \Sigma)^{1/2}
\end{align}
$$

## Characteristic Function

$$
\Phi_X(\omega) = E(\exp(j \omega^{\intercal} X)) = \exp\big(j \omega^\intercal \mu - \frac{1}{2} \omega^\intercal \Sigma \omega\big)
$$

$$
\begin{align}
\dfrac{1}{(2\pi)^{n/2}(\mathrm{det}\Sigma)^{1/2}} \int_{\mathbb{R}^n} \exp(j \omega^\intercal x) \exp\big( -\frac{1}{2}(x-\mu)^\intercal \Sigma^{-1} (x-\mu) \big) dx
\end{align}
$$

a small trick to find how to complete the square, from

$$
-\frac{1}{2} (x-\mu)^\intercal \Sigma^{-1} (x-\mu) + j \omega^\intercal x
$$

we try to look

$$
\begin{align}
&-\dfrac{1}{2\sigma^2} (x-\mu)^2 + j\omega x\\
=& -\dfrac{1}{2\sigma^2} (x - \mu - j\sigma^2 \omega)^2 + j \omega \mu - \frac{1}{2}\sigma^2 \omega^2
\end{align}
$$

then

$$
\begin{align}
&-\frac{1}{2} (x-\mu)^\intercal \Sigma^{-1} (x-\mu) + j \omega^\intercal x\\
= & - \frac{1}{2} (x - \mu - j \Sigma \omega)^{\intercal} \Sigma^{-1} (x - \mu - j \Sigma \omega ) + j \omega^\intercal \mu - \frac{1}{2}\omega^{\intercal} \Sigma \omega
\end{align}
$$

thus

$$
\begin{align}
&\int_{\mathbb{R}^n} \exp(j \omega^\intercal x) \exp\big( -\frac{1}{2}(x-\mu)^\intercal \Sigma^{-1} (x-\mu) \big) dx\\
=& \exp\big(j\omega^\intercal \mu - \frac{1}{2} \omega^\intercal \Sigma \omega\big) \int_{\mathbb{R}^n} \exp\big(-\frac{1}{2} (x-\mu - j \Sigma \omega)^\intercal \Sigma^{-1} (x-\mu - j \Sigma \omega)\big) dx
\end{align}
$$

The intergration inside just change the mean, thus

$$
\Phi_X(\omega) = E(\exp(j \omega^{\intercal} X)) = \exp\big(j \omega^\intercal \mu - \frac{1}{2} \omega^\intercal \Sigma \omega\big)
$$

## Linear Property

&nbsp; $$X \in \mathbb{R}^n, X \sim N(\mu, \Sigma). A \in \mathbb{R}^{m \times n}, Y = A X \in \mathbb{R}^m$$, then

$$
Y \sim N(A \mu, A \Sigma A^\intercal)
$$

$$
\begin{align}
\Phi_{Y}(\omega) &= E(\exp(j \omega^\intercal Y))\\
&= E(\exp(j \omega^\intercal A X))\\
&= E(\exp(j (A^\intercal \omega)^\intercal X))\\
&= \exp\big( j (A^\intercal \omega)^\intercal \mu - \frac{1}{2} (A^\intercal \omega)^\intercal \Sigma (A^{\intercal} \omega) \big)\\
&= \exp\big( j \omega^\intercal A \mu - \frac{1}{2} \omega^\intercal A \Sigma A^\intercal \omega \big)
\end{align}
$$

Then it is obvious, if joint-pdf is Gaussian, then all the $$n$$ individual random variables are boundary Gaussian.

But even if all the $$n$$ individual random variables are boundary Gaussian, it may not be joint Gaussian.

Actually, for $$X \in \mathbb{R}^n$$, we will need $$\forall \alpha \in \mathbb{R}^n, \alpha^\intercal X$$ is Gaussian to make sure $$X$$ is joint Gaussian.

$$
\begin{align}
\Phi_X(\omega) &= E(\exp(j \omega^\intercal X)) = \Phi_{\omega^\intercal X}(1)\\
&= \exp\big( j \mu_{\omega^\intercal X} - \frac{1}{2} \sigma_{\omega^\intercal X}^2 \big)
\end{align}
$$

we know

$$
\mu_{\omega^\intercal X} = E(\omega^\intercal X) = \omega^{\intercal} \mu_X
$$

$$
\begin{align}
&\sigma_{\omega^\intercal X}^2 = E(\omega^\intercal X - \omega^\intercal \mu_X)^2\\
=& E(\omega^\intercal (X - \mu_X) (X - \mu_X)^\intercal \omega)\\
=& \omega^\intercal E((X - \mu_X)(X - \mu_X)^\intercal) \omega\\
=& \omega^\intercal \Sigma_X \omega
\end{align}
$$

thus

$$
\Phi_X(\omega) = \exp\big(j \omega^\intercal \mu_X - \frac{1}{2} \omega^\intercal \Sigma_X \omega\big)
$$

Another good thing about Gaussian: for $$X = (X_1, \dots, X_n)^\intercal \sim N$$, if $$\forall i, j, i \ne j, E(X_i X_j) = E(X_i) E(X_j)$$ (meaning they are uncorrelated), then we have $$\forall i, j, i \ne j$$, $$X_i, X_j$$ are independent.

This is due to for $$i\ne j, \Sigma_{ij} = E(X_i - EX_i)(X_j - E X_j) = E(X_i X_j) - E(X_i)E(X_j) = 0$$.
Thus $$\Sigma$$ is diagonal matrix, from its distribution we know they are independent (because joint-pdf equals the product of boundary pdfs).

To generate any Gaussian, we only need to go from $$X \sim N(0, I)$$, then $$\tilde{X} = \Sigma^{1/2} (X + \Sigma^{-1/2} \mu) \sim N(\mu, \Sigma)$$

## MidJourney Diffusion

A small example, $$X_k = \sqrt{1-\alpha_k} \cdot X_{k-1} + \sqrt{\alpha_k} \cdot \epsilon_k$$, where $$\epsilon_k$$ i.i.d., $$N(0, I)$$.

Reparametric Trick

$$
\beta_k = 1 - \alpha_k
$$

$$
\begin{align}
X_k &= \sqrt{\beta_k} \cdot X_{k-1} + \sqrt{1-\beta_k} \cdot \epsilon_k\\
&= \sqrt{\beta_k} (\sqrt{\beta_{k-1}} \cdot X_{k-1} + \sqrt{1 - \beta_{k-1}} \cdot \epsilon_{k-1}) + \sqrt{1-\beta_k} \cdot \epsilon_k\\
&= \sqrt{\beta_k \beta_{k-1}} \cdot X_{k-2} + \sqrt{\beta_k} \sqrt{1 - \beta_{k-1}} \epsilon_{k-1} + \sqrt{1- \beta_k} \epsilon_k\\
&= \sqrt{\beta_k \beta_{k-1}} \cdot X_{k-1} + N(0, \sqrt{1- \beta_{k} \beta_{k-1}} I)
\end{align}
$$

$$
X_{k} \sim N(0, \sqrt{1-\beta_k \beta_{k-1} \dots \beta_{1}} I)
$$
