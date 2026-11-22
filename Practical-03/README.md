# Practical 3: Statistical Analysis & Data Visualization on Student Ratings

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `evals.csv` (Student Rating Dataset)

## Overview

This practical explores demographic trends, tenure status, age distributions, and evaluation scores in the `evals.csv` dataset using **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**.

## Questions & Key Findings

### Q1. Tenure Percentage Among Visible Minority Professors
- **Total Minority Professors:** `64`
- **Tenured Minority Professors:** `26`
- **Percentage Tenured:** `40.625%` (`40.63%`)
- **Comparison:** Overall, `253` out of `463` professors (`54.64%`) in the dataset hold tenure, whereas only `40.63%` of visible minority professors are tenured. This indicates a noticeable disparity in tenure status for visible minority instructors.

### Q2. Average Age by Tenure Status
Grouped instructors into **Tenured** (`rank == "tenured"`) and **Untenured** (`rank != "tenured"`):

| Tenure Status | Count | Mean Age | Std Dev |
| :--- | :---: | :---: | :---: |
| **Tenured** | 253 | `51.89` | `8.65` |
| **Untenured** | 210 | `44.12` | `9.43` |

- **Finding:** Yes, average age differs substantially by tenure status—tenured professors are on average ~7.77 years older (`51.89` vs. `44.12` years).

### Q3. Best Graph for the `age` Variable
- **Graph Choice:** A **Histogram** (`plt.hist(df["age"], bins=10)`) works best because `age` is a continuous numerical variable, and binning shows its frequency distribution, spread (`29` to `73` years), and central clustering clearly.

### Q4. `pyplot.bar()` vs. `pyplot.barh()` & Gender Distribution
- **Difference:**
  - `pyplot.bar(x, height)` plots **vertical bars** (categories along the horizontal X-axis and values along the vertical Y-axis).
  - `pyplot.barh(y, width)` plots **horizontal bars** (categories along the vertical Y-axis and values along the horizontal X-axis), which is especially useful when category labels are long.
- **Gender Distribution:** Plotted using `plt.bar()` on `df["gender"].value_counts()` (`male`: 268, `female`: 195).

### Q5. Median Evaluation Score for Tenured Professors
- Filtered for `df["rank"] == "tenured"` and computed `.median()` on the `score` column.
- **Median Evaluation Score:** `4.2`

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

```bash
pip install pandas numpy matplotlib seaborn
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/).
2. Upload `evals.csv` to the `/content/` directory.
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-03"
   ```
2. Update the CSV path in `pd.read_csv()` if `evals.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.
