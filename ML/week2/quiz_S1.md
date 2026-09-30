# Week 2, Session 1 — End-of-Day Quiz

> **Time:** 8 minutes  
> **Topics:** Linear regression model, MSE, OLS derivation (scalar), worked example  
> **Format:** 4 questions + 1 challenge, mix of calculation and conceptual  
> **Closed notes**  
> **Calculators allowed**

---

## Questions

**Q1. [Calculation — 4 min]**

Given the data:

| $x_i$ | $y_i$ |
|-------|-------|
| 1 | 3 |
| 2 | 5 |
| 3 | 7 |
| 4 | 9 |

(a) Compute $\bar{x}$, $\bar{y}$, $\text{Var}(x)$, and $\text{Cov}(x, y)$.

(b) Compute the OLS slope $w^*$ and intercept $b^*$.

(c) Write the model $\hat{y} = wx + b$.

**Q2. [Conceptual — 1 min]**

Why do we use **squared error** $(\hat{y} - y)^2$ instead of **absolute error** $|\hat{y} - y|$? Give two reasons.

**Q3. [Conceptual — 1 min]**

The OLS slope formula is $w^* = \text{Cov}(x, y) / \text{Var}(x)$. In one sentence, what does this ratio mean intuitively?

**Q4. [Conceptual — 1 min]**

The intercept formula is $b^* = \bar{y} - w^*\bar{x}$. What geometric property does this formula guarantee about the best-fit line?

**★ [Challenge — optional, 2 min]**

Suppose $\text{Cov}(x, y) = 0$ (x and y are uncorrelated) but $x$ and $y$ are NOT independent (there IS a relationship — just not a linear one).

(a) What is $w^*$? What does the model predict?

(b) Does $w^* = 0$ mean there is NO relationship between $x$ and $y$? Explain.

(c) Give a concrete example of two variables that have $\text{Cov}(x, y) = 0$ but are clearly related.

---
---

## Solutions

### Q1. Solution

**(a) Compute means, variance, and covariance:**

$$\bar{x} = \frac{1+2+3+4}{4} = \frac{10}{4} = 2.5$$

$$\bar{y} = \frac{3+5+7+9}{4} = \frac{24}{4} = 6$$

Centered values:

| $i$ | $x_i$ | $y_i$ | $\tilde{x}_i = x_i - \bar{x}$ | $\tilde{y}_i = y_i - \bar{y}$ | $\tilde{x}_i^2$ | $\tilde{x}_i\tilde{y}_i$ |
|-----|-------|-------|------|------|------|------|
| 1 | 1 | 3 | -1.5 | -3 | 2.25 | 4.5 |
| 2 | 2 | 5 | -0.5 | -1 | 0.25 | 0.5 |
| 3 | 3 | 7 | 0.5 | 1 | 0.25 | 0.5 |
| 4 | 4 | 9 | 1.5 | 3 | 2.25 | 4.5 |
| **Sum** | | | | | **5** | **10** |

$$\text{Var}(x) = \frac{5}{4} = 1.25$$

$$\text{Cov}(x, y) = \frac{10}{4} = 2.5$$

**(b) Compute slope and intercept:**

$$w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)} = \frac{2.5}{1.25} = 2$$

$$b^* = \bar{y} - w^* \cdot \bar{x} = 6 - 2 \cdot 2.5 = 6 - 5 = 1$$

**(c) The model:**

$$\hat{y} = 2x + 1$$

**Grading:** 0–3 scale.  
- 3: All parts (a), (b), (c) correct with correct calculations.  
- 2: Two parts correct, or correct method with minor arithmetic errors.  
- 1: One part correct, or correct setup with significant errors.  
- 0: No correct work.

