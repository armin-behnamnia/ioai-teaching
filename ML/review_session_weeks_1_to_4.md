# Review Session: Weeks 1–4 Exam Preparation

> **Course:** Machine Learning for IOAI Preparation  
> **Session Duration:** 2 hours (120 minutes)  
> **Purpose:** Comprehensive review and teaching of all content from Weeks 1–4 in preparation for the midterm exam  
> **Format:** Interactive lecture with worked examples, mini-exercises, and exam strategy  
> **Prerequisites:** Students have completed Weeks 1–4 handouts, quizzes, and exercises

---

## Session Overview

This review session consolidates four weeks of material into a single coherent narrative. The session is structured around the **three perspectives** introduced in Week 1 — geometry, probability (preview), and optimization — and the **central thread** that connects all four weeks: the overfitting-underfitting tradeoff.

### Timing Plan

| Time | Section | Content |
|------|---------|---------|
| 0:00–0:10 | **Opening** | Exam structure, topic map, study strategy |
| 0:10–0:30 | **Block 1** | Week 1: ML framework, ERM, hypothesis space, loss functions, generalization |
| 0:30–0:55 | **Block 2** | Week 2: Scalar linear regression, OLS derivation, ridge, R², residuals |
| 0:55–1:15 | **Block 3** | Week 3: Polynomial regression, generalization gap, L1/L2 geometry, complexity dial |
| 1:15–1:15 | *Break* | 5-minute break |
| 1:15–1:45 | **Block 4** | Week 4: Train/val/test splits, cross-validation, classification metrics, ROC/AUC, learning curves |
| 1:45–2:00 | **Block 5** | Exam strategy, common mistakes, practice questions |
| 2:00–2:00 | **Q&A** | Open questions |

---

## Block 0: Opening (10 min)

### Exam Structure

The exam has:
- **3 long-answer, multi-part questions** (20 marks each, 60 min total)
- **5 short-answer questions** (6 marks each, 30 min total)
- Topics span all four weeks, with many questions crossing week boundaries

### Topic Dependency Chain

```
Week 1: Framework          ──→  What is learning? Hypothesis space, loss, ERM, true vs. empirical risk
    ↓
Week 2: Linear Regression  ──→  OLS derivation (algebra), MSE, ridge, R², residuals, centroid
    ↓
Week 3: Overfitting Deep   ──→  Polynomial regression, generalization gap, L1/L2 geometry, complexity dial
    ↓
Week 4: Evaluation         ──→  Train/val/test, k-fold CV, confusion matrix, precision/recall/F1, ROC/AUC, learning curves
```

**The unifying thread:** Every week revolves around the same idea — *we minimize training loss, but we care about test loss; the gap is generalization; and we control it through model complexity and proper evaluation.*

### Study Strategy

1. **Master the derivations.** You must be able to derive $b^* = \bar{y} - w\bar{x}$ and $w^* = \text{Cov}(x,y)/\text{Var}(x)$ from scratch using completing the square. This is the single most important skill.
2. **Memorize the diagnostic tables.** The overfitting/underfitting diagnostic table (from training/test errors) and the bias-variance table (for $\lambda = 0$, moderate, $\infty$) are exam-critical.
3. **Understand the geometry.** L1 diamond vs. L2 circle — be able to draw and explain sparsity.
4. **Practice metric computation.** Confusion matrix → accuracy, precision, recall, F1 — this appears on every exam.

---

## Block 1: Week 1 — The ML Framework (20 min)

### 1.1 What Is Machine Learning?

**Mitchell's definition:** A computer program learns from experience E with respect to task T and performance measure P if its performance at T, as measured by P, improves with E.

**Example (spam filter):**
- T: classify emails as spam/not spam
- E: labeled training emails
- P: accuracy (fraction correctly classified)

### 1.2 The Mathematical Setup

