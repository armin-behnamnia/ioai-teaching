# Week 5 Handout: Probability for Machine Learning

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 5 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** Week 1 (ML framework, overfitting/underfitting), Week 2 (scalar linear regression, MSE, ridge regression), Week 3 (overfitting & regularization, bias-variance intuition), Week 4 (model evaluation, cross-validation, classification metrics)  
> **Assumed background:** Your probability course has covered random variables, PMF/PDF, expectation, variance, joint/marginal/conditional distributions, Bayes' theorem, and basic distributions (Bernoulli, Gaussian). Your linear algebra course has covered vectors and matrices. We will USE these tools — not re-derive them.

---

## 1. Motivation

### 1.1 The Questions We've Been Postponing

Throughout Weeks 1–4, we've been building ML intuition using only basic algebra and statistics. Along the way, we've made several promises:

- **Week 2:** "MSE is not arbitrary. It's the loss function you get when you assume Gaussian noise. We'll prove this in Week 5."
- **Week 2:** "Ridge regression corresponds to a prior belief that weights should be small. We'll formalize this."
- **Week 3:** "The bias-variance tradeoff has a formal mathematical decomposition. It comes in Week 5 with probability."

This week, we deliver on all three promises. You already know the probability tools — random variables, distributions, Bayes' theorem. Now we use them to understand **why ML works the way it does**.

### 1.2 What's Different This Week

In your probability course, you learned probability as a mathematical subject. This week, we use probability as a **language for ML**. The key shift:

- Probability asks: "Given a model, what data do we expect?"
- ML asks: "Given data, what model should we choose?"

**Bayes' theorem** is the bridge between these two questions. **Maximum Likelihood Estimation (MLE)** and **Maximum a Posteriori (MAP)** are the two main answers.

### 1.3 The Roadmap

| Session | Topics | Key Deliverable |
|---------|--------|-----------------|
| S1 | Bayes' theorem applied to ML, MLE principle, MLE for Bernoulli/Gaussian, MLE = MSE | The first deep connection |
| S2 | MAP, MAP = Ridge, Lasso from Laplacian prior, bias-variance decomposition | The second and third deep connections |

---

## 2. Bayes' Theorem Applied to ML

### 2.1 The ML Interpretation

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

> **This IS learning, mathematically.** You start with a belief (prior). You observe data. You update your belief using Bayes' theorem. The posterior is your updated belief. Every ML algorithm is implicitly doing this — MLE and MAP are approximations of full Bayesian inference.

### 2.2 The Evidence (and Why We Often Drop It)

The evidence $p(\mathcal{D}) = \int p(\mathcal{D} \mid \theta) \, p(\theta) \, d\theta$ requires integrating over all possible $\theta$. This is often intractable.

**Key insight:** For *optimization* (finding the best $\theta$), the evidence doesn't depend on $\theta$ — it's a constant. So we can work with the **unnormalized posterior**:

$$p(\theta \mid \mathcal{D}) \propto p(\mathcal{D} \mid \theta) \, p(\theta)$$

This is why MLE (which ignores the prior) and MAP (which ignores the evidence) are practical: they avoid the hardest part of Bayes' theorem.

### 2.3 Example: Medical Testing = Class Imbalance

**Setup:** A disease affects 1% of the population. A test is 99% sensitive (TPR) and 95% specific (TNR). If you test positive, what's $P(\text{disease} \mid \text{positive})$?

- Prior: $P(\text{disease}) = 0.01$
- Likelihood: $P(\text{positive} \mid \text{disease}) = 0.99$
- $P(\text{positive} \mid \text{no disease}) = 0.05$ (FPR)

$$P(\text{disease} \mid \text{positive}) = \frac{0.99 \times 0.01}{0.99 \times 0.01 + 0.05 \times 0.99} = \frac{0.0099}{0.0594} = \frac{1}{6} \approx 16.7\%$$

**The surprising result:** Even with a 99% sensitive test, a positive result means only 16.7% chance of disease!

> **ML connection (Week 4):** This is EXACTLY the class imbalance problem. $P(\text{disease} \mid \text{positive})$ is the same as **precision** from Week 4. When the positive class is rare (1%), even a good test generates more false positives than true positives. The prior dominates the posterior. This is why accuracy is misleading with imbalanced data — and why precision, recall, and F1 matter.

