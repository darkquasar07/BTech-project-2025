# GaN HEMTs — Small‑Signal Characterization (Empirical vs Data‑Driven)

## Overview

This project delivers a rigorous, comparison between two complementary approaches for small‑signal modeling of GaN HEMTs:

* **Empirical equivalent‑circuit modeling**, parameterized RLC networks fitted to measured S‑parameters, providing physical insight and circuit‑level interpretability.
* **Data‑driven modeling**, feature‑engineered feedforward ANNs that directly predict the real and imaginary parts of S‑parameters across frequency and bias.

We trained both approaches on high‑quality experimental datasets under two bias regimes
1. **Vd = 10 V, Vg sweep**, and
2.  **Vg = −4 V, Vd sweep**.
   
A parallel DC track (Id–Vg and Id–Vd) was also developed and compared. The ANN models consistently improved prediction accuracy (up to **~50% MRE reduction** on key metrics such as Re(S21)), reduced inference latency to **<0.1 s/sample**, and generalized better to unseen bias points, while empirical models retained interpretability and physics guarantees.

This repository contains data preprocessing, model training/evaluation code, plotting tools (Smith charts, |S| dB plots, three‑way experimental/ ANN/ empirical comparisons), and scripts to reproduce DC surrogate predictions and circuit simulations (Keysight ADS / Verilog‑A integration).

---

## Features

* **Dual‑track comparison:**
  Side-by-side empirical RLC circuit extraction and Artificial Neural Network (ANN) surrogates for Radio Frequency (RF) S‑parameters and DC drain current (Id) curves.
* **Clean preprocessing pipeline:**
  Outlier filtering, noise‑floor trimming, and persistent input/output scalers for deterministic inference.
* **Second‑order feature expansion:**
  Automatic polynomial feature generation including squared terms and pairwise cross‑terms of frequency, gate‑source voltage, and drain‑source voltage to expose nonlinear interactions.
* **Compact, robust neural network:**
  Four hidden layers with neuron counts 64–128–128–64, Swish activation functions, dropout regularization, Huber loss, and Adam optimizer with learning‑rate scheduling, tuned to generalize across bias conditions.
* **Complex‑valued targets (dual output):**
  Networks predict the real and imaginary components simultaneously for each S‑parameter, enabling direct comparison with circuit models and loss evaluation in complex space.
* **Direct‑current surrogate tooling:**
  Matrix‑aware functions for drain‑current versus gate‑voltage and drain‑current versus drain‑voltage prediction that parse experimental CSV layouts and generate quality plots on demand.
* **Reproducible benchmarking:**
  Scripts to compute mean relative error, mean absolute error, mean squared error, and runtime comparisons between the neural surrogate and the empirical extraction method; model weights, scalers, and fitted circuit parameters are exportable.
* **Simulation‑ready outputs:**
  Fitted circuit parameter files and comparison figures prepared for use in Keysight Advanced Design System and Verilog‑A simulation environments.

---

## Related Documentation

For a detailed overview and in-depth explanation of the models, you can view the following resources:
1. [BTP Presentation](https://drive.google.com/file/d/1C1PAATdcTBksBtKoBzIhBrAg5QczZynL/view?usp=sharing)
2. [BTP Report](https://drive.google.com/file/d/1vXS2TYchrgJ4mExlHJeLDfA37pPORlVX/view?usp=sharing)

---
