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




# Maxwell's Equations

$$
\begin{cases}
\nabla \cdot \vec{D} = \rho\\
\nabla \cdot \vec{B} = 0\\
\nabla \times \vec{E} = -\dfrac{\partial \vec{B}}{\partial t}\\
\nabla \times \vec{H} = \dfrac{\partial \vec{D}}{\partial t} + \vec{J}\\
\vec{D} = \epsilon \vec{E}\\
\vec{H} = \vec{B}/\mu\\
\nabla \cdot \vec{J} + \dfrac{\partial \rho}{\partial t} = 0\\
\vec{J} = \rho \vec{u}
\end{cases}
$$

In fact, the two divergence equation can be derived from the two curl equation (how?).

## Lorentz's Force

$$
\vec{F} = q(\vec{E} + \vec{u}\times\vec{B})
$$

## Boundary Condition


$$
\begin{align}
E_{1t} = E_{2t}\\
\dots
\end{align}
$$

## Wave Equation

$$
\dfrac{1}{\mu\epsilon}\nabla^2 \vec{E} = \dfrac{\partial^2 \vec{E}}{\partial t^2}
$$

$$
\dfrac{1}{\mu\epsilon}\nabla^2 \vec{H} = \dfrac{\partial^2 \vec{H}}{\partial t^2}
$$

$$
c^2 = \dfrac{1}{\mu\epsilon}
$$

### Example

$$
c^2 \dfrac{\partial^2 f}{\partial x^2} = \dfrac{\partial^2 f}{\partial t^2}
$$

From d'Alembert's solution, the general solution is given by

$$
f(x,t) = F(kx+\omega t) + G(kx-\omega t)
$$

where $$\omega/k = c$$

## Time Harmonic Field

> Steady State Solution

$$
\vec{E}(x,y,z;t) = \mathrm{Re}\left(\vec{E}_{0}(x,y,z) e^{j\omega t}\right)
$$

Similar to the phasor in AC analysis, assume each component of the vector field is a phasor (having the same time frequency).

$$
\begin{cases}
\nabla \times \vec{E} = -j\omega \mu \vec{H}\\
\nabla \times \vec{H} = \vec{J} + j\omega\epsilon \vec{E}\\
\nabla \cdot \vec{E} = \dfrac{\rho}{\epsilon}\\
\nabla \cdot \vec{H} = 0
\end{cases}
$$

then for source free wave equation

$$
\nabla^2 \vec{E} + k^2 \vec{E} = 0
$$

where $$k^2 = \omega^2 \mu\epsilon$$

In the case of wave in conductor, we can define the compex permittivity

$$
\epsilon_c = \epsilon - j \dfrac{\sigma}{\omega}
$$

where $$\vec{J} = \sigma \vec{E}$$ (Ohms law).

# Plane Wave

## In Lossless Media

$$
\nabla^2 \vec{E} + k^2 \vec{E} = 0
$$

$$
\begin{cases}
\left(\dfrac{\partial^2}{\partial x^2} + \dfrac{\partial^2}{\partial y^2} + \dfrac{\partial^2}{\partial z^2} + k^2\right) E_x(x,y,z) = 0\\
\left(\dfrac{\partial^2}{\partial x^2} + \dfrac{\partial^2}{\partial y^2} + \dfrac{\partial^2}{\partial z^2} + k^2\right) E_y(x,y,z) = 0\\
\left(\dfrac{\partial^2}{\partial x^2} + \dfrac{\partial^2}{\partial y^2} + \dfrac{\partial^2}{\partial z^2} + k^2\right) E_z(x,y,z) = 0
\end{cases}
$$

Assume $$E_x(x,y,z) = X(x)Y(y)Z(z)$$

$$
\left(\dfrac{\partial^2}{\partial x^2} + \dfrac{\partial^2}{\partial y^2} + \dfrac{\partial^2}{\partial z^2} + k^2\right) X(x)Y(y)Z(z) = 0
$$

$$
\dfrac{X''}{X} + \dfrac{Y''}{Y} + \dfrac{Z''}{Z} + k^2 = 0
$$

$$
k_x^2 + k_y^2 + k_z^2 = k^2
$$

$$
E_x(x,y,z) = A e^{-j k_x x} B e^{-j k_y y} C e^{-j k_z z} = E_{x0} e^{-j \vec{k} \cdot \vec{R}}
$$

Assume for $$E_y, E_z$$ they have the same $$\vec{k}$$ as $$E_x$$.

$$
\vec{E}(x,y,z) = \vec{E_0} e^{-j \vec{k}\cdot\vec{R}}
$$

Does it allow different $$k_x,k_y,k_z$$ for different components?


Assume source free space

$$
\nabla \cdot \vec{E} = 0
$$

$$
\vec{E} = \vec{E_0} e^{-j \vec{k}\cdot\vec{R}}
$$

$$
\vec{k} \cdot \vec{E} = 0
$$

The magnetic field can be calculated from

$$
\begin{align}
\vec{H} &= -\dfrac{1}{j\omega \mu} \nabla \times \left( \vec{E_0} e^{-j \vec{k}\cdot \vec{R}} \right)\\
&= \dfrac{1}{-j\omega\mu} \nabla\left(e^{-j \vec{k}\cdot\vec{R}}\right)\times \vec{E_0}\\
&= \dfrac{-j\vec{k}}{-j\omega\mu}e^{-j\vec{k}\cdot\vec{R}} \times \vec{E_0}\\
&= \dfrac{\vec{k} \times \vec{E}}{\omega\mu} = \dfrac{1}{\eta} \hat{a_n} \times \vec{E}
\end{align}
$$

