# Practical 10: Exploratory Analysis, Covariance & PCA on the Wine Dataset

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** Wine Dataset (`sklearn.datasets.load_wine`, `178` samples, `13` chemical features, `3` wine classes)

## Overview

This practical explores feature distributions, covariance structure, standardization, and dimensionality reduction via **Principal Component Analysis (PCA)** on the Wine dataset using **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**, and **Scikit-learn**[cite: 53, 55, 56, 57].

## Workflow & Key Findings

### 1. Basic Statistical Summary (`df.describe()`)
- Inspected count (`178` samples), mean, standard deviation, and quartiles across all `13` chemical attributes[cite: 53, 54, 57].
- Features vary significantly in scale—for example, `nonflavanoid_phenols` averages `0.36` ($\text{SD} = 0.12$), whereas `proline` ranges up to `1680` with high variance ($\text{SD} \approx 314.9$, variance `99,166.7`)[cite: 54, 56].

### 2. Class-Wise Boxplot (`alcohol` by `target`)
- Plotted `sns.boxplot(x='target', y='alcohol', data=df)` across wine classes `0`, `1`, and `2`[cite: 54].
- **Finding:** Class `0` exhibits the highest median alcohol content (`~13.75%`), Class `2` sits in the middle (`~13.15%`), and Class `1` has the lowest median (`~12.3%`) with a few upper outliers[cite: 54].

### 3. Bivariate Scatter Plot (`alcohol` vs. `flavanoids`)
- Plotted `sns.scatterplot(x='alcohol', y='flavanoids', hue='target', palette='Set1')`[cite: 55].
- **Finding:** Shows partial clustering among the three wine classes, though some overlap remains when relying on only two raw variables[cite: 55, 57].

### 4. Covariance Matrix Heatmap
- Computed `df.drop('target', axis=1).cov()` and visualized it with `sns.heatmap(..., annot=True, fmt='.1f', cmap='coolwarm')`[cite: 55].
- **Finding:** Because raw features are unscaled, `proline` (`99,166.7`) and `magnesium` (`204.0`) dominate the covariance matrix, highlighting the necessity of feature scaling before PCA[cite: 56].

### 5. Feature Standardization (`StandardScaler`)
- Standardized all `13` predictor columns (`X`) using `StandardScaler().fit_transform(X)` so every feature has a mean of `0.00` and a standard deviation of `1.00`[cite: 56, 57].

### 6. Dimensionality Reduction & Class Separation (`PCA`)
- Reduced the `13` standardized features into `2` principal components (`PC1` and `PC2`) via `PCA(n_components=2)`[cite: 57].
- **Explained Variance:** `PC1` captures roughly `36%` and `PC2` captures roughly `19%` of the total variance (`~55%` combined)[cite: 57].
- **Finding:** Plotting `PC1` vs. `PC2` produces three distinct, well-separated clusters for wine classes `0`, `1`, and `2`—demonstrating substantially cleaner class separation than raw two-variable scatter plots[cite: 57, 58].

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)[cite: 53].
2. No external CSV upload is required—the dataset loads directly via `sklearn.datasets.load_wine()`[cite: 53].
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-10"
   ```
2. Run the notebook in Jupyter Notebook or VS Code.
