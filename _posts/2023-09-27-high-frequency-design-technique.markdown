---
title:  "High Frequency Design Technique"
date:   2023-09-27 07:00:00 +0200
categories: EM
tags: EM
math: true
---
# Introduction

## What Are High Frequency

Our familiar lumped circuit analysis is only an approximation, which is approximately valid when the circuit dimensions are less than $$\lambda/10$$.

| $$f$$   | $$\lambda$$ | $$\lambda/10$$ |
|---------|-------------|----------------|
| 1 GHz   | 30 cm       | 3cm            |
| 10 GHz  | 3 cm        | 3 mm           |
| 100 GHz | 3 mm        | 300 um         |

## AC Analysis

For a impedance $$Z(s)$$ consists of $$R, L$$ and $$C$$, if we apply a current $$i(t)=I \cos(\omega t + \varphi)$$, then the voltage "response" can be understand as

$$
v(t) \sim V \cos(\omega t + \theta)
$$

with

$$
V e^{j \theta} = I e^{j \varphi} \cdot Z(j\omega)
$$

### Average Power Consumption

Assume

$$
\begin{cases}
v(t) = V \cos(\omega t + \varphi)\\
i(t) = I \cos(\omega t + \theta)
\end{cases}
$$

$$
\overline{P} = \dfrac{1}{T} \int_0^{T} VI\cos(\omega t + \varphi) \cos(\omega t + \theta) dt = \dfrac{VI}{2} \cos(\theta-\varphi)
$$

In phaser representation

$$
\overline{P} = \dfrac{1}{2} \mathrm{Re}(V I^*)
$$

### Maximum Power Transfer

Assume a AC voltage source $$V_G \cos(\omega t)$$ with internal impedance $$Z_G = R_G + j X_G$$. What load impedance will results maximum average power on the load?

$$
\overline{P_L} = \dfrac{1}{2}\mathrm{Re}\left(\dfrac{V_G(R_L+j X_L)}{R_G+jX_G + R_L + jX_L} \cdot \dfrac{V_G}{R_G-j X_G + R_L - j X_L}\right)
$$

we need to maximax

$$
\dfrac{R_L}{(R_G+R_L)^2+(X_G+X_L)^2}
$$

so the maximum power transfer happens when

$$
\begin{cases}
R_L = R_G\\
X_L = -X_G
\end{cases}
$$



# LC Resonance and Matching Networks

## LC Resonance

For series-connected LC circuit, when the reactance magnitudes of $$L$$ and $$C$$ are equal, the pair resonates.

$$
\omega_0 = \dfrac{1}{\sqrt{LC}}
$$

## Series Circuit Quality Factors

Impedance $$Z$$, resistance $$R$$ and reactance $$X$$.

### Q of Inductors and Capacitors

We can model real inductor as the combination of resistance and reactance

$$
Z_L = R_L + j X_L
$$

$$
Z_C = R_C + j X_C
$$

For series $$L$$ and $$R_L$$

$$
Q = \dfrac{X_L}{R_L} = \dfrac{\omega L}{R_L}
$$

For series $$C$$ and $$R_C$$

$$
Q = \dfrac{X_C}{R_C} = \dfrac{1}{\omega C R_C}
$$

### Unloaded Q

The above apply to inductor or capacitor only.
If we connect such real inductor and capacitor in series, it seems we get two different $$Q$$

$$
Q_1 = \dfrac{\omega L}{R_L + R_C}
$$

$$
Q_2 = \dfrac{1}{\omega C (R_L+R_C)}
$$

Which one should we use? Actually at frequency $$\omega_0 = 1/\sqrt{LC}$$

$$
Q_U = \dfrac{\omega_0 L}{R_L+R_C} = \dfrac{1}{\omega_0 C(R_L+R_C)}
$$

the $$Q_U$$ is called as unloaded Q.

### Loaded Q

Then, the series connected real inductor and capacitor, and connected to some resistors and sources (including their internal resistance). Naturally, the loaded Q is defined as

$$
Q_L = \dfrac{\omega_0 L}{Z_{\text{others}} + R_L + R_C} = \dfrac{1}{\omega_0 C (Z_{\text{others}} + R_L + R_C)}
$$

## Parallel Circuit Quality Factors

Admittance $$Y$$, conductance $$G$$ and susceptance $$B$$.


$$
Y_L = G_L + jB_L
$$

$$
Y_C = G_C + jB_C
$$

For parallel $$L$$ and $$G_L$$

$$
Q = \dfrac{B_L}{G_L} = \dfrac{1}{\omega L G_L}
$$

For parallel $$C$$ and $$G_C$$

$$
Q = \dfrac{B_C}{G_C} = \dfrac{\omega C}{G_C}
$$

Similarly

$$
Q_U = \dfrac{1}{\omega L (G_L+G_C)} = \dfrac{\omega C}{G_L + G_C}
$$

$$
Q_L = \dfrac{1}{\omega_L (G_{\text{others}} + G_L + G_C)} = \dfrac{\omega C}{G_{\text{\others}} + G_L + G_C}
$$

## Coupled Resonators

# Distributed Circuits