| Symbol | Meaning |
|--------|---------|
| $\mathbf{x} \in \mathcal{X}$ | Input (feature vector) |
| $y \in \mathcal{Y}$ | Output (target) |
| $\mathcal{D} = \{(\mathbf{x}_i, y_i)\}_{i=1}^n$ | Dataset ($n$ examples) |
| $f_\theta$ | Model parameterized by $\theta$ |
| $\mathcal{H} = \{f_\theta : \theta \in \Theta\}$ | Hypothesis space |
| $L(\hat{y}, y)$ | Loss function |
| $R_{\text{emp}}(\theta)$ | Empirical risk (average training loss) |
| $R(\theta)$ | True risk (expected loss over true distribution) |

### 1.3 Key Equations

**Empirical Risk:**
$$R_{\text{emp}}(\theta) = \frac{1}{n}\sum_{i=1}^n L(f_\theta(\mathbf{x}_i), y_i)$$

**ERM Principle:**
$$\theta^* = \arg\min_{\theta \in \Theta} R_{\text{emp}}(\theta)$$

**True Risk:**
$$R(\theta) = \mathbb{E}_{(\mathbf{x},y) \sim \mathcal{P}}[L(f_\theta(\mathbf{x}), y)]$$

**Why we can't minimize true risk:** We don't know $\mathcal{P}$ (the true data distribution). We only have a finite sample $\mathcal{D}$. The empirical risk is our best approximation.

### 1.4 Types of Learning

| Type | Data | Goal | Example |
|------|------|------|---------|
| Supervised | $(\mathbf{x}_i, y_i)$ | Learn $f: \mathcal{X} \to \mathcal{Y}$ | Spam filter, house prices |
| Unsupervised | $\mathbf{x}_i$ only | Find structure | Clustering, dimensionality reduction |
| Reinforcement | $(s_t, a_t, r_t)$ | Learn policy $\pi(a|s)$ | Game playing, robotics |

Supervised has two sub-types: **regression** ($\mathcal{Y} = \mathbb{R}$) and **classification** ($\mathcal{Y} = \{1, \ldots, K\}$).

### 1.5 Overfitting vs. Underfitting (Qualitative)

| | Underfitting | Good Fit | Overfitting |
|---|---|---|---|
| Training error | High | Moderate | Low (≈0) |
| Test error | High | Moderate | High |
| Complexity | Too low | Just right | Too high |
| Analogy | Didn't study | Understood concepts | Memorized answers |

**Key insight:** Zero training error does NOT mean a good model. The gap between training and test error (the **generalization gap**) is what matters.

### 1.6 The Triality

Every ML problem has three perspectives:
1. **Geometric:** Fitting a surface to data points
2. **Probabilistic:** Estimating a data distribution
3. **Optimization:** Minimizing an objective function

We see all three in linear regression (Week 2): projection (geometry), MLE under Gaussian noise (probability, Week 5 preview), convex minimization (optimization).

### 1.7 Common Loss Functions

| Loss | Formula | Use Case |
|------|---------|----------|
| Squared error | $(\hat{y}-y)^2$ | Regression |
| Absolute error | $|\hat{y}-y|$ | Regression (robust) |
| 0-1 loss | $\mathbb{1}[\hat{y} \neq y]$ | Classification |
| Cross-entropy | $-y\log\hat{y} - (1-y)\log(1-\hat{y})$ | Classification (probabilistic) |

### Mini-Exercise (2 min)

**Q:** For a Netflix recommendation system that predicts user ratings (1–5 stars), identify T, E, P, and the type of learning.

> **A:** T = predict ratings, E = historical rating data, P = MSE or accuracy, Type = supervised regression.

---

## Block 2: Week 2 — Scalar Linear Regression (25 min)

### 2.1 The Model and Loss

**Model:** $\hat{y} = wx + b$ (slope $w$, intercept $b$)

**MSE Loss:**
$$R_{\text{emp}}(w, b) = \frac{1}{n}\sum_{i=1}^n (wx_i + b - y_i)^2$$

**Why squared error?**
- Geometric: measures Euclidean distance (vertical) between predictions and targets
- Practical: differentiable everywhere, unique solution
- Probabilistic (preview): corresponds to Gaussian noise assumption (Week 5)

### 2.2 Deriving $b^*$ (Exam-Critical!)

**Step 1:** Fix $w$. Let $\epsilon_i = wx_i - y_i$.

