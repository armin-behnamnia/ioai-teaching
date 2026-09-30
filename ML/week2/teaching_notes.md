# Week 2 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): Scalar Linear Regression — The Model, MSE, and the OLS Solution

### Learning Objectives

By the end of this session, students should be able to:
1. Write down the linear regression model $\hat{y} = wx + b$ and explain what $w$ and $b$ mean.
2. Define Mean Squared Error (MSE) and explain why we use squared error (not absolute error).
3. Derive the optimal intercept $b^* = \bar{y} - w\bar{x}$ from scratch using only algebra (completing the square).
4. Derive the optimal slope $w^* = \text{Cov}(x,y) / \text{Var}(x)$ by substituting $b^*$ and completing the square again.
5. Compute $w^*$ and $b^*$ for a small dataset by hand.
6. Explain why the best-fit line always passes through the centroid $(\bar{x}, \bar{y})$.

### Materials Needed

- Whiteboard / blackboard with multiple sections (or a document camera)
- Desmos open in browser (for the line-fitting demo — see `visual_demos.md`)
- Printed or projected handout Sections 1–4
- Calculators available (students will be doing arithmetic)

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:08 | **Recap of Week 1 + Hook.** "Last week: framework. Today: our first real model." | See Hook section below. |
| 0:08–0:20 | **The model and MSE.** Write $\hat{y} = wx + b$. Define MSE. Why squared? | Ice cream example throughout. |
| 0:20–0:35 | **Deriving $b^*$: the intercept.** Complete the square in $b$. | This is the key algebraic derivation. Go slow. |
| 0:35–0:50 | **Deriving $w^*$: the slope.** Substitute $b^*$, center, complete the square in $w$. | Second derivation. Students may tire — keep energy up. |
| 0:50–0:65 | **Worked example: ice cream sales.** Full computation on the board. | Let students compute some steps. See Board Work section. |
| 0:65–0:72 | **Intuition for the formulas + correlation connection.** | Conceptual breather after the heavy algebra. |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S1.md`. | |

> **Note:** The two derivations (intercept and slope) are the mathematical heart of this session. If you're running short on time, trim the correlation discussion (Section 3.6 of handout) — it's enriching but not essential. Protect the derivation time.

### Hook: "What's the Best Line?" (8 min)

**Goal:** Connect Week 1's abstract framework to a concrete, solvable problem.

**Instructions:**

1. Project (or draw) 5 data points on a scatter plot: temperature vs. ice cream sales (from handout Section 4). Don't label axes yet.
2. Ask: "Last week we said ML = choose hypothesis space + choose loss + find best parameters. If our hypothesis space is *lines* $\hat{y} = wx + b$, and our loss is squared error, what are the best $w$ and $b$?"
3. Let students eyeball it. Have 2–3 students draw their best-fit line on the board. They'll disagree.
4. "Today we'll find the EXACT best line — using only algebra. No guessing, no calculus, no code. By the end of this session, you'll be able to compute the optimal line for any dataset by hand."
5. Transition: "First, let's make the problem precise."

**Common student responses to watch for:**
- "Just use a neural network." → "We will — in Week 15. But you can't appreciate what a neural network does until you understand the simplest case: a line."
- "Can't we just use Excel / a calculator to fit a line?" → "Yes, but HOW does it know? Today we derive the formula that Excel uses. Understanding the formula gives you power that using the tool doesn't."
- A student who already knows the matrix formula $\hat{\beta} = (X^T X)^{-1} X^T y$ → "Great! You know the matrix version. This week we do it scalar — one input, one output — and derive it from scratch. Can you recover the scalar formula from the matrix formula? We'll check in Week 8."

### Board Work: The Derivations (30 min total)

**This is the most important part of Session 1.** Students must see the algebra done live, step by step.

#### Part 1: Deriving $b^*$ (15 min)

**Write on the board (keep visible for the rest of the session):**

```
Model:    ŷ = wx + b
Loss:     R(w,b) = (1/n) Σ (wxᵢ + b - yᵢ)²
Goal:     find w* and b* that minimize R
```

**Key teaching moves:**

1. **Start with the intercept.** Say: "Let's first ask: for a FIXED slope $w$, what's the best intercept $b$? We'll solve this, then substitute back."

2. **Define the shorthand.** Let $\epsilon_i = wx_i - y_i$ (error without intercept). Then:
   $$R(b) = \frac{1}{n}\sum_i (\epsilon_i + b)^2$$

3. **Expand.** Write it out fully:
   $$R(b) = \frac{1}{n}\sum_i \epsilon_i^2 + 2b \cdot \frac{1}{n}\sum_i \epsilon_i + b^2$$

4. **Identify the quadratic.** Circle it: "This is $R(b) = b^2 + 2b\bar{\epsilon} + \overline{\epsilon^2}$ — a quadratic in $b$!" Write the general form $f(b) = b^2 + cb + d$ next to it, and note it's minimized at $b = -c/2$.

5. **Solve.** 
   $$b^* = -\bar{\epsilon} = -\frac{1}{n}\sum_i (wx_i - y_i) = \bar{y} - w\bar{x}$$

6. **The punchline (box it):** $b^* = \bar{y} - w\bar{x}$. "The best-fit line ALWAYS passes through the point of means $(\bar{x}, \bar{y})$. No matter what slope you pick, the best intercept places the line through the center of the data."

**Common misconceptions to address proactively:**
- **"Why can't we just set $b = 0$?"** → Because the data may not pass through the origin. The intercept lets the line float up and down to the right height.
- **"Is $\bar{\epsilon}$ the same as $\bar{y} - w\bar{x}$?"** → Yes, by linearity of the mean. Walk through: $\bar{\epsilon} = \frac{1}{n}\sum_i (wx_i - y_i) = w\bar{x} - \bar{y}$, so $b^* = -\bar{\epsilon} = \bar{y} - w\bar{x}$.

#### Part 2: Deriving $w^*$ (15 min)

**Key teaching moves:**

1. **Substitute $b^*$ back.** The prediction becomes $\hat{y}_i = w(x_i - \bar{x}) + \bar{y}$. The error becomes $w\tilde{x}_i - \tilde{y}_i$ where $\tilde{x}_i = x_i - \bar{x}$, $\tilde{y}_i = y_i - \bar{y}$.

2. **"Centering" — name it.** Write: "By substituting the optimal $b^*$, we've **centered** the data. The problem reduces to fitting a line through the origin in centered coordinates." This is a key conceptual move.

3. **Expand the loss:**
   $$R(w) = \frac{1}{n}\sum_i (w\tilde{x}_i - \tilde{y}_i)^2 = w^2 \cdot \underbrace{\frac{1}{n}\sum_i \tilde{x}_i^2}_{\text{Var}(x)} - 2w \cdot \underbrace{\frac{1}{n}\sum_i \tilde{x}_i\tilde{y}_i}_{\text{Cov}(x,y)} + \underbrace{\frac{1}{n}\sum_i \tilde{y}_i^2}_{\text{Var}(y)}$$

4. **Identify the quadratic.** "This is $R(w) = Aw^2 - Bw + C$ where $A = \text{Var}(x)$, $B = 2\text{Cov}(x,y)$, $C = \text{Var}(y)$. Minimized at $w = B/(2A)$."

5. **Solve (box it):**
   $$w^* = \frac{\text{Cov}(x,y)}{\text{Var}(x)}$$

6. **Name it.** "This is the **Ordinary Least Squares (OLS)** solution. We derived it using only: expanding a square, taking a mean, and minimizing a quadratic. No calculus."

**Common misconceptions to address proactively:**
- **"I thought you needed derivatives to minimize things."** → Not for quadratics! A quadratic $ax^2 + bx + c$ is minimized at $x = -b/(2a)$ — pure algebra. We're exploiting the fact that MSE is a quadratic in $w$ and $b$.
- **"What if $\text{Var}(x) = 0$?"** → Division by zero! The slope is undefined. This means: if all $x$-values are the same, you can't fit a line (there's no variation in $x$ to explain variation in $y$). The model degenerates to predicting $\bar{y}$.
- **"Is $\text{Cov}(x,y)$ the same as correlation?"** → No. Covariance has units (product of $x$ and $y$ units); correlation is unitless (normalized covariance). We'll connect them in Section 3.6.

### Board Work: The Worked Example (15 min)

**Use the ice cream sales data from handout Section 4.** This is the payoff — students see the formulas produce a concrete answer.

**Key teaching moves:**

1. **Set up the table.** Draw the 5-row data table on the board. Write the formulas for $\bar{x}$, $\bar{y}$, $\text{Var}(x)$, $\text{Cov}(x,y)$ at the top.

2. **Let students compute.** After setting up the table, ask: "What's $\bar{x}$?" Let them calculate. "What's $\bar{y}$?" etc. Don't do all the arithmetic yourself — keep them engaged.

3. **Build the centered table.** This is the key computational device. Write the table with columns $\tilde{x}_i$, $\tilde{y}_i$, $\tilde{x}_i^2$, $\tilde{x}_i\tilde{y}_i$. Fill it in row by row.

4. **Compute the answer.** $w^* = 500/50 = 10$, $b^* = 220 - 250 = -30$. The model is $\hat{y} = 10x - 30$.

5. **Interpret.** "For each additional degree, sales go up $10. At 0°C, the model predicts -$30. Does that make sense?" → No! This is a limitation of linear models outside the data range. The model is only reliable within the range of the training data (15–35°C).

6. **Verify.** Show that $\hat{y}(25) = 220 = \bar{y}$. ✓ The line passes through the centroid.

**Common mistakes students make during the computation:**
- Forgetting to center (subtracting the mean) before computing variance and covariance. → Emphasize: $\text{Var}(x) = \frac{1}{n}\sum_i (x_i - \bar{x})^2$, NOT $\frac{1}{n}\sum_i x_i^2$.
- Mixing up the numerator and denominator of $w^*$. → Mnemonic: "Cov over Var" — the thing being predicted ($y$) is in the numerator.
- Sign errors in centered values. → When $x_i < \bar{x}$, $\tilde{x}_i$ is negative. Students sometimes drop the sign.

### Discussion Prompts

Use these at the indicated times to keep students engaged:

1. **(After defining MSE):** "Why not use absolute error $|\hat{y} - y|$ instead of squared error $(\hat{y} - y)^2$? What would be different?" — Students may say "squared penalizes large errors more." That's true. The deeper answer: squared error gives a unique, closed-form solution. Absolute error doesn't (it gives a median-like solution that's harder to compute). Also: Gaussian noise (Week 5).

2. **(After deriving $b^*$):** "If I told you the best-fit line always passes through $(\bar{x}, \bar{y})$, could you fit a line with only ONE parameter instead of two?" — Yes! If you fix the line to pass through the centroid, you only need to choose the slope. The intercept is determined. This is what we did: solve for $b^*$ first, reducing to a one-parameter problem.

3. **(After the worked example):** "The model predicts -$30 at 0°C. Is the model wrong?" — It's right *within the data range* but wrong *outside* it. This is the problem of **extrapolation**. Linear models are only trustworthy near the training data. Connect to Week 1: the hypothesis space (lines) is an assumption that may not hold everywhere.

4. **(After the correlation connection):** "If $r = 0$ (no correlation), what does the model predict?" → $w^* = 0$, so $\hat{y} = \bar{y}$ for all $x$. The model gives up and predicts the mean. "If $x$ tells you nothing about $y$, the best prediction is just the average of $y$."

### Things NOT to Cover (Save for Later)

| Topic | When |
|-------|------|
| Matrix formulation of OLS | Week 8 |
| Gradient descent on MSE | Week 6 |
| Probabilistic derivation (Gaussian noise → MSE) | Week 5 |
| Bias-variance decomposition | Week 5 |
| Multiple regression (multiple inputs) | Week 8 |
| Cross-validation for model selection | Week 4 |
| Weighted least squares | Week 8 (or not at all) |

**Resist the urge to use calculus.** The whole point of this week is that students can derive OLS with algebra alone. If a student asks "can't we just take the derivative?", say: "Yes, and that's the standard approach. But I want you to see that it's just minimizing a quadratic — something you can do with algebra. The calculus approach generalizes to harder problems, which we'll see in Week 6."

---

## Session 2 (80 min): Overfitting, Regularization, Geometry, and R²

### Learning Objectives

By the end of this session, students should be able to:
1. Explain how polynomial regression can overfit (degree $n-1$ through $n$ points).
2. State the ridge regression objective and solution in scalar form.
3. Explain how $\lambda$ controls the overfitting-underfitting tradeoff.
4. Describe the geometric meaning of the OLS solution (centroid, zero-sum residuals, uncorrelated residuals).
5. Compute and interpret $R^2$ for a linear model.
6. Preview the probabilistic connection (MSE ↔ Gaussian noise) at an intuitive level.

### Materials Needed

- Desmos with polynomial overfitting demo and ridge demo pre-loaded (see `visual_demos.md`)
- Printed or projected handout Sections 5–8
- Paper discussion prompts for Domingos paper (if assigning — see `suggested_paper.md`)

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** Quick: "What are $w^*$ and $b^*$?" | |
| 0:05–0:10 | **Paper discussion (if assigned).** Brief — see `suggested_paper.md`. | Optional. Only if students read the Domingos paper. |
| 0:10–0:25 | **Overfitting with polynomials.** Visual demo + board work. | See Demo 2 in `visual_demos.md`. |
| 0:25–0:45 | **Ridge regression.** Motivation, objective, scalar solution, ice cream example. | The main new content of Session 2. |
| 0:45–0:52 | **L1 / Lasso brief mention.** | 5 min max — just the idea. |
| 0:52–0:65 | **Geometric perspective + R².** Centroid, residuals, R² computation. | |
| 0:65–0:72 | **Probabilistic preview + tradeoff recap.** | Intuition only — no probability required. |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S2.md`. | |

