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
