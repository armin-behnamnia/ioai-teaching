# Week 5 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): Bayes' Theorem for ML + MLE

### Learning Objectives

By the end of this session, students should be able to:
1. Identify the prior, likelihood, evidence, and posterior in a Bayesian ML formulation.
2. Explain why the evidence can be dropped for optimization (MLE and MAP).
3. Apply Bayes' theorem to the medical testing example and connect it to class imbalance (Week 4).
4. State the MLE principle and the log-likelihood trick.
5. Derive MLE for Bernoulli (→ sample mean) and Gaussian (→ sample mean and variance).
6. **Prove that MLE under Gaussian noise = minimizing MSE.**

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Printed or projected handout Sections 2–4
- Quiz S1 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:08 | **Recap of Weeks 1–4 + Hook.** | See Hook section below. |
| 0:08–0:22 | **Bayes' theorem applied to ML.** | Students know Bayes' theorem. Focus on the ML interpretation: prior/likelihood/posterior. |
| 0:22–0:32 | **Medical testing example + class imbalance connection.** | The "aha" moment: Bayes = precision from Week 4. |
| 0:32–0:45 | **MLE: principle, log-likelihood trick, Bernoulli derivation.** | Derive on board. Students should be able to reproduce. |
| 0:45–0:52 | **MLE for Gaussian (quick).** | Same pattern. Emphasize: MLE of mean = sample mean. |
| 0:52–0:68 | **The deep connection: MLE = MSE.** | The payoff. Derive carefully. |
| 0:68–0:72 | **The correspondence table + what if noise isn't Gaussian.** | Gaussian→MSE, Bernoulli→cross-entropy, Laplacian→MAE. |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S1.md`. |

> **Note:** We do NOT review probability basics (PMF/PDF, expectation, variance, joint/marginal/conditional distributions). Students have had 5 weeks of probability. If any student is struggling, refer them to their probability course notes. We start directly with Bayes' theorem applied to ML.

### Hook: "The Questions We've Been Postponing" (8 min)

**Goal:** Motivate probability by cashing in the promises from Weeks 1–4.

**Instructions:**

1. Write on the board: "Three promises:"
   - Week 2: "MSE is not arbitrary — it corresponds to Gaussian noise. We'll prove this in Week 5."
   - Week 2: "Ridge corresponds to a prior on weights. We'll formalize this."
   - Week 3: "Bias-variance has a formal decomposition. It comes in Week 5 with probability."

2. "This week, we deliver on all three. You already know probability — random variables, distributions, Bayes' theorem. Now we use probability as a **language for ML**: understanding *why* we use MSE, *why* ridge works, and *what* the bias-variance tradeoff actually is."

3. **The punchline:** "By the end of today, you'll know *why* MSE is the right loss function (it's the maximum likelihood estimator under Gaussian noise). By the end of next session, you'll know *why* ridge works (it's a Gaussian prior) and *what* bias-variance is (a mathematical decomposition of expected error)."

### Board Work: Bayes' Theorem for ML (14 min)

**Students know Bayes' theorem.** Don't derive it — *interpret* it for ML.

**Key teaching moves:**

1. Write Bayes' theorem on the board with ML labels:
   $$\underbrace{p(\theta \mid \mathcal{D})}_{\text{posterior}} = \frac{\overbrace{p(\mathcal{D} \mid \theta)}^{\text{likelihood}} \, \overbrace{p(\theta)}^{\text{prior}}}{\underbrace{p(\mathcal{D})}_{\text{evidence}}}$$

2. Fill in the table: Prior (belief before data), Likelihood (how data relates to parameter), Evidence (normalizer), Posterior (updated belief).

3. "The Bayesian learning loop: Prior → observe data → Posterior. This IS learning, mathematically."

4. **Why drop the evidence?** "For finding the best $\theta$ (optimization), the evidence doesn't depend on $\theta$. So MLE and MAP can ignore it. This is why MLE and MAP are practical — they avoid the hardest part of Bayes' theorem."

5. "Probability asks: given a model, what data do we expect? ML asks: given data, what model should we choose? Bayes' theorem is the bridge."

### Board Work: Medical Testing = Class Imbalance (10 min)

Work through the medical testing example (handout Section 2.3) on the board.

**Draw a tree diagram:**

