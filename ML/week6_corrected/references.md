# Week 6 (Corrected) — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. Optional — all required material is in the handout.

> **Note:** This reference list covers both Session 1 (probability/MLE/MAP/bias-variance) and Session 2 (gradient descent).

---

## 1. Probability, Bayes' Theorem, and MLE/MAP (Session 1)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2, "Probability Theory" | Bayes' theorem, prior/posterior, MLE/MAP. | ★★ |
| **D2L** — Zhang et al. | Section 2.6, "Probability and Statistics" | Probability for ML, MLE. Free: d2l.ai | ★ |
| **MML** — Deisenroth et al. | Chapter 6, "Continuous Optimization" (MLE/MAP sections) | MLE/MAP derivations. Free: mml-book.github.io | ★★ |
| **A Course in Machine Learning** — Daumé | Chapter 7, "Probabilistic Learning" | Friendly MLE/MAP treatment. Free: ciml.info | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 5.4–5.6, "Maximum Likelihood Estimation," "Bayesian Statistics" | Comprehensive MLE/MAP, Bayesian view. Free: deeplearningbook.org | ★★ |
| **ESL** — Hastie et al. | Section 2.6, "Statistical Decision Theory" | Bias-variance from a decision-theoretic perspective. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1–3.3, "Linear Regression" (Bayesian treatment) | MAP = Ridge, posterior distributions. | ★★★ |

### Foundational Papers

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"Visual Information Theory"** — Christopher Olah (2015) | Full blog post | Intuitive probability, entropy, KL divergence. Free: colah.github.io | ★ |

---

## 2. Bias-Variance Decomposition (Session 1)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" | Clear visual explanation. Free: statlearning.com | ★ |
| **D2L** — Zhang et al. | Section 4.5, "Weight Decay" (bias-variance discussion) | Practical connection to regularization. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 5.2.4, "Bias and Variance" | Formal treatment. Free. | ★★ |
| **ESL** — Hastie et al. | Section 7.2–7.3, "Bias-Variance Decomposition" | Rigorous derivation, connection to regularization. Free. | ★★★ |
| **PRML** — Bishop | Section 3.2, "Bias-Variance Decomposition" | Full derivation with Bayesian perspective. | ★★★ |

---

## 3. Gradient Descent (Session 2)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **D2L** — Zhang et al. | Section 4.4, "Gradient Descent" | Practical GD with code. Free: d2l.ai | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 9, "Gradient Descent" | Friendly, intuitive. Free: ciml.info | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Chapter 5, "Gradient Descent" | Concise overview. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 4.3, "Gradient-Based Optimization" and Section 5.9, "Stochastic Gradient Descent" | Comprehensive: GD, SGD, convergence. Free: deeplearningbook.org | ★★ |
| **PRML** — Bishop | Section 5.2.4, "Gradient Descent Optimization" | GD for neural networks. | ★★ |
| **Boyd & Vandenberghe** | Chapter 9, "Unconstrained Minimization" | Rigorous convergence for convex functions. Free: stanford.edu/~boyd/cvxbook/ | ★★★ |

---

## 4. Stochastic Gradient Descent (SGD)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **D2L** — Zhang et al. | Section 4.4 (SGD subsection) | SGD with code, noisy trajectory. Free. | ★ |
| **Deep Learning** — Goodfellow et al. | Section 5.9, "Stochastic Gradient Descent" | Clear comparison of batch, SGD, mini-batch. Free. | ★★ |

### Foundational Papers

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"An Overview of Gradient Descent Optimization Algorithms"** — Ruder (2016) | Sections 1–2 | **This week's suggested paper.** Best overview of GD variants. | ★★ |
| **"Efficient BackProp"** — LeCun et al. (1998) | Sections 3–4 | Classic practical SGD insights. Free. | ★★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"Optimization Methods for Large-Scale Machine Learning"** — Bottou, Curtis, Nocedal (2018) | Sections 2–4 | Definitive modern SGD theory. | ★★★ |

---

