# Week 6 Handout: Optimization Basics — Gradient Descent

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 6 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** Week 2 (scalar linear regression, MSE, OLS, ridge), Week 3 (overfitting & regularization, lasso has no closed form), Week 4 (model evaluation, learning curves), Week 5 (probability, MLE/MAP, bias-variance decomposition)  
> **Assumed background:** Your calculus course has covered derivatives, partial derivatives, and the chain rule. We will USE these tools — not re-derive them.

---

## 1. Motivation

### 1.1 The Questions We've Been Postponing

Throughout Weeks 1–5, we've been deriving closed-form solutions:

- **Week 2:** OLS has a closed form: $w^* = \text{Cov}(x,y)/\text{Var}(x)$.
- **Week 2:** Ridge has a closed form: $w^*_{\text{ridge}} = \text{Cov}(x,y)/(\text{Var}(x) + \lambda)$.
- **Week 3:** Lasso has **no** closed form. We said: "Lasso requires iterative optimization. When we learn gradient descent in Week 6, we'll see how to handle nonsmooth functions."
- **Week 5:** We showed MSE = MLE and ridge = MAP. But what if the model is more complex? What if there's no closed form for the MLE?

This week, we learn **gradient descent** — the engine that powers almost all modern ML.

### 1.2 Why Not Always Use Closed Form?

| Method | Closed Form? | When Used |
|--------|-------------|-----------|
| OLS (scalar) | Yes | Simple linear regression |
| Ridge (scalar) | Yes | Regularized linear regression |
| Lasso (scalar) | **No** | L1 regularized regression |
| Logistic regression | **No** | Classification (Week 7) |
| Neural networks | **No** | Deep learning (Weeks 15–17) |

Closed-form solutions are the exception. Most ML models require iterative optimization.

### 1.3 The Roadmap

| Session | Topics | Key Deliverable |
|---------|--------|-----------------|
| S1 | Gradient concept, update rule, learning rate, 1D quadratic example, convexity | GD intuition |
| S2 | GD on MSE, SGD, mini-batch, feature scaling, ridge/lasso GD | Training a model with GD |

---

## 2. The Gradient and Gradient Descent

### 2.1 The Gradient: What You Need to Remember

You know derivatives from calculus. Here's what matters for ML:

The **gradient** of a function $f(w_1, \ldots, w_d)$ is the vector of partial derivatives:

$$\nabla f(\mathbf{w}) = \begin{pmatrix} \frac{\partial f}{\partial w_1} \\ \vdots \\ \frac{\partial f}{\partial w_d} \end{pmatrix}$$

**Geometric meaning:** The gradient points in the direction of **steepest ascent** — the direction in which $f$ increases most rapidly. Therefore, $-\nabla f$ points in the direction of **steepest descent**.

> **Key intuition:** To minimize $f$, take a step in the direction $-\nabla f$. This is gradient descent.

### 2.2 The Update Rule

**Gradient descent** minimizes a loss function $L(\mathbf{w})$ by iteratively updating:

$$\boxed{\mathbf{w} \leftarrow \mathbf{w} - \eta \, \nabla L(\mathbf{w})}$$

where $\eta$ is the **learning rate** (step size) and $\nabla L(\mathbf{w})$ is the gradient of the loss.

**Intuition:** "Look at the slope. Take a step downhill. Repeat."

### 2.3 The Algorithm

```
Initialize w (random or zeros)
Set learning rate η
Set max iterations T

for t = 1 to T:
    g = ∇L(w)          # Compute gradient
    w = w - η * g      # Update weights
    if |g| < ε:         # Convergence check
        break

return w
```

### 2.4 Step-by-Step on a 1D Quadratic

Minimize $f(w) = w^2$ (parabola with minimum at $w = 0$).

**Derivative:** $f'(w) = 2w$. **Update:** $w \leftarrow w - \eta \cdot 2w$.

Start: $w_0 = 3$, $\eta = 0.1$.

| Step | $w$ | $f(w)$ | $f'(w)$ | Step size |
|------|-----|--------|---------|-----------|
| 0 | 3.000 | 9.000 | 6.000 | 0.6 |
| 1 | 2.400 | 5.760 | 4.800 | 0.48 |
| 2 | 1.920 | 3.686 | 3.840 | 0.384 |
| 3 | 1.536 | 2.359 | 3.072 | 0.307 |
| ... | ... | ... | ... | ... |
| 20 | 0.036 | 0.001 | 0.072 | 0.007 |

