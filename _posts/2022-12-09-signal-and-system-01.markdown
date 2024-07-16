---
title:  "Signal And System 01"
date:   2022-12-09 05:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

## Signal and System

**How to understand signal $$x(t-t_0)$$?**

If $$t_0$$ is positive, it is a delayed version of $$x(t)$$;
If $$t_0$$ is negative, it is a advanced version of $$x(t)$$.
You can use the impulse function as an example.

**How to systematically sketch $$x(\alpha t + \beta)$$?**

First sketch the waveform of $$x(t + \beta)$$, you can use the impulse function to know if it is delay or advance.
Then reflect/compress/expand the waveform around origin.

**Linear System**

The response to $$x_1(t) + x_2(t)$$ is $$y_1(t) + y_2(t)$$

**Time Invariant System**

The response to $$x(t-t_0)$$ is $$y(t-t_0)$$.

**convolution sum**

$$
x[n] = \sum_{k=-\infty}^{\infty} x[k] \delta[n-k]
$$

$$
x(t) = \int_{-\infty}^{\infty} x(\tau) \delta(t-\tau) d\tau
$$

note that now $$\delta[n-k]$$ and $$\delta(t-\tau)$$ is signal, where $$x[k]$$ and $$x(\tau)$$ are just number.

**convolution is commutative**

$$
x[n]*h[n] = h[n]*x[n]
$$

$$
x(t)*h(t) = h(t)*x(t)
$$

**linear system response**

$$
y[n] = \sum_{k=-\infty}^{\infty} x[k]h_k[n]
$$

where $$h_k[n]$$ is the response to $$\delta[n-k]$$.

$$
y(t) = \int_{-\infty}^{\infty} x(\tau) h_{\tau}(t) d\tau
$$

where $$h_{\tau}(t)$$ is the respones to $$\delta(t-\tau)$$

**linear time invariant response**

$$
y[n] = x[n] * h[n] = \sum_{k=-\infty}^{\infty} x[k]h[n-k]
$$

where $$h[n]$$ is the response to $$\delta[n]$$.

$$
y(t) = x(t)*y(t) = \int_{-\infty}^{\infty} x(\tau) h(t-\tau) d\tau
$$

where $$h(t)$$ is the respones to $$\delta(t)$$

**initial rest (without proof), what is initial rest?**

For differential equation with initial rest, the system is LTI and causal.

$$
y(t) = \int_{-\infty}^{t} x(\tau) h(t-\tau) d\tau
$$

if $$x(t) = x(t)u(t)$$

$$
y(t) = \int_{0}^{t} x(\tau) h(t-\tau) d\tau
$$

**LTI system eigen function**

The response to $$e^{st}$$ (not $$e^{st}u(t)$$) is $$H(s)e^{st}$$, $$H(s)= \int_{-\infty}^{\infty} h(\tau)e^{-s\tau} d\tau$$.

The response to $$z^n$$ (not $$z^n u[n]$$) is $$H(z)z^n$$ is $$H(z) = \sum_{k=-\infty}^{\infty} h[k]z^{-k}$$.

## Fourier Series

**Fourier Series**

$$
x(t) = \sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t}
$$

$$
a_k = \dfrac{1}{T}\int_{T} x(t) e^{-jk\omega_0 t} dt
$$

$$
x[n] = \sum_{k=0}^{N-1} a_k e^{jk\omega_0 n}
$$

$$
a_k = \dfrac{1}{N} \sum_{n=0}^{N-1} x[n] e^{-jk\omega_0 n}
$$

although it is not obvious if or not Fourier series is unique, as an engineer we assume it is unique, meaning there is only one set of $$a_k$$ such that

$$
x(t) = \sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t}
$$

**Fourier Series: Time Shifting**

$$
x(t-t_0) \overset{FS}{\longleftrightarrow} e^{-jk\omega_0 t_0} a_k
$$

$$
x[n-n_0] \overset{FS}{\longleftrightarrow} e^{-jk\omega_0 n_0} a_k
$$

**Fourier Series: Time Reversal**

$$
x(-t) \overset{FS}{\longleftrightarrow} a_{-k}
$$

$$
x[-n] \overset{FS}{\longleftrightarrow} a_{-k}
$$

