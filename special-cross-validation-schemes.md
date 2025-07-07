# 🧪 Special Cross-Validation Schemes

### 📌 When Standard CV Assumptions Fail
- Standard CV assumes data is **i.i.d.** (independent and identically distributed).
- This assumption breaks for:
  - **Grouped data** (e.g. multiple samples per subject)
  - **Time series data** (temporal structure)


### 👥 Cross-Validation for Grouped Data

#### ✅ Examples
- Medical records from multiple patients
- Speech samples from multiple speakers

#### 🎯 Goal
- Ensure the model **generalizes to unseen groups** (e.g., new patients or speakers)

### 🔄 Methods

- **Group K-Fold**
  - Like K-Fold, but splits by group instead of individual samples.
  - No group appears in both train and validation sets in the same fold.
  - The fold may be different size
  - Example: a dataset with 10 groups, k = 5 (5-fold CV), then 2 groups in the validation and the other 8 in the training.
  

- **Leave-One-Group-Out**
  - Each fold leaves out **one entire group** as the validation set.
  - Trains on all other groups.

- **Leave-P-Groups-Out**
  - Leaves out **all combinations of p groups**.
  - Very **computationally expensive** for large datasets.

---

## 🕒 Cross-Validation for Time Series

### ❗ Challenge
- Must **preserve temporal order** — never use future data to predict the past.

### ⏳ Method: Rolling Forecast Origin
- Each fold:
  - Trains on earlier time blocks.
  - Validates on later time blocks.
- Training sets are **growing supersets** over time.

### 🛠 Tool
- Use **`TimeSeriesSplit`** from Scikit-learn for time series cross-validation.

---

> Tailored CV schemes are crucial for **non-i.i.d. data**, such as grouped or time series datasets, to ensure proper model evaluation.
