# Week 4 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): Train/Val/Test Splits & Cross-Validation

### Learning Objectives

By the end of this session, students should be able to:
1. Explain the roles of training, validation, and test sets and why three sets are needed (not two).
2. State the Golden Rule: never touch the test data during model development.
3. Describe the k-fold cross-validation procedure and compute fold sizes for given $k$ and $n$.
4. Compare k-fold CV to LOOCV — when to use each, and the bias-variance tradeoff between them.
5. Define data leakage, give at least two examples, and explain how to prevent it.
6. Explain how overfitting to the validation set occurs and why the test set mitigates it.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos open in browser (for the k-fold visual — see `visual_demos.md`)
- Printed or projected handout Sections 2–3
- Colored markers or chalk (for the k-fold diagram — 5 colors)
- Quiz S1 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:08 | **Recap of Week 3 + Hook.** | See Hook section below. |
| 0:08–0:25 | **Train/val/test split: three sets, three purposes.** | Draw the split diagram. The Golden Rule goes here. |
| 0:25–0:35 | **Data leakage.** | The four leakage types. This is practical and students find it engaging. |
| 0:35–0:55 | **k-Fold cross-validation.** | This is the centerpiece. Draw the 5-fold diagram. Compute fold sizes with students. |
| 0:55–0:62 | **LOOCV.** | Special case $k = n$. Compare to 5-fold using the table. |
| 0:62–0:70 | **Overfitting to the validation set + model selection procedure.** | The 5-step procedure. Connect to Week 3's $\lambda$ tuning. |
| 0:70–0:75 | **Wrap-up + preview of Session 2.** | "Next time: how do we measure performance for classification?" |
| 0:75–0:80 | **Quiz (end-of-session).** 8–10 min. See `quiz_S1.md`. |

### Hook: "How Do We Know If a Model Is Actually Good?" (8 min)

**Goal:** Motivate evaluation by connecting to Week 3's overfitting problem.

**Instructions:**

1. Remind students: "Last week, we saw the U-shaped curve. Training error always goes down with complexity, but test error goes up after the sweet spot. We tuned $\lambda$ to find that sweet spot. But I asked you to trust me — how did we actually *measure* the validation error? How did we split the data?"

2. Ask: "If I train a model on 100 data points and it gets 0% error, is it a good model?" → Students (hopefully): "No, it could be overfitting!"

3. "Right. So how do we know? We need data the model hasn't seen. Today we answer: how do we split the data, and how do we use each part?"

4. **The punchline:** "This week requires no calculus at all — just counting and ratios. But it's the foundation of all ML practice. You cannot tune $\lambda$, choose polynomial degree, or compare models without proper evaluation."

**Common student responses to watch for:**
- "Just split into train and test." → Good intuition, but incomplete. We need THREE sets. This is the key teaching moment.
- "Use cross-validation." → If a student says this, acknowledge it: "Yes! We'll get there. But first, let's understand why a simple split isn't enough."

### Board Work: The Three Sets (15 min)

**This is the most important part of Session 1.** Students must leave with the train/val/test distinction crystal clear.

**Draw on the board (keep it visible for the rest of the session):**

```
  All available data
  ┌──────────────────────────────────────────────────┐
  │████████████████████████████│████████████│████████│
  │  Training set (60%)        │ Validation │  Test  │
  │  Fit model parameters      │ Tune hyper │  Final │
  │  (w, b)                    │ parameters │  eval  │
  │                            │ (degree,λ) │ (ONCE) │
  └──────────────────────────────────────────────────┘
                               (20%)       (20%)
```

**Key teaching moves:**

1. Write the table: Set | Purpose | When | How often. Fill it in WITH students — ask them to guess before revealing.

2. Emphasize the "How often" column. Training: many times. Validation: several times. Test: **exactly once**. Circle "ONCE" on the board.

3. Ask: "Why can't we just use two sets — train and test? Use the test set for both tuning and final evaluation?" → Because you'd be choosing the model that got lucky on the test set. The test set would become a second validation set.

4. State the Golden Rule clearly and prominently: **"Never touch the test data during model development."** Write it in a box.

5. Connect to Week 3: "Last week, we tuned $\lambda$. Which set did we use?" → Validation. "How did we evaluate the final model?" → We didn't, yet — that's what the test set is for.

**Common misconceptions to address proactively:**
- **"Validation set = test set."** → No. Validation is for tuning (used multiple times); test is for final evaluation (used once). This is THE most common confusion.
- **"The test set should be used to pick the best model."** → No. The test set is used to *estimate* performance of the model you already chose. If you use it to pick, it's no longer a test set.
- **"Bigger test set is always better."** → Not necessarily. A larger test set means less training data. For large datasets, small test fractions (1%) are fine because 1% of 1 million is still 10,000 examples.

### Board Work: k-Fold Cross-Validation (15 min)

**This is the centerpiece of Session 1.** The visual diagram is essential.

**Draw the 5-fold diagram with colored markers:**

```
  5-Fold Cross-Validation:

  Fold 1: [VAL]  [TR]  [TR]  [TR]  [TR]  → Validation error₁
  Fold 2: [TR]  [VAL] [TR]  [TR]  [TR]  → Validation error₂
  Fold 3: [TR]  [TR]  [VAL] [TR]  [TR]  → Validation error₃
  Fold 4: [TR]  [TR]  [TR]  [VAL] [TR]  → Validation error₄
  Fold 5: [TR]  [TR]  [TR]  [TR]  [VAL] → Validation error₅

  CV error = (error₁ + error₂ + error₃ + error₄ + error₅) / 5
```

Use a different color for [VAL] in each fold row. This makes it visually obvious that each fold takes a turn as validation.

**Key teaching moves:**

