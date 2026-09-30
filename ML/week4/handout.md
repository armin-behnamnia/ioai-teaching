# Week 4 Handout: Model Evaluation & Validation

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 4 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** Week 1 (ML framework, overfitting/underfitting), Week 2 (scalar linear regression, MSE, R²), Week 3 (overfitting & regularization, generalization gap, the U-shaped curve, bias-variance intuition)

---

## 1. Motivation

### 1.1 The Fundamental Question

> **How do we know if a model is actually good?**

Last week we saw that training error is misleading — it always decreases with complexity, even when the model is overfitting. We need a way to **measure generalization**: how well the model performs on unseen data.

This week we answer: How do we split our data? How do we choose model complexity (degree, λ)? How do we measure performance for classification vs. regression? What metrics matter?

### 1.2 Why This Week?

Model evaluation is the **foundation of all ML practice**. You cannot choose between models, tune hyperparameters, or detect overfitting without proper evaluation. Every IOAI problem involves evaluation. Every real-world ML project starts with "how will I measure success?"

This week requires **no calculus** — only counting, ratios, and basic algebra. It's pulled forward in the course because it's essential for everything that follows.

### 1.3 The Golden Rule

> **Never touch the test data during model development.**

This is the single most important rule in ML. Violating it invalidates your evaluation. We'll see exactly why.

---

## 2. The Train / Validation / Test Split

### 2.1 Three Sets, Three Purposes

| Set | Purpose | When used | How often |
|-----|---------|-----------|-----------|
| **Training set** | Fit the model parameters (w, b) | Every training step | Many times |
| **Validation set** | Tune hyperparameters (degree, λ, k) | Model selection | Several times |
| **Test set** | Final, honest evaluation | ONCE, at the end | Exactly once |

### 2.2 Why Three Sets?

- **Training:** The model learns from this data. Training error is optimistic (the model has seen these examples).
- **Validation:** Used to compare different model configurations (e.g., degree 2 vs. 3, λ=0.1 vs. 1.0). Validation error is less optimistic but still somewhat biased because you're choosing based on it.
- **Test:** The "locked box." Used exactly once at the very end. Gives an honest estimate of generalization performance.

### 2.3 The Data Split

```
  All available data
  ┌──────────────────────────────────────────────────┐
  │████████████████████████████│████████████│████████│
  │  Training set (60%)        │ Validation │  Test  │
  │  Fit model parameters      │ Tune hyper │  Final │
  │                            │ parameters │  eval  │
  └──────────────────────────────────────────────────┘
                               (20%)       (20%)
```

Typical splits: 60/20/20 or 70/15/15. For large datasets, smaller test fractions are fine (e.g., 98/1/1 for millions of examples).

### 2.4 What Goes Wrong Without a Test Set?

If you use the validation set for final evaluation, your estimate is **optimistically biased**. Why? Because you chose the model that performed best on the validation set — you "mined" the validation data for the best configuration. The model that wins on validation data is partly winning by luck (fitting validation-specific noise).

The test set, used only once, avoids this. It's data the model has never seen, in any form.

### 2.5 Data Leakage

**Data leakage** occurs when information from the test/validation set "leaks" into training. Common causes:

| Leak type | Example | Why it's bad |
|-----------|---------|-------------|
| Normalizing before splitting | Compute mean/std on ALL data, then split | The training data "knows" about test statistics |
| Duplicates | Same patient appears in train and test | The model memorizes, not generalizes |
| Temporal leakage | Train on future data, test on past | Real-world deployment can't see the future |
| Feature selection before splitting | Pick top features using ALL data, then split | Feature selection "saw" the test data |

> **Prevention:** Always split FIRST. Do ALL preprocessing (normalization, feature selection, imputation) using ONLY training data. Apply the same transformations to validation/test.

---

## 3. Cross-Validation

### 3.1 The Problem with a Single Split

A single train/validation split is noisy. If you're unlucky, the validation set happens to be "easy" or "hard," giving a biased estimate of model performance.

### 3.2 k-Fold Cross-Validation

**Idea:** Split the data into $k$ equal parts (folds). Train on $k-1$ folds, validate on the remaining fold. Repeat $k$ times, each time using a different fold as validation. Average the $k$ validation errors.