**Pattern:** $w_{t+1} = w_t(1 - 2\eta) = w_t \times 0.8$. Geometric decay. For convergence: $|1 - 2\eta| < 1$, i.e., $0 < \eta < 1$.

> **The chain rule is the most important calculus tool for ML.** When we compute gradients of neural networks (Week 16), the chain rule is applied repeatedly — this is called **backpropagation**. For now, we use it to derive the MSE gradient.

---

## 3. The Learning Rate

The learning rate $\eta$ is the most important hyperparameter in gradient descent.

### 3.1 Three Regimes

**Too small ($\eta = 0.001$):** Each step is tiny. Convergence takes forever. Safe but impractical.

**Too large ($\eta > 1$ for $f(w) = w^2$):** Steps overshoot the minimum. The loss *increases* each step — **divergence**.

**Just right ($\eta = 0.1$):** Steady decrease. Reaches the minimum in a reasonable number of steps.

### 3.2 Convergence Condition

For a quadratic loss $f(w) = aw^2$, GD converges iff:

$$0 < \eta < \frac{1}{a}$$

(The step size must be smaller than $1/\text{curvature}$.)

### 3.3 Convexity

MSE is a **convex** function of $(w, b)$. This means:

- There is exactly one minimum (no local minima).
- GD is **guaranteed** to converge to the global minimum, given a suitable $\eta$.

> **Convexity is a big deal.** For linear regression, GD always works. For neural networks (non-convex), GD might get stuck in local minima — but in practice, it usually works well enough. We'll discuss this in Week 17.

### 3.4 Learning Rate Schedules

| Schedule | Formula | When to Use |
|----------|---------|-------------|
| Fixed | $\eta_t = \eta_0$ | Simple, well-tuned problems |
| Step decay | $\eta_t = \eta_0 \cdot \gamma^{\lfloor t/s \rfloor}$ | Common in practice |
| Inverse | $\eta_t = \eta_0 / (1 + \lambda t)$ | Theoretical guarantees |
| Cosine | $\eta_t = \frac{\eta_0}{2}(1 + \cos(\pi t / T))$ | Popular for neural networks (Week 17) |

> **Intuition:** Early in training, large steps make rapid progress. Later, small steps fine-tune near the minimum.

---

## 4. Gradient Descent on Linear Regression

### 4.1 The Setup

$$\hat{y}_i = wx_i + b, \qquad \text{MSE}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - wx_i - b)^2$$

### 4.2 Computing the Gradient (Chain Rule)

We need $\frac{\partial \text{MSE}}{\partial w}$ and $\frac{\partial \text{MSE}}{\partial b}$.

Let $r_i = y_i - wx_i - b$ (the **residual**). Then $\text{MSE} = \frac{1}{n}\sum_i r_i^2$.

**W.r.t. $w$** (chain rule: outer derivative $\times$ inner derivative):

$$\frac{\partial \text{MSE}}{\partial w} = \frac{1}{n}\sum_i 2r_i \cdot \frac{\partial r_i}{\partial w} = \frac{1}{n}\sum_i 2r_i \cdot (-x_i) = -\frac{2}{n}\sum_{i=1}^{n} x_i r_i$$

**W.r.t. $b$:**

$$\frac{\partial \text{MSE}}{\partial b} = \frac{1}{n}\sum_i 2r_i \cdot (-1) = -\frac{2}{n}\sum_{i=1}^{n} r_i$$

### 4.3 The Update Rules

$$\boxed{w \leftarrow w + \frac{2\eta}{n}\sum_{i=1}^{n} x_i r_i, \qquad b \leftarrow b + \frac{2\eta}{n}\sum_{i=1}^{n} r_i}$$

> **Intuition:** $w$ increases if $x_i$ is positive and the model underpredicts ($r_i > 0$). The term $x_i r_i$ is the "correction" — it's large when the input is correlated with the residual.

### 4.4 The Residual and the Optimality Condition

