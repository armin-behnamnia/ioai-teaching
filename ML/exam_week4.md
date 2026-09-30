# Exam: Week 4 — Model Evaluation & Validation

> **Course:** Machine Learning for IOAI Preparation  
> **Exam Duration:** 40 minutes  
> **Coverage:** Week 4 (Train/val/test splits, cross-validation, data leakage, classification metrics, ROC/AUC, regression metrics, learning curves)  
> **Format:** 3 long-answer multi-part questions + 5 short-answer questions  
> **Closed notes. Calculators permitted.**

---

## Part A: Long-Answer Questions (25 minutes)

### Question 1 [8 marks] — Data Splitting and Cross-Validation

You have a dataset of 500 examples and need to choose a polynomial degree $d \in \{1, 2, 3, 4, 5, 6\}$.

**(a)** [3 marks] You use a 60/20/20 split. How many examples are in each set (training, validation, test)? State the Golden Rule and explain what goes wrong if you use the test set for hyperparameter tuning.

**(b)** [3 marks] You use 5-fold cross-validation on the training set to choose the degree. How many examples are in each training fold and validation fold? How many total model fits will you perform across all candidate degrees? Briefly state the final step after CV selects the best degree.

**(c)** [2 marks] Briefly explain why LOOCV has higher variance than 5-fold CV.

---

### Question 2 [8 marks] — Classification Metrics and Class Imbalance

A classifier detects a rare disease (0.5% prevalence) on 10,000 test examples (50 positive, 9,950 negative):

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | 42 | 8 |
| **Actual Negative** | 110 | 9,840 |

**(a)** [4 marks] Compute: (i) accuracy, (ii) precision, (iii) recall, (iv) F1-score.

**(b)** [2 marks] What accuracy does a trivial baseline (predict "negative" for all) achieve? Explain why the startup's reported "98.8% accuracy" is misleading.

**(c)** [2 marks] If the startup lowers the classification threshold from 0.5 to 0.1, what happens to precision and recall? Is this appropriate for disease screening? Justify.

---

### Question 3 [9 marks] — ROC/AUC, Regression Metrics, and Learning Curves

A classifier outputs probabilities for 6 test examples:

| Example | P(positive) | True Label |
|---------|-------------|------------|
| 1 | 0.90 | Positive |
| 2 | 0.80 | Negative |
| 3 | 0.60 | Positive |
| 4 | 0.40 | Negative |
| 5 | 0.20 | Positive |
| 6 | 0.10 | Negative |

**(a)** [4 marks] Sweep the threshold from 1.0 to 0.0. For each distinct threshold, compute TPR and FPR. Fill in a table with columns: Threshold, TP, FP, TPR, FPR.

**(b)** [2 marks] State the probabilistic interpretation of AUC in one sentence. Is an AUC of 0.5 good or bad? What does it mean?

**(c)** [3 marks] You observe the following learning curve: training error is low, validation error is high, and there is a large gap that is not closing as data increases. What is the diagnosis? Would adding more data help? Would increasing or decreasing model complexity help?

---

## Part B: Short-Answer Questions (15 minutes)

**S1.** [3 marks] You compute the mean and standard deviation of all features using the entire dataset, then split into train/test and normalize both sets. What type of problem is this, why is it problematic, and how do you fix it?

---

**S2.** [3 marks] You try 100 different models and pick the one with the lowest validation error. Is this validation error a reliable estimate of generalization? Name the phenomenon. How does the test set mitigate it?

---

**S3.** [3 marks] You have 1,000 examples and use 5-fold cross-validation comparing 4 candidate models. How many examples are in each validation fold? How many total model fits are performed?

---

**S4.** [3 marks] A learning curve shows both training and validation error high and converged (small gap). What is the diagnosis? Would adding more data help? What would help instead?

---

**S5.** [3 marks] For each scenario, state which metric you would prioritize and why in one sentence:

(a) Cancer screening — missing a positive case is 100× worse than a false alarm.

(b) Spam filtering — flagging a legitimate email as spam is very costly.

(c) Comparing regression models across different datasets — you want a dimensionless metric.

---
---

## Solutions

### Question 1 Solutions

**(a)** [3 marks]

