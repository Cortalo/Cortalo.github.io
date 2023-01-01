---
title:  "Measure Theory 03"
date:   2022-12-31 07:00:00 +0200
categories: math
tags: math
math: true
---


{% include embed/youtube.html id='6LMZLlSH3uM' %}

# Set Functions

## Additive

Given $$\mathscr{C} \subseteq \mathscr{P}(\Omega)$$ and $$\emptyset \in \mathscr{C}$$.
The function $$\mu: \mathscr{C} \to \mathbb{R}_+ \cup \{\infty\}$$ is additive, if and only if

(i) $$\mu(\emptyset) = 0$$

(ii) if disjoint $$E_1, E_2, \dots, E_n \in \mathscr{C}$$, and $$E = \sum_{j=1}^{n}E_j \in \mathscr{C}$$, then $$\mu(E) = \sum_{j=1}^n \mu(E_j)$$.

We can natually define a set function on the semi-algebra like $$(a,b]$$.
We want to extend the set function to algebra and $$\sigma$$-algebra.

## $$\sigma$$-Additive

Given $$\mathscr{C} \subseteq \mathscr{P}(\Omega)$$ and $$\emptyset \in \mathscr{C}$$.
The function $$\mu: \mathscr{C} \to \mathbb{R}_+ \cup \{\infty\}$$ is $$\sigma$$-additive, if and only if

(i) $$\mu(\emptyset) = 0$$

(ii) if disjoint $$E_1, E_2, \dots, E_j, \dots \in \mathscr{C}$$, and $$E = \sum_{j\ge 1}E_j \in \mathscr{C}$$, then $$\mu(E) = \sum_{j\ge 1} \mu(E_j)$$.

## Cover

Set $$E$$ is covered by a collection $$\{E_k\}_{k=1}^{n}$$ means

$$
E \subseteq \cup_{k=1}^{n} E_k
$$

## Finite Monotone

A set function $$\mu: \mathscr{C} \to [0,\infty]$$ is said to be finite monotone provided that, whenever a set $$E \in \mathscr{C}$$ is covered by a finite collection $$\{E_k\}_{k=1}^{n}$$ of sets in $$\mathscr{C}$$

$$
\mu(E) \le \sum_{k=1}^{n}\mu(E_k)
$$

## Countable Monotone

A set function $$\mu: \mathscr{C} \to [0,\infty]$$ is said to be countable monotone provided that, whenever a set $$E \in \mathscr{C}$$ is covered by a countable collection $$\{E_k\}_{k=1}^{\infty}$$ of sets in $$\mathscr{C}$$

$$
\mu(E) \le \sum_{k=1}^{\infty}\mu(E_k)
$$

## Continuous Measure

Given $$\mathscr{C} \subseteq \mathscr{P}(\Omega)$$, and $$\mu: \mathscr{C} \to \mathbb{R}_+ \cup \{\infty\}$$.

- for $$E \in \mathscr{C}$$, $$\mu$$ continuous from below at $$E$$, if and only if $$\forall (E_n)_{n \ge 1}, E_n \in \mathscr{C}, E_n \uparrow E$$, then $$\mu(E_n) \uparrow \mu(E)$$.

- for $$E \in \mathscr{C}$$, $$\mu$$ continuous from above at $$E$$, if and only if $$\forall (E_n)_{n \ge 1}, E_n \in \mathscr{C}, E_n \downarrow E$$ and $$\exists n_0, \mu(E_{n_0}) < \infty$$, then $$\mu(E_n) \downarrow \mu(E)$$.

  - the need of $$\mu(E_{n_0})$$, consider the example of $$E_n = (n, \infty)$$, then $$E_n \downarrow \emptyset$$.

**Lemma:** $$\mathscr{A} \subseteq \mathscr{P}(\Omega)$$ is an algebra, then for an additive $$\mu: \mathscr{A} \to \mathbb{R}_+ \cup \{\infty\}$$.

- $$\mu$$ is $$\sigma$$-additive $$\quad \implies \quad $$ $$\mu$$ continuous at $$E , \forall E \in \mathscr{A}$$.

- $$\mu$$ is continuous from below $$\quad \implies \quad$$ $$\mu$$ is $$\sigma$$-additive.

- $$\mu$$ is continuous from above at $$\emptyset$$ and $$\mu$$ is finite ($$\mu(\Omega) < \infty$$) $$\quad \implies \quad$$ $$\mu$$ is $$\sigma$$-additive.

## Measure Extantion

**Theorem 1:** $$\mathscr{S} \subseteq \mathscr{P}(\Omega)$$ is a semi-algebra, $$\mu: \mathscr{S} \to \mathbb{R}_+ \cup \{\infty\}$$ is additive. Then there exists $$\nu: \mathscr{A}(\mathscr{S}) \to \mathbb{R}_+ \cup \{\infty\}$$ is additive, and

(a) $$\nu(A) = \mu(A) \forall A \in \mathscr{S}$$

(b) $$\nu_1(A) = \nu_2(A) \forall A \in \mathscr{S} \quad \implies \nu_1(E) = \nu_2(E) \forall E \in \mathscr{A}(\mathscr{\mathscr{S}})$$

**Theorem 2:** $$\mathscr{S} \subseteq \mathscr{P}(\Omega)$$ is a semi-algebra, $$\mu: \mathscr{S} \to \mathbb{R}_+ \cup \{\infty\}$$ is $$\sigma$$-additive. Then there exists $$\nu: \mathscr{A}(\mathscr{S}) \to \mathbb{R}_+ \cup \{\infty\}$$ is $$\sigma$$-additive, and

(a) $$\nu(A) = \mu(A) \forall A \in \mathscr{S}$$

(b) $$\nu_1(A) = \nu_2(A) \forall A \in \mathscr{S} \quad \implies \nu_1(E) = \nu_2(E) \forall E \in \mathscr{A}(\mathscr{\mathscr{S}})$$

Using $$\mathscr{A}(\mathscr{S}) = \{ \sum_{j=1}^n E_j, \forall \text{ disjoint } E_j \in \mathscr{S}, \forall 1 \le n < \infty\}$$, the set function extention is in fact

$$
\nu(E) = \sum_{j=1}^n \mu(E_j)
$$
