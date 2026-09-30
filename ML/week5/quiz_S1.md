# Week 5, Session 1 — End-of-Session Quiz

> **Time:** 8 minutes  
> **Topics:** Bayes' theorem for ML, MLE principle, MLE for Bernoulli/Gaussian, MLE = MSE  
> **Format:** 5 questions, mix of conceptual, calculation, and derivation  
> **Closed notes**

---

## Questions

**Q1. [Conceptual — 2 min]**

A disease affects 2% of the population. A test is 95% sensitive (TPR) and 90% specific (TNR). If a randomly selected person tests positive, what is the probability they have the disease?

**Q2. [Conceptual — 1 min]**

In the Bayesian view of ML, what is the "prior"? What is the "posterior"? How does the prior interact with data to produce the posterior? Answer in 2–3 sentences.

**Q3. [Multiple choice — 1 min]**

The evidence $p(\mathcal{D})$ in Bayes' theorem is often dropped in MLE and MAP. Why?

(a) It's always zero.  
(b) It doesn't depend on $\theta$, so it doesn't affect the optimization.  
(c) It's too small to matter.  
(d) It cancels with the prior.

Justify your answer in one sentence.

**Q4. [Derivation — 3 min]**

Derive the MLE for the Bernoulli distribution. You observe $x_1, \ldots, x_n \in \{0, 1\}$, i.i.d. Bernoulli($\theta$).

Show: (a) write the likelihood, (b) take the log, (c) differentiate and set to zero, (d) solve for $\hat{\theta}$.

**Q5. [Conceptual — 1 min]**

Fill in the blanks: "Minimizing MSE is equivalent to ___ under the assumption that the noise follows a ___ distribution." State the key step in the proof.

**★ [Challenge — optional, 2 min]**

In the medical testing example from Q1, suppose the disease prevalence increases from 2% to 20%. Does $P(\text{disease}|\text{positive})$ increase or decrease? By how much (approximately)? Explain why the prior matters so much when the disease is rare.

---

---

## Solutions

### Q1. Solution

$$P(\text{disease}|\text{positive}) = \frac{P(\text{positive}|\text{disease})\,P(\text{disease})}{P(\text{positive})}$$

$$P(\text{positive}) = 0.95 \times 0.02 + 0.10 \times 0.98 = 0.019 + 0.098 = 0.117$$

$$P(\text{disease}|\text{positive}) = \frac{0.019}{0.117} \approx 16.2\%$$

**Grading:** 0–3 scale.  
- 3: Correctly applies Bayes, computes evidence, arrives at ≈ 16.2%.  
- 2: Sets up correctly but arithmetic error, or forgets evidence.  
- 1: Right formula, wrong computation.  
- 0: No correct work.

**Common mistakes:**
- Not computing the evidence (using only the numerator 0.019).
- Confusing sensitivity with specificity. $P(\text{positive}|\text{no disease}) = 1 - 0.90 = 0.10$.
- Reporting 95% — confusing $P(\text{positive}|\text{disease})$ with $P(\text{disease}|\text{positive})$ (prosecutor's fallacy).

### Q2. Solution

The **prior** $p(\theta)$ is our belief about the parameter before seeing data. The **posterior** $p(\theta|\mathcal{D})$ is our updated belief after observing data $\mathcal{D}$. The prior combines with the likelihood $p(\mathcal{D}|\theta)$ via Bayes' theorem to produce the posterior.

**Grading:** 0–3 scale.  
- 3: Correctly defines both and explains the interaction.  
- 2: Defines one correctly.  
- 1: Vague.  
- 0: No correct answer.

### Q3. Solution

**Answer: (b)** It doesn't depend on $\theta$, so it doesn't affect the optimization.

**Justification:** MLE maximizes $p(\mathcal{D}|\theta)$ and MAP maximizes $p(\mathcal{D}|\theta)p(\theta)$. The evidence $p(\mathcal{D}) = \int p(\mathcal{D}|\theta)p(\theta)d\theta$ is a constant w.r.t. $\theta$, so it doesn't change the argmax.

**Grading:** 0–3 scale.  
- 3: Correct answer + justification.  
- 2: Correct answer, weak justification.  
- 1: Wrong answer but reasonable.  
- 0: Wrong, no justification.

### Q4. Solution

**(a)** $p(\mathcal{D}|\theta) = \prod_i \theta^{x_i}(1-\theta)^{1-x_i}$

**(b)** $\ell(\theta) = k\log\theta + (n-k)\log(1-\theta)$, where $k = \sum_i x_i$.

**(c)** $\frac{d\ell}{d\theta} = \frac{k}{\theta} - \frac{n-k}{1-\theta} = 0$

**(d)** $k(1-\theta) = (n-k)\theta \Rightarrow k = n\theta \Rightarrow \hat{\theta} = k/n = \frac{1}{n}\sum_i x_i$

**Grading:** 0–3 scale.  
- 3: All four steps correct.  
- 2: Three steps, or minor algebra errors.  
- 1: One or two steps.  
- 0: No correct work.

**Common mistakes:**
- Not taking the log.
- Chain rule error on $\log(1-\theta)$: derivative is $\frac{-1}{1-\theta}$.

### Q5. Solution

"Minimizing MSE is equivalent to **maximum likelihood estimation (MLE)** under the assumption that the noise follows a **Gaussian** distribution."

**Key step:** The Gaussian log-likelihood contains the term $-\frac{1}{2\sigma^2}\sum_i (y_i - \hat{y}_i)^2$, which is proportional to MSE. Maximizing the log-likelihood = minimizing MSE.

**Grading:** 0–3 scale.  
- 3: Both blanks correct AND explains the key step.  
- 2: Both blanks, weak explanation.  
- 1: One blank.  
- 0: Neither.

### ★ Challenge Solution

With 20% prevalence: $P(\text{positive}) = 0.95 \times 0.20 + 0.10 \times 0.80 = 0.19 + 0.08 = 0.27$. $P(\text{disease}|\text{positive}) = 0.19/0.27 \approx 70.4\%$.

Increases from 16.2% to 70.4%. When the disease is rare, false positives dominate. The prior controls how much weight the likelihood carries.

**Grading:** Bonus.  
- "Excellent": Correct direction, computation (~70%), and explanation.  
- "Good attempt": Correct direction and explanation, no computation.  
- "Attempted": Tried.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | Bayes' theorem application | | |
| Q2 | Prior/posterior | | |
| Q3 | Dropping the evidence | | |
| Q4 | MLE for Bernoulli | | |
| Q5 | MLE = MSE | | |
| ★ | Effect of prior | | |

---

## Post-Quiz Notes

- [ ] Can students apply Bayes (compute evidence)? → If not, practice at start of Session 2.
- [ ] Can students derive MLE for Bernoulli? → If not, practice with Gaussian MLE.
- [ ] Do students understand MLE=MSE? → This is THE key result. Re-derive if needed.

### Topics to spiral back:

- Bayes' theorem → Week 7 (logistic regression: posterior, sigmoid)
- MLE = MSE → Week 8 (matrix MLE)
- Prior/posterior → Week 7 (MAP for logistic), Week 8 (Bayesian LR)