**Fourier Series: even and odd**

If $$x(t)$$ is even, then $$a_{k}$$ is even; If $$x(t)$$ is odd, then $$a_{k}$$ is odd.

If $$x[n]$$ is even, then $$a_{k}$$ is even; If $$x[n]$$ is odd, then $$a_{k}$$ is odd.

**Fourier Series: Multiplication**

$$
x(t)y(t) \overset{FS}{\longleftrightarrow} h_k = \sum_{l=-\infty}^{\infty} a_l b_{k-l}
$$

$$
x[n]y[n] \overset{FS}{\longleftrightarrow} h_k = \sum_{l=0}^{N-1} a_l b_{k-l}
$$

**Fourier Series: Conjugation**

$$
x^{*}(t) \overset{FS}{\longleftrightarrow} a_{-k}^{*}
$$

$$
x^{*}[n] \overset{FS}{\longleftrightarrow} a_{-k}^{*}
$$

**Fourier Series: real $$x(t)$$, real even $$x(t)$$ and real odd $$x(t)$$**

for real $$x(t)$$, $$ a_{k} = a_{-k}^{*} $$

for real even $$x(t)$$, $$a_{k}$$ is pure real and even.

for real odd $$x(t)$$, $$a_{k}$$ is pure imaginary and odd.

for real $$x[t]$$, $$ a_{k} = a_{-k}^{*} $$

for real even $$x[t]$$, $$a_{k}$$ is pure real and even.

for real odd $$x[t]$$, $$a_{k}$$ is pure imaginary and odd.

**Paeseval's theorem**

$$
\dfrac{1}{T}\int_T \vert x(t) \vert^2 dt = \sum_{-\infty}^{\infty} \vert a_k \vert^2
$$

$$
\dfrac{1}{N} \sum_{n=0}^{N-1} \vert x[n] \vert^2 = \sum_{k=0}^{N-1} \vert a_k \vert^2
$$

**filtering**

$$
y(t) = \sum_{k=-\infty}^{\infty} a_k H(jk\omega_0) e^{jk\omega_0 t}
$$

$$
y[n] = \sum_{n=0}^{N-1} a_k H(e^{jk\omega_0}) e^{jk\omega_0 n}
$$

**obtain frequency respones from ode**

$$
RC \dfrac{d y(t)}{dt} + y(t) = x(t)
$$

$$
RC \dfrac{d}{dt}[H(j\omega)e^{j\omega t}] + H(j\omega) e^{j\omega t} = e^{j\omega t}
$$

$$
H(j\omega) = \dfrac{1}{1+RCj\omega}
$$

**convergence of fourier series**

book_signals_and_systems, section 3.4

## Fourier Transform

**Fourier Transform**

$$
x(t) = \dfrac{1}{2\pi} \int_{-\infty}^{\infty} X(\omega) e^{j\omega t} d\omega
$$

$$
X(\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t} dt
$$

$$
X(\omega) = \sum_{k=-\infty}^{\infty} 2\pi a_k \delta(\omega - k\omega_0)
$$

We assume Fourier transform is unique, e.g., there is at most one $$X(\omega)$$ such that

$$
x(t) = \dfrac{1}{2\pi} \int_{-\infty}^{\infty} X(\omega) e^{j\omega t} d\omega
$$

**Fourier Transform: Differentiation and Integration**

$$
\dfrac{d x(t)}{dt} \overset{FT}{\longleftrightarrow} j\omega X(\omega)
$$

$$
\int_{-\infty}^{t} x(\tau) d\tau \overset{FT}{\longleftrightarrow} \dfrac{1}{j\omega} X(\omega) + \pi X(0)\delta(\omega)
$$


**Fourier Transform: Duality**

$$
g(t) \overset{FT}{\longleftrightarrow} f(\omega)
$$

$$
f(t) \overset{FT}{\longleftrightarrow} 2\pi g(-\omega)
$$

**Fourier Transform: Parseval's Relation**

$$
\int_{-\infty}^{\infty} \vert x(t) \vert^2 dt = \dfrac{1}{2\pi} \int_{-\infty}^{\infty} \vert X(\omega) \vert^2 d\omega
$$
