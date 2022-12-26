---
title:  "Signal And System 01"
date:   2022-12-09 05:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

## Discrete-Time Signals

The definition of discrete-time signal is a function from non-negative integer set to real number set.

$$
f: \mathbb{Z}_{\ge 0} \to R
$$

### Basic Signals


- the discrete-time impulse function

$$
\delta[k] = \begin{cases}
1, & \text{$k = 0$} \\
0, & \text{$k > 0$}
\end{cases}
$$

- the discrete-time unit step function

$$
u[k] = 1
$$

- the discrete-time ramp signal

$$
r[k] = k
$$

<!-- - for all the purpose the signal we will used in circuit design, the signal we considered is always causal (thus also right-sided), meaning $$f[k] = 0, \forall k < 0$$. -->
<!-- Then if we assume all the signal mentioned is causal, we don't need to say $$f[k]=0, \forall k < 0$$ every time. -->
<!-- For example, we may simply say $$u[k] = 1$$ and $$r[k]=k$$. -->

### The $$z$$-transform

Instead of describing the value at each point, there is another way to describe a signal by only using one single equation, that is $$Z$$-transform.

$$
F(z) = \sum_{k=0}^{\infty} f[k] z^{-k}
$$

It can be proved its ROC is

$$
|z| > r_1 = \limsup_{k \to \infty} |f[k]|^{1/k}
$$

Please note the term ROC doesn't literally match to "region of convergence", since we always neglect $$r_1$$, whether $$F(z)$$ really converge at $$r_1$$ or not.


| Signal $$x[.]\quad \mathbb{Z}_{\ge 0} \to \mathrm{R}$$ | $$z$$-Transform                  | ROC                                                             | Notes                                                  |
|--------------------------------------------------------|----------------------------------|-----------------------------------------------------------------|--------------------------------------------------------|
| $$\delta[.]$$                                          | $$1$$                            | $$\vert z \vert > 0$$                                           |                                                        |
| $$u[n] = 1$$                                           | $$\dfrac{1}{1-z^{-1}}$$          | $$\vert z\vert>1$$                                              |                                                        |
| $$r[n] = n$$                                           | $$\dfrac{z^{-1}}{(1-z^{-1})^2}$$ | $$\vert z \vert > 1$$                                           |                                                        |
| $$x[n] = a^n$$                                         | $$\dfrac{z}{z-a}$$               | $$\vert z \vert > \vert a \vert$$                               |                                                        |
| $$x[n] = f[n]+g[n]$$                                   | $$F(z)+G(z)$$                    | $$\mathrm{ROC} \supseteq \mathrm{ROC}(f) \cap \mathrm{ROC}(g)$$ | $$\mathrm{ROC}(f) \cap \mathrm{ROC}(g) \ne \emptyset$$ |
| $$x[n] = af[n], \quad a \ne 0$$                        | $$aF(z)$$                        | $$\mathrm{ROC} = \mathrm{ROC}(f)$$                              | $$\mathrm{ROC}(f) \ne \emptyset $$                     |
| $$x[n] = f_{delay,m}[n]$$                              | $$z^{-m}F(z)$$                   | $$\mathrm{ROC} = \mathrm{ROC}(f)$$                              | $$\mathrm{ROC}(f) \ne \emptyset$$                      |
| $$x[n] = (f*g)[n]$$                                    | $$F(z)G(z)$$                     | $$\mathrm{ROC} \supseteq \mathrm{ROC}(f) \cap \mathrm{ROC}(g)$$ | $$\mathrm{ROC}(f) \cap \mathrm{ROC}(g) \ne \emptyset$$ |
| $$x[n] = f[n] - f_{delay,1}[n]$$                       | $$(1-z^{-1})F(z)$$               | $$\mathrm{ROC} \supseteq \mathrm{ROC}(f)$$                      | Difference                                             |


