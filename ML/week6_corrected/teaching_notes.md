# Week 6 (Corrected) — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

> **Correction context:** In Week 5, we covered evaluation metrics review, train/val/test, k-fold, and the *concepts* of MLE/MAP without derivations. We began but did not complete the bias-variance decomposition. Session 1 of this corrected Week 6 delivers all missing Week 5 derivations. Session 2 covers the full Week 6 gradient descent content.

---

## Session 1 (80 min): Completing Week 5 — Probability for ML

### Learning Objectives

By the end of this session, students should be able to:
1. Identify the prior, likelihood, evidence, and posterior in a Bayesian ML formulation.
2. Apply Bayes' theorem to the medical testing example and connect it to class imbalance (Week 4).
3. State the MLE principle and the log-likelihood trick.
4. Derive MLE for Bernoulli (→ sample mean) and Gaussian (→ sample mean and variance).
5. **Prove that MLE under Gaussian noise = minimizing MSE.**
6. Prove that MAP with a Gaussian prior = ridge regression.
7. Show that a Laplacian prior gives lasso.
8. **Complete the bias-variance decomposition derivation.**

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Printed or projected handout Sections 1–5
- Colored markers (for the bias-variance tradeoff diagram)
- Quiz S1 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of what we covered in Week 5.** | "We did metrics review, train/val/test, k-fold, and MLE/MAP concepts. Today we do the derivations." |
| 0:05–0:15 | **Bayes' theorem applied to ML + medical testing.** | Students know Bayes' theorem. Focus on ML interpretation + class imbalance connection. |
| 0:15–0:28 | **MLE: principle, log-likelihood trick, Bernoulli derivation.** | Derive on board. Students must be able to reproduce. |
| 0:28–0:35 | **MLE for Gaussian (quick) + MLE = MSE proof.** | The key proof. Derive carefully. |
| 0:35–0:48 | **MAP: principle, Gaussian prior → ridge, Laplacian → lasso.** | Second payoff derivation. |
| 0:48–0:68 | **Bias-variance decomposition (complete derivation).** | Third payoff. Derive the cross terms vanishing. |
| 0:68–0:72 | **Summary: the three deep connections.** | |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S1.md`. |

> **Note:** This session is derivation-heavy. Students have already seen the *concepts* of MLE/MAP in Week 5, so they have intuition. Now we fill in the math. Keep a brisk pace — don't re-explain what MLE/MAP *mean*, just derive them.

### Hook: "Filling in the Gaps" (5 min)

1. "Last week, we covered evaluation metrics, train/val/test, k-fold, and we discussed what MLE and MAP *mean*. We started the bias-variance decomposition but didn't finish it."

2. "Today, we fill in all the derivations. By the end of this session, you'll be able to: prove MSE = MLE, prove ridge = MAP, and complete the bias-variance decomposition. These are the three deep connections that everything in ML rests on."

3. **The punchline:** "Next session, we'll learn gradient descent — the engine that minimizes all the loss functions we're about to derive."

### Board Work: Bayes' Theorem for ML (5 min)

**Students know Bayes' theorem.** Don't derive it — *interpret* it for ML.

**Key teaching moves:**

1. Write Bayes' theorem with ML labels: posterior = (likelihood × prior) / evidence.

2. Fill in the table: Prior (belief before data), Likelihood (how data relates to parameter), Evidence (normalizer), Posterior (updated belief).

3. "Why drop the evidence? For finding the best θ, it doesn't depend on θ. So MLE and MAP can ignore it."

4. **Medical testing example (3 min):** Quick tree diagram. "Even with 99% sensitivity, a positive result means only 16.7% chance of disease. This is EXACTLY precision from Week 4 — class imbalance."

### Board Work: MLE for Bernoulli (8 min)

**This derivation is a quiz topic.** Students must be able to reproduce it.

**Step-by-step on the board:**

1. **Setup:** $x_1, \ldots, x_n \in \{0,1\}$, i.i.d. Bernoulli($\theta$).
2. **Likelihood:** $\prod_i \theta^{x_i}(1-\theta)^{1-x_i}$
3. **Log-likelihood:** $\ell(\theta) = k\log\theta + (n-k)\log(1-\theta)$, where $k = \sum_i x_i$.
4. **Differentiate:** $\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n-k}{1-\theta} = 0$
5. **Solve:** $\hat{\theta} = k/n$

**Key teaching moves:**
- At each step, ask "What do we do next?"
- Emphasize the log-likelihood trick: products → sums, numerical stability.

### Board Work: MLE = MSE (7 min)

**This is the single most important derivation from Week 5.**

**Step 1:** Model: $y_i = wx_i + b + \epsilon_i$, $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$.

**Step 2:** Likelihood: $\prod_i \mathcal{N}(y_i | wx_i + b, \sigma^2)$

**Step 3:** Log-likelihood: $\ell(w,b) = \text{const} - \frac{1}{2\sigma^2}\sum_i (y_i - wx_i - b)^2$

**Step 4:** Circle the sum. "This is $n \cdot \text{MSE}(w,b)$!"

**Step 5:** "Maximizing $\ell$ = minimizing MSE. **The loss function IS the negative log-likelihood.**"

**Write prominently:**

> **MSE is not arbitrary. It is the maximum likelihood estimator under Gaussian noise.**

**Correspondence table:** Gaussian → MSE, Bernoulli → cross-entropy, Laplacian → MAE.

### Board Work: MAP = Ridge (8 min)

**Step 1:** MAP principle. $\hat{\theta}_{\text{MAP}} = \arg\max_\theta [\log p(\mathcal{D}|\theta) + \log p(\theta)]$

"MAP = MLE + prior. The log-prior acts as a penalty."

**Step 2:** Gaussian prior on $w$. $\log p(w) = -w^2/(2\tau^2) + \text{const}$.

**Step 3:** Combine. Minimize: $\frac{1}{2\sigma^2}\sum (y_i - wx_i - b)^2 + \frac{1}{2\tau^2}w^2$

Multiply by $2\sigma^2$: MSE + $(\sigma^2/\tau^2)w^2 = \text{MSE} + \lambda w^2$.

**Write prominently:**

> **Ridge = MAP with Gaussian noise + Gaussian prior. $\lambda = \sigma^2/\tau^2$.**

**Laplacian prior → Lasso (3 min):** $\log p(w) = -|w|/\tau$. MAP: MSE + $(\sigma^2/\tau)|w|$. $\lambda = \sigma^2/\tau$.

**Connect to Week 3:** "L1 diamond's corners are on the axes — that's why lasso produces exact zeros."

### Board Work: Bias-Variance Decomposition (20 min)

**This is the derivation we started in Week 5 but didn't finish.**

**Step 1: Setup.** $y = f(x) + \epsilon$, $\epsilon \sim \mathcal{N}(0, \sigma^2)$.

**Step 2: Expected test error.** $\mathbb{E}_\mathcal{D}[(y - \hat{f}(x))^2]$

**Step 3: Decompose.** Let $\bar{f} = \mathbb{E}_\mathcal{D}[\hat{f}]$.

$y - \hat{f} = (f - \bar{f}) + (\bar{f} - \hat{f}) + \epsilon = A + B + C$

**Step 4: Expand.** $\mathbb{E}[(A+B+C)^2] = \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$

**Step 5: Cross terms vanish.** (This is where we stopped in Week 5 — now complete it.)
- $\mathbb{E}[AB] = 0$ because $\mathbb{E}[B] = 0$.
- $\mathbb{E}[AC] = 0$ because $\mathbb{E}[\epsilon] = 0$.
- $\mathbb{E}[BC] = 0$ because $\epsilon \perp \mathcal{D}$ and $\mathbb{E}[\epsilon] = 0$.

**Step 6: Result.** $\text{Expected error} = \text{Bias}^2 + \text{Variance} + \sigma^2$

**Step 7: Interpretation table + the tradeoff diagram.**

**Step 8: Connect to Week 3.** Show the table ($\lambda=0$: low bias/high variance; $\lambda \to \infty$: high bias/low variance). "Now it's a theorem."

**Step 9: Connect to Week 4.** "Learning curves: large gap = high variance. Both high + small gap = high bias."

### Discussion Prompts

1. **(After MLE=MSE):** "If MSE corresponds to Gaussian noise, what loss would you use if your data has occasional large outliers?" → MAE (Laplacian noise).

2. **(After MAP=Ridge):** "What happens if we use a Laplacian prior?" → Lasso. The sharp peak at 0 causes sparsity.

3. **(After bias-variance):** "Can you reduce both bias AND variance simultaneously?" → Not for a fixed model class and fixed data. But more data reduces variance without changing bias.

4. **(After connections):** "We now have three views of regularization: Week 2 (algebraic), Week 3 (geometric), now (probabilistic). Which view is 'correct'?" → All of them. The probabilistic view is the deepest.

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "What's the difference between likelihood and probability?" | Same function $p(x\|\theta)$, different perspective. "Likelihood" = function of $\theta$ with fixed data. "Probability" = function of $x$ with fixed $\theta$. (30 sec.) |
| "Do I need to memorize the Gaussian formula?" | Yes, but more importantly: log of Gaussian = quadratic. That's the property that makes MSE work. (30 sec.) |
| "What if my data isn't Gaussian?" | Then MSE might not be the right loss! Your loss function encodes your noise assumption. (1 min.) |
| "Is the evidence always hard to compute?" | Often yes. For MLE and MAP, we drop it. Full Bayesian needs it (MCMC — beyond this course). (1 min.) |

---

## Session 2 (80 min): Gradient Descent — Full Week 6 Content

### Learning Objectives

By the end of this session, students should be able to:
1. Define the gradient and explain it points in the direction of steepest ascent.
2. Write the GD update rule: $\mathbf{w} \leftarrow \mathbf{w} - \eta \nabla L(\mathbf{w})$.
3. Perform GD step-by-step on a 1D quadratic ($f(w) = w^2$).
4. Explain the three learning rate regimes (too small, too large, just right).
5. Derive the gradient of MSE w.r.t. $w$ and $b$ using the chain rule.
6. Apply GD to ridge (shrinkage term) and lasso (subgradient).
7. Compare batch GD, SGD, and mini-batch GD.
8. Explain why feature scaling helps and how to avoid data leakage.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos or Python notebook (for the learning rate demo — see `visual_demos.md`)
- Printed or projected handout Sections 6–11
- Quiz S2 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** "We proved MSE = MLE, ridge = MAP, and bias-variance. Now: HOW do we minimize these losses?" |
| 0:05–0:10 | **Paper discussion (5 min).** Ruder (2016). See `suggested_paper.md`. |
| 0:10–0:22 | **The gradient + GD update rule + 1D quadratic example.** | Step-by-step on the board. Core of the session. |
| 0:22–0:32 | **Learning rate regimes (Desmos demo).** | Three runs: too small, just right, too large. |
| 0:32–0:37 | **Convergence condition + convexity.** | Why GD works for MSE. |
| 0:37–0:55 | **GD on MSE: derive the gradient (chain rule).** | Key derivation. Residual + optimality condition. |
| 0:55–1:02 | **Ridge GD + lasso subgradient.** | Connect to Week 3 and Session 1. |
| 1:02–1:10 | **SGD and mini-batch GD.** | Comparison table. Noisy trajectory. |
| 1:10–1:15 | **Feature scaling.** | Week 4 connection (data leakage). |
| 1:15–1:18 | **Monitoring training: loss curves.** | Week 4 connection (learning curves). |
| 1:18–1:20 | **Wrap-up + preview of Week 7.** | |
| 1:20–1:28 | **Quiz (end-of-session).** 8 min. See `quiz_S2.md`. |

> **Note:** We do NOT review derivative rules (power, product, chain rule). Students have had 5+ weeks of calculus. We start directly with the gradient as a concept and immediately apply it to ML.

### Hook: "Why Not Just Use the Formula?" (3 min)

1. "In Session 1, we proved MSE = MLE. We've been using closed-form OLS: $w^* = \text{Cov}(x,y)/\text{Var}(x)$. But what about lasso? Logistic regression? Neural networks?"

2. Write on the board: "Closed-form exists for: OLS, ridge. Does NOT exist for: lasso, logistic regression, neural networks, most models."

3. "When there's no formula, how do we find the minimum? We use an **iterative method**: start somewhere, take a step downhill, repeat. This is gradient descent."

### Board Work: The Gradient + 1D Quadratic (12 min)

**This is the most important part of Session 2.**

1. "The gradient $\nabla f$ is the vector of partial derivatives. It points UPHILL. To go DOWNHILL, use $-\nabla f$." (2 min)

2. **1D quadratic example:** Minimize $f(w) = w^2$. $f'(w) = 2w$. Update: $w \leftarrow w - \eta \cdot 2w$. (10 min)

Start: $w_0 = 3$, $\eta = 0.1$.

| Step | $w$ | $f(w)$ | $f'(w)$ | Step size |
|------|-----|--------|---------|-----------|
| 0 | 3.000 | 9.000 | 6.000 | 0.6 |
| 1 | 2.400 | 5.760 | 4.800 | 0.48 |
| 2 | 1.920 | 3.686 | 3.840 | 0.384 |
| 3 | 1.536 | 2.359 | 3.072 | 0.307 |

**Key teaching moves:**
1. Compute each step with students. "What's $f'(3)$?" → "6." "What's the update?" → "$w = 3 - 0.1 \times 6 = 2.4$."
2. "Notice: $w_{t+1} = w_t(1 - 2\eta) = w_t \times 0.8$. Each step multiplies by 0.8."
3. "For convergence: $|1 - 2\eta| < 1$, so $0 < \eta < 1$."

### Board Work: Learning Rate Regimes (10 min)

**Use Desmos** (see `visual_demos.md`). Show three runs:

1. **$\eta = 0.01$ (too small):** After 50 steps, $w \approx 1.1$. Very slow.
2. **$\eta = 0.1$ (just right):** After 20 steps, $w \approx 0.04$. Smooth.
3. **$\eta = 1.1$ (too large):** $w$ bounces: $3 \to -3.6 \to 4.32 \to \ldots$ Diverging!

### Board Work: Deriving the MSE Gradient (12 min)

**The key derivation of Session 2.**

**Step 1:** $\text{MSE} = \frac{1}{n}\sum_i (y_i - wx_i - b)^2$. Let $r_i = y_i - wx_i - b$.

**Step 2:** $\frac{\partial}{\partial w}(r_i^2) = 2r_i \cdot (-x_i) = -2x_i r_i$ (chain rule).

$$\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$$

**Step 3:** $\frac{\partial r_i}{\partial b} = -1$.

$$\frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$$

**Step 4:** Update rules: $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i$, $b \leftarrow b + \frac{2\eta}{n}\sum r_i$.

**Key teaching moves:**
1. At each step: "What rule do we use?" → "Chain rule!"
2. **Optimality condition:** "At the minimum, $\sum x_i r_i = 0$. Residuals uncorrelated with inputs. Same as OLS from Week 2!"

### Board Work: Ridge and Lasso GD (7 min)

**Ridge:** $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - 2\eta\lambda w$.

"The $-2\eta\lambda w$ term is shrinkage. Same as the closed form from Week 2, but step by step."

**Lasso:** $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - \eta\lambda \, \text{sgn}(w)$.

"The $-\eta\lambda \, \text{sgn}(w)$ drives $w$ to exactly 0. This is why lasso produces exact zeros."

**Connect to Session 1:** "Remember: ridge = MAP with Gaussian prior, lasso = MAP with Laplacian prior. Now we see how GD implements the shrinkage that the prior demands."

### Board Work: SGD vs Batch GD (8 min)

**Comparison table** (handout Section 9.4).

**Key teaching moves:**
1. "Batch GD: all $n$ examples per step. Expensive for large $n$."
2. "SGD: one random example. Super fast, noisy."
3. "Mini-batch: $B = 32$–$128$. Standard for ML/DL."
4. **Noisy trajectory:** Draw smooth (batch) vs. bouncy (SGD) loss curves.
5. "The noise is GOOD for non-convex problems — helps escape local minima."

### Board Work: Feature Scaling (5 min)

1. "Different scales → elongated loss surface → GD zigzags."
2. Draw elongated vs. spherical contours.
3. "Standardize: $x \to (x - \bar{x})/\sigma_x$. Spherical surface. Smooth convergence."
4. **CRITICAL:** "Compute $\bar{x}$, $\sigma_x$ on training data ONLY. Split first! (Week 4)"

### Discussion Prompts

1. **(After 1D example):** "If $\eta = 0.5$, what happens?" → $w_1 = 3(1-1) = 0$. One step! Optimal learning rate.

2. **(After MSE gradient):** "At the minimum, $\sum x_i r_i = 0$. What does this mean?" → Residuals uncorrelated with inputs.

3. **(After SGD):** "If SGD is noisy, why does it work?" → Expected value equals batch gradient (unbiased). Noise averages out.

4. **(After feature scaling):** "How does scaling connect to Week 4's data leakage?" → Compute stats on training only. Split first.

### Things NOT to Cover

| Topic | When |
|-------|------|
| Adam optimizer | Week 17 |
| Backpropagation | Week 16 |
| Newton's method | Beyond scope |
| Autograd | Week 16 |

---

## Challenge Questions for Advanced Students

### Session 1 Challenges

**Challenge 6C-1A: The Prosecutor's Fallacy**
*(Give after the medical testing example — around minute 13)*

> DNA at a crime scene matches the suspect. The random match probability is 1/10,000. The prosecutor says: "The probability of this match is 1/10,000, so the probability the suspect is innocent is 1/10,000."
>
> **Question:** What's wrong? Use Bayes' theorem. What prior do you need?

**Instructor notes:**
- Confusing $P(\text{match}|\text{innocent})$ with $P(\text{innocent}|\text{match})$.
- If there are $N$ possible suspects, $P(\text{guilty}) \approx 1/N$. For $N = 100$: $P(\text{guilty}|\text{match}) \approx 50\%$.

---

**Challenge 6C-1B: MLE for the Uniform Distribution**
*(Give after Bernoulli MLE — around minute 25)*

> Observe $x_1, \ldots, x_n$ from Uniform$(0, \theta)$: $p(x \mid \theta) = 1/\theta$ for $0 \leq x \leq \theta$.
>
> **Question:** What is the MLE of $\theta$? Is this estimator biased?

**Instructor notes:**
- Likelihood: $\theta^{-n}$ for $\theta \geq \max(x_i)$, 0 otherwise. Maximize by minimizing $\theta$: $\hat{\theta} = \max(x_i)$.
- Biased: $\mathbb{E}[\max(x_i)] = \frac{n}{n+1}\theta < \theta$. MLE is not always unbiased!

---

**Challenge 6C-1C: The Laplacian Prior → Lasso**
*(Give after MAP=Ridge — around minute 45)*

> Show that MAP with Gaussian noise + Laplacian prior gives lasso. What is $\lambda$? Why does the Laplacian cause sparsity?

**Instructor notes:**
- $\log p(w) = -|w|/\tau$. MAP: MSE + $(\sigma^2/\tau)|w|$. $\lambda = \sigma^2/\tau$.
- Sparsity: The Laplacian has a sharp peak at 0 (non-differentiable).

---

### Session 2 Challenges

**Challenge 6C-2A: Optimal Learning Rate for Quadratics**
*(Give after the 1D example — around minute 20)*

> For $f(w) = \frac{1}{2}aw^2$, the update is $w \leftarrow w(1 - \eta a)$. (a) What $\eta$ reaches the minimum in one step? (b) What happens at $\eta = 2/a$? (c) Derive $0 < \eta < 2/a$ for convergence.

**Instructor notes:**
- (a) $\eta = 1/a$: $w_1 = 0$. One step.
- (b) $\eta = 2/a$: $w_1 = -w_0$. Oscillates forever.
- (c) $|1 - \eta a| < 1 \Rightarrow 0 < \eta < 2/a$.
- **Follow-up:** "This is why we standardize features. Large scale → large $a$ → small max $\eta$."

---

**Challenge 6C-2B: The SGD Variance**
*(Give after SGD — around minute 65)*

> Batch gradient: $g_{\text{batch}} = -\frac{2}{n}\sum x_i r_i$. SGD gradient: $g_i = -2x_i r_i$. (a) Show $\mathbb{E}[g_i] = g_{\text{batch}}$. (b) How does variance change with batch size $B$?

**Instructor notes:**
- (a) $\mathbb{E}_i[g_i] = \frac{1}{n}\sum(-2x_i r_i) = g_{\text{batch}}$. Unbiased.
- (b) $\text{Var}(g_{\text{batch}}) = \text{Var}(g_i)/B$. Larger $B$ → lower variance.

---

**Challenge 6C-2C: The Soft-Thresholding Operator**
*(Give after lasso subgradient — around minute 58)*

> For $L(w) = \frac{1}{2}(w - c)^2 + \lambda|w|$ with $c > 0$: (a) Find the minimizer. (b) For what $\lambda$ is $w^* = 0$? (c) Write the solution as a single formula.

**Instructor notes:**
- (a) For $w > 0$: $w = c - \lambda$ (valid if $c > \lambda$).
- (b) $w^* = 0$ when $\lambda \geq c$.
- (c) $w^* = \text{sign}(c)(|c| - \lambda)_+$ (soft-thresholding).

---

## Post-Session Checklist

- [ ] Review quiz results (both sessions)
- [ ] Update student progress tracker
- [ ] Prepare spiral-back questions
- [ ] Preview next session

---

## Preparation Checklist

### Before Session 1

- [ ] Read handout Sections 1–5
- [ ] Prepare the Bayes' theorem ML interpretation board work
- [ ] Prepare the medical testing tree diagram
- [ ] Prepare the MLE for Bernoulli derivation (step by step)
- [ ] Prepare the MLE=MSE proof (the key derivation)
- [ ] Prepare the MAP=Ridge proof
- [ ] Prepare the bias-variance decomposition derivation (complete)
- [ ] Print quiz S1

### Before Session 2

- [ ] Read handout Sections 6–11
- [ ] Prepare the 1D quadratic GD example (step-by-step table)
- [ ] Prepare the Desmos demo with three learning rates
- [ ] Prepare the MSE gradient derivation (chain rule steps)
- [ ] Prepare ridge/lasso GD derivation
- [ ] Prepare SGD vs batch GD comparison table
- [ ] Prepare feature scaling demo
- [ ] Print quiz S2
- [ ] Read the suggested paper (Ruder, 2016)
