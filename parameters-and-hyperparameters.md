# Hyperparameter Tuning Overview

## Parameters and Hyperparameter
- Machine learning models are mathematical functions that represent the relationship between different aspects (features) of data. These models map input variables (features) in the dataset to a target variable or response.
- The objective of a typical learning algorithm is to find a function f that minimizes a certain loss function over a dataset.
- This learning algorithm produces f by optimising a training criterion, which involves tuning a set of parameters (e.g., coefficients in linear regression).
- For example, in a linear regression model, the algorithm maps the input variables to the target using a linear combination of the variables:

  $$\hat{y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n$$

  where $$\beta_i$$ are the model coefficients.
  - The algorithm aims to find the best coefficients 𝛽 that minimise a training criterion—typically the Residual Sum of Squares (RSS).
  - The Residual Sum of Squares (RSS) is the sum of the squared differences between the actual values $$y_i$$ and predicted $$\hat{y}_i$$

  $$RSS = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

- decision trees do something similar. They work by recursively splitting the data based on conditions applied to the input variables (features).
- At each node:
  - Selects a feature (variable).
  - Selects a split point (a threshold value for that feature).
  - Asks a binary question: Is the feature’s value ≤ split point? Based on the answer
    - if yes, send data to the left child note
    - if no, send data to the right child node
  - This process repeats at each new node:
    - Using either a new feature or the same feature with a different split point.
    - The number of such splits determines the depth (not height) of the tree.
- So, a decision tree needs to find which variable to use, which value of the variable to use, and in which node should be used each variable. These are the parameters that need to be optimized by the decision tree and they will do so by minimizing certain training criteria, like for example, the Residual Sum of Squares if it is a regression, or maybe the gini or the entropy if this was a classification.

- Neural networks in the other hand optimise **weights** (parameters) during training.
- Each **neuron** performs a **linear combination** of its inputs:
  - **Input layer** uses original features.
  - **Hidden layers** use outputs from the previous layer.
- This combination is often represented as:

  $$W^\top X$$

(similar to linear regression).
- **Activation functions** are applied after the linear combination  
*(ignored here for simplicity)*.
- The goal of training is to **find the best weights** that:
- Multiply the inputs/outputs at each layer.
- **Minimise a loss function** and improve predictions.
- All model parameters are **learned during training**.

## 🔧 Parameters vs Hyperparameters in Machine Learning

- **Parameters** (e.g. weights, coefficients) are **learned during training**.
- Examples:
  - **Betas** in linear regression  
  - **Weights** in neural networks

## ⚙️ Hyperparameters
- **Not learned** by the algorithm — must be **set before training**.
- Control the model’s **capacity** and **flexibility**.
- Aim to:
  - **Prevent overfitting**
  - **Improve generalisation**
  - Sometimes **accelerate convergence** (e.g., learning rate in gradient descent)

## 📉 Linear Regression & Regularisation

Vanilla Linear Regression
- No hyperparameters.
- Model learns the **best coefficients (betas)** that minimise the Residual Sum of Squares (RSS).

Regularised Linear Regression
- Adds a **penalty term** to the RSS to shrink coefficients and improve generalisation.
- Introduces **hyperparameters**:

## Type of regularisation:
- **Ridge** → penalises the **square** of coefficients  
- **Lasso** → penalises the **absolute value** of coefficients
- **Elastic Net** → combines both

Regularisation strength (λ):
- **Small λ** → weak penalty → close to vanilla regression
- **Large λ** → strong penalty → smaller betas

Impact of Hyperparameters
- Different values of **λ** and regularisation type can result in:
  - Different **betas**
  - Different **prediction performance**
  - **Hyperparameters must be tuned** (e.g., via cross-validation) to get the best model performance

 ## 📉 Decision Trees & hyperparameters
 - **Decision trees have several hyperparameters** that influence how the model makes predictions.
- **Feature selection per node**: Decide whether to evaluate all features or just a subset at each split.
- **Split quality metric**: Choose a metric like **Gini impurity** or **entropy** to measure how good a split is.
- **Tree depth (`max_depth`)**: Controls how deep the tree can grow. Deeper trees often predict better but **risk overfitting**.
- **Minimum samples to split (`min_samples_split`)**: Sets the minimum number of samples required to split a node.
- **Additional parameters** exist to further guide and constrain the model’s training process.

## 🌲 Random Forests & 🌟 Gradient Boosting Machines – Key Points

- Both models involve **multiple estimators** (trees).
- You must decide the number of **estimators** (`n_estimators`) to use:
  - **More estimators** → typically **better performance**
  - But **too many** can lead to **overfitting**

Random Forests
- Use **many decision trees** trained **independently**.
- Key hyperparameter:
  - `n_estimators` – number of trees in the forest

Gradient Boosting Machines (GBMs) e.g. XGBoost
- Trees are built **sequentially**, each correcting the errors of the previous one.
- Key hyperparameters:
  - `n_estimators` – number of boosting rounds (trees)
  - `learning_rate` – controls how much each new tree contributes:
    - **Lower learning rate** → slower learning, better generalisation
    - Helps reduce **overfitting**

# ⚙️ Hyperparameters in Neural Networks & Other ML Models

Neural Networks – Common Hyperparameters
- `num_layers` – number of layers in the network
- `neurons_per_layer` – number of neurons per layer
- `activation_function` – introduces non-linearity (e.g. ReLU, sigmoid)
- `dropout_rate` – controls regularisation by randomly disabling neurons during training
- `momentum` – used in optimisers to accelerate gradient descent

K-Nearest Neighbours (KNN)
- `n_neighbors` – number of neighbours to consider (e.g., 3, 5, 9)

Support Vector Machines (SVM)
- `kernel` – defines the transformation applied to the input data  
  (e.g., linear, polynomial, RBF)


## ✅ Key Takeaways on Hyperparameters
- **Hyperparameters are set before training** begins.
- They **control** how the model learns and **constrain** the parameters found during training.
- They can have a **significant impact** on model performance.
- **Optimal hyperparameters differ** across datasets.
- **Tuning hyperparameters** (e.g., via grid search or random search) is essential for best results.


