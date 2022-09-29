---
title:  "Spectre DC Analysis"
date:   2022-09-25 16:00:00 +0200
categories: analog-circuit
tags: spectre
math: true
---

In DC analysis, equilibrium points are calculated.
It is important to understand that:
- Circuits sometimes have more than one DC solution.
- The DC solution computed by the citcuit simulator may be unstable.

## Newton-Raphson Method

Newton's method solves nonlinear algebraic equation by iteration.
For equations

$$
f(\hat{v}) = 0
$$

starting with an initial guess $$v^{(0)}$$ and repeatedly solving the Newton-Raphson iteration equation

$$
v^{(k+1)} = v^{(k)} - J^{-1}(v^{k}) f(v^{(k)})
$$

where $$J(v) = \frac{d}{dv} f(v)$$ is called the Jacobian of $$f$$ at $$v$$.
It represents the circuit linearized about $$v$$.

It is guaranteed to converge to $$\hat{v}$$ if $$f$$ is continuously differentiable, if the solution is isolated, and if $$v^{(0)}$$ is sufficiently close to $$\hat{v}$$.
In circuit simulation, none of these three conditions are guaranteed, and so neither is convergence.

## Convergence Criteria

In Spectre it uses both of two criteria.
The first one is called Newton update convergence criterion.

$$
|v_n^{(k)} - v_n^{(k-1)}| < \text{reltol} \cdot v_{n,max} + \text{vntol}
$$


where typically

$$v_{n,max} = \text{max}(|v_{n}^{(k)}|, |v_{n}^{(k-1)}|)$$

By default, reltol is 0.001 and vntol (called vabstol in Spectre) is 1uV.

The second one is called Newton residue convergence criterion

$$
|f_n(v^{(k)})| < \text{reltol} f_{n,max} + \text{abstol}
$$

where typically $$f_{n,max}$$ is the absolute value of the largest current entering node $$n$$ from any one branch.

Typicaly, abstol (called iabstol in Spectre) is 1pA.


## Very Small Resistors

Very small resistors put difficulties to the Newton residue convergence criterion.
Since very small voltage error can create large currents.

- Try to avoid small resistors.
- Use 0-volt voltage sources as current probes rather than small-valued resistors.
- Discard overly small parasitic resistors in semiconductors.
- Spectre automatically deletes all parasitic resistors smaller than a particular value, given by the model parameter `minr`.
- If it is necessary to use small valued parasitic resistors, increase `iabstol` to avoid convergence problems.

## Isolated Solutions

If you attempt to simulate a circuit that does not have isolated solutions, the simulator usually fails with an obscure complaint about the matrix or the Jacobian being singular.

Examples:
- Voltages of the subcitcuit can be raised or lowered by any amounts.
- loop of ideal inductors.