1. Draw the diagram row by row. After each row, ask: "Which part is validation? Which is training?"

2. After all 5 rows: "How many times is each data point used for validation?" → Exactly once. "How many times for training?" → $k - 1 = 4$ times.

3. **Compute fold sizes with students:** "If we have 1000 examples and 5 folds, how many in each fold?" → 200 in validation, 800 in training. Do this calculation on the board.

4. "Why is this better than a single split?" → The estimate is less noisy. We average 5 errors instead of relying on one. Also, we get a standard deviation — a measure of stability.

5. "When would you use more folds? Fewer?" → More folds = better estimate but more computation. 5 or 10 is standard.

6. Connect to model selection: "To choose polynomial degree, run 5-fold CV for degree 1, 2, 3, ..., 10. Plot average CV error vs. degree. Pick the degree with lowest CV error." Draw the U-shaped CV error curve.

### Data Leakage (10 min)

**This section is practical and engaging.** Students enjoy finding "what went wrong."

**Present each leakage type as a mini-puzzle:**

1. "I normalize all my data (compute mean and std), THEN split into train/test. What's wrong?" → The training data "knows" about test statistics. The mean includes test data points. Fix: split FIRST, normalize using only training data.

2. "I have patient data. The same patient appears twice — once in training, once in test. What's wrong?" → The model can memorize the patient, not learn the disease pattern. Fix: split by patient, not by record.

3. "I train a stock prediction model on 2020–2023 data and test on 2019 data. What's wrong?" → Temporal leakage. The model trained on data that came AFTER the test period. In deployment, you can't see the future. Fix: always train on the past, test on the future.

4. "I pick the top 10 features using ALL my data, then split into train/test. What's wrong?" → Feature selection "saw" the test data. The selected features are partly chosen because they look good on test. Fix: select features using only training data.

**Key message:** "Always split FIRST. Do ALL preprocessing using ONLY training data. Apply the same transformations to validation/test."

### LOOCV (7 min)

**Keep this brief.** Students should understand it as a special case and know when to use it.

**Present the table comparing LOOCV to 5-fold:**

| Property | LOOCV | 5-fold CV |
|----------|-------|-----------|
| Number of folds | $n$ | 5 |
| Training set per fold | $n-1$ | $4n/5$ |
| Computational cost | $n$ model fits | 5 model fits |
| Bias | Low (trains on almost all data) | Slightly higher |
| Variance | Higher (folds are very similar) | Lower |
| Best for | Small datasets | Most cases |

**Key teaching moves:**

1. "LOOCV is $k = n$. Each fold is ONE data point. Train on $n-1$, test on 1. Repeat $n$ times."

2. "Why is the variance higher?" → The $n$ training sets are almost identical (they differ by just one point). So the $n$ validation errors are highly correlated. Averaging correlated quantities doesn't reduce variance much.

3. "When would you use LOOCV?" → Very small datasets ($n < 50$). For large datasets, $n$ model fits is too expensive.

4. Mention the closed-form formula for linear regression LOOCV (handout E11) — but only as a teaser: "For linear regression, there's a beautiful formula that computes LOOCV in one step — no need to actually run $n$ regressions. We'll see this in Week 8 when we do matrix linear regression."

### Discussion Prompts

Use these at the indicated times to keep students engaged:

1. **(After the three-set split):** "You're building a model to predict exam scores. You have 500 students' data. How would you split it? What would each set be used for?" — Tests whether they can apply the framework to a concrete case.

2. **(After data leakage):** "You're preprocessing data and discover that 5% of values are missing. You fill in the missing values with the mean of the column, computed on ALL data. Then you split into train/test. Is this data leakage? Why or why not?" — Yes! The mean includes test data. Fix: compute mean on training data only, fill in missing values in all sets using that training mean.

3. **(After k-fold):** "If 5-fold CV gives errors [0.12, 0.15, 0.11, 0.14, 0.13], what's the CV error? What's the standard deviation? What does the standard deviation tell you?" → CV error = 0.13, std ≈ 0.015. The low std means the model is stable across different data splits.

4. **(After overfitting to validation):** "If you try 1000 different models and pick the best on the validation set, is the validation error of the winner a reliable estimate of test error?" → No! With 1000 models, one will look good by chance. The validation error is optimistically biased. This is "overfitting to the validation set."

### Things NOT to Cover (Save for Later)

| Topic | When |
|-------|------|
| Nested cross-validation | Mention briefly; full treatment is advanced (not in main curriculum) |
| Stratified k-fold | Week 7 (logistic regression) when we deal with imbalanced classes |
| Time-series cross-validation | Week 20+ (sequence models) |
| Statistical properties of CV (formal bias-variance of CV) | Beyond course scope |
| Cross-entropy loss | Week 7 (logistic regression) |

**Resist the urge to go deep on nested CV.** Just mention it exists: "If you're doing very rigorous evaluation, there's a technique called nested CV. It's advanced — don't worry about it now."

---

## Session 2 (80 min): Classification Metrics, ROC/AUC, Regression Metrics, Learning Curves

### Learning Objectives

