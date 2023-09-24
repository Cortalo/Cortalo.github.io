---
title:  "Analog Circuits Explanation"
date:   2023-07-30 08:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---


# Basics

# Crystal Oscillator

## Resonant Frequency

We want to calculate the resonant frequency of a crystal, including $$C_0, R_m, L_m, C_m$$.
We will first calculate the total impedance.
Then by definition, resonat frequency is the frequency such that the total impedance is purely real.

$$
Z_0 = -\dfrac{j}{\omega C_0}
$$

$$
Z_m = R_m + j\omega L_m - \dfrac{j}{\omega C_m}
$$

$$

Z_p = \dfrac{Z_0 Z_m}{Z_0 + Z_m} = \dfrac{\dfrac{L_m}{C_0} - \dfrac{1}{\omega^2 C_0 C_m} - \dfrac{j R_m}{\omega C_0}}{R_m + j\left(\omega L_m - \dfrac{1}{\omega C_m} - \dfrac{1}{\omega C_0}\right)}
$$

The condition for $$Z_p$$ to be purely real

$$
\dfrac{-\dfrac{R_m}{\omega C_0}}{\dfrac{L_m}{C_0}-\dfrac{1}{\omega^2 C_0 C_m}} = \dfrac{\omega L_m - \dfrac{1}{\omega C_m} - \dfrac{1}{\omega C_0}}{R_m}
$$

$$
-\dfrac{R_m^2}{\omega C_0} = \left(\dfrac{L_m}{C_0}-\dfrac{1}{\omega^2 C_0 C_m}\right) \left(\omega L_m - \dfrac{1}{\omega C_m} - \dfrac{1}{\omega C_0}\right)
$$

$$
\omega^4 + \omega^2 \left(\dfrac{R_m^2}{L_m^2}-\dfrac{2}{L_m C_m} - \dfrac{1}{L_m C_0}\right) + \left(\dfrac{1}{L_m^2 C_m^2} + \dfrac{1}{L_m^2 C_m C_0}\right) = 0
$$

we can find two resonant frequency

$$
\omega^2 = \dfrac{1}{2} \left\{\left(\dfrac{2}{L_m C_m} + \dfrac{1}{L_m C_0} - \dfrac{R_m^2}{L_m^2}\right) \pm\left[\left(\dfrac{R_m^2}{L_m^2}-\dfrac{2}{L_m C_m} - \dfrac{1}{L_m C_0}\right)^2 - 4\left(\dfrac{1}{L_m^2 C_m^2} + \dfrac{1}{L_m^2 C_m C_0}\right)\right]^{1/2}\right\}
$$

some more algebra

$$
\begin{align}
&\left(\dfrac{R_m^2}{L_m^2}-\dfrac{2}{L_m C_m} - \dfrac{1}{L_m C_0}\right)^2 - 4\left(\dfrac{1}{L_m^2 C_m^2} + \dfrac{1}{L_m^2 C_m C_0}\right)\\
=& \left( \dfrac{1}{L_m C_0}-\dfrac{R_m^2}{L_m^2} \right)^2 - \dfrac{4 R_m^2}{L_m^3 C_m}
\end{align}
$$

We assume $$\left( \dfrac{1}{L_m C_0}-\dfrac{R_m^2}{L_m^2} \right)^2 \gg \dfrac{4 R_m^2}{L_m^3 C_m}$$.
For example, $$R_m=10\Omega, L_m=500uH, C_m=5fF, C_0=1pF$$, that will be $$4 \times 10^{30} \gg 6.4 \times 10^{26}$$.
Then

$$
\omega^2 \approx \left(\dfrac{1}{L_m C_m} + \dfrac{1}{2 L_m C_0} - \dfrac{R_m^2}{2 L_m^2}\right) \pm \left( \dfrac{1}{2 L_m C_0}-\dfrac{R_m^2}{2 L_m^2} \right)
$$

$$
\omega_s \approx \dfrac{1}{\sqrt{L_m C_m}}
$$

$$
\omega_a \approx \left(\dfrac{1}{L_m C_m} + \dfrac{1}{L_m C_0} - \dfrac{R_m^2}{L_m^2}\right)^{1/2}
$$

assume again $$\dfrac{1}{L_m C_0} \gg \dfrac{R_m^2}{L_m^2}$$, for example, $$2\times 10^{15} \gg 4 \times 10^{8}$$.

