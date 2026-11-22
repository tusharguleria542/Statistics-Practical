# Practical 7: Regression Analysis (OLS & ANOVA) on Teaching Ratings

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv` (463 Observations)

## Overview

This practical implements Ordinary Least Squares (OLS) regression and formula-based ANOVA modeling on the `TeachingRatings.csv` dataset using **Pandas** and **Statsmodels** (`statsmodels.api`, `statsmodels.formula.api.ols`, and `statsmodels.stats.anova`).

## Questions & Key Findings

| Question | Model / Method | Variables | Key Statistic | p-value | Conclusion ($\alpha = 0.05$) |
| :--- | :--- | :--- | :---: | :---: | :--- |
| **Q1** | OLS Regression with Dummy Variable | `eval ~ female` | $t = -3.250$, $\beta_1 = -0.1680$ | `0.00124` | **Significant** ($p < 0.05$) |
| **Q2** | Formula OLS + ANOVA (`anova_lm`) | `beauty ~ C(age_group)` | $F = 17.5976$ | `4.32e-08` | **Significant** ($p < 0.05$) |
| **Q3** | Simple Linear Regression (OLS) | `eval ~ beauty` | $t = 4.133$, $\beta_1 = 0.1330$ | `4.25e-05` | **Significant** ($p < 0.05$) |

### Q1. Regression with T-Test: Gender vs. Teaching Evaluation
- **Method:** Created a binary dummy variable `female` (`1` for female, `0` for male), added an intercept via `sm.add_constant()`, and fitted `sm.OLS(Y1, X1).fit()`.
- **Regression Equation:** $\widehat{\text{eval}} = 4.0690 - 0.1680(\text{female})$
- **Key Metrics:**
  - **Intercept (`const`):** `4.0690` (average evaluation score for male instructors)
  - **Slope (`female`):** `-0.1680` ($t = -3.250$, $p = 0.001$, $R^2 = 0.022$)
- **Conclusion:** Gender significantly affects teaching evaluation scores; female instructors score on average `0.1680` points lower than male instructors in this dataset.

### Q2. Regression with ANOVA: Beauty Score by Age Group
- **Method:** Categorized `age` into three brackets via `pd.cut(df["age"], bins=[0, 40, 56, 100], labels=["Young", "Middle", "Old"])`, fitted `ols("beauty ~ C(age_group)", data=df).fit()`, and generated an ANOVA table with `anova.anova_lm()`.
- **ANOVA Table Summary:**
  - **`C(age_group)`:** $\text{df} = 2$, $\text{Sum Sq} = 20.4227$, $\text{Mean Sq} = 10.2114$, $F = 17.5976$, $p = 4.32 \times 10^{-8}$
  - **Residual:** $\text{df} = 460$, $\text{Sum Sq} = 266.9252$, $\text{Mean Sq} = 0.5803$
- **Conclusion:** Since $p = 4.32 \times 10^{-8} < 0.05$, beauty scores differ significantly across the three instructor age groups.

### Q3. Linear Regression / Correlation: Evaluation Score vs. Beauty Score
- **Method:** Fitted `sm.OLS(Y3, X3).fit()` with `eval` as the dependent variable and `beauty` (with intercept) as the predictor.
- **Regression Equation:** $\widehat{\text{eval}} = 3.9983 + 0.1330(\text{beauty})$
- **Key Metrics:**
  - **Intercept (`const`):** `3.9983` ($t = 157.727$, $p < 0.001$)
  - **Slope (`beauty`):** `0.1330` ($t = 4.133$, $p = 4.25 \times 10^{-5}$, $R^2 = 0.036$)
- **Conclusion:** Beauty score has a statistically significant positive relationship with teaching evaluation scores.

## Prerequisites

- Python 3.x
- `pandas`
- `statsmodels`

```bash
pip install pandas statsmodels
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
   cd "Statistics-Practical/Practical-07"
   ```
2. Update the CSV path in `pd.read_csv()` if `TeachingRatings.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.
