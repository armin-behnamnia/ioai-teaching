# Week 5, Session 2 — End-of-Session Quiz

> **Time:** 10 minutes  
> **Topics:** MAP, MAP↔loss-function correspondence, bias-variance decomposition  
> **Format:** 6 questions, mix of derivation, conceptual, and multiple choice  
> **Closed notes**  
> **Note:** Q6 is a spiral-back question from Session 1.

---

## Questions

**Q1. [Conceptual — 2 min]**

Fill in the blanks and explain:

"Minimizing MSE is equivalent to ___ under the assumption that the noise follows a ___ distribution."

State the key step in the proof that makes this equivalence work.

**Q2. [Multiple choice — 1 min]**

Ridge regression corresponds to MAP estimation with:

(a) Gaussian noise and a Laplacian prior  
(b) Gaussian noise and a Gaussian prior  
(c) Laplacian noise and a Gaussian prior  
(d) Laplacian noise and a Laplacian prior

Justify your answer in one sentence.

**Q3. [Conceptual — 2 min]**

In MAP estimation, the regularization parameter $\lambda = \sigma^2 / \tau^2$ (noise-to-prior ratio).

(a) What happens to $\lambda$ when the prior is very strong ($\tau^2 \to 0$)? What does this mean for the model?  
(b) What happens to $\lambda$ when we have very little data? Should we rely more on the prior or the likelihood? Why?

**Q4. [Conceptual — 1 min]**

Write the bias-variance decomposition. For each term, state whether it can be reduced by (a) adding more training data, (b) using a more complex model, or (c) neither.

**Q5. [Conceptual — 2 min]**

A prior on $w$ has the form $p(w) \propto \exp(-|w|/\tau)$ (Laplacian). Following the MAP derivation, what regularization does this give? Why does this prior cause sparsity (weights going to exactly 0) while a Gaussian prior does not?

**Q6. [Spiral-back from Session 1 — 1 min]**

In Session 1, we learned that MLE finds the parameter that makes the data most likely. MAP adds a prior. In one sentence: what does the prior do that MLE alone does not?

**★ [Challenge — optional, 2 min]**

Suppose you have a dataset where 5% of the points are extreme outliers. You're fitting linear regression.

(a) Would you expect OLS or MAE to perform better? Why?  
(b) What noise model does MAE correspond to (via MLE)?  
(c) What does this tell you about the relationship between loss functions and data assumptions?

---

---

## Solutions

### Q1. Solution

"Minimizing MSE is equivalent to **MLE** under the assumption that the noise follows a **Gaussian** distribution."

**Key step:** The Gaussian log-likelihood $\ell(w,b) = \text{const} - \frac{1}{2\sigma^2}\sum_i (y_i - wx_i - b)^2$. The sum is $n \cdot \text{MSE}$. Maximizing $\ell$ = minimizing MSE.

**Grading:** 0–3.  
- 3: Both blanks + key step.  
- 2: Both blanks, weak step.  
- 1: One blank.  
- 0: Neither.

### Q2. Solution

**Answer: (b)** Gaussian noise and a Gaussian prior.

**Justification:** Gaussian noise → MSE (data term). Gaussian prior → log-prior is $-w^2/(2\tau^2)$ → L2 penalty. Combined: MSE + $\lambda w^2$ = ridge.

**Grading:** 0–3.  
- 3: Correct + justification.  
- 2: Correct, weak.  
- 1: Wrong but reasonable.  
- 0: Wrong.

**Common mistakes:**
- (a): Gaussian + Laplacian = lasso, not ridge.
- (d): Laplacian + Laplacian = MAE + L1.

### Q3. Solution

**(a)** $\tau^2 \to 0 \Rightarrow \lambda = \sigma^2/\tau^2 \to \infty$. Infinite regularization: $w \to 0$, model predicts $\bar{y}$. Maximum bias, zero variance.

**(b)** With little data, the likelihood is unreliable (high variance). Rely more on the prior — it stabilizes the estimate. This is what ridge does: when $n$ is small, $\lambda w^2$ dominates and prevents extreme weights.

