---
title:  "Laplace Transforms"
date:   2023-01-03 07:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

- Heaviside step function

$$
u(t) = \begin{cases}
1 & \text{ for } \quad t > 0,\\
0 & \text{ for } \quad t \le 0
\end{cases}
$$

| $$H(s)$$                            | $$h(t)$$                          | $$\text{init cond}$$[^fn1] |
|-------------------------------------|-----------------------------------|----------------------------|
| $$1/s$$                             | $$u(t)$$                          | -                          |
| $$1/s^2$$                           | $$r(t) = t \cdot u(t)$$           | -                          |
| $$\dfrac{1}{s+a}$$                  | $$e^{-at} \cdot u(t)$$            | $$A\cdot e^{-at}$$         |
| $$\dfrac{1}{s}\cdot\dfrac{1}{s+a}$$ | $$\dfrac{1}{a} [1-e^{-at}] u(t)$$ | -                          |
| $$\dfrac{s^2}{s^2+b^2}$$            | -                                 | -                          |
| $$\dfrac{s}{s^2+b^2}$$              | $$\cos bt \cdot u(t)$$            | -                          |
| $$\dfrac{bs}{(s+a)^2+b^2}$$         | -                                 | -                          |
| $$\dfrac{b}{(s+a)^2+b^2}$$          | $$e^{-at} \sin bt \cdot u(t)$$    | -                          |

[^fn1]: Initial condition function only depends on the denominator of the transfer function. Such function can be added to the response with appropriate coefficient, to obtain the correct initial condition.

- Responses With Initial Condition

For transfer function $$H(s)$$, input $$X(s)$$ (usually step input $$X(s) = 1/s$$).
The full response with initial condition $$A$$ is

$$
y(t) = F^{-1}(H(s)X(s)) + A \cdot ic(t)
$$