### 2.4 Example: Spam Filtering Setup

Given an email with features $x$:

$$P(\text{spam} \mid x) = \frac{P(x \mid \text{spam}) \, P(\text{spam})}{P(x)}$$

- $P(\text{spam})$: the prior (how common is spam?)
- $P(x \mid \text{spam})$: the likelihood (how typical are these features for spam?)
- $P(\text{spam} \mid x)$: the posterior (probability the email is spam, given features)

This is the foundation of **Naive Bayes** classifiers and connects to logistic regression (Week 7).

---

## 3. Maximum Likelihood Estimation (MLE)

### 3.1 The Principle

> **MLE:** Given data $\mathcal{D} = \{x_1, \ldots, x_n\}$ from a distribution $p(x \mid \theta)$, find the $\theta$ that makes the data **most probable**:

$$\hat{\theta}_{\text{MLE}} = \arg\max_\theta p(\mathcal{D} \mid \theta)$$

**Intuition:** "Of all possible parameter values, which would have made the observed data most likely to occur?"

### 3.2 The Log-Likelihood Trick

Assuming i.i.d. data, the likelihood is a product:

$$p(\mathcal{D} \mid \theta) = \prod_{i=1}^{n} p(x_i \mid \theta)$$

Products are numerically unstable (many small numbers multiply to underflow). We take the **log** (monotonic, so the maximizer is unchanged):

$$\ell(\theta) = \log p(\mathcal{D} \mid \theta) = \sum_{i=1}^{n} \log p(x_i \mid \theta)$$

$$\hat{\theta}_{\text{MLE}} = \arg\max_\theta \ell(\theta)$$

**Why log?** (1) Products become sums (easier to differentiate). (2) Numerical stability. (3) Log-likelihood is concave for many common distributions (unique maximum).

### 3.3 MLE for the Bernoulli (Quick Derivation)

Data: $x_1, \ldots, x_n \in \{0, 1\}$, i.i.d. Bernoulli($\theta$).

**Likelihood:** $\prod_i \theta^{x_i}(1-\theta)^{1-x_i}$

**Log-likelihood:** Let $k = \sum_i x_i$ (number of ones).

$$\ell(\theta) = k \log \theta + (n - k) \log(1 - \theta)$$

**Differentiate and solve:**

$$\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n - k}{1 - \theta} = 0 \quad \Longrightarrow \quad \boxed{\hat{\theta}_{\text{MLE}} = \frac{k}{n} = \frac{1}{n}\sum_{i=1}^{n} x_i}$$

> The MLE for a Bernoulli is the **sample mean**. Flip a coin 100 times, get 60 heads → MLE of $P(\text{heads}) = 0.60$. Intuitive — and now proven.

### 3.4 MLE for the Gaussian (Quick)

Data: $x_1, \ldots, x_n \sim \mathcal{N}(\mu, \sigma^2)$.

$$\ell(\mu, \sigma^2) = -\frac{n}{2}\log(2\pi) - \frac{n}{2}\log(\sigma^2) - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(x_i - \mu)^2$$

Maximizing w.r.t. $\mu$: only the last term depends on $\mu$, and it's negative. So maximizing $\ell$ w.r.t. $\mu$ = minimizing $\sum_i (x_i - \mu)^2$.

$$\boxed{\hat{\mu}_{\text{MLE}} = \bar{x}, \qquad \hat{\sigma}^2_{\text{MLE}} = \frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^2}$$

> The MLE of the Gaussian mean is the sample mean; the MLE of the variance is the sample variance (with denominator $n$, not $n-1$).

---

## 4. The Deep Connection: MLE = MSE

### 4.1 The Setup

In Week 2, we said: "MSE is not arbitrary — it corresponds to Gaussian noise. We'll prove this in Week 5." Here's the proof.

**Model:** $y_i = wx_i + b + \epsilon_i$, where $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$.

This means: $y_i \mid x_i, w, b \sim \mathcal{N}(wx_i + b, \sigma^2)$.

### 4.2 The Likelihood

