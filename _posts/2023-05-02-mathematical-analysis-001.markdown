---
title:  "数学分析 001"
date:   2023-05-02 07:00:00 +0200
categories: math
tags: math
math: true
---

[陈纪修老师的课程](https://www.bilibili.com/video/BV15v411g7VP/)

- P1

# 第一章 集合与映射

## 集合

集合（集），具有某种特定性质，具体的或抽象的对象汇集的总体。集合一般用大写字母，例如$$S,T,A,B,X,Y$$表示。集合中的一个元素一般用小写字母标识，例如$$s,t,a,b,x,y$$。一些记号

$$
x \in S
$$

$$
y \notin S
$$

| 正整数集合  |   整数集合     |  有理数集合 | 实数集合  |
|---|---|---|---|---|
|  $$\mathbb{N}^+$$ | $$\mathbb{Z}$$  | $$\mathbb{Q}$$  |  $$\mathbb{R}$$    |

集合的表示一般又两种方法：
- 枚举法
- 描述法

枚举法

&nbsp; $$ \{\text{red}, \text{green}, \text{blue}\} $$

&nbsp; $$ \mathbb{N}^+ = \{1, 2, \dots, n, \dots\} $$

&nbsp; $$ \mathbb{Z} = \{0, \pm 1, \pm 2, \dots, \pm n, \dots\} $$

描述法

&nbsp; $$S = \{x \vert x \text{ satisfy property } p\}$$

&nbsp; $$A = \{x \vert x^2 = 2\} = \{ \pm \sqrt{2}\}$$

&nbsp; $$Q = \{x \vert x = \dfrac{q}{p}, p \in \mathbb{N}^+, q \in \mathbb{Z}\}$$

集合没有次序关系：$$\{a,b\} = \{b,a\}$$

集合中的元素重复是没有意义的：$$\{a,b\} = \{a,a,b\}$$

空集的概念：$$\emptyset = \{\} = \{x \vert x \in \mathbb{R} \text{ and } x^2 = -1\}$$

- P2

子集的概念：对于集合$$S,T$$，如果$$S$$的所有元素都存在于$$T$$, 则$$S \subset T$$

数学逻辑上的定义：$$S \subset T $$ 定义为 $$ x \in S \implies x \in T$$

$$p \implies q$$ 是记号 $$(p \land q) \lor (\lnot p)$$

&nbsp; $$\mathbb{N}^+ \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R}$$

如果$$S$$中至少有一个元素不属于$$T$$,则$$S$$不是$$T$$的子集，$$S \not\subset T$$

真子集：$$S \subsetneq T$$

例1.1.1： $$T=\{a,b,c\}$$, 求$$T$$的子集

$$
\emptyset, \{a\}, \{b\}, \{c\}, \{a,b\}, \{a,c\}, \{b,c\}, \{a,b,c\}
$$

集合相等：$$S = T \iff S \subset T \text{ and } T \subset S$$

实数的集合

&nbsp; $$(a,b) = \{x \vert x \in \mathbb{R} \text{ and } a < x < b\}$$

&nbsp; $$(a, \infty) = \{x \vert x \in \mathbb{R} \text{ and } a < x < \infty\}$$

&nbsp; $$[a,b] = \{x \vert x \in \mathbb{R}, \text{ and } a \le x \le b\}$$

## 集合的运算


| 并  |   交     |  差 | 补 |
|---|---|---|---|---|
|  $$\cup$$ | $$\cap$$  | $$ \backslash$$  |  $$S_{X}^{C}$$    |

对于补运算，我们需要知道，我们在哪个总集合里讨论问题

&nbsp; $$S \cup T = \{x \vert x \in S \text{ or } x \in T\}$$

&nbsp; $$S \cap T = \{x \vert x \in S \text{ and } x \in T\}$$

&nbsp; $$S \backslash T = \{x \vert x \in S \text{ and } x \not\in T\}$$

&nbsp; $$S_{X}^{C} = S^{C} = \{x \vert x \in X \text{ and } x \not\in S\}$$

例：$$ S = \{a,b,c\}, T = \{b,c,d,e\}$$

&nbsp; $$S \cup T = \{a,b,c,d,e\}$$

&nbsp; $$S \cap T = \{b,c\}$$

&nbsp; $$S \backslash T = \{a\}$$

交换律：

$$S \cup T = T \cup S$$

$$ S \cap T = T \cap S$$

结合律：

$$A \cup (B \cup D) = (A \cup B) \cup D$$

$$A \cap (B \cap D) = (A \cap B) \cap D$$

分配律：

$$A \cap (B \cup D) = (A \cap B) \cup (A \cap D)$$

$$A \cup (B \cap D) = (A \cup B) \cap (A \cup D)$$

以最后一条为例，进行证明，分两步，第一步证明$$A \cup (B \cap D) \subset (A \cup B) \cap (A \cup D)$$

若$$x \in A \cup (B \cap D)$$，则或者$$x \in A$$, 或者 $$x \in B \text{ 且 } x \in D$$，则$$x \in A \cup B$$ 且 $$x \in A \cup D$$, 也就是$$x \in (A \cup B) \cap (A \cup D)$$，所以$$A \cup (B \cap D) \subset (A \cup B) \cap (A \cup D)$$

第二步证明$$A \cup (B \cap D) \supset (A \cup B) \cap (A \cup D)$$

若$$x \in (A \cup B) \cap (A \cup D)$$, 则$$x \in A \cup B$$且$$x \in A \cup D$$，那么或者$$x \in A$$，或者$$x \in B \cap D$$，也就是$$x \in A \cup (B \cap D)$$，所以$$A \cup (B \cap D) \supset (A \cup B) \cap (A \cup D)$$

对偶律(De Morgen)：

&nbsp; $$(A \cup B)^C = A^C \cap B^C$$

&nbsp; $$(A \cap B)^C = A^C \cup B^C$$

- P3

## 有限集与无限集

&nbsp; $$S$$ 是由$$n$$个元素组成（$$n$$是非负正整数），则$$S$$是有限集。

空集是有限集。

不是有限集的集合是无限集。

可列集：如果无限集中的元素可按某种规则排成一列，则该集成为可列集。困惑：一列列出来有重复会有问题么？感觉没有问题。

可列集：$$\mathbb{N}^+, \{x \vert \sin(x) = 0\}$$

任何一个无限集包含可列子集。但是无限集不一定是可列集。之后会证明实数集不是可列集。

定理1.1.1：可列个可列集的并也是可列集

$$
\begin{align}
\bigcup\limits_{n=1}^{\infty} A_n &= A_1 \cup A_2 \cup \dots A_n \cup \dots\\
&= \{x \vert \text{ 存在 } n \in \mathbb{N}^+, \text{ 使得 } x \in A_n\}
\end{align}
$$

先把各个集合列出来

$$
\begin{align}
A_1&: x_{11}, x_{12}, x_{13}, \dots\\
A_2&: x_{21}, x_{22}, x_{23}, \dots\\
A_3&: x_{31}, x_{32}, x_{33}, \dots
\end{align}
$$

然后对角线法排出大集合

定理1.1.2: 有理数集合是可列集

只需要证明$$(0,1]$$上的有理数是可列集，然后可列个可列集是可列集。

## 笛卡尔乘积集合

P3, 27分钟