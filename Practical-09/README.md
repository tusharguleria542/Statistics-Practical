# Practical 9: K-Nearest Neighbors (KNN) Classification on the Iris Dataset

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** Iris Dataset (`sklearn.datasets.load_iris`, `150` records, `4` features)

## Overview

This practical implements a **K-Nearest Neighbors (KNN)** classifier on the Iris dataset using **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**, and **Scikit-learn**[cite: 46]. It covers exploratory data analysis, feature standardization, baseline training ($K=5$), hyperparameter tuning across $K \in [1, 39]$, and 2D PCA decision boundary visualization[cite: 46, 47, 48, 50].

## Workflow & Key Findings

### 1. Exploratory Data Analysis (EDA)
- **Dataset Dimensions:** `150` samples across `3` balanced species (`setosa`, `versicolor`, `virginica` — `50` each)[cite: 46, 47].
- **Groupby Species Means:**

| Species | Sepal Length (cm) | Sepal Width (cm) | Petal Length (cm) | Petal Width (cm) |
| :--- | :---: | :---: | :---: | :---: |
| **Setosa** | `5.006` | `3.428` | `1.462` | `0.246` |
| **Versicolor** | `5.936` | `2.770` | `4.260` | `1.326` |
| **Virginica** | `6.588` | `2.974` | `5.552` | `2.026` |

### 2. Preprocessing & Feature Scaling
- Split into **80% training (`120` samples)** and **20% testing (`30` samples)** using `train_test_split(..., test_size=0.20, random_state=42)`[cite: 47, 48].
- Standardized features via `StandardScaler()` so distance calculations treat all four measurements on an equal scale[cite: 47].

### 3. Baseline Model Evaluation ($K = 5$)
- **Test Accuracy:** `100.00%` (`30 / 30` correctly classified)[cite: 48]
- **Confusion Matrix:**
  ```text
  [[10  0  0]
   [ 0  9  0]
   [ 0  0 11]]
  ```
- **Classification Report:** Achieved `1.00` precision, `1.00` recall, and `1.00` F1-score across all three species[cite: 48].

### 4. Hyperparameter Tuning ($K = 1$ to $39$) & PCA Visualization
- **Error Rate Analysis:** Evaluated test error rates for $K$ from `1` to `39`[cite: 48, 49]. Error remained `0.0000` for $K \in [1, 25]$ and $K = 27$, rising slightly for larger neighborhoods ($K \ge 26$)[cite: 49].
- **Optimal $K$:** Selected **`K = 1`** (`error rate = 0.0000`) as the first minimum-error neighbor count[cite: 49, 50].
- **2D PCA Decision Boundaries:** Reduced the 4D standardized feature space to 2 principal components (`PCA(n_components=2)`) to plot class decision boundaries and test set predictions[cite: 50, 51].

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
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)[cite: 46].
2. No external CSV upload is required—the dataset loads directly via `sklearn.datasets.load_iris()`[cite: 46].
3. Run all cells (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-09"
   ```
2. Run the notebook in Jupyter Notebook or VS Code.