- Almost all the discrete-time signals in practice will have $$z$$-Transform with some $$\mathrm{ROC}\ne\emptyset$$. Although signals like $$x[n] = n^n$$ doesn't have $$z$$-Transform, perhaps they never appear in real practice.


- Time delayed by $$m$$ with initial rest is defined as

$$
f_{delay,m}[n] = \begin{cases}
0, & \text{$n < m$} \\
f[n-m], & \text{$n \ge m$}
\end{cases}
$$


- Convolution is defined as

$$
(f * g)[n] = \sum_{k=0}^{n} f[k]g[n-k] = \sum_{k=0}^{n}f[n-k]g[k]
$$



below is how to visualize the convolution for $$F(z) = 1 + z^{-1} + z^{-2}$$ and $$G(z) = 1 + z^{-1} + z^{-2} + z^{-3}$$.

<img src="/assets/img/2022-12-09-signal-and-system-01/008.png" style="width:80%;height:80%;">




#### Example 01

$$
x[k] = \begin{cases}
1, & \text{$k = 0, 1, 2$} \\
0, & \text{otherwise}
\end{cases}
$$

$$
X(z) = 1 + z^{-1} + z^{-2}, \quad \mathrm{ROC} = \{z \ne 0\}
$$

#### Example 02

$$
x[k] = a^n + 1
$$

$$
X(z) = \dfrac{1}{1-z^{-1}} + \dfrac{z}{z-a}, \quad \mathrm{ROC} = \{|z| > \mathrm{max}(1, |a|)\}
$$

#### Example 03

$$
\begin{align}
u_{delay,1}[n] &= \begin{cases}
0, & \text{$k = 0$} \\
1, & \text{$k > 0$}
\end{cases}\\
U_{delay,1}(z) &= \dfrac{z^{-1}}{1-z^{-1}}, \quad \mathrm{ROC} = \{|z| > 1\}
\end{align}
$$

#### Example 04

calculate the difference of $$u[.]$$

$$
\begin{align}
u[.] - u_{delay,1}[.] &= \delta[.]\\
(1-z^{-1}) \cdot \dfrac{1}{1-z^{-1}} &= 1, \quad \mathrm{ROC} = \{|z| > 0\}
\end{align}
$$

#### Theorem 01

Let $$f[.]$$ and $$g[.]$$ be discrete-time signals with

$$
\mathrm{ROC}(f) \cap \mathrm{ROC}(g) \ne \emptyset
$$

If $$F(z)=G(z)$$ for $$z \in \mathrm{ROC}(f)\cap\mathrm{ROC}(g)$$, then $$f[k] = g[k]$$ for all $$k\in\mathbb{Z}$$

- It implies, for an unkown signal $$f[.]$$, if we know its $$F(z)$$ expression and its $$\mathrm{ROC}(f)$$ is non empty, then in principle we completely know the signal.
- So, we have a two directional table!

#### Example 05

Calculate the $$z$$-Transform of $$x[n]=n+1$$, without calculate explicitly.

We know $$x[.]$$ must have $$X(z)$$ in $$\mathrm{ROC}(x)\ne\emptyset$$. $$\quad \leftarrow \quad $$ ROC $$\limsup$$ rule.

$$x_{delay,1}[.]$$ have $$z$$-Transform $$z^{-1}X(z)$$ in $$\mathrm{ROC}(x)$$. $$\quad \leftarrow \quad $$ $$z$$-Transform of time delay.

$$x_{delay,1}[.] = r[.]$$, which has $$z$$-Transform $$\dfrac{z^{-1}}{(1-z^{-1})^2}$$ with $$\mathrm{ROC} = \{\vert z\vert > 1\}$$. $$\quad \leftarrow \quad $$ table

So, $$X(z) = \dfrac{1}{(1-z^{-1})^2}$$ with $$\mathrm{ROC}(x) = \{\vert z \vert > 1\}$$.


#### Example 06

