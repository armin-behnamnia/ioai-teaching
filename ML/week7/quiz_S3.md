# Week 7, Session 3 — End-of-Session Quiz

> **Time:** 6 minutes
> **Topics:** GD by hand, learning-rate regimes, the MSE gradient, SGD vs. batch, feature scaling
> **Format:** 4 questions
> **Closed notes**

---

## Questions

**Q1. [Calculation — 2 min]**

Minimize $f(w) = 3w^2$ by gradient descent, starting at $w_0 = 2$ with $\eta = 0.1$.

(a) Write the update rule for $w$.
(b) Compute $w_1$ and $w_2$.
(c) What is the multiplication factor per step? Will GD converge?

**Q2. [Multiple choice — 1 min]**

During training, the loss goes $5.0 \to 5.1 \to 5.3 \to 5.6 \to 6.0 \to \ldots$. The most likely diagnosis:

(a) Learning rate too small.
(b) Learning rate too large.
(c) Model underfitting.
(d) Data not shuffled.

Justify in one sentence.

**Q3. [Derivation — 2 min]**

For linear regression with residuals $r_i = y_i - wx_i - b$:

(a) Write $\frac{\partial \text{MSE}}{\partial b}$ in terms of the residuals.
(b) At the optimum, what is $\sum_i x_i r_i$? Give its interpretation in one sentence.

**Q4. [Conceptual — 1 min]**

Give two reasons why mini-batch GD (with $B = 32$–$128$) is the standard in modern ML, compared to full-batch GD.

---

## Solutions

### Q1. Solution

(a) $f'(w) = 6w$, so $w \leftarrow w - 0.6w = 0.4w$.
(b) $w_1 = 2 \times 0.4 = 0.8$; $w_2 = 0.8 \times 0.4 = 0.32$.
(c) Factor $= |1 - \eta a| = |1 - 0.1 \times 6| = 0.4 < 1$: yes, converges (geometrically, since here $f = \frac{1}{2}aw^2$ with $a = 6$; condition $0 < \eta < 2/6 \approx 0.33$ holds).

**Grading:** 0–3.
- 3: Rule + both values + factor/convergence with condition.
- 2: Rule + values, weak analysis.
- 1: One element.
- 0: None.

**Common mistakes:**
- Using $f(w)$ instead of $f'(w)$ in the update.
- Computing $w_1 = 2 - 0.1 \times 6 \times 2$ correctly but then mis-multiplying on the second step.

### Q2. Solution

**Answer: (b).** The loss is increasing (roughly geometrically) — classic divergence: the step overshoots the minimum and grows each iteration, meaning $\eta$ exceeds the stability limit ($\eta > 2/a$ for a quadratic).

**Grading:** 0–3.
- 3: (b) + overshoot/growth rationale.
- 2: (b) + vague rationale.
- 1: (b) only.
- 0: Wrong.

**Common mistakes:**
- Choosing (c) — confusing a growing *loss* with a high-but-stable loss (underfitting).

### Q3. Solution

(a) $\frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_{i=1}^n r_i$.
(b) $\sum_i x_i r_i = 0$: at the optimum the residuals are uncorrelated with the inputs (what's left over carries no linear information about $x$) — the OLS/GD optimality condition.

**Grading:** 0–3.
- 3: Formula + zero + uncorrelated interpretation.
- 2: Formula + zero, weak interpretation.
- 1: One element.
- 0: None.

**Common mistakes:**
- Missing the $-\frac{2}{n}$ (sign/scale).
- Interpreting $\sum x_i r_i = 0$ as "residuals are zero."

### Q4. Solution

Any two of:
1. Much cheaper per step ($B$ examples instead of all $n$) → many more updates per unit compute.
2. The gradient noise (variance $\propto 1/B$) helps escape poor regions in non-convex problems (neural networks).
3. Practical: fits in memory/hardware (GPU) parallelism; enables streaming/large datasets.
4. Slightly noisy steps can also have a regularizing effect.

**Grading:** 0–3.
- 3: Two distinct, correct reasons.
- 2: One correct reason + one fragment.
- 1: One reason.
- 0: None.

**Common mistakes:**
- "Mini-batch converges faster per epoch, always" — overclaim; the honest statement is cheaper *per step*.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | GD by hand + convergence | | |
| Q2 | Regime diagnosis | | |
| Q3 | MSE gradient + optimality | | |
| Q4 | Mini-batch rationale | | |

---

## Post-Quiz Notes

- [ ] Q1/Q3 weak → GD-by-hand drill needed before logistic-regression training (Week 8 S1).
- [ ] Topics to spiral: MSE gradient structure → Week 8 S1 (cross-entropy gradient cancellation); feature scaling → Week 8 (data pipeline); loss curves → Week 17 (NN training).
