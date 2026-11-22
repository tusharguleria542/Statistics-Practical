# Practical 2: Exploratory Data Analysis on Teaching Ratings

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv` (Ratings of Professors at Top USA Universities)

## Overview

This practical performs Exploratory Data Analysis (EDA) and statistical testing on the `TeachingRatings.csv` dataset using **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**, and **SciPy**. It covers data classification, summary statistics, distribution visualization, group-wise comparisons, and a Chi-square test for independence.

## Questions & Key Findings

### Q1. Time-Series vs. Cross-Sectional Data
- **Answer:** The dataset is **cross-sectional data**.
- **Reason:** It captures observations across 463 distinct instructors and courses at a single point in time rather than tracking sequential, chronological measurements of the same subjects over regular time intervals.

### Q2. Summary Statistics for `students`
Calculated using `.mean()`, `.median()`, `.min()`, and `.max()`:
- **Mean:** `36.62`
- **Median:** `23.00`
- **Minimum:** `5`
- **Maximum:** `380`

### Q3. Descriptive Statistics Table
Generated using `df.describe()` across all 463 records (`age`, `beauty`, `eval`, `students`, `allstudents`):

| Statistic | age | beauty | eval | students | allstudents |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Count** | 463 | 463 | 463 | 463 | 463 |
| **Mean** | 48.37 | 0.00 | 4.00 | 36.62 | 55.18 |
| **Std** | 9.80 | 0.79 | 0.55 | 45.02 | 75.07 |
| **Min** | 29.00 | -1.45 | 2.10 | 5.00 | 8.00 |
| **50% (Median)** | 48.00 | -0.07 | 4.00 | 23.00 | 29.00 |
| **Max** | 73.00 | 1.97 | 5.00 | 380.00 | 581.00 |

### Q4. Histogram of the `beauty` Variable
- Plotted using `sns.histplot(df["beauty"], kde=True, bins=15)`.
- **Distribution:** The beauty scores are centered near `0` (ranging from `-1.45` to `1.97`) and show a slight **right (positive) skew**, with the highest concentration of scores between `-0.7` and `0.2`.

### Q5. Average Beauty Score by Gender
Grouped via `df.groupby("gender")["beauty"].agg(["count", "mean", "std"])`:

| Gender | Count | Mean | Std Dev |
| :--- | :---: | :---: | :---: |
| **Female** | 195 | `0.1161` | `0.8178` |
| **Male** | 268 | `-0.0845` | `0.7571` |

- Female instructors have a slightly higher average beauty score (`0.1161`) than male instructors (`-0.0845`).

### Q6. Tenure Status by Gender & Chi-Square Test
Calculated using `pd.crosstab(..., normalize="index") * 100` and `scipy.stats.chi2_contingency`:

| Gender | Tenured (`yes`) | Non-Tenured (`no`) |
| :--- | :---: | :---: |
| **Female** | `74.36%` | `25.64%` |
| **Male** | `80.60%` | `19.40%` |

- **Chi-square p-value:** `0.1374`
- **Conclusion:** Although a slightly higher percentage of male instructors are tenured (`80.60%` vs. `74.36%`), the p-value (`0.1374 > 0.05`) indicates that the difference is **not statistically significant**.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scipy`

Install dependencies locally if running outside Google Colab:
```bash
pip install pandas numpy matplotlib seaborn scipy
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/).
2. Upload `TeachingRatings.csv` to the Colab session storage.
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-02"
   ```
2. Ensure `TeachingRatings.csv` is in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.Notebook or VS Code.
