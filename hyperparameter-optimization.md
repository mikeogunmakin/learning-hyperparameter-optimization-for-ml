# Hyperparameter Overview - Hyperparameter Optimization

- **Parameters** are internal to the model and are learned during training (e.g., weights in linear regression).
- **Hyperparameters** are set **before training** and control the model’s capacity to learn from data.
- **Examples of hyperparameters** (e.g. Random Forests and Gradient Boosting Machines):
  - Number of trees in the ensemble
  - Depth of each tree
  - Learning rate (for Gradient Boosting Machines)
  - Split quality metric (e.g., Gini, entropy)
  - Number of features considered per split
  - Minimum number of samples required to split a node
- **Hyperparameter tuning** involves training models with different hyperparameter combinations and comparing their performance (e.g. rmse).
- Often, multiple combinations of hyperparameters can result in similarly high-performing (or low-performing) models. This is due to the low effective dimensionality of the hyperparameter space — meaning that only a few hyperparameters have a significant impact on model performance, while others contribute very little.
  - Although many hyperparameters may exist, only a small subset truly matter. As a result, many combinations perform similarly because changes in the "less important" hyperparameters don’t significantly alter the outcome.

## 🔧 Hyperparameter Tuning (Hyperparameter Optimization)

- The process of **finding the best hyperparameters** for a model and dataset.
- Objective: **Minimise generalisation error** (not just training loss).
- Generalisation error ≠ training loss — tuning focuses on how well the model performs on **unseen data**.


**Why Is It Challenging?**
- **No direct mathematical formula** to find optimal hyperparameters.
- Unlike model parameters, hyperparameters must be **manually or programmatically tested**.
- Requires trying **multiple combinations** and **evaluating performance** for each.
- The critical step is to **choose how many different hyperparameter combinations we are going to test**.

**Trade-offs in Hyperparameter Search**
- **More combinations tested**:
  - ↑ Higher chance of finding a better model.
  - ↑ Increased **computational cost** (many models need to be trained).
- Due to **low effective dimensionality**:
  - Some hyperparameters may have **minimal impact** on performance.
  - After a point, more combinations ≠ better results.


## 🔍 Hyperparameter Optimization Strategies
- a key question in hyperparameter optimization is how do we find the hyperparameter combinations that maximize our chances to find a better performing model while diminishing computational cost?
- In order to address this, different hyperparameter optimization strategies have been developed.
- Common methods:
  - **Manual Search**
  - **Grid Search**
  - **Random Search**
  - **Bayesian Optimization** and more
- These strategies help explore the **hyperparameter space** to find the best configuration.

**Components of Hyperparameter Tuning: search**
- In the search for the best hyperparameters, we need the following:
- **Hyperparameter space**: the possible values  of each hyperparameter to sample.
- **Sampling strategy**: how candidate combinations are chosen. i.e.a method for sampling these candidates from the hyperparameter space (e.g grid search, random search,etc).
- **Cross-validation**: to estimate model performance.
  - a cross-validation scheme to get a metric of the error and some sort of standard deviation or variance,as well as the performance metric that we want to minimize
  - Mean Error (e.g. RMSE): Measures the average performance of the model across all folds (e.g., average MSE or accuracy). It estimates how well the model is likely to perform on unseen data with a given set of hyperparameters.
  - Standard Deviation of Error: Indicates the variability of model performance across folds. A low standard deviation suggests stable and reliable performance; a high standard deviation may indicate that the model is sensitive to specific data splits, which can signal potential overfitting or instability.
- **Performance metric**: the objective to minimise or maximise (e.g., MSE, accuracy).
- **Variance estimate**: helps assess the stability of results.

**Key concept - Hyperparameter Response Surface**
- Represents the relationship between **hyperparameter settings** (`λ`) and **model performance** (`φ`).
- Formally: 
