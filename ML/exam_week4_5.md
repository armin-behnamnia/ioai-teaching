# Exam: Weeks 4 & 5 (Selected Topics)

> **Course:** Machine Learning for IOAI Preparation  
> **Exam Duration:** 40 minutes  
> **Coverage:** Classification metrics, Train/Val/Test & evaluation procedure, MLE/MAP & Bayesian inference (intuition-focused)  
> **Format:** 3 long-answer multi-part questions + 5 short-answer questions  
> **Closed notes. Calculators permitted.**

---

## Part A: Long-Answer Questions (25 minutes)

### Question 1 [8 marks] — Evaluation Procedure Debugging

A student builds a polynomial regression model on a dataset of 1,000 examples. They use a 70/15/15 split (700 train / 150 validation / 150 test). They try 4 candidate degrees $d \in \{1, 3, 5, 8\}$, selecting the best by 5-fold CV on the training set. The student's pipeline is:

1. Compute mean and std on all 1,000 examples; normalize all features.
2. Split into 700/150/150.
3. Run 5-fold CV on the 700 training examples for each degree.
4. Pick the degree with lowest CV error ($d=5$).
5. Retrain on all 700 training examples with $d=5$.
6. Evaluate on the 150 test examples — get test MSE = 2.1.
7. Unhappy with 2.1, try $d \in \{1, 3, 5, 8\}$ on the test set. Best is $d=3$ with test MSE = 1.6. Report 1.6.

**(a)** [3 marks] Identify **two** bugs in this pipeline. For each, explain why it's wrong and what the consequence is.

**(b)** [3 marks] For the 5-fold CV in step 3: how many examples are in each training fold and validation fold? How many total model fits are performed across all candidate degrees? (Assume the bugs from part (a) are fixed.)

**(c)** [2 marks] After fixing the bugs, the student obtains CV error = 1.8 for the best degree. They want to report 1.8 as the final generalization estimate instead of using the test set. Explain why the CV error of 1.8 is not a reliable final estimate, even though CV was done correctly.

---

### Question 2 [8 marks] — Classification Metrics in Practice

A disease affects 1% of the population. A test has TPR = 95% and FPR = 10%. The test is applied to 10,000 people.

**(a)** [3 marks] Construct the confusion matrix and compute accuracy, precision, and recall. A colleague sees the accuracy and declares the test is excellent. Using a concrete number, explain why this conclusion is wrong.

**(b)** [2 marks] Compute the F1-score. A second colleague suggests reporting the arithmetic mean of precision and recall instead of F1. Using the numbers from this problem, explain why the arithmetic mean is misleading.

**(c)** [3 marks] The hospital wants to use this test for cancer screening. They can adjust the classification threshold. Should they lower or raise it? Explain the effect on precision and recall, and justify your recommendation in terms of the relative costs of false negatives vs. false positives.

---

### Question 3 [9 marks] — MLE, MAP, and the Bayesian View

**(a)** [3 marks] A coin is flipped 100 times, producing 60 heads. A frequentist estimates $P(\text{heads})$ using MLE. What value do they get, and what is the reasoning? Now suppose a Bayesian had a strong prior belief that the coin is fair ($P(\text{heads}) \approx 0.5$). Would their posterior estimate of $P(\text{heads})$ be above or below the frequentist's MLE? Explain why.

**(b)** [3 marks] Consider the linear regression model $y_i = wx_i + b + \epsilon_i$ where $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$. We place a Gaussian prior on the weight: $w \sim \mathcal{N}(0, \tau^2)$. It can be shown that the MAP estimate of $w$ is equivalent to ridge regression with $\lambda = \sigma^2/\tau^2$.

A practitioner sets $\tau^2 = 0.01$ and finds the model predicts $\bar{y}$ for every input. Diagnose the problem: what does $\tau^2 = 0.01$ imply about $\lambda$, and why does this cause the model to collapse? What should they do if they want the data to play a larger role?

