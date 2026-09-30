# Week 6 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. Optional — all required material is in the handout.

---

## 1. Gradient Descent

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

## 2. Stochastic Gradient Descent (SGD)

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

## 3. Learning Rate and Convergence

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

## 4. Feature Scaling

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

## 5. Ridge and Lasso via GD

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

## 6. Convexity

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Boyd & Vandenberghe** | Chapters 1–3 | The definitive reference on convexity. Free. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 4.5 | Convexity in ML. Free. | ★★ |

---

## Quick-Reference: Best Starting Points

### Big Picture

1. **D2L**, Section 4.4 ★ — GD and SGD with code, free
2. **A Course in ML**, Chapter 9 ★ — Friendly, free
3. **Ruder (2016)**, Sections 1–2 ★★ — This week's paper

### Mathematical Rigor

1. **Deep Learning**, Section 4.3 ★★ — Comprehensive optimization
2. **Boyd & Vandenberghe**, Chapter 9 ★★★ — Rigorous convergence

### Going Deep

1. **Bottou et al. (2018)** ★★★ — Definitive SGD theory
2. **Parikh & Boyd (2014)** ★★★ — Proximal methods for lasso
3. **LeCun et al. (1998)** ★★★ — Classic practical insights

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