This is typical TEM wave, where the field is orthgonal to travel direction.

### Polarization

Assume

$$
\begin{align}
\vec{E}(z) &= \left(\hat{a_x} E_x + \hat{a_y}E_y\right) e^{-jkz}\\
&= \left(\hat{a_x} E_{x0} e^{-j\phi_{x0}} + \hat{a_y} E_{y0} e^{-j\phi_{y0}}\right) e^{-jkz}
\end{align}
$$

Dependent on the values of $$\phi_{x0}, \phi_{y0}$$ and $$E_{x0}, E_{y0}$$, it will show different polarization.

## In Lossy Media

$$
\nabla^2 \vec{E} + k_c^2 \vec{E} = 0
$$

$$
k_c = \omega \sqrt{\mu \epsilon_c}
$$

$$
\begin{align}
\gamma &= jk_c = j\omega \sqrt{\mu\epsilon}\left(1+\dfrac{\sigma}{j\omega\epsilon}\right)^{1/2}\\
&= \alpha + j\beta
\end{align}
$$

$$
\nabla^2 \vec{E} - \gamma^2 \vec{E} = 0
$$

$$
\vec{E} = \hat{a_x} E_0 e^{-\gamma z} = \hat{a_x} E_0 e^{-\alpha z} e^{-j\beta z}
$$

### Low-Loss Dielectrics

### Good Conductors

## Group Velocity

phase velocity

$$
u_p = \dfrac{\omega}{\beta}
$$

Dispersion: the situation when the phase velocity is different for different frequency.

Assume two frequency $$\omega_0 \pm \Delta \omega$$ with the same amptitude.

$$
\begin{align}
E(z,t) &= E_0 \cos\left[(\omega_0+\Delta\omega)t - (\beta_0+\Delta\beta)z\right] + E_0\cos\left[(\omega_0-\Delta\omega)t - (\beta_0-\Delta\beta)z\right]\\
&= 2E_0\cos(\Delta \omega t - \Delta \beta z) \cos(\omega_0 t - \beta_0 z)
\end{align}
$$

This is a carrier at frequency $$\omega_0$$ and an envelop at frequency $$\Delta\omega$$.
The phase velocity of carrier is

$$
u = \dfrac{\omega_0}{\beta_0}
$$

The phase velocity of envelop is

$$
u = \dfrac{\Delta \omega}{\Delta \beta}
$$

We call it group velocity

$$
u_g = \dfrac{1}{d\beta/d\omega}
$$

$$
u_g = \dfrac{u_p}{1-\dfrac{\omega}{u_p} \dfrac{du_p}{d\omega}}
$$

## Poynting Vector

$$
\begin{align}
&\nabla \cdot (\vec{E} \times \vec{H}) = \vec{H} \cdot (\nabla \times \vec{E}) - \vec{E} \cdot (\nabla \times \vec{H})\\
=& -\dfrac{\partial}{\partial t} \left(\dfrac{1}{2}\epsilon E^2 + \dfrac{1}{2}\mu H^2\right) - \sigma E^2
\end{align}
$$

&nbsp; $$\vec{E}\times\vec{H}$$ (Poynting vector) is the total power flow.

In the case of steady state sinosoidal analysis, the average power flow

$$
P_{\mathrm{av}} = \dfrac{1}{2}\mathrm{Re}(\vec{E}\times \vec{H}^*)
$$

## Normal Incidence At A Plane Conducting Boundary

Assume the wave travel from $$\sigma=0$$ to $$\sigma=\infty$$.
Incident wave

$$
\begin{cases}
\vec{E_i}(z) = \hat{a_x} E_{i0} e^{-j\beta_{1}z}\\
\vec{H_i}(z) = \hat{a_y} \dfrac{E_{i0}}{\eta_1} e^{-j\beta_1 z}
\end{cases}
$$

Reflected wave

$$
\vec{E_r} = \hat{a_x} E_{r0} e^{+j\beta_1 z}
$$

Total $$\vec{E}$$ in medium 1

$$
\vec{E_i} + \vec{E_r} = \hat{a_x} E_{i0} e^{-j\beta_{1}z} + \hat{a_x} E_{r0} e^{+j\beta_1 z}
$$

using boundary condition for perfect conductor

$$
E_{r0} = - E_{i0}
$$

&nbsp; $$\vec{H_r}$$ can get from $$\vec{E_r}$$.

## Oblique Incidence At A Plane Conducting Boundary

### Perpendicular Polarization

For the components that $$\vec{E_i}$$ is perpendicular to plane of incidence.

We guess the reflected wave $$\vec{E_r}$$ is also perpendicular to the plane of incidence.

$$
\hat{a_{ni}} = \hat{a_x}\sin\theta_i + \hat{a_z} \cos\theta_i
$$

$$
\vec{E_i} = \hat{a_y} E_{i0} e^{-j\beta_1 (x\sin\theta_i + z\cos\theta_i)}
$$

Now 8.7


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
