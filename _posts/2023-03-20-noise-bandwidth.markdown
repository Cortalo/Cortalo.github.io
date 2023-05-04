---
title:  "Noise Bandwidth"
date:   2023-03-20 07:00:00 +0200
categories: math
tags: math
math: true
---

From [TCAS-2017: Design Methodology for Phase-Locked Loops Using Binary (Bang-Bang) Phase Detectors](https://ieeexplore.ieee.org/document/7885515)

$$
\begin{align}
H_{LP}(s) &= H_0 \dfrac{1}{1 + \dfrac{s}{\omega_0 Q} + \dfrac{s^2}{\omega_0^2}}\\
\mathrm{NBW}_{LP} &= \dfrac{\omega_0 Q}{4} (\mathrm{Hz})
\end{align}
$$

$$
\begin{align}
H_{BP}(s) &= H_{max} \dfrac{\dfrac{s}{\omega_0 Q}}{1 + \dfrac{s}{\omega_0 Q} + \dfrac{s^2}{\omega_0^2}}\\
\mathrm{NBW}_{BP} &= \dfrac{\omega_0}{4Q} (\mathrm{Hz})
\end{align}
$$

# Proof

Using the result from [book Theory of Servomechanisms](https://archive.org/details/theoryofservomec0000jame/page/369/)


<img src="/assets/img/2023-03-20-noise-bandwidth/001.png" style="width:100%;height:100%;">


<img src="/assets/img/2023-03-20-noise-bandwidth/002.png" style="width:100%;height:100%;">
