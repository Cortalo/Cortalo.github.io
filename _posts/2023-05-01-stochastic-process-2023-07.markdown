---
title:  "Stochastic Process 2023 07"
date:   2023-05-01 07:00:00 +0200
categories: math
tags: math
math: true
---

From [Hao Zhang's 2023 Lecture 07](https://v.ucas.ac.cn/course/CourseIndex.do?menuCode=2&courseid=456bd6a25b7046d4a0482cddf1a285bb)

# Gaussian Processes

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

34:00
