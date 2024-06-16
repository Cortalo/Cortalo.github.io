---
title:  "Modern Digital Signal Processing"
date:   2024-06-12 05:00:00 +0200
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
Var(X) = E(X-EX)^2
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

P2, 0:50:00