- Training: $500 \times 0.60 = 300$, Validation: $500 \times 0.20 = 100$, Test: $500 \times 0.20 = 100$.

**Golden Rule:** Never touch the test data during model development.

**What goes wrong:** If you use the test set for tuning, you're selecting the model that got lucky on test data. The test set becomes a second validation set, and your estimate of generalization is optimistically biased — the winner is partly fitting test-specific noise.

**Grading:** 1 mark for split sizes, 1 mark for Golden Rule, 1 mark for explaining the consequence.

---

**(b)** [3 marks]

- Training data = 300. Each fold: $300/5 = 60$ in validation, $300 - 60 = 240$ in training.
- Total fits: 5 folds $\times$ 6 candidate degrees $= 30$ fits.
- Final step: Retrain on all 300 training examples with the chosen degree, then evaluate ONCE on the test set.

**Grading:** 1 mark for fold sizes, 1 mark for total fits, 1 mark for the final step (retrain + evaluate once on test).

---

**(c)** [2 marks]

In LOOCV, each training set has $n-1$ examples — the training sets are nearly identical (differ by one point). The $n$ validation errors are therefore highly correlated. Averaging correlated quantities doesn't reduce variance much. In 5-fold CV, training sets differ more substantially (80% vs. 98% of data), so validation errors are less correlated, giving a lower-variance estimate.

**Grading:** 1 mark for "training sets nearly identical / correlated," 1 mark for "averaging correlated values doesn't reduce variance."

---

### Question 2 Solutions

**(a)** [4 marks]

$TP = 42$, $FP = 110$, $FN = 8$, $TN = 9{,}840$. Total $= 10{,}000$.

- **Accuracy** $= (42 + 9{,}840) / 10{,}000 = 9{,}882 / 10{,}000 = 98.82\%$
- **Precision** $= 42 / (42 + 110) = 42 / 152 = 27.6\%$
- **Recall** $= 42 / (42 + 8) = 42 / 50 = 84.0\%$
- **F1** $= 2 \times (0.276 \times 0.840) / (0.276 + 0.840) = 0.464 / 1.116 = 41.6\%$

**Grading:** 1 mark per metric. Minor rounding acceptable.

---

**(b)** [2 marks]

Baseline accuracy (predict "negative" for all): $9{,}950 / 10{,}000 = 99.5\%$.

The baseline achieves **higher** accuracy than the model (99.5% vs. 98.8%)! Accuracy is dominated by the majority class (9,950 negatives). It doesn't reflect the model's ability to detect the rare positive class. The real story is in precision (27.6%) and recall (84%).

**Grading:** 1 mark for baseline accuracy, 1 mark for explaining why accuracy is misleading (majority class dominates / baseline > model).

---

**(c)** [2 marks]

Lowering the threshold to 0.1: the model predicts positive more often → recall increases (catches more positives), but precision decreases (more false positives).

This is appropriate for disease screening: missing a positive case (false negative) is far worse than a false alarm. We want high recall, even at the cost of precision.

**Grading:** 1 mark for correct direction (recall up, precision down), 1 mark for justification (FN cost >> FP cost).

---

### Question 3 Solutions

**(a)** [4 marks]

3 positives, 3 negatives. Sort by probability (descending):

| Threshold | TP | FP | TPR | FPR |
|-----------|----|----|-----|-----|
| > 0.90 | 0 | 0 | 0 | 0 |
| 0.80 | 1 | 1 | 0.33 | 0.33 |
| 0.60 | 2 | 1 | 0.67 | 0.33 |
| 0.40 | 2 | 2 | 0.67 | 0.67 |
| 0.20 | 3 | 2 | 1.0 | 0.67 |
| 0.10 | 3 | 3 | 1.0 | 1.0 |

**Explanation (threshold = 0.60):** Predict positive if $P \geq 0.60$. Examples 1 (0.90, pos), 2 (0.80, neg), 3 (0.60, pos) are positive predictions. TP = 2 (ex 1, 3), FP = 1 (ex 2). TPR = 2/3 ≈ 0.67, FPR = 1/3 ≈ 0.33.

**Grading:** 1 mark for correct TP/FP values, 1 mark for correct TPR, 1 mark for correct FPR, 1 mark for correct threshold ordering including (0,0) and (1,1) endpoints.

---

