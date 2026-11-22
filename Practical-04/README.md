# Practical 4: Duplicate Handling & Multivariate Visualization on Teaching Ratings

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv` (463 Course Observations across 94 Unique Instructors)

## Overview

This practical examines course-level vs. instructor-level aggregation and multivariate relationships in the `TeachingRatings.csv` dataset using **Pandas**, **Matplotlib**, and **Seaborn**. It covers duplicate identification, group-wise bar charts, linear regression scatter plots, and faceted multivariate visualizations.

## Questions & Key Findings

### Q1. Duplicate Instructor Identification & Age Comparison
- **Duplicate Rows:** `456` out of `463` rows belong to professors teaching multiple courses (`df.duplicated(subset=["prof"], keep=False)`).
- **Filtering:** Using `df.drop_duplicates(subset=["prof"])` reduces the dataset from `463` course rows to `94` unique instructors.

| Dataset Scope | Observations ($N$) | Mean Age | Std Dev |
| :--- | :---: | :---: | :---: |
| **All Courses** | 463 | `48.37` | `9.80` |
| **Unique Instructors** | 94 | `47.55` | `10.26` |

- **Finding:** The course-level average age (`48.37`) is slightly higher than the unique instructor average (`47.55`) because older professors teach slightly more courses on average and are counted multiple times at the course level.

### Q2. Average Teaching Evaluation by Course Division
- Grouped by `division` (`df.groupby("division")["eval"].mean()`) and plotted via `sns.barplot()`:
  - **Lower-Division Courses:** `4.09 / 5.00`
  - **Upper-Division Courses:** `3.95 / 5.00`
- **Finding:** Yes, instructors teaching lower-division courses receive slightly higher average teaching evaluations than those teaching upper-division courses.

### Q3. Relationship Between Age and Teaching Evaluation Scores
- Plotted `age` vs. `eval` using `sns.scatterplot()` overlaid with a linear regression line (`sns.regplot(scatter=False)`).
- **Finding:** The regression line slopes slightly downward, indicating a **weak negative relationship**—older instructors tend to receive slightly lower evaluation scores than younger instructors.

### Q4. Gender-Differentiated Scatter Plot (`age` vs. `eval`)
- Color-coded the scatter plot by `gender` (`hue="gender"`, `female`: orange, `male`: blue).
- **Finding:** Across most age groups, male instructors' scores cluster slightly higher than female instructors' scores.

### Q5. Multivariate Scatter Plot (`age` vs. `eval` by Gender & Tenure)
- Built a two-panel grid with `sns.FacetGrid(df, col="gender", hue="tenure")` (`yes`: navy, `no`: crimson).
- **Findings:**
  - Non-tenured instructors (`no`) are concentrated at younger ages (`< 50` years).
  - Tenured instructors (`yes`) span the full age range up to `70+` years.
  - Male tenured instructors maintain consistent ratings across broad age spans, whereas female ratings show slightly lower clusters overall.

## Prerequisites

- Python 3.x
- `pandas`
- `matplotlib`
- `seaborn`

```bash
pip install pandas matplotlib seaborn
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
   cd "Statistics-Practical/Practical-04"
   ``
2. Update the CSV path in `pd.read_csv()` if `TeachingRatings.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code.
