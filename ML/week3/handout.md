# Week 3 Handout: Overfitting & Regularization — Going Deeper

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 3 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** Week 1 (ML framework, overfitting/underfitting concept, hypothesis space), Week 2 (scalar linear regression, OLS, MSE, ridge regression, R²)

---

## 1. Motivation

### 1.1 Where We Left Off

Last week we built our first complete ML model: scalar linear regression. We derived the OLS solution ($w^* = \text{Cov}(x,y)/\text{Var}(x)$, $b^* = \bar{y} - w^*\bar{x}$), introduced ridge regression as a regularized variant, and saw a preview of overfitting with polynomial features.

This week we go **deeper**. Overfitting is the single most important concept in machine learning — every algorithm, every technique, every research paper ultimately grapples with it. We need to understand it mechanistically, not just as a buzzword.

### 1.2 The Central Question

> **If training error always goes down when we make the model more complex, why doesn't the most complex model always win?**

This week we answer this question rigorously (without calculus — the formal bias-variance decomposition comes in Week 5 with probability). We'll see:

- **Polynomial regression** as a way to make linear models nonlinear
- **The training/test gap** — why it appears and what it means
- **Regularization in depth** — ridge, lasso, and the geometry of each
- **The complexity dial** — how degree, λ, and (later) k, depth, and dropout are all the same knob

### 1.3 Why This Matters

Every ML interview, every IOAI problem, every real-world ML project involves the overfitting-underfitting tradeoff. The students who deeply understand this — not just as a definition but as a mechanism — have a massive advantage.

---

## 2. Polynomial Regression: Linear in Parameters, Nonlinear in Features

### 2.1 The Idea

The model $\hat{y} = wx + b$ is linear in $x$. But what if the relationship between $x$ and $y$ is curved? We can make the model nonlinear in $x$ while keeping it **linear in the parameters**:

$$\hat{y} = w_d x^d + w_{d-1} x^{d-1} + \ldots + w_1 x + w_0$$

This is still "linear regression" — we've just replaced the single feature $x$ with $d$ features: $x, x^2, \ldots, x^d$. The OLS machinery from Week 2 applies (in matrix form, which we'll see in Week 8). For now, we work with the scalar intuition.

### 2.2 The Key Tradeoff: Degree vs. Data

With $n$ data points and a polynomial of degree $d$ ($d+1$ parameters):

| Condition | What happens |
|-----------|-------------|
| $d+1 \ll n$ | Model can't fit all patterns — some error remains (potential underfitting) |
| $d+1 \approx n$ | Model can fit the data well — good if the pattern is polynomial |
| $d+1 = n$ | Model passes through every point exactly — zero training error |
| $d+1 > n$ | Infinitely many polynomials fit perfectly — the model is underdetermined |

### 2.3 Visual Example

```
  5 data points, roughly following y = 0.5x² + noise

  Degree 1 (line):              Degree 4 (through all points):
  y                             y
  │      •                      │        •
  │    • ──── line              │      • ╱╲ •
  │   • ───                     │    •   ╲╱  •
  │     •                       │  •  ╱╲╱
  │       •                     │
  └──────── x                   └──────── x
  Training error: moderate      Training error: 0
  Test error: moderate          Test error: HIGH (wild oscillations)
  
  Degree 2 (quadratic):         Degree 10 (way too complex):
  y                             y
  │      •                      │        •
  │    • ── good fit            │      • ╲╱╲╲╱ •
  │   • ──                      │    •  ╱╲╱╲╲╱╲╱
  │     • ─                     │  •  ╱╲╱╲╲╱╲╱╲
  │       •                     │
  └──────── x                   └──────── x
  Training error: low           Training error: 0
  Test error: low               Test error: VERY HIGH
```

### 2.4 The Fundamental Observation

> **Training error is a monotonically decreasing function of model complexity.** As you increase the polynomial degree, training error can only go down (or stay the same). It never goes up.

This is because a higher-degree polynomial can always represent everything a lower-degree one can (just set the extra coefficients to zero) plus more.

> **But test error is NOT monotonic.** It first decreases (the model captures the real pattern), then increases (the model starts fitting noise). This is the **generalization gap**.

### 2.5 Why Does the Test Error Go Up?