**(b)** [2 marks]

**Interpretation:** AUC = the probability that the classifier ranks a randomly chosen positive example higher than a randomly chosen negative example.

AUC = 0.5 means random guessing — the model has no discriminative power. It is bad; the model is no better than a coin flip at ranking positives above negatives.

**Grading:** 1 mark for the interpretation, 1 mark for "random guessing / no discriminative power."

---

**(c)** [3 marks]

**Diagnosis:** Overfitting (high variance).

- Training error low → fits training data well.
- Validation error high → doesn't generalize.
- Large gap not closing → fitting noise, not signal.

**More data?** Unlikely to help significantly — the gap isn't closing, meaning the model's complexity is the issue, not data scarcity.

**Complexity?** Decrease model complexity (or increase regularization $\lambda$). The model has too much capacity — reducing it will raise training error but lower validation error, closing the gap.

**Grading:** 1 mark for diagnosis, 1 mark for "more data won't help (gap not closing)," 1 mark for "decrease complexity / increase regularization."

---

### Short-Answer Solutions

#### S1 Solution [3 marks]

**Type:** Data leakage through preprocessing (normalizing before splitting).

**Why problematic:** The mean and standard deviation include test data, so the training data indirectly "knows" about test set statistics. This gives an over-optimistic estimate of generalization.

**Fix:** Split FIRST. Compute mean/std on training data only. Apply those statistics to normalize both training and test sets.

**Grading:** 1 mark for type, 1 mark for why, 1 mark for fix.

---

#### S2 Solution [3 marks]

**Reliable?** No. With 100 models, some will look good on the validation set by chance. The winner's validation error (1.8%) is optimistically biased — it partly reflects luck rather than true generalization.

**Phenomenon:** Overfitting to the validation set (multiple comparisons problem).

**Test set mitigation:** The test set is used exactly once, after all model selection. Since no model was chosen based on the test set, there is no selection bias, giving an honest estimate.

**Grading:** 1 mark for "not reliable" + explanation, 1 mark for naming the phenomenon, 1 mark for test set mitigation.

---

#### S3 Solution [3 marks]

- Each validation fold: $1{,}000 / 5 = 200$ examples.
- Total model fits: 5 folds $\times$ 4 candidate models $= 20$ fits.

**Grading:** 1 mark for validation fold size, 1 mark for training fold size (implied: 800), 1 mark for total fits. (Accept 1 mark for fold size + 1 mark for total fits + 1 mark for showing work.)

---

#### S4 Solution [3 marks]

**Diagnosis:** Underfitting (high bias). Both errors are high and the gap is small — the model is systematically wrong (too simple).

**More data?** No. The curves have converged, meaning the model has extracted all the signal it can. More data reduces variance, not bias.

**What would help:** Increase model complexity (higher degree, more features, decrease $\lambda$). The model needs more capacity to capture the underlying pattern.

**Grading:** 1 mark for diagnosis, 1 mark for "no, more data won't help," 1 mark for "increase complexity."

---

#### S5 Solution [3 marks]

**(a)** **Recall.** Missing a cancer case (false negative) is 100× worse than a false alarm. Recall measures how many actual positives the model catches — maximize recall, accept lower precision.

**(b)** **Precision.** Flagging a legitimate email as spam (false positive) is very costly. Precision measures how reliable the positive (spam) predictions are — maximize precision, accept lower recall.

**(c)** **$R^2$.** It is dimensionless (doesn't depend on units), making it comparable across datasets with different scales.

**Grading:** 1 mark per scenario. Must state the metric AND justify.

---
---

## Exam Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1(a) | Split sizes, Golden Rule | | |
| Q1(b) | k-fold CV computation | | |
| Q1(c) | LOOCV variance | | |
| Q2(a) | Confusion matrix metrics | | |
| Q2(b) | Baseline, misleading accuracy | | |
| Q2(c) | Threshold tradeoff | | |
| Q3(a) | ROC construction | | |
| Q3(b) | AUC interpretation | | |
| Q3(c) | Learning curve diagnosis | | |
| S1 | Data leakage | | |
| S2 | Overfitting to validation set | | |
| S3 | k-fold CV computation | | |
| S4 | Learning curve, underfitting | | |
| S5 | Choosing the right metric | | |
