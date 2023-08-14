---
title:  "Engineering Mathematics Explanation"
date:   2023-07-23 10:00:00 +0200
categories: math
tags: math
math: true
---

## Multi-Variable Functions

### Taylor's Formula

For multi-variable function $$f(x,y)$$. To expand it around $$(a,b)$$, let

$$
\begin{cases}
x = a + (x_0-a)t\\
y = b + (y_0-b)t
\end{cases}
$$

then $$f(x(t),y(t))=F(t)$$

$$
F(t) = F(0) + \dfrac{F'(0)}{1!} t + \dfrac{F''(0)}{2!}t^2 + \dots
$$

$$
F'(t) = (x_0-a)f_x + (y_0-b)f_y
$$

$$
F''(t) = (x_0-a)^2f_{xx} + 2(x_0-a)(y_0-b)f_{xy} + (y_0-b)^2 f_{yy}
$$

### Implicit Function

From $$f(x,y)=0$$, we try to find the Taylor series of $$y(x)$$.
Then in a sense that, if we can uniquely determine all the derivatives $$y^{(n)}(x_0)$$, then we can make sure $$y(x)$$ is unique in a neighborhood of $$x_0$$.

$$
y(x) = y(x_0) + \dfrac{y'(x_0)}{1!}(x-x_0) + \dots
$$

Let $$R(x) = f(x,y(x)) = 0$$

$$
\begin{align}
R'(x_0) &= \dfrac{\partial f}{\partial x} \dfrac{dx}{dx} + \dfrac{\partial f}{\partial y} \dfrac{dy}{dx}\\
&= \dfrac{\partial f}{\partial x} + \dfrac{\partial f}{\partial y} \dfrac{dy}{dx}\\
&= 0
\end{align}
$$

$$
y'(x_0) = -\dfrac{\dfrac{\partial f}{\partial x}(x_0,y_0)}{\dfrac{\partial f}{\partial y}(x_0, y_0)}
$$

We can also calculate $$y''(x_0)$$, from

$$
y' = -\dfrac{f_x}{f_y}
$$

$$
\begin{align}
y'' &= -\dfrac{(\dfrac{d}{dx} f_x)f_y - f_x (\dfrac{d}{dx}f_y)}{f_y^2}\\
&= -\dfrac{(f_{xx}+f_{xy}y')f_y - f_x(f_{xy} + f_{yy}y')}{f_y^2}
\end{align}
$$