By the end of this session, students should be able to:
1. Construct a confusion matrix from predictions and compute accuracy, precision, recall, and F1.
2. Explain why accuracy is misleading with class imbalance, with a concrete example.
3. Describe the precision-recall tradeoff and how the classification threshold controls it.
4. Construct an ROC curve step-by-step and interpret AUC.
5. Choose the appropriate metric (accuracy, precision, recall, F1, AUC, MSE, MAE, R²) for a given problem.
6. Read a learning curve and diagnose overfitting vs. underfitting from it.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos open in browser (for the ROC curve construction — see `visual_demos.md`)
- Printed or projected handout Sections 4–7
- Colored markers (for the confusion matrix and ROC curve)
- Quiz S2 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** Quick: "What are the three sets? What's the Golden Rule?" |
| 0:05–0:10 | **Paper discussion (5 min).** First paper discussion! Davis & Goadrich. See `suggested_paper.md`. |
| 0:10–0:30 | **Confusion matrix + accuracy + precision + recall + F1.** Build the matrix with students. Worked example. |
| 0:30–0:40 | **Why accuracy fails with imbalance. The spam example.** |
| 0:40–0:55 | **ROC curve construction + AUC.** This is the hardest part. Use Desmos. Step by step. |
| 0:55–0:62 | **Precision-recall tradeoff + PR curves.** When to use PR vs ROC. |
| 0:62–0:70 | **Regression metrics recap + choosing the right metric.** Fast — MSE/RMSE/MAE/R² from Week 2. Focus on *choosing*. |
| 0:70–0:73 | **Learning curves.** Diagnose overfitting/underfitting from data size. Connect to Week 3. |
| 0:73–0:80 | **Quiz (end-of-session).** 10 min. See `quiz_S2.md`. |

> **Note:** This session is DENSE. If running short on time, compress the regression metrics recap (students already know MSE/R² from Week 2) and spend the saved time on ROC curve construction. The ROC curve is the hardest concept and deserves the most time.

### Board Work: Confusion Matrix Construction (15 min)

**This is the most important part of Session 2.** Students must be able to build and interpret the confusion matrix.

**Build the matrix LIVE with students:**

**Step 1: Set up the scenario.**

"Imagine a spam filter. We have 1000 emails: 100 are spam, 900 are not spam. Our model predicts spam/not spam. Let's see how it does."

**Step 2: Draw the empty matrix on the board.**

```
                    Predicted Spam    Predicted Not Spam
                    ──────────────    ──────────────────
Actual Spam         ?                 ?
Actual Not Spam     ?                 ?
```

**Step 3: Fill in the numbers, asking students at each step.**

- "The model correctly identifies 80 spam emails. Where does this go?" → Actual Spam, Predicted Spam = **TP = 80**.
- "20 spam emails get through — the model says 'not spam.' Where?" → Actual Spam, Predicted Not Spam = **FN = 20**.
- "10 good emails get flagged as spam. Where?" → Actual Not Spam, Predicted Spam = **FP = 10**.
- "890 good emails are correctly left alone. Where?" → Actual Not Spam, Predicted Not Spam = **TN = 890**.

**Step 4: Label the cells with their names.**

```
                    Predicted Spam    Predicted Not Spam
                    ──────────────    ──────────────────
Actual Spam         TP = 80           FN = 20
Actual Not Spam     FP = 10           TN = 890
```

**Step 5: Compute each metric, asking students for the formula first.**

- **Accuracy:** $(80 + 890) / 1000 = 970 / 1000 = 97\%$
- **Precision:** $80 / (80 + 10) = 80/90 = 88.9\%$
- **Recall:** $80 / (80 + 20) = 80/100 = 80\%$
- **F1:** $2 \cdot (0.889 \cdot 0.80) / (0.889 + 0.80) = 0.842 = 84.2\%$

**Key teaching moves:**

1. Write the formulas NEXT to the matrix, not separately. Draw arrows:
   - Precision: TP / (TP + FP) → "all predicted positive" (the column)
   - Recall: TP / (TP + FN) → "all actual positive" (the row)

2. **Intuition check:** "Precision asks: when the model says spam, how often is it right? Recall asks: of all the spam, how much did we catch?"

3. **The spam example is deliberate:** 97% accuracy sounds great, but recall is only 80% — the model misses 1 in 5 spam emails. This sets up the "accuracy is misleading" discussion.

4. **Harmonic mean intuition:** "Why not just use the arithmetic mean of precision and recall? If precision = 0.01 and recall = 1.0 (predict everything as positive), the arithmetic mean is 0.505 — looks OK. But the harmonic mean is 0.02 — correctly terrible. The harmonic mean punishes you if either value is low."

### Board Work: Why Accuracy Fails with Imbalance (8 min)

**This is the "aha" moment of Session 2.**

**Present the baseline comparison:**

"Without any model, just predict 'not spam' for EVERYTHING."

| | Predicted Spam | Predicted Not Spam |
|---|---|---|
| **Actual Spam** | 0 | 100 |
| **Actual Not Spam** | 0 | 900 |

- Accuracy: $900 / 1000 = 90\%$
- Precision: $0/0$ — undefined (no positive predictions)
- Recall: $0 / 100 = 0\%$
- F1: 0

**The punchline:** "The baseline gets 90% accuracy by doing NOTHING. Our model gets 97%. That seems like 7% improvement. But the baseline catches 0% of spam. Our model catches 80%. Precision, recall, and F1 tell the real story."

**Then present the extreme case:** "A disease affects 0.1% of people. A model that predicts 'healthy' for everyone gets 99.9% accuracy. Is it a good model? NO — it misses every single case. Accuracy is useless here."

**Write on the board (keep visible):**

> **Accuracy is misleading when classes are imbalanced. Use precision, recall, F1, or AUC instead.**

### Board Work: ROC Curve Construction (15 min)

**This is the hardest concept in Week 4.** Go slowly. Use the handout's worked example (Section 5.5).

**Step 1: Present the data (2 min)**

Write the 8-example table on the board:

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

"There are 4 spam and 4 not-spam. The model outputs a probability for each."

**Step 2: Explain the threshold (3 min)**

"The model doesn't just say 'spam' or 'not spam.' It outputs a probability. We choose a threshold $t$: if $P(\text{spam}) > t$, predict spam. Otherwise, predict not spam."

