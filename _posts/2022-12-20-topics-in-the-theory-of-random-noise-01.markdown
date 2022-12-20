---
title:  "Topics in The Theory of Random Noise 01"
date:   2022-12-20 12:00:00 +0200
categories: math
tags: math
math: true
---

From [book_topics_in_the_theory_of_random_noise](https://archive.org/details/stratonovich-topics-in-the-theory-of-random-noise-vol-1)

# Chapter 1: Random Functions and Their Statistical Characteristics

## 1. Random Variables

The mean value of $$\xi$$ can be defined by

$$
\langle\xi\rangle_{\xi} = \lim_{n\to\infty} \dfrac{\xi_1 + \xi_2 + \dots + \xi_n}{n}
$$

$$
\langle\xi^2\rangle_{\xi} = \lim_{n\to\infty} \dfrac{\xi_1^2 + \xi_2^2 + \dots + \xi_n^2}{n}
$$

if we define function

$$
\theta(z) = \begin{cases}
1 & \text{ for } \quad z > 0,\\
0 & \text{ for } \quad z \le 0
\end{cases}
$$

<img src="/assets/img/2022-12-20-topics-in-the-theory-of-random-noise-01/001.png" style="width:50%;height:50%;">

Then we have *distribution function*

$$
P\{\xi < x\} = F_{\xi}(x) = \langle\theta(x-\xi)\rangle
$$

and the probability density function

$$
\begin{align}
w_\xi(x) &= \dfrac{d}{dx} F_\xi(x) = \dfrac{d}{dx}\langle\theta(x-\xi)\rangle = \langle\dfrac{d}{dx}\theta(x-\xi)\rangle = \langle\delta(x-\xi)\rangle
\end{align}
$$

this can be used to calculate cany $$\langle f(\xi)\rangle$$

$$
\begin{align}
\langle f(\xi)\rangle &= \langle \int_{-\infty}^{\infty} f(x)\delta(x-\xi)dx \rangle = \int_{-\infty}^{\infty}\langle f(x)\delta(x-\xi)\rangle dx\\
&= \int_{-\infty}^{\infty} f(x)\langle\delta(x-\xi)\rangle dx = \int_{-\infty}^{\infty} f(x)w_{\xi}(x)dx
\end{align}
$$

Next, we show how the probability density behaves under transformations of the original random variable $$\xi$$.
Let the new randon variable $$\eta$$ be defined by

$$
\eta = g(\xi)
$$

then

$$
\begin{align}
w_{\eta}(x) &= \langle\delta(x-\eta)\rangle = \langle\delta(x-g(\xi))\rangle\\
&= \int_{-\infty}^{\infty} \delta(x-g(x)) w_{\xi}(x)dx
\end{align}
$$
