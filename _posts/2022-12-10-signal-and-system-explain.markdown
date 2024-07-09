---
title:  "Signal And System Explain"
date:   2022-12-10 05:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

# Signal and System

**convolution is commutative: proof**

from

$$
\sum_{k=-\infty}^{\infty} x[k]h[n-k]
$$

let $$k=n-r$$

$$
\sum_{r=-\infty}^{\infty} x[n-r]h[r]
$$

**LTI system eigen function: proof**

$$
\begin{align}
y(t) &= \int_{-\infty}^{\infty} h(\tau) x(t-\tau) d\tau\\
&= \int_{-\infty}^{\infty} h(\tau) e^{s(t-\tau)} d\tau\\
&= e^{st} \int_{-\infty}^{\infty} h(\tau)e^{-s\tau} d\tau
\end{align}
$$

$$
\begin{align}
y[n] &= \sum_{k=-\infty}^{\infty} h[k]x[n-k]\\
&= \sum_{k=-\infty}^{\infty} h[k]z^{n-k}\\
&= z^n \sum_{k=-\infty}^{\infty} h[k]z^{-k}
\end{align}
$$

**Paeseval's theorem: proof**

$$
\begin{align}
&\sum_{k=-\infty}^{\infty} \vert a_k \vert^2\\
=& \sum_{k=-\infty}^{\infty} a_k a_k^*\\
=& \sum_{k=-\infty}^{\infty} a_k \dfrac{1}{T} \int_T x^*(t) e^{jk\omega_0 t} dt\\
=& \dfrac{1}{T} \sum_{k=-\infty}^{\infty} \int_T x^*(t) a_k e^{jk\omega_0 t} dt\\
=& \dfrac{1}{T} \int_T x^*(t) \sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t} dt\\
=& \dfrac{1}{T} \int_T x^*(t) x(t) dt
\end{align}
$$

$$
\begin{align}
&\sum_{k=0}^{N-1} \vert a_k \vert^2\\
=& \sum_{k=0}^{N-1} a_k a_k^*\\
=& \sum_{k=0}^{N-1} a_k \dfrac{1}{N} \sum_{n=0}^{N-1} x^*[n] e^{jk\omega_0 n}\\
=& \dfrac{1}{N} \sum_{n=0}^{N-1} x^*[n] \sum_{k=0}^{N-1} a_k e^{jk\omega_0 n}\\
=& \dfrac{1}{N} \sum_{n=0}^{N-1} x^*[n] x[n]
\end{align}
$$

book_xinhaoyuxianxingxitongfenxi

## Intro

## Signal

### Continuous-Time Signal and Discrete-Time Signal

### Periodic Signal and Non-Periodic Signal

### Real Signal and Complex Signal

- Deterministic signal, stochastic signal.
- Continuous-time signal, discrete-time signal.
- Periodic signal, non-periodic signal.
- Energy signal, power signal.
- Causal signal, anti-causal signal.

The total energy and average power of a signal $$f(t)$$ is

$$
\begin{align}
E &= \int_{-\infty}^{\infty} \vert f(t) \vert^2 dt\\
P &= \lim_{T \to \infty} \dfrac{1}{T} \int_{-T/2}^{T/2} \vert f(t) \vert^2 dt
\end{align}
$$

- Energy signal: $$E < \infty$$. Clearly it implies $$P = 0$$.
- Power signal: $$0 < P < \infty$$. Clearly it implies $$E = \infty$$.
- Causal signal: $$f(t) = 0 \quad \forall t < 0$$.
- Anti-causal signal: $$f(t) = 0 \quad \forall t \ge 0$$.

Step function

$$
u(t) = \begin{cases}
0, &\quad t < 0\\
1, &\quad t > 0
\end{cases}
$$

the value at $$t = 0$$ is not important, as long as we define $$u(0) < \infty$$.
Since in the theory of generalized function, it is always evaluated by integration.

Impulse function is defined by using generalized function.
For well behaved function $$\phi(t)$$, impulse function $$\delta(t)$$ is the function that satisfy

$$
\int_{-\infty}^{\infty} \delta(t)\phi(t) dt = \phi(0)
$$

e.g.,

$$
\begin{align}
\delta(t) &= \lim_{b\to\infty} b e^{-\pi (bt)^2}\\
\delta(t) &= \lim_{b\to\infty} \dfrac{\sin(bt)}{\pi t}
\end{align}
$$

- The derivitive of $$\delta(t)$$

using $$f(t) \delta'(t) = f(0) \delta'(t) - f'(0) \delta(t)$$, we have

$$
\int_{-\infty}^{\infty} f(t) \delta'(t) dt = -f'(0)
$$

and also

