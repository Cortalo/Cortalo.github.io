---
title:  "TikZ Tutorial"
date:   2022-12-01 13:30:00 +0200
categories: cs
tags: tikz
math: true
---

From [link](https://www.bu.edu/math/files/2013/08/tikzpgfmanual.pdf).

```latex
\documentclass[tikz]{standalone}
\begin{document}
\begin{tikzpicture}
  \draw (-1.5,0) -- (1.5,0);
  \draw (0,-1.5) -- (0,1.5);
\end{tikzpicture}
\end{document}
```

![001](/assets/img/2022-12-01-tikz-tutorial/001.png)

- Straight Path Construction

```latex
\draw (-1.5,0) -- (1.5,0) -- (0,-1.5) -- (0,1.5);
```

![002](/assets/img/2022-12-01-tikz-tutorial/002.png)

- Curved Path Construction

For this, TikZ provides a special syntax.
One ot two "control points" are needed.
The math behind them is not quite trivial, but here is the basic idea:
Suppose you are at point $$x$$ and the first control point is $$y$$.
Then the curve will start "going in the direction of $$y$$ at $$x$$," that is, the tangent of the curve at $$x$$ will point toward $$y$$.
Next, suppose the curve should end at $$z$$ and the second support point is $$w$$.
Then the curve will, indeed, end at $$z$$ and the tangent of the curve at point $$z$$ will go through $$w$$.

```latex
\begin{tikzpicture}
  \filldraw [gray] (0,0) circle (2pt)
                  (1,1) circle (2pt)
                  (2,1) circle (2pt)
                  (2,0) circle (2pt);
  \draw (0,0) .. controls (1,1) and (2,1) .. (2,0);
\end{tikzpicture}
```

![003](/assets/img/2022-12-01-tikz-tutorial/003.png)

The general syntax for extending a path in a "curved" way is `.. controls` *\<first control point\>* `and` *\<second control point\>* `..` *\<end point\>*