$$R(b) = \frac{1}{n}\sum_i (\epsilon_i + b)^2 = \frac{1}{n}\sum_i \epsilon_i^2 + 2b\bar{\epsilon} + b^2$$

**Step 2:** This is a quadratic $b^2 + 2b\bar{\epsilon} + \overline{\epsilon^2}$, minimized at $b = -\bar{\epsilon}$.

$$\boxed{b^* = \bar{y} - w\bar{x}}$$

**Key geometric fact:** The best-fit line ALWAYS passes through the centroid $(\bar{x}, \bar{y})$, regardless of $w$.

### 2.3 Deriving $w^*$ (Exam-Critical!)

**Step 1:** Substitute $b^*$. Prediction becomes $\hat{y}_i = w(x_i - \bar{x}) + \bar{y} = w\tilde{x}_i + \bar{y}$.

**Step 2:** Error becomes $w\tilde{x}_i - \tilde{y}_i$ (centered variables).

**Step 3:**
$$R(w) = w^2 \text{Var}(x) - 2w\text{Cov}(x,y) + \text{Var}(y)$$

**Step 4:** Quadratic $Aw^2 - Bw + C$ with $A = \text{Var}(x)$, $B = 2\text{Cov}(x,y)$. Minimized at $w = B/(2A)$:

$$\boxed{w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)}}$$

### 2.4 OLS Properties (Exam-Critical!)

1. **Line passes through centroid:** $b^* = \bar{y} - w^*\bar{x}$ → $\hat{y}(\bar{x}) = \bar{y}$ ✓
2. **Residuals sum to zero:** $\sum_i e_i = 0$
3. **Residuals uncorrelated with $x$:** $\sum_i x_i e_i = 0$
4. **Residuals uncorrelated with predictions:** $\sum_i \hat{y}_i e_i = 0$ (follows from 2 & 3)
5. **Variance decomposition:** $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$ (follows from 4)

### 2.5 R² (Coefficient of Determination)

$$R^2 = 1 - \frac{\text{SS}_{\text{res}}}{\text{SS}_{\text{tot}}} = 1 - \frac{\sum_i(y_i - \hat{y}_i)^2}{\sum_i(y_i - \bar{y})^2}$$

| $R^2$ | Interpretation |
|-------|---------------|
| 1.0 | Perfect fit |
| 0.0 | No better than predicting $\bar{y}$ |
| < 0 | Worse than predicting $\bar{y}$ (overfit model on test data) |

Also: $R^2 = r^2$ (square of correlation coefficient).

### 2.6 Ridge Regression

**Objective:**
$$R_{\text{ridge}}(w, b) = \frac{1}{n}\sum_i (wx_i + b - y_i)^2 + \lambda w^2$$

**Solution:**
$$w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}, \qquad b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}}\bar{x}$$

**Shrinkage factor:** $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$

- $\lambda = 0$: ridge = OLS (no shrinkage)
- $\lambda \to \infty$: $w \to 0$ (predict $\bar{y}$, extreme underfitting)
- $\lambda$ moderate: sweet spot (balance fit and stability)

**Note:** The intercept $b$ is NOT regularized. Only the slope $w$ is penalized.

### 2.7 Correlation Connection

$$w^* = r \cdot \frac{\sigma_y}{\sigma_x}$$

where $r = \text{Cov}(x,y)/(\sigma_x \sigma_y)$ is the correlation coefficient. If $r = 0$ (no correlation), $w^* = 0$ and the model predicts $\bar{y}$.

### Worked Example: Ice Cream Sales

Data: $(15, 120), (20, 180), (25, 200), (30, 280), (35, 320)$

- $\bar{x} = 25$, $\bar{y} = 220$
- $\text{Var}(x) = 50$, $\text{Cov}(x,y) = 500$
- $w^* = 500/50 = 10$, $b^* = 220 - 250 = -30$
- Model: $\hat{y} = 10x - 30$
- $R^2 = 1 - 600/25600 = 0.977$
- Ridge with $\lambda = 25$: $w^*_{\text{ridge}} = 500/75 \approx 6.67$

### Mini-Exercise (3 min)

