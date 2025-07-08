## Manual Search for Hyperparameter Tuning

### What is Manual Search?
- Trying different hyperparameter values manually.
- Often used despite its simplicity.

### Use Cases
- **Identify promising hyperparameter regions**:
  - Helps understand where model performance improves or plateaus.
  - can help develop intuition for the space that improves performance (low effect dimension)
- **Define intervals for Grid Search**.
   - delimit the gird search.
- **Understand hyperparameter impact**:
  - Learn which ones strongly affect performance.
  - get familair with the hyperparamters and their effect on the models.
- **Set up a benchmark model**.
  - Before diving into automated hyperparameter tuning, you often build a baseline model using sensible default values or a few manually selected hyperparameters.
  - This model gives you a reference point to compare against future improvements.
- **Prepare examples for teaching or open-source tools**.

### Limitations
- **Lacks reproducibility**:
  - No automatic logging of tested parameters.
  - No records of which values we tested.
- **Time-consuming**:
  - Manual tuning, often one parameter at a time.
- **Doesn't explore full space**.
- **Not scalable** for complex models with many hyperparameters.

