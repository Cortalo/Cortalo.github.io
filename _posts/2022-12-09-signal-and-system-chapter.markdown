---
title:  "Signal And System Chapter"
date:   2022-12-11 08:00:00 +0200
categories: math
tags: fourier-analysis
math: true
---

## Signal and System

**Signal**

Signal is numbers with index.
For example the signal $$x(t-t_0)$$ actually means

```
def signal(t):
    return x(t-t_0)
```

or

```
signal = lambda t: x(t-t_0)
```

**Linear System**

The response to $$x_1(t) + x_2(t)$$ is $$y_1(t) + y_2(t)$$


**Time Invariant System**

The response to $$x(t-t_0)$$ is $$y(t-t_0)$$.

**Is linear constant coefficient ODE LTI**?

For example, consider an simple ODE

$$
y'' + y' + y = x(t)
$$

if we let the system has all zero initial conditions before we apply any signal (initial rest), then it is LTI.

We can verify the response to $$x_1(t) + x_2(t)$$ is $$y_1(t) + y_2(t)$$

$$
y_1''(t) + y_1'(t) + y_1(t) = x_1(t)
$$

$$
y_2''(t) + y_2'(t) + y_2(t) = x_2(t)
$$

$$
y_1''(t) + y_2''(t) + y_1'(t)+y_2'(t) + y_1(t) + y_2(t) = x_1(t) + x_2(t)
$$

Since both $$y_1(t)$$ and $$y_2(t)$$ satisfy the initial rest, zero initial conditin at some time $$\tau$$, their addition also satisfy zero inisital consition at $$\tau$$.

We can also verify the response to $$x(t-t_0)$$ is $$y(t-t_0)$$

$$
y''(t) + y'(t) + y(t) = x(t)
$$

$$
y''(t-t_0) + y'(t-t_0) + y(t-t_0) = x(t-t_0)
$$

before $$\tau$$ either $$x(t)$$ or $$x(t-t_0)$$ is zero, thus $$y(t)$$ and $$y(t-t_0)$$ satisfy the initial condition.

**$e^{j\omega t}$ is eigen signal for LTI system**
