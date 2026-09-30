# Week 3, Session 2 — End-of-Day Quiz

> **Time:** 10 minutes  
> **Topics:** Ridge regression (λ knob, shrinkage), bias-variance intuition, lasso/L1 geometry, no closed form for lasso, elastic net, complexity dial, residual analysis  
> **Format:** 5 questions + 1 challenge, mix of conceptual, multiple choice, and calculation  
> **Closed notes**  
> **Calculators allowed**  
> **Note:** Q5 is a spiral-back question from Session 1.

---

## Questions

**Q1. [Multiple choice — 1 min]**

The ridge regression slope is $w^*_{\text{ridge}} = \frac{\text{Cov}(x, y)}{\text{Var}(x) + \lambda}$. Which of the following correctly describes what happens as $\lambda$ increases from 0 to $\infty$?

(a) The slope increases, bias decreases, variance increases.  
(b) The slope shrinks toward zero, bias increases, variance decreases.  
(c) The slope stays the same, only the intercept changes.  
(d) The slope oscillates between positive and negative values.

Justify your answer in one sentence.

**Q2. [Conceptual — 2 min]**

Fill in the following table with "Low," "Moderate," or "High" for each cell:

| | $\lambda = 0$ (OLS) | $\lambda$ moderate | $\lambda \to \infty$ |
|---|---|---|---|
| **Training error** | | | |
| **Test error** | | | |
| **Bias** | | | |
| **Variance** | | | |

**Q3. [Conceptual — 2 min]**

(a) Explain in 2–3 sentences why lasso (L1) produces **sparse** weights (some exactly zero) while ridge (L2) does not. Use the geometric picture.  
(b) Why does lasso have **no closed-form solution**, unlike ridge?

**Q4. [Conceptual — 2 min]**

Fill in the complexity dial table:

| Model | Complexity knob | Low complexity (underfit) | High complexity (overfit) |
|-------|-----------------|--------------------------|--------------------------|
| Polynomial regression | ? | ? | ? |
| Ridge regression | ? | ? | ? |
| k-NN (Week 9) | ? | ? | ? |
| Decision trees (Week 10) | ? | ? | ? |

**Q5. [Spiral-back — 1 min]**

In Session 1, we saw that training error is monotonically non-increasing with polynomial degree, and test error has a U-shape.

(a) Does the same U-shape appear when we plot test error vs. $\lambda$ (the ridge parameter)? If so, which side is overfitting and which is underfitting?  
(b) You fit a polynomial model and observe the residuals show a clear U-shaped pattern (not random scatter). What does this tell you, and what should you do?

**★ [Challenge — optional, 2 min]**

The ridge slope can be written as $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$, where $w^*_{\text{OLS}} = \frac{\text{Cov}(x,y)}{\text{Var}(x)}$.

(a) What is the "shrinkage factor" $\frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$? Is it always between 0 and 1? Why?  
(b) As $\lambda \to 0$, what happens to the shrinkage factor? As $\lambda \to \infty$?  
(c) Can ridge ever change the SIGN of the OLS slope? Why or why not?

---
---

## Solutions

### Q1. Solution

**Answer: (b)** The slope shrinks toward zero, bias increases, variance decreases.

**Justification:** As $\lambda$ increases, the denominator $\text{Var}(x) + \lambda$ grows, so $w^*_{\text{ridge}}$ shrinks toward zero. Shrinking the slope means the model fits the training data less closely (higher bias) but is less sensitive to the specific training data (lower variance). At $\lambda \to \infty$, $w \to 0$ and the model predicts $\bar{y}$ for everything — maximum bias, minimum variance.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning shrinkage and the bias-variance tradeoff.  
- 2: Correct answer, partial justification (e.g., "the slope shrinks" without mentioning bias/variance).  
- 1: Wrong answer but some correct reasoning.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a): This reverses the bias-variance tradeoff. Increasing $\lambda$ increases bias and decreases variance, not the other way around.  
- Choosing (c): The slope definitely changes — that's the whole point of ridge. The intercept changes too (via $b^* = \bar{y} - w\bar{x}$), but the slope is what $\lambda$ controls.  
- Choosing (d): The slope monotonically shrinks toward zero. It never oscillates.

### Q2. Solution

| | $\lambda = 0$ (OLS) | $\lambda$ moderate | $\lambda \to \infty$ |
|---|---|---|---|
| **Training error** | **Low** | **Moderate** | **High** (≈ Var(y)) |
| **Test error** | **High** (can overfit) | **Low** (sweet spot) | **High** |
| **Bias** | **Low** | **Moderate** | **High** |
| **Variance** | **High** | **Moderate** | **Low** |

**Key points:**
- Training error increases monotonically with $\lambda$ (more regularization = worse fit to training data).
- Test error has a U-shape: high at $\lambda = 0$ (overfitting), minimum at moderate $\lambda$, high at $\lambda \to \infty$ (underfitting).
- Bias increases with $\lambda$ (the model systematically underfits). Variance decreases with $\lambda$ (the model is more stable).
- The sweet spot (moderate $\lambda$) minimizes Bias² + Variance, giving the lowest test error.

