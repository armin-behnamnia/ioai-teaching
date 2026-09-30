# Week 7, Session 4 — End-of-Session Quiz

> **Time:** 6 minutes
> **Topics:** Sigmoid properties, logistic model, decision boundary, cross-entropy as negative log-likelihood
> **Format:** 4 questions
> **Closed notes**
> **Note:** The cross-entropy gradient derivation is NOT quizzed yet — it is Week 8 Session 1's opener.

---

## Questions

**Q1. [Calculation — 2 min]**

(a) Compute $\sigma(0)$, $\sigma(2)$ (leave in exact form), and $\sigma(-2)$.
(b) Prove that $\sigma'(z) = \sigma(z)(1 - \sigma(z))$.

**Q2. [Conceptual — 1 min]**

For the logistic model $P(y=1\mid x) = \sigma(2x - 4)$:

(a) What is the decision boundary (the $x$ where $P = 1/2$)?
(b) Is the model more confident at $x = 10$ or at $x = 3$? Why?

**Q3. [Multiple choice — 1 min]**

The cross-entropy loss for logistic regression is:

(a) An ad-hoc penalty chosen for convexity.
(b) The negative log-likelihood of the Bernoulli label model (i.e., MLE).
(c) The squared error between $\hat{p}$ and $y$.
(d) The KL divergence between $x$ and $y$.

Justify in one sentence.

**Q4. [Conceptual — 2 min]**

(a) A model predicts $\hat{p} = 0.001$ for an example whose true label is $y = 1$. What happens to that example's cross-entropy contribution?
(b) In one sentence: why can't we directly minimize accuracy (0-1 loss) with gradient descent?

---

## Solutions

### Q1. Solution

(a) $\sigma(0) = 1/2$; $\sigma(2) = 1/(1+e^{-2})$; $\sigma(-2) = 1/(1+e^{2}) = 1 - \sigma(2)$.

(b) $\sigma(z) = (1 + e^{-z})^{-1}$. Then

$$\sigma'(z) = -(1+e^{-z})^{-2} \cdot (-e^{-z}) = \frac{e^{-z}}{(1+e^{-z})^2} = \frac{1}{1+e^{-z}} \cdot \frac{e^{-z}}{1+e^{-z}} = \sigma(z)\big(1 - \sigma(z)\big) \;\blacksquare$$

**Grading:** 0–3.
- 3: Values + complete proof with both factored factors identified.
- 2: Values + proof with a gap.
- 1: Values only or partial proof.
- 0: None.

**Common mistakes:**
- Dropping the chain-rule minus sign in $\frac{d}{dz}(1+e^{-z})^{-1}$.
- Writing $\sigma'(z) = \sigma(z) - \sigma(z)^2$ is *correct* — accept both forms; watch for $\sigma(z)^2 - \sigma(z)$ (sign flip).

### Q2. Solution

(a) $P = 1/2 \iff 2x - 4 = 0 \iff x = 2$.
(b) $x = 10$: $z = 16$, $P \approx 1$ — far from the boundary on the positive side = confident. At $x = 3$: $z = 2$, $P = \sigma(2) \approx 0.88$ — closer to the boundary, less confident.

**Grading:** 0–3.
- 3: Boundary + confidence + distance-from-boundary reasoning.
- 2: Boundary + correct choice, weak reasoning.
- 1: One element.
- 0: None.

**Common mistakes:**
- Solving $\sigma(2x-4) = 1/2$ numerically instead of using $z = 0$.
- Confusing "confident" with "correct."

### Q3. Solution

**Answer: (b).** Cross-entropy $-\sum [y \log \hat p + (1-y)\log(1-\hat p)]$ is exactly $-\log p(\mathcal{D}\mid w,b)$ for i.i.d. Bernoulli labels with $\hat p_i = \sigma(wx_i+b)$; minimizing it = maximum likelihood. (It happens to also be convex — a bonus, not the reason.)

**Grading:** 0–3.
- 3: (b) + negative-log-likelihood/MLE justification.
- 2: (b) + weak justification.
- 1: (b) only.
- 0: Wrong.

**Common mistakes:**
- Choosing (a) — students conflate "convex" with "arbitrary but convenient."

### Q4. Solution

(a) The contribution $-\log(\hat p) = -\log(0.001) \approx 6.9$ — large; as $\hat p \to 0$ with $y=1$ it grows without bound. Confidently wrong is punished without mercy.
(b) Accuracy is piecewise constant in the parameters: small parameter changes leave almost all predictions unchanged, so the gradient is zero almost everywhere (undefined at flips) — no useful descent direction. We minimize a smooth surrogate (cross-entropy) instead.

**Grading:** 0–3.
- 3: Both parts complete (→ ∞ behavior + flat/staircase gradient).
- 2: Both parts, one weak.
- 1: One part.
- 0: None.

**Common mistakes:**
- Saying the loss "is 0.999" — confusing probability with $-\log$ of it.
- "Accuracy can't be computed" — it can; it just can't be *optimized by gradients*.

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score | Common Mistakes |
|----------|-------|-----------|-----------------|
| Q1 | Sigmoid + miracle derivative | | |
| Q2 | Decision boundary + confidence | | |
| Q3 | Cross-entropy = NLL | | |
| Q4 | Loss behavior + 0-1 loss pathology | | |

---

## Post-Quiz Notes

- [ ] Q1(b) is the gateway to next session — anyone who cannot reproduce $\sigma' = \sigma(1-\sigma)$ must re-derive it before Week 8 S1 (the cancellation depends on it).
- [ ] Topics to spiral: sigmoid → Week 8 S2 (softmax contains sigmoid as a special case); cross-entropy → Week 8 (gradient), Week 11 (entropy/KL), Week 15 (activations).
- [ ] Challenge 7-4B solvers: invite one to present the cancellation at the start of Week 8 S1.
