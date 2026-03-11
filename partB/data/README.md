# Dataset Information

## Primary Dataset: Breast Cancer Wisconsin (Diagnostic)

**Source:** `sklearn.datasets.load_breast_cancer()`

**How to obtain:** This dataset is bundled with scikit-learn and requires no manual download.
Run `from sklearn.datasets import load_breast_cancer; data = load_breast_cancer()` in any
notebook to load it directly.

**Description:**
- 569 instances, 30 real-valued features
- Binary classification: malignant (0) vs. benign (1), mapped to {-1, +1} for LR
- Features: mean, standard error, and worst values of 10 cell nucleus measurements

**How it is used:**
- `X_train.npy`, `X_test.npy`: StandardScaler-transformed feature matrices (80/20 split, random_state=42)
- `y_train.npy`, `y_test.npy`: labels in {-1, +1}

**Preprocessing applied:**
1. Labels converted from {0,1} to {-1,+1} as required by the LR dual formulation (Eq. 1 of the paper)
2. Features standardised to zero mean and unit variance using sklearn.preprocessing.StandardScaler
3. 80/20 train/test split with random_state=42

**No manual steps required.** All notebooks load the dataset programmatically.
