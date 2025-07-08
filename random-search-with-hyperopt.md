# 🎯 Random Search with Hyperopt

## 🧠 Overview
- **Hyperopt** is a Python library for hyperparameter optimization.
- It supports:
  - **Random Search** (`rand.suggest`)
  - More advanced methods like **Bayesian optimization** (covered later).
- to the tune the hyper-parameters of our model with hyperopt we need to:
  - define a model
  - define the hyperparameter space
  - define the objective function we want to minimize

---

## 🔑 Key Components of Hyperopt

1. **`fmin`** — function to minimize the objective.
2. **`hp` module** — defines the hyperparameter search space.
  - the search space can be a dict, a list or a tuple.
  - the search space can be nested.2
3. **Search algorithm** — e.g., `rand.suggest` for Random Search.

---

## ⚙️ Defining the Search Space
Use functions from the `hp` module:
- `hp.choice(label, options)` — categorical values
- `hp.randint(label, upper)` — random integers
- `hp.uniform(label, low, high)` — float between bounds
- `hp.quniform(label, low, high, q)` — float with step size q (convert to int if needed)

Search space can be a **dict, list, or tuple**, and **can be nested** for flexibility.

---

## 🧪 Objective Function
- Takes in a set of hyperparameters (as a dict).
- Converts necessary values to proper types (e.g., `int` for XGBoost params).
- Instantiates the model (`XGBClassifier`) with these parameters.
- Uses `cross_val_score` to compute **mean accuracy** over folds.
- Returns **negative accuracy** (since `fmin` minimizes by default).

---

## 🚀 Running Random Search

```python
fmin(
    fn=objective_function,
    space=param_space,
    algo=rand.suggest,
    max_evals=60,
    rstate=np.random.default_rng(seed),
)
