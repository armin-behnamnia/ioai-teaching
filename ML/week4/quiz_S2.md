# Week 4, Session 2 — End-of-Session Quiz

> **Time:** 10 minutes  
> **Topics:** Classification metrics (confusion matrix, precision, recall, F1), accuracy and imbalance, ROC/AUC, choosing the right metric, learning curves  
> **Format:** 6 questions, mix of conceptual, calculation, multiple choice, and scenarios  
> **Closed notes**  
> **Note:** Q6 is a spiral-back question from Week 3.

---

## Questions

**Q1. [Calculation — 3 min]**

Given the following confusion matrix:

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | 60 | 40 |
| **Actual Negative** | 15 | 85 |

Compute:
(a) Accuracy  
(b) Precision  
(c) Recall  
(d) F1-score

**Q2. [Conceptual — 2 min]**

A disease affects 0.5% of the population. A model achieves 99.5% accuracy. Explain why this number is misleading. What could the model be doing to achieve 99.5% accuracy? What metric(s) would you look at instead?

**Q3. [Multiple choice — 1 min]**

What does AUC (Area Under the ROC Curve) measure?

(a) The accuracy of the classifier at the optimal threshold.  
(b) The probability that the classifier ranks a random positive example higher than a random negative example.  
(c) The fraction of correctly classified examples.  
(d) The harmonic mean of precision and recall.

Justify your answer in one sentence.

**Q4. [Scenarios — 2 min]**

For each scenario below, state which metric you would prioritize and why:

(a) A cancer screening model — you really don't want to miss any positive cases.  
(b) A spam filter — you really don't want to flag a legitimate email as spam.  
(c) A model predicting house prices — you want the error to be in the same units as the price.

**Q5. [Conceptual — 1 min]**

The following learning curve shows training error and validation error as a function of training set size:

```
  Error
    │  Validation
    │  ╲
    │   ╲────────          ← Large gap
    │    ╱
    │   ╱
    │  ╱ Training (low)
    │ ╱
    │╱
    └────────────────── Training set size
```

What is the diagnosis (overfitting or underfitting)? What is one fix you would try?

**Q6. [Spiral-back from Week 3 — 1 min]**

Last week, we learned about regularization (ridge regression) and the regularization parameter $\lambda$. How does cross-validation (which we learned this week) help you choose the best value of $\lambda$? State the procedure in 2–3 sentences.

**★ [Challenge — optional, 2 min]**

Two models are evaluated on a dataset with 100 positives and 9900 negatives:

- **Model A:** TP = 80, FP = 100, FN = 20, TN = 9800  
- **Model B:** TP = 60, FP = 10, FN = 40, TN = 9890  

(a) Compute accuracy, precision, recall, and F1 for both models.  
(b) Which model would you choose for cancer screening? Which for spam filtering? Why?  
(c) This exercise demonstrates why a single metric is insufficient. Explain in one sentence.

---
---

## Solutions

### Q1. Solution

Given: TP = 60, FN = 40, FP = 15, TN = 85. Total = 200.

**(a) Accuracy** = (TP + TN) / Total = (60 + 85) / 200 = 145 / 200 = **72.5%**

**(b) Precision** = TP / (TP + FP) = 60 / (60 + 15) = 60 / 75 = **80.0%**

**(c) Recall** = TP / (TP + FN) = 60 / (60 + 40) = 60 / 100 = **60.0%**

**(d) F1** = 2 · (Precision · Recall) / (Precision + Recall) = 2 · (0.80 · 0.60) / (0.80 + 0.60) = 2 · 0.48 / 1.40 = 0.96 / 1.40 = **68.6%**

**Grading:** 0–3 scale.  
- 3: All four parts correct with correct calculations.  
- 2: Three parts correct, or correct method with minor arithmetic errors.  
- 1: One or two parts correct.  
- 0: No correct work.

**Common mistakes to watch for:**
- Swapping precision and recall. Precision = TP / (TP + FP) [predicted positive column]. Recall = TP / (TP + FN) [actual positive row]. If a student swaps them, they'd get precision = 60% and recall = 80% — check which is which.
- Computing F1 as the arithmetic mean (0.70) instead of the harmonic mean (0.686). The arithmetic mean is close but wrong.
- Using the wrong denominator for accuracy (e.g., dividing by 100 instead of 200).
- Forgetting to convert to percentage. Either fraction or percentage is acceptable, but be consistent.

