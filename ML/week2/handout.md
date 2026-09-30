# Week 2 Handout: Scalar Linear Regression

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 2 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** Week 1 (ML problem formulation, hypothesis space, loss function, empirical risk, overfitting/underfitting)

---

## 1. Motivation

### 1.1 Our First Complete Model

Last week we set up the ML framework: choose a hypothesis space, choose a loss function, find the best parameters. This week we instantiate that framework on the **simplest non-trivial model**: linear regression.

Linear regression is the "hello world" of machine learning. It is:

- **Simple enough to solve exactly** — we can derive a closed-form solution using only algebra (mean, variance, covariance). No calculus, no matrices.
- **Rich enough to illustrate every key concept** — overfitting, regularization, the overfitting-underfitting tradeoff.
- **The foundation for more complex models** — neural networks are, in a sense, stacks of linear regressions with nonlinearities.

> **Important:** This week we work entirely in **scalar notation**. One input variable $x$, one output variable $y$. No vectors, no matrices. In Week 8 (after your linear algebra course has caught up), we'll revisit this with matrix notation and discover that everything generalizes beautifully.

### 1.2 The Problem

We want to predict a **continuous** output $y$ from a single input $x$.

**Concrete example:** Predict ice cream sales $y$ (in dollars) from temperature $x$ (in °C).

We have $n$ training examples: $(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n)$.

**Model:** Assume a linear relationship:
$$\hat{y} = f_{w,b}(x) = wx + b$$

where $w$ is the **slope** (weight) and $b$ is the **intercept** (bias).

**Question:** How do we find the best $w$ and $b$?

---

## 2. The Loss Function: Mean Squared Error

### 2.1 Definition

We use the **squared error** loss and average over all training examples:

$$L(\hat{y}, y) = (\hat{y} - y)^2$$

$$R_{\text{emp}}(w, b) = \frac{1}{n} \sum_{i=1}^{n} (wx_i + b - y_i)^2$$

This is the **Mean Squared Error (MSE)**. It measures the average squared vertical distance between each data point and the line $\hat{y} = wx + b$.

### 2.2 Why Squared Error?

Two justifications:

**Geometric:** The squared error measures the Euclidean distance between predictions and targets. Minimizing MSE = finding the line that is "closest" to all data points in the vertical direction.

**Practical:** The squared error is differentiable everywhere (no corners), and the resulting optimization problem has a **unique** solution — there is one best line.

> **Preview:** In Week 5, when we study probability, we'll discover a deep connection: minimizing MSE is equivalent to assuming the noise in our data follows a Gaussian (bell curve) distribution. The loss function is not arbitrary — it reflects assumptions about the problem. For now, we proceed with the geometric perspective.

### 2.3 Visual Intuition

```
    y
    │        •
    │      ╱
    │    ╱ ← line: ŷ = wx + b
    │  ╱  •
    │╱ ╱
    │╱ ← vertical distance = |ŷᵢ - yᵢ|
    │╱
    └──────────────── x
```

Each data point contributes a squared vertical distance to the loss. The best line minimizes the sum of these squared distances.

---

## 3. Deriving the Optimal Slope and Intercept

### 3.1 The Goal

We want to find $w^*$ and $b^*$ that minimize:

$$R_{\text{emp}}(w, b) = \frac{1}{n} \sum_{i=1}^{n} (wx_i + b - y_i)^2$$

We can solve this using **only algebra** — no calculus required. The key insight is to rewrite the loss in terms of means, variances, and covariances.

### 3.2 Step 1: Find the Optimal Intercept $b^*$

Let's first ask: for a **fixed** slope $w$, what is the best intercept $b$?

The loss as a function of $b$ (with $w$ fixed) is:

$$R(b) = \frac{1}{n} \sum_{i=1}^{n} (wx_i + b - y_i)^2$$

Let's substitute $\hat{y}_i = wx_i$ (the prediction without the intercept) and $\epsilon_i = \hat{y}_i - y_i$ (the error without intercept):

$$R(b) = \frac{1}{n} \sum_{i=1}^{n} (\epsilon_i + b)^2 = \frac{1}{n} \sum_{i=1}^{n} (\epsilon_i^2 + 2b\epsilon_i + b^2)$$