**Q:** Given data $(1,3), (2,5), (3,7), (4,9)$, compute $w^*$, $b^*$, and the model.

> **A:** $\bar{x}=2.5$, $\bar{y}=6$, $\text{Var}(x)=1.25$, $\text{Cov}(x,y)=2.5$. $w^* = 2.5/1.25 = 2$, $b^* = 6 - 2(2.5) = 1$. Model: $\hat{y} = 2x + 1$. (Perfect fit — data is exactly $y = 2x+1$.)

---

## Block 3: Week 3 — Overfitting & Regularization (20 min)

### 3.1 Polynomial Regression

$$\hat{y} = w_d x^d + \ldots + w_1 x + w_0$$

**Key insight:** Linear in **parameters** (the $w_j$), nonlinear in **features** ($x, x^2, \ldots, x^d$). The OLS machinery still applies.

### 3.2 The Degree-vs-Data Tradeoff

| Condition | What happens |
|-----------|-------------|
| $d+1 \ll n$ | Can't fit all patterns (underfitting risk) |
| $d+1 \approx n$ | Fits well (if pattern is polynomial) |
| $d+1 = n$ | Passes through every point (zero training error) |
| $d+1 > n$ | Infinitely many perfect fits (underdetermined) |

### 3.3 The Fundamental Observation (Exam-Critical!)

> **Training error is monotonically non-increasing with complexity.** A higher-degree polynomial can always represent everything a lower-degree one can (set extra coefficients to zero) plus more.

> **Test error is NOT monotonic.** It first decreases (capturing real pattern), then increases (fitting noise). This U-shape is the **most important figure in ML**.

### 3.4 Diagnostic Table (Exam-Critical!)

| Symptom | Diagnosis | Prescription |
|---------|-----------|-------------|
| Both high, small gap | Underfitting | Increase complexity |
| Low train, high test, large gap | Overfitting | Decrease complexity or add regularization |
| Both low, small gap | Good fit | Done! |

### 3.5 The Generalization Gap

$$\text{Generalization gap} = R_{\text{test}} - R_{\text{train}}$$

- Small gap + both high → underfitting
- Large gap + low train → overfitting
- Small gap + both low → good fit

### 3.6 Ridge Regression Revisited

Ridge prevents the wild oscillations of high-degree polynomials by keeping coefficients small.

| $\lambda$ | Effect | Risk |
|-----------|--------|------|
| 0 | OLS (no regularization) | May overfit |
| Small | Slight shrinkage | Good balance |
| Moderate | Sweet spot | Best generalization |
| $\to \infty$ | $w \to 0$ | Underfitting (predicts $\bar{y}$) |

### 3.7 Bias-Variance Intuition (Without Probability)

| | $\lambda=0$ (OLS) | $\lambda$ moderate | $\lambda \to \infty$ |
|---|---|---|---|
| Bias | Low | Moderate | High |
| Variance | High | Moderate | Low |
| Training error | Lowest | Slightly higher | Highest |
| Test error | Can be high | **Lowest** | High |

**Key intuition:** OLS has low bias (fits data hard) but high variance (fits noise, unstable). Ridge trades a small increase in bias for a large decrease in variance. At the sweet spot, total error is minimized.

### 3.8 L1 vs. L2 Geometry (Exam-Critical!)

| Property | Ridge (L2) | Lasso (L1) |
|----------|-----------|------------|
| Penalty | $\lambda \sum w_j^2$ | $\lambda \sum |w_j|$ |
| Constraint shape | Ball (circle/sphere) | Diamond (cross-polytope) |
| Solution | Closed-form | Iterative (no closed form) |
| Sparsity | No (weights small but nonzero) | **Yes** (some weights exactly 0) |
| Feature selection | No | **Yes** |

**Why lasso produces sparsity:** The L1 diamond has corners on the axes. The optimization solution often lands on a corner, where some $w_j = 0$. The L2 circle has no corners, so the solution is typically not on an axis — all weights remain nonzero.

**Why lasso has no closed form:** $|w|$ is not differentiable at $w = 0$ (left derivative $-1$, right derivative $+1$). Can't set gradient to zero. This nondifferentiability is EXACTLY why sparsity occurs.