- "If $t = 1.0$: predict nothing as spam. TP = 0, FP = 0. TPR = 0, FPR = 0. This is the bottom-left corner."
- "If $t = 0.0$: predict everything as spam. TP = 4, FP = 4. TPR = 1, FPR = 1. This is the top-right corner."
- "As we lower $t$ from 1.0 to 0.0, we sweep through intermediate points."

**Step 3: Sweep the threshold (5 min)**

Go through each threshold, filling in the table on the board:

| Threshold | TP | FP | FN | TN | TPR | FPR |
|-----------|----|----|----|----|-----|-----|
| >0.95 | 0 | 0 | 4 | 4 | 0 | 0 |
| 0.90 | 1 | 0 | 3 | 4 | 0.25 | 0 |
| 0.85 | 2 | 1 | 2 | 3 | 0.50 | 0.25 |
| 0.50 | 3 | 2 | 1 | 2 | 0.75 | 0.50 |
| 0.20 | 4 | 3 | 0 | 1 | 1.0 | 0.75 |
| 0.10 | 4 | 4 | 0 | 0 | 1.0 | 1.0 |

For each row, ask: "If threshold is 0.85, which examples are predicted spam?" → Examples 1, 2, 3 (probability ≥ 0.85). Example 1 is spam (TP), Example 2 is spam (TP), Example 3 is not spam (FP). So TP = 2, FP = 1.

**Step 4: Plot the points (3 min)**

Switch to Desmos (or draw on board). Plot $(FPR, TPR)$:

$(0, 0) \to (0, 0.25) \to (0.25, 0.50) \to (0.50, 0.75) \to (0.75, 1.0) \to (1.0, 1.0)$

Connect the points. The curve goes up and to the right.

**Step 5: Interpret (2 min)**

- "The diagonal line from $(0,0)$ to $(1,1)$ is random guessing."
- "A curve hugging the top-left corner is a great classifier — high TPR, low FPR."
- "AUC is the area under this curve. 1.0 = perfect, 0.5 = random."
- **The beautiful interpretation:** "AUC = the probability that the model ranks a random positive example higher than a random negative example." Write this prominently.

### Precision-Recall Tradeoff (7 min)

**Connect to the threshold discussion.**

1. "When we raise the threshold, we predict positive less often. Precision goes UP (we only say positive when very confident), but recall goes DOWN (we miss more positives)."

2. Draw the PR tradeoff curve (precision on y-axis, recall on x-axis). As threshold decreases, we move right and down along the curve.

3. **Use cases:**
   - **Cancer screening (low threshold):** Don't miss any cases. Accept false alarms. Recall is priority.
   - **Spam filter (high threshold):** Don't flag good emails. Accept missing some spam. Precision is priority.

4. **PR curve vs ROC:** "When the positive class is rare (e.g., 0.1% fraud), use the PR curve. ROC can look misleadingly good because the FPR is dominated by the huge number of true negatives."

### Regression Metrics Recap + Choosing the Right Metric (5 min)

**This should be FAST.** Students learned MSE and R² in Week 2.

1. **Quick recap table** (from handout Section 6.1): MSE, RMSE, MAE, R². Don't re-derive — just remind.

2. **MSE vs MAE:** "MSE squares errors, so outliers dominate. MAE treats errors linearly. Choose MSE when large errors are especially bad (house prices). Choose MAE when outliers are common and shouldn't dominate (stock returns)."

