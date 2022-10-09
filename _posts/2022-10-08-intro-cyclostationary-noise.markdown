---
title:  "An Introduction to Cyclostationary Noise"
date:   2022-10-08 16:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

from resources paper [introduction to cyclostationary noise](https://designers-guide.org/theory/cyclo-paper.pdf).

## Introduction

This paper introduces the noise analysis for mixers, oscillators, samplers, and logic gates.

### Ensemble Average

Noise free systems are deterministic, meaning that repeating the same experiment produces the same result.
Noisy systems are stochastic, repeating the same experiment produces slightly different results each time.
An experiment is referred to as a trial and a group of experiments is referred to as an ensemble of trials, or simply an ensemble.

Noise can be characterized by using a averages over the ensemble, called expectations, and denoted by the operator E.
The expection is the limit of the ensemble average as the number of trial approaches infinity.

Let $$v_n$$ be a noisy signal.
It can be separated into a purely noise free, or deterministic signal $$v$$, and a stochastic signal that is pure noise

$$
\begin{align}
v_n(t) &= v(t) + n(t)\\
E\{v_n(t)\} &= v(t)\\
E\{n(t)\} &= 0\\
var\{n(t)\} &= E\{n(t)^2\}
\end{align}
$$

A more general power-like quantity is the autocorrelation

$$
R_n(t,\tau) = E\{n(t) n(t-\tau)\}
$$

It is a measure of how points on the same signal separated by $$\tau$$ seconds are correlated.
We have

$$
var\{(t)\} = R_n(t,0)
$$

By performing the Fourier transform of the autocorrelation function with respect to the variable $$\tau$$ and then averaging over $$t$$, we obtain the time-averaged power spectral density, or PSD, that is measured by spectrum analyzers.

### Colored or Time-Correlated Noise

White noise after a LTI filter becomes colored or time-correlated noise.


### Cyclostationary or Frequency-Correlated Noise

Frequency-uncorrelated noise after a LTPV system becomes frequency-correlated noise.
Considering its single-sided spectrum (for frequency greater than 0).

- noise is correlated at frequency $$kf_0 + f$$ is correlated to $$kf_0 - f$$
- noise is correlated at frequency $$kf_0 + f$$ for different integer $$k$$

Circuits with time-varying operating points can cause the ensemble averages that describe noise to vary with time $$t$$.
If they vary in a periodic fashion, the noise is said to have cyclostationary properties, and the ensemble averages referred to as being cyclostationary.

It can be said that cyclostationary noise is "shaped in time $$t$$".
One cannot tell that noise is cyclostationary by just observing the time-average PSD.

In short

> shape in frequency\time $$\iff$$ correlation in time\frequency
{: .prompt-tip}


## Calculating Noise

We then linearize the circuit about the periodic large signal operating point and apply the small stochastic signal to this linearized system.

These linear time-varying systems generally are quite large and require special numerical techniques to be practical.
The reader is referred to [this](https://ieeexplore.ieee.org/document/661198) and [this](https://ieeexplore.ieee.org/document/545589) for details of numerical implementations.

## Characterizing Cyclostationary Noise

There are three common methods of characterizing cyclostationary noise.

The time-average power spectral density is similar to what would be measured with a conventional spectrum analyzer.
Since the analyzer has a very small effective input bandwidth, it ignores correlations in the noise and so ignores the cyclostationary nature of the noise.

The second method is to use the spectrum along with information about the correlations in the noise between sidebands.

The third.

### Time-Average Power Spectral Density

If a stage that generates cyclostationary noise is followed by a filter whose passband is constrained to a single sidedband (the passband does not contain a harmonic and has a bandwidth of less than $$f_0/2$$, where $$f_0$$ is the fundamental frequency of the cyclostationarity), then the output of the filyer will be stationary.
This is true because noise at different frequency will be uncorrelated.

Consider a stage that generates cyclostationary noise with modulatoin frequency $$f_1$$ that is followed by a stage whose transfer characteristics vary periodically at a frequency of $$f_2$$ (such as mixer, sampler, etc.).
Assume that $$f_1$$ and $$f_2$$ are non commensurate (ther is no $$f_0$$ such that $$f_1 = nf_0$$ and $$f_2 = mf_0$$ with $$n$$ and $$m$$ both integers).
Then there is no way to shift $$f_1$$ by a multiple of $$f_2$$ and have it fall on a correlated copy of itself.
As a result, the cyclostationary nature of the noise at the output of the first stage can be ignored.

The time-averaged power spectral density (PSD) can be used as the basis of a noise model when the subsequent stages eliminate or ignore the cyclostationary nature of the noise.
That is saying we can use time-averaged PSD to model the input noise, however, the output noise are still cyclostationary by default.

When a stage producing cyclostationary noise drives a subsequent stage that has a time-varying transfer function that is synchronous with the first, then ignoring the cyclostationary nature of the noise from the first stage (say by using the time-average PSD) generates incorrect results.

### AM & PM Noise
