---
title:  "Resistance Calculation"
date:   2022-08-27 18:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

{% comment %}
From [Lectures](https://www.youtube.com/watch?v=I9A9BeGJsEM&t=10s) by Prof. Ali Hajimiri.
{% endcomment %}

From Lectures by Prof. Ali Hajimiri.

## Example 01


![example-01](/assets/img/2022-08-27-impedance-calculation/example-01.png)
_Example 01_

The resistance looking into the port $$\pi$$

$$
\begin{align}
R_{\pi} &= \frac{R_1 + R_2}{1+g_m R_2}
\end{align}
$$

The resistance looking into the port $$\mu$$

$$
\begin{align}
R_{\mu} &= R_1 + R_3 + G_m R_1 R_3\\
G_m &= \frac{g_m}{1+g_m R_2}
\end{align}
$$

The resistance looking into the port $$\theta$$

$$
R_{\theta} = \frac{R_2 + R_3}{1+g_m R_2}
$$
