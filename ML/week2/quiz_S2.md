# Week 2, Session 2 — End-of-Day Quiz

> **Time:** 10 minutes  
> **Topics:** Overfitting with polynomials, ridge regression, overfitting-underfitting tradeoff, R², geometric properties  
> **Format:** 5 questions + 1 challenge, mix of conceptual, multiple choice, and calculation  
> **Closed notes**  
> **Calculators allowed**  
> **Note:** Q5 is a spiral-back question from Session 1.

---

## Questions

**Q1. [Conceptual — 2 min]**

You have 6 data points and fit a degree-5 polynomial. The training error is zero.

(a) Is this a good model? Explain why or why not.  
(b) What would happen if you had 600 data points instead and still fit a degree-5 polynomial?

**Q2. [Multiple choice — 1 min]**

Ridge regression modifies the OLS solution by:

(a) Adding $\lambda$ to the numerator: $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y) + \lambda}{\text{Var}(x)}$  
(b) Adding $\lambda$ to the denominator: $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$  
(c) Multiplying the OLS slope by $\lambda$: $w^*_{\text{ridge}} = \lambda \cdot \frac{\text{Cov}(x,y)}{\text{Var}(x)}$  
(d) Setting $w = 0$ when $|w| < \lambda$

Justify your answer in one sentence.

**Q3. [Conceptual — 2 min]**

Complete the following table by filling in "High" or "Low" for each cell:

| Model | Training error | Test error | What's happening |
|-------|---------------|------------|-------------------|
| Constant ($\hat{y} = \bar{y}$) | | | Underfitting |
| Linear ($\hat{y} = wx + b$) | | | Good fit |
| Degree-$(n{-}1)$ polynomial | | | Overfitting |
| Linear + ridge ($\lambda$ moderate) | | | Balanced |

**Q4. [Calculation — 3 min]**

Using the ice cream data from Session 1: $\bar{x} = 25$, $\bar{y} = 220$, $\text{Var}(x) = 50$, $\text{Cov}(x,y) = 500$.

The OLS model is $\hat{y} = 10x - 30$ with $\text{SS}_{\text{res}} = 600$ and $\text{SS}_{\text{tot}} = 25600$.

(a) Compute $R^2$ for the OLS model and interpret it in one sentence.  
(b) Compute the ridge slope $w^*_{\text{ridge}}$ with $\lambda = 200$.  
(c) Does the ridge line still pass through the centroid $(\bar{x}, \bar{y}) = (25, 220)$? Explain why or why not.

**Q5. [Spiral-back — 1 min]**

In Session 1, we derived $b^* = \bar{y} - w^*\bar{x}$. We said this means the best-fit line passes through a specific point.

(a) What point does the line pass through?  
(b) What happens to the slope $w^*$ if $\text{Var}(x) = 0$ (all $x$-values are the same)? Why?

**★ [Challenge — optional, 2 min]**

Consider the variance decomposition: $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$, where $\hat{y}_i = w^*x_i + b^*$ are predictions and $e_i = y_i - \hat{y}_i$ are residuals. This holds for OLS but NOT for ridge regression.

(a) Why does the decomposition fail for ridge? Which step breaks down?  
*(Hint: The decomposition relies on $\text{Cov}(\hat{y}, e) = 0$. Is this still true for ridge?)*

(b) Does this mean $R^2$ is meaningless for ridge? How should we interpret $R^2$ when using ridge?

---
---

## Solutions

### Q1. Solution

**(a)** No, this is not a good model. With 6 data points and a degree-5 polynomial (6 parameters), the model has enough flexibility to pass through every point exactly, including any noise. The polynomial will likely oscillate wildly between data points, making terrible predictions on new data. This is overfitting: zero training error, but high test error.

**(b)** With 600 data points and a degree-5 polynomial (6 parameters), the model is now heavily under-parameterized relative to the data (6 parameters for 600 data points). It can no longer pass through every point. The polynomial will fit the overall trend, and the training error will reflect the true pattern plus irreducible noise. The same model that overfit with 6 data points would likely generalize well with 600 data points.

**The lesson:** Whether a model overfits depends on the ratio of model complexity to data size, not on the model alone.

**Grading:** 0–3 scale.  
- 3: Both parts correct with clear explanation mentioning the parameter-to-data ratio.  
- 2: Both parts correct but explanation is vague, or one part fully correct.  
- 1: One part correct, or correct intuition ("overfitting") without explanation.  
- 0: Says the degree-5 model is good, or no answer.

**Common mistakes to watch for:**
- Saying the degree-5 polynomial is "good because training error is zero" → This is the Week 1 trap! Zero training error ≠ good model. Re-emphasize.
- Saying "more data would make it overfit more" → No, more data relative to parameters REDUCES overfitting. The same degree-5 polynomial with 600 points is well-constrained.

### Q2. Solution

**Answer: (b)** Adding $\lambda$ to the denominator: $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$.

