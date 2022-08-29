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

### Solution

$$
\begin{align}
R_{\pi} &= \frac{R_1 + R_2}{1+g_m R_2}\\
R_{\mu} &= R_1 + R_3 + G_m R_1 R_3\\
G_m &= \frac{g_m}{1+g_m R_2}\\
R_{\theta} &= \frac{R_2 + R_3}{1+g_m R_2}
\end{align}
$$

### Step-by-Step Solution

**The resistance looking into the port $$\pi$$**


![resistance-looking-into-port-pi](/assets/img/2022-08-27-impedance-calculation/example-02.png)
_The resistance looking into the port $$\pi$$_

KCL

$$
\begin{align}
i_1 &= i_x\\
i_2 + i_s = i_x \quad \implies i_2 &= i_x - i_s = i_x - \frac{v_x}{r_m}
\end{align}
$$

KVL

$$
\begin{align}
i_1 R_1 + i_2 R_2 = v_x
\end{align}
$$

thus

$$
\begin{align}
R_{\pi} &= \frac{v_x}{i_x} =  \frac{R_1 + R_2}{1+g_m R_2}
\end{align}
$$

**The resistance looking into the port $$\mu$$**


![resistance-looking-into-port-mu](/assets/img/2022-08-27-impedance-calculation/example-03.png)
_The resistance looking into the port $$\mu$$_

using

$$
\begin{align}
i_1 &= i_x\\
i_s (r_m + R_2) &= - i_1 R_1\\
i_3 + i_s &= i_x\\
v_x &= R_1 i_1 + R_3 i_3
\end{align}
$$

we got

$$
\begin{align}
R_{\mu} &= R_1 + R_3 + G_m R_1 R_3\\
G_m &= \frac{g_m}{1+g_m R_2}
\end{align}
$$

**The resistance looking into the port $$\theta$$**


![resistance-looking-into-port-theta](/assets/img/2022-08-27-impedance-calculation/example-04.png)
_The resistance looking into the port $$\theta$$_

using

$$
\begin{align}
r_m i_s &= R_2 i_2\\
i_2 + i_s &= i_x\\
i_3 + i_s &= i_x\\
i_3 R_3 + i_2 R_2 &= v_x
\end{align}
$$

we got

$$
R_{\theta} = \frac{R_2 + R_3}{1+g_m R_2}
$$


## Example 02

![example-02](/assets/img/2022-08-27-impedance-calculation/example-05.png)
_Example 02_

### Solution

$$
\begin{align}
R_{\pi} &= r_{\pi} \Vert \frac{R_1 + R_2}{1+g_m R_2}\\
R_{\mu} &= R_{left} + R_{right} + G_m R_{left} R_{right}\\
R_{left} &= R_1 \Vert [r_{\pi} + (1+\beta) R_2]\\
R_{right} &= R_3\\
G_{m} &= \frac{g_m}{1 + g_m R_2}\\
R_{\theta} &= \frac{R_2 + R_3}{1+\frac{1+\beta}{\beta+g_m R_1} g_m R_2} \approx \frac{R_2 + R_3}{1 + g_m R_2}
\end{align}
$$
