# Performance Metrics

## Classification Metrics
- There are two classes of metrics
  - threshold-dependent metrics - e.g. accuracy, precision, recall, f-score, FPR (false positive rate), FNR (False negative rate)
  - threshold-independent metrics - e.g ROC-AUC
- **Threshold-dependent** metrics depend on a specified probability cutoff to classify predictions (e.g. 0.5), while **threshold-independent** metrics evaluate model performance across all possible cutoffs without relying on a single threshold (i.e. provide an aggregate view).
- Accuracy:
  - Fraction/percentage of correct predictions (both class 0 and 1).
  - Accuracy = number of correct predictions/total number of predictions
  - Accuracy = (TP + TN) / Total.
- Confusion Matrix:
  - TP: True Positives
  - TN: True Negatives
  - FP: False Positives
  - FN: False Negatives
- Precision (Positive Predictive Value):
  - Proportion of predicted positives that are actual positives.
  - gives an idea of the percentage of observations that are correctly classified from all of those that are classified as members of class 1.
  - so, from all the observations that the model says are from the positive class, how many of them are indeed from the positive class.
  - Precision = TP / (TP + FP).
- Recall (True Positive Rate):
  - Proportion of actual positives that are correctly predicted.
  - Recall = TP / (TP + FN).
  - So, it gives you an idea of how many of the observations from class 1 are going to be correctly identified by this model that you built. The higher the better as it is better at classifying as positive. b 
- F1 Score:
  - weighted harmonic mean of precision and recall.
  - F1 = 2 * (Precision * Recall) / (Precision + Recall).
  - We want this to be as high as possible.
- False Positive Rate (FPR):
  - Proportion of actual negatives incorrectly classified as positive.
  - FPR = FP / (FP + TN).
  - So from all the observations that are from the class 0,or the negative class, how many of them were wrongly classified as the positive class
- False Negative Rate (FNR):
  - Proportion of actual positives incorrectly classified as negative.
  - FNR = FN / (FN + TP).
  - So, from all the observations that do belong to the class 1,or the positive class,how many of them were wrongly classified.
- Receiving Operating Characteristic Curve (ROC Curve)
  - Plots True Positive Rate vs False Positive Rate at various probability thresholds.
  - ROC-AUC (Area Under Curve):
    - The area under the curve is called the ROC-AUC,that is, Area Under the Curve,and it's an aggregate measure of this tradeoff for all the probability thresholds.
    - If the model is random, we would see a Receiving Operating Characteristic Curve that is a diagonal in this square,so the area under the diagonal is 0.5. We want this receiving operator to be as close to this border as possible, so the higher the ROC-AUC the better, and the values that it can take vary between 0.5, which is the minimum for the random model, and 1, which is the maximum for the area of the curve.
    - Aggregates performance across all thresholds.
    - Range: 0.5 (random guess) to 1.0 (perfect classifier).
    - Higher is better.
- Loss Function (Cross-Entropy)
  - The loss function in classification models measures how far the model's predicted probabilities are from the true class labels — it's what the model tries to minimise during training.
  - General form: Loss = -[y * log(p) + (1 - y) * log(1 - p)]
  - Used for model optimisation.
  - Penalises incorrect confident predictions.

## Regression Metrics

## 🔍 Regression Metrics Summary
- Evaluate how close the model’s continuous predictions (\( \hat{y} \)) are to the true values (\( y \)).
- **Goal**: Minimise prediction error.

### 📊 Common Regression Metrics

- **Mean Squared Error (MSE):**  
  - Average of squared differences between predictions and actual values.  
  - Penalises larger errors more.  
  - `MSE = mean((y - ŷ)²)` 

- **Root Mean Squared Error (RMSE):**  
  - Square root of MSE.  
  - Brings error back to the same scale as the target variable.  
  - `RMSE = sqrt(MSE)`
  - takes it back to original scale

- **Mean Absolute Error (MAE):**  
  - Average of absolute differences between predictions and true values.  
  - Less sensitive to large errors than MSE.  
  - `MAE = mean(|y - ŷ|)`

- **R-squared (R²):**  
  - Proportion of variance in the target variable explained by the model.  
  - `R² = 1 - (SS_res / SS_tot)`  
  - Values range from `0` to `1`; higher is better.  
  - `R² = 0.4` means the model explains 40% of the variance.