$$
\int_{-\infty}^{\infty} f(t) \delta^{(n)}(t) dt = (-1)^{n} f^{(n)}(0)
$$

another equation (can only be used in the integral)

$$
\begin{align}
\delta(at) &= \dfrac{1}{|a|}\delta(t)\\
\delta^{(n)}(at) &= \dfrac{1}{\vert a \vert} \dfrac{1}{a^n} \delta^{(n)}(t)
\end{align}
$$

- In summary
  - The definitions
    - &nbsp; $$\int_{-\infty}^{\infty} f(t) \delta^{(n)}(t) dt = (-1)^{n} f^{(n)}(0)$$
  - The formula can be used in anywhere (e.g., in the arguments for the derivitive definition)
    - &nbsp; $$f(t)\delta^{(n)}(t) = f(0) \delta^{(n)}(t)$$
  - The formula can only be used in the integral
    - &nbsp; $$ \delta^{(n)}(at) = \dfrac{1}{\vert a \vert} \dfrac{1}{a^n} \delta^{(n)}(t)  $$
    - &nbsp; $$f(t)\delta'(t) = f(0)\delta'(t) - f'(0)\delta(t)$$

- Exercises

$$
\begin{align}
\int_{-\infty}^{\infty} \dfrac{\sin(2t)}{t} \delta(t) dt &= \lim_{t \to 0} \dfrac{\sin(2t)}{t} = 2
\end{align}
$$

$$
\begin{align}
\int_{-\infty}^{\infty} (t^3 - 3t^2 + 5t - 1) \delta'(t-1)dt &= -g'(1) = -2
\end{align}
$$

$$
\int_{-\infty}^{\infty} (t^3+5) \delta(\dfrac{t}{2})dt = 2 \int_{-\infty}^{\infty} (t^3+5) \delta(t)dt = 10
$$

$$
\begin{align}
\int_{-\infty}^{t}(2-x) \delta'(x)dx = \int_{-\infty}^{t} [2 \delta'(x) - (-1)\delta(t)]dt = 2\delta(t) + u(t)
\end{align}
$$

- Discrete-time impulse and step function

$$
u[k] = \begin{cases}
1, \quad k \ge 0\\
0, \quad k < 0
\end{cases}
$$

$$
\sum_{k=-\infty}^{\infty} f[k] \delta[k] = f[0]
$$

Discrete-time difference

$$
\delta[k] = u[k] - u[k-1]
$$

Discrete-time summation

$$
u[k] = \sum_{i=-\infty}^{k} \delta[i]
$$

Decomposition

$$
u[k] = \sum_{j=0}^{\infty} \delta[k-j]
$$

- Signal reflect, move, and scale
  - give the waveform $$f(t)$$, $$f(-t)$$ is reflect at 0. $$(t \times -1)$$
  - give the waveform $$f(t+2)$$, $$f(-t+2)$$ is reflect at 0. $$(t \times -1)$$
  - give the waveform $$f(t)$$, $$f(t-3)$$ is move right to 3 units. $$(t - 3)$$
  - give the waveform $$f(t+2)$$, $$f(t-1)$$ is move right to 3 units. $$(t - 3)$$
  - give the waveform $$f(t)$$, $$f(3t)$$ is shrink 3 times at 0. $$(t \times 3)$$
  - give the waveform $$f(t+2)$$, $$f(3t+2)$$ is shrink 3 times at 0. $$(t \times 3)$$
  - give the waveform $$f(t)$$, $$f(0.2 t)$$ is expand 5 times at 0. $$(t \times 0.2)$$
  - give the waveform $$f(t+3)$$, $$f(0.2 t + 3)$$ is expand 5 times at 0. $$(t \times 0.2)$$
- Usually first move, then scale, then reflect.

- Do derivitive one the waveform, add the impulse function.

## Introduction to System

- Linear system

$$
T[a f_1(.) + b f_2 (.)] = a T[f_1(.)] + b T[f_2(.)]
$$

- Dynamic linear system
  - &nbsp; $$y(t) = y_{zi}(t) + y_{zs}(t)$$
  - The system are linear for the input and states respectively.

$$
y(.) = y_{zs}(.) + y_{zi}(.)
$$

$$
T[\{af_1(t) + b f_2(t)\}, \{0\}] = a T[\{f_1(.)\}, \{0\}] + b T[\{f_2(.)\}, \{0\}]
$$

$$
T[\{0\}, \{a x_1(0) + b x_2(0)\}] = a T[\{0\}, \{x_1(0)\}] + b T[\{0\}, \{x_2(0)\}]
$$

- Time varying or time invariant: only look zero state response.

$$
T[\{0\}, f(t-td)] = y_{zs}(t-t_d)
$$

