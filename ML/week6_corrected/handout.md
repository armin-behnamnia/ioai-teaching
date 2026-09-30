# Week 6 (Corrected) Handout: Probability Foundations + Optimization Basics — Gradient Descent

> **Course:** Machine Learning for IOAI Preparation
> **Week:** 6 of 44 (Corrected — incorporates Week 5 catch-up)
> **Sessions:** 2 (80 min each)
> **Prerequisites:** Week 2 (scalar linear regression, MSE, OLS, ridge), Week 3 (overfitting & regularization, lasso has no closed form), Week 4 (model evaluation, classification metrics, cross-validation, learning curves)
> **Assumed background:** Your probability course has covered random variables, PMF/PDF, expectation, variance, joint/marginal/conditional distributions, Bayes' theorem, and basic distributions (Bernoulli, Gaussian). Your calculus course has covered derivatives, partial derivatives, and the chain rule.

> **Correction note:** In Week 5, we covered evaluation metrics review, train/val/test, k-fold, and the *concepts* of MLE/MAP (without derivations). We began but did not finish the bias-variance decomposition. This corrected Week 6 delivers the missing Week 5 derivations in Session 1, then proceeds to the full Week 6 gradient descent content in Session 2.

---

## Session 1 Roadmap: Completing Week 5 — Probability for ML

### What We Covered in Week 5 (Recap)

In Week 5, we established:
- **Classification metrics review:** TP/FP/TN/FN, TPR/FPR, precision/recall/F1, negative recall/precision
- **Train/validation/test pipeline:** the golden rule (never touch test during model selection), k-fold cross-validation
- **MLE and MAP concepts:** MLE = find the parameter that makes the data most likely; MAP = MLE + prior. We discussed these *without* concrete derivations.
- **Started the bias-variance decomposition:** began decomposing the expected squared error but did not complete it.

### What We Will Complete Today

| Topic | Status in Week 5 | What We Do Now |
|-------|------------------|----------------|
| Bayes' theorem applied to ML | Not covered | **Full treatment with examples** |
| MLE for Bernoulli | Concept only | **Full derivation** |
| MLE for Gaussian | Not covered | **Full derivation** |
| MLE = MSE proof | Not covered | **The key proof** |
| MAP = Ridge proof | Concept only | **Full derivation** |
| Laplacian prior → Lasso | Not covered | **Full derivation** |
| Bias-variance decomposition | Started, not finished | **Complete derivation** |

---

## 1. Bayes' Theorem Applied to ML

### 1.1 The ML Interpretation

You know Bayes' theorem. In ML, we rename the variables:

$$\underbrace{p(\theta \mid \mathcal{D})}_{\text{posterior}} = \frac{\overbrace{p(\mathcal{D} \mid \theta)}^{\text{likelihood}} \, \overbrace{p(\theta)}^{\text{prior}}}{\underbrace{p(\mathcal{D})}_{\text{evidence}}}$$

| Term | Name | ML Meaning |
|------|------|---------|
| $p(\theta)$ | **Prior** | What we believe about parameters $\theta$ before seeing data |
| $p(\mathcal{D} \mid \theta)$ | **Likelihood** | How likely the data is, if $\theta$ were the true parameter |
| $p(\mathcal{D})$ | **Evidence** | Total probability of the data (normalizing constant) |
| $p(\theta \mid \mathcal{D})$ | **Posterior** | What we believe about $\theta$ after seeing data |

**The Bayesian learning loop:**

$$\text{Prior} \xrightarrow{\text{observe data}} \text{Posterior}$$

> **This IS learning, mathematically.** You start with a belief (prior). You observe data. You update your belief using Bayes' theorem. The posterior is your updated belief.

### 1.2 The Evidence (and Why We Often Drop It)

The evidence $p(\mathcal{D}) = \int p(\mathcal{D} \mid \theta) \, p(\theta) \, d\theta$ requires integrating over all possible $\theta$. This is often intractable.

**Key insight:** For *optimization* (finding the best $\theta$), the evidence doesn't depend on $\theta$ — it's a constant. So we can work with the **unnormalized posterior**:

$$p(\theta \mid \mathcal{D}) \propto p(\mathcal{D} \mid \theta) \, p(\theta)$$

### 1.3 Example: Medical Testing = Class Imbalance

**Setup:** A disease affects 1% of the population. A test is 99% sensitive (TPR) and 95% specific (TNR). If you test positive, what's $P(\text{disease} \mid \text{positive})$?