**Grading:** 0–3.  
- 3: (a) $\lambda \to \infty$, $w \to 0$. (b) Rely on prior, data unreliable.  
- 2: One part correct.  
- 1: One partial.  
- 0: Neither.

**Common mistakes:**
- (a) Saying $\lambda$ decreases (it increases — $\tau^2$ in denominator).
- (b) Saying "rely on data" (data is unreliable when scarce).

### Q4. Solution

$$\text{Expected error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible noise}$$

| Term | (a) More data? | (b) More complex? | (c) Neither? |
|------|----------------|-------------------|--------------|
| Bias² | No | Yes (↓) | |
| Variance | Yes (↓) | Yes (↑) | |
| Irreducible | | | Yes |

**Grading:** 0–3.  
- 3: Correct decomposition + all cells.  
- 2: Decomposition correct, one cell wrong.  
- 1: Decomposition or reasoning, not both.  
- 0: Neither.

**Common mistakes:**
- More data reduces bias (no — only variance).
- More complex reduces variance (no — increases it).

### Q5. Solution

Laplacian prior → **lasso** (L1 penalty $\lambda|w|$, where $\lambda = \sigma^2/\tau$).

**Sparsity:** The Laplacian has a sharp, non-differentiable peak at $w = 0$. The L1 penalty $|w|$ has a "corner" at 0 that drives the solution to exactly 0 when the data signal is weak. The Gaussian (L2) is smooth at 0 — it shrinks toward 0 but never reaches it.

**Grading:** 0–3.  
- 3: Identifies lasso + explains sparsity via non-differentiability/corner at 0.  
- 2: Identifies lasso, weak sparsity explanation.  
- 1: Identifies lasso only.  
- 0: Wrong.

### Q6. Solution (Spiral-Back)

The prior encodes beliefs about the parameter before seeing data, acting as a regularizer that pulls the estimate toward values considered likely a priori. MLE alone has no prior — it only uses the data, which can overfit when data is scarce.

**Grading:** 0–3.  
- 3: Mentions prior beliefs AND regularization/prevents overfitting.  
- 2: One of the two.  
- 1: Vague.  
- 0: Nothing.

### ★ Challenge Solution

**(a)** MAE. OLS (MSE) squares errors — outliers have disproportionate effect. MAE treats errors linearly, so outliers have less influence.

**(b)** Laplacian (double exponential) noise. Heavier tails than Gaussian — large errors are more "expected."

**(c)** The loss function IS a probabilistic assumption. MSE assumes Gaussian noise; MAE assumes Laplacian. If data has outliers, the Gaussian assumption is wrong.

**Grading:** Bonus.  
- "Excellent": All three correct.  
- "Good attempt": Two correct.  
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | MLE = MSE | | |
| Q2 | MAP = Ridge | | |
| Q3 | Role of $\lambda$ | | |
| Q4 | Bias-variance decomposition | | |
| Q5 | Laplacian → lasso + sparsity | | |
| Q6 | Spiral-back: what does a prior do? | | |
| ★ | MSE vs MAE and noise models | | |

---

## Post-Quiz Notes

- [ ] Can students derive MLE=MSE? → If not, re-derive at start of Week 6.
- [ ] Do students understand MAP=Ridge? → If not, connect to Week 3's $\lambda$.
- [ ] Can students state bias-variance and identify what reduces each term? → If not, draw the tradeoff curve.
- [ ] Do students understand lasso sparsity from the Laplacian prior? → If not, connect to Week 3's L1 diamond.

### Topics to spiral back:

- MLE for Bernoulli → Week 7 (cross-entropy = Bernoulli MLE)
- MAP = Ridge → Week 7 (regularized logistic), Week 8 (Bayesian LR)
- Bias-variance → Week 9 (k-NN), Week 10 (tree depth)
- Loss↔noise correspondence → Week 7 (cross-entropy), Week 11 (KL divergence)