Calculate the signal $$(u*u)[.]$$.

Let $$g[.] = (u*u)[.]$$, then $$G(z) = \dfrac{1}{(1-z^{-1})^2}$$ for $$\mathrm{ROC}(g)\supseteq\{\vert z \vert > 1\}$$ $$\quad \leftarrow \quad$$ convolution.

Then $$(u*u)[n]=g[n]=n+1 \quad \leftarrow \quad $$ table

#### Example 07 (Summation)

define $$x_{sum}[.]$$ with

$$
x_{sum}[n] = \sum_{k=0}^{n} x[k]
$$

Then if exists $$X(z)$$ with $$\mathrm{ROC}(x)\ne\emptyset$$ and $$X_{sum}(z)$$ with $$\mathrm{ROC}(x_{sum})\ne\emptyset$$, then

$$
\begin{align}
X_{sum}(z) &= \dfrac{X(z)}{1-z^{-1}} \quad \text{ with } \mathrm{ROC}(x_{sum})\\
\mathrm{ROC}(x_{sum}) &\subseteq \mathrm{ROC}(x)
\end{align}
$$

### LUT Exercises

TODO

## NOT

## Discrete-Time LTI Systems

A system will transform a input signal $$x_{in}[.]$$ to an output signal $$x_{out}[.]$$

$$
x_{out}[.] = H(z)\{x_{in}[.]\}
$$

<img src="/assets/img/2022-12-09-signal-and-system-01/006.png" style="width:50%;height:50%;">

### Basic Systems and Block Diagram


- Amplify or attennuation or identity.

$$
x_{out}[.] = A \cdot x_{in}[.]
$$


<img src="/assets/img/2022-12-09-signal-and-system-01/005.png" style="width:50%;height:50%;">


- Delayed by $$m$$

$$
x_{out}[.] = x_{in}[.-m]
$$

<img src="/assets/img/2022-12-09-signal-and-system-01/007.png" style="width:50%;height:50%;">

- Superposition

$$
x_{out}[.] = H_1(x)\{x_{in}[.]\} + H_2(x)\{x_{in}[.]\}
$$

- Cascade

- Feedback


[link](https://www.youtube.com/watch?v=Ih4s5IFphCw&list=PLUl4u3cNGP61kdPAOC7CzFjJZ8f1eMUxs&index=2&t=579s)



## Discrete-Time Systems

$$y[n] = x[n] - x[n-1]$$ is an example of difference equation.


[this drawing](https://docs.google.com/document/d/1SrHqHcCfa3nMkwBVI772M_HThfVn4lfJ2Ahsqpm3ok4/edit?usp=sharing) explains how to reflect $$x[n-1]$$ is delayed $$x[x]$$.

Knowing that $$x[n-1]$$ is the delayed $$x[n]$$, the difference equation can also be represented by a block diagram.


![001](/assets/img/2022-12-09-signal-and-system-01/001.png)

Let $$x[n]$$ equal the "unit sample" signal $$\delta[n]$$ (the most simple non-trivial signal you can imagine!)


![003](/assets/img/2022-12-09-signal-and-system-01/003.png)

To be more precise, we need to mention the systen start "at rest", meaning all the output at the delay start at 0.
Then you can completely compute the output $$y[n]$$ for any input $$x[n]$$, without any ambigious.

![004](/assets/img/2022-12-09-signal-and-system-01/004.png)

Is there any differences between the difference equation and block diagram?

- operators in the block diagram are more easier to be understood as an manipulation of the whole signal, instead of just single samples.

We can denote the delay operator as $$z^{-1}$$.
[This drawing](https://docs.google.com/document/d/1rzX3g86aLXqFctSlanvA9a-z2Nf7mia__FRLvy35ovM/edit?usp=sharing) shows how the $$z^{-1}$$ signal is applied to the unit sample signal.
The the block diagram can be denoted by

$$
1 - z^{-1}
$$