- Prior: $P(\text{disease}) = 0.01$
- Likelihood: $P(\text{positive} \mid \text{disease}) = 0.99$
- $P(\text{positive} \mid \text{no disease}) = 0.05$ (FPR)

$$P(\text{disease} \mid \text{positive}) = \frac{0.99 \times 0.01}{0.99 \times 0.01 + 0.05 \times 0.99} = \frac{0.0099}{0.0594} = \frac{1}{6} \approx 16.7\%$$

> **ML connection (Week 4):** This is EXACTLY the class imbalance problem. $P(\text{disease} \mid \text{positive})$ is the same as **precision** from Week 4. When the positive class is rare (1%), even a good test generates more false positives than true positives.

---

## 2. Maximum Likelihood Estimation (MLE)

### 2.1 The Principle

> **MLE:** Given data $\mathcal{D} = \{x_1, \ldots, x_n\}$ from a distribution $p(x \mid \theta)$, find the $\theta$ that makes the data **most probable**:

$$\hat{\theta}_{\text{MLE}} = \arg\max_\theta p(\mathcal{D} \mid \theta)$$

### 2.2 The Log-Likelihood Trick

Assuming i.i.d. data, the likelihood is a product:

$$p(\mathcal{D} \mid \theta) = \prod_{i=1}^{n} p(x_i \mid \theta)$$

Products are numerically unstable (underflow). We take the **log** (monotonic, so the maximizer is unchanged):

$$\ell(\theta) = \log p(\mathcal{D} \mid \theta) = \sum_{i=1}^{n} \log p(x_i \mid \theta)$$

### 2.3 MLE for the Bernoulli (Full Derivation)

Data: $x_1, \ldots, x_n \in \{0, 1\}$, i.i.d. Bernoulli($\theta$).

**Likelihood:** $\prod_i \theta^{x_i}(1-\theta)^{1-x_i}$

**Log-likelihood:** Let $k = \sum_i x_i$ (number of ones).

$$\ell(\theta) = k \log \theta + (n - k) \log(1 - \theta)$$

**Differentiate and solve:**

$$\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n - k}{1 - \theta} = 0 \quad \Longrightarrow \quad \boxed{\hat{\theta}_{\text{MLE}} = \frac{k}{n} = \frac{1}{n}\sum_{i=1}^{n} x_i}$$

> The MLE for a Bernoulli is the **sample mean**. Flip a coin 100 times, get 60 heads → MLE of $P(\text{heads}) = 0.60$.

### 2.4 MLE for the Gaussian

Data: $x_1, \ldots, x_n \sim \mathcal{N}(\mu, \sigma^2)$.

$$\ell(\mu, \sigma^2) = -\frac{n}{2}\log(2\pi) - \frac{n}{2}\log(\sigma^2) - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(x_i - \mu)^2$$

Maximizing w.r.t. $\mu$ = minimizing $\sum_i (x_i - \mu)^2$.

$$\boxed{\hat{\mu}_{\text{MLE}} = \bar{x}, \qquad \hat{\sigma}^2_{\text{MLE}} = \frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^2}$$

---

## 3. The Deep Connection: MLE = MSE

### 3.1 The Setup

**Model:** $y_i = wx_i + b + \epsilon_i$, where $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$.

This means: $y_i \mid x_i, w, b \sim \mathcal{N}(wx_i + b, \sigma^2)$.

### 3.2 The Likelihood

$$p(\mathcal{D} \mid w, b, \sigma^2) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi\sigma^2}} \exp\!\left(-\frac{(y_i - wx_i - b)^2}{2\sigma^2}\right)$$

### 3.3 The Log-Likelihood

$$\ell(w, b) = -\frac{n}{2}\log(2\pi\sigma^2) - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2$$

### 3.4 The Key Step

The first term is constant. The second term is **proportional to MSE**:

$$\ell(w, b) = \text{const} - \frac{1}{2\sigma^2}\underbrace{\sum_{i=1}^{n}(y_i - wx_i - b)^2}_{n \cdot \text{MSE}(w, b)}$$

**Maximizing** $\ell(w, b)$ is equivalent to **minimizing** MSE.

$$\boxed{\hat{w}_{\text{MLE}} = \hat{w}_{\text{OLS}} = \arg\min_w \text{MSE}(w, b)}$$

> **The deep connection:** Minimizing MSE is not arbitrary. It is the maximum likelihood estimator under Gaussian noise.

