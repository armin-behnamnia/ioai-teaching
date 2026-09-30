# Week 3, Session 1 — End-of-Day Quiz

> **Time:** 8 minutes  
> **Topics:** Polynomial regression, degree-vs-data tradeoff, training error monotonicity, generalization gap, diagnostic table  
> **Format:** 4 questions + 1 challenge, mix of conceptual, calculation, and multiple choice  
> **Closed notes**  
> **Calculators allowed**

---

## Questions

**Q1. [Conceptual — 2 min]**

You fit three polynomial models to a dataset with 12 data points. You observe:

| Model | Degree | Training MSE | Test MSE |
|-------|--------|-------------|----------|
| A | 1 | 18.5 | 19.2 |
| B | 3 | 2.1 | 3.0 |
| C | 11 | 0.00 | 25.4 |

(a) For each model, state: Is it underfitting, overfitting, or a good fit?  
(b) What is the generalization gap for each model?  
(c) Which model would you deploy, and why?

**Q2. [Multiple choice — 1 min]**

Why does training error always decrease (or stay the same) when you increase the polynomial degree $d$?

(a) Because higher-degree polynomials have more parameters, and more parameters always means lower error.  
(b) Because a degree-$(d+1)$ polynomial can represent everything a degree-$d$ polynomial can (by setting the extra coefficient to zero), plus more.  
(c) Because the test data is easier to fit with more parameters.  
(d) Because higher-degree polynomials automatically remove noise from the data.

Justify your answer in one sentence.

**Q3. [Conceptual — 1 min]**

You have $n = 10$ data points.

(a) What happens when you fit a degree-9 polynomial (10 parameters)? What is the training error?  
(b) What happens when you fit a degree-15 polynomial (16 parameters)? Is the solution unique?

**Q4. [Conceptual — 2 min]**

A classmate says: "My model has training MSE = 0.5 and test MSE = 0.7. It must be overfitting because test error is higher than training error."

(a) Is the classmate correct? Explain why or why not.  
(b) What would overfitting actually look like in terms of training and test errors?

**★ [Challenge — optional, 2 min]**

Prove that training error is a monotonically non-increasing function of polynomial degree $d$. That is, if $d_1 < d_2$, then $R_{\text{train}}(d_2) \leq R_{\text{train}}(d_1)$.

*(Hint: A degree-$d_1$ polynomial is a special case of a degree-$d_2$ polynomial. Think about what the optimizer can do with the extra parameters.)*

---
---

## Solutions

### Q1. Solution

**(a) Diagnoses:**

- **Model A (degree 1):** Both training and test error are high, and the gap is small (0.7). → **Underfitting.** The model is too simple to capture the pattern.
- **Model B (degree 3):** Both errors are low and close (gap = 0.9). → **Good fit.** Degree 3 captures the pattern without fitting noise.
- **Model C (degree 11):** Training error ≈ 0 but test error is very high (gap = 25.4). → **Overfitting.** With 12 parameters for 12 data points, the model passes through every point exactly, memorizing noise.

**(b) Generalization gaps ($R_{\text{test}} - R_{\text{train}}$):**

- Model A: $19.2 - 18.5 = 0.7$
- Model B: $3.0 - 2.1 = 0.9$
- Model C: $25.4 - 0.00 = 25.4$

**(c) Deploy Model B.** It has the lowest test error (3.0), and the generalization gap is small. Model A underfits (can't capture the pattern), and Model C overfits (memorizes noise, terrible test performance).

**Grading:** 0–3 scale.  
- 3: All three parts correct with clear reasoning.  
- 2: Two parts correct, or correct method with minor errors.  
- 1: One part correct.  
- 0: No correct work.

**Common mistakes to watch for:**
- Saying Model A is overfitting because test > train → No! Both errors are HIGH and the gap is small. That's underfitting. Overfitting requires a LARGE gap.
- Saying Model C is a good fit because training error is zero → This is the central trap of the week! Zero training error means overfitting when the test error is high.
- Computing the gap as $R_{\text{train}} - R_{\text{test}}$ (reversed) → The gap is always test minus train, and it's positive when the model overfits.

### Q2. Solution

**Answer: (b)** Because a degree-$(d+1)$ polynomial can represent everything a degree-$d$ polynomial can (by setting the extra coefficient to zero), plus more.

**Justification:** The set of degree-$(d+1)$ polynomials contains the set of degree-$d$ polynomials as a subset (just set the leading coefficient to zero). So the optimizer can always find a solution at least as good as the best degree-$d$ polynomial, and possibly better. The minimum over a larger set is always ≤ the minimum over a smaller set.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning nested hypothesis spaces or "can do everything the lower degree can."  
- 2: Correct answer, partial justification (e.g., "more parameters can fit better" without the nesting argument).  
- 1: Wrong answer but some correct reasoning.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a): "More parameters = lower error" is the right intuition but not the precise reason. The key is the NESTING — a higher-degree polynomial can always replicate a lower-degree one. Without nesting, more parameters wouldn't guarantee lower error. Give partial credit.
- Choosing (c): Test data is irrelevant to training error. Training error only depends on the training data.
- Choosing (d): Higher-degree polynomials don't remove noise — they FIT noise, which is the problem.

### Q3. Solution

**(a)** With $n = 10$ data points and a degree-9 polynomial (10 parameters), $d + 1 = n$. The polynomial has exactly enough degrees of freedom to pass through every data point. The training error is **zero**. The polynomial interpolates all points exactly — but between data points, it will oscillate wildly, leading to high test error.

