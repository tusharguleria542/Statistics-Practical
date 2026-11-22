# Practical 11: Gamma Distribution Modeling & Metropolis-Hastings MCMC on Solar Sunspot Data

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** SILSO Monthly Mean Total Sunspot Number (`SN_m_tot_V2.0.csv`, Jan 1749 – Nov 2018, `3,239` observations)

## Overview

This practical models historical solar sunspot cycles using a **Gamma probability distribution** and performs Bayesian parameter estimation via a **Metropolis-Hastings Markov Chain Monte Carlo (MCMC)** sampler in Python using **Pandas**, **NumPy**, **Matplotlib**, and **SciPy** (`scipy.stats.gamma`, `scipy.special.gammaln`)[cite: 59, 61, 66].

## Workflow & Key Findings

### 1. Time-Series Visualization & Exploratory Summary
- Loaded the official SILSO monthly sunspot dataset (`3,239` monthly observations from `1749-01-01` to `2018-11-01`)[cite: 59, 60].
- **Summary Statistics (`sunspot_number`):**
  - **Minimum:** `0.0`[cite: 65]
  - **Maximum:** `398.2`[cite: 65]
  - **Mean:** `82.39`[cite: 65]
  - **Median:** `68.3`[cite: 65]
- **Distribution Shape:** The histogram (`bins=30`) reveals a strong right-skewed distribution, justifying the use of a Gamma model[cite: 64, 65].

### 2. Cycle-Wise Gamma Distribution Fitting (12-Year Reset)
- Partitioned observations into `23` cycles resetting every `12` years ($\text{cycle} = \lfloor(\text{year} - 1749)/12\rfloor + 1$) and fitted `scipy.stats.gamma.fit(..., floc=0)` on strictly positive counts[cite: 61, 63].
- **First 12-Year Cycle (1749–1760):**
  - **Shape Parameter ($a$):** `1.968`[cite: 63]
  - **Scale Parameter ($b$):** `37.431`[cite: 63]

### 3. Metropolis-Hastings MCMC Parameter Estimation
- **Setup:** Initialized at $a = 4$, $b = 10$ in log-parameter space with Gaussian proposal steps ($\sigma = 0.08$) and ran `5,000` iterations (`504` accepted proposals; `10.08%` acceptance rate)[cite: 66, 67].
- **Trace Comparison:** Plotted **First 50 Samples** (transient movement from initial values), **All 5,000 Samples**, and **Last 50 Samples** (stationary mixing)[cite: 66, 68].
- **Burn-in Removal:** Discarded the first `1,000` transient samples, retaining `4,000` stationary posterior samples for inference[cite: 68, 69].

### 4. Posterior Parameter Estimates & Simulation
Computed point estimates and uncertainty from the `4,000` post-burn-in MCMC samples and simulated synthetic sunspot counts via `gamma.rvs()`[cite: 69, 71]:

| Parameter | Posterior Mean | Posterior Median | Posterior Std Dev |
| :--- | :---: | :---: | :---: |
| **Shape ($a$)** | `1.1731` | `1.1716` | `0.0272` |
| **Scale ($b$)** | `71.7015` | `71.5911` | `1.9654` |

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `scipy`

```bash
pip install pandas numpy matplotlib scipy
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)[cite: 59].
2. Ensure an internet connection is active so `pd.read_csv()` can fetch the live dataset directly from SILSO (`https://www.sidc.be/SILSO/DATA/SN_m_tot_V2.0.csv`)[cite: 59].
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-11"
   ```
2. Run the notebook in Jupyter Notebook or VS Code.
