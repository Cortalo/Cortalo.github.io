---
title:  "An Introduction to Cyclostationary Noise"
date:   2022-10-08 16:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

from resources paper introduction to cyclostationary noise.

## Introduction

This paper introduces the noise analysis for mixers, oscillators, samplers, and logic gates.

### Ensemble Average

Noise free systems are deterministic, meaning that repeating the same experiment produces the same result.
Noisy systems are stochastic, repeating the same experiment produces slightly different results each time.
An experiment is referred to as a trial and a group of experiments is referred to as an ensemble of trials, or simply an ensemble.

Let $$v_n$$ be a noisy signal

$$
v_n(t) = v(t) + n(t)
$$

### Colored or Time-Correlated Noise


### Cyclostationary or Frequency-Correlated Noise

Circuits with time-varying operating points can cause the ensemble averages that describe noise to vary with time $$t$$.
If they vary in a periodic fashion, the noise is said to have cyclostationary properties, and the ensemble averages referred to as being cyclostationary.


## Calculating Noise

We then linearize the circuit about the periodic large signal operating point and apply the small stochastic signal to this linearized system.

These linear time-varying systems generally are quite large and require special numerical techniques to be practical.
The reader is referred to [this](https://ieeexplore.ieee.org/document/661198) and [this](https://ieeexplore.ieee.org/document/545589) for details of numerical implementations.

## Characterizing Cyclostationary Noise
