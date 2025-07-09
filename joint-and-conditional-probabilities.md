## Joint, Marginal, and Conditional Probability – Summary

### 🐶 Example Context
- Study of hip dysplasia across 600 dogs from 3 breeds:
  - German Shepherd, Doberman, Labrador
- Dysplasia categories: None, Mild, Severe

---

### 📊 Marginal Probability
- Probability of a **single event**, summed across other variables.
- Example:
  - P(German Shepherd) = 200 / 600 = 0.33
  - P(No Dysplasia) = 100 / 600 = 0.16
- Found by **summing joint probabilities** across the second variable.

---

### 🔗 Joint Probability
- Probability of **two events happening together**.
- Example:
  - P(Doberman ∩ Mild Dysplasia)
- **Symmetric**:
  - P(A ∩ B) = P(B ∩ A)

---

### ➗ Conditional Probability
- Probability of one event **given** that another has occurred.
- Written as:  
  \[
  P(A \mid B) = \frac{P(A \cap B)}{P(B)}
  \]
- Example:
  - P(Dysplasia | German Shepherd)
  - Calculated by dividing the joint probabilities (breed + dysplasia) by the marginal probability of the breed.

- **Not symmetric**:
  - P(A | B) ≠ P(B | A)

---

### 📌 Prior and Posterior Probability
- **Prior Probability**:  
  - Unconditional probability before seeing new data (e.g., overall P(Dysplasia))
- **Posterior Probability**:  
  - Updated probability **after** observing new data (e.g., P(Dysplasia | Breed = German Shepherd))

- These are connected through **Bayes’ Rule**, which will be covered in the next video.