```
                    ┌── P(pos|D) = 0.99 ── P(D∩pos) = 0.0099
  P(D) = 0.01 ────┤
                    └── P(neg|D) = 0.01

                    ┌── P(pos|¬D) = 0.05 ── P(¬D∩pos) = 0.0495
  P(¬D) = 0.99 ────┤
                    └── P(neg|¬D) = 0.95
```

Compute: $P(\text{disease}|\text{positive}) = 0.0099 / 0.0594 = 1/6 \approx 16.7\%$.

**The "aha" moment:** "Even with a 99% sensitive test, a positive result means only 16.7% chance of disease!"

**Connect to Week 4:** "What is $P(\text{disease}|\text{positive})$ in Week 4 terms?" → **Precision!** "When the positive class is rare (1%), even a good test generates more false positives than true positives. The prior dominates the posterior. This is EXACTLY the class imbalance problem from Week 4."

### Board Work: MLE for Bernoulli (13 min)

**This derivation is a quiz topic.** Students must be able to reproduce it.

**Step-by-step on the board:**

1. **Setup:** $x_1, \ldots, x_n \in \{0,1\}$, i.i.d. Bernoulli($\theta$).

2. **Likelihood:** $p(\mathcal{D}|\theta) = \prod_i \theta^{x_i}(1-\theta)^{1-x_i}$

3. **Log-likelihood:** $\ell(\theta) = k\log\theta + (n-k)\log(1-\theta)$, where $k = \sum_i x_i$.

4. **Differentiate:** $\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n-k}{1-\theta} = 0$

5. **Solve:** $\hat{\theta} = k/n = \frac{1}{n}\sum_i x_i$

**The punchline:** "The MLE for a Bernoulli is the sample mean. Intuitive — and now proven."

**Key teaching moves:**
- At each step, ask "What do we do next?"
- Emphasize the log-likelihood trick: products → sums, numerical stability.
- Students' probability course covered this — but frame it as "the ML answer to 'what parameter best explains the data?'"

### Board Work: MLE = MSE (16 min)

**This is the single most important derivation in Week 5.**

**Step 1: The model.** $y_i = wx_i + b + \epsilon_i$, $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$.

**Step 2: The likelihood.** $\prod_i \mathcal{N}(y_i | wx_i + b, \sigma^2)$

**Step 3: The log-likelihood.** $\ell(w,b) = \text{const} - \frac{1}{2\sigma^2}\sum_i (y_i - wx_i - b)^2$

**Step 4: The key step.** Circle the sum. "This is $n \cdot \text{MSE}(w,b)$!"

$$\ell(w,b) = \text{const} - \frac{1}{2\sigma^2} \cdot n \cdot \text{MSE}(w,b)$$

"Maximizing $\ell$ = minimizing MSE. **The loss function IS the negative log-likelihood.**"

**Write prominently:**

> **MSE is not arbitrary. It is the maximum likelihood estimator under Gaussian noise.**

**Step 5: The correspondence table.** Gaussian → MSE, Bernoulli → cross-entropy, Laplacian → MAE.

"Every loss function corresponds to a noise model. Choosing a loss function is choosing a probabilistic assumption."

**Connect to Week 2:** "In Week 2, I said 'MSE is not arbitrary — we'll prove this in Week 5.' Here's the proof."

### Discussion Prompts

1. **(After medical testing):** "In the medical testing example, what happens if the disease prevalence is 50% instead of 1%?" → $P(\text{dis}|\text{pos}) = 95.2\%$. When the prior is balanced, the likelihood dominates. Rare events are hard to detect — even with good tests.

2. **(After MLE=MSE):** "If MSE corresponds to Gaussian noise, what loss would you use if your data has occasional large outliers?" → MAE (Laplacian noise). The Laplacian has heavier tails.

3. **(After the correspondence table):** "We've been using MSE for regression. Next week we'll use cross-entropy for classification. Why different losses?" → Different noise models. Regression: continuous target, Gaussian noise → MSE. Classification: binary target, Bernoulli → cross-entropy. The loss function matches the data type.

### Anticipated Questions from Students

