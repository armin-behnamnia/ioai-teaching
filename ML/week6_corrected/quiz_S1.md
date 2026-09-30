# Week 6 (Corrected), Session 1 — End-of-Session Quiz

> **Time:** 8 minutes
> **Topics:** Bayes' theorem, MLE derivations, MLE = MSE proof, MAP = Ridge proof, bias-variance decomposition
> **Format:** 6 questions
> **Closed notes**
> **Note:** This quiz covers the Week 5 material that was not assessed last week.

---

## Questions

**Q1. [Calculation — 2 min]**

You flip a coin 20 times and get 14 heads. Using MLE, what is your estimate of $P(\text{heads})$? Show the key step of the derivation.

**Q2. [Derivation — 2 min]**

For the linear model $y_i = wx_i + b + \epsilon_i$ with $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$:

(a) Write the log-likelihood $\ell(w, b)$.
(b) Show that maximizing $\ell(w, b)$ is equivalent to minimizing MSE.

**Q3. [Conceptual — 1 min]**

Fill in the blanks: MAP with a Gaussian prior on $w$ gives ___ regression. The regularization parameter $\lambda = $ ___ / ___. What does each quantity represent?

**Q4. [Conceptual — 1 min]**

State the bias-variance decomposition. Which term(s) can be reduced by:
(a) Adding more training data?
(b) Using a more complex model?
(c) Neither — it's irreducible?

**Q5. [Multiple choice — 1 min]**

In the medical testing example, a disease affects 1% of the population. A test is 99% sensitive and 95% specific. A positive result means:

(a) 99% chance of disease.
(b) About 16.7% chance of disease.
(c) 95% chance of disease.
(d) Cannot be determined without more information.

Explain in one sentence why.

**★ [Challenge — optional, 2 min]**

A prior on $w$ has the form $p(w) \propto \exp(-|w|/\tau)$ (Laplacian prior). Show that MAP with this prior gives lasso regression. What is $\lambda$ in terms of $\sigma^2$ and $\tau$? Why does the Laplacian cause sparsity?

---

---

## Solutions

### Q1. Solution

Likelihood: $\prod_i \theta^{x_i}(1-\theta)^{1-x_i}$. Log-likelihood: $\ell(\theta) = k\log\theta + (n-k)\log(1-\theta)$ where $k = 14$, $n = 20$.

Differentiate: $\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n-k}{1-\theta} = 0 \Rightarrow \hat{\theta} = k/n = 14/20 = 0.70$.

**Grading:** 0–3.
- 3: Correct answer + key derivation step.
- 2: Correct answer, minor derivation gap.
- 1: Correct answer only.
- 0: Wrong.

**Common mistakes:**
- Not showing the derivation step (just writing 0.7).
- Confusing likelihood with log-likelihood.

### Q2. Solution

(a) $\ell(w, b) = \text{const} - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2$

(b) The first term is constant. The second term is $-\frac{1}{2\sigma^2} \cdot n \cdot \text{MSE}(w,b)$. Since we maximize $\ell$ and the coefficient is negative, this is equivalent to minimizing MSE.

**Grading:** 0–3.
- 3: Both parts correct, showing the proportionality to MSE.
- 2: Both parts, minor gaps.
- 1: One part correct.
- 0: None.

**Common mistakes:**
- Forgetting to note that maximizing $\ell$ = minimizing MSE (sign flip).
- Missing the $n$ factor or the $2\sigma^2$ denominator.

### Q3. Solution

MAP with a Gaussian prior gives **ridge** regression. $\lambda = \sigma^2 / \tau^2$ where $\sigma^2$ is the noise variance and $\tau^2$ is the prior variance.

- $\sigma^2$ represents the noise in the data-generating process.
- $\tau^2$ represents how tightly we believe weights should be near 0.

**Grading:** 0–3.
- 3: Ridge + correct $\lambda$ + both quantities explained.
- 2: Ridge + correct $\lambda$.
- 1: Ridge only.
- 0: None.

### Q4. Solution

$\text{Expected error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible noise}$.

(a) Variance (more data → less variance).
(b) Bias² (more complex model → less bias).
(c) Irreducible noise ($\sigma^2$).

**Grading:** 0–3.
- 3: Decomposition + all three parts correct.
- 2: Decomposition + two parts.
- 1: Decomposition only or one part.
- 0: None.

**Common mistakes:**
- Saying more data reduces bias (it doesn't — only variance).
- Saying a more complex model reduces variance (it increases it).

### Q5. Solution

**Answer: (b).** $P(\text{disease}|\text{positive}) = \frac{0.99 \times 0.01}{0.99 \times 0.01 + 0.05 \times 0.99} \approx 16.7\%$.

The prior probability is very low (1%), so even with a good test, most positives are false positives. This is the class imbalance problem from Week 4.

**Grading:** 0–3.
- 3: Correct + explains prior dominates / class imbalance.
- 2: Correct, weak explanation.
- 1: Correct answer only.
- 0: Wrong.

### ★ Challenge Solution

$\log p(w) = -|w|/\tau + \text{const}$. MAP minimizes: $\text{MSE} + (\sigma^2/\tau)|w|$. So $\lambda = \sigma^2/\tau$.

The Laplacian has a sharp peak at 0 (non-differentiable). The L1 penalty has a "corner" at 0 that pushes solutions to exactly 0. Ridge's Gaussian prior is smooth at 0 — shrinks toward 0 but never reaches it.

**Grading:** Bonus.
- "Excellent": All three parts.
- "Good attempt": Two.
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | MLE for Bernoulli | | |
| Q2 | MLE = MSE proof | | |
| Q3 | MAP = Ridge | | |
| Q4 | Bias-variance decomposition | | |
| Q5 | Bayes' theorem / class imbalance | | |
| ★ | Laplacian prior → lasso | | |

---

## Post-Quiz Notes

- [ ] Can students derive MLE for Bernoulli? → Essential for Week 7 (logistic regression).
- [ ] Do they understand MLE = MSE? → This is the foundation for all loss functions.
- [ ] Can they state the bias-variance decomposition? → Essential for the rest of the course.
- [ ] Did anyone attempt the challenge? → Note for differentiation.

### Topics to spiral back:
- MLE for Bernoulli → Week 7 (MLE for logistic regression → cross-entropy)
- MLE = MSE → Week 7 (MLE for Bernoulli → cross-entropy loss)
- MAP = Ridge → Week 8 (matrix form, Bayesian linear regression)
- Bias-variance → Week 9 (k-NN), Week 18 (generalization theory)
