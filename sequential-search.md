# Sequential Search – Summary

- **Hyperparameter optimization** aims to find hyperparameters that minimize or maximize a performance metric.
- The performance metric `L` depends on:
  - The algorithm used for prediction
  - The dataset
  - The hyperparameters `λ`
- The mean of `L` over the training set is represented as `φ(λ)`, known as the **hyperparameter response surface**.
- `φ(λ)` is a **black-box function** – not differentiable or analytically defined.
- Because of this, **gradient-based optimization is not possible**.

## Hyperparameter Search Process
- Define the **hyperparameter space** (range of values).
- Pick **candidate combinations** of hyperparameters.
- Train models and **evaluate performance** for each combination.
- Typically use **cross-validation** to get stable metric estimates.

## Search Strategies
- **Grid Search / Random Search**:
  - Generate all combinations up front.
  - Evaluate in parallel.
  - Suitable for simple models.

- **Sequential Search**:
  - Evaluates a few combinations initially.
  - Chooses the next set of hyperparameters **based on previous results**.
  - Iterative and **not fully parallelizable**.
  - Aims to reduce the number of evaluations by focusing on **promising areas** of the space.
  - Useful when model training is **expensive or slow**.

## Trade-Off in Sequential Search
- Saves **training time**.
- Spends **more time deciding** where to sample next.
- Ideal when model training time >> sampling decision time.

## Next Step
- Introduction to **Bayesian Optimization** in the next video:
  - A **sequential global optimization strategy**.
  - Suitable for **expensive, black-box functions**.
