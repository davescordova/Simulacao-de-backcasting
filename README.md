# Comparative Backcasting Analysis of the Gini Index (1872-2022)

[![Python 3.12+](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Julia 1.10+](https://img.shields.io/badge/Julia-1.10+-purple.svg)](https://julialang.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 1. Overview

This project is an econometric simulation that compares the performance of multiple statistical and machine learning models on a **backcasting** task.

The complete pipeline is contained in the *Simulação.ipynb* notebook, which executes the following steps:
1.  **Simulates** a 151-year time series (1872-2022) for the Gini Index and covariates (GDP, Urbanization, etc.), featuring structural regimes and complex trends.
2.  **Splits** the data into a "Modern" period (1976-2022), simulating data availability (e.g., from national surveys like PNAD), and a "Historical" period (1872-1975), which serves as the ground truth.
3.  **Trains** six different classes of models *exclusively* on the modern data.
4.  **Uses** these models to "backcast" the historical period.
5.  **Compares** the projections against the ground truth to determine which model best captures the long-term dynamics, even with limited information.

## 2. Models Compared

The pipeline trains, evaluates, and compares the following models:

1.  **Linear Regression (OLS)**: The baseline model, assuming linear and stable relationships.
2.  **Markov-Switching Regression (MSR)**: An econometric model that allows coefficients and variance to change according to hidden "states" (regimes).
3.  **Generalized Additive Models (GAMs)**: An interpretable machine learning model that captures complex non-linear relationships using *splines*.
4.  **Structural Time Series Model (UCM)**: A model that decomposes the series into trend, cycle, and seasonality, and uses the learned dynamics for backcasting (by inverting the series).
5.  **Hierarchical Bayesian Model**: A probabilistic model (`PyMC`) that includes a random walk trend to capture long-term stochastic movements.
6.  **Quantum Optimization (QAOA)**: A proof-of-concept model that uses the Quantum Approximate Optimization Algorithm (QAOA) to *solve* the linear regression problem, demonstrating a hybrid quantum-classical optimization approach.
7.  **Gradient Boosted Trees (YDF/TF-DF/XGBoost)**: A machine learning model based on *boosting*, which sequentially builds trees to correct previous errors, known for high performance. (Implemented via YDF/TF-DF).
8.  **Random Forest (YDF/TF-DF/Sklearn)**: A machine learning model based on *bagging*, which builds multiple independent decision trees and combines their predictions for robustness. (Implemented via YDF/TF-DF).
9.  **Vector Autoregression Moving-Average with Exogenous Regressors (VARMAX)**: An econometric model for multiple time series that captures interdependencies and influences from external variables (adapted for univariate backcasting with exogenous variables).

## 3. How to Run

This project was developed in Python 3.12+ in a WSL (Ubuntu) environment.

## 4. Bonus

The *Simulação - Bayesiana(Julia).ipynb* notebook contains the backcasting simulation for the **Hierarchical Bayesian Model**, for the purpose of runtime benchmarking. It does not need to be run in WSL.