### Q2. Solution

**Why accuracy is misleading:** With 0.5% prevalence, only 5 in 1000 people have the disease. A model that predicts "healthy" for EVERYONE achieves 99.5% accuracy — it correctly classifies all 995 healthy people and misses all 5 sick people. This is a useless model despite the high accuracy.

**What the model could be doing:** Simply predicting "negative" (healthy) for every single input, regardless of features. This trivial baseline achieves 99.5% accuracy.

**Better metrics:** Recall (sensitivity) — to measure how many of the actual positive cases the model catches. Precision — to measure how reliable the positive predictions are. F1 or AUC — for a balanced summary. For disease screening, recall is the most important: missing a sick patient is far worse than a false alarm.

**Grading:** 0–3 scale.  
- 3: Correctly explains why accuracy is misleading (baseline gets 99.5%), identifies the trivial model (predict all negative), and names at least one appropriate alternative metric.  
- 2: Two of three elements correct.  
- 1: One element correct.  
- 0: Nothing correct.

**Acceptable variations:**
- "The model could just predict 'no disease' for everyone" ✓
- "99.5% of people are healthy, so always predicting healthy gives 99.5%" ✓
- Alternative metrics: recall, sensitivity, F1, AUC, PR curve ✓
- Mentioning precision is acceptable but recall is more important for this scenario ✓

**Common mistakes to watch for:**
- Saying "the model is overfitting" — this isn't about overfitting. It's about class imbalance making accuracy meaningless. The model isn't necessarily overfitting; it might just be trivial.
- Not identifying the trivial baseline. The key insight is that doing NOTHING gives 99.5% accuracy. If students don't mention this, they're missing the main point.
- Suggesting accuracy is still useful "if you also look at other metrics." Accuracy alone is misleading here; the student should recommend replacing it, not supplementing it.

### Q3. Solution

**Answer: (b)** The probability that the classifier ranks a random positive example higher than a random negative example.

**Justification:** AUC measures the model's ranking ability — not its classification at a single threshold, but how well it orders positives above negatives across all thresholds. An AUC of 1.0 means every positive is ranked above every negative; 0.5 means random ordering.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning ranking or ordering of positives vs. negatives.  
- 2: Correct answer, weak justification.  
- 1: Wrong answer but reasonable justification.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a): AUC is NOT accuracy at a single threshold. It's the area under the entire ROC curve, summarizing performance across ALL thresholds. A single point on the ROC curve corresponds to one threshold; AUC integrates over all of them.
- Choosing (d): F1 is the harmonic mean of precision and recall, not AUC. AUC is the area under the ROC curve (TPR vs FPR).
- Choosing (c): That's the definition of accuracy, not AUC.

### Q4. Solution

**(a) Cancer screening → Recall.**  
Missing a positive case (false negative) is potentially fatal — a sick patient goes untreated. False positives (false alarms) are costly (extra tests, anxiety) but not life-threatening. Recall measures how many actual positives we catch, so we prioritize it.

**(b) Spam filter → Precision.**  
A false positive (legitimate email → spam folder) means the user misses an important email. A false negative (spam → inbox) is annoying but not catastrophic. Precision measures how reliable the positive (spam) predictions are, so we prioritize it.

**(c) House price prediction → RMSE.**  
RMSE is in the same units as the target variable (dollars). An RMSE of $20,000 means the model's predictions are off by about $20,000 on average (in the squared-error sense). MSE is in squared dollars (hard to interpret), and R² is dimensionless (good for comparison but not interpretable as a dollar amount).

**Grading:** 0–3 scale (one point per scenario).  
- 3: All three correct with correct justification.  
- 2: Two correct with justification.  
- 1: One correct with justification.  
- 0: None correct.

**Acceptable variations:**
- (a) "Recall" or "sensitivity" or "TPR" ✓. Also acceptable: "F1 with β > 1" (F2-score, which weights recall more) ✓
- (b) "Precision" ✓. Also acceptable: "F1 with β < 1" (F0.5-score) ✓
- (c) "RMSE" ✓. Also acceptable: "MAE" (if the student justifies that outliers are common in housing) ✓. R² is acceptable IF the student notes it's dimensionless and they want comparability rather than interpretability.