**Justification:** Ridge regression adds a penalty $\lambda w^2$ to the loss. When we complete the square, this penalty adds $\lambda$ to the $\text{Var}(x)$ coefficient (the $w^2$ term), inflating the denominator and shrinking the slope toward zero. When $\lambda = 0$, ridge reduces to OLS.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning the penalty inflating the denominator.  
- 2: Correct answer, partial justification (e.g., "it shrinks the slope" without explaining why).  
- 1: Wrong answer but some correct reasoning.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a): Students may think $\lambda$ is added to the numerator. This would INCREASE the slope, which is the opposite of what ridge does. Ridge SHRINKS the slope.
- Choosing (c): Students may think ridge multiplies by $\lambda$. This is close in spirit (scaling the slope) but wrong in form. The relationship between OLS and ridge slopes is $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$, which is a multiplicative shrinkage, but it's not $\lambda$ times the OLS slope.
- Choosing (d): This describes a soft-thresholding operator (related to lasso), not ridge. Ridge never sets $w$ to exactly zero (for finite $\lambda$).

### Q3. Solution

| Model | Training error | Test error | What's happening |
|-------|---------------|------------|-------------------|
| Constant ($\hat{y} = \bar{y}$) | **High** | **High** | Underfitting |
| Linear ($\hat{y} = wx + b$) | **Moderate/Low** | **Moderate/Low** | Good fit |
| Degree-$(n{-}1)$ polynomial | **Zero (Low)** | **High** | Overfitting |
| Linear + ridge ($\lambda$ moderate) | **Moderate** | **Moderate (or Low)** | Balanced |

**Key distinctions to look for:**
- Underfitting: BOTH training and test error are high. The model is too simple.
- Overfitting: Training error is LOW (or zero), but test error is HIGH. The model fits noise.
- Good fit / balanced: Training and test error are both moderate and similar. The model captures the signal without fitting noise.

**Grading:** 0–3 scale.  
- 3: All 8 cells correct (training + test for all 4 models).  
- 2: 6–7 cells correct.  
- 1: 3–5 cells correct.  
- 0: 0–2 cells correct.

**Common mistakes to watch for:**
- Putting "Low" for the training error of the constant model → No, the constant model has HIGH training error. It can't capture the trend.
- Putting "Low" for the test error of the degree-$(n{-}1)$ polynomial → No, the test error is HIGH because the model overfit.
- Putting "Zero" for ridge training error → No, ridge has nonzero training error (the penalty prevents a perfect fit). Ridge's training error is HIGHER than OLS — that's the point.

### Q4. Solution

**(a) Compute $R^2$:**

$$R^2 = 1 - \frac{\text{SS}_{\text{res}}}{\text{SS}_{\text{tot}}} = 1 - \frac{600}{25600} = 1 - 0.0234 = 0.977$$

**Interpretation:** The model explains 97.7% of the variance in ice cream sales. (Or equivalently: 97.7% of the variation in $y$ is accounted for by the linear model.)

**(b) Compute ridge slope:**

$$w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda} = \frac{500}{50 + 200} = \frac{500}{250} = 2$$

**(c) Does the ridge line pass through the centroid?**

Yes. The ridge intercept is $b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \cdot \bar{x} = 220 - 2 \cdot 25 = 220 - 50 = 170$.

Check: $\hat{y}(25) = 2 \cdot 25 + 170 = 50 + 170 = 220 = \bar{y}$. ✓

The ridge line passes through the centroid because the penalty is on $w$ (the slope), not on $b$ (the intercept). The intercept is still chosen optimally, and the optimal intercept always places the line through $(\bar{x}, \bar{y})$.

**Grading:** 0–3 scale.  
- 3: All three parts correct with correct calculations and interpretation.  
- 2: Two parts correct, or correct method with minor arithmetic errors.  
- 1: One part correct.  
- 0: No correct work.

**Common mistakes to watch for:**
- **R² interpretation:** Saying "the model is 97.7% accurate" → No. R² is the fraction of variance explained, not accuracy. "Accuracy" is a classification metric. The correct interpretation is "the model explains 97.7% of the variance in $y$."
- **Ridge computation:** Using $\lambda$ in the numerator instead of the denominator. → Re-emphasize: $\lambda$ goes in the denominator (it inflates the denominator, shrinking the slope).
- **Centroid question:** Saying "no, ridge doesn't pass through the centroid because it's different from OLS" → Wrong. The ridge line DOES pass through the centroid. The penalty is on $w$, not $b$. The intercept formula $b^* = \bar{y} - w\bar{x}$ holds for ridge too (with the ridge slope).

### Q5. Solution (Spiral-Back)

**(a)** The best-fit line passes through the point of means (the centroid) $(\bar{x}, \bar{y})$.

**(b)** If $\text{Var}(x) = 0$, the slope $w^* = \text{Cov}(x,y) / \text{Var}(x)$ involves division by zero — it is undefined. This makes sense: if all $x$-values are the same, there's no variation in $x$ to explain variation in $y$. You can't fit a line to data where all inputs are identical. The model degenerates to predicting $\bar{y}$.