The gradient is $\nabla_w \text{MSE} = -\frac{2}{n}\sum_i x_i r_i$.

At the minimum, the gradient is zero: $\sum_i x_i r_i = 0$.

> **Key insight:** The gradient is the (negative) correlation between inputs and residuals. When residuals are uncorrelated with inputs, the gradient is zero — the model has extracted all the linear information. **This is the OLS optimality condition.** GD finds the same answer as the closed form.

### 4.5 Ridge Regression with GD

For ridge: $L = \text{MSE} + \lambda w^2$.

$$\frac{\partial L}{\partial w} = -\frac{2}{n}\sum_i x_i r_i + 2\lambda w$$

$$w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - 2\eta\lambda w$$

> The $-2\eta\lambda w$ term is **shrinkage**. Each step, $w$ is pulled toward 0. This is the GD view of ridge — same as Week 2's closed form, but now we see *how* shrinkage happens step by step.

### 4.6 Lasso (Subgradient Descent)

For lasso: $L = \text{MSE} + \lambda|w|$. The derivative of $|w|$ is $\text{sgn}(w)$ (undefined at $w = 0$).

$$w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - \eta\lambda \, \text{sgn}(w)$$

where $\text{sgn}(w) = +1$ if $w > 0$, $-1$ if $w < 0$, and $0$ if $w = 0$ (by convention).

> **This is why lasso drives weights to exactly 0.** When $w$ reaches 0, the subgradient is 0, so it stays there. Ridge (L2) only shrinks *toward* 0, never reaching it. This is the GD view of the geometric argument from Week 3 (L1 diamond vs L2 ball).

---

## 5. Stochastic Gradient Descent (SGD)

### 5.1 The Problem with Batch GD

**Batch gradient descent** uses the entire dataset per step: $\nabla L = -\frac{2}{n}\sum_i x_i r_i$. This costs $O(n)$ per step. For large datasets (millions of examples), this is too slow.

### 5.2 SGD: One Example at a Time

**SGD** uses ONE random example per step:

$$w \leftarrow w + 2\eta \, x_i r_i$$

where $i$ is chosen uniformly at random.

- Each step costs $O(1)$.
- The gradient is **noisy** but unbiased: $\mathbb{E}[g_i] = g_{\text{batch}}$.
- The noise can **escape shallow local minima** (useful for non-convex problems).

### 5.3 Mini-Batch GD

Uses a batch of $B$ examples (typically $B = 32, 64, 128$):

$$w \leftarrow w + \frac{2\eta}{B}\sum_{i \in \text{batch}} x_i r_i$$

This is the **standard** in modern ML. It balances speed ($O(B)$ per step) with stability (averaging reduces variance).

### 5.4 Comparison Table

| Property | Batch GD | SGD | Mini-Batch GD |
|----------|----------|-----|---------------|
| Examples per step | All $n$ | 1 | $B$ (32–128) |
| Cost per step | $O(n)$ | $O(1)$ | $O(B)$ |
| Gradient variance | 0 (exact) | High | Moderate |
| Steps to converge | Few | Many | Moderate |
| Can parallelize? | Yes (expensive) | No | Yes (GPU) |
| Escapes local minima? | No | Yes | Sometimes |
| Used in practice | Small datasets | Rarely alone | **Standard** |

### 5.5 Epochs

An **epoch** = one complete pass through the training data.

- Batch GD: 1 step = 1 epoch.
- SGD: $n$ steps = 1 epoch.
- Mini-batch: $n/B$ steps = 1 epoch.

---

## 6. Feature Scaling

### 6.1 Why Scale Features?

When features have different scales (e.g., $x_1 \in [0,1]$, $x_2 \in [0, 1000]$), the loss surface is **elongated**. GD zigzags: large steps in the steep direction (overshooting), tiny steps in the shallow direction.

After scaling, the loss surface becomes more **spherical**. GD converges smoothly.

### 6.2 Standardization

$$x_i^{(\text{scaled})} = \frac{x_i - \bar{x}}{\sigma_x}$$

After standardization, features have mean 0 and standard deviation 1.

> **Critical (Week 4 connection):** Compute $\bar{x}$ and $\sigma_x$ using ONLY training data. Applying statistics from the full dataset (including test) is **data leakage**!

---