When $d+1 \geq n$, the polynomial has enough flexibility to pass through every training point exactly. But the data contains **noise** — random fluctuations that don't reflect the true underlying pattern. By fitting every point exactly, the model is **memorizing noise**, not learning signal.

Between data points, the polynomial oscillates wildly to hit every point. These oscillations are the model "inventing" patterns where none exist. New data points (from the test set) fall in these oscillation regions and get terrible predictions.

### 2.6 The Memorization Analogy

- **Underfitting (degree 1):** Student who didn't study. Fails both practice test and real test.
- **Good fit (degree 2):** Student who understood the concepts. Does well on both.
- **Overfitting (degree n−1):** Student who memorized the practice test answers word-for-word. Perfect on practice test, fails the real test because the questions are different.

---

## 3. The Generalization Gap

### 3.1 Training Error vs. Test Error

Let's define:
- **Training error** ($R_{\text{train}}$): the MSE on the training data (the data the model was fit on).
- **Test error** ($R_{\text{test}}$): the MSE on new, unseen data (the test set).
- **Generalization gap**: $R_{\text{test}} - R_{\text{train}}$.

### 3.2 The Three Regimes

| Model complexity | $R_{\text{train}}$ | $R_{\text{test}}$ | Gap | Status |
|-----------------|--------------------|--------------------|-----|--------|
| Too low (degree 1) | High | High | Small | Underfitting |
| Just right (degree 2) | Moderate | Moderate | Small | Good fit |
| Too high (degree n−1) | ≈ 0 | High | Large | Overfitting |

### 3.3 The Complexity Curve

```
  Error
    │
    │  R_test ╱╲
    │        ╱  ╲    ← overfitting zone
    │       ╱    ╲
    │      ╱      ╲
    │     ╱        ╲
    │    ╱          ╲
    │   ╱            ╲
    │  ╱   R_train    ╲
    │ ╱    (always ↓)  ╲
    │╱                   ╲
    │
    └─────────────────────── Complexity (degree)
         ↑          ↑
      underfit    sweet spot
       zone
```

This U-shaped test-error curve is the **most important figure in machine learning**. Every model — not just polynomials — produces this shape. The art of ML is finding the sweet spot.

### 3.4 Diagnosing the Problem

Given a model's training and test errors, you can diagnose:

| Symptom | Diagnosis | Prescription |
|---------|-----------|-------------|
| Both high, small gap | Underfitting | Increase complexity (higher degree, more features) |
| Low train, high test, large gap | Overfitting | Decrease complexity or add regularization |
| Both low, small gap | Good fit | Done! (Or you got lucky — check with more data) |

> **This diagnostic table is exam-critical.** You must be able to look at training/test errors and immediately identify the problem.

---

## 4. Ridge Regression Revisited — In Depth

### 4.1 Recap from Week 2

Ridge regression adds a penalty for large weights:

