# GaN-on-Si HEMT Small-Signal Characterization: Empirical vs. Data-Driven Models

## Overview  
This repository contains code for a comprehensive comparison between two approaches to small-signal modeling of GaN-on-Si high-electron-mobility transistors (HEMTs):  
1. **Empirical Equivalent-Circuit Model**  
2. **Data-Driven ANN Model**

The data-driven model is trained and validated on measured S-parameter datasets under two distinct biasing conditions, and it's performance is evaluated in terms of accuracy, extrapolation capability, and inference speed.

---

## Features

- **Polynomial Feature Expansion**  
  Generate second-order combinations of (frequency, V<sub>GS</sub>, V<sub>DS</sub>) as network inputs.

- **Dual-Output ANN**  
  Simultaneously predicts real & imaginary components for all S-parameters.

- **High Accuracy & Speed**  
  - Up to 50 % reduction in mean relative error (MRE) compared to empirical models.  
  - Inference in under 0.1 s per sample.

- **Biasing Datasets**  
  1. Fixed V<sub>D</sub>=10 V, varying V<sub>G</sub>  
  2. Fixed V<sub>G</sub>=–4 V, varying V<sub>D</sub>

- **Evaluation Metrics**  
  MRE, MAE, and MSE on held-out test sets.

---
