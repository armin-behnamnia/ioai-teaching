# Week 5 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. These are optional — all required material is in the handout. References are organized by topic and tagged with difficulty.

---

## 1. Bayes' Theorem for ML

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **MML** — Deisenroth et al. | Section 6.5, "Bayes' Theorem" | Clean ML-focused treatment with the medical testing example. Free: mml-book.github.io | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 2, "Bayes' Rule" | Friendly explanation. Free: ciml.info | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.3, "Bayes' Theorem" | The canonical ML treatment. Introduces prior/likelihood/posterior/evidence. Figure 1.2 (curve fitting with Bayes) is excellent. | ★★ |
| **MacKay** — MacKay | Chapter 2, "Bayes' Theorem" and Chapter 3 | Deep, conversational treatment. Unmatched intuition for prior/posterior. Free: inference.org.uk/mackay/itila/ | ★★ |

---

## 2. Maximum Likelihood Estimation (MLE)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **MML** — Deisenroth et al. | Section 8.3, "Maximum Likelihood Estimation" | Clean derivation of MLE for Gaussian and Bernoulli. Free. | ★ |
| **ISLR** — James et al. | Section 4.4.4, "Maximum Likelihood" | Accessible introduction in the context of classification. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.5, "Curve Fitting Revisited" and Section 2.1, "Binary Variables" | Derives MLE for polynomial regression (→ MSE) and Bernoulli. The MLE=MSE connection is here. | ★★ |
| **ESL** — Hastie et al. | Section 2.6, "Statistical Decision Theory" | Statistical perspective on MLE and loss functions. Free. | ★★★ |
| **MacKay** — MacKay | Chapter 24, "Exact Marginalization" | Deep Bayesian perspective on MLE as MAP with flat prior. Free. | ★★★ |

---

## 3. The MLE ↔ Loss Function Correspondence

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **MML** — Deisenroth et al. | Section 9.2, "Maximum Likelihood Estimation" (regression) | Derives MSE from the Gaussian likelihood. Free. | ★ |
| **PRML** — Bishop | Section 3.1.2, "Maximum Likelihood and Least Squares" | The canonical derivation: Gaussian likelihood → MSE. | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 2.6, "Statistical Decision Theory" | Different loss functions from different probabilistic assumptions. Free. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 5.5, "Maximum Likelihood Estimation" | MLE as minimizing KL divergence. Free: deeplearningbook.org | ★★★ |

---

## 4. MAP and Regularization as Priors

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **MML** — Deisenroth et al. | Section 9.3, "MAP Estimation" | Derives MAP for linear regression. Gaussian prior → ridge. Free. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 7–8, "MLE" and "Regularization" | MAP as "MLE with a prior." Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.6, "Curve Fitting Revisited" (Bayesian) and Section 3.3, "Bayesian Linear Regression" | Canonical treatment. MAP with Gaussian prior = ridge. | ★★ |
| **ESL** — Hastie et al. | Section 3.4.2–3.4.3, "Ridge Regression" (Bayesian perspective) | Ridge as the Bayesian MAP estimate. Free. | ★★★ |
| **MacKay** — MacKay | Chapter 28, "Model Comparison and Occam's Razor" | Deep treatment of priors and MAP. Free. | ★★★ |

---

## 5. Bias-Variance Decomposition

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" | Best accessible introduction. Figures 2.9–2.12 are excellent. Free. | ★ |
| **D2L** — Zhang et al. | Section 5.7, "Underfitting and Overfitting" | Practical intuition with code. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 3.2, "The Bias-Variance Decomposition" | The canonical derivation. Figure 3.5 shows bias-variance for polynomial regression. | ★★ |
| **ESL** — Hastie et al. | Section 7.3, "The Bias-Variance Decomposition" | Rigorous statistical treatment. Free. | ★★★ |
| **Understanding ML** — Shalev-Shwartz & Ben-David | Chapter 5, "The Bias-Complexity Tradeoff" | Formal learning theory perspective. Free. | ★★★ |

---

## Quick-Reference: Best Starting Points

### For Students Who Want the Big Picture

1. **MML**, Sections 6.5, 8.3, 9.2–9.3 ★ — Best ML-focused probability treatment, free
2. **ISLR**, Section 2.2.2 ★ — Best bias-variance intuition, free
3. **A Course in ML**, Chapters 2, 7–8 ★ — Friendly, free

### For Students Who Want Mathematical Rigor

1. **PRML**, Sections 1.2, 3.1–3.3 ★★ — The canonical ML probability treatment
2. **ESL**, Sections 2.6, 7.3 ★★★ — Rigorous, free
3. **MacKay**, Chapters 2, 24, 28 ★★ — Beautiful Bayesian perspective, free

---

## Reference Abbreviation Key

| Abbreviation | Full Title | Authors | Free? |
|--------------|-----------|---------|-------|
| PRML | Pattern Recognition and Machine Learning | Bishop (2006) | No (but widely available) |
| ESL | The Elements of Statistical Learning | Hastie, Tibshirani, Friedman (2009) | Yes: hastie.su.domains/ElemStatLearn/ |
| ISLR | An Introduction to Statistical Learning | James, Witten, Hastie, Tibshirani (2021) | Yes: statlearning.com |
| D2L | Dive into Deep Learning | Zhang, Lipton, Li, Smola (2023) | Yes: d2l.ai |
| Understanding ML | Understanding Machine Learning | Shalev-Shwartz & Ben-David (2014) | Yes |
| MML | Mathematics for Machine Learning | Deisenroth, Faisal, Ong (2020) | Yes: mml-book.github.io |
| Daumé | A Course in Machine Learning | Hal Daumé III (2017) | Yes: ciml.info |
| Goodfellow | Deep Learning | Goodfellow, Courville, Bengio (2016) | Yes: deeplearningbook.org |
| MacKay | Information Theory, Inference, and Learning Algorithms | David MacKay (2003) | Yes: inference.org.uk/mackay/itila/ |