> **Note:** This session is dense. If running long, trim the L1 mention (it's revisited in Week 8) or the probabilistic preview (it's fully developed in Week 5). Protect the ridge regression time.

### Visual Demo: Polynomial Overfitting (15 min)

**This is the centerpiece of Session 2.** Use the Desmos demo from `visual_demos.md` (Demo 2).

**Key teaching moves:**

1. **Show the degree-1 fit.** "This is what we derived yesterday. A line with 2 parameters. Training error is small but nonzero."

2. **Show the degree-4 fit.** With 5 data points, a degree-4 polynomial passes through every point. Training error = 0. "Is this better?" → No! The curve oscillates wildly.

3. **Ask the key question:** "Which model would you trust to predict $y$ at a new $x$-value?" → The line. "Why?" → The polynomial fits noise; the line captures the trend.

4. **The lesson:** Overfitting depends on the ratio of **parameters to data**. A 2-parameter line with 100 data points rarely overfits. A 100-parameter polynomial with 100 data points overfits badly.

5. **Connect to Week 1:** "Last week we saw overfitting qualitatively. Today we see it in the simplest concrete model: linear regression with polynomial features. And today we'll learn a concrete fix: regularization."

### Board Work: Ridge Regression (20 min)

**This is the main new content of Session 2.**

