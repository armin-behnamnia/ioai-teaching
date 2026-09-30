# Week 2 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. These are optional — all required material is in the handout. References are organized by topic and tagged with difficulty.

---

## 1. Linear Regression Basics

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Chapter 3, "Linear Regression," Sections 3.1–3.2 | The most accessible introduction to linear regression. Simple regression (one predictor) is in 3.1 — this is exactly our scalar case. The advertising example is excellent. Free PDF. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 7, "Linear Regression" | Friendly, conversational introduction. Derives the solution and connects to the ML framework from Week 1. Free. | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Section 3.1, "Linear Regression" | Very concise overview of the model, loss, and solution. Good as a quick reference. | ★ |
| **Mathematics for Machine Learning** — Deisenroth et al. | Section 9.2, "Linear Regression" | Clean derivation with explicit algebra. Uses vector notation, but the scalar case is a special case. Free. | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 3.1, "Linear Basis Function Models" | The canonical treatment. Bishop uses the polynomial curve-fitting example (Section 1.1) as motivation. The derivation is calculus-based but clear. | ★★ |
| **ESL** — Hastie et al. | Section 3.2, "Linear Regression Models and Least Squares" | The statistical perspective. More formal than ISLR. Derives OLS from the matrix normal equation. Free. | ★★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Section 9.1, "Linear Predictors" | Formal learning theory perspective on linear regression. Connects to the ERM framework from Week 1. Free. | ★★★ |

---

## 2. The OLS Derivation (Algebraic / Scalar)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.1.1, "Regression with a Single Predictor" | Derives the simple linear regression coefficients using the same covariance/variance formulas we derived in class. Accessible. Free. | ★ |
| **MML** — Deisenroth et al. | Section 9.2.1, "Parameter Estimation" | Derives OLS via both the normal equation and gradient descent. Good bridge to the matrix version (Week 8). Free. | ★★ |
| **PRML** — Bishop | Section 3.1.1, "Maximum Likelihood and Least Squares" | Derives OLS from the probabilistic perspective (Gaussian noise → MSE). This is the derivation we previewed in class and will do formally in Week 5. | ★★ |
| **ESL** — Hastie et al. | Section 3.2.1, "Least Squares" | The matrix derivation. Save for Week 8, but worth skimming now to see where the scalar formulas come from. Free. | ★★★ |

> **Note:** Our derivation in class used only algebra (completing the square) — no calculus. Most textbooks use calculus (setting the derivative to zero). Both approaches give the same answer. If you're comfortable with derivatives, the calculus approach is faster. If not, our algebraic approach is fully rigorous.

---