**(b)** With degree 15 (16 parameters) and 10 data points, $d + 1 > n$. The system is **underdetermined** — there are infinitely many polynomials that pass through all 10 points with zero training error. The solution is **not unique**. OLS (in matrix form) would pick the minimum-norm solution, but there are infinitely many zero-training-error polynomials.

**Grading:** 0–3 scale.  
- 3: Both parts correct with clear explanation.  
- 2: One part fully correct, or both partially correct.  
- 1: One part partially correct.  
- 0: Neither part correct.

**Common mistakes to watch for:**
- (a): Saying the training error is "low" instead of "zero" → With $d+1 = n$, the polynomial passes through every point exactly. Training error is exactly zero.
- (b): Saying the solution is unique → It's NOT unique. When there are more parameters than data points, infinitely many solutions exist. This is the underdetermined regime.
- (b): Saying "it can't fit the data" → It CAN fit the data perfectly (zero training error). The problem is that there are too MANY perfect fits, not too few.

### Q4. Solution

**(a)** No, the classmate is NOT correct. A training MSE of 0.5 and test MSE of 0.7 represents a small gap (0.2) with both errors being low. This is a **good fit**, not overfitting. It is normal for test error to be slightly higher than training error — the model was fit on the training data, so it naturally performs slightly better there.

**(b)** Overfitting would look like: training error very low (near zero) AND test error much higher, with a **large** gap between them. For example, training MSE = 0.01 and test MSE = 15.0 (gap = 14.99) would indicate overfitting. The key is not that test > train (that's always expected), but that the gap is large relative to the error magnitudes.

**Grading:** 0–3 scale.  
- 3: Both parts correct with clear explanation about the gap being large vs. small.  
- 2: One part fully correct, or both partially correct.  
- 1: One part partially correct.  
- 0: Says the classmate is correct.

**Common mistakes to watch for:**
- Agreeing with the classmate → This is the most common misconception! Test > train does NOT automatically mean overfitting. A small gap is normal and healthy. Overfitting requires a LARGE gap.
- Saying "any gap means overfitting" → No. There is always some gap because the model was optimized on the training data. The question is whether the gap is large.
- In (b), giving an example where both errors are high → That's underfitting, not overfitting. Overfitting requires low training error AND high test error.

### ★ Challenge Solution

**Proof:**

Let $\mathcal{H}_{d}$ denote the set of all degree-$d$ polynomials. If $d_1 < d_2$, then $\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$ — every degree-$d_1$ polynomial is a special case of a degree-$d_2$ polynomial (just set the coefficients $w_{d_1+1}, w_{d_1+2}, \ldots, w_{d_2}$ to zero).

The training error is the minimum of the loss over the hypothesis space:

$$R_{\text{train}}(d) = \min_{f \in \mathcal{H}_d} \frac{1}{n}\sum_{i=1}^n (f(x_i) - y_i)^2$$

Since $\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$, the minimum over $\mathcal{H}_{d_2}$ is taken over a larger set. The optimizer can always choose the degree-$d_1$ polynomial (which is in $\mathcal{H}_{d_2}$) and achieve $R_{\text{train}}(d_1)$. But it might find something even better in the larger set. Therefore:

$$R_{\text{train}}(d_2) = \min_{f \in \mathcal{H}_{d_2}} R_{\text{emp}}(f) \leq \min_{f \in \mathcal{H}_{d_1}} R_{\text{emp}}(f) = R_{\text{train}}(d_1)$$

This is a nested hypothesis space argument: searching a bigger space can only find something better (or equal). $\square$

**The lesson:** Training error is monotonically non-increasing because higher-degree polynomial spaces contain lower-degree ones. This is why training error alone is misleading — it can only go down, even as the model gets worse at generalizing.

**Grading:** Bonus — not counted toward the base score.  
- "Excellent": Correct proof using the nesting argument ($\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$).  
- "Good attempt": Correct intuition (bigger space = can do at least as well) without formal notation.  
- "Attempted": Tried but mostly incorrect.

---

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Diagnosing underfitting/overfitting from errors | | |
| Q2 | Why training error is monotonic in degree | | |
| Q3 | Degree-vs-data: $d+1=n$ and $d+1>n$ | | |
| Q4 | Small gap ≠ overfitting | | |
| ★ | Proving monotonicity (nested hypothesis spaces) | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Can students diagnose underfitting vs. overfitting from training/test errors alone? → If Q1 scores are low, re-emphasize the diagnostic table at the start of Session 2. This is exam-critical.
- [ ] Do students understand WHY training error is monotonic? → If Q2 scores are low, review the nesting argument. Many students will say "more parameters" without the precise reasoning.
- [ ] Do students understand the $d+1 = n$ interpolation threshold and the $d+1 > n$ underdetermined regime? → If Q3 scores are low, redraw the degree-vs-data table.
- [ ] Do students understand that a small gap is normal and does NOT indicate overfitting? → If Q4 scores are low, this is a critical misconception. Re-emphasize: overfitting requires a LARGE gap.
- [ ] Did any students attempt the challenge? The nesting argument is a key conceptual tool that we'll use again in Week 18 (generalization theory).

### Topics to spiral back in future quizzes:

- Diagnosing from errors → spiral back in Week 4 (model evaluation: train/test split, cross-validation)
- Training error monotonicity → spiral back in Week 5 (bias-variance decomposition explains WHY test error is U-shaped)
- Degree-vs-data tradeoff → spiral back in Week 8 (matrix form: $d+1$ parameters, $n$ data points, rank of $X$)
- Small gap ≠ overfitting → spiral back in every week (this is a persistent misconception)
- Nested hypothesis spaces → spiral back in Week 18 (VC dimension, double descent, generalization theory)
