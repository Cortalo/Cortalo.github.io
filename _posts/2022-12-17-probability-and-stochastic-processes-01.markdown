---
title:  "Probability and Stochastic Processes"
date:   2022-12-17 05:00:00 +0200
categories: math
tags: probability
math: true
---

# Stochastic Processes

{% include embed/youtube.html id='WzFS3g0PM_M' %}

- A random variable maps the output of a random experiment, $\zeta$, to a real number.

- A stochastic process maps the output of a random experiment, $\zeta$, to a time domain waveform.

- Examples of stochastic processes.

  - &nbsp; $$X(t) = \cos(\omega_o t + \Phi)$$ where $$\Phi \sim U(-\pi,\pi)$$.

  - &nbsp; $$X(t) = e^{-Yt}$$ where $$Y \sim U(0,b)$$ and $$t \ge 0$$.

- First Order Moments.

  - &nbsp; $$E\{X(t)\} = E\{e^{-Yt}\} = \int_{0}^b e^{-yt} \dfrac{1}{b} dy = \dfrac{1}{bt}(1-e^{-bt})$$

  - &nbsp; $$E\{X(t)\} = E\{\cos(\omega_o t + \Phi)\} = \int_{-\pi}^{\pi} \cos(\omega_o t + \phi) \dfrac{1}{2\pi} d\phi = 0$$

- Autocorrelation (Second order moments): $$ R(t_1, t_2) = E\{X(t_1) X(t_2)\} $$

$$
\begin{align}
R(t_1, t_2) &= E\{X(t_1)X(t_2)\}\\
&= E\{\cos(\omega t_1 + \Phi) \cos(\omega t_2 + \Phi)\}\\
&= \dfrac{1}{2} E\{\cos[\omega(t_1 - t_2)]\} + \dfrac{1}{2} E\{\cos[\omega(t_1 + t_2) + 2\Phi]\}\\
&= \dfrac{1}{2}\cos[\omega(t_1 - t_2)]
\end{align}
$$

$$
\begin{align}
R(t_1, t_2) &= E\{X(t_1) X(t_2)\}\\
&= E\{e^{-Y(t_1 + t_2)}\}\\
&= \dfrac{1}{b(t_1+t_2)}\big[1-e^{-b(t_1 + t_2)}\big]
\end{align}
$$

- Auto-covariance: $$C(t_1, t_2) = R(t_1, t_2) - \mu(t_1)\mu(t_2)$$

- Correlation coefficient: $$r(t_1, t_2) = \dfrac{C(t_1,t_2)}{\sigma(t_1)\sigma(t_2)}$$

# Stationarity and Ergodicity

{% include embed/youtube.html id='fF7IZ-lIt48' %}

- A process is strict sense stationary (SSS) if its joint PDF and CDF are independent of a shift in the time axis.

$$
f(x_1,\dots,x_n;t_1,\dots,t_n) = f(x_1,\dots,x_n;t_1+c,\dots,t_n+c)
$$

Then obviously $$E\{X(t)\} = \mu, R(t_1, t_2) = R(t_2 - t_1) = R(\tau)$$

- A process is weak sense stationary (WSS) if

$$
E\{X(t)\} = \mu, \quad R(t_1,t_2) = R(t_2 - t_1)
$$

## White Process

- A white process means: $$C(t_1,t_2) = 0$$ for $$t_1 \ne t_2$$.

- A stricly white process means $$C(t_1, t_2) = q(t_1) \delta(t_2 - t_1)$$

## Gaussian Processes

$$
f_{\mathbf{X}}(\mathbf{x}) = \dfrac{1}{\sqrt{(2\pi)^{N/2} \text{det}(\mathbf{C}_{\mathbf{X}})}} \cdot \exp [-\dfrac{1}{2}(\mathbf{x}-\mu_{X})^{\text{T}} \mathbf{C_X}^{-1} (\mathbf{x}-\mu_X) ]
$$

## Ergodicity in the Mean

Ergodicity in the mean means

$$
E\{X(t)\} = \mu_X, \quad \mu_X = \lim_{T\to\infty} \dfrac{1}{2T}\int_{-T}^{T} X(t) dt
$$

- The ensemble average has to be a constant that doesn't dependent on time.

- Then it coincides with the time average.

## Slutsky's Theorem

- If $$E\{X(t)\} = \mu_X$$ is a constant.

For finite $$T$$, the average of one stochastic process relization is a random waveform

$$
\mu_{X,T} = \dfrac{1}{2T} \int_{-T}^{T} X(t)dt
$$

Mean of the random variable

$$
E\{\mu_{X,T}\} = \dfrac{1}{2T} \int_{-T}^{T} E\{X(t)\} dt = \mu_{X}
$$

Variance of the random varibla

$$
\begin{align}
\sigma_{\mu_{X,T}}^2 &= E\{(\mu_{X,T} - \mu_X)^2\}\\
&= E\bigg\{ \Big( \dfrac{1}{2T} \int_{-T}^{T} X(\alpha)d\alpha -\mu_X \Big) \Big( \dfrac{1}{2T} \int_{-T}^{T} X(\beta)d \beta -\mu_X \Big)\bigg\}\\
&= \dfrac{1}{4T^2} \int_{-T}^{T} \int_{-T}^{T} E\{[X(\alpha)-\mu_X][X(\beta)-\mu_X]\} d\alpha d\beta\\
&= \dfrac{1}{4T^2} \int_{-T}^{T} C_X(\alpha,\beta) d\alpha d\beta
\end{align}
$$

Our stochastic process if ergodic in the mean if

