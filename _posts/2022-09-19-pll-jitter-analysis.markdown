---
title:  "PLL Jitter Analysis"
date:   2022-09-19 12:00:00 +0200
categories: analog-circuit
tags: analog pll
math: true
---

From [Paper](https://ieeexplore.ieee.org/document/4785494?reload=true)

## VCO Phase Noise and Benchmarking

$$
\begin{align}
FOM_{VCO} &= 10 \log \bigg(L_{VCO}(f_m) \cdot \frac{f_m^2}{f_{VCO}^2} \cdot \frac{P_{VCO}}{1mW}\bigg)\\
L_{VCO}(f_m) &= \frac{10^{FOM_{VCO}/10}}{P_{VCO}/1mW} \cdot \frac{f_{VCO}^2}{f_m^2}
\end{align}
$$

where $$L$$ is single sideband noise power to carrier power ratio.

## Loop Phase Noise and Benchmarking

To calculate the output phase noise due to the reference, frequency divider, phase detector and the charge pump.
Since they are low-pass filtered, at low frequency the phase noise level is

$$
\begin{align}
L_{loop} = \frac{S_{\phi,loop}}{2} = \frac{1}{2} \cdot N^2 \cdot \bigg( S_{\phi,ref} + S_{\phi,div} + S_{\phi, PD} + \frac{S_{i,CP}}{K_d^2} \bigg)
\end{align}
$$

Then at high frequency

$$
L_{loop}(f) = L_{loop} \cdot \big|\frac{G(s)}{1+G(s)}\big|^2
$$

### Phase Noise Due to the Reference Path, Divider, and PD

According to [this paper](https://ieeexplore.ieee.org/document/1291682), the time jitter can be written in terms of the integral of the single-sided power spectral density (PSD) of the phase $$S_{\phi}$$ within the Nyquist band (why?)

$$
\begin{align}
\sigma_{t_0}^2 = \frac{1}{4 \pi^2 f_{out}^2} \int_{0}^{f_{out}/2} S_{\phi}(f) df
\end{align}
$$

So

$$
\begin{align}
S_{\phi} = 8 \pi^2 \cdot f_{ref} \cdot \sigma_{t}^2
\end{align}
$$

time jitter depending on the output voltage slope $$\alpha_{out}$$

$$
\begin{align}
\sigma_{t}^2 = \frac{\bar{v_{n}^2}}{\alpha_{out}^2} = \frac{F_{n}\cdot kT/C_{out}}{\alpha_{out}^2}
\end{align}
$$

the total power in for the reference path, divider and PD can be expressed as

$$
P = f_{ref} \cdot C_{tot} \cdot V_{dd}^2
$$

then time jitter can be expressed as

$$
\sigma_{t}^2 = \frac{f_{ref}}{P} \cdot \bigg( \frac{F_{n} \cdot kT \cdot V_{dd}^2 \cdot C_{tot}/C_{out}}{\alpha_{out}^2} \bigg)
$$

To minimize the output jitter, designer can optimize the circuit by choosing the relative sizes of components, e.g., to maximize $$\alpha_{out}$$.
Once this optimization has been done, the jitter can always be reduced on a system level via [admittance level scaling](https://ieeexplore.ieee.org/document/1237362).
Then the voltage slope at every node does not change.
Thus, $$C_{tot}/C_{out}$$ as well as $$F_{n}$$ remains the same as all the node admittances scale toether.
Therefore, on the system level, we can treat the bracketed part as a design-dependent constant and get

$$
\sigma_{t}^2 \propto f_{ref}/P
$$

So

$$
S_{\phi} \propto f_{ref}^2/P
$$

### Phase Noise Due to the CP

$$
\begin{align}
S_{i} &= 8 kT \gamma \cdot (2 I_{CP}/ V_{ov})\\
S_{i,CP} &= S_{i} \cdot (\tau_{PD} / T_{ref})
\end{align}
$$

Power

$$
P_{CP} = I_{CP} V_{dd} \tau_{PD} \cdot f_{ref}
$$

and using $$K_{d} = I_{CP}/2\pi$$

$$
\frac{S_{i,CP}}{K_{d}^2} = \frac{f_{ref}^2}{P_{CP}} \cdot \bigg( \tau_{PD}^2 \cdot \frac{64 \pi^2 \gamma \cdot kT \cdot V_{dd}}{V_{ov}} \bigg) \propto \frac{f_{ref}^2}{P_{CP}}
$$

### Loop Phase Noise Benchmarking

Thus

$$
L_{loop} \propto N^2 \cdot \frac{f_{ref}^2}{P_{loop}} = \frac{f_{out}^2}{P_{loop}}
$$

define

$$
\begin{align}
FOM_{loop} &= 10 \log \bigg( L_{loop} \cdot \big( \frac{1 Hz}{f_{out}} \big)^2 \cdot \frac{P_{loop}}{1mW} \bigg)\\
L_{loop} &= 10^{FOM_{loop}/10} \cdot (\frac{f_{out}}{1 Hz})^2 \cdot \frac{1mW}{P_{loop}}
\end{align}
$$

## PLL Jitter and Benchmarking

To calculate the long-term PLL absolute jitter due to VCO

$$
\begin{align}
  \sigma_{t,VCO}^2 = \frac{1}{2\pi^2 f_{out}^2} \cdot \int_{0}^{\infty} L_{VCO}(f) \cdot |H_{VCO}(s)|^2 d f
\end{align}
$$

$$
    \sigma_{t,VCO}^2 = \frac{2 L_{VCO} (f_r) \cdot f_r^2}{f_{out}^2} \cdot \frac{f_{c,0}}{f_c} \cdot \int_{0}^{\infty} \bigg|\frac{1}{s \cdot [1 + G_0(s)]}\bigg|^2 df
$$

$$
  \sigma_{t,loop}^2 = \frac{L_{loop}}{2\pi^2 f_{out}^2} \cdot \frac{f_{c}}{f_{c,0}} \cdot \int_{0}^{\infty} \bigg| \frac{G_{0}(s)}{1+G_0(s)} \bigg|^2 df
$$

$$
\sigma_{t,PLL} = \sigma_{t,VCO} + \sigma_{t,loop}
$$

$$
\sigma_{t,PLL}^2 = \frac{1}{P_{PLL}} \cdot \bigg( 10^{\frac{FOM_{loop} + FOM_{VCO}}{20}} \cdot \frac{4}{\pi} \cdot \frac{1 mW}{1 Hz} \bigg) \cdot \square
$$

$$
\mathrm{FOM}_{\mathrm{PLL}} = 10 \log \Big( \big(\frac{\sigma_{\mathrm{t,PLL}}}{1 \mathrm{ s}}\big)^2 \cdot \frac{P_{\mathrm{PLL}}}{1 \mathrm{ mW}}  \Big)
$$

$$
\mathrm{FOM}_{\mathrm{PLL}} = 10 \log \Big( \big(\frac{\sigma_{\mathrm{t,PLL}}}{1 \mathrm{ s}}\big)^2 \cdot \frac{\color{red}P_{\mathrm{PLL}}}{1 \mathrm{ mW}}  \Big)
$$

$$
\mathrm{FOM} = 10 \log \Big( \big(\frac{\sigma_{\mathrm{t,out}}}{1 \mathrm{ s}}\big)^2 \cdot \frac{P_{\mathrm{total}}}{1 \mathrm{ mW}}  \Big)
$$
