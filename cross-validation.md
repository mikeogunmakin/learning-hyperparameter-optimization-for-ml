# Cross-Validation Summary

## 🔁 Purpose of Cross-Validation
- Prevents **overfitting** during hyperparameter tuning.
- Ensures **generalization** by validating performance on unseen data.
   - Generalization is the ability of a model to be effective across various inputs, or in other words, across various datasets.
   - If the algorithm generalizes well, the performance across all these datasets should be fairly similar. So the performance of a machine learning model should be constant in the different datasets, assuming that the distribution of the data is similar to the one that we used to train the model.
   - When a model performs well on the training set but not in the test set, or not in the data that we're actually interested in scoring, we say that the model overfits to the training data. The paprameters are not good enough to predict the same response in the test data.
- Helps obtain a **reliable estimate of model performance** with variability/error bounds.

## 📊 Common Approaches in tuning hyperparameters

### 🟢 Approach 1: Train/Test Split

- **Description**:
  - Split historical data into a **training set** and a **test set**.
  - Train the model on the training set.
  - Evaluate performance on the test set (and also training set) and tune the model based on performance.

- **Cons**:
  - ❌ Risk of **overfitting to the test set** if used repeatedly during tuning.
    - When you're tuning a model and checking its performance on the test set after every change, you're using the test set as feedback. Even if you're not feeding it into the model, you’re letting its results influence your decisions. This is a common mistake in Data Science competitions.
  - ❌ No **error bounds** or understanding of performance variability.
  - ❌ Test set may not be **representative** of real-world data.

### 🟡 Approach 2: Train/Validation/Test Split

- **Description**:
  - Split data into **train**, **validation**, and **test** sets.
  - Tune hyperparameters using the validation set performance.
  - Use test set only once for final evaluation.

- **Cons**:
  - ❌ In **small datasets**, splitting three ways can leave **too little data for training**.
  - ❌ A **single validation score** doesn’t show performance variability.
  - ❌ Validation set may not be **representative**, leading to unstable model selection.

### ✅ Approach 3: Cross-Validation (Preferred)

- **Description**:
  - Split training data into **k folds** (e.g., 5-fold).
  - Train and validate k times, rotating the validation fold.
  - Use **average performance** across folds to select hyperparameters space
    
  - Keep test set untouched for final evaluation.

- **Pros**:
  - ✅ Provides a **robust estimate** of model performance.
  - ✅ Produces **error bounds** (e.g., min-max R² scores).
  - ✅ **Reduces variance** by averaging across multiple data splits.
  - ✅ Prevents **test set leakage** by keeping it isolated until the end.


## ✅ What is Cross-Validation?
- The training set is split into **k-folds** (e.g., 5-folds).
- Each fold is used once as a **validation set**, while the others are used for training.
- This results in **k performance scores** that are:
  - **Averaged** to estimate overall performance.
  - Used to calculate **error bounds** (e.g., range of R² scores).


## 🔍 Cross-Validation in Hyperparameter Tuning
- Every set of hyperparameters is evaluated using cross-validation.
- Produces a **mean performance score with an error margin**.
- The best hyperparameters are selected based on **cross-validated performance**, not test set performance.
- Final model is tested once on the **held-out test set** to confirm generalization.
  - ideally metric falls within the interval of the CV error bounds.