$$
\lim_{T \to \infty} \dfrac{1}{4T^2} \int_{-T}^{T} \int_{-T}^{T} C_X(t_1, t_2) d t_1 d t_2 = 0
$$

If the process is WSS, then it is ergodic in the mean if and only if

$$
\lim_{T \to \infty} \dfrac{1}{2T} \int_{-T}^{T} C_X(\tau) d\tau = 0
$$

The proof can be get by google "Slutsky's Theorem ergodicity" or [this link](http://shannon.cm.nctu.edu.tw/rp/random12s07.pdf).

### Example: Ergodicity in the mean

Consider a sinusoid with random phase uniformy distributed between $$\pi$$ and $$-\pi$$, $$X(t) = \cos(\omega t + \Phi)$$.
Then $$C(\tau) = \dfrac{1}{2}\cos(\omega \tau)$$.

$$
\lim_{T\to\infty} \dfrac{1}{2T} \int_{-T}^{T} C(\tau) d\tau = 0
$$

## Egrodicity of the Covariance

The covariance time average

$$
C_{X,T}(\tau) = \dfrac{1}{2T} \int_{-T}^{T} X(t)X(t+\tau)d t - \mu_X^2
$$

# Spectrum of a Random Signal

{% include embed/youtube.html id='w1XewfP956Q' %}

# Deprecated

[Youtube Lecture 2](https://www.youtube.com/watch?v=O3i_61SCgaM&list=PL7sWxFnBVJLUbrCHertPLEqqCyLVnG-tN&index=2)

- Partition: A partition of a set, $$S$$, is a finite series of mutually exclusive subsets that completely define $$S$$ such that

$$
S = A_1 + A_2 + \dots + A_N
$$

- The Axioms of Probability

$$
\begin{align}
P(A) &\ge 0\\
P(S) &= 1\\
\text{If } AB &= \emptyset, \text{ then } P(A \cup B) = P(A) + P(B)
\end{align}
$$

- Conditional Probability

$$
P(A|M) = \dfrac{P(AM)}{P(M)}
$$

- Example: IC Testing Proposal

Let $$G_1$$ and $$G_2$$ represent chips 1 and 2 being good, respectively.

$$
\begin{align}
P(\{\overline{G_1} \,\overline{G_2}\}) &= 0.01 \quad P(\{G_1 \overline{G_2}\}) = 0.01\\
P(\{\overline{G_1} G_2\}) &= 0.01 \quad P(\{G_1 G_2\}) = 0.97
\end{align}
$$

To calculate $$P(\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \vert \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\})$$

$$
\begin{align}
\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \cap \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\} &= \{\overline{G_1}\,\overline{G_2}\}\\
P(\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \vert \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\}) &= \dfrac{0.01}{0.02} = 0.5
\end{align}
$$

- Total Probability Theorem

If $$A_1, A_2, \dots, A_N$$ is a partition of the universal set $$S$$, then

$$
P(B) = \sum_{i} P(B|A_i)P(A_i)
$$

- Bayes Theorem

using

$$
P(AB) = P(BA) = P(A|B)P(B) = P(B|A)P(A)
$$

then

$$
P(A|B) = \dfrac{P(B|A)P(A)}{P(B)} = \dfrac{P(B|A)P(A)}{P(B|A)P(A)+P(B|\overline{A})P(\overline{A})}
$$

Why this can be useful?
Assume the input to the system is either $$A$$ or $$\overline{A}$$, and the output is either $$B$$ or $$\overline{B}$$.
The thing is the system includes some random behavior (like noise) such that $$B$$ is not fully determined by $$A$$.
For a real application, we may have an estimation for $$P(A)$$ and $$P(\overline{A})$$,
and we may know the noise model of the system to determine the values such as $$P(B|A)$$.
Then we can use the Bayes Theorem to calculate $$P(A|B)$$

- Example: Disease Testing

You're designing a test for a disease. $$D$$, that occurs in 0.5% of the population.
If the disease is present, your test alerts the medical staff 97% of the time.
If the disease is not present, it also give a false positive 1%.
If your machine gives an alert, what's the probability the person actually has the disease?

$$
\begin{align}
P(D) &= 0.005\\
P(A|D) &= 0.97\\
P(A|\overline{D}) &= 0.01\\
P(A) &= P(A|D)P(D) + P(A|\overline{D})P(\overline{D}) = 0.0148
\end{align}
$$

then

$$
P(D|A) = \dfrac{P(A|D)P(D)}{P(A)} = 0.328
$$

- Independence: two events $$A$$ and $$B$$ are independent iff

$$
P(AB) = P(A)P(B)
$$

and thus

$$
P(A|B) = P(AB)/P(B) = P(A)
$$

For $$N$$ independent events: $$P(A_1 A_2 \cdots A_N) = P(A_1)P(A_2)\cdots P(A_N)$$

Sometimes two events seems like to influence each others, but they still satisfy the definition of independence.
Example: roll two six sided dice and define $$A = \{ \text{rolling a 3 on the first dice} \}$$ and $$B = \{ \text{ both dice add to 7 } \}$$.

$$
\begin{align}
A &= (3,1), (3,2), (3,3), (3,4), (3,5), (3,6)\\
B &= (1,6), (2,5), (3,4), (4,3), (5,2), (6,1)\\
P(A) &= 1/6\\
P(B) &= 1/6\\
P(AB) &= 1/36
\end{align}
$$

[Youtube Lecture 3](https://www.youtube.com/watch?v=uQe_FnNy-XM&list=PL7sWxFnBVJLUbrCHertPLEqqCyLVnG-tN&index=3)
