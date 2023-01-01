---
title:  "Measure Theory 04"
date:   2023-01-01 07:00:00 +0200
categories: math
tags: math
math: true
---


{% include embed/youtube.html id='M8YGBuiqaOE' %}

# Caratheodory Extension

We want to extend the set function as below.
We start from semi-algebra, to algreba and $$\sigma$$-algebra.

- A $$\sigma$$-additive $$\mu: \mathscr{S} \to \mathbb{R}_{+} \cup \{\infty\}$$, to

- A $$\sigma$$-additive $$\nu: \mathscr{A}(\mathscr{S}) \to \mathbb{R}_{+} \cup \{\infty\}$$, to

- A $$\sigma$$-additive $$\pi: \mathscr{F}(\mathscr{S}) \to \mathbb{R}_{+} \cup \{\infty\}$$

We would

- first define a set funtion on the whole $$\mathscr{P}(\Omega)$$, called $$\pi^{*}: \mathscr{P}(\Omega) \to \mathbb{R}_+ \cup \{\infty\}$$.

- we can show $$\pi^{*}$$ is an outer-measure, although it is not $$\sigma$$-additive.

- then we will define a set $$\mathscr{M} \subseteq \mathscr{P}(\Omega)$$, such that

  - it satisfies $$\mathscr{M}$$ is an $$\sigma$$-algebra and $$\mathscr{M} \supseteq \mathscr{A}(\mathscr{S})$$

  - it satisfies $$\pi^* \vert_{\mathscr{M}}$$ is $$\sigma$$-additive

  - it satisfies $$\pi^* \vert_{\mathscr{A}(\mathscr{S})} = \nu$$

  - does $$\mathscr{M} = \mathscr{F}(\mathscr{S})$$?

## Outer Measure

A set function $$\mu: \mathscr{C} \to \mathbb{R}_+ \cup \{\infty\}$$ is an outer measure if and only if


(i) $$\mu(\emptyset) = 0$$

(ii) $$E \subseteq F, E, F \in \mathscr{C} \quad \implies \quad \mu(E) \le \mu(F)$$

(iii) $$\mu$$ is countable monotone

## Step 1

We define a set function on the whole $$\mathscr{P}(\Omega)$$, namely $$\pi^*: \mathscr{P}(\Omega) \to [0,\infty]$$

$$
\pi^*(A) = \inf_{\{E_i\}} \sum_{i \ge 1} \nu(E_i)
$$

where $$\{E_i\}_{i \ge 1}$$ is a countable covering of $$A$$ in $$\mathscr{A}(\mathscr{S})$$, i.e., $$E_i \in \mathscr{A}(\mathscr{S})$$ and $$A \subseteq \cup_{i \ge 1} E_i$$.
And the function $$\pi^*$$ is defined as the inf value for all possible covering of $$A$$.
