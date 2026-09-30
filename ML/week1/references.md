# Week 1 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. These are optional — all required material is in the handout. References are organized by topic and tagged with difficulty.

---

## 1. What is Machine Learning?

### Foundational / Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **A Course in Machine Learning** — Hal Daumé III | Chapter 1, "What is Machine Learning?" | A friendly, verbose introduction to the ML mindset. Free PDF: ciml.info | ★ |
| **Machine Learning** — Tom Mitchell | Chapter 1, Sections 1.1–1.3 | The classic definition of ML (the T, E, P framework comes from here). The checkers example is excellent. | ★★ |
| **The Hundred-Page Machine Learning Book** — Andriy Burkov | Chapter 1, "Introduction" | Very concise overview of ML types and the learning problem. | ★ |

### Thought-Provoking

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"A Few Useful Things to Know about Machine Learning"** — Pedro Domingos (2012) | Sections 1–3 | Twelve key lessons about ML. Great big-picture perspective. This is also the Week 2 suggested paper. | ★ |
| **"The Bitter Lesson"** — Rich Sutton (2019) | Entire post (1 page) | The argument that computation, not human-designed features, drives AI progress. Provocative. | ★ |

---

## 2. Types of Learning (Supervised, Unsupervised, Reinforcement)

### Supervised Learning

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Pattern Recognition and Machine Learning (PRML)** — Bishop | Section 1.1, "Polynomial Curve Fitting" | The canonical introduction to supervised learning via polynomial regression. We'll revisit this in Week 9. | ★★ |
| **The Elements of Statistical Learning (ESL)** — Hastie et al. | Section 2.1, "Introduction to Supervised Learning" | Statistical perspective on supervised learning. More formal than Bishop. Free PDF. | ★★★ |
| **Introduction to Statistical Learning (ISLR)** — James et al. | Chapter 2, "Statistical Learning" | Very accessible. The advertising example is a great concrete case. Free PDF. | ★ |

### Unsupervised Learning

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.12, "Unsupervised Learning" | Brief overview of clustering, density estimation, and dimensionality reduction. | ★★ |
| **ESL** — Hastie et al. | Section 14.1, "Introduction to Unsupervised Learning" | Overview of unsupervised methods within the statistical learning framework. | ★★★ |

### Reinforcement Learning

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Reinforcement Learning: An Introduction** — Sutton & Barto | Chapter 1, "Introduction" | The classic RL textbook. Chapter 1 gives the agent-environment framework. Free PDF (2nd edition). | ★★ |
| **"Playing Atari with Deep Reinforcement Learning"** — Mnih et al. (2013) | Abstract + Section 1 | A real-world RL example. This is also a suggested paper in Week 32. | ★★★ |

---

