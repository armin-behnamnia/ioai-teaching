# Midterm Exam: Weeks 1–4

> **Course:** Machine Learning for IOAI Preparation  
> **Exam Duration:** 90 minutes  
> **Coverage:** Week 1 (ML Framework), Week 2 (Scalar Linear Regression), Week 3 (Overfitting & Regularization), Week 4 (Model Evaluation & Validation)  
> **Format:** 3 long-answer multi-part questions + 5 short-answer questions  
> **Closed notes. Calculators permitted.**

---

## Topic Coverage Map

| Question | Weeks Covered | Key Concepts |
|----------|---------------|--------------|
| Long Q1 | W1, W2, W3 | ERM, OLS derivation, ridge regression, bias-variance, complexity dial |
| Long Q2 | W2, W3, W4 | Polynomial regression, generalization gap, CV, model selection, metrics |
| Long Q3 | W1, W3, W4 | Loss functions, L1/L2 geometry, confusion matrix, ROC/AUC, precision/recall |
| Short Q1 | W1 | Hypothesis space, ERM, nested hypothesis spaces |
| Short Q2 | W2 | OLS properties, residuals, R² |
| Short Q3 | W3 | Lasso vs. ridge geometry, sparsity |
| Short Q4 | W4 | k-fold CV, data leakage, LOOCV |
| Short Q5 | W3, W4 | Learning curves, diagnosis, regularization connection |

---

## Part A: Long-Answer Questions (60 minutes)

### Question 1 [20 marks] — From Framework to Regularized Regression

Consider a dataset $\mathcal{D} = \{(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n)\}$ with a single input feature $x$ and continuous target $y$. We use the linear model $\hat{y} = wx + b$ with the squared error loss $L(\hat{y}, y) = (\hat{y} - y)^2$.

**(a)** [3 marks] Write the formula for the empirical risk $R_{\text{emp}}(w, b)$ and the true risk $R(w, b)$. State the Empirical Risk Minimization (ERM) principle in one sentence. Explain why we cannot directly minimize the true risk.

**(b)** [5 marks] Derive the optimal intercept $b^*$ by treating $w$ as fixed and completing the square in $b$. Show that $b^* = \bar{y} - w\bar{x}$ and explain in one sentence why this means the best-fit line always passes through the centroid $(\bar{x}, \bar{y})$.

**(c)** [4 marks] After substituting $b^*$, the loss reduces to a quadratic in $w$: $R(w) = \text{Var}(x) \cdot w^2 - 2\text{Cov}(x, y) \cdot w + \text{Var}(y)$. Using this, derive the OLS slope $w^* = \text{Cov}(x, y)/\text{Var}(x)$.

