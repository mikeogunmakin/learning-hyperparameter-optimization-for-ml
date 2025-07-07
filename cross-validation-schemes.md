# 🔁 Cross-Validation Schemes
- Cross-validation helps estimate **generalization error** and **select hyperparameters**.
-  It can also be used to select best performing models from a group of models. for exaple differet algorithms on the same dataset or different feature subsets.
- Always keep a **separate test set** for final performance evaluation.
- There are different schemes/approaches to cross validation.
- When choosing the CV scheme you must consider the bias vs variance trade off and the training set size vs Bias.
- Smaller training sets during CV can lead to **high bias** (underfitting).
   - If the training set is too small, it may not contain enough examples of important variations or relationships in the data.
   - As a result, the model learns overly simplistic rules that fail to capture complexity.
- Larger training sets reduce bias but may increase **variance** (overfitting to noise).
  - With more data, practitioners are tempted (and justified) to use more complex models (deep nets, ensembles, etc.).
  - Complex models can memorize noise or overfit localized patterns
 
## Bias vs Variance

![Diagram](./images/bias-vs-variance.png) 

This chart shows how **generalization error** changes with **model complexity**, helping us understand the trade-off between **bias** and **variance**.

### 🔵 Training Set Error (Blue Line)
- Decreases steadily as model complexity increases.
- A more complex model fits the training data better.

### 🔴 Test Set Error (Red Line)
- Decreases initially (improving generalization), then increases again.
- This U-shaped curve shows where **overfitting begins**.

### Key Zones (Refer to Chart):

- **Left Side – Underfitting (High Bias)**:
  - Simple models (e.g., linear regression, few trees).
  - **High training and test errors**.
  - Model fails to capture data patterns.

- **Middle – Just Right**:
  - Balanced model complexity.
  - **Lowest test error** → best generalization.
  - Ideal model capacity for the task.

- **Right Side – Overfitting (High Variance)**:
  - Very complex models (e.g., deep trees, high-degree polynomials).
  - **Low training error**, but **test error increases**.
  - Model memorizes training data and fails to generalize.


- The goal is to find the “sweet spot” in model complexity where test error is minimized — this is where **bias and variance are balanced**.

## Training set size vs Bias
  
---

## 1. **K-Fold Cross-Validation**
- **Description**: Split training data into *k* equal parts (folds).
- Train on *k-1* folds, validate on the remaining fold.
- Repeat *k* times with different validation folds.
- **Output**: Average performance ± standard deviation.
- **Typical k values**: 5 or 10.
- The higher K
  - bigger the train sets
    - As K increases, the validation set becomes smaller, and the training set becomes larger (since you're using K-1 of the K folds to train). So with higher K, you're training on more data per fold.
  - less model bias
  - more variance
- **Pros**:
  - Widely used and efficient.
  - No overlap in validation folds.
- **Cons**:
  - May not handle imbalanced datasets well.

---

## 2. **Leave-One-Out Cross-Validation (LOOCV)**
- **Description**: Special case of K-Fold where *k = n* (n = number of observations).
- Train on *n-1* samples, test on the single remaining one.
- Repeat *n* times.
- **Pros**:
  - Utilises nearly all data for training.
  - Good for small datasets.
- **Cons**:
  - Very **computationally expensive**.
  - **High variance** due to minimal differences in training sets.
  - **Not suitable** for metrics like ROC-AUC, precision, or recall (due to 1 test sample).
    - Metrics like ROC-AUC, precision, and recall require multiple predictions to compute meaningful results. Since Leave-One-Out Cross-Validation (LOOCV) only uses one instance in the validation set per fold, these metrics can’t be calculated reliably — or at all — within each fold.
    - more appropriate for regression not classification tuning and performance checks.

---

## 3. **Leave-P-Out Cross-Validation (LPOCV)**
- **Description**: Leave out all possible subsets of *p* observations.
- Train on *n-p*, test on *p* observations.
- **Pros**:
  - Larger validation sets improve metric stability (vs. LOOCV).
- **Cons**:
  - **Extremely expensive**: factorial number of combinations.
    - for n observationsm this produces $$\binom{n}{p}$$ train-test pairs
  - **Overlapping test sets** (as subsets are selected randomly)

- Example: Leave-2-Out with 5 Samples (n = 5, p = 2)
  Your dataset: `[A, B, C, D, E]`
  You must consider **every unique pair** of samples to leave out:

   1. Leave out A and B → train on `[C, D, E]`
   2. Leave out A and C → train on `[B, D, E]`
   3. Leave out A and D → train on `[B, C, E]`
   4. Leave out A and E → train on `[B, C, D]`
   5. Leave out B and C → train on `[A, D, E]`
   6. Leave B and D → train on `[A, C, E]`
   7. Leave B and E → train on `[A, C, D]`
   8. Leave C and D → train on `[A, C, E]`
   9. Leave C and E → train on `[A, B, D]`
   10. Leave out D and E → train on `[A, B, C]`

   There are **$\binom{5}{2} = 10$** such combinations.

   For each combination:

   - Train the model on the **remaining n−p samples**.
   - Evaluate it on the **p samples you left out**.
   - Repeat this for every possible combination of p samples.
   - NB: we can see overlap in the test samples as 1 to 3 have 'A' test sample for instance.


---

## 4. **Repeated K-Fold Cross-Validation**
- **Description**: Perform K-Fold CV *n* times with shuffled data.
- Each repetition gives a new train/validation split.
- **Output**: *k × n* performance metrics.
- **Pros**:
  - Provides a more **robust estimate** of model performance.
  - Reduces bias from a single data split.
- **Cons**:
  - Test sets may **overlap across repetitions**.

---

## 5. **Stratified K-Fold Cross-Validation**
- **Description**: Variant of K-Fold for **classification problems**.
- Ensures each fold has similar **distribution** of each class.
- **Essential** when dealing with **imbalanced datasets**.
- **Pros**:
  - Prevents folds without minority class examples.
  - Better performance estimation in classification tasks.
    use
- **Cons**:
  - Only applicable to **classification**, not regression.

---

## 🧠 When to Use What?
- ✅ **K-Fold (k=5 or 10)**: Good default, works well in most scenarios.
  - When k is small, the model trains on significantly less data per fold, so it may underfit, leading to higher bias in the error estimate.
  - With a small k (e.g., 2 or 3), the model trains on only half or two-thirds of the data.
- ✅ **Stratified K-Fold**: Use for **classification**, especially with class imbalance.
- ❌ **Leave-One-Out**: Use only for **small datasets** with continuous error metrics (e.g., MSE).
   - may perform poorly for discontinuous error functions (e.g. number of misclasified cases, precision and recall).
- ❌ **Leave-P-Out**: Rarely used due to high computational cost.
- ✅ **Repeated K-Fold**: Good when seeking more robust performance estimates.