| Question | How to Answer |
|----------|--------------|
| "Is the evidence $p(\mathcal{D})$ always hard to compute?" | Often yes. For MLE and MAP, we drop it. For full Bayesian inference, we need it (MCMC, variational methods — beyond this course). (1 min.) |
| "What's the difference between likelihood and probability?" | Same function $p(x|\theta)$, different perspective. "Likelihood" = function of $\theta$ with fixed data. "Probability" = function of $x$ with fixed $\theta$. (30 sec.) |
| "Do I need to memorize the Gaussian formula?" | Yes, but more importantly: log of Gaussian = quadratic. That's the property that makes MSE work. (30 sec.) |
| "What if my data isn't Gaussian?" | Then MSE might not be the right loss! Laplacian noise → MAE. Your loss function encodes your noise assumption. (1 min.) |

---

## Session 2 (80 min): MAP, Ridge, and Bias-Variance Decomposition

### Learning Objectives

By the end of this session, students should be able to:
1. State the MAP principle and prove that MAP with a Gaussian prior = ridge regression.
2. Explain what $\lambda = \sigma^2/\tau^2$ means.
3. Show that a Laplacian prior gives lasso.
4. Derive the bias-variance decomposition: Expected error = Bias² + Variance + Irreducible noise.
5. Connect the formal decomposition to the intuition from Week 3 and the learning curves from Week 4.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Printed or projected handout Sections 5–6
- Colored markers (for the bias-variance tradeoff diagram)
- Quiz S2 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** Quick: "State MLE. What does MLE=MSE mean?" |
| 0:05–0:10 | **Paper discussion (5 min).** "Visual Information Theory" by Olah. See `suggested_paper.md`. |
| 0:10–0:28 | **MAP: principle, Gaussian prior → ridge.** | Second payoff. Derive carefully. |
| 0:28–0:35 | **Laplacian prior → lasso + correspondence table.** | Quick — same pattern. |
| 0:35–0:38 | **What does a prior do? Connect to Week 3.** | $\lambda = \sigma^2/\tau^2$. |
| 0:38–0:58 | **Bias-variance decomposition.** | Third payoff. Derive the cross terms vanishing. |
| 0:58–0:68 | **Connect to Week 3 (table) + Week 4 (learning curves).** | The decomposition justifies everything. |
| 0:68–0:72 | **Summary: the three deep connections.** | |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S2.md`. |

> **Note:** This session has more time for derivations since we skipped the probability review in Session 1. If students are comfortable with the MLE=MSE proof from Session 1, spend the extra time on the bias-variance derivation and its connections.

### Board Work: MAP = Ridge (18 min)

**Step 1: MAP principle.** $\hat{\theta}_{\text{MAP}} = \arg\max_\theta [\log p(\mathcal{D}|\theta) + \log p(\theta)]$

"MAP = MLE + prior. The log-prior acts as a penalty."

**Step 2: Gaussian prior on $w$.** $w \sim \mathcal{N}(0, \tau^2)$. $\log p(w) = -w^2/(2\tau^2) + \text{const}$.

**Step 3: Combine.**

$$\text{Minimize:} \quad \frac{1}{2\sigma^2}\sum_i (y_i - wx_i - b)^2 + \frac{1}{2\tau^2}w^2$$

Multiply by $2\sigma^2$: $\text{MSE} + (\sigma^2/\tau^2)w^2 = \text{MSE} + \lambda w^2$.

**Write prominently:**

> **Ridge = MAP with Gaussian noise + Gaussian prior. $\lambda = \sigma^2/\tau^2$.**

**Connect to Week 3:** "In Week 3, we tuned $\lambda$ with CV. Now we know what $\lambda$ IS: the noise-to-prior ratio. If the data is noisy ($\sigma^2$ large), $\lambda$ is large → more regularization. If the prior is weak ($\tau^2$ large), $\lambda$ is small → less regularization."

**The full table:**

| Prior | → Regularization |
|-------|-----------------|
| Gaussian | L2 (Ridge) |
| Laplacian | L1 (Lasso) |
| Uniform | None (MLE = OLS) |

### Board Work: Bias-Variance Decomposition (20 min)

**Step 1: Setup.** $y = f(x) + \epsilon$, $\epsilon \sim \mathcal{N}(0, \sigma^2)$.

**Step 2: Expected test error.** $\mathbb{E}_\mathcal{D}[(y - \hat{f}(x))^2]$

**Step 3: Decompose.** Let $\bar{f} = \mathbb{E}_\mathcal{D}[\hat{f}]$.

$y - \hat{f} = (f - \bar{f}) + (\bar{f} - \hat{f}) + \epsilon = A + B + C$

**Step 4: Expand.** $\mathbb{E}[(A+B+C)^2] = \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$

**Step 5: Cross terms vanish.**
- $\mathbb{E}[AB] = 0$ because $\mathbb{E}[B] = 0$.
- $\mathbb{E}[AC] = 0$ because $\mathbb{E}[\epsilon] = 0$.
- $\mathbb{E}[BC] = 0$ because $\epsilon \perp \mathcal{D}$ and $\mathbb{E}[\epsilon] = 0$.

**Step 6: Result.** $\text{Expected error} = \text{Bias}^2 + \text{Variance} + \sigma^2$

**Step 7: Interpretation table + the tradeoff diagram.**

**Step 8: Connect to Week 3.** Show the table ($\lambda=0$: low bias/high variance; $\lambda \to \infty$: high bias/low variance). "Now it's a theorem."

**Step 9: Connect to Week 4.** "Learning curves: large gap = high variance. Both high + small gap = high bias. As $n \to \infty$, variance → 0, bias stays."

### Discussion Prompts

1. **(After MAP=Ridge):** "What happens if we use a Laplacian prior?" → Lasso. The sharp peak at 0 causes sparsity.

2. **(After bias-variance):** "Can you reduce both bias AND variance simultaneously?" → Not for a fixed model class and fixed data. But more data reduces variance without changing bias. Better models (ensembles) can sometimes reduce both.

3. **(After connections):** "We now have three views of regularization: Week 2 (algebraic, $\lambda w^2$), Week 3 (geometric, L2 ball), Week 5 (probabilistic, Gaussian prior). Which view is 'correct'?" → All of them. They're three perspectives on the same phenomenon. The probabilistic view is the deepest — it explains *why* ridge works.

### Things NOT to Cover (Save for Later)

| Topic | When |
|-------|------|
| Full Bayesian inference (posterior distribution, not just MAP point estimate) | Beyond course scope |
| MCMC, variational inference | Beyond course scope |
| Conjugate priors | Beyond course scope |
| Cross-entropy loss derivation | Week 7 (logistic regression) |
| KL divergence | Week 11 (information theory) |
| Matrix-form MLE/MAP | Week 8 (matrix linear regression) |

---

## Challenge Questions for Advanced Students

### Session 1 Challenges

**Challenge 5-1A: The Prosecutor's Fallacy**
*(Give after the medical testing example — around minute 30)*

> DNA at a crime scene matches the suspect. The random match probability is 1/10,000. The prosecutor says: "The probability of this match is 1/10,000, so the probability the suspect is innocent is 1/10,000."
>
> **Question:** What's wrong? Use Bayes' theorem. What prior do you need? How does this relate to the medical testing example?

**Instructor notes:**
- Confusing $P(\text{match}|\text{innocent})$ with $P(\text{innocent}|\text{match})$.
- If there are $N$ possible suspects, $P(\text{guilty}) \approx 1/N$. For $N = 100$: $P(\text{guilty}|\text{match}) \approx 50\%$. Not 99.99%.
- Same as medical testing: DNA test = medical test, suspect pool = prevalence.

---

**Challenge 5-1B: Spam Filtering with Bayes**
*(Give after spam filtering setup — around minute 35)*

> In the spam filter setup, we need $P(x \mid \text{spam})$ — the probability of the email features given that it's spam. If $x$ is a vector of word presence/absence (e.g., "FREE" = 1/0, "VIAGRA" = 1/0, etc.), computing $P(x \mid \text{spam})$ requires modeling the joint distribution of all words.
>
> **Question:** The **Naive Bayes** assumption is that words are conditionally independent given the class: $P(x \mid \text{spam}) = \prod_j P(x_j \mid \text{spam})$. Why is this "naive"? Is it realistic? Why does it work well in practice despite being wrong?

**Instructor notes:**
- Words are NOT independent (e.g., "NEW" and "YORK" co-occur). The assumption is wrong.
- It works because: (1) we only need the posterior to be correct *relative to* the other class, not absolutely; (2) the independence assumption introduces consistent bias that doesn't affect the argmax much; (3) with many features, the errors partially cancel.
- Connects to Week 7 (logistic regression doesn't make this independence assumption).

---

### Session 2 Challenges

**Challenge 5-2A: MLE for the Uniform Distribution**
*(Give after Bernoulli MLE — around minute 20)*

> Observe $x_1, \ldots, x_n$ from Uniform$(0, \theta)$: $p(x \mid \theta) = 1/\theta$ for $0 \leq x \leq \theta$.
>
> **Question:** What is the MLE of $\theta$? (Hint: think about what happens if $\theta < \max(x_i)$.) Is this estimator biased?

**Instructor notes:**
- Likelihood: $\theta^{-n}$ for $\theta \geq \max(x_i)$, 0 otherwise. Maximize by minimizing $\theta$: $\hat{\theta} = \max(x_i)$.
- Biased: $\mathbb{E}[\max(x_i)] = \frac{n}{n+1}\theta < \theta$. MLE is not always unbiased!

---

**Challenge 5-2B: The Laplacian Prior → Lasso**
*(Give after MAP=Ridge — around minute 30)*

> We showed Gaussian prior → ridge. Now consider a **Laplacian** prior: $p(w) = \frac{1}{2\tau}\exp(-|w|/\tau)$.
>
> **Question:** Show that MAP with Gaussian noise + Laplacian prior gives **lasso**. What is $\lambda$? Why does the Laplacian cause sparsity?

**Instructor notes:**
- $\log p(w) = -|w|/\tau$. MAP: MSE + $(\sigma^2/\tau)|w|$. So $\lambda = \sigma^2/\tau$.
- Sparsity: The Laplacian has a sharp peak at 0 (non-differentiable). The L1 penalty has a "corner" at 0 that pushes solutions to exactly 0.
- Connect to Week 3: "L1 diamond's corners are on the axes — that's why the solution lands on an axis ($w_j = 0$)."

---

**Challenge 5-2C: Bias-Variance for k-NN**
*(Give after bias-variance — around minute 55)*

> In Week 9, we'll learn k-NN: predict the average of the $k$ nearest neighbors.
>
> **Question:** (a) $k = 1$: high or low bias? High or low variance? (b) $k = n$: what happens? (c) How does $k$ relate to $\lambda$ in ridge?

**Instructor notes:**
- $k=1$: low bias (matches nearest point), high variance (depends on one point).
- $k=n$: high bias (predicts $\bar{y}$), zero variance.
- $k$ and $\lambda$ are inverse: small $k$ = small $\lambda$ (low bias, high variance).

---

### Managing Advanced Students

| Situation | Strategy |
|-----------|----------|
| Student knows Bayes well | Give Challenge 5-1A (Prosecutor's Fallacy) or 5-1B (Naive Bayes) |
| Student finds MLE trivial | Give Challenge 5-2A (Uniform MLE — non-standard) |
| Student asks about full Bayesian inference | "MAP gives a point estimate. Full Bayesian gives a distribution. MAP is the mode of the posterior. Full Bayesian needs the evidence — harder. Beyond this course." |

---

## Post-Session Checklist

After each session:

- [ ] Review quiz results and note common mistakes
- [ ] Update the student progress tracker
- [ ] Prepare spiral-back questions for the next quiz
- [ ] Check if any student needs intervention
- [ ] Preview next session's material

---

## Preparation Checklist for Week 5

### Before Session 1

- [ ] Read handout Sections 1–4
- [ ] Prepare the Bayes' theorem ML interpretation board work
- [ ] Prepare the medical testing tree diagram
- [ ] Prepare the MLE for Bernoulli derivation (step by step)
- [ ] Prepare the MLE=MSE proof (the key derivation)
- [ ] Print quiz S1
- [ ] Review Weeks 1–4 — be ready to connect MSE, ridge, and bias-variance to probability

### Before Session 2

- [ ] Read handout Sections 5–6
- [ ] Prepare the MAP=Ridge proof
- [ ] Prepare the bias-variance decomposition derivation
- [ ] Prepare the bias-variance tradeoff diagram
- [ ] Print quiz S2
- [ ] Review Session 1 quiz results
- [ ] Read the suggested paper ("Visual Information Theory" by Olah)