**Common mistakes to watch for:**
- **Forgetting to center** before computing variance/covariance. Students compute $\frac{1}{n}\sum x_i^2$ instead of $\frac{1}{n}\sum (x_i - \bar{x})^2$. → Re-emphasize: always subtract the mean first.
- **Mixing up numerator and denominator**: writing $w^* = \text{Var}(x) / \text{Cov}(x,y)$. → Mnemonic: "what you're predicting ($y$) goes on top."
- **Sign errors** in centered values. When $x_i < \bar{x}$, $\tilde{x}_i$ is negative.
- **Forgetting to divide by $n$** in variance/covariance.
- **Not checking**: the data is perfectly linear ($y = 2x + 1$), so the model should fit perfectly. If a student gets nonzero residuals, they made an arithmetic error.

### Q2. Solution

**Two reasons for squared error over absolute error:**

1. **Differentiable / smooth:** Squared error is differentiable everywhere (no corners), making optimization easier. It produces a unique closed-form solution (the OLS formula). Absolute error has a corner at $\hat{y} = y$, making it harder to optimize.

2. **Penalizes large errors more:** Squaring amplifies large errors (e.g., an error of 10 contributes 100 to squared loss but only 10 to absolute loss). This means the model is pushed harder to avoid big mistakes.

3. **(Acceptable alternative) Unique solution:** Squared error gives a unique minimum (one best line). Absolute error can have multiple minima (a range of equally good lines).