**Grading:** 0–3 scale.  
- 3: All 12 cells correct.  
- 2: 9–11 cells correct.  
- 1: 5–8 cells correct.  
- 0: 0–4 cells correct.

**Common mistakes to watch for:**
- Putting "Low" for OLS test error → OLS can overfit, so test error can be HIGH at $\lambda = 0$. The whole point of ridge is that OLS often has high test error due to overfitting.
- Putting "High" for OLS bias → OLS has LOW bias (it tries hard to fit the data). The problem with OLS is HIGH variance, not high bias.
- Putting "Low" for $\lambda \to \infty$ training error → When $\lambda \to \infty$, $w \to 0$ and the model predicts $\bar{y}$ for everything. Training error ≈ Var(y), which is HIGH.
- Reversing bias and variance → A common confusion. Bias = systematic error (how far off on average). Variance = sensitivity to data (how much predictions change with different training sets). More regularization → more bias, less variance.

### Q3. Solution

**(a)** The L1 constraint ($\|\mathbf{w}\|_1 \leq t$) forms a **diamond** shape in weight space, with corners on the axes. The L2 constraint ($\|\mathbf{w}\|^2 \leq t$) forms a **ball** (circle/sphere) with no corners. When the OLS solution is projected back onto the constraint region, the L1 diamond is most likely to be touched at a **corner**, where some weights are exactly zero (on an axis). The L2 ball is typically touched at a smooth point where all weights are nonzero (but small). This is why lasso produces sparsity and ridge does not.

**(b)** Lasso has no closed-form solution because the absolute value function $|w|$ is **not differentiable** at $w = 0$ — it has a "corner" (the left derivative is $-1$ and the right derivative is $+1$). We cannot set the gradient to zero and solve algebraically, as we can for ridge (where $w^2$ is smooth). Lasso requires iterative optimization (e.g., coordinate descent or proximal gradient methods — Week 6).

**Grading:** 0–3 scale.  
- 3: Both parts correct with clear geometric explanation in (a) and nondifferentiability in (b).  
- 2: One part fully correct, or both partially correct.  
- 1: One part partially correct.  
- 0: Neither part correct.

**Common mistakes to watch for:**
- (a): Saying "L1 is stronger than L2" → It's not about strength; it's about the GEOMETRY. The diamond's corners are the key. Both L1 and L2 shrink weights; only L1 produces exact zeros.  
- (a): Mentioning "sparsity" without explaining WHY → Must explain the geometric mechanism (corners on axes).  
- (b): Saying "lasso is more complex" → The reason is mathematical: nondifferentiability of $|w|$ at $w = 0$. It has nothing to do with complexity.  
- (b): Saying "because L1 has no formula" → This is circular. The reason there's no formula is the nondifferentiability.

### Q4. Solution

| Model | Complexity knob | Low complexity (underfit) | High complexity (overfit) |
|-------|-----------------|--------------------------|--------------------------|
| Polynomial regression | Degree $d$ | $d = 1$ (line) | $d = n-1$ (through all points) |
| Ridge regression | $\lambda$ | $\lambda \to \infty$ ($w \to 0$) | $\lambda = 0$ (OLS) |
| k-NN (Week 9) | $k$ | $k = n$ (predict $\bar{y}$) | $k = 1$ (memorize) |
| Decision trees (Week 10) | Depth | Depth 1 (stump) | Depth $\infty$ (memorize) |

**Grading:** 0–3 scale.  
- 3: All 8 cells correct (knob + both directions for all 4 models).  
- 2: 6–7 cells correct.  
- 1: 3–5 cells correct.  
- 0: 0–2 cells correct.

**Common mistakes to watch for:**
- Reversing the $\lambda$ direction → $\lambda = 0$ is OLS (HIGH complexity), $\lambda \to \infty$ is constant (LOW complexity). The relationship is INVERSE: more $\lambda$ = less complex.  
- Reversing the $k$ direction → $k = 1$ is HIGH complexity (memorize), $k = n$ is LOW complexity (predict mean). Again inverse: more $k$ = less complex.  
- For polynomial degree: $d = 1$ is LOW (line), $d = n-1$ is HIGH (through all points). This one is direct: more degree = more complex.  
- For tree depth: Depth 1 is LOW (stump), Depth $\infty$ is HIGH (memorize). Direct: more depth = more complex.

### Q5. Solution (Spiral-Back)

**(a)** Yes! The same U-shape appears. When plotting test error vs. $\lambda$:
- **Small $\lambda$ (left side):** overfitting (like OLS, model is too complex).
- **Large $\lambda$ (right side):** underfitting (model is too constrained, predicts $\bar{y}$).
- **Moderate $\lambda$ (bottom of U):** the sweet spot.

The U-shape is universal — it appears for every complexity knob, not just polynomial degree. This is the complexity dial principle.