## 7. Monitoring Training

### 7.1 The Loss Curve

Plot training loss vs. steps:

- **Steady decrease:** GD is working.
- **Plateau:** Converged (or stuck).
- **Oscillation:** $\eta$ too large. Reduce it.
- **Divergence (loss increases):** $\eta$ way too large. Reduce immediately.

### 7.2 Training vs. Validation Loss

- **Both decrease then plateau:** Good fit.
- **Training ↓, validation ↑:** Overfitting. Regularize (Week 3) or stop early.
- **Both high, no decrease:** Underfitting or $\eta$ too small.

---

## 8. Summary

### Key Equations

> **GD update:** $\mathbf{w} \leftarrow \mathbf{w} - \eta \, \nabla L(\mathbf{w})$

> **MSE gradient:** $\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$, $\quad \frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$

> **SGD update:** $w \leftarrow w + 2\eta \, x_i r_i$ (single example)

> **Ridge GD:** $w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - 2\eta\lambda w$

### Key Intuition

1. **The gradient points uphill.** Step opposite to minimize.
2. **Learning rate controls step size.** Too small = slow. Too large = diverge.
3. **MSE is convex.** GD is guaranteed to find the global minimum.
4. **The gradient is the correlation between inputs and residuals.** Zero gradient = OLS solution.
5. **SGD uses one example per step.** Noisy but fast. Mini-batch is the standard.
6. **Feature scaling helps GD converge faster.**
7. **Lasso uses subgradient descent.** The non-differentiability at 0 causes sparsity.

---

## 9. Exercises

### [Basic]

**E1.** Minimize $f(w) = 3w^2 + 2w + 1$ with $\eta = 0.1$. Start at $w_0 = 2$. Compute $w_1$ and $w_2$.

**E2.** Write the GD update rule. What happens if $\eta = 0$? If $\eta$ is very large?

**E3.** For MSE, write the gradient w.r.t. $w$ and $b$. What is the residual $r_i$?

**E4.** What is the difference between batch GD, SGD, and mini-batch GD?

### [Intermediate]

**E5.** Implement GD for scalar linear regression. $x = [1, 2, 3, 4]$, $y = [2, 4, 6, 8]$. Start $w=0, b=0$, $\eta=0.01$. Run 100 steps. What are the final $w, b$? What are the OLS solutions?

**E6.** For $f(w) = w^2$: (a) For what $\eta$ does GD converge? (b) What is the optimal $\eta$ (one-step convergence)? (c) What happens at $\eta = 1.0$?

**E7.** Explain why feature scaling helps GD converge faster. Draw the loss surface before and after scaling.

**E8.** The ridge update includes $-2\eta\lambda w$. What does this term do? What happens as $\lambda \to \infty$?

### [★ Advanced]

**E9.** Show that for $f(w) = \frac{1}{2}aw^2$, the optimal learning rate (maximizing loss decrease in one step) is $\eta^* = 1/a$. (Exact line search.)

**E10.** ★★ Show that the expected value of the SGD update equals the batch GD update. (SGD is unbiased.)

**E11.** ★★ **Momentum:** $v_t = \gamma v_{t-1} + \eta \nabla L(w_t)$, $w_{t+1} = w_t - v_t$. (a) What does momentum do? (b) How does it help with the zigzag problem?

**E12.** ★★ For $L(w) = \frac{1}{2}(w - c)^2 + \lambda|w|$ with $c > 0$: (a) Find the minimizer. (b) For what $\lambda$ is $w^* = 0$? (This is the **soft-thresholding operator**.)

---

## 10. Connections

| Next Week | How It Uses Week 6 |
|-----------|-------------------|
| Week 7: Logistic Regression | GD trains logistic regression (cross-entropy gradient). |
| Week 8: Matrix Linear Regression | GD in vector form. |
| Week 15–16: Neural Networks | GD + chain rule = backpropagation. |
| Week 17: Training Neural Networks | Adam, momentum, schedules — all extensions of Week 6. |
| Week 18: Generalization Theory | Why GD generalizes: implicit regularization. |

---

*Next week: Logistic Regression. We'll combine the probability from Week 5 (MLE for Bernoulli → cross-entropy loss) with the gradient descent from this week to build our first classification model.*
