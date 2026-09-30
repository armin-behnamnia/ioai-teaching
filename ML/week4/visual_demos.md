# Week 4 — Visual Demos

> **Purpose:** Interactive visual demonstrations to use in class. Each demo includes the setup, what to show, and key teaching points. These are designed to make abstract concepts visceral.

---

## Demo 1: Train / Validation / Test Split Diagram

**Tool:** Whiteboard drawing (no software needed)  
**Used in:** Session 1, minutes 8–25  
**Prep time:** None

### Setup

Draw a large rectangle on the board representing "all available data." Divide it into three sections with vertical lines.

### What to Draw

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

Use different colors for each section if possible. Label each section with:
- **Purpose** (what you do with it)
- **When used** (how often)
- **What lives there** (parameters vs. hyperparameters vs. nothing)

### What to Show

**Part A: The Split (3 min)**

1. Draw the rectangle and the three sections.
2. Label each section. Ask students to guess the percentages before revealing (60/20/20 or 70/15/15).
3. Write the table:

| Set | Purpose | When used | How often |
|-----|---------|-----------|-----------|
| Training | Fit parameters (w, b) | Every training step | Many times |
| Validation | Tune hyperparameters (degree, λ) | Model selection | Several times |
| Test | Final evaluation | At the very end | Exactly once |

4. Circle "Exactly once" for the test set. This is the Golden Rule.

**Part B: Why Three Sets? (3 min)**

1. Ask: "Why not just two — train and test?"
2. Explain: "If you use the test set for tuning, you're choosing the model that got lucky on the test set. It becomes a second validation set. You have no honest evaluation left."
3. Draw a red X over the test set: "This is LOCKED. You don't touch it until the very end."

**Part C: Scaling (2 min)**

1. "For 100 data points: 60 train, 20 val, 20 test."
2. "For 1,000,000 data points: 980,000 train, 10,000 val, 10,000 test. That's 98/1/1."
3. "For large datasets, small test fractions are fine — 10,000 examples is plenty for a reliable estimate."

### Teaching Points

- **The Golden Rule:** Never touch the test data during model development. Write this in a box.
- **Three purposes:** Training = learn parameters. Validation = choose hyperparameters. Test = honest evaluation.
- **Connect to Week 3:** "Last week, we tuned $\lambda$. Which set did we use?" → Validation. "We never used the test set — and we still shouldn't until we're done."

---

## Demo 2: k-Fold Cross-Validation Visual (5-Fold with Colored Blocks)

**Tool:** Whiteboard with colored markers (or projected slide)  
**Used in:** Session 1, minutes 35–55  
**Prep time:** 2 minutes (gather 5 colored markers)

### Setup

Draw a grid: 5 rows (one per fold) × 5 columns (one per data block). Use a different color for the [VAL] block in each row.

### What to Draw

```
  5-Fold Cross-Validation:

  Fold 1: [VAL]  [TR]   [TR]   [TR]   [TR]   → error₁
  Fold 2: [TR]   [VAL]  [TR]   [TR]   [TR]   → error₂
  Fold 3: [TR]   [TR]   [VAL]  [TR]   [TR]   → error₃
  Fold 4: [TR]   [TR]   [TR]   [VAL]  [TR]   → error₄
  Fold 5: [TR]   [TR]   [TR]   [TR]   [VAL]  → error₅

  CV error = (error₁ + error₂ + error₃ + error₄ + error₅) / 5
```

Use **red** for [VAL] in fold 1, **blue** for [VAL] in fold 2, **green** for fold 3, **orange** for fold 4, **purple** for fold 5. The [TR] blocks can all be the same color (e.g., gray).

### What to Show

**Part A: The Procedure (5 min)**

1. Draw the grid row by row. After each row, ask: "Which block is validation? Which are training?"
2. After all 5 rows: "How many times is each data point used for validation?" → Exactly once.
3. "How many times for training?" → $k - 1 = 4$ times.
4. Write the CV error formula: average of the 5 validation errors.

**Part B: Compute Fold Sizes (3 min)**

