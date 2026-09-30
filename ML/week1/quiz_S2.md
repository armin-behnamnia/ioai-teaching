# Week 1, Session 2 — End-of-Day Quiz

> **Time:** 10 minutes  
> **Topics:** Supervised learning pipeline, overfitting/underfitting, generalization, overfitting-underfitting tradeoff  
> **Format:** 5 questions, mix of conceptual, multiple choice, and calculation  
> **Closed notes**  
> **Note:** Q5 is a spiral-back question from Session 1.

---

## Questions

**Q1. [Conceptual — 2 min]**

Explain the difference between overfitting and underfitting. For each, state:
(a) What happens to the training error?
(b) What happens to the test error?
(c) Give a one-sentence analogy (not from the handout — make up your own).

**Q2. [Multiple choice — 1 min]**

A model achieves zero training error but high test error. This is an example of:

(a) Underfitting  
(b) Overfitting  
(c) A bug in the code  
(d) The model being too simple

Justify your answer in one sentence.

**Q3. [Calculation — 3 min]**

Given the dataset:

| $x_i$ | $y_i$ |
|-------|-------|
| 1 | 2 |
| 2 | 4 |
| 3 | 6 |

Model A: $f(x) = 2x$  
Model B: $f(x) = x + 1$

(a) Compute the empirical risk (mean squared error) for Model A.  
(b) Compute the empirical risk for Model B.  
(c) Which model is better according to the empirical risk?

**Q4. [Conceptual — 2 min]**

A student says: "I made my hypothesis space larger (added more parameters), so my model must be better." Is this correct? Explain why or why not in 2–3 sentences.

**Q5. [Spiral-back — 1 min]**

In the supervised learning framework, what are the three components that define a machine learning problem? (Hint: Think about what you choose before you start training.)

**★ [Challenge — optional, 2 min]**

You have 10 data points and fit a degree-9 polynomial. The polynomial passes through all 10 points exactly, so the training error is zero.

(a) How many parameters does this model have?  
(b) Will it generalize well? Why or why not?  
(c) What would happen if you had 10,000 data points and fit the same degree-9 polynomial?

---
---

## Solutions

### Q1. Solution

| | Overfitting | Underfitting |
|---|---|---|
| **(a) Training error** | Low (often near zero) | High |
| **(b) Test error** | High | High |
| **(c) Analogy** | *Example:* Memorizing practice exam answers word-for-word but failing the real exam because questions are phrased differently. | *Example:* Showing up to an exam having only read the textbook cover — you didn't learn enough to answer any questions well. |

**Acceptable analogies (students may create their own):**
- Overfitting: "Learning a specific route to school but getting lost if there's a road closure." ✓
- Underfitting: "Learning to ride a bike by reading a book — never actually practiced." ✓
- Overfitting: "A suit tailored so precisely to one body position that you can't move in it." ✓
- Underfitting: "Wearing a one-size-fits-all sack — fits nobody well." ✓

**Grading:** 0–3 scale.  
- 3: All six cells correct (training error, test error, analogy for both).  
- 2: 4–5 cells correct.  
- 1: 2–3 cells correct.  
- 0: 0–1 cells correct.

**Common mistakes to watch for:**
- Saying overfitting has high training error → No, overfitting has *low* training error. That's the trap — it looks good on training data.
- Saying underfitting has low test error → No, both training and test error are high.

### Q2. Solution

**Answer: (b) Overfitting**

**Justification:** Zero training error means the model perfectly fits (memorizes) the training data, but high test error means it fails to generalize to new data. This is the hallmark of overfitting — the model is too complex relative to the amount of data.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification.  
- 2: Correct answer, weak justification.  
- 1: Wrong answer but some correct reasoning.  
- 0: Wrong answer, no justification.

### Q3. Solution

**Model A: $f(x) = 2x$**

| $i$ | $x_i$ | $y_i$ | $\hat{y}_i = 2x_i$ | $(\hat{y}_i - y_i)^2$ |
|-----|-------|-------|---------------------|------------------------|
| 1 | 1 | 2 | 2 | $(2-2)^2 = 0$ |
| 2 | 2 | 4 | 4 | $(4-4)^2 = 0$ |
| 3 | 3 | 6 | 6 | $(6-6)^2 = 0$ |

$$R_{\text{emp}}(A) = \frac{1}{3}(0 + 0 + 0) = 0$$

**Model B: $f(x) = x + 1$**

| $i$ | $x_i$ | $y_i$ | $\hat{y}_i = x_i + 1$ | $(\hat{y}_i - y_i)^2$ |
|-----|-------|-------|------------------------|------------------------|
| 1 | 1 | 2 | 2 | $(2-2)^2 = 0$ |
| 2 | 2 | 4 | 3 | $(3-4)^2 = 1$ |
| 3 | 3 | 6 | 4 | $(4-6)^2 = 4$ |

