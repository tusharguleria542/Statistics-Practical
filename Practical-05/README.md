# Practical 5: Empirical Probability & Two-Tailed Z-Test Hypothesis Testing

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv` (463 Records)

## Overview

This practical computes empirical probabilities from the `TeachingRatings.csv` dataset and conducts a two-tailed normal distribution hypothesis test (Z-test) using **Pandas**, **NumPy**, and **SciPy** (`scipy.stats`).

## Questions & Key Findings

### Q1. Probability of Receiving an Evaluation Score Greater Than `4.5`
- **Method:** Computed the empirical proportion directly from the dataset via `(df['eval'] > 4.5).mean()`.
- **Count:** `79` out of `463` observations exceed `4.5`.
- **Result:** $P(\text{eval} > 4.5) \approx 0.1706$ (**`17.06%`**)

### Q2. Probability of Receiving an Evaluation Score Between `3.5` and `4.2`
- **Method:** Applied a strict boolean range filter `((df['eval'] > 3.5) & (df['eval'] < 4.2)).mean()`.
- **Count:** `164` out of `463` observations fall strictly within $(3.5, 4.2)$.
- **Result:** $P(3.5 < \text{eval} < 4.2) \approx 0.3542$ (**`35.42%`**)

### Q3. Two-Tailed Hypothesis Test (Normal Distribution Z-Test)
Comparing the scoring average of regional basketball players against the historic professional team average:

- **Hypotheses:**
  - **Null Hypothesis ($H_0$):** The mean points per game of regional players is not different from the historic pro mean ($\mu = 12$).
  - **Alternative Hypothesis ($H_a$):** The mean points per game of regional players is different from the historic pro mean ($\mu \neq 12$).
- **Given Parameters:**
  - Historic Mean ($\mu$): `12`
  - Population Standard Deviation ($\sigma$): `5.5`
  - Sample Size ($n$): `36`
  - Sample Mean ($\bar{x}$): `10.7`
  - Significance Level ($\alpha$): `0.05`
- **Calculations & Results:**
  - **Z-Score:** $z = \frac{10.7 - 12}{5.5 / \sqrt{36}} = \mathbf{-1.4182}$
  - **Two-Tailed p-value:** $2 \times \text{sf}(\vert{}-1.4182\vert{}) = \mathbf{0.1561}$
- **Conclusion:** Since $p = 0.1561 > \alpha = 0.05$, we **fail to reject $H_0$**. There is insufficient statistical evidence to conclude that the regional players' average score differs from the professional historic mean of `12` points per game.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `scipy`

```bash
pip install pandas numpy scipy
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/).
2. Upload `TeachingRatings.csv` to the `/content/` directory.
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-05"
   ```
2. Update the CSV path in `pd.read_csv()` if `TeachingRatings.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.
