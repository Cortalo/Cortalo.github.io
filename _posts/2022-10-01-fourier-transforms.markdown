---
title:  "Fourier Transforms"
date:   2022-10-01 17:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

## Fourier Series

consider a periodic signal $$x(t)$$ with period $$T_0$$

$$
\begin{align}
a_n &= \frac{1}{T_0} \int_{T_0} x(t) e^{-jn\omega_{0}t}dt\\
x(t) &= \sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t}
\end{align}
$$

### Parseval's Theorem

$$
\begin{align}
\frac{1}{T_0} \int_{T_0} |x(t)|^2 dt = \sum_{k=-\infty}^{\infty} |a_k|^2
\end{align}
$$

## Fourier Transform

For a signal $$x(t)$$, if the integration $$\int_{-\infty}^{\infty} x(t) e^{-j\omega t} dt$$ exists for all $$ -\infty < \omega < \infty$$.

$$
\begin{align}
X(\omega) &= \int_{-\infty}^{\infty} x(t) e^{-j \omega t} dt\\
x(t) &= \frac{1}{2\pi} \int_{-\infty}^{\infty} X(\omega) e^{j\omega t} d\omega
\end{align}
$$


### Parseval's Theorem

$$
\int_{-\infty}^{\infty} |x(t)|^2 dt = \frac{1}{2\pi} \int_{-\infty}^{\infty} |X(\omega)|^2 d\omega
$$

## Discrete-Time Fourier Series

for a discrete-time signal $$x[n]$$ with period $$N$$, let $$\Omega_0 = 2\pi/N$$

$$
\begin{align}
a_k &= \frac{1}{N} \sum_{n=0}^{N-1} x[n] e^{-jk\Omega_0 n}\\
x[n] &= \sum_{k=0}^{N-1} a_k e^{jk\Omega_0 n}
\end{align}
$$

### Parseval's Theorem

$$
\frac{1}{N} \sum_{n=0}^{N-1} |x[n]|^2 = \sum_{k=0}^{N-1} |a_k|^2
$$


### Sampling Theorem

- If $$x[n]$$ is a sampling (with sampling frequency $$f_s = 1/T_s$$) of $$x(t)$$, such that $$N \cdot T_s $$ is the period of $$x(t)$$, may or may not be the fundamental period.
- If $$x(t)$$ does not includes any tones with frequency higher or equal than $$ f_s/2 $$
- Then DT FS gives exactly the same coefficients as $$x(t)$$ for frequencies $$0, f_s/N, \dots, (N/2 - 1) f_s/N$$.


## Discrete Fourier Transform

$$
X[k] = \sum_{n=0}^{N-1} x[n] e^{-jk \frac{2\pi}{N} n}
$$


```matlab
function psd = power_spectrum(signal, Fs)
    N = length(signal);
    spectrum = fft(signal)/N;
    psd = abs(spectrum).^2;
    psd = psd(1:N/2+1);
    psd(2:N/2) = 2*psd(2:N/2);
    f = (0:N/2)*Fs/N;
    semilogy(f, psd);
    title("SSB Power Spectrum Density");
    xlabel("f (Hz)");
end
```

## Fourier Transform Table

### Non-Causal Signal

| $$f(t)$$ with $$\, t \in R$$         | $$F(\omega)$$                                  | ROC? |
|--------------------------------------|------------------------------------------------|------|
| $$f(t)$$                             | $$\int_{-\infty}^{\infty} f(t)e^{-j\omega t}$$ |      |
| $$e^{-a\vert t \vert}, \quad a > 0$$ | $$\dfrac{2a}{a^2+\omega^2}$$                   |      |
| $$\delta(t)$$                        | $$1$$                                          |      |
| $$1$$                                | $$2\pi \delta(\omega)$$                        |      |
