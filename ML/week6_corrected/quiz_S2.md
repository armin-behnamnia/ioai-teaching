# Week 6 (Corrected), Session 2 — End-of-Session Quiz

> **Time:** 8 minutes
> **Topics:** Gradient concept, update rule, learning rate, GD on MSE, SGD vs batch GD, feature scaling, ridge/lasso GD
> **Format:** 6 questions
> **Closed notes**
> **Note:** Q6 is a spiral-back from Session 1.

---

## Questions

**Q1. [Calculation — 2 min]**

Minimize $f(w) = w^2$ with $\eta = 0.1$. Start at $w_0 = 5$.

(a) What is $f'(w_0)$?
(b) What is $w_1$?
(c) What is the general formula for $w_{t+1}$ in terms of $w_t$?

**Q2. [Derivation — 2 min]**

For $\text{MSE}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - wx_i - b)^2$:

(a) Compute $\frac{\partial \text{MSE}}{\partial w}$ (show chain rule steps).
(b) Write the GD update rule for $w$.

**Q3. [Multiple choice — 1 min]**

Key difference between batch GD and SGD?

(a) Batch uses closed form; SGD uses iteration.
(b) Batch uses all $n$ examples; SGD uses one random example.
(c) Batch always converges; SGD never.
(d) Batch for regression; SGD for classification.

Justify in one sentence.

**Q4. [Conceptual — 1 min]**

(a) Why does feature scaling help GD converge faster?
(b) What is the data leakage risk when scaling? How do you prevent it?

**Q5. [Conceptual — 1 min]**

The ridge GD update includes $-2\eta\lambda w$. What does this term do? Connect it to what we proved in Session 1 (MAP = Ridge).

**Q6. [Spiral-back — 1 min]**

In Session 1, we proved that MSE = MLE under Gaussian noise, and ridge = MAP with a Gaussian prior. In one sentence: why does this mean that gradient descent on MSE is "maximum likelihood estimation by iterative optimization"?

**★ [Challenge — optional, 2 min]**

For lasso, $L = \text{MSE} + \lambda|w|$. The derivative of $|w|$ is $\text{sgn}(w)$.

(a) Write the lasso GD update.
(b) Why does lasso drive weights to **exactly zero** while ridge does not?
(c) Connect this to Session 1: which prior causes this sparsity, and why?

---

---

## Solutions

### Q1. Solution

(a) $f'(w) = 2w$. $f'(5) = 10$.
(b) $w_1 = 5 - 0.1 \times 10 = 4$.
(c) $w_{t+1} = w_t(1 - 2\eta) = 0.8\, w_t$.

**Grading:** 0–3.
- 3: All correct.
- 2: Two correct.
- 1: One correct.
- 0: None.

**Common mistakes:**
- $f'(w_0) = 5$ (forgetting the factor of 2).
- Adding instead of subtracting: $w_1 = 6$ (going uphill).

### Q2. Solution

Let $r_i = y_i - wx_i - b$.

(a) $\frac{\partial}{\partial w}(r_i^2) = 2r_i \cdot (-x_i) = -2x_i r_i$ (chain rule).

$$\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$$

(b) $w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i$

**Grading:** 0–3.
- 3: Gradient with chain rule + correct update.
- 2: One, or minor errors.
- 1: Partial.
- 0: None.

**Common mistakes:**
- Forgetting chain rule: missing $-x_i$ factor.
- Sign error: $\partial(-wx_i)/\partial w = -x_i$, not $+x_i$.
- Forgetting $\frac{1}{n}$.

### Q3. Solution

**Answer: (b).** Batch uses all $n$; SGD uses one random example.

**Grading:** 0–3.
- 3: Correct + justification.
- 2: Correct, weak.
- 1: Wrong but reasonable.
- 0: Wrong.

### Q4. Solution

(a) Different scales → elongated loss surface → GD zigzags. After scaling → spherical → smooth convergence.

(b) **Leakage risk:** computing $\bar{x}$, $\sigma_x$ on all data (including test). **Prevention:** split FIRST, compute stats on training only, apply to all sets.

**Grading:** 0–3.
- 3: (a) Elongated→spherical + zigzag. (b) Leakage + prevention.
- 2: One correct.
- 1: Partial.
- 0: None.

### Q5. Solution

The $-2\eta\lambda w$ term is **shrinkage** — it pulls $w$ toward 0 each step. In Session 1, we proved ridge = MAP with a Gaussian prior. The shrinkage term is the GD implementation of that prior: the prior says "weights should be small," and GD enforces this by shrinking $w$ at every step.

**Grading:** 0–3.
- 3: Shrinkage + connection to MAP/Gaussian prior from Session 1.
- 2: Shrinkage only, or connection without explaining shrinkage.
- 1: "Regularization."
- 0: None.

### Q6. Solution (Spiral-Back)

Since MSE = MLE under Gaussian noise, minimizing MSE via GD is the same as finding the maximum likelihood estimator iteratively. GD is the optimization tool; MLE is the probabilistic principle that tells us WHAT to minimize.

**Grading:** 0–3.
- 3: Connects GD (how) to MLE (what) clearly.
- 2: Mentions both but connection unclear.
- 1: Partial.
- 0: None.

### ★ Challenge Solution

(a) $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - \eta\lambda \, \text{sgn}(w)$.

(b) $|w|$ is non-differentiable at 0. The subgradient at 0 is 0 (by convention), so once $w$ reaches 0, the shrinkage term vanishes and $w$ stays. Ridge's $2\lambda w$ is smooth at 0 — shrinks toward 0 but never reaches it.

(c) The Laplacian prior $p(w) \propto \exp(-|w|/\tau)$ causes sparsity. Its sharp peak at 0 (non-differentiable) means the MAP solution favors $w = 0$ for weak signals. This is the probabilistic explanation for the geometric L1 diamond argument from Week 3.

**Grading:** Bonus.
- "Excellent": All three parts + connection to Session 1.
- "Good attempt": Two.
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | GD on 1D quadratic | | |
| Q2 | MSE gradient | | |
| Q3 | Batch vs SGD | | |
| Q4 | Feature scaling + leakage | | |
| Q5 | Ridge shrinkage + MAP connection | | |
| Q6 | Spiral-back: GD = MLE by iteration | | |
| ★ | Lasso subgradient + sparsity + prior | | |

---

## Post-Quiz Notes

- [ ] Can students compute GD steps? → Practice more if not.
- [ ] Can students derive MSE gradient (chain rule)? → Essential for Week 7.
- [ ] Do they understand SGD vs batch? → Re-emphasize if not.
- [ ] Do they remember data leakage in scaling? → Week 4 concept; re-emphasize.
- [ ] Do they see the connection between Session 1 (probability) and Session 2 (optimization)? → This is the key synthesis.

### Topics to spiral back:
- GD update rule → Week 7 (logistic regression GD)
- MSE gradient → Week 7 (cross-entropy gradient, "beautiful cancellation")
- SGD vs batch → Week 7, Week 17
- Feature scaling → Week 8 (condition number), Week 15 (NN preprocessing)
- Ridge/lasso GD → Week 8 (coordinate descent), Week 17 (proximal methods)
- MLE/MAP → Week 7 (cross-entropy = MLE for Bernoulli), Week 8 (matrix form)
- Learning rate diagnosis → Week 7, Week 17