```
  5-Fold Cross-Validation:
  
  Fold 1: [VAL]  [TR]  [TR]  [TR]  [TR]  → Validation error₁
  Fold 2: [TR]  [VAL] [TR]  [TR]  [TR]  → Validation error₂
  Fold 3: [TR]  [TR]  [VAL] [TR]  [TR]  → Validation error₃
  Fold 4: [TR]  [TR]  [TR]  [VAL] [TR]  → Validation error₄
  Fold 5: [TR]  [TR]  [TR]  [TR]  [VAL] → Validation error₅
  
  CV error = (error₁ + error₂ + error₃ + error₄ + error₅) / 5
```

**Typical $k$:** 5 or 10. Higher $k$ = more accurate estimate but more computation.

**Advantages:**
- Every data point is used for validation exactly once and for training $k-1$ times.
- The estimate is less noisy than a single split.
- You get a **standard deviation** across folds — a measure of stability.

### 3.3 Leave-One-Out Cross-Validation (LOOCV)

**Special case:** $k = n$ (each fold is a single data point). Train on $n-1$ examples, test on 1. Repeat $n$ times.

| Property | LOOCV | 5-fold CV |
|----------|-------|-----------|
| Number of folds | $n$ | 5 |
| Training set per fold | $n-1$ | $4n/5$ |
| Computational cost | $n$ model fits | 5 model fits |
| Bias | Low (trains on almost all data) | Slightly higher |
| Variance | Higher (folds are very similar) | Lower |
| Best for | Small datasets | Most cases |

> **Rule of thumb:** Use 5-fold or 10-fold CV for most problems. Use LOOCV only for very small datasets ($n < 50$).

### 3.4 Using Cross-Validation for Model Selection

The procedure:
1. Choose a set of candidate models (e.g., degree 1, 2, 3, ..., 10).
2. For each model, run $k$-fold CV and compute the average validation error.
3. Pick the model with the lowest average validation error.
4. (Optional) Retrain on ALL data with the chosen model.
5. Evaluate ONCE on the test set.

```
  Average CV error
    │
    │  ╱╲
    │ ╱  ╲
    │╱    ╲
    │      ╲──────
    │
    └────────────── Polynomial degree
    1   2   3   ...
         ↑
    Best degree (lowest CV error)
```

### 3.5 Overfitting to the Validation Set

Yes, you can overfit to the validation set! If you try **many** models and pick the best on validation, you're performing "multiple comparisons" — the winner is partly lucky.

**Symptoms:** Validation error is much lower than test error.

**Prevention:**
- Keep the test set locked away.
- Don't try too many models (if you try 1000 models, one will look good by chance).
- Use nested cross-validation for very rigorous evaluation (advanced).

---

## 4. Classification Metrics

### 4.1 The Confusion Matrix

For binary classification (positive/negative):

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | True Positive (TP) | False Negative (FN) |
| **Actual Negative** | False Positive (FP) | True Negative (TN) |

### 4.2 Accuracy

$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN} = \frac{\text{Correct predictions}}{\text{Total predictions}}$$

**When good:** Classes are balanced and errors are equally costly.

**When bad:** Class imbalance. If 99% of emails are not spam, a model that predicts "not spam" for everything has 99% accuracy — but it's useless.

### 4.3 Precision and Recall

$$\text{Precision} = \frac{TP}{TP + FP} = \frac{\text{Correctly predicted positive}}{\text{All predicted positive}}$$

$$\text{Recall} = \frac{TP}{TP + FN} = \frac{\text{Correctly predicted positive}}{\text{All actual positive}}$$

**Intuition:**
- **Precision:** "When the model says positive, how often is it right?" (Quality of positive predictions)
- **Recall:** "Of all the actual positives, how many did the model find?" (Coverage of actual positives)

### 4.4 The Precision-Recall Tradeoff

By adjusting the classification threshold, you can trade precision for recall:

