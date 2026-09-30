# Week 3 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. These are optional — all required material is in the handout. References are organized by topic and tagged with difficulty.

---

## 1. Polynomial Regression and Basis Functions

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 7.8.1, "Polynomial Regression" and Section 7.8.2, "Step Functions" | Accessible treatment of polynomial regression as a basis function approach. Clear examples. Free PDF: statlearning.com | ★ |
| **A Course in ML** — Daumé | Chapter 7, related discussion on feature maps | How polynomial features extend linear regression to nonlinear patterns. Free: ciml.info | ★ |
| **The Hundred-Page ML Book** — Burkov | Section on polynomial features (within regression chapter) | Concise overview of how polynomial features make linear models nonlinear. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.1, "Polynomial Curve Fitting" and Section 3.1, "Linear Basis Function Models" | THE canonical example. Bishop fits polynomials of increasing degree and shows the training/test error curves. The overfitting demo (Figure 1.4) is worth studying. Polynomial features as a special case of basis functions. | ★★ |
| **ESL** — Hastie et al. | Section 5.1–5.2, "Basis Expansions" | The statistical perspective on basis functions: polynomials, splines, wavelets. Free PDF: hastie.su.domains/ElemStatLearn/ | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2, related discussion on feature maps | How polynomial features generalize to other basis functions. Clean derivation. Free: mml-book.github.io | ★★ |

> **Note:** Polynomial regression is still "linear regression" — it's linear in the parameters ($w_0, w_1, \ldots, w_d$), just nonlinear in the feature $x$. The OLS machinery applies unchanged (we just have more features). The matrix form (Week 8) makes this precise.

---

