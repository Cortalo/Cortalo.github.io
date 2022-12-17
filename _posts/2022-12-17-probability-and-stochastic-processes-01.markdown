---
title:  "Probability and Stochastic Processes"
date:   2022-12-17 05:00:00 +0200
categories: math
tags: probability
math: true
---

[Youtube Lecture 2](https://www.youtube.com/watch?v=O3i_61SCgaM&list=PL7sWxFnBVJLUbrCHertPLEqqCyLVnG-tN&index=2)

- Partition: A partition of a set, $$S$$, is a finite series of mutually exclusive subsets that completely define $$S$$ such that

$$
S = A_1 + A_2 + \dots + A_N
$$

- The Axioms of Probability

$$
\begin{align}
P(A) &\ge 0\\
P(S) &= 1\\
\text{If } AB &= \emptyset, \text{ then } P(A \cup B) = P(A) + P(B)
\end{align}
$$

- Conditional Probability

$$
P(A|M) = \dfrac{P(AM)}{P(M)}
$$

- Example: IC Testing Proposal

Let $$G_1$$ and $$G_2$$ represent chips 1 and 2 being good, respectively.

$$
\begin{align}
P(\{\overline{G_1} \,\overline{G_2}\}) &= 0.01 \quad P(\{G_1 \overline{G_2}\}) = 0.01\\
P(\{\overline{G_1} G_2\}) &= 0.01 \quad P(\{G_1 G_2\}) = 0.97
\end{align}
$$

To calculate $$P(\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \vert \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\})$$

$$
\begin{align}
\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \cap \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\} &= \{\overline{G_1}\,\overline{G_2}\}\\
P(\{\overline{G_1}\,\overline{G_2}, G_1 \overline{G_2}\} \vert \{\overline{G_1}\,\overline{G_2}, \overline{G_1}G_2\}) &= \dfrac{0.01}{0.02} = 0.5
\end{align}
$$

- Total Probability Theorem

If $$A_1, A_2, \dots, A_N$$ is a partition of the universal set $$S$$, then

$$
P(B) = \sum_{i} P(B|A_i)P(A_i)
$$

- Bayes Theorem

using

$$
P(AB) = P(BA) = P(A|B)P(B) = P(B|A)P(A)
$$

then

$$
P(A|B) = \dfrac{P(B|A)P(A)}{P(B)} = \dfrac{P(B|A)P(A)}{P(B|A)P(A)+P(B|\overline{A})P(\overline{A})}
$$

Why this can be useful?
Assume the input to the system is either $$A$$ or $$\overline{A}$$, and the output is either $$B$$ or $$\overline{B}$$.
The thing is the system includes some random behavior (like noise) such that $$B$$ is not fully determined by $$A$$.
For a real application, we may have an estimation for $$P(A)$$ and $$P(\overline{A})$$,
and we may know the noise model of the system to determine the values such as $$P(B|A)$$.
Then we can use the Bayes Theorem to calculate $$P(A|B)$$

- Example: Disease Testing

You're designing a test for a disease. $$D$$, that occurs in 0.5% of the population.
If the disease is present, your test alerts the medical staff 97% of the time.
If the disease is not present, it also give a false positive 1%.
If your machine gives an alert, what's the probability the person actually has the disease?

$$
\begin{align}
P(D) &= 0.005\\
P(A|D) &= 0.97\\
P(A|\overline{D}) &= 0.01\\
P(A) &= P(A|D)P(D) + P(A|\overline{D})P(\overline{D}) = 0.0148
\end{align}
$$

then

$$
P(D|A) = \dfrac{P(A|D)P(D)}{P(A)} = 0.328
$$

- Independence: two events $$A$$ and $$B$$ are independent iff

$$
P(AB) = P(A)P(B)
$$

and thus

$$
P(A|B) = P(AB)/P(B) = P(A)
$$

For $$N$$ independent events: $$P(A_1 A_2 \cdots A_N) = P(A_1)P(A_2)\cdots P(A_N)$$

Sometimes two events seems like to influence each others, but they still satisfy the definition of independence.
Example: roll two six sided dice and define $$A = \{ \text{rolling a 3 on the first dice} \}$$ and $$B = \{ \text{ both dice add to 7 } \}$$.

$$
\begin{align}
A &= (3,1), (3,2), (3,3), (3,4), (3,5), (3,6)\\
B &= (1,6), (2,5), (3,4), (4,3), (5,2), (6,1)\\
P(A) &= 1/6\\
P(B) &= 1/6\\
P(AB) &= 1/36
\end{align}
$$

[Youtube Lecture 3](https://www.youtube.com/watch?v=uQe_FnNy-XM&list=PL7sWxFnBVJLUbrCHertPLEqqCyLVnG-tN&index=3)