1. "If we have 1000 examples and 5 folds, how many in each fold?" → 200.
2. "Training per fold?" → 800. "Validation per fold?" → 200.
3. "How many total model fits?" → 5.
4. Try $k = 10$: "100 per fold, 900 training, 10 model fits."

**Part C: Compare to Single Split (2 min)**

1. "A single 80/20 split gives ONE validation error. It might be unlucky — the validation set happens to be easy or hard."
2. "5-fold CV gives FIVE validation errors. We average them — less noise. We also get a standard deviation — a measure of stability."
3. Write: "Single split: 1 estimate. 5-fold CV: 5 estimates (average + std)."

**Part D: LOOCV (3 min)**

1. "What if $k = n$? Each fold is ONE data point. Train on $n-1$, test on 1. Repeat $n$ times."
2. "For 1000 examples, that's 1000 model fits. Expensive!"
3. Draw the comparison table:

| Property | LOOCV ($k=n$) | 5-fold CV |
|----------|---------------|-----------|
| Folds | $n$ | 5 |
| Training per fold | $n-1$ | $4n/5$ |
| Model fits | $n$ | 5 |
| Bias | Low | Slightly higher |
| Variance | Higher | Lower |
| Best for | Small $n$ | Most cases |

### Teaching Points

- Every data point is used for validation exactly once and for training $k-1$ times.
- CV reduces the noise of a single split.
- Higher $k$ = lower bias but higher variance and more computation. 5 or 10 is the sweet spot.
- LOOCV ($k=n$) is for very small datasets only.

---

## Demo 3: Confusion Matrix Construction (Fill In Live with Students)

**Tool:** Whiteboard drawing (no software needed)  
**Used in:** Session 2, minutes 10–25  
**Prep time:** None

### Setup

Draw an empty 2×2 grid on the board. Prepare the spam filter scenario: 1000 emails (100 spam, 900 not spam). The model's results: 80 spam correctly identified, 20 spam missed, 10 good emails flagged, 890 good emails left alone.

### What to Draw

**Step 1: Draw the empty grid**

```
                    Predicted Spam    Predicted Not Spam
                    ──────────────    ──────────────────
Actual Spam         ?                 ?
Actual Not Spam     ?                 ?
```

**Step 2: Fill in with students**

Ask students where each number goes:

```
                    Predicted Spam    Predicted Not Spam
                    ──────────────    ──────────────────
Actual Spam         TP = 80           FN = 20
Actual Not Spam     FP = 10           TN = 890
```

**Step 3: Add labels and arrows**

Draw arrows showing:
- Precision: TP / (TP + FP) → points to the **column** (all predicted positive)
- Recall: TP / (TP + FN) → points to the **row** (all actual positive)

**Step 4: Compute metrics**

Write the formulas and results next to the matrix:

```
Accuracy  = (TP + TN) / Total = (80 + 890) / 1000 = 97%
Precision = TP / (TP + FP)   = 80 / 90           = 88.9%
Recall    = TP / (TP + FN)   = 80 / 100          = 80%
F1        = 2·P·R / (P + R)  = 2·(0.889·0.80) / (0.889 + 0.80) = 84.2%
```

### What to Show

**Part A: Building the Matrix (5 min)**

1. Present the scenario: "1000 emails. 100 spam, 900 not spam. Our model catches 80 of the 100 spam, but flags 10 good emails as spam."
2. Draw the empty grid. Ask students to fill in each cell.
3. After each cell, ask: "What do we call this? TP, FP, FN, or TN?"
4. **Mnemonic for students:** "True/False = did we get it right? Positive/Negative = what did we predict?"

**Part B: Computing Metrics (5 min)**

1. Ask students for the formula BEFORE writing it. "How would you compute accuracy?" → Correct / Total.
2. "Precision: of everything we PREDICTED as spam, how much was actually spam?" → TP / (TP + FP). Point to the column.
3. "Recall: of all the ACTUAL spam, how much did we catch?" → TP / (TP + FN). Point to the row.
4. "F1: the harmonic mean. High only when BOTH precision and recall are high."

