---
title:  "Computer Aided Circuit Analysis 001"
date:   2023-07-11 07:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

In this post, the principle of DC analysis, AC analysis, transient analysis are explained.
We will focus on the minimum examples, such that the algorithms can be simplified as much as possible.
In the later posts, the algorithms for more complicated scenario will be introduced.

References:

- [Paper: Elements of Computer-Aided Circuit Analysis](https://ieeexplore.ieee.org/document/1083238)

## DC Analysis

### Linear DC Analysis

Linear circuits are composed of resistors, capacitors, inductors, independent and dependent sources.
In the minimum example in this section, we assume the circuits are only compsed of linear resistors and independent current sources.

Nodal analysis are applied to the linear DC analysis.
For a circuit of $$N$$ nodes, the number of equations (or the dimension of the voltage vector) will be $$N-1$$, since one of the node will be selected as the ground reference.

The equation will be
