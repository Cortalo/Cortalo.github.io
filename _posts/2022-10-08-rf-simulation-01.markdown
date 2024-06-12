---
title:  "RF Simulation 01"
date:   2022-10-08 10:00:00 +0200
categories: analog-circuit
tags: spectre
math: true
---

# Theory

## AC analysis

For example, $$v_{out} = v_{in}^2$$, then

$$
\begin{align}
v_{out} &= (v_{in,DC} + \Delta v_{in})^2 \\
 &\approx v_{in,DC}^2 + 2 \cdot v_{in,DC} \cdot  \Delta v_{in}
\end{align}
$$

Then

$$
\Delta v_{out} \approx 2 \cdot v_{in,DC} \cdot \Delta v_{in}
$$

## PAC analysis

$$
\begin{align}
\left(a \cos(\omega_0 t) + \Delta v_{in}\right)^2 = \left(\dfrac{a}{2} e^{j \omega_0 t} + \dfrac{a}{2} e^{-j\omega_0 t} + \Delta v_{in}\right)^2
\end{align}
$$

# Old

From resources: book introduction to rf simulatoin and its application.

## Characteristics of RF Circuits

RF circuits have several unique characteristics that are barriers to the application of traditional circuit simmulation techniques.
Researchers have developed [many special purpose algorithms](https://ieeexplore.ieee.org/document/643622) that overcome these barriers to provide practical simulation for RF circuits.

### Narrowband Signals

Modulated carriers are characterized as having a periodic high-frequency carrier signal and a low-frequency modulation signal that using either AM, PM or FM.
For example, a typical mobile telephone transmission has a 10-30 kHz modulation bandwidth riding on a 1-2 GHz carrier.

The ratio between the lowest frequency present in the modulation and the frequency of the carrier is a measure of the relative frequency resolution required of the simulation.
Thus transient analysis is expensive.

Passing a narrowband signal through a nonliear circuit results in a broadband signal whose spectrum is relatively sparse, as shown in Figure 3.
In general, this spectrum consists of clusters of frequencies near the harmonics of the carrier.

RF simulators exploit the sparse nature of this spectrum in various ways and with varying degrees of success.

### Time-Varying Linear Nature of the RF Signal Path

A simple change of perspective allows the mixer to be treated as having a single input and a near-linear, though oeriodicaly time-varying, transfer function.
As an example, consider a mixer made from an ideal multiplier and followed by a low-pass filter.

$$
v_{out}(t) = LPF\{\cos(\omega_{LO} t) \cdot v_{in}(t)\}
$$

or

$$
\begin{align}
v_{out}(t) &= \int_{-\infty}^{t} h_{LPF}(t-\tau) \cos(\omega_{LO}\tau) v_{in}(\tau) d\tau\\
&= \int_{-\infty}^{t} h(t,\tau) v_{in}(\tau) d\tau
\end{align}
$$

It is clearly a linear time varying (LTV) system with input $$v_{in}$$, and the impulse response (for a impulse input at $$\tau$$) is $$h(t,\tau)$$.
Especially, it is a periodic LTV system, meaning

$$
h(t,\tau) = h(t + N \cdot T, \tau + N \cdot T)
$$

To show LTV system will induce frequency translation, consider $$v_{in}(t) = m(t) \cos(\omega_c)t$$

$$
\begin{align}
v_{out}(t) &= LPF\{m(t) \cos(\omega_c t) \cos(\omega_{LO} t)\}\\
&\approx m(t) \cos((\omega_c - \omega_{LO})t)
\end{align}
$$

This demonstrates that a linear periodically-time-varying system (LPTV) implements frequency translation.


Often we can assume that the information signal is small enough to allow the use of a linear approximation of the circuit from its input to its output.
Linearizing a nonlinear circuit about a periodically-varying operating point extends small-signal analysis to circuits such as mixers, switched filters, samplers, and oscillators.

### Linear Passive Components

At the high frequencies present in RF circuits, the passive components, such as transmission lines, spiral inductors, packages (including bond wires) and substrates, often play a significant role in the behavior of the circuit.
The nature of such components often make then difficult to include in the simulation.

There are different techniques to deal with such distributed components.


## Basic RF Building Blocks

RF systems are constructed primarily using four basic building blocks: amplifiers, filters, mixers, and oscillators.

### Mixers
