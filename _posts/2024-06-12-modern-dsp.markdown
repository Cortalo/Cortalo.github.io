---
title:  "Modern Digital Signal Processing"
date:   2024-06-12 05:00:00 +0200
categories: math
tags: math
math: true
---

**P1**

**independent**

$$
P(AB) = P(A) \cdot P(B)
$$


**conditional probability**

$$
P(B|A) = P(AB)/P(A)
$$


**total probability formula**

if $$A_i \cap A_j = \emptyset$$ and $$\bigcup\limits_{k=1}^n A_k = \Omega$$

$$
P(B) = P(B|A_1)P(A_1) + \dots + P(B|A_n)P(A_n)
$$


**Bayesian**

$$
P(B \vert A) = \dfrac{P(A \vert B) P(B)}{P(A)} = \dfrac{P(A \vert B)P(B)}{\sum_{k} P(A \vert C_k) P(C_k)}
$$


**Bernoulli distribution**

**Binomial distribution** $$P(x=k) = \binom{n}{k}p^k (1-p)^{n-k}$$

**Possion distribution** $$P(x=k) = \dfrac{\lambda^k}{k!}\exp(-\lambda)$$


**uniform distribution**: $$f(x) = \dfrac{1}{b-a}I_{[a,b]}(x)$$

**exponetional distribution**: $$f(x) = \lambda \exp(-\lambda x)I_{[0,\infty)}(x)$$

**Gaussian distribution**: $$f(x) = \dfrac{1}{\sqrt{2\pi\sigma^2}} \exp(-\dfrac{(x-\mu)^2}{2\sigma^2})$$

**P2**

**expectation (mean)**

$$
E(X) = \int_{-\infty}^{\infty} x f(x) dx
$$

**expectation is linear**

$$
E\left(\sum_{k=1}^{n} X_k\right) = \sum_{k=1}^{n} E(X_k)
$$

**variance**

$$
Var(X) = E(X-EX)^2 = E(X^2) - (E(X))^2
$$


**approximation**

$$
\min\limits_{a} E(X-a)^2 = EX
$$

$$
\min\limits_{g} E(X-g(Y))^2 = E(X \vert Y)
$$

to find the result above, we need **conditional expection**

$$
E(X \vert Y)
$$

conditional expection has several important properties.

1. &nbsp; $$E(X \vert Y)$$ is a random variable.
2. &nbsp; $$E\left(\sum\limits_{k=1}^{n} X_k \vert Y\right) = \sum\limits_{k=1}^{n} E(X_k \vert Y)$$
3. &nbsp; $$E(E(X\vert Y)) = E(X)$$
4. &nbsp; $$E(X h(Y) \vert Y) = h(Y) E(X \vert Y)$$

now we give the formal prove

$$
\begin{align}
 & E(X-g(Y))^2 = E(X - E(X \vert Y) + E(X \vert Y) - g(Y))^2\\
= & E(X-E(X \vert Y))^2 + E(E(X \vert Y) - g(Y))^2 + 2 E((X - E(X \vert Y))(E(X \vert Y) - g(Y)))
\end{align}
$$

we only need to show the last term equals zero.

$$
\begin{align}
& E((X - E(X \vert Y))(E(X \vert Y) - g(Y)))\\
= & E( E(  (X - E(X \vert Y))(E(X \vert Y) - g(Y))\vert Y) ) = 0
\end{align}
$$



**conditional variance**

$$
Var(X \vert Y) = E\left( \left( X - E(X \vert Y) \right)^2 \vert Y \right)
$$

we can show

$$
Var(X) = Var( E (X \vert Y)) + E( Var(X \vert Y))
$$

$$
\begin{align}
& E(X - EX)^2 = E(X - E(X \vert Y) + E(X \vert Y) - EX)^2\\
= & E(X - E(X \vert Y))^2 + E(E(X \vert Y) - EX)^2 + 2 E \left( (X-E(X \vert Y))(E(X \vert Y) - EX) \right)
\end{align}
$$

we can show the last term is zero

$$
E \left( (X-E(X \vert Y))(E(X \vert Y) - EX) \right) = E\left( E \left( (X-E(X \vert Y))(E(X \vert Y) - EX) \vert Y \right) \right) = 0
$$

the first term

$$
E(X - E(X \vert Y))^2 = E\left( E\left( (X - E(X \vert Y))^2 \vert Y \right) \right) = E(Var(X \vert Y))
$$

the second term

$$
E(E(X \vert Y) - EX)^2 = E( (E(X \vert Y) - E(E(X \vert Y)) )^2 ) = Var(E(X \vert Y))
$$

**P3**

**Mean Square Error (MSE)**

$$
MSE(\hat{\theta}) = E(\hat{\theta} - \theta)^2
$$

**unbias estimator**

$$
E(\hat{\theta}) = \theta
$$

then

$$
MSE(\hat{\theta}) = Var(\hat{\theta})
$$

**sufficiency**

