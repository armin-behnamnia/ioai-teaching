# Week 6, Session 1 — End-of-Session Quiz

> **Time:** 8 minutes  
> **Topics:** Gradient concept, update rule, learning rate, 1D quadratic, convergence, convexity  
> **Format:** 5 questions  
> **Closed notes**

---

## Questions

**Q1. [Calculation — 2 min]**

Minimize $f(w) = w^2$ with $\eta = 0.1$. Start at $w_0 = 5$.

(a) What is $f'(w_0)$?  
(b) What is $w_1$?  
(c) What is the general formula for $w_{t+1}$ in terms of $w_t$?

**Q2. [Conceptual — 2 min]**

Explain the GD update rule $\mathbf{w} \leftarrow \mathbf{w} - \eta \, \nabla L(\mathbf{w})$. What does each symbol represent? Why do we subtract the gradient (not add it)?

**Q3. [Multiple choice — 1 min]**

Which is true about the learning rate $\eta$?

(a) Larger $\eta$ always converges faster.  
(b) If $\eta$ is too large, the loss may increase (diverge).  
(c) $\eta$ has no effect on convergence.  
(d) Smaller $\eta$ always gives a better solution.

Justify in one sentence.

**Q4. [Conceptual — 2 min]**

For $f(w) = w^2$, the update is $w \leftarrow w(1 - 2\eta)$.

(a) For what range of $\eta$ does GD converge?  
(b) What happens at $\eta = 0.5$?  
(c) What happens at $\eta = 1.0$?

**Q5. [Conceptual — 1 min]**

What does it mean for a function to be **convex**? Why is convexity important for gradient descent?

**★ [Challenge — optional, 2 min]**

For $f(w) = \frac{1}{2}aw^2$, the update is $w \leftarrow w(1 - \eta a)$. (a) What $\eta$ reaches the minimum in one step? (b) What happens at $\eta = 2/a$? (c) Derive the convergence condition.

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

- $\mathbf{w}$: parameters. $\eta$: learning rate. $\nabla L$: gradient of loss. $\leftarrow$: assignment.
- We **subtract** because the gradient points **uphill** (steepest ascent). To minimize, we go **downhill** ($-\nabla L$).

**Grading:** 0–3.  
- 3: All symbols + why subtract.  
- 2: Most symbols, mentions downhill.  
- 1: Partial.  
- 0: None.

### Q3. Solution

**Answer: (b).** Too large $\eta$ → overshooting → divergence.

**Grading:** 0–3.  
- 3: Correct + justification (overshoot/diverge).  
- 2: Correct, weak.  
- 1: Wrong but reasonable.  
- 0: Wrong.

### Q4. Solution

(a) $0 < \eta < 1$ (from $|1 - 2\eta| < 1$).  
(b) $\eta = 0.5$: $w \leftarrow w(1-1) = 0$. Minimum in one step!  
(c) $\eta = 1.0$: $w \leftarrow w(1-2) = -w$. Oscillates between $w_0$ and $-w_0$ forever.

**Grading:** 0–3.  
- 3: All correct.  
- 2: Two correct.  
- 1: One correct.  
- 0: None.

**Common mistakes:**
- Missing $\eta > 0$ (at $\eta = 0$, no movement).
- Saying $\eta = 1.0$ diverges. It oscillates (loss doesn't increase). Divergence is $\eta > 1$.

### Q5. Solution

Convex = "bowl-shaped." A line between any two points lies above the function. One global minimum, no local minima. GD is **guaranteed** to converge to the global minimum (for suitable $\eta$).

**Grading:** 0–3.  
- 3: Defines convexity (one minimum/bowl) + explains guarantee.  
- 2: One of the two.  
- 1: Vague.  
- 0: None.

### ★ Challenge Solution

(a) $\eta = 1/a$: $w_1 = w_0(1-1) = 0$. One step.  
(b) $\eta = 2/a$: $w_1 = -w_0$. Oscillates.  
(c) $|1 - \eta a| < 1 \Rightarrow 0 < \eta < 2/a$.

**Grading:** Bonus.  
- "Excellent": All three.  
- "Good attempt": Two.  
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | GD on 1D quadratic | | |
| Q2 | Update rule | | |
| Q3 | Learning rate | | |
| Q4 | Convergence condition | | |
| Q5 | Convexity | | |
| ★ | Optimal learning rate | | |

---

## Post-Quiz Notes

- [ ] Can students compute GD steps? → Practice more if not.
- [ ] Do they understand why we subtract? → Re-emphasize "uphill vs downhill."
- [ ] Can they identify the convergence range? → Review $|1-2\eta|<1$ if not.

### Topics to spiral back:

- GD update rule → Week 7 (logistic regression GD)
- Learning rate regimes → Week 7, Week 17
- Convergence condition → Week 8 (matrix GD, condition number)
- Convexity → Week 7 (logistic regression is convex), Week 13 (SVM)