**Common mistakes to watch for:**
- (a) Saying "accuracy" — accuracy is misleading for medical screening (imbalanced, and doesn't distinguish error types).
- (b) Saying "accuracy" — same issue. Spam filtering is also imbalanced and error types matter.
- (c) Saying "MSE" — MSE is in squared dollars, not the same units. RMSE fixes this. Give partial credit if the student says MSE and acknowledges the units issue.

### Q5. Solution

**Diagnosis: Overfitting (high variance).**

The training error is low (the model fits the training data well) but the validation error is high and there's a large gap between them. This means the model is fitting noise in the training data rather than learning generalizable patterns.

**Fix (any one of the following):**
- Add more training data (this would close the gap — the curves would converge).
- Increase regularization (add or increase $\lambda$ in ridge regression — this constrains the model and reduces overfitting).
- Reduce model complexity (use a lower polynomial degree, fewer features, a simpler model).
- Use early stopping (if applicable — stop training before the model overfits).

**Grading:** 0–3 scale.  
- 3: Correct diagnosis (overfitting) + valid fix.  
- 2: Correct diagnosis, weak or no fix.  
- 1: Wrong diagnosis but reasonable fix (e.g., says "underfitting" but suggests "add more data" — the fix is wrong for the diagnosis, but shows some understanding).  
- 0: Wrong diagnosis and no valid fix.

**Common mistakes to watch for:**
- Saying "underfitting" — underfitting has BOTH errors high with a SMALL gap. The large gap with low training error is the hallmark of overfitting.
- Suggesting "make the model more complex" — this would make overfitting WORSE, not better. The model is already too complex.
- Suggesting "add more features" — this increases complexity and would worsen overfitting.

### Q6. Solution (Spiral-Back)

**Procedure for choosing $\lambda$ via cross-validation:**

1. Choose a set of candidate $\lambda$ values (e.g., $\lambda = 0.001, 0.01, 0.1, 1, 10$).
2. For each $\lambda$, run k-fold cross-validation: split the training data into $k$ folds, train on $k-1$ folds with that $\lambda$, evaluate on the held-out fold, and average the $k$ validation errors.
3. Select the $\lambda$ with the lowest average validation (CV) error.
4. (Optional) Retrain on all training data with the chosen $\lambda$.
5. Evaluate ONCE on the test set.

**Key point:** Cross-validation provides a reliable estimate of how well each $\lambda$ value generalizes, allowing us to pick the best one without touching the test set. This is exactly the model selection procedure from Session 1 (handout Section 3.4), applied to the regularization parameter.

**Grading:** 0–3 scale.  
- 3: Describes trying multiple $\lambda$ values, using CV to estimate validation error for each, and picking the $\lambda$ with lowest CV error. Mentions not touching the test set.  
- 2: Describes the procedure but misses a key step (e.g., doesn't mention averaging across folds, or doesn't mention trying multiple $\lambda$ values).  
- 1: Vaguely mentions using CV or validation data to choose $\lambda$ but lacks detail.  
- 0: No correct answer.

**Acceptable variations:**
- "Try different $\lambda$ values, use cross-validation to see which gives the lowest validation error, pick that one" ✓
- Mentioning the U-shaped curve from Week 3 (CV error vs. $\lambda$ is U-shaped) ✓ — this is a great connection.
- Mentioning that the test set is NOT used for $\lambda$ selection ✓

**Common mistakes to watch for:**
- Saying "use the test set to choose $\lambda$" — NO! The test set is for final evaluation only. $\lambda$ is chosen using the validation set or cross-validation.
- Saying "choose the $\lambda$ that gives the lowest training error" — training error always decreases as $\lambda \to 0$ (less regularization = more overfitting). Training error doesn't help choose $\lambda$.
- Not connecting to the U-shaped curve from Week 3. The CV error vs. $\lambda$ curve is U-shaped, just like the complexity curve. This is the key spiral-back connection.

### ★ Challenge Solution

**(a) Compute metrics for both models:**

**Model A:** TP = 80, FP = 100, FN = 20, TN = 9800. Total = 10,000.

- Accuracy = (80 + 9800) / 10000 = 9880 / 10000 = **98.8%**
- Precision = 80 / (80 + 100) = 80 / 180 = **44.4%**
- Recall = 80 / (80 + 20) = 80 / 100 = **80.0%**
- F1 = 2 · (0.444 · 0.80) / (0.444 + 0.80) = 2 · 0.355 / 1.244 = 0.711 / 1.244 = **57.1%**

**Model B:** TP = 60, FP = 10, FN = 40, TN = 9890. Total = 10,000.

- Accuracy = (60 + 9890) / 10000 = 9950 / 10000 = **99.5%**
- Precision = 60 / (60 + 10) = 60 / 70 = **85.7%**
- Recall = 60 / (60 + 40) = 60 / 100 = **60.0%**
- F1 = 2 · (0.857 · 0.60) / (0.857 + 0.60) = 2 · 0.514 / 1.457 = 1.029 / 1.457 = **70.6%**

**(b) Which model for which scenario?**

- **Cancer screening → Model A.** Model A has higher recall (80% vs 60%). In cancer screening, missing a positive case (false negative) is far worse than a false alarm. Model A catches 80% of positives vs only 60% for Model B. Model A's lower precision (more false alarms) is an acceptable tradeoff.

- **Spam filtering → Model B.** Model B has much higher precision (85.7% vs 44.4%). In spam filtering, a false positive (flagging a good email as spam) is very costly. Model B makes fewer false positive errors (10 vs 100). Model B's lower recall (misses more spam) is an acceptable tradeoff — some spam in the inbox is annoying but not harmful.

**(c) Why a single metric is insufficient:**

Model B has higher accuracy (99.5% vs 98.8%) and higher F1 (70.6% vs 57.1%), but Model A has higher recall (80% vs 60%). If we only looked at accuracy, we'd choose Model B — but for cancer screening, Model A is clearly better because it catches more cases. Different applications prioritize different types of errors, so no single metric captures everything we care about.

**Grading:** Bonus — not counted toward the base score.  
- "Excellent": All parts correct with clear reasoning.  
- "Good attempt": Most calculations correct, correct model choices, partial reasoning.  
- "Attempted": Tried but significant errors in calculation or reasoning.

**The deeper lesson:** This challenge mirrors the Davis & Goadrich paper's central point. On an imbalanced dataset (100 positives, 9900 negatives), accuracy is dominated by the true negatives and doesn't reflect the model's ability to identify the positive class. The choice between Model A and Model B depends on the application's cost structure, not on any single metric.

---
---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Confusion matrix computation | | |
| Q2 | Accuracy and class imbalance | | |
| Q3 | AUC interpretation | | |
| Q4 | Choosing the right metric | | |
| Q5 | Learning curve diagnosis | | |
| Q6 | Spiral-back: CV for λ selection | | |
| ★ | Multi-metric comparison on imbalanced data | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Can students compute precision/recall/F1 from a confusion matrix? → If not, practice at the start of Week 5. This is a foundational skill.
- [ ] Do students understand WHY accuracy fails with imbalance? → If not, present the "predict all negative" baseline example again.
- [ ] Do students know the AUC probability interpretation? → This is a key exam/competition concept. If missed, re-emphasize in Week 7 (logistic regression).
- [ ] Can students read a learning curve and diagnose overfitting vs. underfitting? → If not, draw the four patterns on the board next week.
- [ ] Did students connect CV to λ selection (Q6)? → This is the spiral-back to Week 3. If they can't make the connection, review the model selection procedure.
- [ ] Did any students attempt the challenge? How did they do? → Note for differentiation. The challenge reinforces the paper's main point.

### Topics to spiral back in future quizzes:

- Confusion matrix / precision / recall → spiral back in Week 7 (logistic regression, cross-entropy)
- ROC / AUC → spiral back in Week 7 (logistic regression ROC curves) and Week 14 (neural network evaluation)
- Choosing the right metric → spiral back in every week that introduces a new model (k-NN Week 9, trees Week 10, SVM Week 13)
- Learning curves → spiral back in Week 6 (gradient descent, monitoring training) and Week 16 (neural network training)
- CV for hyperparameter selection → spiral back in Week 8 (degree selection), Week 9 (k selection), Week 10 (depth selection), Week 13 (C selection)