Now consider ridge regression with the objective:
$$R_{\text{ridge}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2 + \lambda w^2$$

**(d)** [4 marks] The ridge solution is $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$. Express $w^*_{\text{ridge}}$ in terms of $w^*_{\text{OLS}}$ and identify the shrinkage factor. What happens to the shrinkage factor as $\lambda \to 0$ and as $\lambda \to \infty$?

**(e)** [4 marks] Fill in the following table using "low," "moderate," or "high" for each cell:

| | $\lambda = 0$ (OLS) | $\lambda$ moderate | $\lambda \to \infty$ |
|---|---|---|---|
| **Bias** | ? | ? | ? |
| **Variance** | ? | ? | ? |
| **Training error** | ? | ? | ? |
| **Test error** | ? | ? | ? |

Explain in 2–3 sentences: why does ridge regression, despite being biased, sometimes achieve lower test error than OLS?

---

### Question 2 [20 marks] — Overfitting, Model Selection, and Evaluation

You are given 20 data points generated from a true relationship $y = 0.5x^2 + \epsilon$ where $\epsilon$ is random noise. You fit polynomial regression models of varying degree $d$ and record the training and test MSE:

| Degree $d$ | Training MSE | Test MSE |
|------------|-------------|----------|
| 1 | 12.5 | 13.1 |
| 2 | 1.8 | 2.3 |
| 3 | 1.5 | 2.1 |
| 5 | 0.6 | 4.7 |
| 8 | 0.02 | 18.5 |
| 15 | 0.001 | 32.0 |

**(a)** [3 marks] For each of degrees 1, 2, and 15, state whether the model is underfitting, overfitting, or a good fit. Justify each answer using both the error values and the generalization gap.

**(b)** [3 marks] Prove that training error is a monotonically non-increasing function of polynomial degree $d$. That is, if $d_1 < d_2$, then $R_{\text{train}}(d_2) \leq R_{\text{train}}(d_1)$. *(Hint: Think about the hypothesis spaces $\mathcal{H}_{d_1}$ and $\mathcal{H}_{d_2}$.)*

**(c)** [4 marks] You decide to use 5-fold cross-validation to select the best polynomial degree. You have 20 data points. How many data points are in each training fold? How many in each validation fold? How many total model fits will you perform? Describe the 5-step model selection procedure.

**(d)** [4 marks] Suppose that instead of cross-validation, you try 500 different polynomial degrees and pick the one with the lowest validation error on a single validation set. Explain the risk of "overfitting to the validation set." Why does the test set (used once, at the end) mitigate this?

**(e)** [3 marks] Suppose your data has a temporal component (e.g., the $x$ values are dates). You shuffle the data before splitting into train/test. What type of data leakage occurs, and why is it problematic? How should you split time-series data instead?

**(f)** [3 marks] After selecting degree $d=2$, you evaluate on the test set and get $R^2 = 0.91$. Explain what $R^2 = 0.91$ means in terms of variance explained. If instead you got $R^2 = -0.05$, what would that indicate?

---

### Question 3 [20 marks] — Loss Functions, Regularization Geometry, and Classification Metrics

**(a)** [4 marks] Consider two loss functions for regression: squared error $L_2(\hat{y}, y) = (\hat{y}-y)^2$ and absolute error $L_1(\hat{y}, y) = |\hat{y}-y|$. 

(i) Which is more sensitive to outliers? Justify with a concrete numerical example.  
(ii) The Huber loss transitions from $L_2$ for small errors to $L_1$ for large errors. Explain in 2–3 sentences why this is a good compromise.

**(b)** [5 marks] Consider L1 (lasso) and L2 (ridge) regularization in a two-parameter setting ($w_1, w_2$).

(i) Write the penalty term for each.  
(ii) Sketch (or describe precisely) the constraint region for each in the $(w_1, w_2)$ plane.  
(iii) Explain why lasso tends to produce sparse solutions (some $w_j = 0$ exactly) while ridge does not. Refer to the geometry in your explanation.  
(iv) State one scenario where lasso is preferred over ridge, and one where ridge is preferred over lasso.

**(c)** [5 marks] A spam filter is evaluated on 2000 emails (200 spam, 1800 not spam). The confusion matrix is:

| | Predicted Spam | Predicted Not Spam |
|---|---|---|
| **Actual Spam** | 160 | 40 |
| **Actual Not Spam** | 30 | 1770 |

(i) Compute accuracy, precision, recall, and F1.  
(ii) A baseline model that predicts "not spam" for everything achieves what accuracy? Explain why this demonstrates that accuracy alone is misleading.  
(iii) If this were a cancer screening model instead of a spam filter, would you prioritize precision or recall? Explain why.

**(d)** [4 marks] A classifier outputs probabilities. You sweep the classification threshold from 1.0 down to 0.0 and plot the ROC curve.

(i) What are the x-axis and y-axis of the ROC curve? Give their formulas.  
(ii) State the probabilistic interpretation of AUC (in one sentence).  
(iii) An AUC of 0.3 is obtained. Is this worse or better than random guessing? What should you do?

**(e)** [2 marks] Fill in the blank: The F1-score is the \_\_\_\_\_\_\_\_\_ mean of precision and recall. Explain in one sentence why this type of mean is chosen over the arithmetic mean.

---

## Part B: Short-Answer Questions (30 minutes)

**S1.** [6 marks] Let $\mathcal{H}_1$ be the set of all constant functions $f(x) = b$ and $\mathcal{H}_2$ be the set of all linear functions $f(x) = wx + b$. Note that $\mathcal{H}_1 \subset \mathcal{H}_2$. Let $\theta_1^*$ and $\theta_2^*$ be the empirical risk minimizers in each space. 

(a) Prove that $R_{\text{emp}}(\theta_2^*) \leq R_{\text{emp}}(\theta_1^*)$.  
(b) Does this imply that $\theta_2^*$ will generalize better (have lower true risk)? Explain why or why not.

---

**S2.** [6 marks] For the OLS solution, two key properties of the residuals $e_i = y_i - \hat{y}_i$ are:

1. $\sum_{i=1}^n e_i = 0$ (residuals sum to zero)  
2. $\sum_{i=1}^n x_i \cdot e_i = 0$ (residuals are uncorrelated with $x$)

(a) Briefly explain why each property holds.  
(b) Using property 2, explain why $\text{Cov}(\hat{y}, e) = 0$ (the predictions are uncorrelated with the residuals).  
(c) Using (b), prove the variance decomposition: $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$.

---

**S3.** [6 marks] Answer each in 2–3 sentences:

(a) Why does lasso have no closed-form solution while ridge does? Refer to differentiability.  
(b) What is elastic net, and what problem with pure lasso does it address?  
(c) The intercept $b$ is typically not regularized in ridge or lasso. Give one reason why.

---

**S4.** [6 marks] You have 50 data points and need to choose between 5-fold cross-validation and leave-one-out cross-validation (LOOCV).

(a) How many model fits does each method require?  
(b) LOOCV has lower bias but higher variance than 5-fold CV. Explain why the variance is higher.  
(c) State the Golden Rule of model evaluation. Give one example of data leakage and how to prevent it.  
(d) You normalize your data by computing the mean and standard deviation on ALL data, then split into train/test. Is this a problem? If so, how do you fix it?

---

**S5.** [6 marks] Consider the following learning curve (training error and validation error vs. training set size):

```
  Error
    │
    │  Validation
    │  ╲
    │   ╲
    │    ╲───────
    │     ╱  ← gap is small and shrinking
    │    ╱
    │   ╱ Training
    │  ╱
    │╱
    └────────────────── Training set size
```

(a) What is the diagnosis: underfitting, overfitting, or good fit? Justify your answer.  
(b) Would adding more training data significantly help here? Why or why not?  
(c) Would increasing or decreasing regularization ($\lambda$) help? Explain.  
(d) Contrast this with the complexity curve from Week 3: what does each curve vary (data size vs. model complexity), and how are they complementary?

---
---

## Solutions

### Question 1 Solutions

**(a)** [3 marks]

Empirical risk:
$$R_{\text{emp}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2$$

True risk:
$$R(w, b) = \mathbb{E}_{(x,y) \sim \mathcal{P}}\left[(wx + b - y)^2\right]$$

**ERM principle:** Find the parameters that minimize the average loss on the training data: $\theta^* = \arg\min_{\theta} R_{\text{emp}}(\theta)$.

**Why we cannot minimize the true risk:** The true risk depends on the unknown joint distribution $\mathcal{P}$ over $(x, y)$. We only have a finite sample $\mathcal{D}$, so we cannot compute the expectation. We approximate it with the empirical risk.

**Grading:** 1 mark for each formula, 1 mark for ERM + why true risk is uncomputable.

---

**(b)** [5 marks]

Fix $w$. The loss as a function of $b$:
$$R(b) = \frac{1}{n}\sum_{i=1}^n (wx_i + b - y_i)^2$$

Let $\epsilon_i = wx_i - y_i$. Then:
$$R(b) = \frac{1}{n}\sum_i (\epsilon_i + b)^2 = \frac{1}{n}\sum_i \epsilon_i^2 + 2b \cdot \frac{1}{n}\sum_i \epsilon_i + b^2$$

This is a quadratic in $b$: $R(b) = b^2 + 2b\bar{\epsilon} + \overline{\epsilon^2}$, where $\bar{\epsilon} = \frac{1}{n}\sum_i \epsilon_i$.

A quadratic $f(b) = b^2 + cb + d$ is minimized at $b = -c/2$, so:
$$b^* = -\bar{\epsilon} = -\frac{1}{n}\sum_i (wx_i - y_i) = \frac{1}{n}\sum_i y_i - w \cdot \frac{1}{n}\sum_i x_i = \bar{y} - w\bar{x}$$

**Centroid explanation:** Since $b^* = \bar{y} - w\bar{x}$, we have $\hat{y}(\bar{x}) = w\bar{x} + b^* = w\bar{x} + \bar{y} - w\bar{x} = \bar{y}$. The prediction at $x = \bar{x}$ is $\bar{y}$, so the line passes through $(\bar{x}, \bar{y})$ regardless of $w$.

**Grading:** 2 marks for expansion and identifying the quadratic, 2 marks for solving $b^*$, 1 mark for centroid explanation.

---

**(c)** [4 marks]

Substituting $b^* = \bar{y} - w\bar{x}$, the prediction becomes $\hat{y}_i = w(x_i - \bar{x}) + \bar{y} = w\tilde{x}_i + \bar{y}$ where $\tilde{x}_i = x_i - \bar{x}$.

The error: $\hat{y}_i - y_i = w\tilde{x}_i - \tilde{y}_i$ where $\tilde{y}_i = y_i - \bar{y}$.

The loss:
$$R(w) = \frac{1}{n}\sum_i (w\tilde{x}_i - \tilde{y}_i)^2 = w^2 \underbrace{\frac{1}{n}\sum_i \tilde{x}_i^2}_{\text{Var}(x)} - 2w \underbrace{\frac{1}{n}\sum_i \tilde{x}_i\tilde{y}_i}_{\text{Cov}(x,y)} + \underbrace{\frac{1}{n}\sum_i \tilde{y}_i^2}_{\text{Var}(y)}$$

This is $R(w) = \text{Var}(x) \cdot w^2 - 2\text{Cov}(x,y) \cdot w + \text{Var}(y)$, a quadratic $Aw^2 - Bw + C$ with $A = \text{Var}(x)$, $B = 2\text{Cov}(x,y)$.

Minimized at $w = B/(2A)$:
$$w^* = \frac{2\text{Cov}(x,y)}{2\text{Var}(x)} = \frac{\text{Cov}(x,y)}{\text{Var}(x)}$$

**Grading:** 2 marks for substitution/centering, 2 marks for identifying the quadratic and solving.

---

**(d)** [4 marks]

$$w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda} = \frac{\text{Cov}(x,y)}{\text{Var}(x)} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$$

**Shrinkage factor:** $s = \frac{\text{Var}(x)}{\text{Var}(x) + \lambda} \in (0, 1)$ for $\lambda > 0$.

- As $\lambda \to 0$: $s \to 1$, so $w^*_{\text{ridge}} \to w^*_{\text{OLS}}$ (no shrinkage).
- As $\lambda \to \infty$: $s \to 0$, so $w^*_{\text{ridge}} \to 0$ (model predicts $\bar{y}$ for everything).

**Grading:** 2 marks for the expression, 1 mark for identifying the shrinkage factor, 1 mark for both limits.

---

**(e)** [4 marks]

| | $\lambda = 0$ (OLS) | $\lambda$ moderate | $\lambda \to \infty$ |
|---|---|---|---|
| **Bias** | Low | Moderate | High |
| **Variance** | High | Moderate | Low |
| **Training error** | Lowest | Slightly higher | Highest ($\approx \text{Var}(y)$) |
| **Test error** | Can be high | Lowest | High |

**Explanation:** OLS has low bias (it fits the data aggressively) but high variance (it fits noise, so estimates swing wildly with different training data). Ridge introduces a small bias (shrinkage toward zero) but dramatically reduces variance (more stable estimates). At the sweet spot, the reduction in variance outweighs the increase in bias, leading to lower total test error. This is the bias-variance tradeoff.

**Grading:** 2 marks for correct table, 2 marks for explanation mentioning bias-variance tradeoff.

---

### Question 2 Solutions

**(a)** [3 marks]

- **Degree 1:** Both errors are high (~12–13) with a small gap (0.6). This is **underfitting** — the model is too simple (a line cannot capture a quadratic relationship).
- **Degree 2:** Both errors are low (~1.8–2.3) with a small gap (0.5). This is a **good fit** — the model captures the true quadratic pattern without fitting noise.
- **Degree 15:** Training error $\approx 0$ but test error is very high (32.0), with an enormous gap (32.0). This is **overfitting** — the model memorizes the training data including noise, and generalizes terribly.

**Grading:** 1 mark per diagnosis with correct justification.

---

**(b)** [3 marks]

A degree-$d_1$ polynomial is a special case of a degree-$d_2$ polynomial (for $d_1 < d_2$): simply set the extra coefficients $w_{d_1+1} = w_{d_1+2} = \ldots = w_{d_2} = 0$. Therefore the hypothesis space $\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$.

When we minimize the empirical risk over $\mathcal{H}_{d_2}$, the optimizer can always choose the degree-$d_1$ solution (by setting extra coefficients to zero). So:
$$\min_{f \in \mathcal{H}_{d_2}} R_{\text{emp}}(f) \leq \min_{f \in \mathcal{H}_{d_1}} R_{\text{emp}}(f)$$

Therefore training error is monotonically non-increasing in degree.

**Grading:** 1 mark for nested hypothesis space argument, 1 mark for the set inclusion, 1 mark for the inequality conclusion.

---

**(c)** [4 marks]

- Each fold: $20/5 = 4$ data points in validation, $20 - 4 = 16$ in training.
- Total model fits: $5$ (one per fold) $\times$ (number of candidate degrees being compared). If comparing 6 degrees, that's $5 \times 6 = 30$ fits. (Either "5 per degree" or "5 × number of candidates" is acceptable.)

**5-step procedure:**
1. Choose candidate degrees (e.g., $d = 1, 2, 3, 5, 8, 15$).
2. For each degree $d$, run 5-fold CV: split training data into 5 folds, train on 4 folds, validate on 1, repeat 5 times, average the validation errors.
3. Select the degree with the lowest average CV error.
4. (Optional) Retrain on all training data with the chosen degree.
5. Evaluate ONCE on the test set.

**Grading:** 1 mark for fold sizes, 1 mark for total fits, 2 marks for the 5-step procedure.

---

**(d)** [4 marks]

**Overfitting to the validation set:** When you try many models (500) and pick the best on the validation set, the winner is partly benefiting from luck — some model will look good on the validation set by chance, simply because you tried so many. This is the multiple comparisons problem. The validation error of the winner is optimistically biased: it underestimates the true test error.

**Why the test set helps:** The test set is used exactly once, after all model selection is done. Since no model was chosen based on the test set, there is no selection bias. The test set provides an honest, unbiased estimate of generalization performance.

**Grading:** 2 marks for explaining overfitting to validation set (multiple comparisons / lucky winner), 2 marks for why test set mitigates.

---

**(e)** [3 marks]

**Temporal leakage:** Shuffling time-series data breaks the temporal order, so the training set may contain data from the future relative to the test set. In deployment, you cannot see future data, so this is unrealistic and leads to over-optimistic estimates.

**Correct approach:** Train on the past, test on the future. For cross-validation, use time-series CV (rolling origin): train on $[1..t]$, validate on $[t+1..t+k]$, then expand the training window forward.

**Grading:** 1 mark for identifying temporal leakage, 1 mark for why it's problematic, 1 mark for correct approach.

---

**(f)** [3 marks]

$R^2 = 0.91$ means the model explains 91% of the variance in $y$. Specifically, $R^2 = 1 - \text{SS}_{\text{res}}/\text{SS}_{\text{tot}}$, so the residual (unexplained) sum of squares is only 9% of the total sum of squares.

$R^2 = -0.05$ means the model performs **worse** than simply predicting $\bar{y}$ for every input. The model's predictions are so bad that the residual sum of squares exceeds the total sum of squares. This can happen when the model overfit the training data and generalizes poorly to the test set.

**Grading:** 1 mark for "91% of variance explained," 1 mark for the formula interpretation, 1 mark for "worse than predicting the mean."

---

### Question 3 Solutions

**(a)** [4 marks]

**(i)** Squared error ($L_2$) is more sensitive to outliers.

Example: Suppose errors are $\{1, 1, 1, 1, 10\}$.
- MSE contribution of the outlier: $10^2 = 100$. Total MSE $= (1+1+1+1+100)/5 = 20.8$. The outlier dominates (100 out of 104 total).
- MAE contribution of the outlier: $10$. Total MAE $= (1+1+1+1+10)/5 = 2.8$. The outlier is proportional, not dominant.

Squaring amplifies large errors, making MSE sensitive to outliers.

**(ii)** Huber uses squared error for small errors (smooth, differentiable, easy to optimize — like $L_2$) and absolute error for large errors (robust to outliers — like $L_1$). This means typical predictions get the nice optimization properties of $L_2$, while outliers don't dominate the loss as they would under pure $L_2$.

**Grading:** 1 mark for correct identification with example, 1 mark for the numerical demonstration, 2 marks for Huber explanation.

---

**(b)** [5 marks]

**(i)** 
- Ridge (L2): $\lambda(w_1^2 + w_2^2)$
- Lasso (L1): $\lambda(|w_1| + |w_2|)$

**(ii)** 
- L2 constraint $\|\mathbf{w}\|^2 \leq t$: a **circle** (ball) centered at the origin.
- L1 constraint $\|\mathbf{w}\|_1 \leq t$: a **diamond** (cross-polytope) with corners on the axes at $(\pm t, 0)$ and $(0, \pm t)$.

**(iii)** The OLS solution is somewhere in the interior. Regularization pulls it back to the nearest point on the constraint region. For the L2 circle, the nearest point is typically **not** on an axis, so both $w_1$ and $w_2$ are nonzero (but small). For the L1 diamond, the nearest point is often a **corner** — and corners lie on the axes, where one $w_j = 0$. This is why lasso produces sparsity (exact zeros) and ridge does not.

**(iv)** 
- Lasso preferred: when you have many features but believe only a few are relevant (feature selection). Lasso zeros out irrelevant features.
- Ridge preferred: when all features are relevant (many small effects) or when features are correlated. Ridge keeps all features with small weights and handles correlated features more stably.

**Grading:** 1 mark for penalties, 1 mark for shapes, 2 marks for sparsity geometry, 1 mark for scenarios.

---

**(c)** [5 marks]

$TP = 160$, $FP = 30$, $FN = 40$, $TN = 1770$. Total $= 2000$.

**(i)**
- **Accuracy** $= (160 + 1770)/2000 = 1930/2000 = 96.5\%$
- **Precision** $= 160/(160+30) = 160/190 = 84.2\%$
- **Recall** $= 160/(160+40) = 160/200 = 80.0\%$
- **F1** $= 2 \cdot (0.842 \cdot 0.80)/(0.842 + 0.80) = 2 \cdot 0.6736/1.642 = 1.347/1.642 = 82.0\%$

**(ii)** Baseline (predict "not spam" for everything): $TP = 0$, $FP = 0$, $FN = 200$, $TN = 1800$. Accuracy $= 1800/2000 = 90\%$. The baseline achieves 90% accuracy by doing nothing. The model's 96.5% looks good, but the baseline already gets 90%. The real improvement is in recall (80% vs 0%) and F1 (82% vs 0%). Accuracy is dominated by the majority class (not spam) and hides the model's ability to detect spam.

**(iii)** For cancer screening, **recall** is prioritized. Missing a cancer case (false negative) is potentially fatal, while a false alarm (false positive) leads to extra tests and anxiety but is not life-threatening. We want to catch as many true positive cases as possible, even at the cost of more false positives.

**Grading:** 2 marks for correct computations, 1 mark for baseline accuracy + explanation, 1 mark for recall with justification, 1 mark for F1.

---

**(d)** [4 marks]

**(i)** 
- x-axis: FPR $= \frac{FP}{FP + TN}$
- y-axis: TPR $= \frac{TP}{TP + FN}$ (same as Recall)

**(ii)** AUC = the probability that the classifier ranks a randomly chosen positive example higher than a randomly chosen negative example.

**(iii)** AUC $= 0.3$ is **worse** than random guessing (AUC $= 0.5$). The model systematically ranks negatives above positives. You should **flip the predictions** (invert the model's output), which would give AUC $= 0.7$.

**Grading:** 1 mark for axes, 1 mark for AUC interpretation, 1 mark for worse than random, 1 mark for flipping.

---

**(e)** [2 marks]

**Harmonic** mean.

The harmonic mean punishes extreme imbalances: if precision $= 0.01$ and recall $= 1.0$ (predict everything positive), the arithmetic mean is $0.505$ (looks OK) but the harmonic mean (F1) is $\approx 0.02$ (correctly terrible). The harmonic mean is high only when BOTH precision and recall are high.

**Grading:** 1 mark for "harmonic," 1 mark for explanation with imbalanced example.

---

### Short-Answer Solutions

#### S1 Solution [6 marks]

**(a)** [3 marks]

Since $\mathcal{H}_1 \subset \mathcal{H}_2$, every function in $\mathcal{H}_1$ is also in $\mathcal{H}_2$. When we minimize $R_{\text{emp}}$ over $\mathcal{H}_2$, the optimizer searches a **superset** of $\mathcal{H}_1$. The minimum over a larger set is at most the minimum over a smaller set:
$$R_{\text{emp}}(\theta_2^*) = \min_{f \in \mathcal{H}_2} R_{\text{emp}}(f) \leq \min_{f \in \mathcal{H}_1} R_{\text{emp}}(f) = R_{\text{emp}}(\theta_1^*)$$

The optimizer can always achieve at least as low a loss because it can choose the $\mathcal{H}_1$ solution if nothing better exists in $\mathcal{H}_2 \setminus \mathcal{H}_1$.

**(b)** [3 marks]

No, this does **not** imply better generalization. Lower empirical risk does not guarantee lower true risk. The more complex model $\theta_2^*$ may have fit noise in the training data (overfitting), leading to a large generalization gap. The true risk $R(\theta_2^*)$ could be higher than $R(\theta_1^*)$ if the additional flexibility of $\mathcal{H}_2$ is used to memorize noise rather than learn signal. This is precisely the overfitting-underfitting tradeoff.

**Grading:** (a) 1 mark for set inclusion, 1 mark for superset argument, 1 mark for inequality. (b) 1 mark for "no," 1 mark for overfitting explanation, 1 mark for generalization gap.

---

#### S2 Solution [6 marks]

**(a)** [2 marks]

1. $\sum_i e_i = 0$: This follows from the intercept formula $b^* = \bar{y} - w^*\bar{x}$. The intercept positions the line so that positive and negative errors exactly balance.
2. $\sum_i x_i e_i = 0$: The OLS solution captures ALL the linear relationship between $x$ and $y$. The residuals have no remaining linear pattern in $x$. (Formally, this is the optimality condition for $w^*$.)

**(b)** [2 marks]

Since $\hat{y}_i = w^*x_i + b^*$ is a linear function of $x_i$, and $\sum_i x_i e_i = 0$, we can write:
$$\sum_i \hat{y}_i e_i = \sum_i (w^* x_i + b^*) e_i = w^* \sum_i x_i e_i + b^* \sum_i e_i = w^* \cdot 0 + b^* \cdot 0 = 0$$

Therefore $\text{Cov}(\hat{y}, e) = \frac{1}{n}\sum_i \hat{y}_i e_i - \bar{\hat{y}}\bar{e} = 0 - 0 = 0$ (using both properties from part (a)).

**(c)** [2 marks]

Since $y_i = \hat{y}_i + e_i$, we have:
$$\text{Var}(y) = \text{Var}(\hat{y} + e) = \text{Var}(\hat{y}) + \text{Var}(e) + 2\text{Cov}(\hat{y}, e)$$

From part (b), $\text{Cov}(\hat{y}, e) = 0$, so:
$$\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$$

This says: total variance = explained variance + unexplained variance.

**Grading:** (a) 1 mark per property. (b) 1 mark for linearity argument, 1 mark for using both properties. (c) 1 mark for variance decomposition formula, 1 mark for using Cov = 0.

---

#### S3 Solution [6 marks]

**(a)** [2 marks] The L1 penalty $|w|$ is not differentiable at $w = 0$ (the left derivative is $-1$, the right derivative is $+1$). Setting the gradient to zero doesn't work at nondifferentiable points, so there is no closed-form solution. Ridge's $w^2$ penalty is smooth and differentiable everywhere, so we can solve by setting the derivative to zero.

**(b)** [2 marks] Elastic net combines L1 and L2: $\lambda_1\sum|w_j| + \lambda_2\sum w_j^2$. It addresses lasso's problem with correlated features: lasso tends to pick one of two correlated features arbitrarily and zero the other. Elastic net's L2 component stabilizes the solution, keeping both features (small but nonzero).

**(c)** [2 marks] The intercept $b$ represents a baseline shift, not the model's sensitivity to $x$. Overfitting is caused by large slopes (weights), not by the intercept. Regularizing $b$ would unnecessarily force the model toward predicting $\bar{y}$, which is too aggressive. The intercept just positions the line vertically.

**Grading:** 2 marks per part.

---

#### S4 Solution [6 marks]

**(a)** [1 mark] 5-fold CV: 5 model fits. LOOCV: 50 model fits (one per data point).

**(b)** [2 marks] In LOOCV, each training set has $n-1 = 49$ points — the training sets are nearly identical (differing by just one point). The 50 validation errors are therefore highly correlated. Averaging correlated quantities doesn't reduce variance much. In 5-fold CV, the training sets differ more substantially (80% vs 98% of data), so the validation errors are less correlated, giving a lower-variance estimate.

**(c)** [1 mark] **Golden Rule:** Never touch the test data during model development. The test set is used exactly once for final evaluation.

Example of leakage: Computing normalization statistics (mean, std) on ALL data before splitting into train/test. The training data "knows" about test statistics. **Fix:** Split first, compute normalization on training data only, apply those statistics to transform validation/test data.

**(d)** [2 marks] Yes, this is data leakage. The mean and std include test data points, so the training data has indirect access to test set information. **Fix:** Split into train/test FIRST. Compute mean and std using only the training data. Then apply those same statistics to normalize both training and test data.

**Grading:** (a) 1 mark. (b) 1 mark for correlated folds, 1 mark for averaging correlated quantities. (c) 1 mark for golden rule + example. (d) 1 mark for identifying leakage, 1 mark for fix.

---

#### S5 Solution [6 marks]

**(a)** [2 marks] **Good fit** (or very mild underfitting). Both training and validation error are low and the gap between them is small and shrinking with more data. The curves have nearly converged, which indicates the model is neither overfitting (large gap) nor severely underfitting (both errors high).

**(b)** [1 mark] Adding more data would help only marginally. The curves have already converged, meaning the model has extracted most of the learnable signal. The remaining error is likely irreducible (noise) or due to model bias. More data primarily reduces variance (closes the gap), but the gap is already small.

**(c)** [1 mark] Since the model is already a good fit with a small gap, $\lambda$ is likely well-tuned. If anything, slightly **decreasing** $\lambda$ (less regularization) might help if there's mild underfitting — but the effect would be minimal since the curves have converged. Increasing $\lambda$ would risk pushing toward underfitting.

**(d)** [2 marks] The **complexity curve** (Week 3) fixes the training data size and varies model complexity (e.g., polynomial degree, $\lambda$). It reveals the U-shaped test error curve and helps find the sweet spot in complexity. The **learning curve** (Week 4) fixes the model and varies training set size. It reveals whether more data would help (large gap → yes) or whether the model has reached its limit (converged → no). They are complementary: the complexity curve tells you *what model to use*, the learning curve tells you *whether to collect more data*.

**Grading:** (a) 1 mark for diagnosis, 1 mark for justification. (b) 1 mark for "marginally" + converged reasoning. (c) 1 mark for reasonable answer with justification. (d) 1 mark per curve description.

---
---

## Exam Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1(a) | ERM, true vs. empirical risk | | |
| Q1(b) | OLS intercept derivation | | |
| Q1(c) | OLS slope derivation | | |
| Q1(d) | Ridge shrinkage factor | | |
| Q1(e) | Bias-variance table | | |
| Q2(a) | Diagnosing over/underfitting | | |
| Q2(b) | Monotonicity proof | | |
| Q2(c) | k-fold CV procedure | | |
| Q2(d) | Overfitting to validation set | | |
| Q2(e) | Temporal leakage | | |
| Q2(f) | R² interpretation | | |
| Q3(a) | L1 vs L2 loss, Huber | | |
| Q3(b) | L1/L2 geometry, sparsity | | |
| Q3(c) | Confusion matrix, metrics | | |
| Q3(d) | ROC/AUC | | |
| Q3(e) | Harmonic mean | | |
| S1 | Nested hypothesis spaces | | |
| S2 | Residual properties, Var decomposition | | |
| S3 | Lasso/ridge, elastic net | | |
| S4 | CV, LOOCV, data leakage | | |
| S5 | Learning curves, diagnosis | | |