**(c)** [3 marks] A Bayesian and a frequentist each observe the same dataset $\mathcal{D}$ and are asked to estimate a parameter $\theta$.

(i) In one sentence each: what does the frequentist treat as fixed and what does the Bayesian treat as random?

(ii) The Bayesian computes the full posterior $p(\theta \mid \mathcal{D})$ and wants to report the **expected value** of $\theta$ under this distribution (not the mode). Write the formula for this estimate. Contrast this with what the MAP estimate gives.

---

## Part B: Short-Answer Questions (15 minutes)

**S1.** [3 marks] A researcher tries 50 different models and picks the one with the lowest validation error (1.8%). She reports 1.8% as the model's generalization error. What is wrong with this? Name the phenomenon. How should she get an honest estimate instead?

---

**S2.** [3 marks] A team builds a classifier with AUC = 0.3 on a balanced dataset. They conclude the model is slightly below average and deploy it. What is wrong with their reasoning? What should they do instead?

---

**S3.** [3 marks] You have 800 training examples and use 5-fold CV to compare 3 models. How many total model fits will you perform? If each fit takes 2 minutes, how long does the full CV take?

---

**S4.** [3 marks] A model has training MSE = 0.5 and validation MSE = 6.2. The learning curve shows the gap is not closing as training data increases. Diagnose the problem. Would adding more data help? Would increasing or decreasing model complexity help?

---

**S5.** [3 marks] Two students debate regularization. Student A says: "A strong prior means we trust the data more." Student B says: "A strong prior means we trust our prior belief more, and $\lambda$ will be large." Which student is correct? Explain using the relationship $\lambda = \sigma^2/\tau^2$.

---
---

## Solutions

### Question 1 Solutions

**(a)** [3 marks]

**Bug 1 (step 1): Normalizing before splitting.** Computing mean/std on all 1,000 examples leaks test statistics into training. The training data indirectly "knows" about the test set, giving an over-optimistic estimate. **Fix:** Split first, compute mean/std on training data only, then apply to all sets.

**Bug 2 (step 7): Using the test set for model selection.** After evaluating on the test set (step 6), going back and trying different degrees on the test set violates the principle that the test set is used exactly once. By trying 4 degrees and picking the best, the student is doing model selection on the test set — it becomes a second validation set. The reported MSE of 1.6 is optimistically biased (the winner is partly lucky). **Fix:** Report 2.1 (the original test evaluation). All model selection must happen on training/validation only.

