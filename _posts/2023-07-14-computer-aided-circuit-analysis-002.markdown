---
title:  "Computer Aided Circuit Analysis 002"
date:   2023-07-14 07:00:00 +0200
categories: analog-circuit
tags: analog
math: true
---

In this post, the detail of linear DC nodal analysis is discussed.
The material is from [Book: Electronic Circuit and System Simulation Methods](https://ieeexplore.ieee.org/document/735799).
Most of the content are from chapter 2 in the book.

## Linear DC Nodal Analysis

For the linear DC nodal analysis perspective, the circuits can have different components:

- Resistor
- Independent voltage source
- Independent current source
- Voltage-controlled current source
- Current-controlled current source
- Voltage-controlled voltage source
- Current-controlled current source

We have seen that nodal analysis can easily deal with resistor and independent current source.
Now we will see how to deal with the others.

We start from the nodal equations with only resistors and independent current sources.
If there are $$N+1$$ nodes, we can write down $$N+1$$ equations

$$
YV=I
$$

The equations will be indefinite. We can make it definite by picking any of the node as ground reference, then the corresponding row and column can be removed in $$Y$$, such that the equations are definite.
However, in this post, we will keep the original $$N+1$$ equtions in the form, for the symmetry of the equations.

### Matrix Stamps

#### Resistor

For a resistor connecting from node $$i$$ to node $$j$$, it will give the matrix stamps in $$Y$$ matrix.

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/002.png" style="width:20%;height:20%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/001.png" style="width:40%;height:40%;">


#### Independent Current Source

For a independent current source connecting from node $$i$$ to node $$j$$, it will give the matrix stamps in current vector

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/003.png" style="width:10%;height:10%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/004.png" style="width:30%;height:30%;">


#### Independent Voltage Sources

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/007.png" style="width:60%;height:60%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/008.png" style="width:60%;height:60%;">


#### Voltage-Controlled Current Source

Voltage-controlled current source is a four-terminal element.
It will give matrix stamp in $$Y$$ matrix.

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/005.png" style="width:50%;height:50%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/006.png" style="width:60%;height:60%;">

#### Current-Controlled Current Source

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/009.png" style="width:50%;height:50%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/010.png" style="width:60%;height:60%;">

#### Voltage-Controlled Voltage Source

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/011.png" style="width:60%;height:60%;">

#### Current-Controlled Voltage Source

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/012.png" style="width:60%;height:60%;">

### When Do Nodal Equations Fail?

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/013.png" style="width:60%;height:60%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/014.png" style="width:60%;height:60%;">

### DC Solution of Circuits with Energy Storage

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/015.png" style="width:60%;height:60%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/016.png" style="width:60%;height:60%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/017.png" style="width:40%;height:40%;">

<img src="/assets/img/2023-07-14-computer-aided-circuit-analysis-002/018.png" style="width:70%;height:70%;">