### 3.9 Elastic Net

$$R_{\text{elastic}} = \text{MSE} + \lambda_1 \sum |w_j| + \lambda_2 \sum w_j^2$$

Combines L1 (sparsity) and L2 (stability with correlated features). Constraint shape is a "rounded diamond."

### 3.10 The Complexity Dial (Exam-Critical!)

Every ML model has a complexity knob — they're all the same knob:

| Model | Knob | Low complexity | High complexity |
|-------|------|---------------|----------------|
| Polynomial | Degree $d$ | $d=1$ (line) | $d=n-1$ (through all) |
| Ridge | $\lambda$ | $\lambda \to \infty$ | $\lambda = 0$ (OLS) |
| Lasso | $\lambda$ | $\lambda \to \infty$ | $\lambda = 0$ |
| k-NN | $k$ | $k=n$ (predict $\bar{y}$) | $k=1$ (memorize) |
| Decision trees | Depth | Depth 1 | Depth $\infty$ |

The U-shaped test error curve is **universal** — it applies to every model and every knob.

### 3.11 Residual Analysis

| Residual pattern | Diagnosis | Fix |
|-----------------|-----------|-----|
| Random scatter | Good fit | Done |
| Clear curve (U-shape) | Underfitting | Add polynomial features |
| Increasing spread | Heteroscedasticity | Weighted regression (advanced) |
| Outliers | Data errors or extremes | Investigate; Huber loss |

### Mini-Exercise (3 min)

**Q:** You fit three models and get: (A) train MSE = 15, test MSE = 16; (B) train MSE = 2, test MSE = 3; (C) train MSE = 0.01, test MSE = 28. Diagnose each.

> **A:** A = underfitting (both high, small gap). B = good fit (both low, small gap). C = overfitting (train ≈ 0, test high, large gap).

---

## Block 4: Week 4 — Model Evaluation & Validation (30 min)

### 4.1 The Train/Validation/Test Split

| Set | Purpose | How often |
|-----|---------|-----------|
| Training | Fit parameters ($w, b$) | Many times |
| Validation | Tune hyperparameters ($\lambda, d$) | Several times |
| Test | Final honest evaluation | **Exactly once** |

Typical split: 60/20/20 or 70/15/15.

### 4.2 The Golden Rule (Exam-Critical!)

> **Never touch the test data during model development.**

If you use the test set to pick models, it becomes a second validation set — your estimate is optimistically biased.

### 4.3 Why Three Sets?

- **Training:** Model has seen this data → training error is optimistic
- **Validation:** Used for model selection → validation error is somewhat biased (you chose the winner)
- **Test:** Never seen in any form → honest estimate

### 4.4 Data Leakage

| Leak type | Example | Fix |
|-----------|---------|-----|
| Normalizing before splitting | Mean/std on ALL data | Split first, normalize with train stats only |
| Duplicates | Same patient in train and test | Split by patient, not by record |
| Temporal leakage | Train on future, test on past | Train on past, test on future |
| Feature selection before splitting | Pick features on ALL data | Select features on train only |

> **Prevention:** Always split FIRST. Do ALL preprocessing using ONLY training data. Apply same transformations to validation/test.

### 4.5 k-Fold Cross-Validation

**Procedure:**
1. Split data into $k$ equal folds
2. For each fold $i$: train on $k-1$ folds, validate on fold $i$
3. Average the $k$ validation errors

**Fold sizes (example: $n=1000$, $k=5$):**
- Each validation fold: $1000/5 = 200$ examples
- Each training fold: $1000 - 200 = 800$ examples
- Total model fits: $5$ per candidate model

**Advantages:**
- Every point used for validation exactly once
- Less noisy than a single split
- Gives standard deviation (stability measure)

### 4.6 LOOCV (Leave-One-Out)

$k = n$: each fold is one data point. Train on $n-1$, test on 1.

| Property | LOOCV | 5-fold CV |
|----------|-------|-----------|
| Folds | $n$ | 5 |
| Training per fold | $n-1$ | $4n/5$ |
| Cost | $n$ fits | 5 fits |
| Bias | Low | Slightly higher |
| Variance | Higher (folds correlated) | Lower |
| Best for | Small $n$ ($<50$) | Most cases |

