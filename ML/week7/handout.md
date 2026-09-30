# Week 7 Handout: Consolidation & Logistic Regression I — From Regression to Classification

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 7 of 44  
> **Sessions:** 4 (70 min each)  
> **Prerequisites:** Weeks 1–6 (linear regression, overfitting & regularization, model evaluation, probability/MLE/MAP, gradient descent concept)  
> **Assumed background:** Derivatives, partial derivatives, chain rule (calculus course). Random variables, Bayes' theorem, Bernoulli and Gaussian distributions (probability course).

> **Schedule note:** After the two-week break, the course moves to **4 sessions of 70 minutes per week**. This week we (1) actively review Weeks 1–6, (2) complete the derivations and gradient-descent topics that were introduced conceptually but not finished, and (3) begin logistic regression — our second complete ML model and our first classifier.

---

## The Week at a Glance

| Session | Focus | Key Deliverable |
|---------|-------|-----------------|
| S1 | **Review I: The regression story (Weeks 1–4).** Pipeline, OLS/ridge, overfitting, evaluation. | Weeks 1–4 fully recalled |
| S2 | **Review II + Completing probability (Weeks 5–6).** MAP = Ridge, Laplacian → Lasso, full bias-variance derivation. | The three deep connections |
| S3 | **Completing gradient descent (Week 6).** GD by hand, learning rate regimes, the MSE gradient, SGD/mini-batch. | GD fully operational |
| S4 | **Logistic regression I.** Sigmoid, the model, decision boundary, cross-entropy = negative log-likelihood. | First classifier, third deep connection |

---

# Part I: The Map of Weeks 1–6 (Sessions 1–2)

## 1. The Story So Far

1. **Week 1 — The problem.** Learning = function approximation. An ML problem is specified by: input space $X$, output space $Y$, hypothesis space $H$, loss function $L$. We care about **generalization** — performance on unseen data.
2. **Week 2 — The first model.** $\hat{y} = wx + b$, MSE loss, closed-form OLS: $w^* = \text{Cov}(x,y)/\text{Var}(x)$, $b^* = \bar{y} - w^*\bar{x}$. Ridge: add $\lambda w^2$.
3. **Week 3 — The central tension.** Overfitting vs. underfitting. Complexity controls (degree, $\lambda$) all turn the same dial. L1 (sparse) vs. L2 (shrink) geometry.
4. **Week 4 — The judge.** Train/validation/test, the golden rule, k-fold CV, data leakage. Classification metrics: confusion matrix, precision/recall/F1, ROC/AUC. When accuracy lies (class imbalance).
5. **Week 5–6 — The probability lens + the engine.** Bayes for ML, MLE (Bernoulli → sample mean; Gaussian → sample mean/variance), **MLE = MSE**, **MAP = Ridge**, bias-variance decomposition. Gradient descent: the iterative engine that minimizes any loss.

## 2. Master Formula Sheet

| Week | Key Idea | Key Formula |
|------|----------|-------------|
| W1 | Learning = function approximation | $(X, Y, H, L)$ |
| W2 | OLS (closed form) | $w^* = \frac{\text{Cov}(x,y)}{\text{Var}(x)},\quad b^* = \bar{y} - w^*\bar{x}$ |
| W2 | Ridge (closed form) | $w^*_{\text{ridge}} = \frac{\text{Cov}(x,y)}{\text{Var}(x) + \lambda}$ |
| W3 | Complexity dial | training error ↓ with complexity; test error is U-shaped |
| W4 | Precision / Recall / F1 | $\frac{TP}{TP+FP}$, $\frac{TP}{TP+FN}$, $\frac{2PR}{P+R}$ |
| W4 | AUC | $P(\text{score}(+) > \text{score}(-))$ |
| W5 | Bayes for ML | posterior $\propto$ likelihood × prior |
| W5 | MLE (Bernoulli) | $\hat{\theta} = \frac{1}{n}\sum_i x_i$ |
| W5 | MLE (Gaussian) | $\hat{\mu} = \bar{x},\quad \hat{\sigma}^2 = \frac{1}{n}\sum_i (x_i - \bar{x})^2$ |
| W5/6 | **MLE = MSE** | Gaussian noise ⇒ minimize $\sum_i (y_i - wx_i - b)^2$ |
| W5/6 | **MAP = Ridge** | Gaussian prior ⇒ $\lambda = \sigma^2/\tau^2$ |
| W6 | GD update | $\mathbf{w} \leftarrow \mathbf{w} - \eta \nabla L(\mathbf{w})$ |

