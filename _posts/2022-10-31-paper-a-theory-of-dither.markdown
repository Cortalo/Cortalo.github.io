---
title:  "Paper A Theory of Nonsubtractive Dither"
date:   2022-10-31 06:00:00 +0200
categories: analog-circuit
tags: pll
math: true
---

From [Robert A. Wannamaker's Paper](https://ieeexplore.ieee.org/abstract/document/823976)

## 1. Introduction

### A. The Classical Model of Quantization

For Mid-tread quantization

$$
Q(w) = \Delta \lfloor \frac{w}{\Delta} + \frac{1}{2} \rfloor
$$

where $\lfloor . \rfloor$ is floor function, e.g.,

$$
\begin{align}
\lfloor 0.5 \rfloor &= 0\\
\lfloor 1 \rfloor &= 1\\
\lfloor 1.5 \rfloor &= 1
\end{align}
$$

### B. Dither: Subtractive versus Nonsubtractive

For SD (subtractively diththered), total error is

$$
\varepsilon = q(x+\nu)
$$

For nonsubstractively dithered system

$$
\varepsilon = q(x+\nu) + \nu
$$

It has been shown by Schuchman that

## Nonsubtractive Dither Theory

### A. Total Error PDF's

The input to the quantizer is $$w=x+\nu$$, which is the sum of the