$$p(\mathcal{D} \mid w, b, \sigma^2) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi\sigma^2}} \exp\!\left(-\frac{(y_i - wx_i - b)^2}{2\sigma^2}\right)$$

### 4.3 The Log-Likelihood

$$\ell(w, b) = -\frac{n}{2}\log(2\pi\sigma^2) - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2$$

### 4.4 The Key Step

The first term is constant. The second term is **proportional to MSE**:

$$\ell(w, b) = \text{const} - \frac{1}{2\sigma^2}\underbrace{\sum_{i=1}^{n}(y_i - wx_i - b)^2}_{n \cdot \text{MSE}(w, b)}$$

**Maximizing** $\ell(w, b)$ is equivalent to **minimizing** MSE.

$$\boxed{\hat{w}_{\text{MLE}} = \hat{w}_{\text{OLS}} = \arg\min_w \text{MSE}(w, b)}$$

> **The deep connection:** Minimizing MSE is not arbitrary. It is the maximum likelihood estimator under Gaussian noise. The loss function and the noise model are two sides of the same coin.

### 4.5 The MLE ↔ Loss Function Correspondence Table

| Noise Model | Likelihood | → Loss Function | Used When |
|-------------|------------|----------------|-----------|
| **Gaussian** $\mathcal{N}(0, \sigma^2)$ | $\prod_i \exp\!\left(-\frac{(y_i - \hat{y}_i)^2}{2\sigma^2}\right)$ | **MSE:** $\frac{1}{n}\sum_i (y_i - \hat{y}_i)^2$ | Regression (continuous target) |
| **Bernoulli** $\text{Ber}(\theta)$ | $\prod_i \theta^{y_i}(1-\theta)^{1-y_i}$ | **Cross-entropy:** $-\sum_i [y_i \log \hat{y}_i + (1-y_i)\log(1-\hat{y}_i)]$ | Binary classification (Week 7) |
| **Laplacian** (double exponential) | $\prod_i \exp\!\left(-\frac{|y_i - \hat{y}_i|}{b}\right)$ | **MAE:** $\frac{1}{n}\sum_i |y_i - \hat{y}_i|$ | Robust regression (outliers) |

> **Pattern:** The log of each noise model's likelihood gives a different loss function. The choice of loss function is a **probabilistic assumption** about how the data was generated.

### 4.6 What If the Noise Isn't Gaussian?

If the noise is Laplacian (heavy tails), MLE gives MAE instead of MSE. MAE is more robust to outliers because it doesn't square the errors. **Your loss function encodes your assumptions about the data-generating process.** There is no universal loss function — only the one that matches your noise model.

---

## 5. Maximum a Posteriori (MAP)

### 5.1 From MLE to MAP

MLE finds the parameter that makes the data most likely. But MLE has no way to encode **prior knowledge** — it can overfit when data is scarce.

**MAP estimation** uses Bayes' theorem to combine prior knowledge with data:

$$\hat{\theta}_{\text{MAP}} = \arg\max_\theta p(\theta \mid \mathcal{D}) = \arg\max_\theta \left[ p(\mathcal{D} \mid \theta) \, p(\theta) \right]$$