3. **Choosing the right metric — scenarios:** Present 3-4 scenarios and ask students which metric to use:
   - "Medical diagnosis: which metric?" → Recall (don't miss disease)
   - "Spam filtering: which metric?" → Precision (don't flag good email)
   - "House price prediction: which metric?" → RMSE (interpretable, large errors matter)
   - "Imbalanced classification: which metric?" → F1 or AUC (accuracy is misleading)

### Learning Curves (3 min)

**Keep this brief** — it's the last topic before the quiz.

1. "A learning curve plots training error and validation error vs. TRAINING SET SIZE (not complexity)."

2. Draw the standard picture: training error increases (harder to fit more data), validation error decreases (more data = better generalization). They converge.

3. **Diagnosis table** (from handout Section 7.2): Both high + small gap = underfitting. Low train + high val + large gap = overfitting. Both low + small gap = good fit.

4. **Key insight:** "If the curves haven't converged (large gap), adding more data will help. If they've converged but both are high, adding data WON'T help — you need a more complex model."

5. **Connect to Week 3:** "Last week's complexity curve: fixed data, vary complexity. This week's learning curve: fixed model, vary data. They're complementary tools."

### Anticipated Questions from Students

| Question | How to Answer |
|----------|--------------|
| "Why can't I use the test set multiple times? It's my data." | Each time you look at test results and make a decision, you're leaking information. The test set becomes a second validation set. The more you use it, the more optimistically biased your estimate becomes. (1 min.) |
| "What's a good value for AUC?" | 0.5 = random, 0.7 = okay, 0.8 = good, 0.9 = excellent, 1.0 = perfect. Below 0.5 means your model is worse than random — flip your predictions! (30 sec.) |
| "Why harmonic mean for F1? Why not geometric mean?" | The harmonic mean punishes extreme imbalances more severely. If precision = 0 and recall = 1, harmonic mean = 0 (correct — the model is terrible). Geometric mean would also give 0, but for less extreme cases (precision = 0.1, recall = 1), harmonic mean = 0.18 while geometric mean = 0.32 — the harmonic mean is more punishing, which is what we want. (1 min. Don't go deeper unless asked.) |
| "What if precision and recall are both 0?" | F1 is undefined (0/0). This means the model makes no positive predictions OR gets all positive predictions wrong. Either way, it's useless for the positive class. (30 sec.) |
| "Is a higher k always better for CV?" | Not necessarily. Higher k = lower bias (trains on more data per fold) but higher variance (folds are more correlated) and more computation. 5 or 10 is the sweet spot for most problems. LOOCV ($k = n$) is only for very small datasets. (1 min.) |
| "Can I normalize data before splitting?" | NO! This is data leakage. Always split first, then normalize using only training data statistics. (30 sec. This is a quiz question — make sure everyone hears this.) |
| "What's the difference between RMSE and standard deviation?" | Good question! SD measures spread of the data around its mean. RMSE measures spread of predictions around the true values. If the model predicts the mean, RMSE = SD. R² = 1 - RMSE²/SD². (1 min. Don't derive unless asked.) |
| A sharp student asks about AUC and imbalanced data | "Great question. AUC can be misleading with highly imbalanced data because FPR is dominated by the huge number of true negatives. That's why PR curves are preferred for imbalanced datasets. The Davis & Goadrich paper we're reading this week discusses exactly this." (1 min.) |

### Differentiation Notes

**For struggling students:**
- The confusion matrix is the biggest barrier. After class, offer to go over TP/FP/FN/TN one more time. Give them the mnemonic: "True/False = did we get it right? Positive/Negative = what did we predict?"
- Focus them on the *formulas* (accuracy, precision, recall) rather than the *ROC curve construction*. The ROC curve is the hardest concept and can wait.
- Reassure them: "The confusion matrix and precision/recall will come up every week. You'll get lots of practice."

**For advanced students:**
- They may find the confusion matrix trivial. Redirect them to the ★ exercises (E9–E12) in the handout.
- Direct them to the AUC = P(score(+) > score(−)) proof (handout E9). This is a beautiful result that requires careful thinking.
- In class, when asking questions, direct basic precision/recall questions to struggling students and the ROC/AUC interpretation questions to advanced students. Example: "Compute precision from this matrix" (anyone) → "Why does the ROC curve go up when we lower the threshold?" (advanced).
- Mention: "If you already know F1, look at Fβ in the exercises. It generalizes F1 to weight precision vs. recall differently. Think about what β = 2 means."

---

## Challenge Questions for Advanced Students

> **How to use these:** Give these to sharp students *during* class when they finish an activity early, or as "think about this while I explain the basics to others" prompts. They are NOT extra homework — they are conversation starters. Follow up with these students individually or in a small group during breaks or after class. The goal is to keep them intellectually hungry without derailing the class pace.
>
> **Delivery:** Write the question on a sticky note, slip it to the student, or display it on a side board. Say: "While we review [topic], think about this. Let's discuss after class or during the break."
>
> **Principle:** Every challenge is tied to a Week 4 concept but pushes *deeper* — either toward a topic we'll cover later (creating anticipation) or toward a subtlety that most students won't notice (building analytical thinking).

---

### Session 1 Challenges

**Challenge 4-1A: The Nested Cross-Validation Question**
*(Give after k-fold CV — around minute 55)*

> We use cross-validation to choose the best model (e.g., best polynomial degree). But what if we also have a hyperparameter of the cross-validation procedure itself — like the number of folds $k$? If we try $k = 3, 5, 10$ and pick the $k$ that gives the lowest CV error, is this legitimate? What goes wrong?
>
> **Question:** How would you design a validation scheme that avoids bias when you're tuning BOTH the model AND the cross-validation procedure? (Hint: think about using cross-validation *inside* cross-validation.)

**Instructor notes (don't share with student yet):**
- This is **nested cross-validation**. The outer loop splits data into train/test folds. For each outer training fold, you run an inner cross-validation to choose the model. Then you evaluate on the outer test fold.
- The key insight: any choice made using the data (including the choice of $k$) introduces optimistic bias if evaluated on the same data. You need a "higher level" holdout to evaluate the choice.
- **Follow-up if the student figures it out:** "This is computationally expensive. When would the extra rigor be worth it?" → Medical applications, safety-critical systems, small datasets where every decision matters. For large datasets, a simple train/val/test split is usually sufficient because the variance is low.

---

**Challenge 4-1B: The Bootstrap vs. Cross-Validation**
*(Give after LOOCV — around minute 60)*

> In cross-validation, we split the data into folds. But there's another resampling method called the **bootstrap**: draw $n$ samples from your data *with replacement* (so some examples appear multiple times, others not at all). On average, about 63.2% of examples appear in the bootstrap sample; the remaining 36.8% are "out of bag" (OOB).
>
> **Question:** Could you use the bootstrap for model validation instead of cross-validation? What are the advantages and disadvantages? In particular, think about: (a) How many times is each example used for training? For validation? (b) Is the bootstrap estimate higher or lower variance than k-fold CV?

**Instructor notes:**
- Yes, the bootstrap can be used for validation. The OOB examples serve as the validation set.
- (a) Each example is in the bootstrap sample ~63.2% of the time (training) and OOB ~36.8% of the time (validation). This is different from k-fold CV, where each example is in training exactly $k-1$ out of $k$ times.
- (b) The bootstrap estimate typically has higher variance than k-fold CV because the training sets overlap heavily (like LOOCV). But it's useful when you also want confidence intervals (you can get them from the bootstrap distribution).
- **Follow-up:** "Breiman used the bootstrap in random forests for OOB estimation. We'll see this if we cover random forests later. The bootstrap is also the foundation of many statistical methods we'll encounter." (Connects to the Week 4 suggested paper if using the Breiman alternative, or to future ensemble methods.)

---

**Challenge 4-1C: The "Adversarial" Validation Set**
*(Give after overfitting to validation — around minute 65)*

> We said that trying many models and picking the best on the validation set causes "overfitting to the validation set." But how many is "too many"? If I try 5 models, is that OK? What about 50? 1000?
>
> **Question:** Can you think of a way to *quantify* the risk of overfitting to the validation set? If the validation set has $m$ examples and I try $M$ models, under what conditions is the validation winner likely to generalize well? (Hint: think about what "luck" means in terms of probability. If each model's validation error is an independent random estimate, how much can the best of $M$ models beat its true error by?)

**Instructor notes:**
- This is the **multiple comparisons problem**. If each model's validation error is an unbiased estimate with some variance $\sigma^2/m$, then the minimum of $M$ such estimates is biased downward. The more models you try, the more biased the winner's error becomes.
- Roughly, the bias grows like $\sigma \sqrt{2 \log(M)/m}$ (from extreme value theory — don't derive this, just mention the intuition).
- **Follow-up:** "This is why the test set is essential. Even if you overfit to the validation set by trying 1000 models, the test set — used ONCE — gives you an honest estimate. The test set is your 'reality check.'" Connects to the Bonferroni correction and multiple testing in statistics.

---

**Challenge 4-1D: Stratified Sampling**
*(Give after data leakage — around minute 35)*

> When we split data into train/validation/test, we usually shuffle randomly. But consider this: you have a dataset with 90% cats and 10% dogs. You do a random 80/20 split. It's possible (though unlikely) that the test set ends up with 0 dogs.
>
> **Question:** How would you design a splitting strategy that guarantees the class proportions are preserved in each split? What are the advantages? Can you think of a case where this strategy would be tricky to implement?

**Instructor notes:**
- This is **stratified sampling** (or stratified k-fold for CV). Instead of random splitting, split within each class separately so that each fold has the same proportion of each class.
- Advantages: ensures the validation/test estimates are representative, especially with imbalanced classes.
- Tricky cases: multi-label classification (an example can belong to multiple classes), regression (there are no "classes" to stratify on — you can stratify on binned values of $y$), very small datasets with rare classes (some folds might have 0 examples of a rare class).
- **Follow-up:** "We'll use stratified k-fold when we cover logistic regression (Week 7) and decision trees. Most ML libraries do this by default for classification. Always check!"

---

**Challenge 4-1E: Time-Series Splitting**
*(Give after data leakage — around minute 35)*

> We said that for time-series data, you should train on the past and test on the future. But what about cross-validation? Standard k-fold CV shuffles the data, which breaks temporal order.
>
> **Question:** Design a cross-validation scheme for time-series data that respects temporal order. How would the folds look? What are the tradeoffs compared to standard k-fold?

**Instructor notes:**
- This is **time-series cross-validation** (or "rolling origin" CV). The folds are:
  - Fold 1: Train on [1..t], validate on [t+1..t+k]
  - Fold 2: Train on [1..t+k], validate on [t+k+1..t+2k]
  - ...and so on, expanding the training window.
- Alternatively, use a sliding window: train on [t..t+w], validate on [t+w..t+w+k], then slide forward.
- Tradeoffs: earlier folds have less training data (higher bias). The validation sets are not independent (they overlap temporally). But this is the ONLY valid approach for time-series — standard k-fold would leak future information into training.
- **Follow-up:** "This is essential for stock prediction, weather forecasting, and any problem where time matters. We'll see this again in Week 20+ when we cover sequence models."

---

### Session 2 Challenges

**Challenge 4-2A: The AUC Probability Interpretation**
*(Give after ROC/AUC — around minute 55)*

> We stated that $\text{AUC} = P(\text{score(positive)} > \text{score(negative)})$ — the probability that a randomly chosen positive example gets a higher score than a randomly chosen negative example. This is a beautiful result.
>
> **Question:** Can you prove this? Here's the hint from the handout: think about what happens as you sweep the threshold. Each point on the ROC curve corresponds to a threshold. The area under the curve can be computed as a sum over all pairs of (positive, negative) examples.
>
> *This is handout exercise E9. Give it to students who want a real mathematical challenge.*

**Instructor notes:**
- The proof sketch: Consider all pairs $(i, j)$ where $i$ is a positive example and $j$ is a negative example. There are $n_+ \cdot n_-$ such pairs.
- As the threshold sweeps from high to low, each time we pass a positive example's score, TPR increases by $1/n_+$. Each time we pass a negative example's score, FPR increases by $1/n_-$.
- The AUC is the sum of rectangular areas under the ROC curve. Each rectangle corresponds to a threshold value. The area contributed when we pass a positive example at score $s$ is proportional to the fraction of negatives with score $< s$.
- Summing over all positives: $\text{AUC} = \frac{1}{n_+ n_-} \sum_{i \in \text{pos}} \sum_{j \in \text{neg}} \mathbb{1}[s_i > s_j] = P(s_+ > s_-)$.
- **Follow-up:** "This interpretation is why AUC is so popular — it measures *ranking ability*, not just classification at a single threshold. A model with AUC = 0.9 ranks 90% of positive-negative pairs correctly."

---

**Challenge 4-2B: The Fβ-Score**
*(Give after F1 — around minute 25)*

> The F1-score treats precision and recall equally. But what if false negatives are 5 times worse than false positives (like in cancer screening)?
>
> The **Fβ-score** generalizes F1:
> $$F_\beta = (1 + \beta^2) \cdot \frac{\text{Precision} \cdot \text{Recall}}{\beta^2 \cdot \text{Precision} + \text{Recall}}$$
>
> **Question:** (a) What does $\beta = 2$ emphasize — precision or recall? What about $\beta = 0.5$? (b) Show that $F_1$ (when $\beta = 1$) is the harmonic mean of precision and recall. (c) What happens to $F_\beta$ as $\beta \to \infty$? As $\beta \to 0$? Explain why these limits make sense.
>
> *This is handout exercise E10.*

**Instructor notes:**
- (a) $\beta = 2$ emphasizes recall (it weighs recall more heavily, because the $\beta^2$ factor multiplies precision in the denominator, making the score more sensitive to low recall). $\beta = 0.5$ emphasizes precision.
- (b) Setting $\beta = 1$: $F_1 = 2 \cdot \frac{P \cdot R}{P + R}$, which is the harmonic mean.
- (c) As $\beta \to \infty$: $F_\beta \to \text{Recall}$ (precision becomes irrelevant — we only care about recall). As $\beta \to 0$: $F_\beta \to \text{Precision}$ (recall becomes irrelevant). This makes sense: $\beta \to \infty$ means "false negatives are infinitely bad" → only care about recall.
- **Follow-up:** "The Fβ-score is used in information retrieval and medical applications. In practice, people often just look at precision and recall separately rather than combining them — but Fβ gives you a single number for optimization."

---

**Challenge 4-2C: Why ROC Can Be Misleading with Imbalanced Data**
*(Give after PR curves — around minute 60)*

> We said that PR curves are more informative than ROC when classes are imbalanced. But WHY? ROC plots TPR vs. FPR, which seem like they shouldn't depend on class balance.
>
> **Question:** Consider a dataset with 100 positives and 9900 negatives. A model has TP = 80, FP = 100, FN = 20, TN = 9800. Compute TPR, FPR, precision, and recall. Now suppose we add 90,000 more negative examples (all correctly classified: TN becomes 99,800). Recompute TPR, FPR, precision, and recall. What changed? What didn't? Why does this matter?

**Instructor notes:**
- Original: TPR = 80/100 = 0.80, FPR = 100/9900 ≈ 0.0101, Precision = 80/180 ≈ 0.44, Recall = 0.80.
- After adding negatives: TPR = 0.80 (unchanged), FPR = 100/99900 ≈ 0.001 (much smaller!), Precision = 80/180 ≈ 0.44 (unchanged), Recall = 0.80 (unchanged).
- The FPR dropped dramatically because the denominator (FP + TN) is dominated by the huge number of negatives. The ROC curve looks BETTER even though the model didn't improve — it just has more negatives to be correctly classified.
- But precision and recall are UNCHANGED — they only depend on the positive class. This is why PR curves are more stable and informative for imbalanced data.
- **Follow-up:** "This is exactly the argument made in the Davis & Goadrich paper we're reading this week. They show that a curve can dominate in ROC space but not in PR space. This is a subtle and important result."

---

**Challenge 4-2D: The Cost-Sensitive Threshold**
*(Give after precision-recall tradeoff — around minute 58)*

> We choose the classification threshold to trade off precision vs. recall. But in practice, different errors have different *costs*. In cancer screening, a false negative (missed cancer) costs 100× more than a false positive (extra tests).
>
> **Question:** If a false positive costs $c_{FP}$ and a false negative costs $c_{FN}$, what threshold should you use? Can you express the optimal threshold in terms of $c_{FP}$ and $c_{FN}$? (Hint: the model outputs $P(y=1|x)$. You want to minimize expected cost.)
>
> *This connects to Challenge 2-D from Week 1.*

**Instructor notes:**
- The optimal threshold is $t^* = \frac{c_{FP}}{c_{FP} + c_{FN}}$.
- Intuition: if $c_{FN} \gg c_{FP}$ (false negatives are much worse), then $t^*$ is close to 0 — predict positive easily (accept false positives to avoid false negatives). If $c_{FP} \gg c_{FN}$, then $t^*$ is close to 1 — be very sure before predicting positive.
- Derivation (brief): predict positive when expected cost of predicting positive < expected cost of predicting negative. $c_{FP} \cdot P(y=0|x) < c_{FN} \cdot P(y=1|x)$. Rearranging: $P(y=1|x) > \frac{c_{FP}}{c_{FP} + c_{FN}}$.
- **Follow-up:** "This is why we said medical diagnosis → low threshold (recall), spam filtering → high threshold (precision). The costs drive the threshold. We'll formalize this with probability in Week 5 and logistic regression in Week 7."

---

**Challenge 4-2E: Learning Curves and the Bias-Variance Decomposition**
*(Give after learning curves — around minute 72)*

> We can diagnose overfitting and underfitting from learning curves. Last week (Week 3), we discussed the bias-variance tradeoff qualitatively.
>
> **Question:** On a learning curve (training error and validation error vs. training size), where is the "bias" and where is the "variance"? Specifically: (a) When the gap between training and validation error is large, is that high bias or high variance? (b) When both errors are high and converged, is that high bias or high variance? (c) As training size $\to \infty$, what happens to the gap? What does this tell you about whether variance can be eliminated with enough data?

**Instructor notes:**
- (a) Large gap = high variance (the model fits training data well but doesn't generalize — it's sensitive to the specific training sample). This is overfitting.
- (b) Both high and converged = high bias (the model can't capture the pattern even with lots of data). This is underfitting. The variance is low (the gap is small), but the bias is high.
- (c) As $n \to \infty$, the gap → 0 (training and validation error converge). This means variance → 0 with enough data. But if the converged error is still high, that's irreducible bias (the model is too simple). You can reduce variance with more data, but you CANNOT reduce bias with more data — you need a more complex model.
- **Follow-up:** "This is the formal bias-variance decomposition. We'll derive it mathematically in Week 5 after we learn probability. For now, the learning curve gives you the qualitative picture: gap = variance, converged level = bias + irreducible error."

---

### Ongoing Challenges (Cross-Week)

These are longer-form questions that advanced students can think about throughout the week. Mention them at the end of Session 2 and discuss during office hours or the start of Week 5.

**Ongoing 1: The "No Free Lunch" for Metrics**

> We've seen many metrics: accuracy, precision, recall, F1, AUC, MSE, RMSE, MAE, R². Each is "best" for some problems. Is there a metric that's always good? Or does the choice of metric depend on the problem, just like the choice of model?
>
> Can you state a "No Free Lunch theorem for metrics"? Is there a sense in which no single metric can capture everything we care about?

**Instructor notes:** This is a deep question. The answer is yes — there's no universal metric. Every metric encodes a value judgment about what kinds of errors matter. Accuracy says all errors are equal. F1 says false positives and false negatives are equally bad. Fβ says they're differently bad. MSE says large errors are disproportionately bad. The choice of metric IS a modeling decision, just like the choice of hypothesis space. This connects to the Domingos paper (Week 2, Section 1: "Evaluation" = the metric). Seeds discussions of fairness, multi-objective optimization, and the alignment problem.

---

**Ongoing 2: The "Evaluation Cascade"**

> In this course, we'll learn many models: linear regression, k-NN, decision trees, SVMs, neural networks. Each has hyperparameters (degree, $k$, depth, $C$, learning rate). For each, we need to do cross-validation. But what if we want to compare ALL of these models?
>
> If we run 5-fold CV for each of 10 models, that's 50 model fits. Is this legitimate? What if we have 100 candidate models? At what point does the "best" model just reflect noise? How would you handle this in practice?

**Instructor notes:** This connects to Challenge 4-1C (overfitting to the validation set) and the multiple comparisons problem. In practice, ML practitioners do try many models, and the validation winner is somewhat optimistically biased. The test set is the final check. In rigorous settings (especially with small data), nested CV is needed. In Kaggle-style competitions, the leaderboard acts as a "test set" — and the public leaderboard overfitting is a well-known phenomenon. Seeds discussion of the difference between research and practice.

---

**Ongoing 3: The "Metric Gaming" Question**

> Metrics are used not just to evaluate models, but to decide which model to deploy — and sometimes, to evaluate people. A doctor whose performance is measured by "number of patients seen per hour" might rush through appointments. A police department measured by "arrest rate" might make unnecessary arrests.
>
> **Question:** Can you think of how a ML metric could be "gamed" — where a model optimizes the metric but makes the underlying problem worse? What does this say about the importance of choosing the RIGHT metric? How is this related to the alignment problem in AI?

**Instructor notes:** This is a crucial question about AI ethics and alignment. Examples: A spam filter measured by precision might just predict "not spam" for everything (precision is undefined or trivially high). A recidivism model measured by accuracy might be racist (if the data is biased). A content recommendation system measured by "engagement" might promote inflammatory content. The lesson: the metric you optimize determines the behavior you get. If the metric is wrong, the model will be "correct but harmful." This connects to Goodhart's Law: "When a measure becomes a target, it ceases to be a good measure." Seeds Weeks 38+ (AI ethics and alignment).

---

### Managing Advanced Students: Practical Tips

| Situation | Strategy |
|-----------|----------|
| Student finishes confusion matrix exercise early | Hand them Challenge 4-2B (Fβ-score). Say: "F1 treats precision and recall equally. Can you generalize it?" |
| Student answers ROC questions instantly | Give them Challenge 4-2A (prove AUC = P(+) > P(−)). This is a genuine mathematical challenge. |
| Student seems bored during regression metrics recap | Give them Ongoing Challenge 1 (No Free Lunch for metrics). It's philosophical and open-ended. |
| Student asks about multi-class classification | "Great question! We've only done binary. For multi-class, the confusion matrix gets bigger, and you can compute precision/recall per class. We'll see this with logistic regression (Week 7) and neural networks (Week 14+)." Don't derive now. |
| Multiple advanced students interested in the paper | Form a "paper club" during the break. Ask them to discuss: "Davis & Goadrich claim PR curves are better than ROC for imbalanced data. Can you construct an example that shows this?" (This is Challenge 4-2C.) |
| Student already knows all the metrics | Push toward the *philosophy* of metrics. "If you could only use ONE metric for the rest of your career, which would you choose and why?" There's no right answer — it forces them to think about tradeoffs. |

---

## Post-Session Checklist

After each session, the instructor should:

- [ ] Review quiz results and note common mistakes
- [ ] Update the student progress tracker
- [ ] Prepare spiral-back questions for the next quiz
- [ ] Check if any student needs intervention (⚠ or ✗ on the tracker)
- [ ] Preview next session's material and adjust if needed
- [ ] Note which challenge questions were given out and to whom

---

## Preparation Checklist for Week 4

### Before Session 1

- [ ] Read handout Sections 1–3
- [ ] Prepare the data split diagram for board work
- [ ] Prepare the 5-fold CV diagram (use colored markers)
- [ ] Prepare the data leakage examples (4 scenarios)
- [ ] Print quiz S1 (or have it ready to project)
- [ ] Print handout for students (or distribute digitally)
- [ ] Review Week 3 material — be ready to connect $\lambda$ tuning to validation sets

### Before Session 2

- [ ] Read handout Sections 4–7
- [ ] Prepare the confusion matrix example (spam filter, 1000 emails)
- [ ] Set up Desmos with the ROC curve data (8 examples from handout Section 5.5)
- [ ] Prepare the "accuracy fails" comparison (model vs. baseline)
- [ ] Prepare the learning curve diagrams (4 patterns: underfit, overfit, good, both-high)
- [ ] Print quiz S2
- [ ] Review Session 1 quiz results — prepare to address common mistakes at the start of Session 2
- [ ] Read the suggested paper (Davis & Goadrich) — prepare the 5-minute discussion
- [ ] Have the "How to Read a Research Paper" guide ready to distribute (from `suggested_paper.md`)