$$= \frac{1}{n}\sum_{i=1}^{n}\epsilon_i^2 + 2b \cdot \frac{1}{n}\sum_{i=1}^{n}\epsilon_i + b^2$$

This is a **quadratic in $b$**: $R(b) = b^2 + 2b\bar{\epsilon} + \overline{\epsilon^2}$, where $\bar{\epsilon} = \frac{1}{n}\sum_i \epsilon_i$.

A quadratic $f(b) = b^2 + cb + d$ is minimized at $b = -c/2$. So:

$$b^* = -\bar{\epsilon} = -\frac{1}{n}\sum_{i=1}^{n}(wx_i - y_i) = \frac{1}{n}\sum_{i=1}^{n} y_i - w \cdot \frac{1}{n}\sum_{i=1}^{n} x_i$$

$$\boxed{b^* = \bar{y} - w \cdot \bar{x}}$$

where $\bar{x} = \frac{1}{n}\sum_i x_i$ is the mean of the inputs and $\bar{y} = \frac{1}{n}\sum_i y_i$ is the mean of the outputs.

> **Key insight:** The best-fit line always passes through the **point of means** $(\bar{x}, \bar{y})$. No matter what slope $w$ you choose, the optimal intercept makes the line go through the "center" of the data. This is a beautiful geometric fact.

### 3.3 Step 2: Find the Optimal Slope $w^*$

Now substitute $b^* = \bar{y} - w\bar{x}$ back into the loss. The prediction becomes:

$$\hat{y}_i = wx_i + b^* = wx_i + \bar{y} - w\bar{x} = w(x_i - \bar{x}) + \bar{y}$$

The error is:

$$\hat{y}_i - y_i = w(x_i - \bar{x}) + \bar{y} - y_i = w(x_i - \bar{x}) - (y_i - \bar{y})$$

Let's define **centered** variables: $\tilde{x}_i = x_i - \bar{x}$ and $\tilde{y}_i = y_i - \bar{y}$. Then:

$$\hat{y}_i - y_i = w\tilde{x}_i - \tilde{y}_i$$

The loss becomes:

$$R(w) = \frac{1}{n}\sum_{i=1}^{n}(w\tilde{x}_i - \tilde{y}_i)^2 = \frac{1}{n}\sum_{i=1}^{n}(w^2\tilde{x}_i^2 - 2w\tilde{x}_i\tilde{y}_i + \tilde{y}_i^2)$$

$$= w^2 \cdot \frac{1}{n}\sum_i \tilde{x}_i^2 - 2w \cdot \frac{1}{n}\sum_i \tilde{x}_i\tilde{y}_i + \frac{1}{n}\sum_i \tilde{y}_i^2$$

This is a quadratic in $w$: $R(w) = Aw^2 - Bw + C$ where:
- $A = \frac{1}{n}\sum_i \tilde{x}_i^2 = \text{Var}(x)$ (the variance of $x$)
- $B = \frac{2}{n}\sum_i \tilde{x}_i\tilde{y}_i = 2\text{Cov}(x, y)$ (twice the covariance)
- $C = \frac{1}{n}\sum_i \tilde{y}_i^2 = \text{Var}(y)$ (the variance of $y$)

A quadratic $Aw^2 - Bw + C$ (with $A > 0$) is minimized at $w = B/(2A)$:

$$w^* = \frac{2\text{Cov}(x, y)}{2\text{Var}(x)} = \frac{\text{Cov}(x, y)}{\text{Var}(x)}$$

$$\boxed{w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)} = \frac{\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^2}}$$

### 3.4 Summary: The OLS Solution

$$\boxed{w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)}, \qquad b^* = \bar{y} - w^* \cdot \bar{x}}$$

This is the **Ordinary Least Squares (OLS)** solution. It requires only:
- The mean of $x$ and $y$
- The variance of $x$
- The covariance of $x$ and $y$

All computable with basic arithmetic — no derivatives, no matrices.

### 3.5 Intuition for the Formula

