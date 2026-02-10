# Day 03 — Multi-Fidelity Gaussian Processes (MFGP) & Model Calibration

This folder contains the materials for **Day 03** of VITAL Training School 02 (Sahli Costabal & Peirlinck session).
The goal is to get hands-on with **multi-fidelity Gaussian process modelling**, **Bayesian optimization**, and **parameter tuning** in a physiological modelling context.

We will 
- Cover the idea of **multi-fidelity surrogate modelling** and why it helps when high-fidelity evaluations are expensive.
- Fit a **multi-fidelity GP** and use it for **Bayesian optimization** (BoTorch / GPyTorch stack).
- Calibrate model parameters by defining a **misfit / objective function** and running an optimization loop.
- Interpret posterior uncertainty and use it for decision making (e.g., exploration vs exploitation).

---

## Repository contents (this folder)

### Slides / lecture notes
`Lecture1_MFGP.html`  and `Lecture1_MFGP.pdf` covering:
  - GP basics and uncertainty
  - Multi-fidelity GP structure (BoTorch)
  - Expected improvement and multi-fidelity acquisition logic
  - Practice blocks and final assignment

### Practice notebooks
- `vital26TS02_botorch_multifidelity_1d.ipynb`  
  Warm-up: multi-fidelity GP on a 1D function (kernel structure, training, querying, EI).
- `vital26TS02_circulatory_model_tuning.ipynb`  
  Applied: tuning parameters in a circulatory model using the above methodology.

### Final assignment
- `vital26TS02_pulse_wave_tutorial.ipynb`  
  You will complete this notebook. A reference solution will be provided later.

---

## Setup

## Option A - Run online through colab (recommended)
[COLAB NOTEBOOK 1](https://colab.research.google.com/github/VITAL-horizoneurope/trainingschool02/blob/main/Day03_SahliCostabal_Peirlinck/vital26TS02_botorch_multifidelity_1d.ipynb)  
[COLAB NOTEBOOK 2](https://colab.research.google.com/github/VITAL-horizoneurope/trainingschool02/blob/main/Day03_SahliCostabal_Peirlinck/vital26TS02_circulatory_model_tuning.ipynb)  
[COLAB NOTEBOOK 3](https://colab.research.google.com/github/VITAL-horizoneurope/trainingschool02/blob/main/Day03_SahliCostabal_Peirlinck/vital26TS02_pulse_wave_tutorial.ipynb)

### Option B — Run locally after creating a local enviroment
Our virtual environment was Python 3.12 with pip install botorch
