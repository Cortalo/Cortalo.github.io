---
title:  "Measure Theory 01"
date:   2022-12-30 06:00:00 +0200
categories: math
tags: math
math: true
---


{% include embed/youtube.html id='llnNaRzuvd4' %}

# Introdution: A Non-Measurable Set

Can we define a measure on $$\mathbb{R}$$, such that it works on all the subsets of $$\mathbb{R}$$?

(i) $$\lambda: \mathfrak{P}(\mathbb{R}) \to \mathbb{R}_+ \cup \{\infty\}$$

(ii) $$\lambda((a,b)) = \lambda([a,b]) = b-a$$

(iii) $$\lambda(A+x) = \lambda(\{a_i + x, a_i \in A\}) = \lambda(A)$$

(iv) $$\lambda(\cup_{j\ge 1} A_j) = \sum_{j \ge 1} \lambda (A_j)$$

It is impossible to define such a measure on all the subsets.

- We define $$x \sim y \quad \iff \quad y - x \in \mathbb{Q}$$.

- Define $$[x] = \{ y \in \mathbb{R}, y - x \in \mathbb{Q}\}$$.

- then $$\Lambda = \mathbb{R} \vert_{\sim}$$.

- then using the axiom of choice, from each family in $$\Lambda$$, we choose one representitive to form $$\Omega$$, it is possible to make $$\Omega \subseteq \mathbb{R}$$ and $$\Omega \subseteq (0,1)$$.
For example, $$\Omega = \{\dfrac{1}{2}, \dfrac{\sqrt{2}}{2}, \dfrac{\sqrt{3}}{2}, \cdots\}$$.

- Then it is easy to show if $$p, q \in \mathbb{Q}$$ and $$p \ne q$$, we have $$(\Omega + p) \cap (\Omega + q) = \emptyset$$

- For set $$\sum_{q\in \mathbb{Q}, -1 < q < 1} (\Omega + q)$$

  - first, $$\sum_{q \in \mathbb{Q}, -1< q <1} (\Omega + q) \subseteq (-1,2)$$, then $$\lambda(\Omega) = 0$$.

  - second, $$(0,1) \subseteq \sum_{q\in \mathbb{Q}, -1<q<1} (\Omega + q)$$, then $$\lambda(\Omega) \ne 0$$.
