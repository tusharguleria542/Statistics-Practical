# Practical 1: Revisiting Pandas and NumPy

**Author:** Tushar Guleria  
**Registration / ID:** GF202459441  
**Environment:** Google Colab (Python 3)  
**Dataset:** `StudentsPerformance.csv`

---

## Overview

This practical revisits core **Pandas** and **NumPy** workflows commonly used in data preprocessing and linear algebra operations. Using the `StudentsPerformance.csv` dataset, the notebook demonstrates loading tabular data, inspecting array properties, performing matrix arithmetic, and encoding categorical features for machine learning pipelines.

---


## Objectives & Steps Covered

### Step 1: Loading Raw Data into a Pandas DataFrame
- Loaded `StudentsPerformance.csv` using `pd.read_csv()`.
- Selected key columns (`gender`, `parental level of education`, `math score`, and `reading score`) and previewed the first 5 rows with `.head()`.

### Step 2: NumPy Array Creation & Properties
- Extracted a $2 \times 2$ numerical matrix (`matrix_a`) from the `math score` and `reading score` of the first two students using `.head(2).to_numpy()`.
- Inspected core array attributes:
  - **Shape:** `(2, 2)`
  - **Size:** `4`
  - **Dimensions (`ndim`):** `2`
- **Why a $2 \times 2$ square matrix?**
  1. Matrix inversion (`np.linalg.inv()`) is only defined for square matrices; a non-square shape throws a `LinAlgError`.
  2. Matching square dimensions ensure element-wise operations and matrix multiplication (dot product) execute cleanly without dimension mismatches.

### Step 3: Matrix Operations with NumPy
- Extracted a second $2 \times 2$ matrix (`matrix_b`) from students 3 and 4 using `.iloc[2:4].to_numpy()`.
- Performed the following operations:
  - **Addition:** `matrix_a + matrix_b`
  - **Subtraction:** `matrix_a - matrix_b`
  - **Element-wise Multiplication:** `matrix_a * matrix_b`
  - **Dot Product (Matrix Multiplication):** `np.dot(matrix_a, matrix_b)`
  - **Transpose:** `matrix_a.T`
  - **Inverse:** `np.linalg.inv(matrix_a)`

### Optional: One-Hot Encoding (Categorical to Numerical)
- Applied `pd.get_dummies(df, columns=['gender'], dtype=int)` to convert the categorical `gender` column (`male` / `female`) into binary numerical columns (`gender_female`, `gender_male`) suitable for machine learning models.

---

## Sample Outputs

**Matrices Extracted:**
```text
Matrix A:
[[72 72]
 [69 90]]

Matrix B:
[[90 95]
 [47 57]]
```

**Operations Summary:**
```text
Addition (A + B):
[[162 167]
 [116 147]]

Subtraction (A - B):
[[-18 -23]
 [ 22  33]]

Element-wise Multiplication (A * B):
[[6480 6840]
 [3243 5130]]

Dot Product (A @ B):
[[ 9864 10944]
 [10440 11685]]

Transpose of A:
[[72 69]
 [72 90]]

Inverse of A:
[[ 0.05952381 -0.04761905]
 [-0.04563492  0.04761905]]
```

---

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`

Install dependencies locally if running outside Google Colab:
```bash
pip install pandas numpy
```

---

## How to Run

### Option 1: Google Colab
1. Open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/).
2. Upload `StudentsPerformance.csv` to the `/content/` directory.
3. Run all cells sequentially (`Runtime` → `Run all`).

### Option 2: Local Machine
1. Clone the repository and navigate to this folder:
   ```bash
   git clone [https://github.com/tusharguleria542/Statistics-Practical.git](https://github.com/tusharguleria542/Statistics-Practical.git)
   cd "Statistics-Practical/Practical-01"
   ```
2. Update the CSV path in `pd.read_csv()` if `StudentsPerformance.csv` is stored in this folder.
3. Run the notebook in Jupyter Notebook or VS Code