**(b)** A U-shaped pattern in the residuals means the model is **systematically wrong** — it's **underfitting**. The model is missing a nonlinear pattern in the data. The fix is to **increase model complexity** (e.g., add polynomial features, increase the degree, or use a more flexible model). Random scatter in residuals indicates a good fit; a pattern indicates underfitting.

**Grading:** 0–3 scale.  
- 3: Both parts correct with clear explanation.  
- 2: One part fully correct, or both partially correct.  
- 1: One part partially correct.  
- 0: Neither part correct.

**Common mistakes to watch for:**
- (a): Saying the U-shape doesn't appear for $\lambda$ → It does! The U-shape is universal across all complexity knobs. This is the key insight of the complexity dial.  
- (a): Reversing the directions (saying large $\lambda$ = overfitting) → Large $\lambda$ = more regularization = LESS complex = underfitting.  
- (b): Saying the U-shaped residuals indicate overfitting → No! A pattern in residuals means the model is MISSING something — that's underfitting. Overfitting would show random residuals (the model fits everything, including noise).  
- (b): Saying "add regularization" → No, regularization makes the model SIMPLER. The model is already too simple (missing the curve). You need MORE complexity, not less.

### ★ Challenge Solution

**(a)** The shrinkage factor is $s = \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$. Since $\text{Var}(x) > 0$ (assuming $x$ is not constant) and $\lambda \geq 0$, we have $\text{Var}(x) + \lambda \geq \text{Var}(x) > 0$, so $0 < s \leq 1$. The shrinkage factor is always between 0 and 1 (inclusive of 1 when $\lambda = 0$). This means ridge always shrinks the OLS slope toward zero, never past it.

**(b)** 
- As $\lambda \to 0$: $s \to \frac{\text{Var}(x)}{\text{Var}(x)} = 1$. Ridge reduces to OLS — no shrinkage.
- As $\lambda \to \infty$: $s \to \frac{\text{Var}(x)}{\infty} = 0$. The slope shrinks to zero — the model predicts $\bar{y}$ for everything.

**(c)** No, ridge can never change the sign of the OLS slope. The shrinkage factor $s = \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$ is always positive (since $\text{Var}(x) > 0$ and $\lambda \geq 0$). Therefore $w^*_{\text{ridge}} = s \cdot w^*_{\text{OLS}}$ has the same sign as $w^*_{\text{OLS}}$. Ridge shrinks the magnitude but preserves the direction. (In the multi-feature case, this is more subtle — ridge can change individual weight signs due to correlations between features — but in the scalar case, the sign is always preserved.)

**The lesson:** Ridge is a "gentle" regularizer — it shrinks weights toward zero but never eliminates them (no sparsity) and never flips their signs (in the scalar case). This contrasts with lasso, which CAN set weights to exactly zero.

**Grading:** Bonus — not counted toward the base score.  
- "Excellent": All three parts correct with clear reasoning.  
- "Good attempt": 1–2 parts correct, or correct intuition without full algebra.  
- "Attempted": Tried but mostly incorrect.

---

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Ridge shrinkage and bias-variance direction | | |
| Q2 | Bias-variance table for λ = 0, moderate, ∞ | | |
| Q3 | L1 geometry (sparsity) and no closed form | | |
| Q4 | The complexity dial table | | |
| Q5 | Spiral-back: U-shape for λ + residual analysis | | |
| ★ | Ridge shrinkage factor and sign preservation | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Do students understand that increasing $\lambda$ shrinks the slope and trades bias for variance? → If Q1 scores are low, review the ridge formula and the denominator mechanism at the start of Week 4.
- [ ] Can students fill in the bias-variance table correctly? → If Q2 scores are low, redraw the table on the board. The most common error is reversing bias and variance.
- [ ] Do students understand the L1 diamond geometry and why it produces sparsity? → If Q3 scores are low, redraw the circle vs. diamond diagram. This is the conceptual core of Session 2.
- [ ] Can students fill in the complexity dial table? → If Q4 scores are low, redraw the universal table. Watch for reversed directions on $\lambda$ and $k$.
- [ ] Do students connect the U-shape across different knobs and understand residual patterns? → If Q5 scores are low, review the complexity dial principle and residual analysis.
- [ ] Did any students attempt the challenge? The shrinkage factor is a key algebraic result. Students who get this are ready for the matrix ridge treatment in Week 8.

### Topics to spiral back in future quizzes:

- Ridge shrinkage mechanism → spiral back in Week 4 (validation curve for choosing λ) and Week 8 (matrix ridge: the shrinkage becomes a matrix operation)
- Bias-variance table → spiral back in Week 5 (formal bias-variance decomposition with probability)
- L1/L2 geometry → spiral back in Week 8 (matrix form, KKT conditions) and Week 6 (subgradient methods for lasso)
- Complexity dial → spiral back in Week 9 (k as the knob), Week 10 (depth as the knob), and Week 15 (number of parameters as the knob)
- Residual analysis → spiral back in Week 4 (model diagnostics) and Week 7 (logistic regression residuals)
- Shrinkage factor → spiral back in Week 8 (matrix ridge regression, ridge path)