**Draw on the board:**

```
OLS Loss:      R(w,b) = (1/n) Σ (wxᵢ + b - yᵢ)²
Ridge Loss:    R_ridge(w,b) = (1/n) Σ (wxᵢ + b - yᵢ)² + λw²
                                                        ↑ penalty
```

**Key teaching moves:**

1. **Motivate.** "When we use polynomial features, the weights can grow large to chase noise. Ridge regression adds a penalty: don't let $w$ get too big."

2. **The objective.** Write the ridge loss. Explain the two terms: "fit the data" (MSE) + "keep the weight small" ($\lambda w^2$). The $\lambda$ controls the balance.

3. **The solution (give, don't derive fully).** "Using the same completing-the-square approach, the ridge solution is:"
   $$w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$$
   "Compare to OLS: the only difference is the $+\lambda$ in the denominator."

4. **The $\lambda$ table.** Draw the table from handout Section 6.4 on the board and fill it in WITH students:
   - $\lambda = 0$: OLS (no regularization)
   - $\lambda$ small: slight shrinkage
   - $\lambda$ moderate: sweet spot
   - $\lambda \to \infty$: $w \to 0$, predict $\bar{y}$ (extreme underfitting)

5. **Ice cream example.** With $\lambda = 25$: $w^*_{\text{ridge}} = 500/75 \approx 6.67$ vs. OLS $w^* = 10$. "The ridge slope is smaller — more conservative. It predicts less dramatic sales increases."

6. **The intercept.** Note that $b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \bar{x}$. The ridge line ALSO passes through the centroid! (The penalty is on $w$, not $b$.)

**Common misconceptions to address proactively:**
- **"Does ridge always make the model better?"** → No. If $\lambda$ is too large, the model underfits (predicts $\bar{y}$). Ridge trades training error for stability. It helps only if the OLS model was overfitting.
- **"Why penalize $w^2$ and not $|w|$?"** → That's L1 (lasso), which we'll mention next. L2 (ridge) is smoother and has a closed-form solution. L1 doesn't (the absolute value has a corner).
- **"Why don't we penalize $b$?"** → Good question! In practice, we often don't penalize the intercept because it represents the baseline, not the sensitivity. The slope $w$ is what determines how much the model reacts to $x$ — that's what we want to control.
- **"How do we choose $\lambda$?"** → Cross-validation. We'll learn this in Week 4. For now, treat $\lambda$ as a knob.

### Board Work: L1 / Lasso (5 min — Brief)

**Keep this to 5 minutes.** The goal is awareness, not mastery.

1. **Write the lasso objective:**
   $$R_{\text{lasso}}(w,b) = \frac{1}{n}\sum_i (wx_i + b - y_i)^2 + \lambda |w|$$

2. **Key difference from ridge:** L1 penalizes $|w|$ (not $w^2$). The absolute value has a corner at $w = 0$. This makes the solution more likely to set $w$ to **exactly zero** — performing feature selection.

3. **Scalar case:** "With one feature, lasso either keeps it ($w \neq 0$) or kills it ($w = 0$). In the multi-feature case (Week 8), lasso's geometry — a diamond vs. a circle — makes sparsity much more likely. We'll revisit this."

4. **Don't derive the lasso solution.** It doesn't have a clean closed form (because of the corner). Just state the qualitative behavior.

### Board Work: Geometric Perspective and R² (13 min)

**Part 1: The Centroid (3 min)**

Recap: $b^* = \bar{y} - w^*\bar{x}$ means the line passes through $(\bar{x}, \bar{y})$. Draw this on a scatter plot. Mark the centroid with a dot. Draw the line through it.

**Part 2: Residuals (5 min)**

1. **Define residuals:** $e_i = y_i - \hat{y}_i$.
2. **State the two properties:**
   - $\sum_i e_i = 0$ (residuals sum to zero)
   - $\sum_i x_i e_i = 0$ (residuals uncorrelated with $x$)
3. **Explain the first.** "The line is positioned so positive and negative errors exactly balance. This follows from the intercept formula."
4. **Explain the second (intuition).** "The line captures ALL the linear relationship between $x$ and $y$. What's left (the residuals) has no linear pattern. It's noise from the linear perspective."
5. **Preview Week 8.** "In matrix notation, these two properties become: the residual vector is perpendicular to the column space. Same idea, higher-dimensional language."

**Part 3: R² (5 min)**

1. **Write the formula:**
   $$R^2 = 1 - \frac{\text{SS}_{\text{res}}}{\text{SS}_{\text{tot}}}$$
2. **Define the terms.** $\text{SS}_{\text{res}} = \sum_i (y_i - \hat{y}_i)^2$ (unexplained), $\text{SS}_{\text{tot}} = \sum_i (y_i - \bar{y})^2$ (total).
3. **Interpret.** "$R^2$ is the fraction of variance in $y$ explained by the model. $R^2 = 1$ means perfect. $R^2 = 0$ means no better than predicting $\bar{y}$."
4. **Compute for ice cream.** $R^2 = 1 - 600/25600 = 0.977$. "The model explains 97.7% of the variance. Excellent fit."
5. **Connect to correlation.** "$R^2 = r^2$. The square of the correlation coefficient. This is the link between correlation (a statistical concept) and regression (a modeling concept)."

### The Probabilistic Preview (5 min — Brief)

**Don't spend more than 5 minutes.** The goal is to plant a seed.

**Say:**

"You might wonder: why squared error? Why not absolute error? There's a deep reason.

Imagine the true relationship is $y = wx + b + \text{noise}$. If the noise tends to be small and symmetric — equally likely to be positive or negative — then the 'most likely' value of $w$ given the data turns out to be exactly the MSE minimizer.

In other words: **MSE is not arbitrary.** It's the loss function you get when you assume the noise follows a bell curve (Gaussian distribution). We'll prove this in Week 5.

Similarly, ridge regression has a probabilistic meaning: it corresponds to a prior belief that the weights should be small. We'll formalize this too.

**For now:** The choice of loss function and regularizer encode assumptions about how the data was generated. Different assumptions → different loss functions."

**Do NOT derive anything.** Just state the connection and create anticipation for Week 5.

### Wrapping Up Session 2

End with:

"Today we've seen our first complete ML model. We derived the OLS solution from scratch using algebra. We saw overfitting with polynomials and learned ridge regression as a fix. We discovered the geometric beauty of OLS: the line through the centroid, residuals summing to zero, R² as explained variance.

Next week: Overfitting & Regularization — Going Deeper. We'll see polynomial overfitting in full detail, the L1 vs. L2 geometry, the complexity dial that unifies all ML models, and the generalization gap made precise.

Before you leave: take the quiz."

### Anticipated Questions from Students

| Question | How to Answer |
|----------|--------------|
| "Why is it called 'regression'?" | Francis Galton (1886) studied how tall parents' children tend to "regress" toward the average height. The term stuck. It has nothing to do with the math — it's historical. (30 seconds.) |
| "Can linear regression handle nonlinear data?" | Not directly — but if you transform the features (e.g., add $x^2, x^3$), you can fit curves. That's polynomial regression, which we saw today. The model is linear in the parameters, even if it's nonlinear in $x$. (1 min.) |
| "What if the relationship isn't linear at all?" | Then linear regression will have high bias (underfit). You need a more complex model: polynomial features, or a neural network, or k-NN. We'll see these in coming weeks. (30 sec.) |
| "Why don't we penalize $b$?" | The intercept is a baseline, not a sensitivity. We want to control how much the model reacts to $x$ (the slope $w$), not where the line sits vertically (the intercept $b$). In practice, the intercept is usually not penalized. (30 sec.) |
| "Is ridge always better than OLS?" | No! If the true relationship is linear and there's no noise, OLS is perfect and ridge makes it worse (by shrinking the slope unnecessarily). Ridge helps when OLS overfits — i.e., when there's noise or too many features. (1 min.) |
| "How do you choose $\lambda$?" | Cross-validation. We split the data, try different $\lambda$ values, and pick the one with the best validation error. We'll learn this in Week 4. For now, treat $\lambda$ as a knob. (30 sec.) |
| "What's the difference between $R^2$ and $r$?" | $R^2 = r^2$. $r$ is the correlation coefficient (ranges from -1 to 1, tells direction and strength). $R^2$ is its square (ranges from 0 to 1, tells fraction of variance explained). In simple linear regression, they're the same thing. (30 sec.) |
| A sharp student asks about the matrix formula $\hat{\beta} = (X^TX)^{-1}X^Ty$ | "Excellent — you know the matrix version. In Week 8, we'll derive it and show it reduces to our scalar formulas when there's one input. Can you verify that the matrix formula gives $w^* = \text{Cov}/\text{Var}$ in the scalar case? Try it." Write it down as a challenge. |
| "What if there are outliers?" | MSE is sensitive to outliers (squaring amplifies large errors). Alternatives: absolute error (more robust) or Huber loss (hybrid). The handout's E11 covers this. We'll discuss robust regression later. (30 sec.) |

### Differentiation Notes

**For struggling students:**
- The derivations in Session 1 are the biggest barrier. After class, offer to go through the completing-the-square steps one more time. Focus them on the *results* ($w^* = \text{Cov}/\text{Var}$, $b^* = \bar{y} - w\bar{x}$) rather than the derivations. They can use the formulas even if they can't derive them yet.
- The worked example is the most concrete part. Encourage struggling students to redo it themselves with the handout. Practice with the exercises (E1) builds fluency.
- Reassure them: "The algebra looks intimidating, but it's just two tools: expanding a square and minimizing a quadratic. If you can do $(a+b)^2 = a^2 + 2ab + b^2$, you can follow this."

**For advanced students:**
- Redirect them to the ★ exercises (E8–E11) in the handout. E8 (prove residuals are uncorrelated with $x$) and E9 (variance decomposition) are excellent.
- If they already know the matrix formula, ask them to derive the scalar formula from it as a check. "Can you show that $(X^TX)^{-1}X^Ty$ reduces to $\text{Cov}(x,y)/\text{Var}(x)$ when $X$ has one column?"
- In class, direct computational questions to struggling students and conceptual/probing questions to advanced students. Example: "Compute $w^*$ for this data" (anyone) → "Why does the ridge solution still pass through the centroid?" (advanced).
- If a student mentions gradient descent, say: "That's an iterative method for minimizing the loss. We derived the closed form today — we can find the exact minimum without iteration. Gradient descent is for when there's no closed form. We'll see it in Week 6."

---

## Challenge Questions for Advanced Students

> **How to use these:** Give these to sharp students *during* class when they finish an activity early, or as "think about this while I explain the basics to others" prompts. They are NOT extra homework — they are conversation starters. Follow up with these students individually or in a small group during breaks or after class. The goal is to keep them intellectually hungry without derailing the class pace.
>
> **Delivery:** Write the question on a sticky note, slip it to the student, or display it on a side board. Say: "While we review [topic], think about this. Let's discuss after class or during the break."
>
> **Principle:** Every challenge is tied to a Week 2 concept but pushes *deeper* — either toward a topic we'll cover later (creating anticipation) or toward a subtlety that most students won't notice (building analytical thinking).

---

### Session 1 Challenges

**Challenge 2-1A: No-Intercept Regression**
*(Give after deriving $b^*$ — around minute 40)*

> We derived $b^* = \bar{y} - w\bar{x}$ by fixing $w$ and optimizing $b$. Now consider the model $\hat{y} = wx$ (no intercept). 
>
> **Question:** Derive the optimal $w^*$ for this model using the same algebraic approach (complete the square). You should get $w^* = \frac{\sum_i x_i y_i}{\sum_i x_i^2}$. When does this differ from the OLS solution with intercept? Give a concrete numerical example where the two give very different answers.

**Instructor notes (don't share with student yet):**
- Without the intercept, you can't center the data. The loss is $R(w) = \frac{1}{n}\sum_i (wx_i - y_i)^2 = w^2 \frac{1}{n}\sum_i x_i^2 - 2w \frac{1}{n}\sum_i x_i y_i + \frac{1}{n}\sum_i y_i^2$. Minimized at $w^* = \frac{\sum_i x_i y_i}{\sum_i x_i^2}$.
- This differs from OLS whenever the best-fit line doesn't pass through the origin — i.e., almost always. Example: the ice cream data. OLS gives $w = 10, b = -30$. No-intercept gives $w = \frac{15\cdot120 + 20\cdot180 + 25\cdot200 + 30\cdot280 + 35\cdot320}{15^2 + 20^2 + 25^2 + 30^2 + 35^2} = \frac{27000}{3750} = 7.2$. Very different slope!
- This connects to the handout's E10. The no-intercept model forces the line through the origin, which is a strong (and often wrong) assumption.
- **Follow-up:** "When would the no-intercept model be appropriate?" → When you have a physical reason to believe the relationship passes through the origin (e.g., $y$ = distance traveled, $x$ = time, starting from rest).

---

**Challenge 2-1B: The Variance Decomposition**
*(Give after deriving $w^*$ — around minute 50)*

> We showed that the best-fit line passes through $(\bar{x}, \bar{y})$ and the residuals $e_i = y_i - \hat{y}_i$ sum to zero. 
>
> **Question:** Prove that $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$ — the total variance of $y$ equals the explained variance plus the unexplained variance. 
> *(Hint: First show that $\text{Cov}(\hat{y}, e) = 0$ using the fact that residuals are uncorrelated with $x$. Then use $\text{Var}(A + B) = \text{Var}(A) + \text{Var}(B) + 2\text{Cov}(A, B)$.)*

**Instructor notes:**
- Key steps: (1) Since $\hat{y}_i = w^* x_i + b^*$ is a linear function of $x$, and $\sum_i x_i e_i = 0$ (residuals uncorrelated with $x$), we have $\sum_i \hat{y}_i e_i = 0$ (residuals uncorrelated with predictions). (2) Since $y = \hat{y} + e$ and $\text{Cov}(\hat{y}, e) = 0$, we get $\text{Var}(y) = \text{Var}(\hat{y} + e) = \text{Var}(\hat{y}) + \text{Var}(e)$.
- This is the variance decomposition that makes $R^2$ work: $R^2 = \text{Var}(\hat{y}) / \text{Var}(y) = 1 - \text{Var}(e)/\text{Var}(y)$.
- **Follow-up:** "This decomposition only works for OLS. Does it work for ridge regression?" → Not exactly! Ridge residuals don't satisfy $\sum_i x_i e_i = 0$ (because the penalty changes the optimality condition). So $R^2$ for ridge is defined differently. Seeds Week 8 discussion.

---

**Challenge 2-1C: The Gauss-Markov Theorem (Intuition)**
*(Give after the worked example — around minute 65)*

> We chose MSE because it's differentiable and has a unique solution. But is OLS the "best" estimator? 
>
> **Question:** Among all **unbiased** linear estimators (estimators of the form $\hat{w} = \sum_i c_i y_i$ for some weights $c_i$ that don't depend on $y$), OLS has the **lowest variance**. This is the Gauss-Markov theorem. Can you give an intuitive argument for why this might be true? Why would penalizing the slope (ridge) NOT satisfy the conditions of this theorem?

**Instructor notes:**
- The Gauss-Markov theorem states that OLS is the Best Linear Unbiased Estimator (BLUE). "Best" = lowest variance.
- Intuition: OLS uses all the information in the data optimally (via the projection/orthogonality conditions). Any other linear unbiased estimator uses the information less efficiently.
- Ridge regression is NOT unbiased — it's biased (the shrinkage pulls the estimate toward zero). So Gauss-Markov doesn't apply. Ridge trades bias for variance: higher bias, lower variance. This is the bias-variance tradeoff (Week 5).
- **Follow-up:** "If OLS is the best unbiased estimator, why would we ever use ridge (which is biased)?" → Because sometimes lower variance + some bias beats unbiased + high variance. This is the bias-variance tradeoff. Seeds Week 5.

---

**Challenge 2-1D: Weighted Least Squares**
*(Give during the worked example — around minute 60)*

> In our MSE, every data point contributes equally. But what if some data points are more reliable than others?
>
> **Question:** Suppose point $i$ has reliability weight $r_i > 0$ (higher = more trustworthy). Define the weighted MSE: $R_w(w,b) = \frac{1}{n}\sum_i r_i (wx_i + b - y_i)^2$. Derive the weighted OLS solution. How does it differ from the standard OLS solution?

**Instructor notes:**
- The weighted solution involves weighted means: $\bar{x}_w = \frac{\sum_i r_i x_i}{\sum_i r_i}$, etc. The slope becomes $w^* = \frac{\text{Cov}_w(x,y)}{\text{Var}_w(x)}$ where all means and covariances use the weights $r_i$.
- The line still passes through the weighted centroid $(\bar{x}_w, \bar{y}_w)$.
- **Follow-up:** "When would you use this?" → When you know some measurements are noisier than others (e.g., different instruments, different sample sizes per group). Connects to heteroscedasticity (Week 8).

---

**Challenge 2-1E: The Correlation Coefficient and Causation**
*(Give after the correlation discussion — around minute 68)*

> We showed $w^* = r \cdot \sigma_y / \sigma_x$, where $r$ is the correlation. High correlation → steep slope → strong linear relationship.
>
> **Question:** "Correlation does not imply causation" is a famous saying. In the context of linear regression: if $w^* \neq 0$, does that mean $x$ CAUSES $y$? Give a concrete example where $w^*$ is large but $x$ does not cause $y$. Can regression ever establish causation?

**Instructor notes:**
- No! Regression measures association, not causation. Example: ice cream sales and drowning deaths are positively correlated (both increase in summer), but ice cream doesn't cause drowning — temperature is a confounder.
- Regression can establish causation only under additional assumptions: no unmeasured confounders, correct temporal ordering, and (ideally) randomized intervention. This is the domain of causal inference.
- **Follow-up:** "How could you establish causation?" → Randomized experiments (randomly assign $x$, measure $y$). Or use causal inference methods (instrumental variables, do-calculus). Seeds later-course discussion of causality.

---

### Session 2 Challenges

**Challenge 2-2A: Ridge Derivation**
*(Give after stating the ridge solution — around minute 40)*

> I stated the ridge solution $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$ without deriving it.
>
> **Question:** Derive it! Use the same approach as OLS: substitute $b^* = \bar{y} - w\bar{x}$ (which still holds — the penalty is on $w$, not $b$), center the data, and complete the square. Show that the penalty adds $\lambda$ to the $\text{Var}(x)$ term in the denominator.

**Instructor notes:**
- After centering, the ridge loss is $R(w) = w^2 \text{Var}(x) - 2w\text{Cov}(x,y) + \text{Var}(y) + \lambda w^2 = w^2(\text{Var}(x) + \lambda) - 2w\text{Cov}(x,y) + \text{Var}(y)$.
- This is a quadratic in $w$: $A = \text{Var}(x) + \lambda$, $B = 2\text{Cov}(x,y)$, so $w^* = B/(2A) = \text{Cov}(x,y)/(\text{Var}(x) + \lambda)$.
- The key insight: the penalty $\lambda w^2$ adds to the $w^2$ coefficient, inflating the denominator.
- **Follow-up:** "Does the ridge line pass through the centroid?" → Yes! $b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \bar{x}$. The penalty doesn't affect the intercept formula because we don't penalize $b$.

---

**Challenge 2-2B: Ridge and the Bias-Variance Tradeoff**
*(Give during the $\lambda$ table discussion — around minute 42)*

> Ridge shrinks $w$ toward zero. The OLS slope is unbiased (correct on average), but ridge is biased (systematically too small).
>
> **Question:** If ridge is biased and OLS is not, why would we ever use ridge? Can you think of a scenario where a biased estimator is better than an unbiased one? (We'll formalize this as the "bias-variance tradeoff" in Week 5 — for now, think intuitively.)

**Instructor notes:**
- The answer: OLS may have low bias but high variance (the estimate swings wildly with different training sets). Ridge has higher bias but lower variance (the estimate is more stable). If the variance reduction outweighs the bias increase, ridge has lower total error.
- Analogy: a clock that is always exactly 1 hour fast (biased but low variance — perfectly consistent) vs. a clock that is correct on average but swings ±3 hours (unbiased but high variance). The biased clock is more useful!
- **Follow-up:** "How would you measure this tradeoff in practice?" → Train/test split. Compute test MSE for OLS and ridge with various $\lambda$. The best $\lambda$ minimizes test MSE. Seeds Week 4 (model evaluation) and Week 5 (bias-variance decomposition).

---

**Challenge 2-2C: Polynomial Features and the Design Matrix**
*(Give during the polynomial overfitting demo — around minute 20)*

> We said polynomial regression $\hat{y} = w_d x^d + \ldots + w_1 x + w_0$ is "linear in the parameters." 
>
> **Question:** If we define new features $z_1 = x, z_2 = x^2, \ldots, z_d = x^d$, then the model is $\hat{y} = w_d z_d + \ldots + w_1 z_1 + w_0$. This is linear in $z_1, \ldots, z_d$. Can you write down the OLS solution for this multi-feature model? (Hint: it involves the same covariance/variance idea, but generalized.) What goes wrong when $d + 1 = n$ (number of parameters equals number of data points)?

**Instructor notes:**
- The multi-feature OLS solution is $\mathbf{w}^* = (\mathbf{Z}^T \mathbf{Z})^{-1} \mathbf{Z}^T \mathbf{y}$ in matrix form (Week 8). The student doesn't need to know matrices — they should recognize that each feature contributes a covariance term.
- When $d + 1 = n$, the system is exactly determined: there's a unique polynomial through all points. The matrix $\mathbf{Z}^T \mathbf{Z}$ is square and invertible, so the solution exists and gives zero training error.
- When $d + 1 > n$, the system is underdetermined: infinitely many solutions. The matrix is singular (not invertible).
- When $d + 1 < n$, the system is overdetermined: no exact solution, OLS gives the best fit.
- **Follow-up:** "What does ridge do when $d + 1 > n$?" → Ridge adds $\lambda$ to the diagonal, making the matrix invertible even when it's singular. This is why ridge is useful in high-dimensional settings. Seeds Week 8.

---

**Challenge 2-2D: R² Can Be Negative**
*(Give after introducing R² — around minute 58)*

> We said $R^2 = 1$ is perfect and $R^2 = 0$ means "no better than predicting $\bar{y}$." Can $R^2$ ever be negative?
>
> **Question:** Under what circumstances would $R^2 < 0$? Give a concrete example. (Hint: think about what happens if you use a model that's worse than just predicting $\bar{y}$.) Can this happen with OLS? Can it happen with ridge?

**Instructor notes:**
- $R^2 < 0$ when $\text{SS}_{\text{res}} > \text{SS}_{\text{tot}}$, i.e., the model's predictions are worse (in squared error) than just predicting $\bar{y}$.
- This CANNOT happen with OLS on the training data — OLS always fits at least as well as the constant model $\hat{y} = \bar{y}$ (which is a special case of the linear model with $w = 0$, $b = \bar{y}$). So training $R^2 \geq 0$ for OLS.
- It CAN happen with ridge (large $\lambda$ can make the model worse than $\bar{y}$ on training data — though this is unusual since ridge also includes $w = 0$ as a limit).
- It CAN happen on TEST data: a model that overfit the training data may have worse test $R^2$ than the constant model.
- **Follow-up:** "If $R^2$ is always $\geq 0$ for OLS on training data, why is it useful?" → Because we care about TEST $R^2$, which can be negative if the model overfit. Also, $R^2$ lets us compare models quantitatively.

---

**Challenge 2-2E: The Bayesian Perspective (Preview)**
*(Give during the probabilistic preview — around minute 68)*

> I mentioned that ridge regression corresponds to a "prior belief that weights should be small." This is a Bayesian idea.
>
> **Question:** In the Bayesian framework, you start with a prior distribution over $w$ (your belief before seeing data), then update it with the data to get a posterior distribution. Ridge regression is equivalent to: (1) a Gaussian prior on $w$ (centered at 0), (2) Gaussian noise on the observations, and (3) taking the mean of the posterior. Can you sketch why a Gaussian prior on $w$ would lead to a $w^2$ penalty? (Hint: the log of a Gaussian density is a quadratic.)

**Instructor notes:**
- A Gaussian prior $p(w) \propto \exp(-w^2 / (2\tau^2))$ has log-density $\log p(w) = -w^2/(2\tau^2) + \text{const}$. Maximizing the posterior (MAP estimation) is equivalent to minimizing the negative log-posterior: $-\log p(w|\text{data}) \propto \text{MSE} + w^2/(2\tau^2)$. This is ridge with $\lambda = 1/(2\tau^2)$!
- The prior variance $\tau^2$ controls the strength: a tight prior (small $\tau^2$) = strong regularization (large $\lambda$). A wide prior (large $\tau^2$) = weak regularization (small $\lambda$).
- **Follow-up:** "What prior would give L1 (lasso) instead of L2?" → A Laplace prior $p(w) \propto \exp(-|w|/\tau)$, which has a sharp peak at 0. This is why lasso produces sparsity. Seeds Week 5 (probability) and Week 8 (Bayesian regression).

---

### Ongoing Challenges (Cross-Week)

These are longer-form questions that advanced students can think about throughout the week. Mention them at the end of Session 2 and discuss during office hours or the start of Week 3.

**Ongoing 1: The Normal Equation and Matrix Form**

> We derived everything in scalar notation: one input, one output. In Week 8, we'll see the matrix version: $\hat{\boldsymbol{\beta}} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$. Can you see how the scalar formulas ($w^* = \text{Cov}/\text{Var}$, $b^* = \bar{y} - w^*\bar{x}$) are special cases of this matrix formula? Try to verify it by writing out $\mathbf{X}$ and $\mathbf{y}$ for the ice cream data and computing the matrix product by hand.

**Instructor notes:** This is excellent preparation for Week 8. The student should set up $\mathbf{X} = [\mathbf{x}, \mathbf{1}]$ (a column of $x$-values and a column of ones), compute $\mathbf{X}^T\mathbf{X}$ (a 2×2 matrix), invert it, and multiply through. The result should match $w^* = 10, b^* = -30$. This exercise builds matrix intuition and shows that the scalar formulas are not magic — they're the 1D case of a general result.

---

**Ongoing 2: OLS as a Projection**

> The geometric facts we discovered — the line passes through the centroid, residuals sum to zero, residuals are uncorrelated with $x$ — are all manifestations of a single deeper fact: OLS projects the data onto the hypothesis space. In 1D, this means the residual vector is "perpendicular" to the $x$-axis. In higher dimensions (Week 8), it means the residual vector is perpendicular to the column space of $\mathbf{X}$. Can you draw a picture of this projection in 2D (two data points, one feature)? What does "perpendicular" mean geometrically?

**Instructor notes:** This is the geometric heart of linear regression. With 2 data points and 1 feature, the data $\mathbf{y} = (y_1, y_2)$ lives in $\mathbb{R}^2$. The hypothesis space (all vectors of the form $w\mathbf{x} + b\mathbf{1}$) is a 2D plane in $\mathbb{R}^2$ — actually, with 2 parameters and 2 data points, it's all of $\mathbb{R}^2$, so the residual is zero (perfect fit). Better to use 3 data points: $\mathbf{y} \in \mathbb{R}^3$, and the hypothesis space is a 2D plane in $\mathbb{R}^3$. The OLS solution is the projection of $\mathbf{y}$ onto this plane, and the residual is perpendicular to the plane. This is the picture to draw. Seeds Week 8.

---

**Ongoing 3: The OLS-Ridge Continuum**

> We saw that $\lambda = 0$ gives OLS and $\lambda \to \infty$ gives $w = 0$ (predict $\bar{y}$). Plot the ridge slope $w^*_{\text{ridge}}$ as a function of $\lambda$ for the ice cream data. What shape is the curve? What is the training MSE as a function of $\lambda$? What do you think the TEST MSE looks like (without computing it)?

**Instructor notes:**
- $w^*_{\text{ridge}}(\lambda) = 500/(50 + \lambda)$. This is a decreasing function: starts at 10 ($\lambda = 0$), approaches 0 as $\lambda \to \infty$. The shape is hyperbolic.
- Training MSE increases monotonically with $\lambda$ (more regularization = worse fit on training data).
- Test MSE is typically U-shaped: high at $\lambda = 0$ (overfitting), decreases to a minimum at the optimal $\lambda$, then increases again as $\lambda \to \infty$ (underfitting). This U-shape is the bias-variance tradeoff in action.
- **Follow-up:** "How would you find the optimal $\lambda$?" → Cross-validation (Week 4). The student can sketch the U-curve and see why there's a sweet spot.

---

### Managing Advanced Students: Practical Tips

| Situation | Strategy |
|-----------|----------|
| Student finishes the worked example early | Hand them Challenge 2-1A (no-intercept regression). It's a natural extension — same tools, new twist. |
| Student already knows the OLS formula | Ask them to DERIVE it (Challenge 2-1B or the ridge derivation, Challenge 2-2A). Knowing the formula ≠ understanding why it's true. |
| Student asks about the matrix formula | Give them Ongoing Challenge 1. "You know the matrix version — verify it reduces to our scalar formula. We'll do this formally in Week 8." |
| Student seems bored during the derivation | Give them Challenge 2-1C (Gauss-Markov) or Challenge 2-1D (weighted least squares). These generalize the current derivation and require independent thinking. |
| Student asks "why squared error?" during Session 1 | Give them a preview of the probabilistic connection (Challenge 2-2E). "The short answer: Gaussian noise. The deep answer involves probability — here's a preview question." |
| Multiple advanced students | Form a "study cluster." Give them Ongoing Challenge 2 (OLS as projection) and ask them to discuss it together during the break. The geometric picture is best discovered collaboratively. |
| Student is frustrated by the algebra | Remind them: "The derivations are hard. The formulas are easy. Focus on the formulas first — $w^* = \text{Cov}/\text{Var}$, $b^* = \bar{y} - w^*\bar{x}$. Come back to the derivation when you're ready. The algebra will make more sense the second time." |

---

## Post-Session Checklist

After each session, the instructor should:

- [ ] Review quiz results and note common mistakes
- [ ] Update the student progress tracker (see `03_Assessment_Strategy.md`)
- [ ] Prepare spiral-back questions for the next quiz
- [ ] Check if any student needs intervention (⚠ or ✗ on the tracker)
- [ ] Preview next session's material and adjust if needed

---

## Preparation Checklist for Week 2

### Before Session 1

- [ ] Read handout Sections 1–4
- [ ] Practice the two derivations ($b^*$ and $w^*$) on the board — time yourself. The algebra must flow smoothly.
- [ ] Prepare the ice cream data table on the board (or a slide)
- [ ] Open Desmos (for the line-fitting demo — see `visual_demos.md`, Demo 1)
- [ ] Print quiz S1 (or have it ready to project)
- [ ] Print handout for students (or distribute digitally)
- [ ] Have calculators available (students will need them for the worked example)
- [ ] Prepare sticky notes with challenge questions for advanced students

### Before Session 2

- [ ] Read handout Sections 5–8
- [ ] Set up Desmos with the polynomial overfitting demo (Demo 2) and ridge demo (Demo 3)
- [ ] Prepare the ridge solution derivation (or at least the key steps) — you may want to show it briefly
- [ ] Review Session 1 quiz results — prepare to address common mistakes at the start of Session 2
- [ ] Print quiz S2
- [ ] Prepare the R² computation for the ice cream example on the board
- [ ] Prepare sticky notes with Session 2 challenge questions
- [ ] If assigning the Domingos paper: prepare the 5-minute discussion prompts (see `suggested_paper.md`)
