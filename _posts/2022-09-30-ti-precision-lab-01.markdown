---
title:  "TI Precision Lab 01"
date:   2022-09-30 19:30:00 +0200
categories: analog-circuit
tags: analog
math: true
---

## 2.1 Vos and Ib

### Input Offset Voltage

- changing supply voltage or common mode voltage will affect Vos.
- Vos is typically caused by mismatch between the differential input pair.
- the tail resistor mismatch can be minimized by laser trimmed resistor.
- e.g., at TA=25, RL=10k, VCM = VOUT = midsupply.
- e.g., Vs = $$\pm$$15V, VCM=0V
- TYP = 75uV, MAX = 150uV.
- where TYP means $$\pm \sigma$$=75uV, corresponding to 68% probability.
- you will never find one device exceed MAX.

### Input Bias CCCurrent, Input Offset Current

- bipolar base current.
- for CMOS it is due to leakage of input ESD protection diodes.