4. **(Acceptable alternative — preview)** Probabilistic: Squared error corresponds to Gaussian noise, which is the most common noise model. (We'll see this in Week 5.)

**Grading:** 0–3 scale.  
- 3: Two correct, distinct reasons.  
- 2: One correct reason, or two partially correct.  
- 1: Mentions squared error "is better" without specific reasoning.  
- 0: No correct answer.

**Common mistakes to watch for:**
- Saying "squared error is more accurate" — this is vague and not quite right. Both are valid loss functions; they optimize for different things.
- Saying "squared error removes negative signs" — true but trivial. Absolute error also removes negative signs. The key difference is smoothness and the quadratic penalty on large errors.

### Q3. Solution

**Intuitive meaning of $w^* = \text{Cov}(x, y) / \text{Var}(x)$:**

The slope is the ratio of "how much $x$ and $y$ move together" (covariance) to "how much $x$ moves" (variance). It tells you how much $y$ changes, on average, for a unit change in $x$.

**Acceptable variations:**
- "How much $x$ and $y$ co-vary, scaled by how much $x$ varies." ✓
- "The covariance of $x$ and $y$ per unit of variance in $x$." ✓
- "How much $y$ changes when $x$ changes, accounting for the spread of $x$." ✓
- "The linear relationship between $x$ and $y$, normalized by the spread of $x$." ✓

**Grading:** 0–3 scale.  
- 3: Correctly explains both numerator (co-movement) and denominator (spread of $x$), or gives an equivalent correct intuition.  
- 2: Explains one part correctly (e.g., "how much $x$ and $y$ move together" but doesn't mention the denominator).  
- 1: Vague but partially correct (e.g., "how $x$ affects $y$").  
- 0: Incorrect or no answer.

**Common mistakes to watch for:**
- "It's the correlation" → No, it's covariance divided by variance. Correlation is covariance divided by the product of standard deviations. They're related but not the same.
- "It's how much $y$ changes when $x$ increases by 1" → This is the *interpretation* of $w^*$, not the meaning of the *formula*. Partial credit — the student understands the slope but not the formula's structure.

### Q4. Solution

**Geometric property guaranteed by $b^* = \bar{y} - w^*\bar{x}$:**

The best-fit line always passes through the point of means (the centroid) $(\bar{x}, \bar{y})$.

**Verification:** $\hat{y}(\bar{x}) = w^*\bar{x} + b^* = w^*\bar{x} + (\bar{y} - w^*\bar{x}) = \bar{y}$. ✓

**Acceptable variations:**
- "The line goes through the center of the data." ✓
- "The line passes through $(\bar{x}, \bar{y})$." ✓
- "The average prediction equals the average of $y$." ✓ (This is equivalent.)
- "The residuals sum to zero." ✓ (This follows from the line passing through the centroid.)

**Grading:** 0–3 scale.  
- 3: Correctly states that the line passes through $(\bar{x}, \bar{y})$ (or equivalent).  
- 2: Mentions "the center of the data" or "the mean" without being specific.  
- 1: Vague (e.g., "it centers the line").  
- 0: Incorrect or no answer.

**Common mistakes to watch for:**
- "The line passes through the origin" → No! It passes through $(\bar{x}, \bar{y})$, not $(0, 0)$. These are the same only if $\bar{x} = 0$ and $\bar{y} = 0$.
- "The line minimizes the error" → True but not what the intercept formula specifically guarantees. The slope also contributes to minimizing error.

### ★ Challenge Solution

**(a)** If $\text{Cov}(x, y) = 0$, then $w^* = 0 / \text{Var}(x) = 0$. The model predicts $\hat{y} = b^* = \bar{y} - 0 \cdot \bar{x} = \bar{y}$ for all $x$. The model gives up and predicts the mean of $y$ regardless of $x$.

**(b)** No! $w^* = 0$ means there is no *linear* relationship. There could be a nonlinear relationship that linear regression cannot capture. For example, if $y = x^2$ and $x$ is symmetric around 0, then $\text{Cov}(x, y) = 0$ but $y$ is completely determined by $x$.

**(c) Concrete example:** Let $x$ take values $\{-2, -1, 0, 1, 2\}$ and $y = x^2$ take values $\{4, 1, 0, 1, 4\}$.

- $\bar{x} = 0$, $\bar{y} = 2$
- $\text{Cov}(x, y) = \frac{1}{5}\sum_i (x_i - 0)(y_i - 2) = \frac{1}{5}[(-2)(2) + (-1)(-1) + (0)(-2) + (1)(-1) + (2)(2)] = \frac{1}{5}[-4 + 1 + 0 - 1 + 4] = 0$

So $\text{Cov}(x, y) = 0$, meaning $w^* = 0$ and linear regression predicts $\hat{y} = 2$ for all $x$. But $y$ is perfectly determined by $x$ via $y = x^2$! Linear regression completely misses the relationship because it's only looking for *linear* patterns.

**The lesson:** Linear regression can only find linear relationships. A zero slope means "no linear relationship," NOT "no relationship." This is why the choice of hypothesis space matters — if the true relationship is nonlinear, you need a more expressive model (polynomial features, neural networks, etc.).

**Grading:** Bonus — not counted toward the base score.  
- "Excellent": All three parts correct, with a valid example.  
- "Good attempt": 1–2 parts correct, or correct intuition without a concrete example.  
- "Attempted": Tried but mostly incorrect.

---

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Compute OLS coefficients by hand | | |
| Q2 | Why squared error | | |
| Q3 | Intuition for slope formula | | |
| Q4 | Intercept → centroid property | | |
| ★ | Cov = 0 ≠ no relationship | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Can students compute $w^*$ and $b^*$ by hand? → If not, practice more worked examples. This is the core skill of Week 2.
- [ ] Do students center the data correctly (subtract the mean) before computing variance and covariance? → This is the most common error. Re-emphasize in Session 2.
- [ ] Do students understand WHY the line passes through the centroid? → If not, review the $b^*$ derivation at the start of Session 2.
- [ ] Did any students attempt the challenge? How did they do? → Note for differentiation. The challenge tests understanding of linear vs. nonlinear relationships — a key conceptual point.

### Topics to spiral back in future quizzes:

- Computing OLS coefficients → spiral back in Week 2 S2 quiz (ridge regression computation)
- Why squared error → spiral back in Week 5 (probabilistic derivation)
- Centroid property → spiral back in Week 8 (matrix projection)
- Cov = 0 ≠ independence → spiral back in Week 5 (probability, independence)