| Threshold | Precision | Recall | Use case |
|-----------|-----------|--------|----------|
| High (0.9) | High | Low | Spam filter (don't flag good emails) |
| Low (0.1) | Low | High | Cancer screening (don't miss any cases) |
| Balanced (0.5) | Moderate | Moderate | General purpose |

```
  Precision
    │
    │ ●────── ← high threshold
    │  ╲
    │   ●
    │    ╲
    │     ● ← balanced
    │      ╲
    │       ●
    │        ╲
    │         ●────── ← low threshold
    └────────────────── Recall
```

### 4.5 F1-Score

$$F_1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$$

The **harmonic mean** of precision and recall. It's high only when BOTH are high. (Arithmetic mean would be high if either one is high — not what we want.)

**Why harmonic mean?** If precision = 0.01 and recall = 1.0 (predict everything as positive), the arithmetic mean is 0.505 (looks OK) but the harmonic mean (F1) is ~0.02 (correctly terrible). The harmonic mean punishes extreme imbalances.

### 4.6 Worked Example: Computing All Metrics

**Confusion matrix:**

| | Predicted Spam | Predicted Not Spam |
|---|---|---|
| **Actual Spam** | 80 | 20 |
| **Actual Not Spam** | 10 | 890 |

- $TP = 80$, $FP = 10$, $FN = 20$, $TN = 890$
- Total = 1000

**Accuracy:** $(80 + 890) / 1000 = 970 / 1000 = 97\%$

**Precision:** $80 / (80 + 10) = 80 / 90 = 88.9\%$

**Recall:** $80 / (80 + 20) = 80 / 100 = 80\%$

**F1:** $2 \cdot (0.889 \cdot 0.80) / (0.889 + 0.80) = 2 \cdot 0.711 / 1.689 = 0.842 = 84.2\%$

**Interpretation:** The model has 97% accuracy (looks great!), but recall is only 80% — it misses 20% of spam. Precision is 89% — when it says "spam," it's right 89% of the time.

### 4.7 Why Accuracy Is Misleading Here

Without the model, just predicting "not spam" for everything:
- Accuracy: $900 / 1000 = 90\%$ (only 10% of emails are spam)
- Precision: undefined (0/0 — no positive predictions)
- Recall: 0%
- F1: 0

The model's 97% accuracy vs. the baseline's 90% accuracy seems like a 7% improvement. But the model catches 80% of spam while the baseline catches 0%. **Precision, recall, and F1 tell the real story.**

---

## 5. ROC Curves and AUC

### 5.1 The ROC Curve

**ROC** = Receiver Operating Characteristic (from WWII radar detection).

Plot **True Positive Rate** vs. **False Positive Rate** as the classification threshold varies from 0 to 1.

$$TPR = \text{Recall} = \frac{TP}{TP + FN}$$

$$FPR = \frac{FP}{FP + TN}$$

### 5.2 Constructing an ROC Curve

For each threshold $t$ (from 1.0 down to 0.0):
1. Predict positive if $P(y=1|x) > t$, else negative.
2. Compute TPR and FPR.
3. Plot the point $(FPR, TPR)$.

```
  TPR
  1.0 │            ╱─────── ← good classifier
      │          ╱
      │        ╱
      │      ╱
      │    ╱
  0.5 │  ╱
      │╱
  0.0 │──────────────── FPR
      0.0      0.5      1.0

  Diagonal = random guessing
  Top-left corner = perfect classifier
```

### 5.3 Interpreting ROC

| Curve shape | Meaning |
|-------------|---------|
| Hugs top-left corner | Excellent classifier |
| Diagonal line | Random guessing (no signal) |
| Below diagonal | Worse than random (flip predictions!) |

### 5.4 AUC: Area Under the Curve

$$AUC = \text{Area under the ROC curve}$$

| AUC | Interpretation |
|-----|---------------|
| 1.0 | Perfect classifier |
| 0.9 | Excellent |
| 0.7 | Good |
| 0.5 | Random guessing |
| < 0.5 | Worse than random |

> **AUC = probability that the classifier ranks a random positive example higher than a random negative example.** This is a beautiful interpretation — AUC measures the model's ability to **rank** positives above negatives.

### 5.5 Worked Example: ROC Construction

**Model probabilities and true labels:**

| Example | P(spam) | True label |
|---------|---------|------------|
| 1 | 0.95 | Spam |
| 2 | 0.90 | Spam |
| 3 | 0.85 | Not spam |
| 4 | 0.70 | Spam |
| 5 | 0.50 | Not spam |
| 6 | 0.30 | Spam |
| 7 | 0.20 | Not spam |
| 8 | 0.10 | Not spam |

Sort by probability (descending) and sweep threshold:

| Threshold | TP | FP | FN | TN | TPR | FPR |
|-----------|----|----|----|----|-----|-----|
| >0.95 | 0 | 0 | 4 | 4 | 0 | 0 |
| 0.90 | 1 | 0 | 3 | 4 | 0.25 | 0 |
| 0.85 | 2 | 1 | 2 | 3 | 0.50 | 0.25 |
| 0.70 | 2 | 1 | 2 | 3 | 0.50 | 0.25 |
| 0.50 | 3 | 2 | 1 | 2 | 0.75 | 0.50 |
| 0.30 | 3 | 2 | 1 | 2 | 0.75 | 0.50 |
| 0.20 | 4 | 3 | 0 | 1 | 1.0 | 0.75 |
| 0.10 | 4 | 4 | 0 | 0 | 1.0 | 1.0 |

Plot $(FPR, TPR)$: $(0,0), (0, 0.25), (0.25, 0.50), (0.25, 0.50), (0.50, 0.75), (0.50, 0.75), (0.75, 1.0), (1.0, 1.0)$

The curve goes up and to the right. The AUC is the area under this curve.

### 5.6 When to Use ROC vs. PR Curves

| Situation | Use | Why |
|-----------|-----|-----|
| Balanced classes | ROC | Works well when both classes are common |
| Highly imbalanced classes | PR curve | ROC can look misleadingly good when negatives dominate |
| Comparing classifiers | AUC | Single number summary |

**PR curve:** Plot Precision (y-axis) vs. Recall (x-axis). More informative than ROC when the positive class is rare (e.g., fraud detection where 0.1% of transactions are fraud).

---

## 6. Regression Metrics

### 6.1 Metrics Summary

| Metric | Formula | When to use |
|--------|---------|-------------|
| **MSE** | $\frac{1}{n}\sum_i (\hat{y}_i - y_i)^2$ | When large errors are especially bad (squared penalty) |
| **RMSE** | $\sqrt{\text{MSE}}$ | Same as MSE but in same units as $y$ (interpretable) |
| **MAE** | $\frac{1}{n}\sum_i |\hat{y}_i - y_i|$ | When outliers are present (less sensitive than MSE) |
| **R²** | $1 - \frac{SS_{\text{res}}}{SS_{\text{tot}}}$ | Fraction of variance explained (dimensionless) |

### 6.2 MSE vs. MAE

- **MSE** squares errors, so large errors are penalized disproportionately. One outlier with error 10 contributes 100 to MSE but only 10 to MAE.
- **MAE** treats all errors linearly. More robust to outliers.
- **RMSE** is between MSE and MAE in sensitivity — it's MSE but in interpretable units.

| Error | MSE contribution | MAE contribution |
|-------|-----------------|-----------------|
| 1 | 1 | 1 |
| 2 | 4 | 2 |
| 5 | 25 | 5 |
| 10 | 100 | 10 |

The error of 10 dominates MSE (100 out of 130 total) but is proportional in MAE (10 out of 18).

### 6.3 R² (Recap from Week 2)

$$R^2 = 1 - \frac{\sum_i (y_i - \hat{y}_i)^2}{\sum_i (y_i - \bar{y})^2}$$

- $R^2 = 1$: perfect fit
- $R^2 = 0$: model is no better than predicting $\bar{y}$
- $R^2 < 0$: model is worse than predicting $\bar{y}$

> **R² is dimensionless** — it doesn't depend on the scale of $y$. This makes it comparable across different problems. MSE and MAE depend on units (dollars vs. cents give different MSE but same R²).

### 6.4 Choosing the Right Metric

| Problem | Metric | Why |
|---------|--------|-----|
| House price prediction | RMSE | Interpretable (error in dollars), large errors matter |
| Stock return prediction | MAE | Outliers are common; don't want them to dominate |
| Model comparison across datasets | R² | Dimensionless, comparable |
| Classification (balanced) | Accuracy | Simple, works when classes are balanced |
| Classification (imbalanced) | F1 / AUC | Accuracy misleading when one class dominates |
| Medical diagnosis | Recall | Missing a disease is much worse than a false alarm |
| Spam filtering | Precision | False positives (flagging good email) are very costly |

---

## 7. Learning Curves

### 7.1 What Is a Learning Curve?

A learning curve plots **training error and validation error** as a function of **training set size** (not complexity).

```
  Error
    │
    │  Validation
    │  ╲
    │   ╲
    │    ╲─────── ← converges as data increases
    │     ╱
    │    ╱
    │   ╱ Training
    │  ╱  (increases as data increases — harder to fit)
    │ ╱
    │╱
    └────────────────── Training set size
```

### 7.2 Diagnosing from Learning Curves

| Pattern | Training error | Validation error | Gap | Diagnosis | Fix |
|---------|---------------|-------------------|-----|-----------|-----|
| Both high, small gap | High | High | Small | **Underfitting** (high bias) | More complex model |
| Low train, high val, large gap | Low | High | Large | **Overfitting** (high variance) | More data, or regularize |
| Both low, small gap | Low | Low | Small | **Good fit** | Done! |
| Both high, large gap | High | High | Large | **Need more data AND complexity** | Add features AND data |

> **Key insight:** If the curves haven't converged (large gap), adding more data will help (reduce overfitting). If they've converged but both are high, adding data won't help — you need a more complex model.

### 7.3 Connection to Week 3

Last week we saw the **complexity curve** (error vs. model complexity). This week we see the **learning curve** (error vs. data size). They're complementary:

- **Complexity curve:** Fixed data, vary model → find the sweet spot in complexity.
- **Learning curve:** Fixed model, vary data → determine if more data would help.

---

## 8. Connections

### 8.1 What This Enables

| Next Week | How It Uses Week 4 |
|-----------|-------------------|
| Week 5: Probability for ML | Formal bias-variance decomposition (uses train/test framework) |
| Week 6: Gradient Descent | Validation error to monitor training, early stopping |
| Week 7: Logistic Regression | Cross-entropy loss, classification metrics applied |
| Week 8: Matrix LR + Consolidation | Choose degree/λ via cross-validation |
| Week 9: k-NN | Choose k via cross-validation |
| Week 10: Decision Trees | Choose depth via cross-validation, evaluate trees |
| Week 13-14: SVMs | Choose C via cross-validation |

### 8.2 Key Vocabulary to Master

- [ ] Training / validation / test sets
- [ ] The golden rule: never touch test data during development
- [ ] Data leakage
- [ ] k-fold cross-validation
- [ ] Leave-one-out cross-validation (LOOCV)
- [ ] Overfitting to the validation set
- [ ] Confusion matrix (TP, FP, FN, TN)
- [ ] Accuracy, precision, recall, F1-score
- [ ] Why accuracy fails with class imbalance
- [ ] The precision-recall tradeoff
- [ ] ROC curve (TPR vs. FPR)
- [ ] AUC (area under ROC curve)
- [ ] PR curve (when to use instead of ROC)
- [ ] MSE, RMSE, MAE, R²
- [ ] Learning curves (error vs. training size)
- [ ] Diagnosing underfitting/overfitting from learning curves

---

## 9. Exercises

### [Basic]

**E1.** Given this confusion matrix, compute accuracy, precision, recall, and F1:

| | Predicted + | Predicted − |
|---|---|---|
| **Actual +** | 45 | 5 |
| **Actual −** | 15 | 35 |

**E2.** Explain in one sentence: why is accuracy a bad metric when classes are imbalanced? Give a concrete example.

**E3.** You have 1000 examples. You use 5-fold cross-validation. How many examples are in each training fold? How many in each validation fold? How many total model fits will you do?

**E4.** What is data leakage? Give one example of how it can happen accidentally. How do you prevent it?

### [Intermediate]

**E5.** You're building a model to detect a rare disease that affects 0.1% of the population. Your model achieves 99.9% accuracy. Should you be impressed? What metric would you look at instead? What could the model be doing to achieve 99.9% accuracy?

**E6.** Two models have the following ROC curves:
- Model A: AUC = 0.85
- Model B: AUC = 0.72

Which is better? What does the AUC number mean in plain English?

**E7.** Your model has training MSE = 1.2 and validation MSE = 5.8. What is happening? Name three possible fixes.

**E8.** Fill in the confusion matrix given: precision = 0.80, recall = 0.60, and there are 100 actual positives. Compute TP, FP, FN, TN (assume 200 actual negatives), accuracy, and F1.

### [★ Advanced]

**E9.** Prove that **AUC = P(score(positive) > score(negative))**, i.e., the probability that a randomly chosen positive example has a higher model score than a randomly chosen negative example.  
*(Hint: Think about what happens as you sweep the threshold. Each point on the ROC curve corresponds to a threshold. The area under the curve can be computed as a sum over all pairs of (positive, negative) examples.)*

**E10.** The **Fβ-score** generalizes F1:
$$F_\beta = (1 + \beta^2) \cdot \frac{\text{Precision} \cdot \text{Recall}}{\beta^2 \cdot \text{Precision} + \text{Recall}}$$
(a) What does $\beta = 2$ emphasize (precision or recall)? What about $\beta = 0.5$?  
(b) Show that $F_1$ is the harmonic mean of precision and recall.  
(c) What happens to $F_\beta$ as $\beta \to \infty$? As $\beta \to 0$? Explain why these limits make sense.

**E11.** ★★ For linear regression, the **LOOCV error** has a beautiful closed-form formula:
$$\text{LOOCV} = \frac{1}{n}\sum_{i=1}^{n} \left(\frac{y_i - \hat{y}_i}{1 - h_{ii}}\right)^2$$
where $h_{ii}$ is the $i$-th diagonal element of the hat matrix $\mathbf{H} = \mathbf{X}(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T$ (from Week 2/8).
(a) Why does this formula make sense? What does $1 - h_{ii}$ represent?  
(b) What happens when $h_{ii}$ is close to 1? What does that mean about the $i$-th data point?  
(c) Why is this formula useful compared to actually running $n$ regressions?  
*(Note: This uses matrix notation from Week 8. You can attempt the intuition now and revisit after Week 8.)*

**E12.** ★★ You have a dataset with 10,000 examples (100 positive, 9900 negative). You want to compare two models:
- Model A: 80 TP, 20 FN, 100 FP, 9800 TN
- Model B: 60 TP, 40 FN, 10 FP, 9890 TN

(a) Compute accuracy, precision, recall, and F1 for both models.  
(b) Compute AUC for both (you may need to estimate from the confusion matrix).  
(c) Which model would you choose for: (i) cancer screening, (ii) spam filtering? Why?  
(d) This exercise demonstrates why a single metric is insufficient. Discuss.

---

## 10. Summary

### Key Equations

> **Confusion Matrix:** TP, FP, FN, TN

> **Accuracy:** $\frac{TP + TN}{TP + TN + FP + FN}$

> **Precision:** $\frac{TP}{TP + FP}$

> **Recall:** $\frac{TP}{TP + FN}$

> **F1:** $2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$

> **TPR (Recall):** $\frac{TP}{TP + FN}$

> **FPR:** $\frac{FP}{FP + TN}$

> **AUC:** Area under the ROC curve = P(score(+) > score(−))

> **R²:** $1 - \frac{SS_{\text{res}}}{SS_{\text{tot}}}$

### Key Intuition (If You Remember Nothing Else...)

1. **Never touch the test set during model development.** Train on training, tune on validation, evaluate on test — once.
2. **Cross-validation reduces the noise** of a single train/validation split. Use 5-fold or 10-fold for most problems.
3. **Accuracy is misleading with imbalanced classes.** Use precision, recall, F1, or AUC instead.
4. **Precision = quality of positive predictions. Recall = coverage of actual positives.** They trade off against each other.
5. **F1 is the harmonic mean** of precision and recall — high only when both are high.
6. **ROC/AUC measures ranking ability** — the probability that a random positive scores higher than a random negative.
7. **Learning curves diagnose problems:** large gap = overfitting (need more data), both high = underfitting (need more complexity).
8. **Data leakage invalidates evaluation.** Always split first, then preprocess.
9. **Choose metrics for the problem:** medical → recall, spam → precision, imbalanced → F1/AUC.

---

*Next week: Probability for Machine Learning. We'll formalize the bias-variance decomposition we've been building intuitively, derive MSE from the Gaussian noise assumption (MLE), and discover that ridge regression has a deep probabilistic meaning (MAP with a Gaussian prior). The probability toolkit we build this week will power everything from logistic regression to neural networks.*
