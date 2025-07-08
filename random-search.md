## Random Search for Hyperparameter Optimization

### What is Random Search?
- Selects random combinations of hyperparameters from the specified space.
- Hyperparameter values are **sampled independently** from predefined **distributions** (not a fixed grid).
- The user defines **how many combinations** to sample.

### Comparison to Grid Search
- **Grid Search** evaluates all combinations in a manually defined grid.
- **Random Search** evaluates a fixed number of **random combinations**, which:
  - Covers **more of the important dimensions**.
  - Avoids wasting time on less important dimensions.

### Why Random Search is Effective
- Leverages the concept of **Low Effective Dimension**:
  - Some hyperparameters impact performance more than others.
  - Random Search samples more **varied values** of the important parameters.
- **Works well for continuous hyperparameters**, unlike Grid Search.
    - it selects values from a distribution of parameter values.
- Random sampling allows broader exploration of the space.

### Advantages
- **Efficient in high-dimensional spaces**.
   - The power of Random Search is its ability to explore important hyperparameters more finely, especially when there are many.
   - Random Search explores more of the important hyperparameters because it samples values independently, not in fixed grids. This means more varied combinations of impactful parameters are tested, improving the chance of finding good models—especially when many other parameters matter less.
- **Can be parallelized**, like Grid Search.
- **Supports continuous hyperparameter distributions**.
- **Computational budget is flexible**:
  - Number of iterations can be fixed regardless of space size.
  - Budget scales better with complex models (e.g., neural networks).
- tradeoff: small reduction in efficiency in low dimensonal spaces.
  - Random Search is slightly less efficient in low-dimensional spaces because it samples hyperparameters randomly and might miss optimal values. In contrast, Grid Search systematically tests all combinations, which is feasible and more reliable when there are only a few hyperparameters to tune.

- Generally, if we have high dimensional hyperparameter spaces, we are better equipped if we do a Random Search, but for small dimensional spaces,Grid Search works well enough.

### Considerations
- We can choose a computational budget independently(ish) of the nuber of parameters and possible values
   - You can fix a computational budget (like “I’ll try 100 random configs”) and stay within it.
   - The “ish” acknowledges a practical caveat: Not all models are equally easy or fast to train
     - A neural network might take much longer to train than a gradient boosting machine, even for the same number of hyperparameter combinations.
     - More complex models = more time and resources needed per trial.
     - So while Random Search lets you control the number of combinations, the total computational cost still depends on the model you’re tuning.
    - Basically, you can set a fixed number of random hyperparameter samples in Random Search, making it independent of the size of the search space — but the actual compute cost (“ish”) still depends on the model complexity and training time.
- Adding parameters that do not influence performance does not decrease efficiency of the search (if enough iterations are allowed).
 - You can set how many hyperparameter combinations to try (e.g. 50, 100), regardless of how many hyperparameters you have or how many possible values each one can take. This means:
   - regardless of the search algorithm we will set a "budget" (the number of iterations), because in RS adding more parameters does not influence the performance much, provide we provide allow for enough iterations.
   - You don’t need to evaluate every combination like in Grid Search.
- Important to specify a continuous distribution of the hyperparameter to take full advantage of the randomization.
-  Define **distributions** for each hyperparameter (e.g., uniform, log-uniform).
- Choose the **number of iterations** based on resources and model complexity.
  - **60 random samples** provide a **95% chance** of finding a near-optimal combination.
- In low-dimensional spaces, **Grid Search may still be more effective**.

### Summary: Grid vs. Random Search

| Aspect                      | Grid Search              | Random Search               |
|----------------------------|--------------------------|-----------------------------|
| Search Type                | Exhaustive (Cartesian)   | Random sampling             |
| Continuous Support         | Poor                     | Excellent                   |
| High-Dim Efficiency        | Low (too expensive)                     | High                        |
| Low-Dim Efficiency         | High                     | Depends |
| Parallelizable             | Yes                      | Yes                         |
| Manual Value Specification | Required                 | Not needed (uses distributions) |

