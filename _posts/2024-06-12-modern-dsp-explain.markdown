---
title:  "Modern Digital Signal Processing Explanation"
date:   2024-06-12 06:00:00 +0200
categories: math
tags: math
math: true
---

**P1**

[video lectures](https://www.bilibili.com/video/BV1ga4y157L5/)

Textbook:

- S.M.kay, fundamental of statistical signal processing vol i ii, this book is easy to understand.
- S. Haykin: adaptive filter theory, fifth edition.
- Petre Stoica and Randolph Moses: spectral analysis of signal
- Murphy, machine learning

probability is defined on the subsets of sample spaces

$$
P(A \cup B) = P(A) + P(B), A \cap B = \emptyset
$$

$$
\begin{align}
& \forall A_1, A_2, \dots, A_k \dots \subseteq \Omega, A_i \cap A_j = \emptyset, \forall i,j\\
& P(\bigcup\limits_{k=1}^{\infty} A_k) = \sum_{k=1}^{\infty} P(A_k), \text{(countable additivity)}
\end{align}
$$

$$
P(\bigcup\limits_{k=1}^{\infty} A_k) = \sum_{k=1}^{\infty} P(A_k) - \sum_{i < j}P(A_i \cap A_j) + \sum_{i<j<k} P(A_i \cap A_j \cap A_k) - \dots \text{(inclusive exclusive)}
$$

example for using inclusive exclusive: assuming n persons has n hats, now they randomly throw the hats and get one, what is the probability such that no one get the correct hat?

Let $$P(A_k)$$ be the probability that person $$k$$ get the correct hat, obviously

$$
P(A_k) = \dfrac{(n-1)!}{n!} = \dfrac{1}{n}
$$

the probability that no one get the correct hat

$$
P(\overline{A_1} \cap \overline{A_2} \cap \dots \cap \overline{A_n})
$$

using De Morgen's law

$$
P(\overline{A_1 \cup A_2 \cup \dots \cup A_n}) = 1 - P(A_1 \cup \dots \cup A_n)
$$

$$
P(A_1 \cup \dots \cup A_n) = \sum_{k=1}^{n} P(A_k) - \sum_{i<j}P(A_i \cap A_j) + \sum_{i<j<k}P(A_i \cap A_j \cap A_k) - \dots
$$

where

$$
\begin{align}
P(A_k) &= \dfrac{(n-1)!}{n!} = \dfrac{1}{n}\\
P(A_i \cap A_j) &= \dfrac{(n-2)!}{n!} = \dfrac{1}{n(n-1)}\\
P(A_i \cap A_j \cap A_k) &= \dfrac{(n-3)!}{n!} = \dfrac{1}{n(n-1)(n-2)}\\
& \vdots
\end{align}
$$

$$
\begin{align}
P(A_1 \cup \dots \cup A_n) &= n \cdot \dfrac{1}{n} - \binom{n}{2} \dfrac{1}{n(n-1)} + \binom{n}{3} \dfrac{1}{n(n-1)(n-2)} - \dots\\
&= 1 - \dfrac{1}{2!} + \dfrac{1}{3!} - \dots
\end{align}
$$

the probability is $$ 1 - P(A_1 \cup \dots \cup A_n )= \dfrac{1}{2!} - \dfrac{1}{3!} + \dfrac{1}{4!} - \dots$$

**independent**

$$
P(AB) = P(A) \cdot P(B)
$$


**conditional probability**

$$
P(B|A) = P(AB)/P(A)
$$

conditional probability is also a probability, defined on a new sample space, the original sample space is $$\Omega$$, the new sample space is $$A$$.
related name for conditional inclusing prior.

if $$A$$ and $$B$$ are independent, $$P(B\vert A) = P(B)$$, meaning knowing $$A$$ doesn't give information regarding $$B$$.


**total probability formula**

if $$A_i \cap A_j = \emptyset$$ and $$\bigcup\limits_{k=1}^n A_k = \Omega$$

$$
P(B) = P(B|A_1)P(A_1) + \dots + P(B|A_n)P(A_n)
$$

example: n person n hats, the first one will randomly pick one hat, then start from the second person, if his hat is still there, he will pick his own hat; otherwise he randomly pick one hat. For the last person, what is the probability that he pick his own hat?

Let the event $$A_n$$ be person $$n$$ pick his own hat, when there is in total $$n$$ person,let the events $$B_1, B_2, \dots, B_n$$ be the first person pick hat $$1, 2,\dots, n$$.
Using total probability formula

$$
P(A_n) = P(A_n \vert B_1)P(B_1) + \dots + P(A_n \vert B_n) P(B_n)
$$

$$
P(A_n \vert B_1) P(B_1) = 1 \cdot \dfrac{1}{n}
$$

$$
P(A_n \vert B_n) P(B_n) = 0 \cdot \dfrac{1}{n}
$$

for $$P(A_n \vert B_k)$$, we know that person $$2, \dots, k-1$$ pick their own hat, then person $$k$$ need to pick randomly from the remainly $$n-k+1$$ hats.
We can imagin hat $$1$$ is person $$k$$'s original hat, then

$$
P(A_n \vert B_k) = P(A_{n-k+1})
$$

$$
P(A_n) = 1 \cdot \dfrac{1}{n} + \left(\sum_{k=2}^{n-1} \dfrac{1}{n} P(A_{n-k+1})\right) + 0 \cdot \dfrac{1}{n}
$$

$$
P(A_1) = 1
$$

$$
P(A_2) = \dfrac{1}{2}
$$

$$
P(A_3) = \dfrac{1}{3} + \dfrac{1}{3} P(A_2) = \dfrac{1}{2}
$$

assumes $$P(A_2) = P(A_3) = \dots = P(A_{n-1}) = 1/2$$

$$
P(A_n) = \dfrac{1}{n} + \dfrac{n-2}{n} \cdot \dfrac{1}{2} = \dfrac{1}{2}
$$

**Bayesian**

$$
P(B \vert A) = \dfrac{P(A \vert B) P(B)}{P(A)} = \dfrac{P(A \vert B)P(B)}{\sum_{k} P(A \vert C_k) P(C_k)}
$$

example

The first bag has 4 black and 3 white balls, the second bag has 5 black and 2 white ball.
Now randomly choose 2 balls from first bag to second bag, then pick one ball from second bag, we found it is white ball.
Based on this condition what is the probability that the choosed 2 balls have same color?

Let event $$B$$ be the 2 balls have same color, let event $$A$$ be we found it is white.
Let event $$C_1, C_2, C_3$$ be the 2 balls are all white, all black and one white one black.

$$
P(B\vert A) = \dfrac{P(AB)}{P(A)} = \dfrac{P(AB\vert C_1) P(C_1) + P(AB \vert C_2) P(C_2) + P(AB \vert C_3) P(C_3)}{P(A\vert C_1)P(C_1) + P(A\vert C_2)P(C_2) + P(A \vert C_3) P(C_3)}
$$

**random variables** is a determinstic function $$X: \Omega \to \mathbb{R}$$.

**probability density function** and **culmilitive density function**

**Bernoulli distribution**

**Binomial distribution** $$P(x=k) = \binom{n}{k}p^k (1-p)^{n-k}$$

**Possion distribution** $$P(x=k) = \dfrac{\lambda^k}{k!}\exp(-\lambda)$$

possion distribution can be derived from binomial distribution, let $$n \to \infty, p \to 0$$ while $$np=\lambda$$

$$
\begin{align}
P(x=k) &= \dfrac{n!}{k!(n-k)!} \dfrac{\lambda^k}{n^k} \left(1 - \dfrac{\lambda}{n}\right)^{n-k}\\
&=\dfrac{\lambda^k}{k!} \cdot \dfrac{n!}{(n-k)! \cdot n^k} \cdot  \left(1 - \dfrac{\lambda}{n}\right)^n \cdot \left(1- \dfrac{\lambda}{n}\right)^{-k}\\
&= \dfrac{\lambda^k}{k!} \cdot \dfrac{n \cdot (n-1) \dots (n-k+1)}{n^k} \cdot \left(1 - \dfrac{\lambda}{n}\right)^n \cdot \left(1- \dfrac{\lambda}{n}\right)^{-k}\\
&= \dfrac{\lambda^k}{k!}\exp(-\lambda)
\end{align}
$$

here I use $$\lim_{n\to\infty} \left(1 + \dfrac{a}{n}\right)^n = \exp(a)$$

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

example

still $$N$$ person randomly choose $$N$$ hats, what is the expection number of the person pick their own hat?

$$
E(X_1 + \dots X_N) = N \cdot \dfrac{1}{N} = 1
$$

**variance**

$$
Var(X) = E(X-EX)^2 = E(X^2) - (E(X))^2
$$

**convex function**: convex function is like a bowl, for example $$g(x) = x^2$$

$$
g(\alpha x + (1-\alpha)y) \le \alpha g(x) + (1-\alpha)g(y)
$$

$$
g\left(\sum_{k=1}^{n} \alpha_k x_k\right) \le \sum_{k=1}^{n} \alpha_k g(x_k)\quad \text{ where } \quad \left(\alpha_k \ge 0, \sum_{k=1}^{n} \alpha_k = 1\right)
$$

then

$$
E\left(g(X)\right) \ge g\left(E(X)\right)
$$

to feel the correctness for the  equation above, note that convex function has another property, such that it has a supporting plane at any point of the function (P2, 0:43:00)

$$
g(x) \ge g(a) + L_a (x-a)
$$

then

$$
g(X) \ge g(a) + L_a (X-a)
$$

$$
E(g(X)) \ge g(a) + L_a \left(E\left(X\right)-a\right)
$$

since $$a$$ can be arbitary, let $$a = E(X)$$

$$
E(g(X)) \ge g(E(X))
$$

for example, $$E(X^2) \ge (E(X))^2$$, then it is easy to show, if we let $$g(X) = X^2$$

$$
Var(X) = E(X - EX)^2 = E(X^2) - (E(X))^2 \ge 0
$$

**approximation**

we define mean square distance between two random variable

$$
\left(E(X-Y)^2\right)^{1/2} = d(X,Y)
$$

if we want to find the best approximation in terms of a constant

$$
\min\limits_{a} E(X-a)^2
$$

$$
\dfrac{d}{da} E(X-a)^2 = 0
$$

$$
-2E(X-a) = 0
$$

$$
a=EX
$$

now can understand mean is the best approximation using an constant, and variance is the square distance.

$$
\min\limits_{g} E(X-g(Y))^2
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

now we can find $$ \min\limits_{g} E(X-g(Y))^2 $$ intuitively

$$
E(X-g(Y))^2 = E(E((X-g(Y))^2 \vert Y))
$$

we know

$$
E((X-g(Y))^2 \vert Y) \ge E((X - E(X \vert Y))^2 \vert Y)
$$

thus

$$
E(X-g(Y))^2 = E(E((X-g(Y))^2 \vert Y)) \ge E( E((X - E(X \vert Y))^2 \vert Y) ) = E( (X - E(X \vert Y))^2)
$$

thus the optimal $$g(Y) = E(X \vert Y)$$.

The above is an intuitive understanding, now we give the formal prove

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

we typicaly want to do **parametric** or **non-parametric** model, an example for **parametric** can be we know the data follows guassian distribution, and we want to find its mean and variance;
an example for non-parametric model is clustering.

We first look at parametric model.
We want to find a function $$\hat{\theta}(X_1, \dots, X_n)$$, such a function we may call it estimator, statistic or feature.

For such estimator, there are two school of thoughts: **frequencist** and **bayesian**.
We first look at frequencist.
It assume the actual $$\theta$$ is an unknown constant (not random).

$$
\min\limits_{\hat{\theta}} E(\hat{\theta}(X_1, \dots, X_n) - \theta)^2
$$

$$
\hat{\theta}_{opt} = E(\theta \vert X_1, \dots, X_n) = \theta
$$

$$
\begin{align}
& E(\hat{\theta} - \theta)^2 = E(\hat{theta} - E(\hat{\theta}) + E(\hat{\theta}) - \theta)^2\\
= & E(\hat{\theta} - E(\hat{\theta}))^2 + E(E(\hat{\theta}) - \theta)^2 + 2E((\hat{\theta} - E(\hat{\theta}))(E(\hat{\theta})-\theta))\\
= & E(\hat{\theta} - E(\hat{\theta}))^2 + E(E(\hat{\theta}) - \theta)^2
\end{align}
$$

The first term is variance, the second term is bias.

for example, a typical estimator for mean is

$$
\hat{\theta}(X_1, \dots, X_n) = \dfrac{1}{n} \sum_{k=1}^{n} X_k
$$

assume all $$E(X_k) = \theta$$

$$
E(\hat{\theta}) = \theta
$$

$$
\begin{align}
& Var(\hat{\theta}) = E(\dfrac{1}{n} \sum_{k=1}^{n} X_k - \theta)^2\\
= & \dfrac{1}{n^2} E(\sum_{k=1}^{n} (X_k - \theta))^2\\
= & \dfrac{1}{n^2} \left( \sum_{k=1}^{n} E(X_k - \theta)^2  \right) + \dfrac{1}{n^2} \sum_{i \ne j} E (X_i - \theta)(X_j - \theta)
\end{align}
$$

assume $$E (X_i - \theta)(X_j - \theta) = 0$$ when $$i \ne j$$

$$
Var(\hat{\theta}) = \dfrac{\sigma^2}{n}
$$

a typical estimator for variance is

$$
\hat{\theta} = \dfrac{1}{n-1} \sum_{k=1}^n (X_k - \overline{X})^2
$$

where

$$
\overline{X} = \dfrac{1}{n} \sum_{k=1}^{n} X_k
$$

we can check $$E(\hat{\theta})$$

$$
\begin{align}
& (n-1) E(\hat{\theta}) = E(\sum_{k=1}^{n} (X_k - \overline{X})^2)\\
= & \sum_{k=1}^n E(X_k^2 - 2 X_k \overline{X} + \overline{X}^2)\\
= & \sum_{k=1}^n E(X_k^2) - 2 E\left((\sum_{k=1}^n X_k) \overline{X}\right) + n E(\overline{X}^2)\\
= & \sum_{k=1}^n E(X_k^2) - 2n E(\overline{X}^2) + n E(\overline{X}^2)\\
= & \sum_{k=1}^n E(X_k^2) - n E(\overline{X}^2)
\end{align}
$$

$$
E(X_k^2) = \sigma^2 + \mu^2
$$

$$
E(\overline{X}^2) = \dfrac{\sigma^2}{n} + \mu^2
$$

$$
(n-1)E(\hat{\theta}) = n (\sigma^2 + \mu^2) - n (\dfrac{\sigma^2}{n} + \mu^2) = (n-1) \sigma^2
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

P3

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

**poisson**

$$
f(x_1, \dots, x_n, \lambda) = \lambda^{\sum_{k=1}^{n} x_k} \exp(-\lambda) \prod_{k=1}^{n} \dfrac{1}{(x_k)!}
$$

$$
s = \sum_{k=1}^{n} x_k
$$

**gaussian**

assume $$\sigma^2$$ is known, but $$\mu$$ is unknown

$$
f(x_1, \dots, x_n, \mu) =
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
\theta = \int_{-\infty}^{\infty} \hat{\theta(x)} f(x, \theta) dx
$$

$$
\begin{align}
1 &= \dfrac{\partial}{\partial \theta} \int_{-\infty}^{\infty} \hat{\theta}(x) f(x,\theta) dx\\
&= \int_{-\infty}^{\infty} \hat{\theta}(x) \dfrac{\partial}{\partial \theta} f(x,\theta) dx
\end{align}
$$

$$
1 = \int_{-\infty}^{\infty} f(x,\theta) dx
$$

$$
0 = \int_{-\infty}^{\infty} \dfrac{\partial}{\partial \theta} f(x,\theta) dx
$$

$$
0 = \int_{-\infty}^{\infty} \theta \dfrac{\partial}{\partial \theta} f(x,\theta) dx
$$

$$
\begin{align}
1 &= \int_{-\infty}^{\infty} (\hat{\theta}(x) - \theta) \dfrac{\partial}{\partial \theta} f(x,\theta) dx\\
&= \int_{-\infty}^{\infty} (\hat{\theta}(x) - \theta) \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right) f(x,\theta) dx
\end{align}
$$