$$
\begin{align}
\omega_a \approx \sqrt{\dfrac{1}{L_m \left(C_m \Vert C_0\right)}}
\end{align}
$$

or

$$
\begin{align}
\omega_a \approx \sqrt{\dfrac{1}{L_m C_m}} \left(1+\dfrac{C_m}{C_0}\right)^{1/2} \approx \sqrt{\dfrac{1}{L_m C_m}} \left(1+\dfrac{C_m}{2C_0}\right)
\end{align}
$$

If there are load capacitance, the load capacitance $$C_L$$ will be parallel with $$C_0$$, thus

$$
\omega_s \approx \dfrac{1}{\sqrt{L_m C_m}}
$$

$$
\omega_a \approx \sqrt{\dfrac{1}{L_m \left(C_m \Vert \left(C_0+C_L\right)\right)}} \approx \sqrt{\dfrac{1}{L_m C_m}} \left(1+\dfrac{C_m}{2(C_0+C_L)}\right)
$$

depending on how the oscillator is designed, the oscillation frequency will be betwenn the two value

$$
\omega_s \le \omega_{osc} \le \omega_a
$$

## Equivalent Resistance

Let's denote $$jX = j\omega L_m - \dfrac{j}{\omega C_m}$$, and $$j X_{C0} = -\dfrac{j}{\omega C_0}$$.
The total impedence of the crystal

$$
\begin{align}
Z &= \dfrac{\left(R_m + jX\right)\left(j X_{C0}\right)}{R_m + j(X+X_{C0})}\\
&= \dfrac{R_m X_{C0}^2}{R_m^2 + \left(X+X_{C0}\right)^2} + \dfrac{jX_{C0}\left[R_m^2 + X\left(X+X_{C0}\right)\right]}{R_m^2 + \left(X+X_{C0}\right)^2}
\end{align}
$$

The effective resistance is given by

$$
R_e = \dfrac{R_m X_{C0}^2}{R_m^2 + \left(X+X_{C0}\right)^2}
$$

consider the frequency between $$\dfrac{1}{\sqrt{L_m C_m}} \le \omega \le \dfrac{1}{\sqrt{L_m C_m}} \left(\dfrac{C_m}{2(C_0+C_L)}\right) $$.
Since it is a narrow frequency range, $$X_{C0}$$ stay almost constant.
From $$\omega_s$$ to $$\omega_a$$, $$X$$ will increase from 0 to some positive value.
Since $$X_{C0}$$ is negative, $$R_e$$ will increase if we sweep the frequency from $$\omega_s$$ to $$\omega_a$$.
At $$\omega_s$$, $$X=0$$

$$
R_e\vert_{\omega=\omega_s} = \dfrac{R_m X_{C0}^2}{R_m^2 + X_{C0}^2} \approx R_m \quad (\text{ usually } \vert X_{C0} \vert \gg R_m)
$$

on the other hand, when $$\omega=\omega_a$$, we can use either of the two equations for $$\omega_a$$, consider the one

$$
\omega_a \approx \sqrt{\dfrac{1}{L_m \left(C_m \Vert \left(C_0+C_L\right)\right)}}
$$

then

$$
\omega_a L_m = \dfrac{1}{\omega_a C_m} + \dfrac{1}{\omega_a (C_0+C_L)}
$$

and

$$
X = \dfrac{1}{\omega_a\left(C_L+C_0\right)}
$$

then

$$
\begin{align}
R_e\vert_{\omega=\omega_a} &= \dfrac{R_m \left(\dfrac{1}{\omega_a C_0}\right)^2}{R_m^2 + \left(\dfrac{1}{\omega_a\left(C_L+C_0\right)} - \dfrac{1}{\omega_a C_0}\right)^2}\\
&= \dfrac{R_m X_{C0}^2}{R_m^2 + X_{C0}^2 \left(\dfrac{C_L}{C_L+C_0}\right)^2}
\end{align}
$$

assume $$\left\vert X_{C0} \left(\dfrac{C_L}{C_L+C_0} \right)\right\vert \gg R_m$$

$$
\begin{align}
R_e\vert_{\omega=\omega_a} &\approx R_m \left(\dfrac{C_L+C_0}{C_L}\right)^2
\end{align}
$$
