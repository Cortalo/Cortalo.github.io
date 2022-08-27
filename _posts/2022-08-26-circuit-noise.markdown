---
title:  "Noise in Circuits"
date:   2022-08-26 18:40:00 +0200
categories: analog-circuit
tags: analog
math: true
---

## Noise Type

- Thermal noise:

$$\overline{v_n^2}/ \Delta f = 4 k T R, \quad \overline{i_n^2} / \Delta f = \frac{4kT}{R}$$

- Shot noise:

$$\overline{i_n^2} /\Delta f = 2 q I_{DC}$$

- Flicker noise:

$$\overline{v_n^2} / \Delta f = \frac{K}{C_{ox}WL} \cdot \frac{1}{f}$$

- Flicker noise doesn't depend on bias current or temperature (really?). PMOS typically has smaller flicker noise than NMOS.
- Larger device (larger $$WL$$) will have smaller flicker noise.

### Example 01

$$
\begin{align}
    &\int_{0}^{\infty} \Big| \frac{1}{1 + j2\pi f RC} \Big|^2 4 kT R d f = 4 k T R \int_{0}^{\infty} \frac{1}{1 + (2 \pi R C f)^2} df \\
    = & \frac{4 k T R}{2 \pi RC}\int_{0}^{\infty} \frac{2 \pi R C}{1 + (2\pi R C f)^2}df\\
    =& \frac{2 kT}{\pi C} \int_{0}^{\infty}\frac{1}{1+x^2}dx\\
    =& \frac{2 kT}{\pi C} \frac{\pi}{2} = \frac{kT}{C}
\end{align}
$$

the calculation can be viewed as, using the cutoff frequency $$f_c = \frac{1}{2\pi RC}$$ of $$H(s) = \frac{1}{1 + sRC}$$

$$
\begin{align*}
    4 k T R \cdot \frac{1}{2 \pi RC} \cdot \frac{\pi}{2} = \frac{k T}{C}
\end{align*}
$$

the additional factor $$\frac{\pi}{2}$$ for equivalent noise bandwidth.

<p style="text-align: right"> $\square$ </p>
