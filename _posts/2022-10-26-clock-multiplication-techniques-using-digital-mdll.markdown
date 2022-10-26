---
title:  "Paper Clock Multiplication Techniques Using Digitial Multiplying Delay-Locked-Loops"
date:   2022-10-26 16:40:00 +0200
categories: analog-circuit
tags: pll
math: true
---

From [Amr Elshazly's Paper](https://ieeexplore.ieee.org/document/6515347)

## Introduction

A classical digital PLL composed of TDC, digital loop filter (DLF) and DCO (possibly DAC followed by VCO).

Digital Multiplying DLL is different from classical digital PLL, in terms of noise transfers and many other things.

## Overview of Multiplying Delay-Locked Loops

Unlike classical PLLs, MDLLs in a sense remove jitter accumulation by edge realignment.
[Sheng Ye's paper](https://ieeexplore.ieee.org/document/1088109) shows edge relaignment can effectively remove phase noise up to about $$2 \omega_{loop}$$ instead of $$\omega_{loop}$$ by high-pass filtering.
