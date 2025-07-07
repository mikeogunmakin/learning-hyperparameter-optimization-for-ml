# 📉 Bias-Variance Trade-off Summary

## 🧠 General Concepts

- **Bias**: Error due to incorrect assumptions in the model (e.g., using a linear model for non-linear data) → leads to **underfitting**.
- **Variance**: Error due to model sensitivity to training data fluctuations → leads to **overfitting**.
- **Trade-off**: Increasing model complexity usually reduces bias but increases variance.  
  - In the **deep learning era**, this trade-off is discussed less explicitly but still exists.
- **High Bias**: Simple models (e.g., linear regression) don’t capture patterns well.
  - under fitting -> high bias
- **High Variance**: Complex models (e.g., deep networks) fit training data too closely but perform poorly on new data.
-  - over fitting -> high variance
- **"Just Right" Model**: Balanced complexity that generalizes well — neither underfits nor overfits.
 

## 🔍 Diagnosing Bias & Variance Using Errors

-  The two key numbers to look at to understand bias and variance are the training set error and the validation (or development) set error.

| Training Error | Dev (Validation) Error | Diagnosis                     |
|----------------|------------------------|-------------------------------|
| High           | High                   | **High Bias** (Underfitting)  |
| Low            | High                   | **High Variance** (Overfitting) |
| High           | Very High              | **High Bias & High Variance** |
| Low            | Low                    | **Low Bias & Low Variance** ✅ |

- **Training error** → reveals bias (fit to training data).
- **Gap between training and dev error** → reveals variance (generalization performance).