## 3. Self-Check Question Bank (use before/during the review sessions)

1. Define all four components of the ML problem setup. Which one encodes "what we're allowed to learn"?
2. Derive $w^* = \text{Cov}(x,y)/\text{Var}(x)$ from scratch (you did this in Week 2 with algebra only).
3. Why does training error *always* decrease as polynomial degree increases? Why is this misleading?
4. Sketch the L2 ball and the L1 diamond. Why does L1 produce exact zeros?
5. State the golden rule of the test set. What is data leakage?
6. When is a PR curve better than ROC? What does AUC measure?
7. Derive MLE for the Bernoulli. Where does the log-likelihood trick help?
8. Show that maximizing the Gaussian log-likelihood = minimizing MSE.
9. What are the three learning-rate regimes? What is the convergence condition for $f(w) = \frac{1}{2}aw^2$?
10. Write the GD update rules for linear regression in terms of the residuals $r_i = y_i - wx_i - b$.

---

# Part II: Completing the Probability Story (Session 2)

## 4. MAP = Ridge Regression (Full Derivation)

**The MAP principle.** Maximize the *posterior* over parameters:

$$\hat{w}_{\text{MAP}} = \arg\max_w \; p(w \mid \mathcal{D}) \propto p(\mathcal{D} \mid w)\, p(w)$$

"MAP = MLE + prior." The log-prior acts as a **penalty**.

**Setup.** Same model as Week 5: $y_i = wx_i + b + \epsilon_i$, $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$, but now place a **Gaussian prior** on the weight: $w \sim \mathcal{N}(0, \tau^2)$.

**Step 1 — the two ingredients:**

$$\log p(\mathcal{D} \mid w, b) = \text{const} - \frac{1}{2\sigma^2}\sum_{i=1}^n (y_i - wx_i - b)^2, \qquad \log p(w) = \text{const} - \frac{w^2}{2\tau^2}$$

**Step 2 — add them** (log of product = sum of logs). MAP minimizes the negative log posterior:

$$\frac{1}{2\sigma^2}\sum_{i=1}^n (y_i - wx_i - b)^2 + \frac{1}{2\tau^2}w^2$$