**Grading:** 1.5 marks per bug (0.5 for identifying, 0.5 for why it's wrong, 0.5 for consequence). Any two correct bugs accepted.

---

**(b)** [3 marks]

- Training set = 700. Each fold: $700/5 = 140$ in validation, $700 - 140 = 560$ in training.
- Total fits: 5 folds $\times$ 4 candidate degrees $= 20$ fits.

**Grading:** 1 mark for validation fold size (140), 1 mark for training fold size (560), 1 mark for total fits (20).

---

**(c)** [2 marks]

The CV error of 1.8 is optimistically biased because the model was **selected** based on the validation folds — the winner is partly the result of luck (fitting validation-specific noise). CV error estimates the performance of the *selection procedure*, not the final model. The test set, never used for any selection decision, provides an honest, unbiased estimate. That's why you can't skip it.

**Grading:** 1 mark for "CV error is optimistically biased because model was selected on validation folds," 1 mark for "test set is unbiased because never used for selection."

---

### Question 2 Solutions

**(a)** [3 marks]

10,000 people: 100 positive (1%), 9,900 negative.

- TPR = 95% → TP = 95, FN = 5.
- FPR = 10% → FP = 990, TN = 8,910.

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | 95 | 5 |
| **Actual Negative** | 990 | 8,910 |

- **Accuracy** $= (95 + 8{,}910) / 10{,}000 = 90.05\%$
- **Precision** $= 95 / (95 + 990) = 8.8\%$
- **Recall** $= 95 / 100 = 95.0\%$

**Why the colleague is wrong:** A trivial baseline that predicts "negative" for everyone achieves accuracy $= 9{,}900/10{,}000 = 99\%$ — **higher** than the test's 90%. The test is actually worse than doing nothing in terms of accuracy. The high-sounding 90% is misleading because accuracy is dominated by the majority class.

**Grading:** 1 mark for correct confusion matrix, 1 mark for accuracy/precision/recall, 1 mark for the baseline argument (99% > 90%).

---

**(b)** [2 marks]

$$F_1 = 2 \times \frac{0.088 \times 0.95}{0.088 + 0.95} = \frac{0.167}{1.038} = 16.1\%$$

Arithmetic mean $= (0.088 + 0.95)/2 = 51.9\%$.

The arithmetic mean (51.9%) makes the test look passable, but F1 (16.1%) correctly reveals it's terrible. The arithmetic mean doesn't punish the extreme imbalance: precision is only 8.8% — the test is wrong more than 9 out of 10 times when it says "positive." The harmonic mean is high only when **both** values are high.

**Grading:** 1 mark for F1 + arithmetic mean computation, 1 mark for explaining why arithmetic mean is misleading (doesn't punish imbalance).

---

**(c)** [3 marks]

**Lower the threshold.** The model predicts positive more often → recall increases (catches more true positives), precision decreases (more false positives).

**Justification:** For cancer screening, missing a positive case (false negative) is potentially fatal, while a false alarm (false positive) leads to extra tests but is not life-threatening. The cost of a false negative is much higher than a false positive, so we should prioritize recall — even at the cost of more false positives.

**Grading:** 1 mark for correct threshold effect (recall up, precision down), 1 mark for "lower the threshold," 1 mark for justification (FN cost >> FP cost).

---

### Question 3 Solutions

**(a)** [3 marks]

**Frequentist (MLE):** $\hat{\theta} = 60/100 = 0.60$. The MLE is the sample mean — the parameter value that makes the observed data most probable is the one matching the observed frequency.

**Bayesian:** The posterior estimate would be **below 0.60** (pulled toward 0.5). The prior belief that the coin is fair pulls the estimate toward 0.5. The posterior is a compromise between the prior (0.5) and the data (0.60), so the result is somewhere in between. The stronger the prior, the closer to 0.5.

**Grading:** 1 mark for MLE = 0.60 (sample mean), 1 mark for "below 0.60," 1 mark for explaining the prior pulls toward 0.5 (compromise between prior and data).

---

**(b)** [3 marks]

**Diagnosis:** $\tau^2 = 0.01$ is very small → $\lambda = \sigma^2/\tau^2$ is very large → extreme regularization. The prior is so strong that it dominates the data entirely. The weight $w$ is shrunk to approximately 0, so the model predicts $\bar{y}$ for every input (complete underfitting).

**What to do:** Increase $\tau^2$ (weaken the prior) so the data plays a larger role. As $\tau^2 \to \infty$, $\lambda \to 0$ and MAP reduces to MLE (OLS), letting the data dominate.

**Grading:** 1 mark for "large $\lambda$," 1 mark for "prior dominates data, $w \to 0$, predicts $\bar{y}$," 1 mark for "increase $\tau^2$."

---

**(c)** [3 marks]

**(i)**
- **Frequentist:** $\theta$ is a fixed but unknown constant. The data is random.
- **Bayesian:** $\theta$ is a random variable with a distribution (the posterior). The data updates the prior into the posterior.

**(ii)**
- **Posterior mean (expected value):** $\hat{\theta} = \mathbb{E}[\theta \mid \mathcal{D}] = \int \theta \, p(\theta \mid \mathcal{D}) \, d\theta$
- **MAP (mode):** $\hat{\theta}_{\text{MAP}} = \arg\max_\theta p(\theta \mid \mathcal{D})$

The posterior mean is the **average** of $\theta$ under the posterior distribution. The MAP is the **most likely** single value (the peak/mode). They can differ when the posterior is asymmetric.

**Grading:** (i) 1 mark for frequentist (fixed), 1 mark for Bayesian (random/distribution). (ii) 1 mark for the integral formula + contrast with MAP (mode vs. mean).

---

### Short-Answer Solutions

#### S1 Solution [3 marks]

**What's wrong:** With 50 models, some will look good on the validation set by chance. The winner's validation error (1.8%) is optimistically biased — it partly reflects luck rather than true generalization.

**Phenomenon:** Overfitting to the validation set (multiple comparisons problem).

**Honest estimate:** Use a test set that was never touched during model development or hyperparameter tuning. Evaluate the selected model on it exactly once.

**Grading:** 1 mark for "not reliable" + reason, 1 mark for phenomenon name, 1 mark for test set solution.

---

#### S2 Solution [3 marks]

**What's wrong:** AUC = 0.5 is random guessing. AUC = 0.3 is **worse** than random — the model systematically ranks negatives above positives. It's not "slightly below average"; it's anti-correlated with the truth.

**What to do:** Flip the predictions (invert the model's output). This gives AUC = $1 - 0.3 = 0.7$, which is actually a decent classifier.

**Grading:** 1 mark for "worse than random, not slightly below average," 1 mark for "model systematically ranks negatives above positives," 1 mark for "flip predictions."

---

#### S3 Solution [3 marks]

- Total model fits: 5 folds $\times$ 3 models $= 15$ fits.
- Time: $15 \times 2 = 30$ minutes.

**Grading:** 1 mark for 15 fits, 1 mark for 30 minutes, 1 mark for showing the computation.

---

#### S4 Solution [3 marks]

**Diagnosis:** Overfitting (high variance). Low training error + high validation error + large gap = the model fits training data (including noise) but doesn't generalize.

**More data?** Unlikely to help — the gap is not closing, meaning complexity is the issue, not data scarcity.

**Complexity?** **Decrease** model complexity (or increase regularization $\lambda$). The model has too much capacity — reducing it raises training error but lowers validation error, closing the gap.

**Grading:** 1 mark for diagnosis (overfitting), 1 mark for "more data won't help," 1 mark for "decrease complexity."

---

#### S5 Solution [3 marks]

**Student B is correct.** A strong prior means $\tau^2$ is small, so $\lambda = \sigma^2/\tau^2$ is large — heavy regularization. The prior dominates the data, pulling weights toward 0. We trust our prior belief more than the data.

Student A is wrong: a strong prior means we trust the data **less**, not more. When $\tau^2$ is large (weak prior), $\lambda \to 0$ and we trust the data more (MAP → MLE).

**Grading:** 1 mark for "Student B is correct," 1 mark for explaining $\tau^2$ small → $\lambda$ large, 1 mark for explaining Student A is wrong (strong prior = trust data less).

---
---

## Exam Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1(a) | Pipeline debugging (leakage + test set misuse) | | |
| Q1(b) | k-fold CV computation | | |
| Q1(c) | Why CV error is biased | | |
| Q2(a) | Confusion matrix, baseline argument | | |
| Q2(b) | F1 vs arithmetic mean | | |
| Q2(c) | Threshold tradeoff, metric priority | | |
| Q3(a) | MLE intuition, prior pulling estimate | | |
| Q3(b) | $\lambda = \sigma^2/\tau^2$, diagnosing collapse | | |
| Q3(c) | Frequentist vs Bayesian, posterior mean vs MAP | | |
| S1 | Overfitting to validation set | | |
| S2 | AUC interpretation, flipping predictions | | |
| S3 | k-fold CV computation | | |
| S4 | Learning curve diagnosis | | |
| S5 | Prior strength, $\lambda = \sigma^2/\tau^2$ | | |
