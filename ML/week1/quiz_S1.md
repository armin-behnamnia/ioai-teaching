# Week 1, Session 1 — End-of-Day Quiz

> **Time:** 8 minutes  
> **Topics:** ML problem setup, types of learning, notation  
> **Format:** 4 questions, mix of conceptual and multiple choice  
> **Closed notes**

---

## Questions

**Q1. [Conceptual — 2 min]**

Tom Mitchell defines learning as improvement on a task T with experience E, measured by performance P.

For a spam filter trained on 10,000 labeled emails, identify T, E, and P.

**Q2. [Multiple choice — 1 min]**

Which of the following is an example of **unsupervised learning**?

(a) Predicting house prices from features like area and number of bedrooms.  
(b) Grouping customers into segments based on their purchasing behavior, without knowing the segments in advance.  
(c) A robot learning to walk by receiving rewards for moving forward.  
(d) Classifying emails as spam or not spam using labeled training data.

Justify your answer in one sentence.

**Q3. [Conceptual — 2 min]**

In one sentence each, define:

(a) Hypothesis space  
(b) Loss function  
(c) Empirical risk

**Q4. [Multiple choice — 1 min]**

The goal of supervised learning is to find parameters $\theta^*$ that minimize:

(a) The loss on a single training example  
(b) The empirical risk (average loss on training data)  
(c) The true risk (expected loss over all possible data)  
(d) The number of parameters in the model

Justify your answer in one sentence.

**★ [Challenge — optional, 2 min]**

We want to minimize the true risk $R(\theta)$, but we minimize the empirical risk $R_{\text{emp}}(\theta)$ instead. Give one reason why these two might differ significantly, and one scenario where they would be approximately equal.

---
---

## Solutions

### Q1. Solution

| Symbol | Answer |
|--------|--------|
| **T** (Task) | Classify emails as spam or not spam |
| **E** (Experience) | The 10,000 labeled emails (training data) |
| **P** (Performance) | Accuracy (percentage of emails correctly classified) |

**Grading:** 0–3 scale.  
- 3: All three correct.  
- 2: Two correct.  
- 1: One correct.  
- 0: None correct or no answer.

### Q2. Solution

**Answer: (b)** Grouping customers into segments based on purchasing behavior without knowing the segments in advance.

**Justification:** Unsupervised learning means no labels ($y$) are given — the algorithm finds structure in the input data alone. Customer segmentation has no pre-defined groups (no $y$), so the algorithm must discover them.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification.  
- 2: Correct answer, weak/missing justification.  
- 1: Wrong answer but reasonable justification.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (d): Students may think "spam detection" is unsupervised because it's automated. It's supervised because the training emails are labeled.
- Choosing (c): Reinforcement learning is a separate category. It uses rewards, not labels, but it's not "unsupervised" in the standard sense.

### Q3. Solution

**(a) Hypothesis space:** The set of all possible models (functions) that the learning algorithm can choose from. (e.g., "all linear functions" or "all neural networks with 2 layers.")

**(b) Loss function:** A function $L(\hat{y}, y)$ that measures how wrong a prediction $\hat{y}$ is compared to the true value $y$. (e.g., squared error $(\hat{y} - y)^2$.)

**(c) Empirical risk:** The average loss of a model on the training data: $R_{\text{emp}}(\theta) = \frac{1}{n}\sum_{i=1}^n L(f_\theta(\mathbf{x}_i), y_i)$.

**Grading:** 0–3 scale (one point per definition).  
- 3: All three correct and clearly stated.  
- 2: Two correct.  
- 1: One correct.  
- 0: None correct.

**Acceptable variations:**
- Hypothesis space: "the family of functions the model can represent" ✓
- Loss function: "a measure of prediction error" ✓ (but "a measure of how good the model is" is too vague — it measures error, not goodness)
- Empirical risk: "the average training loss" ✓ / "the total loss on the training set divided by n" ✓

### Q4. Solution

**Answer: (b)** The empirical risk (average loss on training data).

**Justification:** We cannot compute the true risk because we don't know the true data distribution. We approximate it with the empirical risk computed on our finite training sample. This is the Empirical Risk Minimization (ERM) principle.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning that the true risk is unknown/uncomputable.  
- 2: Correct answer, partial justification.  
- 1: Wrong answer, but some correct reasoning.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (c): Conceptually, we *want* to minimize the true risk, but we *can't* because we don't know the true distribution. The correct answer is (b) because that's what we actually do in practice. If a student chooses (c) with the justification "that's what we actually want," give 2 points — they understand the goal but not the practical constraint.

### ★ Challenge Solution

**Why they might differ:**
- The training data may not be representative of the true distribution (sampling bias). The model might fit the training data perfectly but generalize poorly.
- The model might overfit: it memorizes training examples including noise, which doesn't help on new data.
- The hypothesis space might be too large, allowing low empirical risk but high true risk.

**When they would be approximately equal:**
- When the training data is large and representative (i.i.d. samples from the true distribution), and the hypothesis space is not too complex relative to the data size. In this case, by the law of large numbers, the empirical average converges to the expectation.
- Formally (preview): when $n$ is large and the model complexity is controlled, the generalization gap $|R(\theta) - R_{\text{emp}}(\theta)|$ is small.

**Grading:** Bonus — not counted toward the base score. Mark as "attempted" / "good attempt" / "excellent" for tracking purposes.

---
---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Mitchell's T/E/P | | |
| Q2 | Supervised vs. unsupervised | | |
| Q3 | Hypothesis space / loss / empirical risk | | |
| Q4 | ERM principle | | |
| ★ | Generalization gap | | |