## 5. Learning Rate and Convergence

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **D2L** — Zhang et al. | Section 4.4 (learning rate discussion) | Practical $\eta$ selection. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 4.3.1 and 5.9 | Schedules, adaptive rates, convergence theory. Free. | ★★ |
| **Boyd & Vandenberghe** | Section 9.3, "Gradient Descent Methods" | Rigorous convergence proofs. Free. | ★★★ |

---

## 6. Feature Scaling

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.6.6, "Standardization" | Practical standardization. Free. | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Chapter 3, "Feature Engineering" | Concise scaling methods. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 12.2, "Preprocessing" | Scaling and conditioning. Free. | ★★ |
| **ESL** — Hastie et al. | Section 3.4.1, "Ridge Regression" (scaling discussion) | Why ridge requires standardization. Free. | ★★★ |

---

## 7. Ridge and Lasso via GD

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 6.2, "Ridge Regression" and Section 6.6, "Lasso" | Practical discussion. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4, "Shrinkage Methods" | Ridge/lasso optimization perspective. Free. | ★★★ |
| **"Proximal Algorithms"** — Parikh & Boyd (2014) | Chapters 1–3 | Proximal gradient for lasso (subgradient methods). Free. | ★★★ |

---

## 8. Convexity

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Boyd & Vandenberghe** | Chapters 1–3 | The definitive reference on convexity. Free. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 4.5 | Convexity in ML. Free. | ★★ |

---

## Quick-Reference: Best Starting Points

### For Session 1 (Probability/MLE/MAP/Bias-Variance)

1. **ISLR**, Section 2.2.2 ★ — Bias-variance, free
2. **PRML**, Section 1.2 ★★ — Bayes/MLE/MAP
3. **"Visual Information Theory"**, Olah (2015) ★ — Intuitive probability

### For Session 2 (Gradient Descent)

1. **D2L**, Section 4.4 ★ — GD and SGD with code, free
2. **A Course in ML**, Chapter 9 ★ — Friendly, free
3. **Ruder (2016)**, Sections 1–2 ★★ — This week's paper

### Going Deep

1. **Bottou et al. (2018)** ★★★ — Definitive SGD theory
2. **Parikh & Boyd (2014)** ★★★ — Proximal methods for lasso
3. **LeCun et al. (1998)** ★★★ — Classic practical insights
4. **ESL**, Section 7.2–7.3 ★★★ — Rigorous bias-variance

---

## Reference Abbreviation Key

| Abbreviation | Full Title | Authors | Free? |
|--------------|-----------|---------|-------|
| PRML | Pattern Recognition and Machine Learning | Bishop (2006) | No |
| ESL | The Elements of Statistical Learning | Hastie et al. (2009) | Yes: hastie.su.domains/ElemStatLearn/ |
| ISLR | An Introduction to Statistical Learning | James et al. (2021) | Yes: statlearning.com |
| D2L | Dive into Deep Learning | Zhang et al. (2023) | Yes: d2l.ai |
| MML | Mathematics for Machine Learning | Deisenroth et al. (2020) | Yes: mml-book.github.io |
| Daumé | A Course in Machine Learning | Hal Daumé III (2017) | Yes: ciml.info |
| Goodfellow | Deep Learning | Goodfellow et al. (2016) | Yes: deeplearningbook.org |
| Burkov | The Hundred-Page Machine Learning Book | Burkov (2019) | No |
| Boyd & Vandenberghe | Convex Optimization | Boyd & Vandenberghe (2004) | Yes: stanford.edu/~boyd/cvxbook/ |
| Ruder | "An Overview of Gradient Descent Optimization Algorithms" | Ruder (2016) | Yes: ruder.io |
| Bottou et al. | "Optimization Methods for Large-Scale ML" | Bottou, Curtis, Nocedal (2018) | Yes (arXiv) |
| LeCun et al. | "Efficient BackProp" | LeCun et al. (1998) | Yes |
| Parikh & Boyd | "Proximal Algorithms" | Parikh & Boyd (2014) | Yes |
| Olah | "Visual Information Theory" | Christopher Olah (2015) | Yes: colah.github.io |
