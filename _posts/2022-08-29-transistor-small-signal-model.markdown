---
title:  "Transistor Small Signal Model"
date:   2022-08-29 8:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

{% comment %}
From [Lectures](https://www.youtube.com/watch?v=I9A9BeGJsEM&t=10s) by Prof. Ali Hajimiri.
{% endcomment %}


## MOSFET

$$
\begin{align}
    C_{ox} &= \frac{3.9 \epsilon_0}{t_{ox}} = \frac{3.9 \times 8.85e-12}{t_{ox}}\\
    I_D &= \frac{1}{2}\mu_n C_{ox} \frac{W}{L}(V_{GS}-V_{TH})^2(1+\lambda V_{DS}) \quad \quad \text{pinch-off region}\\
    I_D &= \mu_n C_{ox} \frac{W}{L}\big( (V_{GS} - V_{TH})V_{DS} - \frac{1}{2}V_{DS}^2 \big) \quad \quad \text{triode region}
\end{align}
$$

bode effect (simply remember as source degeneration will have higher threshold voltage).

$$
\begin{align}
    V_{th} = V_{th0} + \gamma (\sqrt{|V_{SB}+2\Phi_F|} - \sqrt{|2\Phi_F|})
\end{align}
$$

$$
\begin{align*}
    g_m &= \frac{d I_{DS}}{d V_{GS}} = \mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TH}) = \frac{2 I_{DS}}{V_{GS} - V_{TH}} = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_{DS}}\\
    g_{ds} &= \lambda I_{DS} \quad \quad r_o = \frac{1}{\lambda I_{DS}} = \frac{L}{I_D} (\frac{d x_d}{d V_{DS}})^{-1}
\end{align*}
$$

### $$\pi$$ Model

![mosfet-pi-model](/assets/img/2022-08-29-transistor-small-signal-model/example-01.png)
_MOSFET $$\pi$$ model_

- The arrow indicates source of nmos or pmos.
- pmos has the same small signal model as nmos.
  - However pmos has source at the top.
  - The small signal model is flipped.

### $$T$$ Model

![mosfet-t-model](/assets/img/2022-08-29-transistor-small-signal-model/example-02.png)
_MOSFET $$T$$ model_

## BJT

$$
\begin{align}
r_{\pi} &= \beta r_m\\
\alpha &= \frac{\beta}{\beta+1}\\
\beta &= \frac{\alpha}{1-\alpha}
\end{align}
$$