we want to use Cauchy-Schwarz inequality

$$
\left( \int f(x) g(x) dx \right)^2 \le \int f(x)^2 dx \int g(x)^2 dx
$$


$$
\begin{align}
1^2 &= \left(\int_{-\infty}^{\infty} (\hat{\theta}(x) - \theta) \sqrt{f(x,\theta)} \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)  \sqrt{f(x,\theta)} dx\right)^2\\
& \le \int_{-\infty}^{\infty} (\hat{\theta}(x) - \theta)^2 f(x,\theta) dx \int_{-\infty}^{\infty} \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2 f(x,\theta) dx\\
&= E(\hat{\theta}(x) - \theta)^2 \cdot E \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2
\end{align}
$$

$$
E(\hat{\theta}(x) - \theta)^2 \ge 1 / E \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2
$$

where $$ E \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2 $$ is called Fisher information.

It can be proved that (P3, 1:57:00)

$$
E \left(\dfrac{\partial}{\partial \theta} \ln f(x,\theta)\right)^2 = -E\left( \dfrac{\partial^2}{\partial \theta^2} \ln f(x,\theta) \right)
$$

the cauchy is equal if and only if

$$
\dfrac{\partial}{\partial \theta} \ln f(x,\theta) = k(\theta)(\hat{\theta}(x)-\theta)
$$

**notese until P3 somewhere**

video until P6 0:00:00
