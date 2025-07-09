## Bayes' Rule – Summary

### 📘 What is Bayes' Rule?
- A mathematical relationship connecting:
  - **Prior probability** (belief before seeing evidence)
  - **Posterior probability** (belief after seeing evidence)
  - **Likelihood** (evidence given a condition)
- Formula:  
  $$\[
  P(A $$\mid B$$) = \frac{P(B \mid A) \cdot P(A)}{P(B)}
  \]$$
  - $$\(P(A \mid B)\)$$: Posterior (probability of A given B)
  - $$\(P(B \mid A)\)$$: Likelihood (conditional probability, of B taking place given A.
  - $$\(P(A)\)$$: Prior
  - $$\(P(B)\)$$: Evidence or marginal probability

---

### 🧠 Key Concepts Recap
- **Joint Probability**:  
  $$\[
  P(A \cap B) = P(A \mid B) \cdot P(B) = P(B \mid A) \cdot P(A)
  \]$$
- **Conditional Probability**: Not symmetric.  
  $$\[
  P(A \mid B) \neq P(B \mid A)
  \]$$
- **Bayes' Rule** is derived by equating two expressions of the joint probability.

---

### 🏦 Fraud Detection Example
- Prior probability of fraud: \(P(\text{Fraud}) = 0.001\)
- ML model:
  - Correctly flags fraud 99%: \(P(\text{Positive} \mid \text{Fraud}) = 0.99\)
  - False positive rate 5%: \(P(\text{Positive} \mid \text{Non-Fraud}) = 0.05\)
- Want to compute:  
  \[
  P(\text{Fraud} \mid \text{Positive})
  \]

#### Applying Bayes' Rule:
\[
P(\text{Fraud} \mid \text{Positive}) = 
\frac{0.99 \cdot 0.001}
     {0.99 \cdot 0.001 + 0.05 \cdot 0.999}
= 0.019 \text{ or } 1.9\%
\]

- Even with a 99% accurate model, the chance of actual fraud is only 1.9% due to how rare fraud is overall.
- This shows how **base rates (priors)** impact interpretation of model outputs.

---

### 📊 General Notes on Bayes' Rule
- Helps shift from general belief (prior) to updated belief (posterior) after seeing new evidence.
- The denominator (evidence) is computed by **summing over all possibilities**:
  \[
  P(B) = P(B \mid A)P(A) + P(B \mid \neg A)P(\neg A)
  \]

---

### 🤖 Application to Machine Learning
- In ML/AI, Bayes' Rule is used to:
  - Estimate the **posterior** probability of parameters/hyperparameters
  - Given evidence from model performance (e.g., generalisation error)

- In **Bayesian Hyperparameter Optimization**:
  - Prior: belief over hyperparameters
  - Likelihood: performance metric (e.g., error given hyperparameters)
  - Posterior: updated belief of good hyperparameters given results

---

### 🔜 What’s Next
- Introduce **Bayesian Optimization** using **Gaussian Processes**
- Estimate posterior distribution of hyperparameters given data
- Use this to guide intelligent hyperparameter search