**Why LOOCV has higher variance:** Training sets are nearly identical (differ by 1 point), so validation errors are highly correlated. Averaging correlated values doesn't reduce variance much.

### 4.7 Model Selection Procedure

1. Choose candidate models (e.g., degrees 1–10)
2. For each, run $k$-fold CV, compute average validation error
3. Pick model with lowest average CV error
4. (Optional) Retrain on all data with chosen model
5. Evaluate ONCE on test set

### 4.8 Overfitting to the Validation Set

If you try 500 models and pick the best on validation, the winner is partly lucky. This is the **multiple comparisons problem**. The test set (used once) mitigates this.

### 4.9 Confusion Matrix (Exam-Critical!)

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | TP (True Positive) | FN (False Negative) |
| **Actual Negative** | FP (False Positive) | TN (True Negative) |

### 4.10 Classification Metrics (Exam-Critical!)

**Accuracy:**
$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}$$

**Precision:** (quality of positive predictions)
$$\text{Precision} = \frac{TP}{TP + FP}$$

**Recall:** (coverage of actual positives)
$$\text{Recall} = \frac{TP}{TP + FN}$$

**F1-Score:** (harmonic mean of precision and recall)
$$F_1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$$

**Why harmonic mean?** If precision = 0.01 and recall = 1.0, arithmetic mean = 0.505 (looks OK) but harmonic mean ≈ 0.02 (correctly terrible). Harmonic mean is high only when BOTH are high.

### 4.11 Why Accuracy Fails with Imbalance

**Example:** Disease affects 0.1% of population. Model that predicts "healthy" for everyone gets 99.9% accuracy but catches 0% of cases. Accuracy is useless here.

**Baseline comparison:** Always compare against the trivial baseline (predict majority class).

### 4.12 Worked Example: Spam Filter

| | Predicted Spam | Predicted Not Spam |
|---|---|---|
| **Actual Spam** | 80 | 20 |
| **Actual Not Spam** | 10 | 890 |

- Total = 1000
- Accuracy = (80 + 890)/1000 = 97%
- Precision = 80/(80+10) = 88.9%
- Recall = 80/(80+20) = 80%
- F1 = 2(0.889 × 0.80)/(0.889 + 0.80) = 84.2%

**Baseline (predict "not spam" for all):** Accuracy = 900/1000 = 90%, Recall = 0%, F1 = 0. The model's 97% accuracy vs. baseline's 90% seems like 7% improvement, but the model catches 80% of spam while baseline catches 0%.

### 4.13 Precision-Recall Tradeoff

