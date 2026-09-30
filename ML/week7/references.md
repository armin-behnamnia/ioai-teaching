# Week 7 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. Optional — all required material is in the handout.

> **Note:** Session 1–2 references cover the review (regression, evaluation, probability). Sessions 3–4 cover gradient descent and logistic regression.

---

## 1. Review: Linear Regression & Regularization (Sessions 1–2)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.1–3.2 (linear regression), 6.2 (ridge), 6.6 (lasso) | The complete regression story with R labs. Free: statlearning.com | ★ |
| **D2L** — Zhang et al. | Section 3.1 (linear regression), 4.5 (weight decay) | Modern treatment, code included. Free: d2l.ai | ★ |
| **Daumé** — *A Course in Machine Learning* | Chapters 1–2 (learning, linear models), Chapter 7 (probabilistic learning) | Friendly re-derivation of everything from Weeks 1–5. Free: ciml.info | ★ |
| **ESL** — Hastie et al. | Section 3.2 (linear regression), 3.4 (shrinkage) | The rigorous version of W2–W3. Free. | ★★★ |

## 2. Review: Evaluation & Metrics (Session 1)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** | Section 2.2 (evaluating model performance), 5.1 (cross-validation) | Bias-variance intuition + validation. Free. | ★ |
| **D2L** | Section 5.5 (k-fold CV) | Practical cross-validation. Free. | ★ |

## 3. MAP, Priors, and the Bayesian View (Session 2)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.4 (Bayesian probabilities), 3.1.2–3.3 (Bayesian linear regression) | Where MAP = Ridge lives in full generality. | ★★★ |
| **MML** — Deisenroth et al. | Section 8.2–8.3 (linear regression, MAP) | Careful MAP derivations. Free: mml-book.github.io | ★★ |
| **Goodfellow et al.** | Section 5.4–5.6 (MLE, Bayesian statistics) | MLE/MAP from the deep-learning perspective. Free: deeplearningbook.org | ★★ |
| **"Visual Information Theory"** — Olah | Full post | Entropy/KL — the probabilistic bridge to Week 11. Free: colah.github.io | ★ |

## 4. Bias-Variance (Session 2)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** | Section 2.2.2 | The clearest visual treatment. Free. | ★ |
| **ESL** | Section 7.2–7.3 | The rigorous decomposition (matches our derivation). Free. | ★★★ |
| **Goodfellow et al.** | Section 5.2.4 | Compact formal statement. Free. | ★★ |

## 5. Gradient Descent (Session 3)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **D2L** | Section 3.2 (GD for linear regression), 12.4 (SGD and minibatch) | GD/SGD with runnable code. Free: d2l.ai | ★ |
| **Daumé** | Chapter 9 (gradient descent) | Intuition-first. Free: ciml.info | ★ |
| **Goodfellow et al.** | Section 4.3 (gradient-based optimization), 5.9 (SGD) | Convergence, convexity, condition numbers. Free. | ★★ |
| **Boyd & Vandenberghe** | Chapter 9 (unconstrained minimization) | The rigorous theory (convexity, step-size theorems). Free. | ★★★ |
| **Ruder (2016)** | Sections 1–2 | This week's carry-over paper from Week 6 — GD variants survey. Free: ruder.io | ★★ |

## 6. Feature Scaling (Session 3)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** | Section 6.2.1 (why ridge needs scaling) | The variance-dominance argument. Free. | ★ |
| **Goodfellow et al.** | Section 4.3.2 (condition number), 12.2 (preprocessing) | Why elongated valleys slow GD. Free. | ★★ |

## 7. Logistic Regression (Session 4)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** | Section 4.1–4.3 (classification, logistic regression) | The standard textbook treatment; log-odds interpretation; 4.3 has the MLE derivation. Free: statlearning.com | ★ |
| **D2L** | Section 3.4 (softmax regression — includes binary as a special case) | The logistic model + cross-entropy with code. Free. | ★ |
| **Daumé** | Chapter 4 (logistic regression) | The 0-1-loss → surrogate-loss story. Free: ciml.info | ★ |
| **PRML** — Bishop | Section 4.3.2 (logistic regression), 4.3.4 (Laplace approximation context) | Deeper probabilistic view; §4.5 has the softmax/ multi-class generalization. | ★★★ |
| **ESL** | Section 4.4 (logistic regression) | Logistic vs. LDA, optimality of the log-odds-linear form. Free. | ★★★ |

## 8. Sigmoid, Odds, and Log-Odds (Session 4, ★ sections)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** | Section 4.3.1 (the logistic model) | Odds ratios and interpretability. Free. | ★ |
| **"Understanding Logistic Regression Coefficients"** — various blog treatments | — | Interpretation practice for $e^w$ as odds multiplier. | ★ |

---

## Quick-Reference: Best Starting Points

### For the review (Sessions 1–2)
1. **ISLR**, Sections 2.2 + 3.1–3.2 + 6.2 ★ — the whole W2–W3 story, free
2. **Daumé**, Chapters 1–2 ★ — friendliest re-derivation, free
3. **ISLR**, Section 2.2.2 ★ — bias-variance, free

### For gradient descent (Session 3)
1. **D2L**, Section 3.2 ★ — GD on linear regression with code, free
2. **Goodfellow et al.**, Section 4.3 ★★ — convexity and convergence
3. **Ruder (2016)** ★★ — the Week 6 paper; now fully readable after Session 3

### For logistic regression (Session 4)
1. **ISLR**, Section 4.1–4.3 ★ — the canonical first reading, free
2. **D2L**, Section 3.4 ★ — code + cross-entropy
3. **Daumé**, Chapter 4 ★ — the surrogate-loss motivation

### Going Deep
1. **ESL**, Section 3.4 + 4.4 ★★★ — the full statistical treatment
2. **PRML**, Section 3.3 + 4.3.2 ★★★ — the Bayesian view (MAP = Ridge in context)
3. **Boyd & Vandenberghe**, Chapter 9 ★★★ — convex analysis of GD

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
| Boyd & Vandenberghe | Convex Optimization | Boyd & Vandenberghe (2004) | Yes: stanford.edu/~boyd/cvxbook/ |
| Ruder | "An Overview of Gradient Descent Optimization Algorithms" | Ruder (2016) | Yes: ruder.io |
| Olah | "Visual Information Theory" | Christopher Olah (2015) | Yes: colah.github.io |
