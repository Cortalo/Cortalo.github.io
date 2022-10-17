---
title:  "Phase Noise in Signal 01"
date:   2022-10-11 17:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

## Chapter 0 Signal's Spectrum and Power

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


## Chapter 2 Review of Modulation Theory

**From Modulatoin Spectrum to Signal Spectrum**

### Amplitude Modulation

For a carrier power $$C$$

$$
V(t) = \sqrt{2C} [1 + M'(t)] \cos\omega t
$$

If

$$M'(t) = M'\cos pt$$

the result

$$
V(t) = \sqrt{2C} [\cos(\omega t) + \frac{M'}{2}\cos(\omega -p)t + \frac{M'}{2}\cos(\omega + p)t]
$$

It shows for AM, a tone in $$M'(t) (M'\angle 0 \text{ at frequency } p)$$ with carrier $$\sqrt{2C}\angle 0 \text{ at frequency } \omega$$, they will create three tones in the signal

$$
\begin{align}
& M'\sqrt{C/2}\angle 0 \text{ at } \omega - p\\
& \sqrt{2C}\angle 0 \text{ at } \omega\\
& M'\sqrt{C/2}\angle 0 \text{ at } \omega + p
\end{align}
$$


### Phase Modulation

$$
\begin{align}
V(t) &= \sqrt{2C} \cos(\omega t + \theta(t))\\
V(t) &= \sqrt{2C} \cos(\omega t + \theta \cos p t)\\
V(t) & \approx \sqrt{2C} [\cos \omega t + \frac{\theta}{2} \cos((\omega+p)t+\frac{\pi}{2}) + \cos((\omega-p)t + \frac{\pi}{2})]
\end{align}
$$

It shows for PM, a tone in $$\theta(t) (\theta\angle 0) \text{ at } p$$ with carrier $$\sqrt{2C} \angle 0 \text{ at } \omega$$, they will create three tones in the signal

$$
\begin{align}
& \theta \sqrt{C/2}\angle \frac{\pi}{2} \text{ at } \omega - p\\
& \sqrt{2C} \angle 0 \text{ at } \omega\\
& \theta \sqrt{C/2}\angle \frac{\pi}{2} \text{ at } \omega + p
\end{align}
$$

### Frequency Modulation

### The Addition of an Arbitrary Phase Angle

In general for AM, a tone in $$M'(t) (M'\angle \phi_m \text{ at frequency } p)$$ with carrier $$\sqrt{2C}\angle \phi_c \text{ at frequency } \omega$$, they will create three tones in the signal


$$
\begin{align}
& M'\sqrt{C/2}\angle \phi_c - \phi_m \text{ at } \omega - p\\
& \sqrt{2C}\angle \phi_c \text{ at } \omega\\
& M'\sqrt{C/2}\angle \phi_c + \phi_m \text{ at } \omega + p
\end{align}
$$

Thus for AM, the two sidebands has phases sum to $$2\phi_c$$


In general for PM, a tone in $$\theta(t) (\theta\angle \phi_m) \text{ at } p$$ with carrier $$\sqrt{2C} \angle \phi_c \text{ at } \omega$$, they will create three tones in the signal


$$
\begin{align}
& \theta \sqrt{C/2}\angle \frac{\pi}{2} + \phi_c - \phi_m \text{ at } \omega - p\\
& \sqrt{2C} \angle \phi_c \text{ at } \omega\\
& \theta \sqrt{C/2}\angle \frac{\pi}{2} + \phi_c + \phi_m \text{ at } \omega + p
\end{align}
$$


Thus for AM, the two sidebands has phases sum to $$2\phi_c + \pi$$

### Linear Approximation

PM are not linear.
However, for very small AM and PM amplitude, we assume we can use superposition, meaning it we have both AM and PM with many tones

$$
V(t) = \sqrt{2C}[1+M'(t)]\cos(\omega t + \theta(t))
$$

we assume by appliying each tones in AM or PM, they will give all the correct sidebands for the signal.

### Phasor Representation

### Power Interpretation

A tone in the modulation with power $$N_0$$ creates two sidebands, each has power

$$
\overline{\phi_o^2} = \frac{2N_{op}}{C} = 2L
$$

or amplitude

$$
\theta = \sqrt{4N_{op}/C}
$$

## Chapter 3 The Relationship Between Phase Jitter And Noise Density

**From Signal Spectrum to Modulatoin Spectrum**

### The Representation of Narrow Band Noise

$$
V_n(t) = \sqrt{n_1} \cos[(\omega + p_1)t + \phi_1] + \sqrt{n_2} \cos[(\omega + p_2) t + \phi_2] + \dots
$$

### Phase Jitter Due to Superposed Single Sideband Noise

#### Convert Signal Spectrum to PM Modulation Spectrum

Considering signal spectrum (assume $$p > 0$$)

$$
\begin{align}
& \sqrt{2C} \angle 0 \text{ at } \omega\\
& \sqrt{2N_0} \angle \phi \text{ at } \omega + p
\end{align}
$$

This can be convert to spectrum due to PM

$$
\begin{align}
& \sqrt{N_0/2} \angle \pi - \phi \text{ at } \omega - p\\
& \sqrt{2C} \angle 0 \text{ at } \omega\\
& \sqrt{N_0/2} \angle \phi \text{ at } \omega + p
\end{align}
$$

That is modulation spectrum

$$
\begin{align}
N_{op} &= N_0/4\\
&\sqrt{N_0/C}\angle \phi - \frac{\pi}{2} \text{ at } p
\end{align}
$$


Considering signal spectrum (assume $$p > 0$$)

$$
\begin{align}
& \sqrt{2C} \angle 0 \text{ at } \omega\\
& \sqrt{2N_0} \angle \phi \text{ at } \omega - p
\end{align}
$$

This can be convert to spectrum due to PM

$$
\begin{align}
& \sqrt{N_0/2} \angle \phi \text{ at } \omega - p\\
& \sqrt{2C} \angle 0 \text{ at } \omega\\
& \sqrt{N_0/2} \angle \pi - \phi \text{ at } \omega + p
\end{align}
$$

That is modulation spectrum

$$
\sqrt{N_0/C}\angle \frac{\pi}{2} - \phi \text{ at } p
$$

#### Convert Signal Spectrum to AM Modulation Spectrum

### Phase Jitter due to Superposed Double Sideband Noise

Considering signal spectrum (assume p > 0)

$$
\begin{align}
& \sqrt{2n_1}\angle \phi_1 \text{ at } \omega-p\\
& \sqrt{2N_0} \angle 0 \text{ at } \omega\\
& \sqrt{2n_2} \angle \phi_2 \text{ at } \omega+p
\end{align}
$$

spectrum due to PM

$$
\begin{align}
& \sqrt{n_1/2} \angle \phi_1 \text{ at } \omega - p\\
& \sqrt{n_1/2} \angle \pi - \phi \text{ at } \omega + p\\
& \sqrt{2N_0} \angle 0 \text{ at } \omega\\
& \sqrt{n_2/2} \angle \pi - \phi_2 \text{ at } \omega - p\\
& \sqrt{n_2/2} \angle \phi_2 \text{ at } \omega + p
\end{align}
$$

Thus

$$
\begin{align}
L &= \frac{N_0}{2C}\\
S_\phi &= 2L = \frac{N_0}{C}
\end{align}
$$


## Chapter 4 Noise Induced Frequency Deviation
