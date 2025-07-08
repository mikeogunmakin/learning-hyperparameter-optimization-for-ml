## Grid Search for Hyperparameter Optimization

### What is Grid Search?
- An **exhaustive search** over a manually specified grid of hyperparameter values.
- Evaluates **all possible combinations** (Cartesian product) of provided values.
- Example:
  - 2 hyperparameters with 3 values each → 3 × 3 = **9 combinations**.

### Limitations
- **Curse of dimensionality**:
  - Number of combinations grows **exponentially** with more hyperparameters. it can be computationally expensive.
- **Manual specification required**:
  - You must choose the specific values to test.
- **Not ideal for continuous hyperparameters**:
  - Can’t search every possible value, only the discrete ones you specify.
- **Does not cover entire space**, only the predefined grid.
- **Can perform poorly** with complex models and large search spaces.

### Advantages
- **Works well** with models that have **few hyperparameters**.
- **Parallelizable**:
  - Each combination can be evaluated independently → useful in distributed systems.
- Can be used in **stages**:
  - Start with a coarse grid to locate promising regions.
  - Expand grid around those regions to fine-tune further.

### Considerations
- Choose a **reasonable grid** of hyperparameter values based on:
  - Domain knowledge
  - Prior manual search
- Grid Search is **computationally expensive**, but:
  - **Parallelisation** makes it feasible on distributed systems.
  - Ideal if you have access to **high-performance computing resources**.
- Best used when:
  - The hyperparameter space is **small** or **well-understood**.
  - You want **deterministic and reproducible** search results.

### Practical Tip
- Use a **small initial grid** to identify promising areas (optimal region),
  then **narrow and extend** the grid for fine-tuning.