**Part C: Interpretation (3 min)**

1. "97% accuracy sounds great. But recall is 80% — we miss 1 in 5 spam emails."
2. "Precision is 89% — when we say 'spam,' we're right 89% of the time."
3. "Which metric matters depends on the problem. For spam, precision matters (don't flag good emails). For cancer, recall matters (don't miss cases)."

**Part D: The Baseline Comparison (2 min)**

1. "What if we just predict 'not spam' for everything?"
2. Draw the baseline matrix:

```
                    Predicted Spam    Predicted Not Spam
                    ──────────────    ──────────────────
Actual Spam         TP = 0            FN = 100
Actual Not Spam     FP = 0            TN = 900
```

3. "Accuracy: 900/1000 = 90%. Only 7% worse than our model! But recall = 0%, F1 = 0. The baseline catches NO spam."
4. **The punchline:** "Accuracy makes the baseline look decent. Precision, recall, and F1 reveal it's useless."

### Teaching Points

- The confusion matrix is the starting point for all classification metrics.
- **Precision = column** (all predicted positive). **Recall = row** (all actual positive).
- Accuracy can be misleading. Always compute multiple metrics.
- The mnemonic "True/False = right/wrong, Positive/Negative = prediction" helps students remember TP/FP/FN/TN.

---

## Demo 4: ROC Curve Construction Step-by-Step (Desmos)

