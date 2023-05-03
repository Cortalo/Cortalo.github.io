---
title:  "Cauchy Inequality"
date:   2023-05-03 07:00:00 +0200
categories: math
tags: math
math: true
---

Review inner product: an inner product $$\langle x, y \rangle \to \mathbb{R}$$ if and only if it satisfies

1. &nbsp; $$\langle x, y \rangle = \langle y, x \rangle$$

2. &nbsp; $$\langle x, x \rangle \ge 0$$

3. &nbsp; $$\langle x, x \rangle = 0 \quad \implies \quad x = 0$$. Confusion: do we really need this?

4. &nbsp; $$\langle x, \alpha y + \beta z \rangle = \alpha \langle x, y \rangle + \beta \langle x, z \rangle$$

5. &nbsp; $$\langle \alpha x + \beta y, z \rangle = \alpha \langle x, z \rangle + \beta \langle y, z \rangle$$

# Cauchy Inequality

$$
\vert \langle x, y \rangle \vert \le \sqrt{\langle x, x\rangle \langle y, y \rangle}
$$

# Proof

$$
g(\lambda) = \langle \lambda x + y, \lambda x + y \rangle = \lambda^2 \langle x,x \rangle + 2 \lambda \langle x, y \rangle + \langle y, y \rangle \ge 0
$$

the above we use proerty 1, 2, 4, 5.

if $$\langle x, x \rangle = 0$$, then $$\langle x, y \rangle$$ must be 0. Otherwise we can take $$\lambda = \dfrac{-1 + \langle y, y \rangle}{2 \langle x , y \rangle}$$ such that $$g(\lambda) = -1$$.

When $$\langle x, x \rangle = 0$$, $$0 \le 0$$ of course holds.

When $$\langle x, x \rangle \ne 0$$, $$g(\lambda)$$ is a quadratic equation with 1 or zero real root. Thus its discriminate $$b^2 - 4 ac < 0$$

$$
(2\langle x, y \rangle )^2 - 4 \langle x, x \rangle \langle y, y \rangle \le 0
$$

it gives

$$
\vert \langle x, y \rangle \vert \le \sqrt{\langle x, x\rangle \langle y, y \rangle}
$$