- LTI system.
  - if $$f(t) \to y_{zs}(t)$$, then $$f'(t) \to y_{zs}'(t)$$
  - if $$f(t) \to y_{zs}(t)$$, then $$\int_{-\infty}^{t} f(x)dx \to \int_{-\infty}^{t} y_{zs}(x)dx$$
  - TODO: how to prove?

- Causal system and non-causal system.
  - It is defined for $$y_{zs}(t)$$

- Example:

For a causal LTI causal system with initial state $$x(0\_)$$, if $$x(0\_) = 1$$ and with a causal input $$f_1(t)$$, the full response is

$$
y_1(t) = [e^{-t} + \cos(\pi t)] u(t)
$$

if $$x(0\_) = 2$$ and input $$3f_1(t)$$, the full response is

$$
y_2(t) = [-2 e^{-t} + 3\cos(\pi t)] u(t)
$$

then for input $$f'_1(t) + 2 f_1(t-1)$$, find the zero state response.

- Solution: $$y_{zs}(t) = -3\delta(t) + [4e^{-t} - \pi \sin(\pi t)] u(t) + 2\{-4e^{-(t-1)} + \cos[\pi(t-1)]\} u(t-1)$$

# Continuous-Time Time-Domain Analysis

## Response of LTI System

### Differential Equations

The differential equation

$$
a_2 \dfrac{d^2 y(t)}{dt^2} + a_1 \dfrac{y(t)}{dt} + a_0 y(t) = f(t)
$$

with initial conditions
$$
y(0_+), \quad y'(0_+)
$$

we can determine the responses for the given $$f(t)$$ and initial conditions.

### Block Diagram of Differential Equations

Take the example of

$$
y''(t) + ay'(t) + by(t) = f(t)
$$


<img src="/assets/img/2022-12-09-signal-and-system-01/009.png" style="width:80%;height:80%;">

Another example

$$
y''(t) + 3y'(t) + 2y(t) = 4f'(t) + f(t)
$$

<img src="/assets/img/2022-12-09-signal-and-system-01/010.png" style="width:80%;height:80%;">


### Classic Solution of Differential Equations

If $$f(t)$$ has finite derivative up to $$f^{(m)}(t)$$, for differential equations

$$
\begin{align}
&y^{(n)}(t) + a_{n-1} y^{(n-1)}(t) + \dots + a_1 y^{(1)}(t) + a_0 y(t) \\
&= b_m f^{(m)}(t) + b_{m-1} f^{(m-1)}(t) + \dots + b_1 f^{(1)}(t) + b_0 f(t)
\end{align}
$$

and $$n$$ initial conditions

$$
y^{(n-1)}(0), y^{(n-2)}(0),\dots, y(0)
$$

The solution is composed of homogeneous solution and special solution

$$
y(t) = y_h(t) + y_p(t)
$$

where homogeneous solution is the complete solution of the homogeneous differential equation with all possible initial conditions

$$
y^{(n)}(t) + a_{n-1} y^{(n-1)}(t) + \dots + a_1 y^{(1)}(t) + a_0 y(t) = 0
$$

the corresponding eigen-function has $$n$$ roots

$$
F(\lambda) = \lambda^n + a_{n-1} \lambda^{n-1} + \dots + a_1 \lambda + a_0 = 0
$$

If the $$n$$ roots $$\lambda_1, \dots, \lambda_n$$ are not equal to each other

$$
y_h(t) = C_1 e^{\lambda_1 t} + C_2 e^{\lambda_2 t} + \dots + C_n e^{\lambda_n t}
$$

If there are $$e_i$$ same roots $$\lambda$$, the corresponding term is

$$
(C_0 + C_1 t + \dots + C_{e_i - 1} t^{e_i - 1}) e^{\lambda t}
$$

and the special solution is one arbitrary solution satisfy the original differential equation without worring about the initial condition.

TODO: finish the table for special solution.

Example:

$$
\begin{align}
& y''(t) + 5y'(t) + 6y(t) = f(t)\\
& f(t) = 2e^{-t}, t \ge 0\\
& y'(0) = -1, y(0) = 2
\end{align}
$$

### On Initial Conditions

### Zero Input Response

### Zero State Response

# Deprecated

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

### From Time-Domain to $$z$$-Domain

### From $$z$$-Domain to Time-Domain

## Discrete-Time Systems

$$
y[.] = a_0 x[.] + a_1 \cdot x_{delay,1}[.] + a_2 \cdot x_{delay,2}[.] + \dots + a_m \cdot x_{delay,m}[.] + b_1 \cdot y_{delay,1}[.] + b_2 \cdot y_{delay,2}[.] + \dots + b_r \cdot y_{delay,r}[.]
$$


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