**Grading:** 0–3 scale.  
- 3: Both parts correct.  
- 2: One part fully correct, or both parts partially correct.  
- 1: One part partially correct.  
- 0: Neither part correct.

**Common mistakes to watch for:**
- Saying the line passes through the origin → No, it passes through $(\bar{x}, \bar{y})$.
- Saying $w^* = 0$ when $\text{Var}(x) = 0$ → No, it's undefined (division by zero), not zero. If anything, the model can't determine a slope at all.
- Saying "the slope doesn't exist because $x$ and $y$ are uncorrelated" → No, the slope doesn't exist because $\text{Var}(x) = 0$, regardless of the covariance. Even if $\text{Cov}(x,y) \neq 0$, the slope is undefined when $\text{Var}(x) = 0$.

### ★ Challenge Solution

**(a)** The variance decomposition $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$ relies on $\text{Cov}(\hat{y}, e) = 0$ (the predictions and residuals are uncorrelated). For OLS, this holds because the residuals are uncorrelated with $x$ (i.e., $\sum_i x_i e_i = 0$), and $\hat{y}$ is a linear function of $x$, so $\hat{y}$ and $e$ are also uncorrelated.

For ridge regression, the residuals are NOT uncorrelated with $x$. The ridge optimality condition is different: the penalty $\lambda w^2$ changes the first-order condition, so $\sum_i x_i e_i \neq 0$ in general. Since $\hat{y}$ is still a linear function of $x$, this means $\text{Cov}(\hat{y}, e) \neq 0$, and the variance decomposition fails.

**Intuition:** Ridge deliberately introduces a bias (the slope is too small). This bias creates a correlation between the predictions and the residuals — the model systematically under-predicts for large $x$ and over-predicts for small $x$ (when $w > 0$). This correlation breaks the clean decomposition.

**(b)** $R^2$ is not meaningless for ridge, but it must be interpreted differently. For OLS, $R^2 = \text{Var}(\hat{y}) / \text{Var}(y)$ (the fraction of variance explained). For ridge, this equality no longer holds because the decomposition fails.

However, the computational formula $R^2 = 1 - \text{SS}_{\text{res}} / \text{SS}_{\text{tot}}$ still makes sense: it measures how much better the ridge model is compared to the constant model $\hat{y} = \bar{y}$. It's just no longer equal to the fraction of variance explained, and it no longer equals $r^2$.

In practice, for ridge regression, $R^2$ is reported as $1 - \text{SS}_{\text{res}} / \text{SS}_{\text{tot}}$ but interpreted as "the proportion of variance in $y$ that the model accounts for" — with the understanding that this is an approximation when the model is biased.

**The lesson:** The beautiful properties of OLS (variance decomposition, $R^2 = r^2$, residuals uncorrelated with $x$) are CONSEQUENCES of the OLS optimality conditions. When you change the objective (by adding a penalty), these properties may break. Regularization trades mathematical elegance for better generalization.

**Grading:** Bonus — not counted toward base score.  
- "Excellent": Both parts correct, with clear explanation of why $\text{Cov}(\hat{y}, e) \neq 0$ for ridge.  
- "Good attempt": Correct intuition (ridge breaks the OLS properties) but incomplete explanation.  
- "Attempted": Tried but mostly incorrect.

---

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Polynomial overfitting + data size | | |
| Q2 | Ridge regression formula | | |
| Q3 | Overfitting-underfitting tradeoff table | | |
| Q4 | R² computation + ridge computation | | |
| Q5 | Spiral-back: centroid + Var(x)=0 | | |
| ★ | Variance decomposition failure for ridge | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Do students understand that zero training error ≠ good model? → If many got Q1 wrong, revisit the polynomial overfitting demo at the start of Week 3.
- [ ] Can students correctly state the ridge formula? → If Q2 scores are low, review the ridge derivation or provide a formula sheet.
- [ ] Can students fill in the overfitting-underfitting table? → If Q3 scores are low, this is a Week 1 concept that hasn't fully landed. Spiral it back again in Week 3 (polynomial overfitting, complexity dial).
- [ ] Can students compute R² and interpret it correctly? → If Q4 scores are low, practice more R² computations. Watch for "accuracy" instead of "variance explained."
- [ ] Do students remember the centroid property and the Var(x)=0 edge case? → If Q5 scores are low, review at the start of Week 3.
- [ ] Did any students attempt the challenge? The variance decomposition failure for ridge is an advanced concept. Students who get this are ready for the matrix treatment in Week 8.

### Topics to spiral back in future quizzes:

- Overfitting with polynomials → spiral back in Week 3 (polynomial overfitting in depth) and Week 10 (decision tree depth)
- Ridge regression formula → spiral back in Week 4 (cross-validation for λ selection) and Week 8 (matrix ridge)
- R² interpretation → spiral back in Week 4 (model evaluation metrics)
- Centroid property → spiral back in Week 8 (projection interpretation)
- Var(x) = 0 edge case → spiral back in Week 8 (multicollinearity, singular matrices)
- Overfitting-underfitting table → spiral back in every week (this is the central theme of the first half of the course)