| Threshold | Precision | Recall | Use case |
|-----------|-----------|--------|----------|
| High (0.9) | High | Low | Spam filter (don't flag good emails) |
| Low (0.1) | Low | High | Cancer screening (don't miss cases) |
| Balanced (0.5) | Moderate | Moderate | General purpose |

### 4.14 ROC Curve and AUC

**ROC:** Plot TPR vs. FPR as threshold sweeps from 1.0 to 0.0.

$$TPR = \text{Recall} = \frac{TP}{TP + FN}, \qquad FPR = \frac{FP}{FP + TN}$$

| Curve shape | Meaning |
|-------------|---------|
| Hugs top-left | Excellent classifier |
| Diagonal | Random guessing (AUC = 0.5) |
| Below diagonal | Worse than random (flip predictions!) |

**AUC interpretation (Exam-Critical!):**

> AUC = probability that the classifier ranks a random positive example higher than a random negative example.

| AUC | Interpretation |
|-----|---------------|
| 1.0 | Perfect |
| 0.9 | Excellent |
| 0.7 | Good |
| 0.5 | Random |
| < 0.5 | Worse than random |

### 4.15 PR Curve vs. ROC

| Situation | Use |
|-----------|-----|
| Balanced classes | ROC |
| Highly imbalanced | PR curve (ROC looks misleadingly good) |

### 4.16 Regression Metrics

| Metric | Formula | When to use |
|--------|---------|-------------|
| MSE | $\frac{1}{n}\sum(\hat{y}_i - y_i)^2$ | Large errors are especially bad |
| RMSE | $\sqrt{\text{MSE}}$ | Same units as $y$ (interpretable) |
| MAE | $\frac{1}{n}\sum|\hat{y}_i - y_i|$ | Outliers present (less sensitive) |
| R² | $1 - \text{SS}_{\text{res}}/\text{SS}_{\text{tot}}$ | Dimensionless comparison |

### 4.17 Learning Curves

Plot training error and validation error vs. **training set size** (not complexity).

| Pattern | Training | Validation | Gap | Diagnosis | Fix |
|---------|----------|------------|-----|-----------|-----|
| Both high, small gap | High | High | Small | Underfitting | More complex model |
| Low train, high val | Low | High | Large | Overfitting | More data or regularize |
| Both low, small gap | Low | Low | Small | Good fit | Done |

**Key insight:** If curves haven't converged (large gap), more data will help. If converged but both high, need more complexity — more data won't help.

### 4.18 Complexity Curve vs. Learning Curve

| | Complexity Curve (W3) | Learning Curve (W4) |
|---|---|---|
| X-axis | Model complexity (degree, 1/λ) | Training set size |
| Fixed | Data size | Model |
| Reveals | Sweet spot in complexity | Whether more data helps |

They are complementary: complexity curve tells you **what model to use**, learning curve tells you **whether to collect more data**.

### Mini-Exercise (3 min)

**Q:** A model has training MSE = 1.2 and validation MSE = 5.8. What is happening? Name three fixes.

> **A:** Overfitting (low train, high val, large gap). Fixes: (1) add regularization (increase $\lambda$), (2) reduce model complexity (lower degree), (3) collect more training data.

---

## Block 5: Exam Strategy & Common Mistakes (15 min)

### 5.1 Top 10 Common Mistakes

1. **Swapping precision and recall.** Precision = TP/(TP+FP) [column]. Recall = TP/(TP+FN) [row].
2. **Using arithmetic mean instead of harmonic mean for F1.** F1 = 2·P·R/(P+R), not (P+R)/2.
3. **Saying "test > train means overfitting."** Overfitting requires a LARGE gap, not just test slightly above train.
4. **Forgetting to center before computing variance/covariance.** Var(x) = (1/n)Σ(x_i - x̄)², NOT (1/n)Σx_i².
5. **Normalizing before splitting.** Always split FIRST, then normalize with train stats.
6. **Confusing validation and test sets.** Validation = tune hyperparameters (multiple uses). Test = final eval (once).
7. **Saying "choose λ with lowest training error."** Training error always decreases as λ→0. Use CV error.
8. **Forgetting why lasso has no closed form.** |w| is not differentiable at w=0. This IS why sparsity happens.
9. **Using MSE for imbalanced classification.** Use precision, recall, F1, or AUC instead.
10. **Saying "more data always fixes overfitting."** More data helps if the gap is large. If converged but both high, you need more complexity.

### 5.2 Derivation Checklist

You must be able to derive on the exam:
- [ ] $b^* = \bar{y} - w\bar{x}$ (complete the square in $b$)
- [ ] $w^* = \text{Cov}(x,y)/\text{Var}(x)$ (substitute $b^*$, complete the square in $w$)
- [ ] Ridge shrinkage factor: $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \text{Var}(x)/(\text{Var}(x) + \lambda)$
- [ ] Training error is monotonically non-increasing in degree (nested hypothesis space argument)
- [ ] $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$ (using Cov($\hat{y}$, e) = 0)

### 5.3 Memorization Checklist

- [ ] The diagnostic table (underfitting/overfitting/good fit from train/test errors)
- [ ] The bias-variance table (for λ = 0, moderate, ∞)
- [ ] The complexity dial table (degree, λ, k, depth)
- [ ] Formulas: accuracy, precision, recall, F1, TPR, FPR
- [ ] AUC = P(score(+) > score(−))
- [ ] L1 = diamond (sparse), L2 = circle (not sparse)
- [ ] Golden Rule: never touch test data during development
- [ ] k-fold: each point used for validation once, training k−1 times

### 5.4 Exam Time Management

- **Long questions (20 min each):** Spend 3-4 min per part. If stuck on a derivation, write what you know and move on — partial credit matters.
- **Short questions (6 min each):** Spend 1-2 min per sub-part. These are faster — don't overthink.
- **Leave 5 min at the end** to review your work.

### 5.5 Practice Questions

**Practice 1:** Given data $(1, 2), (3, 5), (5, 8), (7, 11)$, compute $w^*$, $b^*$, and the model. Then compute MSE and $R^2$.

> $\bar{x}=4, \bar{y}=6.5, \text{Var}(x)=5, \text{Cov}(x,y)=7.5$. $w^*=1.5, b^*=0.5$. Model: $\hat{y}=1.5x+0.5$. Predictions: 2, 5, 8, 11. MSE=0, $R^2=1$ (perfect fit).

**Practice 2:** A classifier has TP=45, FP=15, FN=5, TN=35. Compute all metrics. Is this better for cancer screening or spam filtering?

> Accuracy = 80/100 = 80%. Precision = 45/60 = 75%. Recall = 45/50 = 90%. F1 = 2(0.75×0.90)/(0.75+0.90) = 81.8%. High recall → good for cancer screening.

**Practice 3:** You have 200 examples and use 10-fold CV. How many in each train/val fold? How many total fits?

> Each fold: 20 validation, 180 training. 10 total fits per candidate model.

**Practice 4:** Explain why training error is monotonically non-increasing with polynomial degree, but test error is not.

> Nested hypothesis spaces: $\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$, so the optimizer can always do at least as well. But higher degree can fit noise, which hurts generalization.

**Practice 5:** Sketch the L1 and L2 constraint regions in 2D. Explain why lasso produces sparsity.

> L2 = circle (no corners, solution not on axis). L1 = diamond (corners on axes, solution lands on corner → some $w_j = 0$).

---

## Summary: The Complete Picture

```
Week 1: Framework
  ├── Learning = improving performance with experience
  ├── ERM: minimize average training loss
  ├── True risk vs. empirical risk → generalization gap
  └── Overfitting (too complex) vs. underfitting (too simple)

Week 2: Linear Regression  
  ├── OLS: w* = Cov/Var, b* = ȳ - w*x̄
  ├── Line through centroid, residuals sum to zero
  ├── R² = fraction of variance explained
  └── Ridge: shrink slope toward zero with λ

Week 3: Overfitting Deep
  ├── Polynomial regression (linear in params, nonlinear in features)
  ├── Training error ↓ with complexity, test error is U-shaped
  ├── L1 (lasso) = diamond → sparsity; L2 (ridge) = circle → shrinkage
  ├── Complexity dial: degree, λ, k, depth — all the same knob
  └── Bias-variance: regularization ↑ bias, ↓ variance

Week 4: Evaluation
  ├── Train/val/test: fit params / tune hyperparams / final eval (once)
  ├── k-fold CV: average over k folds, less noisy than single split
  ├── Confusion matrix → accuracy, precision, recall, F1
  ├── ROC/AUC: ranking ability = P(score(+) > score(−))
  ├── Learning curves: error vs. data size (complement to complexity curve)
  └── Golden Rule: never touch test data during development
```

**The one sentence that connects everything:**

> *We minimize training loss (ERM), but we care about test loss (generalization); the gap between them depends on model complexity (the complexity dial), which we control with regularization (ridge/lasso) and measure properly with cross-validation and the right metrics.*

---

## Post-Session Checklist for Instructor

- [ ] Distribute the exam review sheet (this document)
- [ ] Remind students of exam time and location
- [ ] Review quiz results from Weeks 1–4 — identify common weak spots
- [ ] Prepare targeted office hours for students struggling with derivations
- [ ] Ensure all students can compute confusion matrix metrics from scratch
- [ ] Verify students understand the L1/L2 geometry (draw it!)
- [ ] Check that students know the Golden Rule and data leakage examples

---

*Good luck on the exam. Remember: every ML problem is hypothesis space + loss function + optimizer. Choose all three carefully. Minimize training loss, but care about test loss. The gap is generalization.*
