# Week 7, Session 2 — End-of-Session Quiz

> **Time:** 6 minutes (short — derivation-heavy day)
> **Topics:** MAP = Ridge, Laplacian prior → Lasso, bias-variance decomposition
> **Format:** 3 questions
> **Closed notes**
> **Note:** The full derivations are re-assessed in the Week 8 mini-exam. This quiz checks the load-bearing steps.

---

## Questions

**Q1. [Reconstruction — 3 min]**

Complete the MAP = Ridge chain (fill in the blanks):

$$\hat{w}_{\text{MAP}} = \arg\max_w \big[\log p(\mathcal{D}\mid w) + \underline{\hspace{2cm}}\big]$$

With Gaussian noise ($\sigma^2$) and a Gaussian prior $w \sim \mathcal{N}(0, \tau^2)$, minimizing the negative log-posterior gives:

$$\sum_i (y_i - wx_i - b)^2 + \underline{\hspace{1cm}} \cdot w^2$$

(a) Fill blank 1. (b) Fill blank 2 (in terms of $\sigma^2$ and $\tau^2$). (c) What is this method called?

**Q2. [Multiple choice — 1 min]**

In the bias-variance decomposition $\mathbb{E}[(y - \hat{f})^2] = \text{Bias}^2 + \text{Variance} + \sigma^2$, which term(s) can be reduced by collecting MORE training data?

(a) Bias$^2$ only.
(b) Variance only.
(c) Both.
(d) $\sigma^2$.

Justify in one sentence.

**Q3. [Conceptual — 2 min]**

(a) In one sentence: why does a Laplacian prior produce sparse (exactly-zero) weights while a Gaussian prior does not?
(b) If the data becomes noisier ($\sigma^2$ increases) and the prior stays the same, what happens to the effective $\lambda$, and what does that mean for the fitted model?

---

## Solutions

### Q1. Solution

(a) $\log p(w)$ — the log-prior.
(b) $\lambda = \sigma^2/\tau^2$ (the multiplier of $w^2$ after scaling by $2\sigma^2$).
(c) Ridge regression.

**Grading:** 0–3.
- 3: All three parts.
- 2: Two parts.
- 1: One part.
- 0: None.

**Common mistakes:**
- $\lambda = \tau^2/\sigma^2$ (inverted — "noise on top": λ grows with σ²).
- Writing the prior as a penalty on the *data* rather than on $w$.

### Q2. Solution

**Answer: (b).** More training data reduces the randomness of the fitted model (how much $\hat f$ wobbles with the sample) — the variance term. Bias is a property of the model class/average fit and is unchanged; $\sigma^2$ is in the world, not the data size.

**Grading:** 0–3.
- 3: (b) + wobble/instability justification.
- 2: (b) + weak justification.
- 1: (b) only.
- 0: Wrong.

**Common mistakes:**
- Choosing (c) — "more data helps everything" intuition.

### Q3. Solution

(a) The Laplacian has a sharp non-differentiable corner at 0: its penalty $|w|$ pushes weights toward zero at constant speed and lets them land exactly on 0; the Gaussian penalty $w^2$ is smooth and flat at 0, so it shrinks toward but (generically) never reaches 0.
(b) $\lambda = \sigma^2/\tau^2$ increases → stronger shrinkage → a flatter, more regularized (higher-bias, lower-variance) model. "Noisier data → trust the prior more."

**Grading:** 0–3.
- 3: Corner/smoothness mechanism + correct λ direction with interpretation.
- 2: One part fully correct.
- 1: Fragments.
- 0: None.

**Common mistakes:**
- "Laplacian is spiky, so weights get spiky" — circular phrasing without the constant-speed-push mechanism.
- Saying λ decreases with noise.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | MAP = Ridge | | |
| Q2 | Bias-variance terms | | |
| Q3 | Sparsity mechanism + λ interpretation | | |

---

## Post-Quiz Notes

- [ ] MAP = Ridge is the most exam-critical derivation so far — anyone below 2 gets a re-derive assignment for homework.
- [ ] Bias-variance term-identification errors → re-spiral in Week 8 quizzes and the Phase 1 mini-exam.
- [ ] Topics to spiral: MAP=Ridge → Week 8 (matrix form), regularized logistic regression (Week 8 S2).
