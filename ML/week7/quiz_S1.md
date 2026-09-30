# Week 7, Session 1 — End-of-Session Quiz

> **Time:** 8 minutes
> **Topics:** Spiral-back review — Weeks 1–4 (problem setup, OLS/ridge, overfitting, evaluation)
> **Format:** 5 questions
> **Closed notes**
> **Note:** After the two-week break, this quiz is deliberately review-focused. Use results to identify decay.

---

## Questions

**Q1. [Conceptual — 2 min]**

State the four components of the ML problem setup (input space, output space, hypothesis space, loss function), and explain in one sentence each what the hypothesis space and the loss function represent.

**Q2. [Calculation — 2 min]**

A dataset has $\bar{x} = 2$, $\bar{y} = 5$, $\text{Var}(x) = 4$, $\text{Cov}(x,y) = 6$.

(a) Compute the OLS solution $(w^*, b^*)$.
(b) Compute the ridge solution for $w$ with $\lambda = 2$ (same $b$ rule).

**Q3. [Conceptual — 1 min]**

Sketch or describe: training error and test error as model complexity increases. Label the underfitting and overfitting regions, and mark where you would want to operate.

**Q4. [Calculation — 2 min]**

A classifier on 2000 examples (200 positives) produces: TP = 120, FN = 80, FP = 180, TN = 1520.

(a) Build the confusion matrix and compute accuracy, precision, recall.
(b) A colleague says "92% accuracy — great model!" Respond in one sentence.

**Q5. [Conceptual — 1 min]**

State the golden rule of the test set, and give one concrete example of data leakage.

---

## Solutions

### Q1. Solution

- Input space $X$: where the features live.
- Output space $Y$: where the predictions/targets live.
- Hypothesis space $H$: the set of models/functions we allow ourselves to choose from — it encodes our assumptions ("what we're allowed to learn").
- Loss function $L$: a numerical measure of how wrong a prediction is — it encodes what we care about.

**Grading:** 0–3.
- 3: All four named + both H and L explained.
- 2: All four named, one explanation missing/weak.
- 1: Two or three components.
- 0: None.

**Common mistakes:**
- Confusing hypothesis space with the model's parameters.
- Saying the loss "measures accuracy" without the wrongness framing.

### Q2. Solution

(a) $w^* = \text{Cov}/\text{Var} = 6/4 = 1.5$; $b^* = \bar{y} - w^*\bar{x} = 5 - 1.5 \times 2 = 2$.

(b) $w^*_{\text{ridge}} = \text{Cov}/(\text{Var} + \lambda) = 6/(4+2) = 1$.

**Grading:** 0–3.
- 3: All values correct with formulas visible.
- 2: One arithmetic slip.
- 1: Correct approach, multiple slips.
- 0: Wrong approach.

**Common mistakes:**
- $b^* = \bar{y} + w^*\bar{x}$ (sign error — the classic).
- Adding $\lambda$ to Cov instead of Var.

### Q3. Solution

Training error decreases monotonically with complexity. Test error is U-shaped: decreases, reaches a minimum, then increases. Underfitting = left (both errors high). Overfitting = right (training low, test high, large gap). Operate near the bottom of the U.

**Grading:** 0–3.
- 3: Both curves correct + regions labeled + operating point.
- 2: Curves correct, labels missing.
- 1: Only one curve or no U-shape.
- 0: None.

**Common mistakes:**
- Drawing test error as monotonically decreasing.
- Putting overfitting on the left.

### Q4. Solution

(a) Accuracy $= (120+1520)/2000 = 82\%$. Precision $= 120/300 = 40\%$. Recall $= 120/200 = 60\%$.

(b) With 10% prevalence, a trivial "always negative" classifier already gets 90% — accuracy is dominated by the majority class. Precision/recall (or PR curves) are the right lenses (class imbalance).

**Grading:** 0–3.
- 3: All metrics correct + imbalance argument.
- 2: Metrics correct, weak argument.
- 1: Partial metrics.
- 0: None.

**Common mistakes:**
- Precision $= 120/200$ (using actual positives instead of predicted positives).

### Q5. Solution

Golden rule: the test set is used exactly once, at the very end — never for model selection or tuning. Leakage example: computing normalization statistics (or scaling, or feature selection) on the full dataset before splitting; or using future data to predict the past; any test information influencing training decisions.

**Grading:** 0–3.
- 3: Rule + a genuine leakage example.
- 2: Rule + vague example.
- 1: One of the two.
- 0: None.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | ML problem setup (W1) | | |
| Q2 | OLS + ridge closed form (W2) | | |
| Q3 | Complexity dial (W3) | | |
| Q4 | Confusion matrix / imbalance (W4) | | |
| Q5 | Golden rule / leakage (W4) | | |

---

## Post-Quiz Notes

- [ ] If Q2 is weak → re-drill closed forms in Session 2's warm-up.
- [ ] If Q4 is weak → the metrics story must be re-touched before Week 8's ROC-for-logistic-regression.
- [ ] Record names for anyone scoring 0–1 on two or more questions → targeted check-in.