- **$w^* = \text{Cov}(x,y) / \text{Var}(x)$:** The slope is the ratio of "how much $x$ and $y$ move together" (covariance) to "how much $x$ moves" (variance). If $x$ doesn't vary at all ($\text{Var}(x) = 0$), the slope is undefined — you can't fit a line to data where all inputs are the same.
- **$b^* = \bar{y} - w^*\bar{x}$:** The intercept ensures the line passes through the point of means $(\bar{x}, \bar{y})$.
- **Sign of $w^*$:** If $x$ and $y$ are positively correlated, $\text{Cov}(x,y) > 0$, so $w^* > 0$ (upward-sloping line). If negatively correlated, $w^* < 0$ (downward-sloping). If uncorrelated, $w^* = 0$ (flat line — $x$ tells you nothing about $y$).

### 3.6 The Correlation Connection

We can rewrite the slope using the **correlation coefficient** $r$:

$$r = \frac{\text{Cov}(x, y)}{\sigma_x \cdot \sigma_y}$$

where $\sigma_x = \sqrt{\text{Var}(x)}$ and $\sigma_y = \sqrt{\text{Var}(y)}$ are standard deviations. Then:

$$w^* = r \cdot \frac{\sigma_y}{\sigma_x}$$

This says: the slope is the correlation (how linearly related) times the ratio of spreads (how $y$ scales relative to $x$). The correlation $r \in [-1, 1]$ tells you the **strength** of the linear relationship; the ratio $\sigma_y / \sigma_x$ tells you the **scale**.

---

## 4. Worked Example: Ice Cream Sales vs. Temperature

### Data

| $i$ | $x_i$ (temp °C) | $y_i$ (sales $) |
|-----|------------------|------------------|
| 1 | 15 | 120 |
| 2 | 20 | 180 |
| 3 | 25 | 200 |
| 4 | 30 | 280 |
| 5 | 35 | 320 |

### Step 1: Compute means

$$\bar{x} = \frac{15+20+25+30+35}{5} = \frac{125}{5} = 25$$

$$\bar{y} = \frac{120+180+200+280+320}{5} = \frac{1100}{5} = 220$$

### Step 2: Compute centered values and products

| $i$ | $x_i$ | $y_i$ | $\tilde{x}_i = x_i - \bar{x}$ | $\tilde{y}_i = y_i - \bar{y}$ | $\tilde{x}_i^2$ | $\tilde{x}_i \tilde{y}_i$ |
|-----|-------|-------|-------------------------------|-------------------------------|-----------------|---------------------------|
| 1 | 15 | 120 | -10 | -100 | 100 | 1000 |
| 2 | 20 | 180 | -5 | -40 | 25 | 200 |
| 3 | 25 | 200 | 0 | -20 | 0 | 0 |
| 4 | 30 | 280 | 5 | 60 | 25 | 300 |
| 5 | 35 | 320 | 10 | 100 | 100 | 1000 |
| **Sum** | | | | | **250** | **2500** |

### Step 3: Compute variance and covariance

$$\text{Var}(x) = \frac{1}{n}\sum_i \tilde{x}_i^2 = \frac{250}{5} = 50$$

$$\text{Cov}(x, y) = \frac{1}{n}\sum_i \tilde{x}_i \tilde{y}_i = \frac{2500}{5} = 500$$

### Step 4: Compute slope and intercept

$$w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)} = \frac{500}{50} = 10$$

$$b^* = \bar{y} - w^* \cdot \bar{x} = 220 - 10 \cdot 25 = 220 - 250 = -30$$

### The model:

$$\hat{y} = 10x - 30$$

