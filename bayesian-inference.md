# Bayesian Inference – Summary Notes

## 🧠 Core Ideas
- **Bayesian inference** has two foundational ideas
-  is the process of:
  1. **Reallocating probability (credibility)** across possible options.
  2. These possibilities across which the probability is reallocated are usually the **parameters** (or hyperparameters) of a mathematical model.

## 🎯 Belief and Probability
- In Bayesian statistics, **probability = degree of belief**.
- Beliefs can be based on:
  - Prior knowledge (e.g., historical data)
  - Personal judgement or subjective information
- Beliefs are **updated** as new information becomes available using **Bayes' Rule**.

## 🎁 Birthday Gift Example (Discrete Inference)
- Initial belief: Four people could’ve left the gift → equal probabilities (the **prior**).
- New evidence eliminates some candidates (parents out of town, partner forgot, sister lost the key).
- After each update, probabilities are reassigned → resulting in a **posterior** belief (most likely: best friend).
- This process illustrates **Bayesian updating**: Prior → Evidence → Posterior.

## 📊 Height Distribution Example (Continuous Inference)
- Goal: Infer where a group of women is from based on their height.
- Prior: Equal belief they’re from Europe, Latin America, or Asia.
- New data: Observed heights of first few women.
- These heights align more with Latin American height distribution.
- Probabilities are updated accordingly → results in a **posterior distribution**.

## 🔄 Inference Process
1. Start with a **prior** distribution (initial belief).
   - prior probability is the unconditional probability assigned to an event before any relevant information is taken into account.
2. Gather data (evidence).
3. Use Bayes' Rule to compute the **posterior**.
   - the posterior probability of an event, is the **conditional probability** that is assigned after taking into account the new evidence.
4. Posterior becomes the new prior for further updates.
5. Repeat as more evidence arrives.

## 📐 Key Definitions
- **Prior**: Belief about an event before seeing any data.
- **Posterior**: Updated belief after considering new evidence.
- **Bayes' Rule**: Mathematical formula that relates the prior and posterior using conditional probability.