### 3.5 The MLE ↔ Loss Function Correspondence Table

| Noise Model | Likelihood | → Loss Function | Used When |
|-------------|------------|----------------|-----------|
| **Gaussian** $\mathcal{N}(0, \sigma^2)$ | $\prod_i \exp\!\left(-\frac{(y_i - \hat{y}_i)^2}{2\sigma^2}\right)$ | **MSE:** $\frac{1}{n}\sum_i (y_i - \hat{y}_i)^2$ | Regression (continuous target) |
| **Bernoulli** $\text{Ber}(\theta)$ | $\prod_i \theta^{y_i}(1-\theta)^{1-y_i}$ | **Cross-entropy:** $-\sum_i [y_i \log \hat{y}_i + (1-y_i)\log(1-\hat{y}_i)]$ | Binary classification (Week 7) |
| **Laplacian** (double exponential) | $\prod_i \exp\!\left(-\frac{|y_i - \hat{y}_i|}{b}\right)$ | **MAE:** $\frac{1}{n}\sum_i |y_i - \hat{y}_i|$ | Robust regression (outliers) |

---

## 4. Maximum a Posteriori (MAP)

### 4.1 From MLE to MAP

**MAP estimation** uses Bayes' theorem to combine prior knowledge with data:

$$\hat{\theta}_{\text{MAP}} = \arg\max_\theta p(\theta \mid \mathcal{D}) = \arg\max_\theta \left[ p(\mathcal{D} \mid \theta) \, p(\theta) \right]$$

Taking the log:

$$\hat{\theta}_{\text{MAP}} = \arg\max_\theta \left[ \underbrace{\log p(\mathcal{D} \mid \theta)}_{\text{log-likelihood}} + \underbrace{\log p(\theta)}_{\text{log-prior}} \right]$$

> **MAP = MLE + prior.** The log-prior acts as a **penalty**. When the prior is flat (uniform), MAP = MLE.

### 4.2 MAP with a Gaussian Prior = Ridge Regression

**Setup:** Same as Section 3.1, but now place a **Gaussian prior** on the weight $w$:

$$w \sim \mathcal{N}(0, \tau^2)$$

**Log-likelihood** (from Section 3.3, dropping constants):

$$\log p(\mathcal{D} \mid w) = -\frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2 + \text{const}$$

**Log-prior:**

$$\log p(w) = -\frac{w^2}{2\tau^2} + \text{const}$$

**Combining (maximize posterior = minimize negative):**

$$\text{Minimize:} \quad \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2 + \frac{1}{2\tau^2} w^2$$