**Interpretation:** For each additional degree Celsius, ice cream sales increase by $10. At 0°C, the model predicts -$30 (which doesn't make physical sense — this is a limitation of linear models outside the data range).

### Verification

| $i$ | $x_i$ | $y_i$ | $\hat{y}_i = 10x_i - 30$ | Error $\hat{y}_i - y_i$ | Squared error |
|-----|-------|-------|--------------------------|--------------------------|---------------|
| 1 | 15 | 120 | 120 | 0 | 0 |
| 2 | 20 | 180 | 170 | -10 | 100 |
| 3 | 25 | 200 | 220 | 20 | 400 |
| 4 | 30 | 280 | 270 | -10 | 100 |
| 5 | 35 | 320 | 320 | 0 | 0 |

$$R_{\text{emp}} = \frac{1}{5}(0 + 100 + 400 + 100 + 0) = \frac{600}{5} = 120$$

The model fits well — the errors are small relative to the range of sales (120–320). Note that the line passes through the point of means $(25, 220)$: $\hat{y}(25) = 250 - 30 = 220$. ✓

---

## 5. Overfitting in Linear Regression

### 5.1 Can a Linear Model Overfit?

A simple line $\hat{y} = wx + b$ has only 2 parameters — it seems too simple to overfit. And for the case of one input variable, this is mostly true. But linear regression becomes powerful (and dangerous) when we add **polynomial features**.

### 5.2 Polynomial Regression

Instead of $\hat{y} = wx + b$, we can use:

$$\hat{y} = w_d x^d + w_{d-1} x^{d-1} + \ldots + w_1 x + w_0$$

This is still "linear regression" — it's linear in the **parameters** $w_0, \ldots, w_d$, even though it's nonlinear in $x$. We're just replacing $x$ with the features $x, x^2, \ldots, x^d$.

With $n$ data points and $d+1$ parameters:
- If $d+1 = n$: the polynomial passes through every point exactly (zero training error).
- If $d+1 > n$: infinitely many polynomials pass through all points.
- If $d+1 < n$: the polynomial can't fit all points (some error remains).

### 5.3 Visual Example

```
  Data: 5 points following a roughly linear trend

  Degree 1 (line):         Degree 4 (passes through all):
  y                        y
  │    •                   │        •
  │  • ─── good fit        │      • ╱╲ •
  │ • ───                  │    •   ╲╱  •
  │  •                     │  •  ╱╲╱
  └──────── x              └──────── x
  (captures trend,         (zero training error,
   small errors)            but wild oscillations)
```

The degree-4 polynomial has zero training error but will make terrible predictions between data points. This is **overfitting**.

### 5.4 The Lesson

Overfitting depends on the ratio of **model complexity** (number of parameters) to **data size** ($n$). A 2-parameter line rarely overfits with 100 data points. A 100-parameter polynomial can overfit with 100 data points.

---

## 6. Regularization: Ridge Regression (Scalar Form)

### 6.1 The Idea

When we have many features (or polynomial terms), the weights can grow large to fit noise. **Ridge regression** adds a penalty for large weights:

$$R_{\text{ridge}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2 + \lambda w^2$$

where $\lambda > 0$ is the **regularization strength**.

The new objective trades off two goals:
- **Fit the data** (first term: low MSE)
- **Keep the weight small** (second term: low $w^2$)

### 6.2 The Ridge Solution (Scalar Form)

Using the same algebraic approach (completing the square), the ridge solution is:

$$w^*_{\text{ridge}} = \frac{\text{Cov}(x, y)}{\text{Var}(x) + \lambda}$$

$$b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \cdot \bar{x}$$

> **Compare to OLS:** The only difference is the $+\lambda$ in the denominator. This **shrinks** the slope toward zero. When $\lambda = 0$, ridge = OLS. When $\lambda \to \infty$, $w \to 0$ (the model predicts $\bar{y}$ for everything — extreme underfitting).

### 6.3 Intuition

- The OLS slope is $\text{Cov}(x,y) / \text{Var}(x)$.
- The ridge slope is $\text{Cov}(x,y) / (\text{Var}(x) + \lambda)$.
- The denominator is **inflated** by $\lambda$, making the slope smaller in magnitude.
- A smaller slope means the model is **less sensitive** to $x$ — it's more conservative, less likely to fit noise.

### 6.4 The Regularization Parameter $\lambda$

| $\lambda$ | Effect | Risk |
|-----------|--------|------|
| $\lambda = 0$ | OLS (no regularization) | May overfit |
| $\lambda$ small | Slight shrinkage | Good — balances fit and stability |
| $\lambda$ moderate | Meaningful shrinkage | Sweet spot |
| $\lambda \to \infty$ | $w \to 0$ | Underfitting (predicts $\bar{y}$) |

Choosing $\lambda$ is a **model selection** problem. We'll learn how to do this with cross-validation in Week 4.

### 6.5 Ridge on the Ice Cream Example

Using $\lambda = 25$:

$$w^*_{\text{ridge}} = \frac{500}{50 + 25} = \frac{500}{75} \approx 6.67$$

$$b^*_{\text{ridge}} = 220 - 6.67 \cdot 25 = 220 - 166.67 = 53.33$$

**Comparison:**

| | OLS | Ridge ($\lambda=25$) |
|---|---|---|
| $w$ | 10 | 6.67 |
| $b$ | -30 | 53.33 |
| $|w|$ | 10 | 6.67 |

The ridge slope is smaller — the model is more conservative. It predicts less dramatic increases in sales per degree. The training MSE will be higher, but if the OLS model was fitting noise, the ridge model may generalize better.

### 6.6 L1 Regularization (Lasso) — Brief Mention

Instead of penalizing $w^2$ (L2), we can penalize $|w|$ (L1):

$$R_{\text{lasso}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2 + \lambda |w|$$

The key difference: L1 has a **corner** at $w = 0$ (the absolute value function is not smooth there). This means the L1 solution is more likely to set weights to **exactly zero** — performing **feature selection**. In the scalar case this means lasso can decide "this feature is useless" and set $w = 0$ entirely.

In the multi-feature case (Week 8), lasso's geometry (a diamond vs. a circle) makes sparsity much more likely. We'll revisit this in depth later.

---

## 7. The Geometric Perspective

### 7.1 The Line Through the Center

We showed that $b^* = \bar{y} - w^*\bar{x}$, which means the best-fit line always passes through $(\bar{x}, \bar{y})$ — the **centroid** of the data. This is a geometric fact:

```
    y
    │        •
    │      ╱
    │    ╱ ← best-fit line
    │  ● ← (x̄, ȳ) — centroid
    │╱  •
    │
    └──────────────── x
```

No matter what slope you choose, the best intercept always centers the line on the data's centroid.

### 7.2 The Residuals

The **residuals** are the errors $e_i = y_i - \hat{y}_i = y_i - (wx_i + b)$.

A key property of the OLS solution: **the residuals sum to zero**:

$$\sum_{i=1}^{n} e_i = 0$$

This follows from the intercept formula. The line is positioned so that the positive and negative errors exactly balance.

Another property: **the residuals are uncorrelated with $x$**:

$$\sum_{i=1}^{n} x_i \cdot e_i = 0$$

This means the line captures ALL the linear relationship between $x$ and $y$. What's left (the residuals) has no linear pattern — it's "noise" from the linear perspective.

> **These two properties (residuals sum to zero, uncorrelated with $x$) are the scalar version of "the residual is perpendicular to the column space" — a geometric fact we'll formalize with matrices in Week 8.**

### 7.3 R²: How Good Is the Fit?

The **coefficient of determination** $R^2$ measures the fraction of variance in $y$ explained by the model:

$$R^2 = 1 - \frac{\text{SS}_{\text{res}}}{\text{SS}_{\text{tot}}}$$

where:
- $\text{SS}_{\text{res}} = \sum_i (y_i - \hat{y}_i)^2$ is the residual sum of squares (unexplained variance)
- $\text{SS}_{\text{tot}} = \sum_i (y_i - \bar{y})^2$ is the total sum of squares (total variance of $y$)

| $R^2$ value | Interpretation |
|-------------|---------------|
| $R^2 = 1$ | Perfect fit (all points on the line) |
| $R^2 = 0$ | The model is no better than predicting $\bar{y}$ |
| $R^2 < 0$ | The model is worse than predicting $\bar{y}$ (possible with ridge or a bad model) |

$R^2$ is also the square of the correlation coefficient: $R^2 = r^2$.

### 7.4 R² for the Ice Cream Example

$$\text{SS}_{\text{res}} = 600$$

$$\text{SS}_{\text{tot}} = (-100)^2 + (-40)^2 + (-20)^2 + 60^2 + 100^2 = 10000 + 1600 + 400 + 3600 + 10000 = 25600$$

$$R^2 = 1 - \frac{600}{25600} = 1 - 0.0234 = 0.977$$

The model explains 97.7% of the variance in sales — a very good fit!

---

## 8. The Overfitting-Underfitting Tradeoff (Revisited)

### 8.1 Three Regimes

| Model | Training error | Test error | What's happening |
|-------|---------------|------------|-------------------|
| Constant ($\hat{y} = \bar{y}$) | High | High | Underfitting: too simple |
| Linear ($\hat{y} = wx + b$) | Moderate | Moderate | Good fit (if relationship is linear) |
| High-degree polynomial | Zero | High | Overfitting: too complex |
| Linear + ridge ($\lambda$ moderate) | Moderate | Moderate (or better) | Regularized: balanced |

### 8.2 How Regularization Helps

Ridge regression addresses overfitting by **constraining** the model. Instead of allowing $w$ to be any value, we pull it toward zero. This is like saying: "I'd rather have a slightly worse fit on training data if it means a more stable model."

The tradeoff:
- **$\lambda$ too small:** Model fits noise → overfitting.
- **$\lambda$ too large:** Model can't fit the signal → underfitting.
- **$\lambda$ just right:** Model fits the signal, ignores noise → good generalization.

This is the same overfitting-underfitting tradeoff from Week 1, now with a concrete knob ($\lambda$) to control it.

### 8.3 The Probabilistic Perspective (Preview — No Probability Required)

You might wonder: is there a deeper reason we chose the squared error? Why not absolute error?

**The idea (intuition only):** Imagine the true relationship is $y = wx + b + \text{noise}$. If the noise tends to be small and symmetric (equally likely to be positive or negative), then the "most likely" value of $w$ given the data turns out to be exactly the MSE minimizer.

In other words: **MSE is not arbitrary.** It's the loss function you get when you assume the noise follows a bell-curve (Gaussian) distribution. We'll prove this rigorously in Week 5.

Similarly, **ridge regression** has a probabilistic meaning: it corresponds to having a "prior belief" that the weights should be small.

> **For now:** The key takeaway is that the choice of loss function and regularizer encode assumptions about how the data was generated. Different assumptions → different loss functions.

---

## 9. Connections

### 9.1 What This Enables

| Next Week | How It Uses Week 2 |
|-----------|-------------------|
| Week 3: Overfitting & Regularization | Going deeper into polynomial overfitting, lasso/L1 geometry, the complexity dial |
| Week 4: Model Evaluation | R², MSE as evaluation metrics; train/test split to detect overfitting |
| Week 5: Probability for ML | MSE ↔ Gaussian noise, ridge ↔ Gaussian prior (formal derivation) |
| Week 6: Gradient Descent | Iterative optimization of MSE (when closed form is too expensive) |
| Week 7: Logistic Regression | Overfitting in classification, regularization for logistic regression |
| Week 8: Matrix Linear Regression | Everything here, generalized to multiple features |

### 9.2 Key Vocabulary to Master

- [ ] Mean, variance, covariance
- [ ] Mean squared error (MSE)
- [ ] Ordinary Least Squares (OLS)
- [ ] Slope $w^* = \text{Cov}(x,y) / \text{Var}(x)$
- [ ] Intercept $b^* = \bar{y} - w^*\bar{x}$
- [ ] The line passes through the centroid $(\bar{x}, \bar{y})$
- [ ] Residuals sum to zero
- [ ] Residuals are uncorrelated with $x$
- [ ] Ridge regression (L2 regularization)
- [ ] Regularization parameter $\lambda$
- [ ] Lasso (L1 regularization) — brief
- [ ] $R^2$ (coefficient of determination)
- [ ] Correlation coefficient $r$
- [ ] Polynomial features and overfitting
- [ ] The overfitting-underfitting tradeoff (revisited)

---

## 10. Exercises

### [Basic]

**E1.** Given the data:

| $x_i$ | $y_i$ |
|-------|-------|
| 1 | 3 |
| 2 | 5 |
| 3 | 7 |
| 4 | 9 |

(a) Compute $\bar{x}$, $\bar{y}$, $\text{Var}(x)$, and $\text{Cov}(x, y)$.  
(b) Compute the OLS slope $w^*$ and intercept $b^*$.  
(c) Write the model $\hat{y} = wx + b$.  
(d) Compute the MSE and $R^2$.

**E2.** For the data in E1, compute the ridge regression slope with $\lambda = 2$. How much smaller is $|w^*_{\text{ridge}}|$ compared to $|w^*_{\text{OLS}}|$?

**E3.** Explain in one sentence each:  
(a) Why does the best-fit line always pass through $(\bar{x}, \bar{y})$?  
(b) Why do the residuals sum to zero?  
(c) Why does adding $\lambda$ to the denominator shrink the slope toward zero?

### [Intermediate]

**E4.** You have 10 data points and fit a degree-9 polynomial. The training error is zero. Is this a good model? Explain why or why not. What would happen if you had 1000 data points instead?

**E5.** Suppose $\text{Cov}(x, y) = 0$ (x and y are uncorrelated). What is the OLS slope? What does the model predict? Is this reasonable?

**E6.** Two students fit a line to the same data. Student A gets $w = 2, b = 1$. Student B gets $w = 1.8, b = 1.5$. How can you determine which student's model is better? Describe the procedure without computing.

**E7.** The correlation between study hours and exam score is $r = 0.8$. The standard deviation of study hours is $\sigma_x = 2$ hours, and the standard deviation of exam scores is $\sigma_y = 15$ points. Compute the OLS slope. If a student studies 3 hours more than average, what is the predicted change in exam score?

### [★ Advanced]

**E8.** Prove that the OLS residuals are uncorrelated with $x$, i.e., $\sum_{i=1}^{n} x_i \cdot e_i = 0$ where $e_i = y_i - (w^*x_i + b^*)$.  
*(Hint: Substitute $b^* = \bar{y} - w^*\bar{x}$, expand, and use the formula for $w^*$.)*

**E9.** Prove the **variance decomposition**: $\text{Var}(y) = \text{Var}(\hat{y}) + \text{Var}(e)$, where $\hat{y}_i = w^*x_i + b^*$ are the predictions and $e_i = y_i - \hat{y}_i$ are the residuals. In words: the total variance of $y$ equals the explained variance plus the unexplained variance.  
*(Hint: Show that $\text{Cov}(\hat{y}, e) = 0$ first, using the fact that residuals are uncorrelated with $x$. Then use $\text{Var}(A + B) = \text{Var}(A) + \text{Var}(B) + 2\text{Cov}(A, B)$.)*

**E10.** ★★ Consider fitting $\hat{y} = wx$ (no intercept). Derive the optimal $w^*$ using the same algebraic approach (complete the square). Show that $w^* = \frac{\sum_i x_i y_i}{\sum_i x_i^2}$. When does this differ from the OLS solution with intercept? Give a concrete example where the two give very different answers.

**E11.** ★★ The **Huber loss** is a hybrid of squared error and absolute error:
$$L_\delta(\hat{y}, y) = \begin{cases} \frac{1}{2}(\hat{y} - y)^2 & \text{if } |\hat{y} - y| \leq \delta \\ \delta(|\hat{y} - y| - \frac{1}{2}\delta) & \text{if } |\hat{y} - y| > \delta \end{cases}$$
(a) Why might Huber loss be better than MSE when the data has **outliers**?  
(b) Why is it not used as commonly as MSE in practice?  
(c) Connect this to the L1 vs. L2 discussion: which is more robust to outliers — $|error|$ or $(error)^2$? Why?

---

## 11. Summary

### Key Equations

> **Model:** $\hat{y} = wx + b$

> **MSE Loss:** $R_{\text{emp}}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(wx_i + b - y_i)^2$

> **OLS Solution:**
> $$w^* = \frac{\text{Cov}(x, y)}{\text{Var}(x)}, \qquad b^* = \bar{y} - w^* \cdot \bar{x}$$

> **Ridge Solution:**
> $$w^*_{\text{ridge}} = \frac{\text{Cov}(x, y)}{\text{Var}(x) + \lambda}, \qquad b^*_{\text{ridge}} = \bar{y} - w^*_{\text{ridge}} \cdot \bar{x}$$

> **R²:** $R^2 = 1 - \frac{\text{SS}_{\text{res}}}{\text{SS}_{\text{tot}}}$

### Key Intuition (If You Remember Nothing Else...)

1. **The best-fit line passes through the centroid $(\bar{x}, \bar{y})$.** The intercept ensures this.
2. **The slope is Cov/Var.** It's the ratio of "how much x and y move together" to "how much x moves."
3. **Residuals sum to zero and are uncorrelated with x.** The line captures all the linear signal.
4. **Ridge shrinks the slope toward zero** by adding $\lambda$ to the denominator. This combats overfitting.
5. **The overfitting-underfitting tradeoff** is controlled by model complexity (polynomial degree) and regularization ($\lambda$).
6. **MSE is not arbitrary** — it corresponds to Gaussian noise (formal derivation in Week 5).

---

*Next week: Overfitting & Regularization — Going Deeper. We'll see polynomial overfitting in full detail, the L1 vs. L2 geometry, the complexity dial that unifies all ML models, and the generalization gap made precise.*
