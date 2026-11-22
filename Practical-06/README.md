# Practical 6: Inferential Hypothesis Testing & Correlation Analysis

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical applies four core statistical inference tests—**Independent T-Test**, **One-Way ANOVA**, **Chi-Square Test of Independence**, and **Pearson Correlation**—on the `TeachingRatings.csv` dataset using **Pandas**, **SciPy** (`scipy.stats`), **Seaborn**, and **Matplotlib**.

## Questions & Key Findings

| Question | Statistical Test | Variables Tested | p-value | Statistical Decision ($\alpha = 0.05$) |
| :--- | :--- | :--- | :---: | :--- |
| **Q1** | Independent Two-Sample T-Test | `gender` vs. `eval` | `0.0012` | **Significant** ($p < 0.05$) |
| **Q2** | One-Way ANOVA | `age_group` vs. `beauty` | `0.0000` | **Significant** ($p < 0.05$) |
| **Q3** | Chi-Square Test of Independence | `tenure` vs. `gender` | `0.1374` | **Not Significant** ($p > 0.05$) |
| **Q4** | Pearson Correlation | `eval` vs. `beauty` | `0.0000` | **Significant** ($p < 0.05$) |

### Q1. Independent T-Test: Does Gender Affect Teaching Evaluation Rates?
- **Method:** Separated `eval` scores for male and female instructors and ran `stats.ttest_ind(male_eval, female_eval)`.
- **Result:** `p-value = 0.0012` ($< 0.05$).
- **Conclusion:** Gender has a statistically significant effect on teaching evaluation scores in this dataset.

### Q2. One-Way ANOVA: Does Beauty Score Differ by Age?
- **Method:** Discretized `age` into three brackets using `pd.cut()`—**Young** (`< 40`), **Mid** (`40–55`), and **Senior** (`> 55`)—and compared group `beauty` scores via `stats.f_oneway(young, mid, senior)`.
- **Result:** `p-value = 0.0000` ($< 0.05$).
- **Conclusion:** Average beauty scores differ significantly across instructor age brackets.

### Q3. Chi-Square Test: Is There an Association Between Tenure and Gender?
- **Method:** Built a $2 \times 2$ contingency table with `pd.crosstab(df['tenure'], df['gender'])` and ran `stats.chi2_contingency()`.
- **Result:** `p-value = 0.1374` ($> 0.05$).
- **Conclusion:** There is no statistically significant association between an instructor's gender and tenure status.

### Q4. Pearson Correlation: Is Evaluation Score Correlated with Beauty Score?
- **Method:** Computed Pearson's $r$ via `stats.pearsonr(df['eval'], df['beauty'])` and visualized pairwise correlations (`eval`, `beauty`, `age`) using `sns.heatmap()`.
- **Result:** Correlation coefficient $r = 0.19$ with `p-value = 0.0000` ($< 0.05$).
- **Conclusion:** There is a statistically significant positive correlation between beauty scores and teaching evaluation scores.

## Prerequisites

- Python 3.x
- `pandas`
- `scipy`
- `seaborn`
- `matplotlib`

```bash
pip install pandas scipy seaborn matplotlib
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
   cd "Statistics-Practical/Practical-06"
   ```
2. Update the CSV path in `pd.read_csv()` if `TeachingRatings.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.
