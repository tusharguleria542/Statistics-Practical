# Practical 8: Decision Tree Classifier (Pima Indians Diabetes)

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** Pima Indians Diabetes Dataset (`768` records, `9` columns)

## Overview

This practical builds, evaluates, and mathematically interprets a **Decision Tree Classifier** (`criterion="entropy"`, `max_depth=3`) using **Pandas**, **NumPy**, **Matplotlib**, and **Scikit-learn** to predict diabetes outcomes (`0`: No Diabetes, `1`: Diabetes)[cite: 36, 37, 38, 39]. It also computes manual **Entropy**, **Information Gain**, and **Gini Index** metrics at the root node and compares candidate splits across features[cite: 42, 43, 44, 45].

## Workflow & Key Findings

### 1. Dataset Exploration & Splitting
- **Shape:** `768` rows $\times$ `9` columns (`8` medical features + binary `Outcome` target)[cite: 37, 38].
- **Class Distribution:** `500` No Diabetes (`0`), `268` Diabetes (`1`)[cite: 38].
- **Train/Test Split:** Stratified 80/20 split (`random_state=42`) yielding `614` training samples and `154` testing samples[cite: 38].

### 2. Model Performance (`max_depth=3`, `criterion="entropy"`)
- **Test Accuracy:** `69.48%` (`0.6948`)[cite: 39]
- **Confusion Matrix:**
  ```text
  [[92  8]
   [39 15]]
  ```
- **Classification Report Summary:**

| Class | Precision | Recall | F1-Score | Support |
| :--- | :---: | :---: | :---: | :---: |
| **No Diabetes (`0`)** | `0.70` | `0.92` | `0.80` | 100 |
| **Diabetes (`1`)** | `0.65` | `0.28` | `0.39` | 54 |
| **Overall Accuracy** | — | — | **`0.69`** | **154** |

### 3. Root Node Impurity & Candidate Split Analysis
- **Root Decision Rule:** `Glucose <= 154.50`[cite: 42]
- **Root Split Metrics:**
  - **Parent Entropy:** `0.9328` $\rightarrow$ **Weighted Child Entropy:** `0.7891` (**Information Gain:** `0.1436`)[cite: 43]
  - **Parent Gini Index:** `0.4541` $\rightarrow$ **Weighted Child Gini Index:** `0.3619` (**Gini Reduction:** `0.0923`)[cite: 43]
- **Top Candidate Root Splits by Information Gain:**

| Feature | Best Threshold | Information Gain |
| :--- | :---: | :---: |
| **Glucose** | `154.5000` | `0.143640` |
| **BMI** | `29.6500` | `0.074059` |
| **Age** | `27.5000` | `0.065433` |

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`

```bash
pip install pandas numpy matplotlib scikit-learn
```

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)[cite: 36].
2. Ensure an internet connection is active so `pd.read_csv()` can fetch the dataset directly from GitHub[cite: 36].
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-08"
   ```
2. Run the notebook in Jupyter Notebook or VS Code.
