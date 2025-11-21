README.md (Expanded & Polished Version)
Hierarchical Bayesian Time Series Forecasting (HBM) — Google Colab Project
Project Overview

This project implements an Advanced Hierarchical Bayesian Model (HBM) for forecasting multiple related time series using PyMC. Hierarchical Bayesian modeling is particularly powerful when:

Several time series share common characteristics

Each individual series has limited data

A pooled statistical structure can improve forecast stability

By leveraging shared hyperparameters, the model borrows strength across all series, resulting in improved accuracy and more realistic uncertainty estimation.

This notebook generates a full synthetic dataset, constructs the hierarchical model, conducts Bayesian inference via MCMC, performs diagnostics, and compares the model to classical forecasting methods.

Objectives

Generate Synthetic Time Series Data

At least 10 interconnected time series

Shared trend & seasonality

Series-specific AR(1) structure

Added noise to simulate real-world behavior

Build a Hierarchical Bayesian AR(1) Model

Shared priors for intercepts, slopes, AR coefficients, and seasonal amplitudes

Captures both global patterns and series-level variations

Performs inference using PyMC’s MCMC samplers

Evaluate Model Performance

Posterior predictive checks

Forecast uncertainty visualization

Diagnostic metrics (trace plots, R-hat) to confirm convergence

Benchmark Against ARIMA

Fit ARIMA(1,0,0) to each series individually

Compute forecasting accuracy using:

MASE (Mean Absolute Scaled Error)

CRPS (Continuous Ranked Probability Score)

Provide Practical Takeaways

When should hierarchical modeling be used?

How much accuracy improvement is observed?

How uncertainty estimates differ from classical models

Files Generated & Used
1. Dataset File

hbm_synthetic.csv
Contains the generated dataset including:

series_id — identifier for each time series

t — time index

y — observed value

Saved automatically in Colab at:

/content/hbm_synthetic.csv

2. Notebook Code

Full Python implementation using:

NumPy, Pandas (data handling)

PyMC (Bayesian modeling)

ArviZ (posterior analysis)

Statsmodels (ARIMA baseline)

Matplotlib (plots)

3. Uploaded Screenshots

Referenced for documentation clarity:

/mnt/data/Screenshot 2025-11-21 102612.png

/mnt/data/Screenshot 2025-11-21 102620.png

Important Compatibility Notes
⚠ Problem

Google Colab currently defaults to Python 3.12, which is incompatible with PyMC 5.x due to recent NumPy changes.

This may trigger:

ModuleNotFoundError: No module named 'numpy.lib.array_utils'

Solution

Install compatible versions of the core libraries:

numpy==1.26.0
pytensor==2.15.0
pymc==5.10.0

Restart Required

After installation, restart the runtime:

Runtime → Restart runtime


Failure to restart will continue using the incompatible preinstalled version.

How to Run This Project (Google Colab)
Step 1 — Open a new notebook

Visit https://colab.research.google.com/

Step 2 — Paste the full project code into the notebook
Step 3 — Run the dependency installation cell

This installs correct versions and removes broken ones.

Step 4 — Restart runtime

Colab:
Runtime → Restart runtime

Step 5 — Run the remaining cells in order

The code will automatically:

Generate dataset
Fit hierarchical Bayesian model
Show diagnostic plots
Perform posterior predictive checks
Compute accuracy metrics
Compare with ARIMA baseline

Output & Evaluation
1. Model Diagnostics

The notebook provides:

Trace plots (confirm Markov chain mixing)

R-hat values (should be ≈1.0 for convergence)

Posterior summaries (means, credible intervals)

Model parameter distributions

These confirm whether the Bayesian sampling is reliable.

2. Forecasting Output

For selected series:

Posterior predictive median

90% uncertainty intervals

Comparison with observed values

3. Benchmark Metrics
Metric	Description	Why It Matters
MASE	Scale-free error measure	Allows comparison across series
CRPS	Measures probabilistic accuracy	Evaluates uncertainty forecasting

HBM generally outperforms ARIMA when data is noisy or limited.