**Step 3 — multiply by $2\sigma^2$** (positive constant, doesn't change the minimizer):

$$\sum_{i=1}^n (y_i - wx_i - b)^2 + \frac{\sigma^2}{\tau^2}w^2 \;=\; n \cdot \text{MSE}(w,b) + \lambda w^2$$

$$\boxed{\text{Ridge} = \text{MAP with Gaussian noise} \times \text{Gaussian prior}, \qquad \lambda = \frac{\sigma^2}{\tau^2}}$$

**Interpretation of $\lambda = \sigma^2/\tau^2$ (noise-to-prior ratio):**

| Scenario | Meaning | Effect on $\lambda$ |
|----------|---------|--------------------|
| Noisy data ($\sigma^2$ large) | Data is unreliable → trust the prior | Large → strong shrinkage |
| Tight prior ($\tau^2$ small) | We strongly believe $w \approx 0$ | Large → strong shrinkage |
| Clean data ($\sigma^2$ small) | Trust the data | Small → weak shrinkage |
| Loose prior ($\tau^2$ large) | Let the data decide | Small → weak shrinkage |

> **This is not a coincidence.** Regularization is not an ad-hoc trick — it is Bayesian reasoning. Every penalty is a prior in disguise.

## 5. The Laplacian Prior → Lasso

**Laplacian prior:** $p(w) = \frac{1}{2\tau} e^{-|w|/\tau}$ — sharp peak at $w = 0$, heavy tails.

$$-\log p(w) = \frac{|w|}{\tau} + \text{const}$$

**MAP objective** (multiply by $\sigma^2$ as before):

$$\sum_{i=1}^n (y_i - wx_i - b)^2 + \frac{\sigma^2}{\tau}|w| = n \cdot \text{MSE} + \lambda |w|, \qquad \lambda = \frac{\sigma^2}{\tau}$$

$$\boxed{\text{Lasso} = \text{MAP with Gaussian noise} \times \text{Laplacian prior}, \qquad \lambda = \frac{\sigma^2}{\tau}}$$

**Why sparsity?** The Laplacian has a *non-differentiable corner* at $w = 0$ (Week 3's L1 diamond). The Gaussian is smooth and flat at 0, so ridge shrinks *toward* zero but (in general) never reaches it; the Laplacian's corner pushes the solution *exactly onto* zero.

| Prior | Shape at 0 | Penalty | Result |
|-------|-----------|---------|--------|
| Gaussian $\mathcal{N}(0, \tau^2)$ | smooth, flat | $\lambda w^2$ (L2) | shrinkage toward 0 |
| Laplacian | sharp corner | $\lambda \lvert w \rvert$ (L1) | exact zeros, sparsity |

## 6. The Full Bias-Variance Decomposition

**Setup.** $y = f(x) + \epsilon$ with $\epsilon \sim \mathcal{N}(0, \sigma^2)$ (noise independent of the training data $\mathcal{D}$). A learning algorithm trained on $\mathcal{D}$ produces $\hat{f}(x)$. We measure the **expected test error** at a fixed point $x$, over random training sets and random noise:

$$\mathbb{E}\big[(y - \hat{f}(x))^2\big]$$

**Step 1 — the decomposition trick.** Let $\bar{f}(x) = \mathbb{E}_\mathcal{D}[\hat{f}(x)]$ (the *average* model over all possible training sets). Write

$$y - \hat{f} = \underbrace{(f - \bar{f})}_{A} + \underbrace{(\bar{f} - \hat{f})}_{B} + \underbrace{\epsilon}_{C}$$

**Step 2 — expand the square.**

$$\mathbb{E}[(A+B+C)^2] = \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$$

**Step 3 — the cross terms vanish.** *(This is the step we owed since Week 5.)*

- $2\mathbb{E}[AB] = 0$: $A$ is constant given $x$; $\mathbb{E}[B] = \mathbb{E}[\bar{f} - \hat{f}] = 0$ by definition of $\bar{f}$.
- $2\mathbb{E}[AC] = 0$: $A$ is constant; $\mathbb{E}[\epsilon] = 0$.
- $2\mathbb{E}[BC] = 0$: $\epsilon$ is independent of $\mathcal{D}$ (hence of $\hat{f}$), and $\mathbb{E}[\epsilon] = 0$.

**Step 4 — name the surviving terms.**

$$\boxed{\mathbb{E}\big[(y - \hat{f}(x))^2\big] = \underbrace{(f - \bar{f})^2}_{\text{Bias}^2} + \underbrace{\mathbb{E}\big[(\hat{f} - \bar{f})^2\big]}_{\text{Variance}} + \underbrace{\sigma^2}_{\text{irreducible}}}$$

| Term | Meaning | Reduced by |
|------|---------|-----------|
| Bias$^2$ | Systematic error: how far the *average* model is from the truth | More complex model, more features |
| Variance | Instability: how much the model changes with the training set | More data, regularization, simpler model |
| $\sigma^2$ | Noise floor | **Nothing.** It's in the data, not the model. |

**The tradeoff.** Increasing complexity: bias ↓, variance ↑. This is now a *theorem*, not an observation — it is the mathematical form of Week 3's complexity dial.

**Connections:**
- **Week 3:** $\lambda = 0$ → low bias, high variance; $\lambda \to \infty$ → $\hat{f} \equiv \bar{y}$: high bias, zero variance.
- **Week 4:** learning-curve diagnosis — gap between training and validation error = variance; both high together = bias.

## 7. The Three Deep Connections (Summary)

Linear regression can be derived three independent ways, and they agree:

| View | Question answered | Result |
|------|-------------------|--------|
| **Geometry** (W2, W8) | Which line is closest to the points? | Minimize vertical distances (MSE, projection) |
| **Probability** (W5–6) | Which parameters make the data most likely? | MLE = OLS; MAP = Ridge/Lasso |
| **Optimization** (W6) | How do we actually find the minimum? | Gradient descent |

One model, three lenses. In Week 8 we will see all three again in matrix form.

---

# Part III: Completing Gradient Descent (Session 3)

## 8. GD Step-by-Step on a 1D Quadratic

Minimize $f(w) = w^2$. Gradient (derivative): $f'(w) = 2w$. Update: $w \leftarrow w - \eta \cdot 2w$.

Start at $w_0 = 3$ with $\eta = 0.1$:

| Step | $w$ | $f(w)$ | $f'(w)$ | Step size $\eta f'(w)$ |
|------|-----|--------|---------|------------------------|
| 0 | 3.000 | 9.000 | 6.000 | 0.600 |
| 1 | 2.400 | 5.760 | 4.800 | 0.480 |
| 2 | 1.920 | 3.686 | 3.840 | 0.384 |
| 3 | 1.536 | 2.359 | 3.072 | 0.307 |
| 4 | 1.229 | 1.510 | 2.458 | 0.246 |
| ... | ... | ... | ... | ... |
| 20 | 0.036 | 0.001 | 0.072 | 0.007 |

**Geometric decay:** $w_{t+1} = w_t(1 - 2\eta)$. With $\eta = 0.1$: each step multiplies $w$ by $0.8$. After $t$ steps: $w_t = 3 \times 0.8^t \to 0$.

## 9. Learning-Rate Regimes and Convergence

For a general quadratic $f(w) = \frac{1}{2}aw^2$ (so $f'(w) = aw$):

$$w_{t+1} = w_t(1 - \eta a)$$

| Regime | Condition | Behavior |
|--------|-----------|----------|
| Too small | $\eta \ll 1/a$ | Slow crawl; many steps |
| Just right | $\eta \approx 1/a$ | Converges fastest ($\eta = 1/a$: one step!) |
| Too large | $\eta > 2/a$ | $|1 - \eta a| > 1$: oscillates and **diverges** |

$$\boxed{\text{Convergence for quadratics: } |1 - \eta a| < 1 \iff 0 < \eta < \frac{2}{a}}$$

**Diagnostic rule of thumb:**
- Loss decreasing slowly → $\eta$ too small.
- Loss oscillating or exploding → $\eta$ too large.
- Loss decreasing steadily → good.

## 10. Convexity (Why GD Works for MSE)

A function is **convex** if the line segment between any two points on its graph lies above the graph. Consequences:

- A convex function has **one global minimum** (no local minima to get stuck in).
- For convex $L$, GD with small enough $\eta$ converges to the global minimum.

**MSE for linear regression is convex in $(w, b)$** — a paraboloid. **Ridge: also convex.** Lasso: convex but non-smooth (the $|w|$ corner — handled by *subgradients*, Section 12). Neural networks (Week 15+): **not convex** — initialization and SGD noise will matter.

## 11. The MSE Gradient — Chain Rule at Work

**Goal:** run GD on $\text{MSE}(w,b) = \frac{1}{n}\sum_{i=1}^n (y_i - wx_i - b)^2$. Let $r_i = y_i - wx_i - b$ (the **residual**).

**Chain rule pattern:** outer derivative × inner derivative.

$$\frac{\partial}{\partial w} r_i^2 = 2r_i \cdot \frac{\partial r_i}{\partial w} = 2r_i \cdot (-x_i) = -2x_i r_i$$

$$\boxed{\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_{i=1}^n x_i r_i, \qquad \frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_{i=1}^n r_i}$$

**The GD updates become:**

$$w \leftarrow w + \frac{2\eta}{n}\sum_{i=1}^n x_i r_i, \qquad b \leftarrow b + \frac{2\eta}{n}\sum_{i=1}^n r_i$$

> **Read the update in words:** each data point *pulls* the line toward itself with strength proportional to its residual $r_i$ (how wrong the model currently is on that point) and its input $x_i$. Points the model gets right ($r_i = 0$) contribute nothing.

**The optimality condition.** At the minimum, the gradient is zero:

$$\sum_{i=1}^n x_i r_i = 0 \qquad \text{and} \qquad \sum_{i=1}^n r_i = 0$$

This says: **at the OLS solution, residuals are uncorrelated with the inputs and have zero mean.** GD converges to exactly the closed-form solution from Week 2 — the two routes to OLS agree.

## 12. Ridge and Lasso by Gradient Descent

**Ridge GD** (add $\lambda w^2$ to the loss):

$$\frac{\partial}{\partial w}\left(\text{MSE} + \lambda w^2\right) = -\frac{2}{n}\sum x_i r_i + 2\lambda w \quad\Longrightarrow\quad w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - 2\eta\lambda w$$

The extra term $-2\eta\lambda w$ is **shrinkage**: every step, $w$ is also multiplied by $(1 - 2\eta\lambda) < 1$ and pulled toward zero. Same effect as the closed-form denominator $\text{Var}(x) + \lambda$ — reached step by step.

**Lasso GD** (subgradient of $|w|$ at $w = 0$ is the interval $[-1, 1]$; take $\text{sgn}(w)$):

$$w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - \eta\lambda \, \text{sgn}(w)$$

The term $-\eta\lambda\,\text{sgn}(w)$ pushes $w$ toward zero at **constant speed**. When $w$ gets close to zero, it does not slow down (unlike ridge's proportional pull) — it crosses exactly to $0$. **This is why lasso produces exact zeros.**

## 13. Batch GD, SGD, and Mini-Batch

| Property | Batch GD | SGD (1 example) | Mini-batch ($B$ examples) |
|----------|----------|-----------------|---------------------------|
| Gradient per step | all $n$ examples | 1 random example | $B$ random examples ($B = 32$–$128$) |
| Cost per step | high | very low | low |
| Gradient quality | exact | noisy, unbiased | slightly noisy |
| Trajectory | smooth | bouncy | mildly bouncy |
| Typical use | small problems, theory | streaming data | **the standard in modern ML** |

- **Epoch:** one full pass through the training data. With $n = 1000$ and $B = 100$: one epoch = 10 updates.
- SGD's gradient is **unbiased**: $\mathbb{E}[\nabla L_i] = \nabla L$. The noise averages out over many steps.
- The noise is **useful** for non-convex problems (neural networks): it can kick GD out of bad regions. For convex problems it just makes the path bumpy.
- Mini-batch variance scales as $1/B$: bigger batch = smoother but costlier steps.

## 14. Feature Scaling (and Leakage)

If features have very different scales, the loss surface becomes an **elongated ellipse**: GD zigzags across the narrow valley instead of descending straight to the bottom.

**Fix — standardization:** $x_j \to (x_j - \bar{x}_j)/\sigma_j$ for each feature $j$. Now the surface is nearly spherical and one learning rate works for all directions.

> **Golden-rule connection (Week 4):** compute $\bar{x}_j, \sigma_j$ on the **training set only**, *after* splitting. Computing them on the full dataset leaks test information into training — data leakage.

## 15. Monitoring Training: Loss Curves

Plot training loss (and validation loss) vs. epoch:

| Pattern | Diagnosis | Fix |
|---------|-----------|-----|
| Steady decrease, then plateau | healthy convergence | done |
| Decrease too slow | $\eta$ too small | raise $\eta$ |
| Oscillation / explosion | $\eta$ too large | lower $\eta$ |
| Training ↓, validation ↓ then ↑ | overfitting (variance) | regularize, more data, early stop |
| Both high, small gap | underfitting (bias) | more complex model / features |

---

# Part IV: Logistic Regression I (Session 4)

## 16. From Regression to Classification

**New task:** $y \in \{0, 1\}$ (spam / not spam, disease / healthy, pass / fail).

**Why not linear regression?** Fitting $\hat{y} = wx + b$ to 0/1 targets gives predictions outside $[0, 1]$, is sensitive to outliers far from the boundary, and doesn't give calibrated probabilities.

**What we actually want:** a model of $P(y = 1 \mid x)$ — a number in $[0, 1]$. Then classify by thresholding: predict 1 if $P(y=1\mid x) > 0.5$.

**Why not optimize accuracy directly?** Accuracy counts errors — the **0-1 loss**. It is piecewise constant: tiny changes in $w$ either change no prediction or flip one. The gradient is zero almost everywhere (and undefined elsewhere). **We need a smooth surrogate** that is high when the model is confidently wrong and low when it is confidently right.

## 17. The Sigmoid Function

$$\boxed{\sigma(z) = \frac{1}{1 + e^{-z}}}$$

**Properties (verify each):**

1. **Range:** $0 < \sigma(z) < 1$ for all $z$ — a probability.
2. **Endpoint values:** $\sigma(0) = \frac{1}{2}$; $\sigma(z) \to 1$ as $z \to +\infty$; $\sigma(z) \to 0$ as $z \to -\infty$.
3. **Symmetry:** $\sigma(-z) = 1 - \sigma(z)$.
4. **Monotone increasing**, S-shaped ("squashing function").
5. **The miracle derivative:**

$$\boxed{\sigma'(z) = \sigma(z)\big(1 - \sigma(z)\big)}$$

*Proof:* $\sigma'(z) = \frac{e^{-z}}{(1+e^{-z})^2} = \frac{1}{1+e^{-z}} \cdot \frac{e^{-z}}{1+e^{-z}} = \sigma(z)\big(1 - \sigma(z)\big)$. $\blacksquare$

The derivative is expressible **in terms of the function itself** — no new computation needed. Maximum slope at $z = 0$ (value $\tfrac{1}{4}$); slope $\to 0$ as $z \to \pm\infty$ (**saturation**).

## 18. The Logistic Model and Its Decision Boundary

$$\boxed{P(y = 1 \mid x) = \sigma(wx + b), \qquad \hat{y} = 1 \iff wx + b > 0}$$

- The model outputs a **probability**; the classification is a thresholding of it.
- **The decision boundary is the line $wx + b = 0$** — linear, exactly like regression, but now separating two classes.
- Points *far* from the boundary on the correct side: $P \approx 1$ (confident). Points on the boundary: $P = \frac{1}{2}$ (uncertain).
- In 2D ($w_1 x_1 + w_2 x_2 + b$): the boundary is a line; $w$ is its normal vector; $|b|/\lVert w \rVert$ is the distance from the origin.

## 19. Cross-Entropy = Negative Log-Likelihood

**Everything from Week 5 applies.** The label $y_i$ is a coin flip with success probability $\hat{p}_i = \sigma(wx_i + b)$ depending on the input:

$$P(y_i \mid x_i, w, b) = \hat{p}_i^{\,y_i}\,(1 - \hat{p}_i)^{\,1 - y_i} \qquad \text{(Bernoulli)}$$

**Likelihood of the whole dataset** (i.i.d.):

$$p(\mathcal{D} \mid w, b) = \prod_{i=1}^n \hat{p}_i^{\,y_i}(1 - \hat{p}_i)^{1 - y_i}$$

**Log-likelihood:**

$$\ell(w, b) = \sum_{i=1}^n \Big[ y_i \log \hat{p}_i + (1 - y_i)\log(1 - \hat{p}_i) \Big]$$

**MLE = maximize $\ell$ = minimize the negative log-likelihood** — which is exactly the **binary cross-entropy**:

$$\boxed{L(w, b) = -\frac{1}{n}\sum_{i=1}^n \Big[ y_i \log \hat{p}_i + (1 - y_i)\log(1 - \hat{p}_i) \Big], \qquad \hat{p}_i = \sigma(wx_i + b)}$$

**This is the third entry in the correspondence table:**

| Noise / label model | Likelihood | Loss |
|---------------------|-----------|------|
| Gaussian | $\prod \mathcal{N}(y_i \mid wx_i + b, \sigma^2)$ | **MSE** |
| Laplacian | $\prod \text{Lap}(y_i \mid wx_i + b, \tau)$ | **MAE** |
| **Bernoulli** | $\prod \hat{p}_i^{y_i}(1-\hat{p}_i)^{1-y_i}$ | **cross-entropy** |

**Behavior check (why cross-entropy is the right shape):**

| Situation | Contribution to loss |
|-----------|----------------------|
| $y_i = 1$, $\hat{p}_i \to 1$ (right, confident) | $\to 0$ |
| $y_i = 1$, $\hat{p}_i \to 0$ (wrong, confident) | $\to \infty$ — **punished without mercy** |
| $\hat{p}_i = \frac{1}{2}$ (uncertain) | $\log 2 \approx 0.69$ regardless of $y_i$ |

Cross-entropy is a **smooth, convex surrogate** for the 0-1 loss — exactly what Section 16 demanded.

**Regularized logistic regression (one line):** by Section 4, MAP with a Gaussian prior adds $\lambda w^2$ to the loss; a Laplacian prior adds $\lambda |w|$. The whole Week 3 story carries over unchanged.

## 20. ★ Preview: The Gradient and the Beautiful Cancellation

*(Derived in full in Week 8, Session 1. Strong students should attempt it now.)*

Differentiating the cross-entropy for one example, using the chain rule with $\hat{p} = \sigma(z)$, $z = wx + b$:

$$\frac{\partial}{\partial \hat{p}}\Big[-y\log\hat{p} - (1-y)\log(1-\hat{p})\Big] = \frac{\hat{p} - y}{\hat{p}(1 - \hat{p})}$$

$$\frac{\partial \hat{p}}{\partial w} = \underbrace{\sigma'(z)}_{=\ \hat{p}(1-\hat{p})} \cdot x$$

**Multiply** — and the denominator of the first factor cancels exactly against $\sigma' = \hat{p}(1-\hat{p})$:

$$\boxed{\frac{\partial L_i}{\partial w} = (\hat{p}_i - y_i)\,x_i, \qquad \frac{\partial L_i}{\partial b} = \hat{p}_i - y_i}$$

The residual $\hat{p}_i - y_i$ appears again — the same structure as the MSE gradient (Section 11), with the *probability error* replacing the *value error*. Note: no $\sigma'$ factor survives, so **saturated neurons still send a clear gradient signal** — this is precisely why we don't use MSE on top of a sigmoid (there, the $\hat{p}(1-\hat{p})$ factor *stays* and vanishes when the model saturates).

## 21. ★ Odds and Log-Odds

The **odds** of an event with probability $p$ are $\frac{p}{1-p}$. For the logistic model:

$$\log\frac{P(y=1\mid x)}{P(y=0\mid x)} = wx + b$$

**Logistic regression is linear regression on the log-odds.** Interpretation: increasing $x$ by one unit multiplies the odds by $e^w$. This is why logistic regression remains the default interpretable model in medicine and social science ("odds ratio").

## 22. ★ Optimal Thresholds and Cost-Sensitive Classification

Thresholding at $0.5$ is only optimal under symmetric costs. If a false positive costs $c_{FP}$ and a false negative costs $c_{FN}$, the optimal threshold is:

$$t^* = \frac{c_{FP}}{c_{FP} + c_{FN}}$$

Example: cancer screening ($c_{FN}$ huge) → $t^*$ small → predict "disease" easily (high recall). This is the Week 4 precision/recall tradeoff, now with the dial that turns it. *(Derivation exercise: Challenge 7-4C.)*

---

## Connections to What's Next

| Next topic | Connection to this week |
|------------|------------------------|
| Week 8 S1: training logistic regression (GD, the cancellation in full) | Sections 19–20; GD machinery from Part III |
| Week 8 S2: softmax regression (multi-class) | Section 17's sigmoid generalizes to softmax; cross-entropy generalizes naturally |
| Week 8 S3–S4: matrix linear regression + Phase 1 consolidation | The three deep connections (Section 7), now in matrix form |
| Week 15+: neural networks | Logistic regression = a 0-hidden-layer neural network; $\sigma$ is an activation function; cross-entropy is the standard classification loss |