$$R_{\text{emp}}(B) = \frac{1}{3}(0 + 1 + 4) = \frac{5}{3} \approx 1.67$$

**(c)** Model A is better because $R_{\text{emp}}(A) = 0 < 1.67 = R_{\text{emp}}(B)$.

**Grading:** 0–3 scale.  
- 3: All three parts correct with correct calculations.  
- 2: Two parts correct, or correct method with arithmetic errors.  
- 1: One part correct.  
- 0: No correct work.

**Common mistakes to watch for:**
- Forgetting to square the errors (computing $\frac{1}{3}(0 + (-1) + (-2)) = -1$ — negative "error" doesn't make sense).  
- Forgetting to divide by $n = 3$.  
- Squaring the prediction instead of the error ($(4)^2$ instead of $(4-4)^2$).  
- Computing absolute error instead of squared error.

### Q4. Solution

**Answer:** No, this is incorrect.

A larger hypothesis space means the model *can* represent more complex functions. This means it can fit more patterns, but it also increases the risk of overfitting (the model can fit noise, not just signal). A larger hypothesis space only helps if it includes the true function AND the data is sufficient to distinguish the true function from noise. Beyond that point, adding parameters makes generalization worse, not better.

**Key points to look for in the answer:**
- Larger hypothesis space → more flexibility (can fit more patterns) ✓
- But → higher overfitting risk (can fit noise) ✓
- The model is not automatically "better" — it depends on the data and the true function ✓

**Grading:** 0–3 scale.  
- 3: Says "not correct" and explains both the flexibility increase and the overfitting risk.  
- 2: Says "not correct" and explains one side (either flexibility or overfitting).  
- 1: Says "not correct" but gives weak or incorrect reasoning.  
- 0: Says "correct" or no answer.

### Q5. Solution (Spiral-Back)

The three components that define a machine learning problem are:

1. **Hypothesis space** $\mathcal{H}$ — the set of models to choose from
2. **Loss function** $L$ — how to measure prediction error
3. **Optimizer** (or optimization procedure) — how to find the best parameters (minimize empirical risk)

**Alternative acceptable answers:**
- "Model + loss + optimizer" ✓
- "Hypothesis space + loss function + data" ✓ (data is also a valid answer — the learning problem is defined by what data you have)
- "Input space, output space, hypothesis space" ✓ (these define the problem setup; loss + optimizer define the solution approach)

**Grading:** 0–3 scale.  
- 3: All three correct.  
- 2: Two correct.  
- 1: One correct.  
- 0: None correct.

### ★ Challenge Solution

**(a)** A degree-9 polynomial $f(x) = a_9 x^9 + a_8 x^8 + \ldots + a_1 x + a_0$ has **10 parameters** (coefficients $a_0, a_1, \ldots, a_9$). With 10 data points and 10 parameters, the system is exactly determined — there is a unique polynomial passing through all points (assuming the $x$-values are distinct).

**(b)** It will likely **not generalize well**. With 10 parameters and 10 data points, the model has enough flexibility to pass through every point exactly, including any noise. The polynomial will likely oscillate wildly between data points. The model has memorized the data rather than learned the underlying pattern.

**(c)** With 10,000 data points and a degree-9 polynomial (10 parameters), the model is now **under-parameterized** relative to the data. It can no longer pass through every point (there are 10,000 constraints but only 10 parameters). The polynomial will fit the overall trend, and the empirical risk will reflect the true pattern + irreducible noise. In this case, the same model that overfit with 10 points would likely generalize **well** with 10,000 points.

**The lesson:** Whether a model overfits depends not just on the model's complexity, but on the **ratio of model complexity to data size**. The same model can overfit with little data and underfit with lots of data.

**Grading:** Bonus — not counted toward base score.  
- "Excellent": All three parts correct.  
- "Good attempt": 1–2 parts correct or correct intuition without full explanation.  
- "Attempted": Tried but mostly incorrect.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Overfitting vs. underfitting | | |
| Q2 | Identifying overfitting | | |
| Q3 | Empirical risk calculation | | |
| Q4 | Hypothesis space and complexity | | |
| Q5 | Spiral-back: ML problem components | | |
| ★ | Parameters vs. data size | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Did students confuse "low training error" with "good model"? → Re-emphasize next week.
- [ ] Can students compute empirical risk? → If not, practice in Week 2.
- [ ] Do students understand the three components (hypothesis space, loss, optimizer)? → If not, review at the start of Week 2, Session 1.
- [ ] Did any students attempt the challenge? How did they do? → Note for differentiation.

### Topics to spiral back in future quizzes:

- Overfitting/underfitting → spiral back in Week 2 (ridge regression) and Week 5 (formal treatment)
- Empirical risk calculation → spiral back in Week 2 (MSE for linear regression)
- Types of learning → spiral back in Week 6 (SGD is supervised) and Week 19 (unsupervised)
