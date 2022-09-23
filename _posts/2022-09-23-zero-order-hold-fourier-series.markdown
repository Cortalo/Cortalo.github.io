---
title:  "Zero Order Hold Fourier Series"
date:   2022-09-23 09:00:00 +0200
categories: math
tags: fourier-series
math: true
---

For a function $$\sin(\omega_0 t)$$, it has Fourier Series

$$
\sin(\omega_0 t) = \frac{1}{2j} e^{j\omega_0 t} - \frac{1}{2j}e^{-j\omega_0 t}
$$

For such a function with zero order hold with frequency $$\omega_s$$, assuming

$$
\omega_s = N \omega_0
$$

and

$$
T_s = \frac{2\pi}{\omega_s}
$$

then we can calculate its Fourier Series $$\sum a_k e^{j k \omega_0 t}$$

$$
\begin{align}
a_k &= \frac{\omega_0}{2\pi} \sum_{m=0}^{N-1} \int_{m \cdot T_s}^{(m+1)T_s} \sin(\omega_0 \cdot m \cdot T_s) e^{-jk\omega_0 t} dt
\end{align}
$$

we can calculate, if $$k=0$$

$$
\begin{align}
a_0 &= \frac{\omega_0}{2\pi} \cdot T_s \sum_{m=0}^{N-1} \sin(\omega_0 \cdot m \cdot T_s)\\
&= \frac{1}{N} \cdot \frac{1}{2j} \sum_{m=0}^{N-1} \bigg( e^{j m \omega_0 T_s} - e^{-jm\omega_0 T_s}\bigg)\\
&= 0
\end{align}
$$

if $$k \ne 0$$

$$
\begin{align}
&\int_{m \cdot T_s}^{(m+1)T_s} \sin(\omega_0 \cdot m \cdot T_s) e^{-jk\omega_0 t} dt = \sin(\omega_0 \cdot m \cdot T_s) \int_{m\cdot T_s}^{(m+1)T_s} e^{-jk\omega_0 t}\\
=& \frac{1}{2j}\bigg( e^{jm\omega_0 T_s} - e^{-jm\omega_0 T_s}\bigg) \cdot \frac{1}{-jk\omega_0} \bigg( e^{-jk(m+1)\omega_0 T_s} - e^{-jkm\omega_0 T_s} \bigg)\\
=& \frac{1}{2k \omega_0} \bigg( Terms \bigg)
\end{align}
$$

where

$$
\begin{align}
Terms =& e^{-jk\omega_0 T_s} \cdot e^{j(1-k)m \omega_0 T_s}\\
& - e^{j(1-k)m \omega_0 T_s}\\
& - e^{-jk\omega_0 T_s} e^{-j(1+k)m \omega_0 T_s}\\
& + e^{-j(1+k)m \omega_0 T_s}
\end{align}
$$

using the theorm from DSSP (FFT chapter), summation of terms will be nonzero only when

$$
e^{j(1-k)m\omega_0 T_s} = 1 \quad \text{or} \quad e^{-j(1+k)m\omega_0 T_s} = 1
$$

that is when

$$
k = 1 + qN \quad \text{or} -1 + qN
$$

the results

$$
a_k = \frac{1}{2j} \cdot \frac{1}{1+qN} \cdot \frac{\sin(\pi/N)}{\pi/N} \cdot e^{-j\pi/N} \quad \text{when} \quad k = 1+qN
$$

and

$$
a_k = \frac{1}{2j} \cdot \frac{1}{-1+qN} \cdot \frac{\sin(\pi/N)}{\pi/N} \cdot e^{j\pi/N} \quad \text{when} \quad k = -1+qN
$$

If subtract the sampling signal from the original signal, the remaining parts has fourier series as (approximately)

$$
\begin{equation*}
            a_k =
            \left\{
            \begin{aligned}
            &j \frac{\pi}{N}, \quad \quad \quad \quad \quad \quad \quad k=1 \\
            &-j \frac{\pi}{N}, \quad \quad \quad \quad \quad \quad k=-1\\
            & \frac{1}{2j} \cdot \frac{1}{1+qN}, \quad \quad \quad k = 1 + qN\\
            & \frac{1}{2j} \cdot \frac{1}{-1+qN},  \quad \quad k = -1 + qN\\
            & 0, \quad \quad \quad \quad \quad \quad \quad \quad \text{otherwise}
            \end{aligned}
            \right.
\end{equation*}
$$
