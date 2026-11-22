# Practical 12: Metropolis MCMC Sampling & Deterministic Logistic Growth Model

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)

## Overview

This practical contrasts stochastic sampling and deterministic modeling in Python using **NumPy**, **Matplotlib**, and **SciPy**[cite: 72, 75]. **Part A** implements the **Metropolis Algorithm** (MCMC) to sample from a standard normal distribution[cite: 72, 75], while **Part B** simulates a **Deterministic Logistic Growth Model** using Euler's Method[cite: 75, 76].

## Parts & Key Findings

### Part A: Implementation of the Metropolis Algorithm (Stochastic MCMC)
- **Aim:** Generate random samples from a target probability distribution ($\mathcal{N}(0, 1)$) using the Metropolis Algorithm[cite: 72, 75].
- **Configuration:**
  - **Target Distribution:** Standard Normal PDF (`norm.pdf(x, loc=0, scale=1)`)[cite: 72, 73]
  - **Iterations:** `1,000`[cite: 73]
  - **Initial Value:** `0`[cite: 73]
  - **Proposal Standard Deviation:** `1`[cite: 73]
- **Result & Visualization:**
  - Achieved an **acceptance rate of `0.703` (`70.3%`)**[cite: 73].
  - Plotted a normalized histogram (`bins=50`) of generated samples overlaid against the analytical standard normal PDF curve, confirming that the empirical sample distribution closely follows $\mathcal{N}(0, 1)$[cite: 73, 74, 75].

### Part B: Deterministic Logistic Growth Model
- **Aim:** Simulate and visualize population growth under carrying-capacity constraints over time[cite: 75].
- **Governing Differential Equation & Euler Discretization:**
  $$\frac{dP}{dt} = rP\left(1 - \frac{P}{K}\right), \qquad P_{\text{next}} = P_{\text{current}} + \Delta t \cdot rP\left(1 - \frac{P}{K}\right)$$[cite: 75, 76]
- **Model Parameters:**
  - **Growth Rate ($r$):** `0.2`[cite: 75, 76]
  - **Carrying Capacity ($K$):** `1,000`[cite: 76]
  - **Initial Population ($P_0$):** `50`[cite: 76]
  - **Time Horizon:** $t \in [0, 50]$ across `200` evenly spaced steps[cite: 76]
- **Result & Visualization:**
  - Simulated population rises in an S-shaped (sigmoid) trajectory and converges toward the carrying capacity ceiling, reaching a **final population of `999.22`** at $t = 50$[cite: 76, 77, 78].

## Prerequisites

- Python 3.x
- `numpy`
- `matplotlib`
- `scipy`

```bash
pip install numpy matplotlib scipy
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)[cite: 72].
2. No external dataset upload is required—both simulations run self-contained in Python[cite: 72, 73, 75, 76].
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-12"
   ```
2. Run the notebook in Jupyter Notebook or VS Code.