$$
f(x,\theta \vert s = t) \text{ is independent of } \theta
$$

for example, $$X_1, \dots X_n$$ iid ber(p), each $$X$$ is either 0 or 1.

$$
f(x_1, \dots, x_n) = p^{\sum_{k=1}^n x_k} (1-p)^{n - \sum_{k=1}^n x_k}
$$

let $$s = \sum_{k=1}^n x_k$$

$$
\begin{align}
& P(x_1, \dots, x_n \vert s = t)\\
= & P(x_1, \dots, x_n, s = t) / P(s=t)\\
= & p^t (1-p)^{n-t} / \binom{n}{t} p^t (1-p)^{n-t}\\
= & 1 / \binom{n}{t}
\end{align}
$$

**Naymen Facterization (without proof)**

$$
s \text{ is sufficient} \quad \iff \quad f(x,\theta) = g(s(x),\theta)h(x)
$$


**Rao Blackwell Procedure**

assume $$\hat{\theta}$$ is unbias estimator, then if $$s$$ is sufficient

$$
E(\hat{\theta} \vert s)
$$

is also an estimator, it is also unbias, and its MSE is smaller than $$MSE(\hat{\theta})$$, to prove it, first it is an estimator,
we didn't prove it here, but $$s$$ is sufficient will make sure $$E(\hat{\theta} \vert s)$$ is not a function of $$\theta$$ (without proof).

Then it is unbias

$$
E(E(\hat{\theta} \vert s )) = E(\hat{\theta}) = \theta
$$

then MSE is smaller

$$
Var(\hat{\theta}) = Var(E(\hat{\theta} \vert s)) + E(Var(\hat{\theta} \vert s))
$$

for example, $$X_1, \dots, X_n$$ iid $$N(\mu, \sigma^2)$$, $$\sigma^2$$ is known, $$s = \sum_{k=1}^{n} X_k$$, assume $$\hat{\theta} = X_1$$

$$
E(X_1 \vert \sum_{k=1}^{n} X_k) \text{ is the new estimator}
$$

from symmetry

$$
E(X_j \vert \sum_{k=1}^{n} X_k) = E(X_i \vert \sum_{k=1}^{n} X_k)
$$

$$
n \cdot E(X_1 \vert \sum_{k=1}^{n} X_k) = E( \sum_{k=1}^{n} X_k \vert \sum_{k=1}^{n} X_k ) = \sum_{k=1}^{n} X_k
$$

$$
E(X_j \vert \sum_{k=1}^{n} X_k) = \dfrac{\sum_{k=1}^{n} X_k}{n}
$$

it is clear the MSE get smaller.

**completeness**

Say $$T$$ is a statistic, it is said to be complete, meaning for every function $$g$$, if $$E(g(T)) = 0$$ then $$g(T) = 0$$.

**Lehmam Scheffe theorem**

if $$T$$ is sufficient and complete, and $$E(h(T)) = \theta$$, then $$h(T)$$ is minimum variance unbias estimator

for any unbias estimator $$\hat{\theta}$$, we know $$E(\hat{\theta} \vert T)$$ has smaller or equal MSE.

$$
E(h(T) - E(\hat{\theta} \vert T)) = \theta - \theta = 0
$$

so $$h(T) = E(\hat{\theta} \vert T)$$, so $$h(T)$$ is better or equal to any unbias estimator.

**Craner Rao Lower Bound**

for any unbias estimaor $$\hat{\theta}$$

$$
MSE(\hat{\theta}) \ge 1/I(\theta)
$$

where $$I(\theta)$$ is fisher information

$$
1/I(\theta) = E \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2 = -E\left( \dfrac{\partial^2}{\partial \theta^2} \ln f(x,\theta) \right)
$$

**P4**

one dimenitonal $$X$$ one dimentional $$Y$$

$$
\min_{\alpha} E(Y-\alpha X)^2 = (EX^2)^{-1} E(XY)
$$

multi dimention $$X$$ and one dimention $$Y$$

$$
\begin{align}
& Y \in \mathbb{R}, \quad X \in \mathbb{R}^n, \quad \alpha \in \mathbb{R}^n\\
& \min_{\alpha} E(Y - \alpha^{\intercal}X) = (E(X X^{\intercal}))^{-1} E(XY)
\end{align}
$$

continuous $$X$$ and one dimention $$Y$$

$$
\begin{align}
& \min_{h} E\left(Y(t) - \int_{-\infty}^{\infty}h(t-\tau) X(\tau) d\tau\right)^2\\
& H_{opt}(\omega) = \left( S_X(\omega) \right)^{-1} S_{XY}(\omega)
\end{align}
$$

**P5**

the above

$$
\begin{align}
& \min_{h} E\left(Y(t) - \int_{-\infty}^{\infty}h(t-\tau) X(\tau) d\tau\right)^2\\
& H_{opt}(\omega) = \left( S_X(\omega) \right)^{-1} S_{XY}(\omega)
\end{align}
$$

cannot gaurantee causal $$h$$.
