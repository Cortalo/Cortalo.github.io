---
title:  "Paper A -58dBc-Worst-Fractional-Spur and -234dB-FoM, 5.5GHz Ring-DCO-Based Fractional-N DPLL Using a Time-Invariant-Probability Modulator, Generating a Nonlinearity-Robust DTC-Control Word"
date:   2022-10-28 06:00:00 +0200
categories: analog-circuit
tags: pll
math: true
---

ISSCC 2020 17.3


From [Jaehyouk Choi's Paper](https://ieeexplore.ieee.org/document/9062948)

The concept of this work is from [Micheal Peter Kennedy's Paper](https://ieeexplore.ieee.org/document/8759073) that showed that if the expected value of an arbitrary analog or digial signal $$X$$, $$E[X](t)$$, is constant over time, the power spectral density (PSD) of $$X$$ shows no spurious tones.
This leads to the idea that, if we can modulate $$D_{DCW}$$ such that its probability density function (PDF) is time-invatiant, $$E[\tau_{DTC}](t)$$ becomes constant over time even after passing a nonlinear $$f_{DTC}(D_{DCW})$$, so the PSD of $$\tau_{DTC}$$ has no fractoinal spurs.

> Why PSD of $$X$$ shows no spurious tones, if $$E[X](t)$$ is constant over time?
{: .prompt-warning }

> If PSD of $X$ shows spur, it must have a long term sinusoidal at certain frequency. It causes $$E[X](t)$$ varys with time.
{: .prompt-tip }