## 3. The Hypothesis Space and Model Selection

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Section 2.1, "A Formal Model — The Statistical Learning Framework" | Rigorous mathematical formulation of the learning problem. The ERM principle is defined here. | ★★★ |
| **PRML** — Bishop | Section 1.3, "Model Selection" | How to choose between hypothesis spaces. Preview of cross-validation (Week 4). | ★★ |
| **ESL** — Hastie et al. | Section 2.9, "Model Selection" | Statistical view of model selection. (The bias-variance decomposition is sketched here, but we'll defer the formal treatment to Week 5.) Free. | ★★★ |
| **Mathematics for Machine Learning** — Deisenroth et al. | Section 8.2, "Parameter Estimation" | The ML problem formulated with linear algebra. Good bridge to Week 2. | ★★ |

---

## 4. Loss Functions

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.3.5, "Loss Functions for Regression and Classification" | Overview of common loss functions and their properties. | ★★ |
| **ESL** — Hastie et al. | Section 2.4, "Linear Regression of an Indicator Matrix" | Shows how different loss functions arise from different assumptions. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 5.7, "Maximum Likelihood Estimation" | Connects loss functions to probability (preview of Week 4). The deep learning perspective. | ★★★ |

---

## 5. Overfitting and Generalization

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **A Course in Machine Learning** — Daumé | Chapter 5, "Generalization" | Very accessible explanation of overfitting and why training error ≠ test error. Free. | ★ |
| **Neural Networks and Deep Learning** — Michael Nielsen | Chapter 1, "Using neural nets to recognize handwritten digits" — Section "Overfitting and regularization" | Intuitive explanation of overfitting in the context of neural networks. Free online. | ★★ |
| **ISLR** — James et al. | Section 2.2, "Assessing Model Accuracy" | The overfitting-underfitting tradeoff explained very accessibly with the polynomial example. (The section uses the terms "bias" and "variance" — we'll formalize these in Week 5. For now, read for intuition.) Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.3, "Model Selection" and Section 1.5, "Decision Theory" | How to think about generalization and model complexity. The polynomial curve fitting example (Section 1.1) is worth reading now. | ★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Chapter 2, "A Formal Learning Model" and Chapter 3, "A Formal Model — The Statistical Learning Framework" | Rigorous treatment of the learning problem, ERM, and generalization. | ★★★ |
| **"Understanding Deep Learning Requires Rethinking Generalization"** — Zhang et al. (2017) | Sections 1–3 | Shows that neural networks can memorize random data. Provocative. This is also the Week 18 suggested paper — reading just the abstract and intro now is fine. | ★★★ |

---

## 6. The Overfitting-Underfitting Tradeoff

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" | Best accessible explanation. (This section uses the terms "bias" and "variance" — we'll formalize these in Week 5. For now, read it for the intuition about overfitting and underfitting.) Free. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 5, "Generalization" | Intuitive version. Free. | ★ |

> **Note:** The formal "bias-variance decomposition" requires probability, which we cover in Week 5. For now, focus on the intuition: too-simple models are consistently wrong (underfit), too-complex models are unreliable (overfit). The mathematical treatment is in **PRML** Section 3.2 and **ESL** Section 7.3 — save these for after Week 5.

---

## 7. Empirical Risk Minimization (ERM)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Section 2.1, "A Formal Model" and Section 9.1, "Learning via Uniform Convergence" | The formal definition of ERM and the conditions under which it works. This is the theoretical ML perspective. | ★★★ |
| **ESL** — Hastie et al. | Section 2.7, "Classes of Restricted Estimators" | How restricting the hypothesis space relates to ERM and generalization. | ★★★ |
| **Vapnik, "The Nature of Statistical Learning Theory"** | Chapter 1, "Learning and Statistical Inference" | Vapnik is the co-inventor of SVMs and a key figure in statistical learning theory. Philosophical and mathematical. | ★★★★ |

---

## 8. Mitchell's Definition of Learning

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Machine Learning** — Tom Mitchell | Chapter 1, Section 1.1, "Well-Posed Learning Problems" | The original statement of the T, E, P definition. The checkers-playing example. | ★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Section 2.1 | A more formal version of the same idea. | ★★★ |

---

## 9. Probability Perspective (Preview for Week 5)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.4, "Polynomial Curve Fitting Revisited" — the probabilistic version | Shows how the squared error loss arises from a Gaussian noise assumption. This is the key connection we'll make in Week 4. | ★★ |
| **Mathematics for Machine Learning** — Deisenroth et al. | Section 6.7, "Maximum Likelihood Estimation" | Clean derivation of MLE. Good preparation for Week 4. | ★★ |
| **Information Theory, Inference, and Learning Algorithms** — MacKay | Chapter 2, "Probability, Entropy, and Inference" | A beautiful, physical approach to probability and information. Free PDF. Preview of Week 5. | ★★★ |

---

## 10. Optimization Perspective (Preview for Week 3)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 4.3, "Gradient-Based Optimization" | Intuitive introduction to gradient descent. Good preparation for Week 3. | ★★ |
| **Mathematics for Machine Learning** — Deisenroth et al. | Section 7.1, "Optimization Using Gradient Descent" | Mathematical derivation of gradient descent. | ★★ |
| **ESL** — Hastie et al. | Section 4.5.2, "Piecewise Linear Networks" (discusses optimization) | More advanced, but shows how optimization fits into the bigger picture. | ★★★ |

---

## Quick-Reference: Best Starting Points by Student Level

### For Students Who Want the Big Picture (Accessible)

1. **ISLR**, Chapter 2 — "Statistical Learning" ★ — Best overall introduction
2. **A Course in Machine Learning**, Chapter 1 ★ — Friendly and free
3. **Michael Nielsen's book**, Chapter 1 ★★ — Great for neural network intuition

### For Students Who Want Mathematical Rigor

1. **PRML**, Sections 1.1–1.3 ★★ — The gold standard
2. **Understanding Machine Learning**, Chapter 2 ★★★ — Formal learning theory
3. **Mathematics for Machine Learning**, Chapter 8 ★★ — Linear algebra perspective

### For Students Who Want to Go Very Deep

1. **ESL**, Chapter 2 ★★★ — Statistical learning theory
2. **MacKay's book**, Chapter 2 ★★★ — Information-theoretic perspective
3. **Understanding Machine Learning**, Chapters 2–6 ★★★ — PAC learning, VC dimension, generalization bounds

---

## How to Use These References

1. **Don't read everything.** Pick one reference that matches your level and read the indicated section.
2. **Read with the handout open.** The handout is your primary material. References fill gaps or go deeper.
3. **Focus on examples and figures** on first reading. Come back to proofs later.
4. **If a reference uses notation you don't understand**, check the notation table in the handout (Section 2.1). If it's different from our notation, translate it.
5. **If you're confused by a reference**, ask in class or office hours. Different authors explain the same concept differently — sometimes a second explanation clicks.

---

## Reference Abbreviation Key

| Abbreviation | Full Title | Authors | Free? |
|--------------|-----------|---------|-------|
| PRML | Pattern Recognition and Machine Learning | Bishop (2006) | No (but widely available) |
| ESL | The Elements of Statistical Learning | Hastie, Tibshirani, Friedman (2009) | Yes: hastie.su.domains/ElemStatLearn/ |
| ISLR | An Introduction to Statistical Learning | James, Witten, Hastie, Tibshirani (2021) | Yes: statlearning.com |
| D2L | Dive into Deep Learning | Zhang, Lipton, Li, Smola (2023) | Yes: d2l.ai |
| Understanding ML | Understanding Machine Learning: From Theory to Algorithms | Shalev-Shwartz & Ben-David (2014) | Yes: authors' website |
| MML | Mathematics for Machine Learning | Deisenroth, Faisal, Ong (2020) | Yes: mml-book.github.io |
| Daumé | A Course in Machine Learning | Hal Daumé III (2017) | Yes: ciml.info |
| Nielsen | Neural Networks and Deep Learning | Michael Nielsen (2015) | Yes: neuralnetworksanddeeplearning.com |
| Goodfellow | Deep Learning | Goodfellow, Courville, Bengio (2016) | Yes: deeplearningbook.org |
| Sutton & Barto | Reinforcement Learning: An Introduction (2nd ed.) | Sutton & Barto (2018) | Yes: incompleteideas.net |
| MacKay | Information Theory, Inference, and Learning Algorithms | David MacKay (2003) | Yes: inference.org.uk/mackay/itila/ |
| Mitchell | Machine Learning | Tom Mitchell (1997) | No |
| Burkov | The Hundred-Page Machine Learning Book | Andriy Burkov (2019) | No (but very short) |
| Vapnik | The Nature of Statistical Learning Theory | Vladimir Vapnik (2000) | No |