Multiply by $2\sigma^2$ (doesn't change the minimizer):

$$\text{Minimize:} \quad \sum_{i=1}^{n}(y_i - wx_i - b)^2 + \frac{\sigma^2}{\tau^2} w^2 = \text{MSE} + \lambda w^2$$

where $\lambda = \sigma^2/\tau^2$.

$$\boxed{\text{MAP with Gaussian noise + Gaussian prior} = \text{Ridge regression}}$$

> **Ridge regression is not an arbitrary penalty.** It is the MAP estimator under Gaussian noise + a Gaussian prior on weights. $\lambda = \sigma^2/\tau^2$ is the **noise-to-prior ratio**.

### 4.3 MAP with a Laplacian Prior = Lasso

**Laplacian prior:** $p(w) = \frac{1}{2\tau}\exp(-|w|/\tau)$

$$\log p(w) = -\frac{|w|}{\tau} + \text{const}$$

**MAP objective (minimize negative):**

$$\text{Minimize:} \quad \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2 + \frac{1}{\tau}|w|$$

Multiply by $2\sigma^2$:

$$\text{MSE} + \frac{\sigma^2}{\tau}|w| = \text{MSE} + \lambda|w|$$

where $\lambda = \sigma^2/\tau$.

$$\boxed{\text{MAP with Gaussian noise + Laplacian prior} = \text{Lasso regression}}$$

### 4.4 The Full Correspondence Table

| Prior on $w$ | Log-Prior | → Regularization | Effect |
|--------------|-----------|-------------------|--------|
| **Gaussian** $\mathcal{N}(0, \tau^2)$ | $-\frac{w^2}{2\tau^2}$ | **L2 (Ridge):** $\lambda w^2$ | Shrinks all weights toward 0 |
| **Laplacian** $\frac{1}{2\tau}\exp(-|w|/\tau)$ | $-\frac{|w|}{\tau}$ | **L1 (Lasso):** $\lambda |w|$ | Drives some weights to exactly 0 (sparsity) |
| **Uniform** (flat) | $0$ | **None:** $\lambda = 0$ | MAP = MLE = OLS |

---

## 5. The Bias-Variance Decomposition (Complete Derivation)

### 5.1 The Setup

**Setup:** Data generated by $y = f(x) + \epsilon$, where $f(x)$ is the true function and $\epsilon \sim \mathcal{N}(0, \sigma^2)$ is irreducible noise.

We train a model $\hat{f}$ on a training set $\mathcal{D}$. The prediction at point $x$ is $\hat{f}(x; \mathcal{D})$ — it depends on the random training set $\mathcal{D}$.

### 5.2 The Decomposition

The **expected test error** at point $x$ (averaged over all possible training sets $\mathcal{D}$) is:

$$\mathbb{E}_\mathcal{D}\left[(y - \hat{f}(x))^2\right] = \underbrace{\left(f(x) - \mathbb{E}_\mathcal{D}[\hat{f}(x)]\right)^2}_{\text{Bias}^2} + \underbrace{\mathbb{E}_\mathcal{D}\left[(\hat{f}(x) - \mathbb{E}_\mathcal{D}[\hat{f}(x)])^2\right]}_{\text{Variance}} + \underbrace{\sigma^2}_{\text{Irreducible noise}}$$

$$\boxed{\text{Expected error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible noise}}$$

### 5.3 The Full Derivation

Let $\bar{f}(x) = \mathbb{E}_\mathcal{D}[\hat{f}(x)]$ (average prediction over all training sets). Let $y = f(x) + \epsilon$.

$$y - \hat{f} = (f - \bar{f}) + (\bar{f} - \hat{f}) + \epsilon = A + B + C$$

Expand the square:

$$\mathbb{E}[(A+B+C)^2] = \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$$

**Cross terms vanish:**
- $\mathbb{E}[AB] = (f - \bar{f})\mathbb{E}[B] = 0$ because $\mathbb{E}[B] = \mathbb{E}[\bar{f} - \hat{f}] = \bar{f} - \bar{f} = 0$.
- $\mathbb{E}[AC] = (f - \bar{f})\mathbb{E}[\epsilon] = 0$ because $\mathbb{E}[\epsilon] = 0$.
- $\mathbb{E}[BC] = \mathbb{E}[B]\mathbb{E}[\epsilon] = 0$ because $\hat{f}$ depends on $\mathcal{D}$ and $\epsilon$ is independent of $\mathcal{D}$, and $\mathbb{E}[\epsilon] = 0$.

**Remaining terms:**
- $\mathbb{E}[A^2] = (f - \bar{f})^2$ = **Bias²** (systematic error: average prediction vs. truth).
- $\mathbb{E}[B^2] = \mathbb{E}[(\hat{f} - \bar{f})^2]$ = **Variance** (how much predictions vary across training sets).
- $\mathbb{E}[C^2] = \text{Var}(\epsilon) = \sigma^2$ = **Irreducible noise**.

### 5.4 Interpreting Each Term

| Term | Definition | Meaning | Can we reduce it? |
|------|-----------|---------|-------------------|
| **Bias²** | $(f - \bar{f})^2$ | Systematic error: how far the average model is from the truth | Yes — more flexible model |
| **Variance** | $\mathbb{E}[(\hat{f} - \bar{f})^2]$ | Sensitivity: how much the model changes with different training data | Yes — simpler model, regularize, more data |
| **Irreducible noise** | $\sigma^2$ | Inherent randomness in the data-generating process | **No** — noise floor |

### 5.5 The Tradeoff

```
  Error
    │  Total = Bias² + Var + Noise
    │  ╲                          ╱
    │   ╲                        ╱
    │    ╲                      ╱
    │     ╲        ╱╲          ╱
    │      ╲      ╱  ╲        ╱
    │       ╲    ╱    ╲      ╱
    │        ╲  ╱      ╲    ╱
    │         ╲╱        ╲  ╱
    │                    ╲╱
    │
    │  Bias²          Variance
    │  (decreasing)    (increasing)
    │
    └────────────────────────────── Model complexity
    Simple                   Complex
    (underfit)               (overfit)
              ↑
          Sweet spot
```

### 5.6 Connecting to Week 3

| | $\lambda = 0$ (OLS) | $\lambda$ moderate (ridge) | $\lambda \to \infty$ |
|---|---|---|---|
| **Bias** | Low | Moderate | High |
| **Variance** | High | Moderate | Low |

> **The bias-variance decomposition is the mathematical justification for regularization.** Ridge (MAP with Gaussian prior) trades a small increase in bias for a large decrease in variance.

---

## Session 1 Summary: The Three Deep Connections

### Connection 1: MSE = MLE under Gaussian Noise

| Aspect | Loss Function View | Probabilistic View |
|--------|-------------------|-------------------|
| What we minimize | $\frac{1}{n}\sum_i (y_i - \hat{y}_i)^2$ | Negative log-likelihood of Gaussian |
| Assumption | (implicit) | $\epsilon \sim \mathcal{N}(0, \sigma^2)$ |
| Result | OLS solution | MLE solution (same thing) |

### Connection 2: Ridge = MAP with Gaussian Prior

| Aspect | Regularization View | Probabilistic View |
|--------|---------------------|-------------------|
| What we minimize | MSE + $\lambda w^2$ | Negative log-posterior |
| Assumption | (implicit) | $w \sim \mathcal{N}(0, \tau^2)$ |
| $\lambda$ | Regularization strength | $\sigma^2 / \tau^2$ (noise-to-prior ratio) |
| Result | Ridge solution | MAP solution (same thing) |

### Connection 3: Bias-Variance Decomposition

| Week 3 (intuition) | Now (formal) |
|--------------------|--------------------|
| "Low bias, high variance" for OLS | $\text{Bias}^2$ small, $\text{Variance}$ large |
| "High bias, low variance" for strong ridge | $\text{Bias}^2$ large, $\text{Variance}$ small |
| "Sweet spot minimizes their sum" | $\min_\lambda (\text{Bias}^2 + \text{Variance} + \sigma^2)$ |

---

## Session 2 Roadmap: Gradient Descent

### Motivation: Why Not Always Use Closed Form?

Throughout Weeks 1–5, we've been deriving closed-form solutions:

- **Week 2:** OLS has a closed form: $w^* = \text{Cov}(x,y)/\text{Var}(x)$.
- **Week 2:** Ridge has a closed form: $w^*_{\text{ridge}} = \text{Cov}(x,y)/(\text{Var}(x) + \lambda)$.
- **Week 3:** Lasso has **no** closed form. We said: "Lasso requires iterative optimization."
- **Session 1 (just now):** We showed MSE = MLE and ridge = MAP. But what if the model is more complex? What if there's no closed form for the MLE?

| Method | Closed Form? | When Used |
|--------|-------------|-----------|
| OLS (scalar) | Yes | Simple linear regression |
| Ridge (scalar) | Yes | Regularized linear regression |
| Lasso (scalar) | **No** | L1 regularized regression |
| Logistic regression | **No** | Classification (Week 7) |
| Neural networks | **No** | Deep learning (Weeks 15–17) |

Closed-form solutions are the exception. Most ML models require iterative optimization.

---

## 6. The Gradient and Gradient Descent

### 6.1 The Gradient: What You Need to Remember

The **gradient** of a function $f(w_1, \ldots, w_d)$ is the vector of partial derivatives:

$$\nabla f(\mathbf{w}) = \begin{pmatrix} \frac{\partial f}{\partial w_1} \\ \vdots \\ \frac{\partial f}{\partial w_d} \end{pmatrix}$$

**Geometric meaning:** The gradient points in the direction of **steepest ascent**. Therefore, $-\nabla f$ points in the direction of **steepest descent**.

> **Key intuition:** To minimize $f$, take a step in the direction $-\nabla f$. This is gradient descent.

### 6.2 The Update Rule

$$\boxed{\mathbf{w} \leftarrow \mathbf{w} - \eta \, \nabla L(\mathbf{w})}$$

where $\eta$ is the **learning rate** (step size) and $\nabla L(\mathbf{w})$ is the gradient of the loss.

### 6.3 The Algorithm

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

### 6.4 Step-by-Step on a 1D Quadratic

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

> **The chain rule is the most important calculus tool for ML.** When we compute gradients of neural networks (Week 16), the chain rule is applied repeatedly — this is called **backpropagation**.

---

## 7. The Learning Rate

The learning rate $\eta$ is the most important hyperparameter in gradient descent.

### 7.1 Three Regimes

**Too small ($\eta = 0.001$):** Each step is tiny. Convergence takes forever. Safe but impractical.

**Too large ($\eta > 1$ for $f(w) = w^2$):** Steps overshoot the minimum. The loss *increases* each step — **divergence**.

**Just right ($\eta = 0.1$):** Steady decrease. Reaches the minimum in a reasonable number of steps.

### 7.2 Convergence Condition

For a quadratic loss $f(w) = aw^2$, GD converges iff:

$$0 < \eta < \frac{1}{a}$$

### 7.3 Convexity

MSE is a **convex** function of $(w, b)$. This means:

- There is exactly one minimum (no local minima).
- GD is **guaranteed** to converge to the global minimum, given a suitable $\eta$.

> **Convexity is a big deal.** For linear regression, GD always works. For neural networks (non-convex), GD might get stuck in local minima — but in practice, it usually works well enough.

### 7.4 Learning Rate Schedules

| Schedule | Formula | When to Use |
|----------|---------|-------------|
| Fixed | $\eta_t = \eta_0$ | Simple, well-tuned problems |
| Step decay | $\eta_t = \eta_0 \cdot \gamma^{\lfloor t/s \rfloor}$ | Common in practice |
| Inverse | $\eta_t = \eta_0 / (1 + \lambda t)$ | Theoretical guarantees |
| Cosine | $\eta_t = \frac{\eta_0}{2}(1 + \cos(\pi t / T))$ | Popular for neural networks (Week 17) |

---

## 8. Gradient Descent on Linear Regression

### 8.1 The Setup

$$\hat{y}_i = wx_i + b, \qquad \text{MSE}(w, b) = \frac{1}{n}\sum_{i=1}^{n}(y_i - wx_i - b)^2$$

### 8.2 Computing the Gradient (Chain Rule)

Let $r_i = y_i - wx_i - b$ (the **residual**). Then $\text{MSE} = \frac{1}{n}\sum_i r_i^2$.

**W.r.t. $w$** (chain rule: outer derivative $\times$ inner derivative):

$$\frac{\partial \text{MSE}}{\partial w} = \frac{1}{n}\sum_i 2r_i \cdot \frac{\partial r_i}{\partial w} = \frac{1}{n}\sum_i 2r_i \cdot (-x_i) = -\frac{2}{n}\sum_{i=1}^{n} x_i r_i$$

**W.r.t. $b$:**

$$\frac{\partial \text{MSE}}{\partial b} = \frac{1}{n}\sum_i 2r_i \cdot (-1) = -\frac{2}{n}\sum_{i=1}^{n} r_i$$

### 8.3 The Update Rules

$$\boxed{w \leftarrow w + \frac{2\eta}{n}\sum_{i=1}^{n} x_i r_i, \qquad b \leftarrow b + \frac{2\eta}{n}\sum_{i=1}^{n} r_i}$$

> **Intuition:** $w$ increases if $x_i$ is positive and the model underpredicts ($r_i > 0$). The term $x_i r_i$ is the "correction" — it's large when the input is correlated with the residual.

### 8.4 The Residual and the Optimality Condition

At the minimum, the gradient is zero: $\sum_i x_i r_i = 0$.

> **Key insight:** The gradient is the (negative) correlation between inputs and residuals. When residuals are uncorrelated with inputs, the gradient is zero — the model has extracted all the linear information. **This is the OLS optimality condition.** GD finds the same answer as the closed form.

### 8.5 Ridge Regression with GD

For ridge: $L = \text{MSE} + \lambda w^2$.

$$\frac{\partial L}{\partial w} = -\frac{2}{n}\sum_i x_i r_i + 2\lambda w$$

$$w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - 2\eta\lambda w$$

> The $-2\eta\lambda w$ term is **shrinkage**. Each step, $w$ is pulled toward 0. This is the GD view of ridge — same as Week 2's closed form, but now we see *how* shrinkage happens step by step.

### 8.6 Lasso (Subgradient Descent)

For lasso: $L = \text{MSE} + \lambda|w|$. The derivative of $|w|$ is $\text{sgn}(w)$ (undefined at $w = 0$).

$$w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - \eta\lambda \, \text{sgn}(w)$$

> **This is why lasso drives weights to exactly 0.** When $w$ reaches 0, the subgradient is 0, so it stays there. Ridge (L2) only shrinks *toward* 0, never reaching it.

---

## 9. Stochastic Gradient Descent (SGD)

### 9.1 The Problem with Batch GD

**Batch gradient descent** uses the entire dataset per step: $\nabla L = -\frac{2}{n}\sum_i x_i r_i$. This costs $O(n)$ per step. For large datasets, this is too slow.

### 9.2 SGD: One Example at a Time

**SGD** uses ONE random example per step:

$$w \leftarrow w + 2\eta \, x_i r_i$$

- Each step costs $O(1)$.
- The gradient is **noisy** but unbiased: $\mathbb{E}[g_i] = g_{\text{batch}}$.
- The noise can **escape shallow local minima** (useful for non-convex problems).

### 9.3 Mini-Batch GD

Uses a batch of $B$ examples (typically $B = 32, 64, 128$):

$$w \leftarrow w + \frac{2\eta}{B}\sum_{i \in \text{batch}} x_i r_i$$

This is the **standard** in modern ML.

### 9.4 Comparison Table

| Property | Batch GD | SGD | Mini-Batch GD |
|----------|----------|-----|---------------|
| Examples per step | All $n$ | 1 | $B$ (32–128) |
| Cost per step | $O(n)$ | $O(1)$ | $O(B)$ |
| Gradient variance | 0 (exact) | High | Moderate |
| Steps to converge | Few | Many | Moderate |
| Can parallelize? | Yes (expensive) | No | Yes (GPU) |
| Escapes local minima? | No | Yes | Sometimes |
| Used in practice | Small datasets | Rarely alone | **Standard** |

### 9.5 Epochs

An **epoch** = one complete pass through the training data.

- Batch GD: 1 step = 1 epoch.
- SGD: $n$ steps = 1 epoch.
- Mini-batch: $n/B$ steps = 1 epoch.

---

## 10. Feature Scaling

### 10.1 Why Scale Features?

When features have different scales, the loss surface is **elongated**. GD zigzags: large steps in the steep direction (overshooting), tiny steps in the shallow direction.

After scaling, the loss surface becomes more **spherical**. GD converges smoothly.

### 10.2 Standardization

$$x_i^{(\text{scaled})} = \frac{x_i - \bar{x}}{\sigma_x}$$

> **Critical (Week 4 connection):** Compute $\bar{x}$ and $\sigma_x$ using ONLY training data. Applying statistics from the full dataset (including test) is **data leakage**!

---

## 11. Monitoring Training

### 11.1 The Loss Curve

- **Steady decrease:** GD is working.
- **Plateau:** Converged (or stuck).
- **Oscillation:** $\eta$ too large. Reduce it.
- **Divergence (loss increases):** $\eta$ way too large. Reduce immediately.

### 11.2 Training vs. Validation Loss

- **Both decrease then plateau:** Good fit.
- **Training ↓, validation ↑:** Overfitting. Regularize or stop early.
- **Both high, no decrease:** Underfitting or $\eta$ too small.

---

## 12. Summary

### Session 1 Key Equations (Week 5 Completion)

> **Bayes' theorem:** $p(\theta \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \theta) \, p(\theta)}{p(\mathcal{D})}$

> **MLE:** $\hat{\theta}_{\text{MLE}} = \arg\max_\theta \sum_i \log p(x_i \mid \theta)$

> **Gaussian noise → MSE:** $\arg\max_w \ell(w) = \arg\min_w \text{MSE}(w)$

> **Gaussian prior → Ridge:** $\lambda = \sigma^2 / \tau^2$

> **Laplacian prior → Lasso:** $\lambda = \sigma^2 / \tau$

> **Bias-variance:** $\mathbb{E}[(y - \hat{f})^2] = \text{Bias}^2 + \text{Variance} + \sigma^2$

### Session 2 Key Equations (Week 6 Gradient Descent)

> **GD update:** $\mathbf{w} \leftarrow \mathbf{w} - \eta \, \nabla L(\mathbf{w})$

> **MSE gradient:** $\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$, $\quad \frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$

> **SGD update:** $w \leftarrow w + 2\eta \, x_i r_i$ (single example)

> **Ridge GD:** $w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i - 2\eta\lambda w$

### Key Intuition

1. **Bayes' theorem is the math of learning:** Prior + data → posterior.
2. **MSE = MLE under Gaussian noise.** The loss function is not arbitrary.
3. **Ridge = MAP with a Gaussian prior.** $\lambda = \sigma^2/\tau^2$.
4. **Lasso = MAP with a Laplacian prior.** The sharp peak at 0 causes sparsity.
5. **Expected error = Bias² + Variance + Irreducible noise.**
6. **The gradient points uphill.** Step opposite to minimize.
7. **Learning rate controls step size.** Too small = slow. Too large = diverge.
8. **MSE is convex.** GD is guaranteed to find the global minimum.
9. **SGD uses one example per step.** Noisy but fast. Mini-batch is the standard.
10. **Feature scaling helps GD converge faster.**

---

## 13. Exercises

### Session 1 Exercises (Week 5 Completion)

**E1.** You flip a coin 20 times and get 14 heads. Using MLE, what is your estimate of $P(\text{heads})$?

**E2.** Derive the MLE for the Bernoulli distribution (Section 2.3). Show each step: write the likelihood, take the log, differentiate, and solve.

**E3.** Fill in the blanks: Minimizing MSE is equivalent to ___ under the assumption that noise follows a ___ distribution. Ridge regression is equivalent to ___ with a ___ prior on the weights.

**E4.** For the bias-variance decomposition, which term(s) can be reduced by:
(a) Adding more training data?
(b) Using a more complex model?
(c) Neither — it's irreducible?

**E5.** A prior on $w$ has the form $p(w) \propto \exp(-|w|/\tau)$ (Laplacian prior). Following the derivation in Section 4.2, show that MAP with this prior gives **lasso** regression. What is $\lambda$?

**E6.** In the medical testing example (Section 1.3), suppose the disease prevalence changes from 1% to 10%. Recompute $P(\text{disease} \mid \text{positive})$. How does the prior affect the posterior?

### Session 2 Exercises (Week 6 Gradient Descent)

**E7.** Minimize $f(w) = 3w^2 + 2w + 1$ with $\eta = 0.1$. Start at $w_0 = 2$. Compute $w_1$ and $w_2$.

**E8.** Write the GD update rule. What happens if $\eta = 0$? If $\eta$ is very large?

**E9.** For MSE, write the gradient w.r.t. $w$ and $b$. What is the residual $r_i$?

**E10.** Implement GD for scalar linear regression. $x = [1, 2, 3, 4]$, $y = [2, 4, 6, 8]$. Start $w=0, b=0$, $\eta=0.01$. Run 100 steps. What are the final $w, b$? What are the OLS solutions?

**E11.** For $f(w) = w^2$: (a) For what $\eta$ does GD converge? (b) What is the optimal $\eta$ (one-step convergence)? (c) What happens at $\eta = 1.0$?

**E12.** Explain why feature scaling helps GD converge faster. Draw the loss surface before and after scaling.

**E13.** The ridge update includes $-2\eta\lambda w$. What does this term do? What happens as $\lambda \to \infty$?

### [★ Advanced]

**E14.** Show that for $f(w) = \frac{1}{2}aw^2$, the optimal learning rate (maximizing loss decrease in one step) is $\eta^* = 1/a$. (Exact line search.)

**E15.** ★★ Show that the expected value of the SGD update equals the batch GD update. (SGD is unbiased.)

**E16.** ★★ For $L(w) = \frac{1}{2}(w - c)^2 + \lambda|w|$ with $c > 0$: (a) Find the minimizer. (b) For what $\lambda$ is $w^* = 0$? (This is the **soft-thresholding operator**.)

**E17.** ★★ Show that the MLE for the variance of a Gaussian, $\hat{\sigma}^2_{\text{MLE}} = \frac{1}{n}\sum_i (x_i - \bar{x})^2$, is a **biased** estimator. Specifically, show that $\mathbb{E}[\hat{\sigma}^2_{\text{MLE}}] = \frac{n-1}{n}\sigma^2$.

---

## 14. Connections

| Next Week | How It Uses This Week |
|-----------|-------------------|
| Week 7: Logistic Regression | Bernoulli MLE → cross-entropy loss (Session 1). GD trains logistic regression (Session 2). |
| Week 8: Matrix Linear Regression | MLE/MAP in vector/matrix form. GD in vector form. |
| Week 9: k-NN | Bias-variance for k-NN (small k = low bias/high variance). |
| Week 11: Information Theory | KL divergence. Cross-entropy = entropy + KL. |
| Week 15–16: Neural Networks | GD + chain rule = backpropagation. |
| Week 17: Training Neural Networks | Adam, momentum, schedules — all extensions of GD. |
| Week 18: Generalization Theory | Bias-variance as special case. Why GD generalizes: implicit regularization. |

---

*Next week: Logistic Regression. We'll combine the probability from Session 1 (MLE for Bernoulli → cross-entropy loss) with the gradient descent from Session 2 to build our first classification model.*
