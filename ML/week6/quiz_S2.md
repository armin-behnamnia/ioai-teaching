# Week 6, Session 2 — End-of-Session Quiz

> **Time:** 10 minutes  
> **Topics:** GD on MSE, SGD vs batch GD, feature scaling, ridge/lasso GD  
> **Format:** 6 questions  
> **Closed notes**  
> **Note:** Q6 is a spiral-back from Session 1.

---

## Questions

**Q1. [Derivation — 3 min]**

For $\text{MSE}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - wx_i - b)^2$:

(a) Compute $\frac{\partial \text{MSE}}{\partial w}$ (show chain rule steps).  
(b) Compute $\frac{\partial \text{MSE}}{\partial b}$.  
(c) Write the GD update rules for $w$ and $b$.

**Q2. [Multiple choice — 1 min]**

Key difference between batch GD and SGD?

(a) Batch uses closed form; SGD uses iteration.  
(b) Batch uses all $n$ examples; SGD uses one random example.  
(c) Batch always converges; SGD never.  
(d) Batch for regression; SGD for classification.

Justify in one sentence.

**Q3. [Conceptual — 2 min]**

The gradient of MSE w.r.t. $w$ is $-\frac{2}{n}\sum_i x_i r_i$ where $r_i = y_i - \hat{y}_i$.

(a) What does it mean when this gradient is zero ($\sum_i x_i r_i = 0$)?  
(b) Why is this the optimality condition for OLS?

**Q4. [Conceptual — 2 min]**

(a) Why does feature scaling help GD converge faster?  
(b) What is the data leakage risk when scaling? How do you prevent it?

**Q5. [Conceptual — 1 min]**

The ridge GD update includes $-2\eta\lambda w$. What does this term do? What happens as $\lambda \to \infty$?

**Q6. [Spiral-back — 1 min]**

If you observe the training loss **oscillating** (going up and down), what should you do? Why?

**★ [Challenge — optional, 2 min]**

For lasso, $L = \text{MSE} + \lambda|w|$. The derivative of $|w|$ is $\text{sgn}(w)$.

(a) Write the lasso GD update.  
(b) Why does lasso drive weights to **exactly zero** while ridge does not?  
(c) What is the subgradient at $w = 0$, and why does $w$ "stick" there?

---

---

## Solutions

### Q1. Solution

Let $r_i = y_i - wx_i - b$.

(a) $\frac{\partial}{\partial w}(r_i^2) = 2r_i \cdot (-x_i) = -2x_i r_i$ (chain rule).

$$\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$$

(b) $\frac{\partial r_i}{\partial b} = -1$.

$$\frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$$

(c) $w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i$, $\quad b \leftarrow b + \frac{2\eta}{n}\sum_i r_i$.

**Grading:** 0–3.  
- 3: All three with chain rule.  
- 2: Two, or minor errors.  
- 1: One.  
- 0: None.

**Common mistakes:**
- Forgetting chain rule: missing $-x_i$ factor.
- Sign error: $\partial(-wx_i)/\partial w = -x_i$, not $+x_i$.
- Forgetting $\frac{1}{n}$.

### Q2. Solution

**Answer: (b).** Batch uses all $n$; SGD uses one random example.

**Grading:** 0–3.  
- 3: Correct + justification.  
- 2: Correct, weak.  
- 1: Wrong but reasonable.  
- 0: Wrong.

### Q3. Solution

(a) Residuals are **uncorrelated** with inputs. The model has extracted all linear information from $x$ about $y$.

(b) At the MSE minimum, gradient = 0, i.e., $\sum x_i r_i = 0$. This IS the OLS optimality condition (scalar normal equation). GD finds the same answer as the closed form.

**Grading:** 0–3.  
- 3: (a) Uncorrelated residuals. (b) Gradient=0 at minimum = OLS.  
- 2: One correct.  
- 1: Partial.  
- 0: None.

**Common mistakes:**
- "Residuals = 0" (no — just uncorrelated with $x$).
- Not connecting to OLS.

### Q4. Solution

(a) Different scales → elongated loss surface → GD zigzags (overshoots in steep direction, crawls in shallow). After scaling → spherical surface → smooth convergence.

(b) **Leakage risk:** computing $\bar{x}$, $\sigma_x$ on all data (including test). **Prevention:** split FIRST, compute stats on training only, apply to all sets.

**Grading:** 0–3.  
- 3: (a) Elongated→spherical + zigzag. (b) Leakage + prevention.  
- 2: One correct.  
- 1: Partial.  
- 0: None.

### Q5. Solution

The $-2\eta\lambda w$ term is **shrinkage**. Each step pulls $w$ toward 0. As $\lambda \to \infty$: shrinkage dominates, $w \to 0$, model predicts $\bar{y}$ (max bias, zero variance).

**Grading:** 0–3.  
- 3: Shrinkage + $\lambda \to \infty$ behavior.  
- 2: One part.  
- 1: "Regularization."  
- 0: None.

### Q6. Solution (Spiral-Back)

Learning rate is **too large**. Steps overshoot. Fix: **reduce $\eta$** (e.g., halve it).

**Grading:** 0–3.  
- 3: $\eta$ too large + reduce it.  
- 2: Identifies problem, no fix.  
- 1: Vague.  
- 0: None.

### ★ Challenge Solution

(a) $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - \eta\lambda \, \text{sgn}(w)$.

(b) $|w|$ is non-differentiable at 0. The subgradient at 0 is 0 (by convention), so once $w$ reaches 0, the shrinkage term vanishes and $w$ stays. Ridge's $2\lambda w$ is smooth at 0 — shrinks toward 0 but never reaches it.

(c) Subgradient at $w = 0$ is 0. The update becomes $w \leftarrow \frac{2\eta}{n}\sum x_i r_i$ (data term only). If this is smaller than the "stickiness," $w$ stays at 0. This is **soft-thresholding**: weights zeroed when data signal < $\lambda$.

**Grading:** Bonus.  
- "Excellent": All three.  
- "Good attempt": Two.  
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | MSE gradient | | |
| Q2 | Batch vs SGD | | |
| Q3 | Optimality condition | | |
| Q4 | Feature scaling + leakage | | |
| Q5 | Ridge shrinkage term | | |
| Q6 | Spiral-back: oscillating loss | | |
| ★ | Lasso subgradient + sparsity | | |

---

## Post-Quiz Notes

- [ ] Can students derive MSE gradient (chain rule)? → Essential for Week 7.
- [ ] Do they understand SGD vs batch? → Re-emphasize if not.
- [ ] Do they remember data leakage in scaling? → Week 4 concept; re-emphasize.
- [ ] Did anyone attempt the challenge? → Note for differentiation.

### Topics to spiral back:

- MSE gradient → Week 7 (cross-entropy gradient, "beautiful cancellation")
- SGD vs batch → Week 7, Week 17
- Feature scaling → Week 8 (condition number), Week 15 (NN preprocessing)
- Ridge/lasso GD → Week 8 (coordinate descent), Week 17 (proximal methods)
- Learning rate diagnosis → Week 7, Week 17
