---
title:  "5T OTA Design"
date:   2023-06-14 07:00:00 +0200
categories: analog-circuit
tags: analog amplifier
math: true
---

Assume we need to design an amplifier with the following specification.

- Load capacitance $$C_L$$.
- Gain-bandwidth product $$f_u$$.

## Choose The Topology

Assume we choose the simple 5 transistor amplifier as the topology.
Also we commonly use PMOS as the input differential pair because in many technologies:

- With same $$g_m$$ and $$I_d$$, PMOS will have larges size, thus smaller offset.
- N-well is more clean than the substrate.
- PMOS have less flicker noise, because of the larger size and holes are far from surface or interface compared with electrons.

## Choose The $$g_m/I_d$$ Ratio For Each Transistor

If the focus is low noise (instead of small input capacitance), we will use larger $$g_m/I_d$$ (e.g., 25) for the input differential pair.
Since with the same current, they give us larger $$g_m$$, thus smaller input referred voltage noise $$4kT\gamma / g_m$$.

For the current mirror, we will use smaller $$g_m/I_d$$, to reduce the current noise $$4kT \gamma g_m$$. However, if $$g_m/I_d$$ is too small, the transistor will need a large overdrive voltage, then a small head room for the amplifier. As a example we may choose $$g_m/I_d=16$$ for the current mirror transistors.

## Choose The Channel Length For Each Transistor

The choice of channel length is a bit arbitrary.
In general longer channel will give higher intrinsic gain ($$g_m/g_{ds}$$).
Usually we simulate the PMOS and NMOS seperately, to find the relation between channel length and intrinsic gain.
In many technologies, intrinsic gain will increase until a certain channel length.
We may choose such channel length as the initial design, to have enough gain without having too much parasitics.

## Find The $$I_d/W$$ Ratio For Each Transistor

At the same time, simulate the $$\dfrac{I_D}{W}$$ vs. $$\dfrac{g_m}{I_D}$$ plot, for the later width determination.
Since we have decided the $$g_m/I_d$$ ratio for each transistor, the $$I_d/W$$ value can be found through the plot.

## Find The First $$g_m$$

For the 5 transistor amplifier, the $$g_{mp}$$ of the input differential pair can be determined by

$$
2\pi f_u = A_v \cdot \omega_p = g_{mp} R_o \cdot \dfrac{1}{R_o C_L} = \dfrac{g_{mp}}{C_L}
$$

$$
g_{mp} = 2\pi f_u C_L
$$

## Find All The Currents

We can use

$$
I_{D} = \dfrac{g_{m}}{g_m/I_D}
$$

to determine the current for the input differential pair.
Then all the currents can be determined by the topology.

## Find All the Width

We can use

$$
W = \dfrac{I_D}{I_D/W}
$$

to determine all the width of each transistor.