(The evidence $p(\mathcal{D})$ doesn't depend on $\theta$, so we drop it.)

Taking the log:

$$\hat{\theta}_{\text{MAP}} = \arg\max_\theta \left[ \underbrace{\log p(\mathcal{D} \mid \theta)}_{\text{log-likelihood}} + \underbrace{\log p(\theta)}_{\text{log-prior}} \right]$$

> **MAP = MLE + prior.** The log-prior acts as a **penalty** that pulls $\theta$ toward values the prior considers likely. When the prior is flat (uniform), MAP = MLE.

### 5.2 MAP with a Gaussian Prior = Ridge Regression

**Setup:** Same as Section 4.1, but now place a **Gaussian prior** on the weight $w$:

$$w \sim \mathcal{N}(0, \tau^2)$$

**The log-posterior:**

$$\log p(w \mid \mathcal{D}) = \log p(\mathcal{D} \mid w) + \log p(w) + \text{const}$$

**Log-likelihood** (from Section 4.3, dropping constants):

$$\log p(\mathcal{D} \mid w) = -\frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2 + \text{const}$$

**Log-prior:**

$$\log p(w) = \log \mathcal{N}(w \mid 0, \tau^2) = -\frac{w^2}{2\tau^2} + \text{const}$$

**Combining (maximize posterior = minimize negative):**

$$\text{Minimize:} \quad \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2 + \frac{1}{2\tau^2} w^2$$

Multiply by $2\sigma^2$ (doesn't change the minimizer):

$$\text{Minimize:} \quad \sum_{i=1}^{n}(y_i - wx_i - b)^2 + \frac{\sigma^2}{\tau^2} w^2 = \text{MSE} + \lambda w^2$$

where $\lambda = \sigma^2/\tau^2$.

$$\boxed{\text{MAP with Gaussian noise + Gaussian prior} = \text{Ridge regression}}$$

> **The deep connection (revealed):** Ridge regression is not an arbitrary penalty. It is the MAP estimator under Gaussian noise + a Gaussian prior on weights. The regularization parameter $\lambda = \sigma^2 / \tau^2$ is the **ratio of noise variance to prior variance**:
> - If the prior is strong ($\tau^2$ small → $\lambda$ large): we believe $w$ is near 0, and the data must be very convincing to move it.
> - If the prior is weak ($\tau^2$ large → $\lambda$ small): we let the data speak (approaching MLE/OLS).

### 5.3 The Full Correspondence Table

| Prior on $w$ | Log-Prior | → Regularization | Effect |
|--------------|-----------|-------------------|--------|
| **Gaussian** $\mathcal{N}(0, \tau^2)$ | $-\frac{w^2}{2\tau^2}$ | **L2 (Ridge):** $\lambda w^2$ | Shrinks all weights toward 0 |
| **Laplacian** $\frac{1}{2\tau}\exp(-|w|/\tau)$ | $-\frac{|w|}{\tau}$ | **L1 (Lasso):** $\lambda |w|$ | Drives some weights to exactly 0 (sparsity) |
| **Uniform** (flat) | $0$ | **None:** $\lambda = 0$ | MAP = MLE = OLS |

> **Pattern:** Each prior distribution corresponds to a regularization method. The log of the prior density becomes the penalty term. This is why "the choice of regularization is a probabilistic assumption."

### 5.4 What Does a Prior Do in MAP?

1. **Shrinkage:** Pulls the estimate toward the prior mean (e.g., 0 for ridge). Reduces variance at the cost of bias.
2. **Regularization:** Prevents overfitting by disfavoring extreme parameter values. More data → likelihood dominates → prior matters less.
3. **Domain knowledge:** Tight prior = strong belief. Weak prior = let the data decide.

> **Connection to Week 3:** In Week 3, we said "ridge shrinks weights toward zero." Now we know *why*: it's because ridge assumes a Gaussian prior centered at zero. The $\lambda$ knob from Week 3 is the ratio of noise to prior strength.

---

## 6. The Bias-Variance Decomposition

### 6.1 The Setup

We now have the probability tools to derive the **bias-variance decomposition** — the formal version of the intuition from Week 3.

**Setup:** Data generated by $y = f(x) + \epsilon$, where $f(x)$ is the true function and $\epsilon \sim \mathcal{N}(0, \sigma^2)$ is irreducible noise.

We train a model $\hat{f}$ on a training set $\mathcal{D}$. The prediction at point $x$ is $\hat{f}(x; \mathcal{D})$ — it depends on the random training set $\mathcal{D}$.

### 6.2 The Decomposition

The **expected test error** at point $x$ (averaged over all possible training sets $\mathcal{D}$) is:

$$\mathbb{E}_\mathcal{D}\left[(y - \hat{f}(x))^2\right] = \underbrace{\left(f(x) - \mathbb{E}_\mathcal{D}[\hat{f}(x)]\right)^2}_{\text{Bias}^2} + \underbrace{\mathbb{E}_\mathcal{D}\left[(\hat{f}(x) - \mathbb{E}_\mathcal{D}[\hat{f}(x)])^2\right]}_{\text{Variance}} + \underbrace{\sigma^2}_{\text{Irreducible noise}}$$

$$\boxed{\text{Expected error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible noise}}$$

### 6.3 Derivation

Let $\bar{f}(x) = \mathbb{E}_\mathcal{D}[\hat{f}(x)]$ (average prediction over all training sets). Let $y = f(x) + \epsilon$.

$$\mathbb{E}_\mathcal{D}[(y - \hat{f})^2] = \mathbb{E}_\mathcal{D}[((f - \bar{f}) + (\bar{f} - \hat{f}) + \epsilon)^2]$$

Expand the square ($A = f - \bar{f}$, $B = \bar{f} - \hat{f}$, $C = \epsilon$):

$$= \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$$

**Cross terms vanish:**
- $\mathbb{E}[AB] = (f - \bar{f})\mathbb{E}[B] = 0$ because $\mathbb{E}[B] = \mathbb{E}[\bar{f} - \hat{f}] = \bar{f} - \bar{f} = 0$.
- $\mathbb{E}[AC] = (f - \bar{f})\mathbb{E}[\epsilon] = 0$ because $\mathbb{E}[\epsilon] = 0$.
- $\mathbb{E}[BC] = \mathbb{E}[B]\mathbb{E}[\epsilon] = 0$ because $\hat{f}$ depends on $\mathcal{D}$ and $\epsilon$ is independent of $\mathcal{D}$, and $\mathbb{E}[\epsilon] = 0$.

**Remaining terms:**
- $\mathbb{E}[A^2] = (f - \bar{f})^2$ = **Bias²** (systematic error: average prediction vs. truth).
- $\mathbb{E}[B^2] = \mathbb{E}[(\hat{f} - \bar{f})^2]$ = **Variance** (how much predictions vary across training sets).
- $\mathbb{E}[C^2] = \text{Var}(\epsilon) = \sigma^2$ = **Irreducible noise**.

### 6.4 Interpreting Each Term

| Term | Definition | Meaning | Can we reduce it? |
|------|-----------|---------|-------------------|
| **Bias²** | $(f - \bar{f})^2$ | Systematic error: how far the average model is from the truth | Yes — more flexible model |
| **Variance** | $\mathbb{E}[(\hat{f} - \bar{f})^2]$ | Sensitivity: how much the model changes with different training data | Yes — simpler model, regularize, more data |
| **Irreducible noise** | $\sigma^2$ | Inherent randomness in the data-generating process | **No** — noise floor |

### 6.5 The Tradeoff

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

### 6.6 Connecting to Week 3

In Week 3, we had this qualitative table:

| | $\lambda = 0$ (OLS) | $\lambda$ moderate (ridge) | $\lambda \to \infty$ |
|---|---|---|---|
| **Bias** | Low | Moderate | High |
| **Variance** | High | Moderate | Low |

Now we can prove this:
- **$\lambda = 0$ (OLS = MLE):** Fits freely → low bias, but fits noise → high variance.
- **$\lambda$ moderate (ridge = MAP):** Gaussian prior shrinks weights → slightly higher bias, but much lower variance.
- **$\lambda \to \infty$:** Prior dominates → $w \to 0$ → predicts $\bar{y}$ → high bias, zero variance.

> **The bias-variance decomposition is the mathematical justification for regularization.** Ridge (MAP with Gaussian prior) trades a small increase in bias for a large decrease in variance. This is exactly what we observed in Week 3 — now it's a theorem.

### 6.7 Connecting to Week 4

In Week 4, we learned about **learning curves** (training error and validation error vs. training set size):

- **Large gap** → high variance (overfitting). More data will help.
- **Both high, small gap** → high bias (underfitting). More data won't help; need more complexity.

The bias-variance decomposition explains why:
- As $n \to \infty$, $\hat{f}$ converges to $\bar{f}$ → **variance → 0**. The gap closes.
- But if the model is too simple, $\bar{f} \neq f$ → **bias remains high**.
- More data reduces variance but **cannot** reduce bias or irreducible noise.

---

## 7. Summary: The Three Deep Connections

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

| Week 3 (intuition) | Week 5 (formal) |
|--------------------|--------------------|
| "Low bias, high variance" for OLS | $\text{Bias}^2$ small, $\text{Variance}$ large |
| "High bias, low variance" for strong ridge | $\text{Bias}^2$ large, $\text{Variance}$ small |
| "Sweet spot minimizes their sum" | $\min_\lambda (\text{Bias}^2 + \text{Variance} + \sigma^2)$ |

---

## 8. Exercises

### [Basic]

**E1.** You flip a coin 20 times and get 14 heads. Using MLE, what is your estimate of $P(\text{heads})$? What assumption are you making?

**E2.** State Bayes' theorem. For each term (prior, likelihood, evidence, posterior), give its name and explain what it means in one sentence.

**E3.** Fill in the blanks: Minimizing MSE is equivalent to ___ under the assumption that noise follows a ___ distribution. Ridge regression is equivalent to ___ with a ___ prior on the weights.

**E4.** For the bias-variance decomposition, which term(s) can be reduced by:
(a) Adding more training data?
(b) Using a more complex model?
(c) Neither — it's irreducible?

### [Intermediate]

**E5.** Derive the MLE for the Bernoulli distribution (Section 3.3). Show each step: write the likelihood, take the log, differentiate, and solve. (This is a quiz topic — make sure you can do it without notes.)

**E6.** A prior on $w$ has the form $p(w) \propto \exp(-|w|/\tau)$ (Laplacian prior). Following the derivation in Section 5.2, show that MAP with this prior gives **lasso** regression (L1 penalty $\lambda |w|$). What is $\lambda$ in terms of $\sigma^2$ and $\tau$?

**E7.** In the medical testing example (Section 2.3), suppose the disease prevalence changes from 1% to 10%. Recompute $P(\text{disease} \mid \text{positive})$. How does the prior affect the posterior?

**E8.** Fill in the MLE↔loss-function correspondence table:

| Noise Model | → Loss Function |
|-------------|----------------|
| Gaussian | ? |
| ? | Cross-entropy |
| Laplacian | ? |

For each, state the assumption and when you would use it.

**E9.** In the bias-variance decomposition, explain why $\mathbb{E}[\epsilon] = 0$ is necessary for the cross terms to vanish. What happens if the noise has non-zero mean? Which term would change?

### [★ Advanced]

**E10.** Show that the MLE for the variance of a Gaussian, $\hat{\sigma}^2_{\text{MLE}} = \frac{1}{n}\sum_i (x_i - \bar{x})^2$, is a **biased** estimator. Specifically, show that $\mathbb{E}[\hat{\sigma}^2_{\text{MLE}}] = \frac{n-1}{n}\sigma^2$.
*(Hint: Use $\sum_i (x_i - \bar{x})^2 = \sum_i (x_i - \mu)^2 - n(\bar{x} - \mu)^2$, and $\mathbb{E}[(\bar{x}-\mu)^2] = \sigma^2/n$.)*

**E11.** ★★ The **Bayesian posterior** for linear regression with Gaussian noise and a Gaussian prior on $w$ is itself a Gaussian. This means we can compute not just the MAP estimate (the mean) but also the **uncertainty** (the variance of the posterior).
(a) Write the full posterior $p(w \mid \mathcal{D}) \propto p(\mathcal{D} \mid w) p(w)$. Show it's Gaussian in $w$.
(b) What is the mean of the posterior? (It should be the ridge solution.)
(c) What is the variance of the posterior? How does it change with more data (larger $n$)?
(d) How does the posterior variance relate to the bias-variance tradeoff?
*(This connects to Bayesian linear regression. We'll revisit in Week 8 with matrix notation.)*

**E12.** ★★ Consider the MAP objective with Gaussian noise (variance $\sigma^2$) and a Gaussian prior (variance $\tau^2$):
(a) Show that as $\tau^2 \to \infty$ (uninformative prior), MAP reduces to MLE (= OLS).
(b) Show that as $\tau^2 \to 0$ (infinitely strong prior), $w \to 0$ (the model predicts $\bar{y}$).
(c) Suppose you have very little data ($n = 3$). Would you prefer MLE or MAP? Why?
(d) Suppose you have lots of data ($n = 10{,}000$). Does the prior matter much? Why or why not?

**E13.** ★★ The bias-variance decomposition assumes the true model is $y = f(x) + \epsilon$ with $\mathbb{E}[\epsilon] = 0$. But what if our model class **includes** the true $f$?
(a) In this case, is the bias zero, positive, or depends?
(b) If the model class includes $f$ and we have infinite data, what is the expected error?
(c) If the model class does NOT include $f$ (model misspecification), can the bias ever be zero? Give an example.

---

## 9. Connections

### 9.1 What This Enables

| Next Week | How It Uses Week 5 |
|-----------|-------------------|
| Week 6: Gradient Descent | Minimizing the negative log-likelihood (same as minimizing MSE) via iterative optimization |
| Week 7: Logistic Regression | Bernoulli likelihood → cross-entropy loss. MAP with Gaussian prior → L2 regularized logistic regression. |
| Week 8: Matrix Linear Regression | MLE/MAP in vector/matrix form. Bayesian linear regression (posterior distribution over weight vectors). |
| Week 9: k-NN | Bias-variance for k-NN (small k = low bias/high variance, large k = high bias/low variance) |
| Week 11: Information Theory | KL divergence between distributions. Cross-entropy = entropy + KL divergence. |
| Week 15-16: Neural Networks | Cross-entropy loss for classification. Gaussian assumption for regression heads. |
| Week 18: Generalization Theory | Bias-variance decomposition as a special case of generalization bounds. |

### 9.2 Key Vocabulary to Master

- [ ] Bayes' theorem: prior, likelihood, evidence, posterior (ML interpretation)
- [ ] MLE: the principle, log-likelihood trick
- [ ] MLE for Bernoulli → sample mean
- [ ] MLE for Gaussian → sample mean and variance
- [ ] MLE under Gaussian noise = MSE loss (the proof)
- [ ] MLE↔loss-function correspondence table
- [ ] MAP = MLE + prior
- [ ] MAP with Gaussian prior = ridge regression (the proof)
- [ ] MAP with Laplacian prior = lasso regression
- [ ] $\lambda = \sigma^2/\tau^2$: noise-to-prior ratio
- [ ] Bias-variance decomposition: Bias² + Variance + Irreducible noise
- [ ] Why more data reduces variance but not bias
- [ ] Why regularization reduces variance but increases bias

---

## 10. Summary

### Key Equations

> **Bayes' theorem:** $p(\theta \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \theta) \, p(\theta)}{p(\mathcal{D})}$

> **MLE:** $\hat{\theta}_{\text{MLE}} = \arg\max_\theta \sum_i \log p(x_i \mid \theta)$

> **MAP:** $\hat{\theta}_{\text{MAP}} = \arg\max_\theta \left[ \sum_i \log p(x_i \mid \theta) + \log p(\theta) \right]$

> **Gaussian noise → MSE:** $\arg\max_w \ell(w) = \arg\min_w \text{MSE}(w)$

> **Gaussian prior → Ridge:** $\lambda = \sigma^2 / \tau^2$

> **Bias-variance:** $\mathbb{E}[(y - \hat{f})^2] = \text{Bias}^2 + \text{Variance} + \sigma^2$

### Key Intuition (If You Remember Nothing Else...)

1. **Bayes' theorem is the math of learning:** Prior + data → posterior.
2. **MLE finds the parameter that makes the data most likely.** For Bernoulli, it's the sample mean.
3. **MSE = MLE under Gaussian noise.** The loss function is not arbitrary — it encodes a probabilistic assumption.
4. **MAP = MLE + prior.** The prior acts as a regularizer.
5. **Ridge = MAP with a Gaussian prior.** $\lambda = \sigma^2/\tau^2$.
6. **Lasso = MAP with a Laplacian prior.** The sharp peak at 0 causes sparsity.
7. **Every loss function corresponds to a noise model.**
8. **Expected error = Bias² + Variance + Irreducible noise.** Regularization trades bias for variance. More data reduces variance but not bias.

---

*Next week: Gradient Descent. We've been using closed-form solutions (OLS, ridge) — but most ML models don't have closed-form solutions. Gradient descent is how we minimize the loss functions we just derived (MSE, cross-entropy, etc.) when no formula exists. The probabilistic view from this week tells us WHAT to minimize; gradient descent tells us HOW.*
