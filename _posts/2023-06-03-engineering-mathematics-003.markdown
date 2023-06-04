---
title:  "Engineering Mathematics 003"
date:   2023-06-03 08:00:00 +0200
categories: math
tags: math
math: true
---

From [Junyao Wang' Lecture 003](https://ocw.nthu.edu.tw/ocw/index.php?page=chapter&cid=145&chid=1829)

Exercise 10:

$$
\dfrac{dy}{dx} = \dfrac{vy-s\sqrt{x^2+y^2}}{vx}
$$

$$
y(w) = 0
$$

$$
udx + xdu = udx - (s/v) \sqrt{1+u^2} dx = udx - r\sqrt{1+u^2} dx
$$

$$
\dfrac{du}{\sqrt{1+u^2}} + r \dfrac{dx}{x} = 0
$$

$$
\ln \vert u + \sqrt{1+u^2} \vert + r \ln \vert x \vert = C
$$

$$
(u + \sqrt{1+u^2})x^r = k
$$

$$
(\dfrac{y}{x} + \sqrt{1+(\dfrac{y}{x})^2})x^r = k
$$

$$
k = w^{s/v}
$$

## Another Form

$$ (a_1 x + b_1 y + c_1) dx + (a_2 x  +b_2 y + c_2) dy = 0 $$

If $$c_1 \ne 0$$ or $$c_2 \ne 0$$

### First Case

If $$\dfrac{a_1}{a_2} \ne \dfrac{b_1}{b_2}$$

$$
\begin{cases}
a_1 x + b_1 y + c_1 = 0\\
a_2 x + b_2 y + c_2 = 0
\end{cases}
$$

the two lines cross at the point $$(x,y)=(\alpha,\beta)$$.
Let

$$
\begin{cases}
x = u+\alpha\\
y = v + \beta
\end{cases}
$$


$$
[a_1(u+\alpha) + b_1(v + \beta) + c_1] du + [\alpha_2 (u+\alpha) + b_2(v+\beta) + c_2] dv = 0
$$


$$
(a_1 u + b_1 v) du + (a_2 u + b_2 v) dv = 0
$$

Exercise 11:

$$
(-3x + y + 6)dx + (x+y+2)dy = 0
$$

$$
(x,y) = (1, -3)
$$

$$
\begin{cases}
x = u+1\\
y = v-3
\end{cases}
$$

$$
(-3u+v)du + (u+v)dv = 0
$$

Let $$s = u/v, du = sdv + vds$$

$$
(\dfrac{-3s+1}{s+1})(sdv + vds) + dv = 0
$$

$$
\dfrac{dv}{v} + \dfrac{3s-1}{(3s+1)(s-1)}ds
$$

$$
\dfrac{dv}{v} + \dfrac{1}{2}\dfrac{1}{s+\dfrac{1}{3}} ds + \dfrac{1}{2}\dfrac{1}{s-1} ds = 0
$$

$$
\ln \vert v \vert + \dfrac{1}{2} \ln \vert s + \dfrac{1}{3} \vert + \dfrac{1}{2} \ln \vert s - 1 \vert = C
$$

$$
v^2 \vert (s+\frac{1}{3})(s-1) \vert = C
$$

$$
\vert (3u + v)(u - v) \vert = C
$$

$$
\vert (3x+y)(x-y-4) \vert = C
$$

### Second Case

$$ (a_1 x + b_1 y + c_1) dx + (a_2 x  +b_2 y + c_2) dy = 0 $$

$$
\dfrac{a_1}{a_2} = \dfrac{b_1}{b_2} = m \ne \dfrac{c_1}{c_2}
$$

Let $$a_2 x + b_2 y = z$$

$$
dy = \dfrac{dz - a_2 dx}{b_2}
$$

$$
(mz + c_1) dx + (z + c_2) \dfrac{dz - a_2 dx}{b_2}
$$

$$
dx + \dfrac{(z+c_2)dz}{(b_2 m - a_2)z + (b_2 c_1 - a_2 c_2)} = 0
$$

Exercise 12:

$$
(x+y)dx + (3x + 3y - 4)dy = 0
$$

Let $$z = x+y$$

$$
zdx + (3z-4)(dz - dx) = 0
$$

$$
dx - \dfrac{3}{2}dz - \dfrac{dz}{z-2} = 0
$$

$$
x - \dfrac{3}{2}z - \ln \vert z-2 \vert = C
$$