$$R_{\text{ridge}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2 + \lambda w^2$$

The ridge solution (scalar form):

$$w^*_{\text{ridge}} = \frac{\text{Cov}(x, y)}{\text{Var}(x) + \lambda}, \qquad b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \cdot \bar{x}$$

### 4.2 Why Does Ridge Help?

When we use polynomial features, some coefficients become very large (to create the wild oscillations that fit noise). Ridge penalizes large coefficients, **preventing the oscillations**.

- $\lambda = 0$: OLS. The model can overfit freely.
- $\lambda$ small: Slight penalty. Weights are somewhat constrained.
- $\lambda$ moderate: The sweet spot. Weights are nonzero but controlled. The model fits the signal but can't fit noise.
- $\lambda \to \infty$: $w \to 0$. The model predicts $\bar{y}$ for everything — extreme underfitting.

### 4.3 The Bias-Variance Intuition (Without Probability)

We can understand the effect of $\lambda$ without the formal probability-based decomposition (which comes in Week 5):

| | $\lambda = 0$ (OLS) | $\lambda$ moderate (ridge) | $\lambda \to \infty$ |
|---|---|---|---|
| **Training error** | Lowest | Slightly higher | Highest (≈ Var(y)) |
| **Test error** | Can be high (overfit) | Lowest (sweet spot) | High (underfit) |
| **Weights** | Can be large | Moderate | ≈ 0 |
| **Stability** | Low (changes a lot with different training data) | Moderate | High (always predicts ȳ) |
| **Bias** (systematic error) | Low | Moderate | High |
| **Variance** (sensitivity to data) | High | Moderate | Low |

> **Key intuition:** OLS has low bias (it tries hard to fit the data) but high variance (it fits noise, so it changes wildly with different data). Ridge trades a small increase in bias for a large decrease in variance. The net effect is lower test error.

### 4.4 Choosing λ: The Validation Curve

How do we pick the right $\lambda$? We try several values and plot the validation error:

```
  Validation error
    │
    │  ╱╲
    │ ╱  ╲
    │╱    ╲
    │      ╲──────
    │
    └────────────── λ (log scale)
    0   small   large
    
    ← overfit  sweet  underfit →
    → spot
```

- Small $\lambda$: validation error is high (overfitting, like OLS).
- Moderate $\lambda$: validation error is minimized (sweet spot).
- Large $\lambda$: validation error increases (underfitting).

We choose the $\lambda$ that minimizes validation error. (We'll formalize this with cross-validation in Week 4.)

### 4.5 Ridge with Polynomial Features

When we use polynomial features ($x, x^2, \ldots, x^d$), ridge applies the penalty to **all** coefficients:

$$R_{\text{ridge}} = \frac{1}{n}\sum_i (w_d x_i^d + \ldots + w_1 x_i + w_0 - y_i)^2 + \lambda(w_1^2 + w_2^2 + \ldots + w_d^2)$$

Note: the intercept $w_0 = b$ is typically **not** regularized. It just shifts the prediction — it doesn't contribute to overfitting in the same way.

### 4.6 Worked Example: Ridge on Polynomials

**Data:** 8 points following $y \approx 0.3x^2$ with noise:
$(1, 0.5), (2, 1.2), (3, 2.8), (4, 4.8), (5, 7.5), (6, 10.8), (7, 14.7), (8, 19.2)$

**Model:** Degree-7 polynomial (8 parameters, 8 data points → can fit exactly)

| $\lambda$ | Training MSE | Test MSE (on 8 new points) | Behavior |
|-----------|-------------|---------------------------|----------|
| 0 (OLS) | 0.000 | 52.3 | Wildly overfits |
| 0.01 | 0.002 | 3.1 | Much better |
| 0.1 | 0.15 | 1.8 | Good fit |
| 1.0 | 1.2 | 2.5 | Slight underfit |
| 10 | 8.5 | 9.1 | Underfitting |
| 100 | 25.3 | 26.0 | Severe underfitting |

The sweet spot is around $\lambda = 0.1$. Notice how training MSE increases monotonically with $\lambda$, but test MSE has a U-shape.

---

## 5. L1 Regularization (Lasso) — In Depth

### 5.1 The Lasso Penalty

Instead of penalizing $w^2$ (L2/ridge), we penalize $|w|$ (L1/lasso):

$$R_{\text{lasso}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2 + \lambda |w|$$

In the multi-feature case: $\lambda \sum_j |w_j|$ instead of $\lambda \sum_j w_j^2$.

### 5.2 Why Lasso Gives Sparsity

The key difference between L1 and L2 is the **geometry of the constraint**:

- **L2 (Ridge):** The constraint $\|\mathbf{w}\|^2 \leq t$ is a **ball** (circle in 2D, sphere in 3D). The ridge solution touches the ball at the closest point to OLS — usually **not on an axis**, so all weights are nonzero (but small).

- **L1 (Lasso):** The constraint $\|\mathbf{w}\|_1 \leq t$ is a **diamond** (cross-polytope). The diamond has **corners on the axes**. The lasso solution often lands on a corner, where some weights are **exactly zero**.

```
     L2 (Ridge)                    L1 (Lasso)
        w₂                            w₂
        │  ╱                          │  ╱
        │ ╱●  ← solution              │●  ← solution (on a corner!)
        │╱╲                           │╲ ╲
   ─────●──●──── w₁             ─────●  ●──── w₁
       ╱│╱                           ╱│ ╲
      ╱ │                          ╱  │  ╲ ← diamond
     ●  │                         ●   │   ●
        │                              │
```

When the solution lands on a corner of the L1 diamond, some $w_j = 0$, meaning feature $j$ is **eliminated**. Lasso performs **feature selection** automatically.

### 5.3 No Closed Form for Lasso

Unlike ridge, lasso has **no closed-form solution** because $|w|$ is not differentiable at $w = 0$ (it has a "corner" — the left derivative is $-1$ and the right derivative is $+1$). Setting the gradient to zero doesn't work at the nondifferentiable points.

This is exactly WHY lasso produces sparsity: the optimum often occurs AT a corner (a nondifferentiable point where some $w_j = 0$).

> **Connection to future weeks:** Lasso requires iterative optimization (coordinate descent or proximal gradient). When we learn gradient descent in Week 6, we'll understand how to handle nonsmooth functions with subgradient methods.

### 5.4 Ridge vs. Lasso: When to Use Each

| Property | Ridge (L2) | Lasso (L1) |
|----------|-----------|------------|
| Penalty | $\lambda \sum w_j^2$ | $\lambda \sum |w_j|$ |
| Constraint shape | Ball (sphere) | Diamond (cross-polytope) |
| Solution | Closed-form | Iterative (no closed form) |
| Sparsity | No (weights small but nonzero) | Yes (some weights exactly 0) |
| Feature selection | No | Yes |
| When to use | Many small effects | Few important features |
| Geometric intuition | Shrinks toward origin | Shrinks toward axes |

### 5.5 Elastic Net: Best of Both

**Elastic Net** combines L1 and L2:

$$R_{\text{elastic}} = \text{MSE} + \lambda_1 \sum |w_j| + \lambda_2 \sum w_j^2$$

- Gets sparsity from L1 (feature selection)
- Gets stability from L2 (handles correlated features better — L1 alone tends to pick one of two correlated features randomly)
- The constraint shape is a "rounded diamond" — between the L1 diamond and the L2 circle

---

## 6. The Complexity Dial: A Unifying Principle

### 6.1 Every Model Has a Complexity Knob

The most important insight of this week: **every ML model has a parameter that controls the overfitting-underfitting tradeoff**. They're all the same knob, just dressed differently.

| Model | Complexity knob | Low complexity (underfit) | High complexity (overfit) |
|-------|-----------------|--------------------------|--------------------------|
| Polynomial regression | Degree $d$ | $d = 1$ (line) | $d = n-1$ (through all points) |
| Ridge regression | $\lambda$ | $\lambda \to \infty$ ($w \to 0$) | $\lambda = 0$ (OLS) |
| Lasso | $\lambda$ | $\lambda \to \infty$ ($w \to 0$) | $\lambda = 0$ (OLS) |
| k-NN (Week 9) | $k$ | $k = n$ (predict ȳ) | $k = 1$ (memorize) |
| Decision trees (Week 10) | Depth | Depth 1 (stump) | Depth ∞ (memorize) |
| Neural networks (Week 15) | Number of parameters | Few neurons | Millions of neurons |

### 6.2 The Universal Curve

No matter what model or what complexity knob, the test error curve always has the same shape:

```
  Error
    │
    │  Test ╱╲
    │      ╱  ╲
    │     ╱    ╲
    │    ╱      ╲
    │   ╱        ╲
    │  ╱ Train    ╲
    │ ╱  (always ↓) ╲
    │╱                ╲
    └────────────────── Complexity
```

The x-axis might be "degree," "1/λ," "1/k," "depth," or "number of parameters" — but the shape is always the same. **This is the most important picture in ML.**

### 6.3 The Art of ML

The art of machine learning is:
1. Choosing the right model (which family of functions to search over)
2. Setting the complexity knob to the right value (not too simple, not too complex)
3. Measuring test error properly to know when you've found the sweet spot (Week 4)

---

## 7. Residual Analysis (Brief)

### 7.1 What Residuals Tell Us

The residuals $e_i = y_i - \hat{y}_i$ contain the information the model **couldn't** capture. Analyzing them reveals whether the model is adequate:

| Residual pattern | Diagnosis | Fix |
|-----------------|-----------|-----|
| Random scatter around 0 | Good fit — residuals are noise | Done! |
| Clear curve (e.g., U-shape) | Underfitting — model misses nonlinear pattern | Add polynomial features |
| Increasing spread | Heteroscedasticity — noise varies with x | Consider weighted regression (advanced) |
| Outliers | Data errors or genuinely extreme points | Investigate; consider robust loss (Huber) |

### 7.2 Visual Residual Analysis

```
  Good fit (random residuals):     Underfit (pattern in residuals):
  
  e                                e
  │  • •                           │      •
  │•   •                           │    •   •
  │ • •                            │  •       •  ← U-shape:
  │  • •                           │•           •  model misses curve
  │    •                           │
  └────── x                        └────────── x
```

If residuals show a pattern, the model is **systematically** wrong — it's underfitting. If residuals are random, the model has captured all the signal.

### 7.3 Connection to Week 2

Recall from Week 2: the OLS residuals sum to zero and are uncorrelated with $x$. If the residuals ARE correlated with $x$ (show a pattern), it means a linear model isn't capturing the relationship — we need polynomial features or a different model.

---

## 8. The Probabilistic Perspective (Preview — No Probability Required)

### 8.1 Where Do Loss Functions Come From?

You might wonder: is MSE the "right" loss? What about absolute error, or other choices?

**The answer (preview):** MSE is not arbitrary. It's the loss you get when you assume the noise in your data follows a **Gaussian (bell curve) distribution**. We'll prove this in Week 5 using Maximum Likelihood Estimation (MLE).

Similarly:
- **Ridge** corresponds to a "prior belief" that weights should be small (MAP with Gaussian prior — Week 5).
- **Lasso** corresponds to a "prior belief" that most weights should be zero (MAP with Laplace prior — Week 5).
- **Absolute error** corresponds to assuming noise follows a **Laplace distribution** (heavier tails than Gaussian — more robust to outliers).

### 8.2 The Triality (Updated)

| Perspective | Linear Regression | This Week's Deepening |
|-------------|-------------------|----------------------|
| **Geometry** | Projection, centroid, residuals | Residual analysis, L1/L2 constraint geometry |
| **Optimization** | Convex minimization, normal equation | The complexity dial, the validation curve |
| **Probability** | *(Coming Week 5)* | MSE ↔ Gaussian, ridge ↔ Gaussian prior, lasso ↔ Laplace prior |

### 8.3 What We're Building Toward

In Week 5, we'll formalize the **bias-variance decomposition** using probability:
- **Bias²:** how far the average prediction is from the truth (systematic error).
- **Variance:** how much predictions change with different training data (sensitivity).
- **Irreducible error:** the noise we can never predict.

$$\text{Expected test error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible error}$$

This week we built the **intuition** for this decomposition. In Week 5, we'll derive it mathematically.

---

## 9. Connections

### 9.1 What This Enables

| Next Week | How It Uses Week 3 |
|-----------|-------------------|
| Week 4: Model Evaluation | Train/test split, cross-validation to detect overfitting and choose λ/degree |
| Week 5: Probability for ML | Formal bias-variance decomposition, MLE → MSE, MAP → ridge/lasso |
| Week 6: Gradient Descent | Iterative optimization of MSE + regularization |
| Week 7: Logistic Regression | Overfitting in classification, regularization for logistic regression |
| Week 8: Matrix LR | Multi-feature ridge/lasso in matrix form |
| Week 9: k-NN | k as the complexity dial (same tradeoff, different knob) |
| Week 10: Decision Trees | Depth as the complexity dial, pruning as regularization |

### 9.2 Key Vocabulary to Master

- [ ] Polynomial regression (linear in parameters, nonlinear in features)
- [ ] Training error vs. test error
- [ ] Generalization gap
- [ ] The U-shaped test error curve
- [ ] Diagnosing underfitting vs. overfitting from errors
- [ ] Ridge regression: the λ knob, bias-variance intuition
- [ ] Lasso: sparsity, feature selection, L1 geometry
- [ ] No closed form for lasso (nondifferentiability)
- [ ] Elastic Net
- [ ] The complexity dial (degree, λ, k, depth — all the same knob)
- [ ] Residual analysis (patterns → underfitting)
- [ ] Validation curve for choosing λ
- [ ] Bias-variance intuition (without formal decomposition)

---

## 10. Worked Examples

### Example 1: Diagnosing Model Behavior

You fit three polynomial models to a dataset. You observe:

| Model | Training MSE | Test MSE |
|-------|-------------|----------|
| A (degree 1) | 15.2 | 16.1 |
| B (degree 3) | 2.1 | 3.5 |
| C (degree 15) | 0.01 | 28.7 |

**Diagnosis:**
- **Model A:** Both errors are high and similar → **underfitting**. The model is too simple (degree 1 can't capture the pattern).
- **Model B:** Both errors are low and close → **good fit**. Degree 3 captures the pattern without fitting noise.
- **Model C:** Training error ≈ 0 but test error is very high → **overfitting**. Degree 15 memorizes the training data including noise.

**Action:** Use Model B. If you want to fine-tune, try degrees 2–5 and use cross-validation (Week 4).

### Example 2: Choosing λ for Ridge Regression

You fit ridge regression (with degree-5 polynomial features) for several values of λ:

| $\lambda$ | Training MSE | Validation MSE |
|-----------|-------------|-----------------|
| 0.001 | 0.02 | 8.5 |
| 0.01 | 0.15 | 2.3 |
| 0.1 | 0.8 | 1.2 |
| 1.0 | 3.2 | 2.8 |
| 10 | 12.5 | 13.1 |
| 100 | 35.0 | 35.5 |

**Analysis:**
- Training MSE increases monotonically with λ (as expected — more regularization = worse fit).
- Validation MSE has a U-shape: high at λ=0.001 (overfitting), minimum at λ=0.1, then increases (underfitting).
- **Best λ ≈ 0.1** (lowest validation MSE).
- At λ=100, training ≈ validation ≈ Var(y) — the model predicts ȳ for everything.

### Example 3: Ridge vs. Lasso on a Feature Selection Problem

You have 20 features, but only 3 are truly relevant. You fit:

| Method | Weights | Test MSE |
|--------|---------|----------|
| OLS | All 20 nonzero, some very large | 15.3 (overfit) |
| Ridge (λ=1) | All 20 nonzero, but small | 5.2 |
| Lasso (λ=1) | 3 nonzero, 17 exactly zero | 3.8 |
| Elastic Net (λ₁=0.5, λ₂=0.5) | 4 nonzero, 16 zero | 3.9 |

**Analysis:**
- OLS overfits — too many features, not enough data.
- Ridge helps but keeps all features (no sparsity).
- Lasso is best — it correctly identifies the 3 relevant features and zeros out the rest.
- Elastic Net is close to lasso — useful if the 3 relevant features are correlated (lasso might pick only 2 of them).

---

## 11. Exercises

### [Basic]

**E1.** You fit polynomials of degree 1, 3, and 10 to a dataset with 15 points. You get:
- Degree 1: train MSE = 20, test MSE = 22
- Degree 3: train MSE = 3, test MSE = 4
- Degree 10: train MSE = 0.001, test MSE = 15

For each model, state: (a) Is it underfitting, overfitting, or good fit? (b) What is the generalization gap? (c) Which model would you deploy?

**E2.** Explain in 2-3 sentences: why does training error always decrease when you increase polynomial degree, but test error does not?

**E3.** You have a ridge regression model with $\lambda = 0.001$. The training error is very low but the test error is high. What should you do? (Be specific — what parameter do you change and in which direction?)

**E4.** Explain the difference between L1 and L2 regularization in terms of: (a) the penalty formula, (b) the constraint geometry, (c) whether they produce sparsity.

### [Intermediate]

**E5.** You are fitting a polynomial model and observe the residuals show a clear U-shaped pattern. What does this tell you? What should you do to fix it?

**E6.** A classmate says: "I'll just use the highest-degree polynomial possible and add a tiny bit of ridge regularization. That way I get the flexibility of high degree and the safety of regularization." Is this a good strategy? What are the potential problems?

**E7.** You have 50 data points and 50 features (plus bias = 51 parameters). OLS gives zero training error. You add ridge with $\lambda = 10$ and training error becomes 2.3, but test error drops from 25 to 4.1. Explain what happened. Why did training error go up but test error go down?

**E8.** Fill in the table:

| $\lambda$ | Bias | Variance | Training error | Test error |
|-----------|------|----------|----------------|------------|
| 0 (OLS) | ? | ? | ? | ? |
| moderate | ? | ? | ? | ? |
| $\to \infty$ | ? | ? | ? | ? |

Use "low," "moderate," or "high" for each cell.

### [★ Advanced]

**E9.** Prove that training error is a monotonically non-increasing function of polynomial degree $d$. That is, if $d_1 < d_2$, then $R_{\text{train}}(d_2) \leq R_{\text{train}}(d_1)$.  
*(Hint: A degree-$d_1$ polynomial is a special case of a degree-$d_2$ polynomial. Think about what the optimizer can do with the extra parameters.)*

**E10.** Consider the "double descent" phenomenon. In the classical regime (up to the interpolation threshold $d+1 = n$), test error follows the U-curve. But in the over-parameterized regime ($d+1 \gg n$), test error can **decrease again**.  
(a) Sketch the full double-descent curve (test error vs. degree).  
(b) Why might having MORE parameters than data points lead to BETTER generalization? (This is counterintuitive.)  
(c) What does this imply about the classical overfitting-underfitting tradeoff? Is it wrong?  
*(This is a preview of Week 18 — Generalization Theory. You don't need to solve it rigorously, just reason qualitatively.)*

**E11.** ★★ The **bias-variance decomposition** (formal treatment in Week 5) decomposes expected test error as:
$$\text{Error} = \text{Bias}^2 + \text{Variance} + \text{Noise}$$
Even without the formal derivation, you can reason about each term:
(a) For OLS (λ=0): is bias high or low? Is variance high or low?
(b) For ridge with moderate λ: what happens to bias? To variance?
(c) For ridge with λ→∞: what happens to bias? To variance?
(d) The "sweet spot" λ minimizes Bias² + Variance. Sketch this as a function of λ and explain why the sum has a minimum.
(e) Why can't we reduce the "Noise" term? What is it?

**E12.** ★★ Consider two loss functions: $L_2(\hat{y}, y) = (\hat{y} - y)^2$ and $L_1(\hat{y}, y) = |\hat{y} - y|$.  
(a) Which is more sensitive to outliers? Why? (An outlier is a data point with a very large error.)  
(b) Suppose your data has 5% corrupted points (outliers). Which loss would you prefer?  
(c) The **Huber loss** transitions from L2 (for small errors) to L1 (for large errors). Why is this a good compromise?  
(d) Connect this to the L1 vs. L2 regularization discussion: is there a relationship between using L1 loss and L1 regularization? (They're different concepts, but the geometry is related.)

---

## 12. Summary

### Key Equations

> **Polynomial model:** $\hat{y} = w_d x^d + \ldots + w_1 x + w_0$ (linear in parameters, nonlinear in features)

> **Ridge (scalar):** $w^*_{\text{ridge}} = \frac{\text{Cov}(x, y)}{\text{Var}(x) + \lambda}$

> **Generalization gap:** $R_{\text{test}} - R_{\text{train}}$

> **The complexity dial:** degree ↑, λ ↓, k ↓, depth ↑ → more complex → more overfitting risk

### Key Intuition (If You Remember Nothing Else...)

1. **Training error always decreases with complexity. Test error has a U-shape.** The gap between them is the generalization gap.
2. **Overfitting = fitting noise.** The model memorizes the training data, including random fluctuations that don't generalize.
3. **Regularization constrains the model.** Ridge shrinks weights toward zero (L2 ball). Lasso pushes weights to exactly zero (L1 diamond → sparsity).
4. **Every model has a complexity dial.** Degree, λ, k, depth — they all control the same tradeoff.
5. **Diagnose from errors:** both high → underfit; low train + high test → overfit; both low → good.
6. **Residuals reveal underfitting.** If they show a pattern, the model is missing something.
7. **The bias-variance tradeoff** (formal in Week 5): regularization increases bias but decreases variance. The sweet spot minimizes their sum.

---

*Next week: Model Evaluation & Validation. We'll learn how to properly measure generalization — train/test splits, cross-validation, and the metrics (accuracy, precision, recall, F1, ROC/AUC) that tell you whether your model is actually good. The overfitting we've seen this week gets its formal treatment with proper evaluation methodology.*