**Tool:** Desmos Graphing Calculator (https://www.desmos.com/calculator)  
**Used in:** Session 2, minutes 40–55  
**Prep time:** 10 minutes

### Setup

**Step 1: Enter the 8 data points**

This is the worked example from handout Section 5.5. Write the table on the board AND have it ready in Desmos.

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

There are 4 spam (positives) and 4 not-spam (negatives).

**Step 2: Prepare the Desmos plot**

In Desmos, create a scatter plot of the (FPR, TPR) points:

Enter each point individually:
- `(0, 0)`
- `(0, 0.25)`
- `(0.25, 0.5)`
- `(0.5, 0.75)`
- `(0.75, 1)`
- `(1, 1)`

Add the diagonal line: `y = x` from 0 to 1 (this represents random guessing).

Connect the points with line segments to form the ROC curve.

**Step 3: Prepare the threshold-sweep table**

Have this table ready to fill in on the board:

| Threshold | TP | FP | FN | TN | TPR | FPR |
|-----------|----|----|----|----|-----|-----|
| >0.95 | 0 | 0 | 4 | 4 | 0 | 0 |
| 0.90 | 1 | 0 | 3 | 4 | 0.25 | 0 |
| 0.85 | 2 | 1 | 2 | 3 | 0.50 | 0.25 |
| 0.50 | 3 | 2 | 1 | 2 | 0.75 | 0.50 |
| 0.20 | 4 | 3 | 0 | 1 | 1.0 | 0.75 |
| 0.10 | 4 | 4 | 0 | 0 | 1.0 | 1.0 |

### What to Show

**Part A: The Threshold Concept (3 min)**

1. Show the 8-example table on the board.
2. "The model outputs a probability for each example. We choose a threshold $t$: if $P(\text{spam}) > t$, predict spam."
3. "If $t = 1.0$: predict nothing as spam. TP = 0, FP = 0. TPR = 0, FPR = 0." → Point to bottom-left of the plot.
4. "If $t = 0.0$: predict everything as spam. TP = 4, FP = 4. TPR = 1, FPR = 1." → Point to top-right of the plot.
5. "As we lower $t$ from 1.0 to 0.0, we sweep through intermediate points."

**Part B: Sweep the Threshold (5 min)**

1. Start with threshold > 0.95 (predict nothing as spam). "Which examples are above 0.95?" → Example 1 only. "But wait — 0.95 is not > 0.95, so actually nothing." → TP = 0, FP = 0, TPR = 0, FPR = 0. Plot (0, 0).
2. Lower to $t = 0.90$: "Which examples have $P \geq 0.90$?" → Examples 1, 2. Both spam. TP = 2, FP = 0. TPR = 2/4 = 0.50, FPR = 0/4 = 0. Plot (0, 0.50).

   > **Note:** The handout uses "≥ threshold" for simplicity. Be consistent — either ">" or "≥". Use "≥" in class to match the handout table. The key idea is the same either way.

3. Lower to $t = 0.85$: Examples 1, 2, 3. Example 3 is not spam. TP = 2, FP = 1. TPR = 0.50, FPR = 1/4 = 0.25. Plot (0.25, 0.50).
4. Lower to $t = 0.50$: Examples 1–5. TP = 3 (examples 1, 2, 4), FP = 2 (examples 3, 5). TPR = 3/4 = 0.75, FPR = 2/4 = 0.50. Plot (0.50, 0.75).
5. Lower to $t = 0.20$: Examples 1–7. TP = 4, FP = 3. TPR = 1.0, FPR = 0.75. Plot (0.75, 1.0).
6. Lower to $t = 0.10$: All examples. TP = 4, FP = 4. TPR = 1.0, FPR = 1.0. Plot (1.0, 1.0).

**Part C: The Curve (3 min)**

1. Show all points plotted in Desmos. Connect them with line segments.
2. "This is the ROC curve. It goes from (0,0) to (1,1)."
3. Draw (or show) the diagonal line $y = x$: "This is random guessing. Any model above the diagonal is better than random."
4. "A curve hugging the top-left corner is excellent — high TPR, low FPR."

**Part D: AUC Interpretation (2 min)**

1. "AUC = area under the ROC curve. For this example, AUC ≈ 0.82." (Estimate by counting squares or using Desmos.)
2. Show the AUC interpretation table:

| AUC | Meaning |
|-----|---------|
| 1.0 | Perfect |
| 0.9 | Excellent |
| 0.7 | Good |
| 0.5 | Random |
| < 0.5 | Worse than random (flip!) |

3. **The beautiful interpretation:** "AUC = the probability that the model ranks a random positive example higher than a random negative example." Write this prominently.
4. "If AUC = 0.82, there's an 82% chance that a random spam email gets a higher score than a random non-spam email."

**Part E: Good vs. Bad ROC Curves (2 min)**

Draw three curves on the board (or in Desmos):

```
  TPR
  1.0 │ ┌────────     │    ╱──────      │ ╱
      │ │             │   ╱             │╱
      │ │             │  ╱              │
  0.5 │ │             │ ╱               │
      │ │             │╱                │
  0.0 │─┘────────     │────────────     │────────────
      0.0     1.0     0.0     1.0       0.0     1.0
       Perfect          Good             Random
       (AUC = 1.0)     (AUC ≈ 0.7)      (AUC = 0.5)
```

### Teaching Points

- The ROC curve shows the tradeoff between TPR (catching positives) and FPR (false alarms) at every threshold.
- The diagonal is random guessing. Above the diagonal = better than random.
- AUC is a single-number summary: 1.0 = perfect, 0.5 = random.
- **AUC = P(positive scores higher than negative)** — this is the key interpretation.
- Lowering the threshold always increases both TPR and FPR — you catch more positives but also get more false alarms.

---

## Demo 5: Precision-Recall Tradeoff Visualization

**Tool:** Desmos (or whiteboard drawing)  
**Used in:** Session 2, minutes 55–62  
**Prep time:** 5 minutes

### Setup

In Desmos, plot the 8 data points from Demo 4 as a number line (probability axis) with their labels. Alternatively, draw a horizontal number line on the board.

### What to Draw / Show

**Step 1: The Probability Number Line**

Draw a horizontal line from 0 to 1. Place the 8 examples on it:

```
  0.10  0.20  0.30  0.50  0.70  0.85  0.90  0.95
  ──N────N────S────N────S────N────S────S──→ P(spam)
  
  S = Spam, N = Not spam
```

**Step 2: Sweep the Threshold**

Draw a vertical line representing the threshold $t$. Move it from right to left.

- **$t = 0.95$ (far right):** Predict spam only for $P > 0.95$. No examples pass. Precision = undefined (0/0), Recall = 0%.
- **$t = 0.90$:** Example 1 (spam) passes. Precision = 1/1 = 100%, Recall = 1/4 = 25%.
- **$t = 0.85$:** Examples 1, 2 (spam), 3 (not spam) pass. Precision = 2/3 = 67%, Recall = 2/4 = 50%.
- **$t = 0.50$:** Examples 1–5 pass. TP = 3, FP = 2. Precision = 3/5 = 60%, Recall = 3/4 = 75%.
- **$t = 0.10$ (far left):** All examples pass. Precision = 4/8 = 50%, Recall = 4/4 = 100%.

**Step 3: Plot the PR Curve**

Plot (Recall, Precision) points in Desmos:

```
  Precision
  1.0 │ ●
      │  ╲
  0.7 │   ●
      │    ╲
  0.6 │     ●
      │      ╲
  0.5 │       ●
      │
  0.0 │──────────── Recall
      0   0.25  0.5  0.75  1.0
```

### What to Show

**Part A: The Tradeoff (3 min)**

1. Start with threshold at far right. "High threshold = very selective. We only predict spam when we're very confident. Precision is high, but recall is low — we miss most spam."
2. Move threshold to the left. "Lowering the threshold: we catch more spam (recall goes up), but we also start flagging good emails (precision goes down)."
3. Move threshold to far left. "Low threshold = predict spam for everything. Recall = 100% (we catch all spam), but precision is terrible (lots of false alarms)."

**Part B: Use Cases (2 min)**

| Threshold | Precision | Recall | Use case |
|-----------|-----------|--------|----------|
| High (0.9) | High | Low | Spam filter (don't flag good emails) |
| Low (0.1) | Low | High | Cancer screening (don't miss any cases) |
| Balanced (0.5) | Moderate | Moderate | General purpose |

1. "For spam: precision matters. A false positive (good email → spam folder) is very costly. Use a high threshold."
2. "For cancer: recall matters. A false negative (missed cancer) is potentially fatal. Use a low threshold."
3. "There is no 'correct' threshold in general — it depends on the costs of each type of error."

**Part C: PR vs ROC (2 min)**

1. "ROC plots TPR vs FPR. PR plots Precision vs Recall."
2. "When classes are balanced, both work fine."
3. "When classes are imbalanced (e.g., 0.1% fraud), PR is more informative. ROC can look misleadingly good because FPR is dominated by the huge number of true negatives."
4. "This is the key insight from the Davis & Goadrich paper we're reading this week."

### Teaching Points

- Precision and recall trade off against each other. You can't maximize both simultaneously.
- The threshold controls the tradeoff. High threshold → high precision, low recall. Low threshold → low precision, high recall.
- The "right" threshold depends on the problem — specifically, on the relative costs of false positives vs. false negatives.
- PR curves are preferred over ROC for imbalanced datasets.

---

## Demo 6: Learning Curves (Train vs. Val Error vs. Training Size)

**Tool:** Desmos (or whiteboard drawing)  
**Used in:** Session 2, minutes 70–73  
**Prep time:** 5 minutes

### Setup

In Desmos, prepare four learning curve plots. Alternatively, draw them on the board. Each plot has:
- X-axis: Training set size (from 0 to $n$)
- Y-axis: Error
- Two curves: Training error (starts low, increases) and Validation error (starts high, decreases)

### What to Draw

**Plot 1: Overfitting (high variance)**

```
  Error
    │  Validation
    │  ╲
    │   ╲────────        ← Large gap
    │    ╱
    │   ╱
    │  ╱ Training
    │ ╱
    │╱
    └────────────────── Training set size
```

- Training error: low (model fits training data well)
- Validation error: high (model doesn't generalize)
- Large gap between the two
- **Diagnosis:** Overfitting. **Fix:** More data, or regularization.

**Plot 2: Underfitting (high bias)**

```
  Error
    │  Validation
    │  ╲
    │   ╲
    │    ╲
    │     ╲──────        ← Small gap, both HIGH
    │     ╱──────
    │    ╱
    │   ╱ Training
    │  ╱
    └────────────────── Training set size
```

- Training error: high (model can't fit even the training data)
- Validation error: high
- Small gap (both converged at a high level)
- **Diagnosis:** Underfitting. **Fix:** More complex model, add features.

**Plot 3: Good Fit**

```
  Error
    │  Validation
    │  ╲
    │   ╲
    │    ╲___            ← Small gap, both LOW
    │    ╱───
    │   ╱
    │  ╱ Training
    │ ╱
    │╱
    └────────────────── Training set size
```

- Training error: low
- Validation error: low
- Small gap, both converged at a low level
- **Diagnosis:** Good fit. **Done!**

**Plot 4: Need More Data AND Complexity**

```
  Error
    │  Validation
    │  ╲
    │   ╲
    │    ╲              ← Large gap, both HIGH
    │     ╲
    │      ╲
    │     ╱
    │    ╱ Training
    │   ╱
    └────────────────── Training set size
```

- Training error: high (but might decrease with more data)
- Validation error: high
- Large gap AND both high
- **Diagnosis:** Need more data AND a more complex model.

### What to Show

**Part A: The Shape of Learning Curves (2 min)**

1. Draw Plot 1 (overfitting). "As we add more training data, training error goes UP (harder to fit more points) but validation error goes DOWN (more data = better generalization)."
2. "The gap between them is the 'generalization gap.' A large gap means overfitting."

**Part B: Diagnosis (1 min)**

1. Show all four plots side by side.
2. Point to the key feature of each:
   - Overfitting: large gap, low training error
   - Underfitting: small gap, both high
   - Good fit: small gap, both low
   - Need both: large gap, both high

**Part C: The Key Insight (1 min)**

1. "If the curves haven't converged (large gap), adding more data WILL help — the gap will shrink."
2. "If the curves HAVE converged but both are high, adding more data WON'T help. You need a more complex model."
3. **Connect to Week 3:** "Last week's complexity curve: fixed data, vary complexity → find the sweet spot. This week's learning curve: fixed model, vary data → determine if more data would help. They're complementary tools."

### Teaching Points

- Learning curves plot error vs. **training set size** (not model complexity — that was Week 3's complexity curve).
- Large gap = overfitting (high variance). Adding data helps.
- Both high + small gap = underfitting (high bias). Adding data doesn't help; need more complexity.
- The two tools (complexity curve + learning curve) together give a complete picture of model health.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Train/val/test split diagram | S1 | 8 min | Whiteboard | Three sets, three purposes, the Golden Rule |
| 2 | k-fold cross-validation visual | S1 | 13 min | Whiteboard + colors | CV procedure, fold sizes, LOOCV comparison |
| 3 | Confusion matrix construction | S2 | 15 min | Whiteboard | Build TP/FP/FN/TN, compute all metrics |
| 4 | ROC curve construction | S2 | 15 min | Desmos | Step-by-step ROC construction, AUC interpretation |
| 5 | Precision-recall tradeoff | S2 | 7 min | Desmos / Whiteboard | Threshold tradeoff, PR vs ROC |
| 6 | Learning curves | S2 | 3 min | Desmos / Whiteboard | Diagnose overfitting/underfitting from data size |

**Total demo time:** ~61 minutes across both sessions. This leaves ~19 minutes per session for lecture, discussion, and quizzes. Session 1 has more time for lecture; Session 2 is demo-heavy.

---

## Pre-Class Tech Check

Before each session, verify:

- [ ] Desmos loads and the ROC curve data is entered (Session 2)
- [ ] Desmos has the PR curve points plotted (Session 2)
- [ ] Desmos has the learning curve sketches ready (Session 2)
- [ ] Whiteboard has enough space for the k-fold diagram and confusion matrix
- [ ] Colored markers are available (5 colors for k-fold, 2 colors for ROC)
- [ ] Quiz printed or ready to project
- [ ] The 8-example ROC table is written out for quick reference (Session 2)
- [ ] The spam filter scenario (1000 emails) is ready (Session 2)