## 2. Overfitting and the Generalization Gap

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" | How model complexity affects overfitting in regression. The polynomial example (Figure 2.9) is a great visual. Free. | ★ |
| **A Course in ML** — Daumé | Chapter 5, "Generalization" | Accessible discussion of overfitting in the context of linear models. Free. | ★ |
| **Neural Networks and Deep Learning** — Nielsen | Chapter 1, "Overfitting and Regularization" | Intuitive explanation of overfitting and how regularization combats it. Free: neuralnetworksanddeeplearning.com | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.1, "Polynomial Curve Fitting" (especially Figures 1.4–1.7) | The classic demonstration: training error decreases monotonically with degree, but test error has a U-shape. The generalization gap is visible in the figures. | ★★ |
| **ESL** — Hastie et al. | Section 2.9, "Model Selection" and Section 7.2–7.3, "Bias-Variance Decomposition" | The statistical theory of overfitting in regression. The formal bias-variance decomposition (we'll cover it in Week 5). Free. | ★★★ |
| **Understanding ML** — Shalev-Shwartz & Ben-David | Chapter 2, "A Formal Learning Model" (overfitting examples) and Chapter 4, "Learning via Uniform Convergence" | Formal definition of overfitting in the PAC learning framework. Free. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 5.2, "Capacity, Overfitting and Underfitting" | The deep learning perspective on overfitting. Defines capacity, generalization gap, and the relationship to model complexity. Free: deeplearningbook.org | ★★ |

> **Note:** The U-shaped test error curve is the most important figure in machine learning. Every model — not just polynomials — produces this shape. The art of ML is finding the sweet spot. We'll see this recur with k (Week 9), tree depth (Week 10), and number of neurons (Week 15).

---

## 3. Ridge Regression In Depth

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 6.2.1, "Ridge Regression" | The best accessible introduction to ridge. Clear explanation of the shrinkage mechanism. The credit dataset example is great. Free. | ★ |
| **A Course in ML** — Daumé | Chapter 7.3, "Regularization" | Friendly introduction to the regularization idea. Connects to overfitting. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 3.1.4, "Regularized Least Squares" | Derives ridge from the optimization perspective. Shows how $\lambda$ controls the bias-variance tradeoff. Figure 3.6 shows the training/test error curves vs. $\lambda$. | ★★ |
| **ESL** — Hastie et al. | Section 3.4.1, "Ridge Regression" | The canonical statistical treatment. Derives the ridge solution, discusses the SVD perspective, and explains why ridge works. Free. | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2.3, "Regularized Least Squares" | Clean derivation of ridge using the matrix form. The MAP/Bayesian interpretation is in Section 9.2.4. Free. | ★★ |

### The Shrinkage Mechanism

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.1, Figure 3.8 | Shows how ridge shrinks the OLS coefficients toward zero as $\lambda$ increases. The "ridge path" is a key visualization. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.4, related discussion | The Bayesian interpretation: ridge = MAP with Gaussian prior. The prior "pulls" weights toward zero. (Formal treatment in Week 5.) | ★★ |
| **ISLR** — James et al. | Section 6.2.1, Figure 6.5 | Accessible version of the ridge shrinkage plot. Free. | ★ |

> **Note:** In the scalar case, $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$. The shrinkage factor $\frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$ is always in $(0, 1]$, so ridge always shrinks toward zero but never changes the sign. In the matrix case (Week 8), the shrinkage is more complex but the principle is the same.

---

## 4. Lasso (L1 Regularization) and Sparsity

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 6.2.2, "The Lasso" | The best accessible introduction to lasso. Clear explanation of sparsity and feature selection. Free. | ★ |
| **A Course in ML** — Daumé | Chapter 7.3 (continued) | Introduces L1 regularization and its difference from L2. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.2, "The Lasso" | The canonical treatment. Derives the lasso, explains the geometry, discusses why there's no closed form. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.4 (continued) and Section 3.3 (Bayesian LR) | Lasso from the Bayesian perspective: Laplace prior (vs. Gaussian prior for ridge). The sparsity arises from the sharp peak of the Laplace distribution at zero. | ★★ |
| **MML** — Deisenroth et al. | Section 9.2.3 (continued) | L1 regularization in the matrix form. Discusses the lack of a closed form and the need for iterative optimization. Free. | ★★ |

### The Geometry of L1 vs. L2

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.2, Figure 3.11 | The famous diagram showing why L1 produces sparsity: the diamond constraint hits the contours at corners, where some coefficients are exactly zero. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.4, Figure 3.4 | Similar geometric picture for L1 vs. L2. | ★★ |
| **ISLR** — James et al. | Section 6.2.2, Figure 6.7 | Accessible version of the L1 vs. L2 geometry diagram. Free. | ★ |

> **Note:** The key geometric insight: the L1 constraint ($\|\mathbf{w}\|_1 \leq t$) is a diamond with corners on the axes. The L2 constraint ($\|\mathbf{w}\|^2 \leq t$) is a ball with no corners. The lasso solution often lands on a corner (where some $w_j = 0$), while the ridge solution lands on a smooth point (all $w_j \neq 0$). No calculus needed — just geometry.

### Why No Closed Form for Lasso

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.2 (discussion of subdifferentials) | Why $|w|$ is nondifferentiable at $w = 0$ and what this means for optimization. Free. | ★★★ |
| **PRML** — Bishop | Section 3.1.4 (related discussion) | The Laplace prior and its nondifferentiability. Connects to the Bayesian view. | ★★ |

> **Note:** Lasso requires iterative optimization (coordinate descent, proximal gradient). We'll learn gradient descent in Week 6 and see how to handle nonsmooth functions with subgradient methods. The nondifferentiability is not a bug — it's the feature. The corners are where weights become zero.

---

## 5. Elastic Net

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 3.4.3 (brief mention within the lasso section) and Section 18.4 | The original elastic net paper is Zou & Hastie (2005). Combines L1 and L2 penalties. Free. | ★★★ |
| **ISLR** — James et al. | Section 6.2.3 (if covered) or related discussion | Brief accessible introduction to elastic net as a compromise between ridge and lasso. Free. | ★ |
| **PRML** — Bishop | Section 3.1.4 (related discussion) | The Bayesian perspective: elastic net corresponds to a prior that is a mixture of Gaussian and Laplace. | ★★ |

> **Note:** Elastic net combines L1 (sparsity/feature selection) with L2 (stability with correlated features). The constraint shape is a "rounded diamond." Useful when you want sparsity but have correlated features (where lasso picks one and drops the other arbitrarily).

---

## 6. Bias-Variance Intuition (Without Probability)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" | The most accessible explanation. Uses the bullseye analogy and a simple simulation. Free. | ★ |
| **Deep Learning** — Goodfellow et al. | Section 5.2, "Capacity, Overfitting and Underfitting" | Clean definitions of bias and variance without probability. The relationship to capacity is well explained. Free. | ★★ |
| **Neural Networks and Deep Learning** — Nielsen | Chapter 1 (overfitting section) | Intuitive explanation of the bias-variance tradeoff with the bullseye diagram. Free. | ★★ |

### More Rigorous (Formal Treatment — Week 5)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 7.2–7.3, "Bias-Variance Decomposition" | The formal derivation using probability. We'll cover this in Week 5. Figure 7.2 (bias-variance on simulated data) is the classic visualization. Free. | ★★★ |
| **PRML** — Bishop | Section 3.2, "The Bias-Variance Decomposition" | The Bayesian perspective on bias-variance. Figure 3.5 shows the decomposition as a function of model complexity. | ★★ |
| **Understanding ML** — Shalev-Shwartz & Ben-David | Section 5.2, "Error Decomposition" | The learning-theoretic version: approximation error (bias) vs. estimation error (variance). Free. | ★★★ |

> **Note:** This week we built the INTUITION for bias-variance (OLS: low bias, high variance; ridge: moderate bias, moderate variance; $\lambda \to \infty$: high bias, low variance). The formal mathematical decomposition using probability comes in Week 5. For now, the key takeaway: regularization trades a small increase in bias for a large decrease in variance, lowering total error.

---

## 7. The Complexity Dial (Unifying Principle)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **Deep Learning** — Goodfellow et al. | Section 5.2, "Capacity, Overfitting and Underfitting" | The concept of "capacity" as a unifying notion of model complexity. Different models have different capacity knobs. Free. | ★★ |
| **ESL** — Hastie et al. | Section 2.9 (model selection) and Section 7.2 (bias-variance) | The universal U-shaped curve appears for every complexity parameter. Free. | ★★★ |
| **"A Few Useful Things to Know about Machine Learning"** — Domingos (2012) | Section 5, "Overfitting Has Many Faces" | Overfitting manifests through different complexity knobs but is fundamentally the same phenomenon. The Week 3 suggested paper. | ★ |
| **Understanding ML** — Shalev-Shwartz & Ben-David | Chapter 2 (overfitting) and related discussion on hypothesis class size | The formal learning-theory view: larger hypothesis class = more overfitting risk. Free. | ★★★ |

> **Note:** The complexity dial is the most important unifying concept in this course. Degree, $\lambda$, $k$, depth, and number of parameters are all the same knob — they all produce the U-shaped test error curve. We'll see this recur in every subsequent model: k-NN (Week 9, knob = $k$), decision trees (Week 10, knob = depth), SVMs (Week 13–14, knob = $C$), and neural networks (Week 15–16, knob = number of parameters).

---

## 8. Residual Analysis

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.1.3, "Assessing the Accuracy of the Coefficients" (residual discussion) | How to use residual plots to diagnose model problems. Free. | ★ |
| **ESL** — Hastie et al. | Section 3.2, related discussion on residual diagnostics | The statistical perspective on residual analysis. Free. | ★★★ |
| **Statistics** — Freedman, Pisani, Purves | Chapter on "The Regression Line" (residual discussion) | Intuitive, non-technical treatment of residuals and what they reveal. Highly recommended for building intuition. | ★ |
| **PRML** — Bishop | Section 1.1 (related discussion) | Residual analysis in the context of polynomial curve fitting — shows how residual patterns reveal underfitting. | ★★ |

> **Note:** The key principle: if residuals show a PATTERN (curve, trend), the model is underfitting — it's missing signal. If residuals are RANDOM SCATTER around zero, the model has captured all the signal. This connects to Week 2's property: OLS residuals are uncorrelated with $x$. If they ARE correlated (show a pattern), we need polynomial features or a different model.

---

## 9. Domingos (2012) — Section 5: "Overfitting Has Many Faces"

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"A Few Useful Things to Know about Machine Learning"** — Domingos (2012) | Section 5, "Overfitting Has Many Faces" | Overfitting comes in multiple forms: bias vs. variance, true error vs. training error, multiple comparisons. Ridge and lasso address the parameter-count face. The Week 3 suggested paper re-read. | ★ |
| **"A Few Useful Things to Know about Machine Learning"** — Domingos (2012) | Section 2, "It's Generalization That Counts" | The fundamental goal is generalization, not training performance. Connects to the generalization gap. | ★ |

> **Note:** This week's suggested paper is a RE-READ of Domingos (2012), focusing on Section 5. In Week 2, you read the full paper. This week, Section 5 takes on new meaning: you've now seen overfitting mechanistically (polynomial degree, generalization gap) and learned the tools to combat it (ridge, lasso, the complexity dial). See `suggested_paper.md` for the full reading guide.

---

## 10. Double Descent (Preview for Week 18)

> **Note:** These references are for advanced students who want a preview of what lies beyond the U-curve. Not required for Week 3, but connected to the polynomial overfitting discussion.

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"Reconciling Modern Machine-Learning Practice and the Bias-Variance Trade-Off"** — Belkin et al. (2019) | Sections 1–3 | The double descent phenomenon: test error decreases AGAIN past the interpolation threshold. The paper that reignited interest in over-parameterized models. | ★★★ |
| **Deep Learning** — Goodfellow et al. | Section 5.2.1 (related discussion) | Brief mention of the tension between classical capacity control and modern over-parameterized models. Free. | ★★ |
| **Understanding ML** — Shalev-Shwartz & Ben-David | Chapter 4 (uniform convergence) and related discussion | The classical theory that explains the U-curve. The double descent phenomenon requires going beyond this framework. Free. | ★★★ |

---

## Quick-Reference: Best Starting Points by Student Level

### For Students Who Want the Big Picture (Accessible)

1. **ISLR**, Section 2.2.2 ★ — Best accessible explanation of the bias-variance tradeoff and the U-shaped curve
2. **ISLR**, Section 6.2.1–6.2.2 ★ — Best accessible introduction to ridge and lasso
3. **A Course in ML**, Chapter 5 ★ — Accessible discussion of overfitting and generalization
4. **Freedman, Pisani, Purves**, regression chapters ★ — Best for building statistical intuition about residuals

### For Students Who Want Mathematical Rigor

1. **PRML**, Section 1.1 ★★ — The classic polynomial curve-fitting example (overfitting made visceral)
2. **PRML**, Section 3.1.4 ★★ — Ridge and lasso from the optimization and Bayesian perspectives
3. **MML**, Section 9.2 ★★ — Clean derivation of regularized least squares, free

### For Students Who Want to Go Very Deep

1. **ESL**, Sections 3.4.1–3.4.2 ★★★ — Full treatment: ridge, lasso, geometry, SVD perspective
2. **ESL**, Section 7.2–7.3 ★★★ — Formal bias-variance decomposition (save for Week 5)
3. **Belkin et al. (2019)** ★★★ — Double descent: what lies beyond the U-curve (preview for Week 18)

---

## How to Use These References

1. **Don't read everything.** Pick one reference that matches your level and read the indicated section.
2. **Read with the handout open.** The handout is your primary material. References fill gaps or go deeper.
3. **Focus on examples and figures** on first reading. Come back to proofs later.
4. **If a reference uses matrix notation** (vectors, matrices, transposes), don't panic. Our scalar formulas are the one-variable special case. We'll cover the matrix version in Week 8.
5. **If a reference uses calculus** (derivatives, gradients), note that our derivation used only algebra. Both approaches give the same result.
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