## 3. Regularization: Ridge Regression and Lasso

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 6.2, "Shrinkage Methods" — Sections 6.2.1 (Ridge) and 6.2.2 (Lasso) | The best accessible introduction to ridge and lasso. Clear examples, minimal math. The credit dataset example is great. Free. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 7.3, "Regularization" | Friendly introduction to the regularization idea. Connects to the overfitting discussion. Free. | ★ |
| **An Introduction to Statistical Learning** — ISLR (Python edition) | Section 6.2 | Same as above, with Python code. (This course doesn't use code, but the explanations are excellent.) | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 3.1.4, "Regularized Least Squares" and Section 3.3, "Bayesian Linear Regression" | Derives ridge from the Bayesian perspective (Gaussian prior on weights). This is the probabilistic meaning we previewed in class. | ★★ |
| **ESL** — Hastie et al. | Section 3.4.1, "Ridge Regression" and Section 3.4.2, "The Lasso" | The canonical statistical treatment. Derives the ridge solution and discusses the lasso geometry (diamond vs. circle). Free. | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2.3, "Regularized Least Squares" | Clean derivation of ridge using the matrix form. The MAP/Bayesian interpretation is in Section 9.2.4. Free. | ★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Chapter 13, "Stochastic Gradient Descent" (for regularized ERM) | Formal treatment of regularized learning. More theoretical than practical. Free. | ★★★ |

### The Geometry of L1 vs. L2

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.2, Figure 3.11 | The famous diagram showing why L1 (lasso) produces sparsity: the diamond constraint region hits the contours at corners, where some coefficients are exactly zero. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.4, Figure 3.4 | Similar geometric picture for L1 vs. L2. | ★★ |
| **ISLR** — James et al. | Section 6.2.2, Figure 6.7 | Accessible version of the L1 vs. L2 geometry diagram. Free. | ★ |

---

## 4. R² and Correlation

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.1.3, "Assessing the Accuracy of the Coefficients" and Section 3.2.2, "Model Fit" | Defines RSE, R², and the F-statistic for regression. Very accessible. Free. | ★ |
| **ESL** — Hastie et al. | Section 3.2.2, related discussion | Statistical perspective on R² and the relationship to correlation. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.2, related discussion on goodness of fit | Discusses the connection between R² and the Bayesian evidence framework. | ★★ |
| **Statistics** — Freedman, Pisani, Purves | Chapters 8–10 | A statistics textbook (not ML) with the best intuitive treatment of correlation, regression, and R². Highly recommended for building intuition. | ★ |

---

## 5. Overfitting in Regression

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" and Section 6.1, "Subset Selection" | How model complexity affects overfitting in regression. The polynomial example (Figure 2.9) is a great visual. Free. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 5, "Generalization" | Accessible discussion of overfitting in the context of linear models. Free. | ★ |
| **Neural Networks and Deep Learning** — Nielsen | Chapter 1, "Overfitting and Regularization" | Intuitive explanation of overfitting and how regularization combats it. Free. | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.1, "Polynomial Curve Fitting" | THE classic example of overfitting in regression. Bishop fits polynomials of increasing degree and shows the training/test error curves. We replicated this in our Desmos demo. | ★★ |
| **ESL** — Hastie et al. | Section 2.9, "Model Selection" and Section 7.2–7.3, "Bias-Variance Decomposition" | The statistical theory of overfitting in regression. The formal bias-variance decomposition is here (we'll cover it in Week 5). Free. | ★★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Chapter 2, "A Formal Learning Model" (overfitting examples) and Chapter 4, "Learning via Uniform Convergence" | Formal definition of overfitting in the PAC learning framework. Free. | ★★★ |

---

## 6. Probability Perspective (Preview for Week 5)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.2.4, "Polynomial Curve Fitting Revisited" (the probabilistic version) | Shows how the squared error loss arises from a Gaussian noise assumption. This is the key connection we previewed in class. | ★★ |
| **PRML** — Bishop | Section 3.1.2, "Maximum Likelihood and Least Squares" | The formal derivation: maximize the Gaussian likelihood → minimize MSE. We'll do this in Week 5. | ★★ |
| **MML** — Deisenroth et al. | Section 8.3, "Maximum Likelihood Estimation" and Section 9.2.4, "Maximum Likelihood as Orthogonal Projection" | Clean derivation of MLE and its connection to least squares. Free. | ★★ |
| **Information Theory, Inference, and Learning Algorithms** — MacKay | Chapter 2, "Probability, Entropy, and Inference" and Chapter 3, "More about Inference" | A beautiful, physical approach to probability and inference. The regression discussion is insightful. Free PDF. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 5.7, "Maximum Likelihood Estimation" | The deep learning perspective on MLE. Shows how many loss functions arise from probabilistic assumptions. Free. | ★★★ |

> **Note:** The probabilistic perspective (MSE ↔ Gaussian noise, ridge ↔ Gaussian prior) is developed formally in Week 5. For now, these references are for students who want a preview. The key idea: the choice of loss function is not arbitrary — it encodes assumptions about how the data was generated.

---

## 7. Polynomial Regression and Basis Functions

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.1, "Polynomial Curve Fitting" and Section 3.1, "Linear Basis Function Models" | The canonical treatment. Polynomial features as a special case of basis functions. The overfitting demo (Figure 1.4) is worth studying. | ★★ |
| **ISLR** — James et al. | Section 7.8.1, "Polynomial Regression" and Section 7.8.2, "Step Functions" | Accessible treatment of polynomial regression and other basis function approaches. Free. | ★ |
| **ESL** — Hastie et al. | Section 5.1–5.2, "Basis Expansions" | The statistical perspective on basis functions: polynomials, splines, wavelets. Free. | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2, related discussion on feature maps | How polynomial features generalize to other basis functions. Free. | ★★ |

---

## 8. Geometric Perspective (Projection, Residuals)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.2, "Linear Regression Models and Least Squares" — especially the geometric discussion | The "regression by projection" view: OLS projects the data onto the column space. This is the matrix version of our centroid/residual properties. Free. | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2.4, "Maximum Likelihood as Orthogonal Projection" | Clean geometric derivation. Shows that OLS = orthogonal projection of $\mathbf{y}$ onto the column space of $\mathbf{X}$. Free. | ★★ |
| **PRML** — Bishop | Section 3.1.2, related geometric discussion | The geometric interpretation within the Bayesian framework. | ★★ |
| **Statistics** — Freedman, Pisani, Purves | Chapter 12, "The Regression Line" | Intuitive, non-matrix treatment of the geometric properties of regression. The centroid, residuals, and R² are explained with pictures. | ★ |

---

## Quick-Reference: Best Starting Points by Student Level

### For Students Who Want the Big Picture (Accessible)

1. **ISLR**, Chapter 3, Sections 3.1–3.2 ★ — Best overall introduction to simple and multiple regression
2. **ISLR**, Chapter 6, Section 6.2 ★ — Best accessible introduction to ridge and lasso
3. **A Course in Machine Learning**, Chapter 7 ★ — Friendly and free
4. **Freedman, Pisani, Purves**, Chapters 8–12 ★ — Best for building statistical intuition about correlation and regression

### For Students Who Want Mathematical Rigor

1. **PRML**, Section 3.1 ★★ — The gold standard for linear regression
2. **MML**, Section 9.2 ★★ — Clean algebraic derivation, free
3. **ESL**, Section 3.2 ★★★ — Statistical depth, free

### For Students Who Want to Go Very Deep

1. **ESL**, Sections 3.2–3.4 ★★★ — Full treatment: OLS, ridge, lasso, geometry
2. **Understanding Machine Learning**, Chapters 2, 9, 13 ★★★ — Learning theory perspective
3. **MacKay's book**, Chapters 2–3 ★★★ — Information-theoretic / Bayesian perspective

---

## How to Use These References

1. **Don't read everything.** Pick one reference that matches your level and read the indicated section.
2. **Read with the handout open.** The handout is your primary material. References fill gaps or go deeper.
3. **Focus on examples and figures** on first reading. Come back to proofs later.
4. **If a reference uses matrix notation** (vectors, matrices, transposes), don't panic. Our scalar formulas ($w^* = \text{Cov}/\text{Var}$, $b^* = \bar{y} - w\bar{x}$) are the one-variable special case. We'll cover the matrix version in Week 8.
5. **If a reference uses calculus** (derivatives, gradients), note that our derivation used only algebra. Both approaches give the same result. The calculus approach is more general; the algebraic approach is more elementary.
6. **If you're confused by a reference**, ask in class or office hours. Different authors explain the same concept differently — sometimes a second explanation clicks.

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
| MacKay | Information Theory, Inference, and Learning Algorithms | David MacKay (2003) | Yes: inference.org.uk/mackay/itila/ |
| Mitchell | Machine Learning | Tom Mitchell (1997) | No |
| Burkov | The Hundred-Page Machine Learning Book | Andriy Burkov (2019) | No (but very short) |
| Freedman et al. | Statistics (4th ed.) | Freedman, Pisani, Purves (2007) | No |
