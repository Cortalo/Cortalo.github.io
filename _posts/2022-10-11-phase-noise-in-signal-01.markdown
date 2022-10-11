---
title:  "Phase Noise in Signal 01"
date:   2022-10-11 17:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

## Signal's Spectrum and Power

consider a periodic signal $$x(t)$$ with period $$T_0$$

$$
\begin{align}
a_n &= \frac{1}{T_0} \int_{T_0} x(t) e^{-jn\omega_{0}t}dt\\
x(t) &= \sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t} = \sum_{k=-\infty}^{\infty} A_k e^{j\phi_k} e^{jk\omega_0 t}
\end{align}
$$

Its spectrum can be described as tones with amplitude and phase $$A_ke^{j\phi_k}$$, for frequencies $$k\omega_0 (k = 0, \pm 1, \pm 2, \dots)$$, and power

$$
\begin{align}
\frac{1}{T_0} \int_{T_0} |x(t)|^2 dt = \sum_{k=-\infty}^{\infty} |a_k|^2 = \sum_{k=-\infty}^{\infty} |A_k|^2
\end{align}
$$

For real signal $$x(t)$$

$$
\begin{align}
A_k &= A_{-k}\\
\phi_k &= -\phi_{-k}
\end{align}
$$

thus

$$
\begin{align}
x(t) &= B_0 + \sum_{k=1}^{\infty} B_k \cos(k\omega_0 t + \phi_k)\\
B_0 &= A_0\\
B_k &= 2 A_k
\end{align}
$$

Its spectrum can also be described as tones with amplitude and phase $$B_k \angle \phi_k$$, for frequencies $$k\omega_0 (k = 0, 1, 2, \dots)$$ with cosine base, and power

$$
\begin{align}
\frac{1}{T_0} \int_{T_0} |x(t)|^2 dt = |B_0|^2 + \sum_{k=1}^{\infty} \frac{|B_k|^2}{2}
\end{align}
$$

The use of $$\cos$$ or $$\sin$$ are arbitraty, as long as $$\cos$$ and $$\sin$$ are not mixed in one spectrum.

## Chapter 2 Review of Modulation Theory

**From Modulatoin Spectrum to Signal Spectrum**

### Amplitude Modulation

In this example we use sine base.
For a carrier power $$C$$

$$
V(t) = \sqrt{2C} [1 + M'(t)] \sin\omega t
$$

If

$$M'(t) = M'\sin pt$$

the result

$$
V(t) = \sqrt{2C} [\sin(\omega t) + \frac{M'}{2}\cos(\omega -p)t - \frac{M'}{2}\cos(\omega + p)t]
$$

It shows for AM, a tone in $$M'(t) (M'\angle 0 \text{ at frequency } p)$$ with carrier $$\sqrt{2C}\angle 0 \text{ at frequency } \omega$$, they will create three tones in the signal

$$
\begin{align}
& M'\sqrt{C/2}\angle \pi/2 \text{ at } \omega - p\\
& \sqrt{2C}\angle 0 \text{ at } \omega\\
& M'\sqrt{C/2}\angle -\pi/2 \text{ at } \omega + p
\end{align}
$$

### Phase Modulation
