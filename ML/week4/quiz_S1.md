# Week 4, Session 1 — End-of-Session Quiz

> **Time:** 8 minutes  
> **Topics:** Train/val/test split, golden rule, k-fold cross-validation, data leakage  
> **Format:** 5 questions, mix of conceptual, multiple choice, and calculation  
> **Closed notes**

---

## Questions

**Q1. [Conceptual — 2 min]**

A student trains a model on their training data and reports: "My model gets 5% error on the training data, so it's a good model."

(a) What is wrong with this reasoning?  
(b) What should the student do instead to properly evaluate their model?

**Q2. [Multiple choice — 1 min]**

Which of the following is the correct use of the **test set**?

(a) Using it to choose the best polynomial degree.  
(b) Using it to tune the regularization parameter $\lambda$.  
(c) Using it exactly once, at the very end, to estimate generalization performance.  
(d) Using it to check if the model is overfitting during training.

Justify your answer in one sentence.

**Q3. [Calculation — 2 min]**

You have 500 examples. You use 5-fold cross-validation.

(a) How many examples are in each validation fold?  
(b) How many examples are in each training fold?  
(c) How many total model fits will you perform?  
(d) How many times is each example used for validation?

**Q4. [Conceptual — 2 min]**

What is data leakage? Give one concrete example of how it can happen, and state the rule for preventing it.

**Q5. [Multiple choice — 1 min]**

Which of the following is an example of **data leakage**?

(a) Shuffling the data before splitting into train and test.  
(b) Computing the mean and standard deviation of ALL data (including test) for normalization, then splitting.  
(c) Using k-fold cross-validation instead of a single train/test split.  
(d) Setting aside 20% of the data as a test set before any preprocessing.

Justify your answer in one sentence.

**★ [Challenge — optional, 2 min]**

In k-fold cross-validation, what happens when $k = n$ (where $n$ is the number of examples)? This is called Leave-One-Out Cross-Validation (LOOCV).

(a) How many model fits are required?  
(b) What is one advantage of LOOCV over 5-fold CV?  
(c) What is one disadvantage?  
(d) When would you choose LOOCV over 5-fold CV?

---

---

## Solutions

### Q1. Solution

**(a)** Training error is an optimistically biased estimate of performance. The model has seen the training data during fitting, so it can achieve low error by memorizing the data (overfitting) rather than learning generalizable patterns. A low training error does NOT imply the model will perform well on new, unseen data.

**(b)** The student should:
- Split the data into training, validation, and test sets.
- Train on the training set.
- Tune hyperparameters (if any) using the validation set.
- Evaluate the final model ONCE on the test set to get an honest estimate of generalization performance.

**Grading:** 0–3 scale.  
- 3: (a) Correctly identifies that training error is biased/optimistic and explains why (model has seen the data). (b) Mentions using a separate test/validation set for evaluation.  
- 2: One part correct, other part partial.  
- 1: One part correct.  
- 0: Neither part correct.

**Common mistakes to watch for:**
- Saying "the model might be overfitting" without explaining that training error is biased because the model has seen the data. (Give partial credit — the intuition is right, but the explanation is incomplete.)
- Suggesting "use cross-validation" for part (b) without mentioning a test set. (Cross-validation is correct for model selection, but the test set is needed for final evaluation. Give full credit if they mention either validation or test sets — the key idea is "evaluate on data the model hasn't seen.")

### Q2. Solution

**Answer: (c)** Using it exactly once, at the very end, to estimate generalization performance.

**Justification:** The test set is the "locked box." Its sole purpose is to provide an honest, unbiased estimate of how well the model will perform on truly unseen data. If you use it for model selection or tuning, it becomes a second validation set, and the estimate becomes optimistically biased.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification mentioning that the test set should be used only once / for final evaluation.  
- 2: Correct answer, weak justification.  
- 1: Wrong answer but reasonable justification.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a) or (b): Students who confuse validation and test sets. The validation set is for tuning; the test set is for final evaluation. Re-emphasize this distinction next session.
- Choosing (d): Checking for overfitting during training is done with the validation set, not the test set.

### Q3. Solution

**(a)** Each validation fold has $500 / 5 = 100$ examples.

**(b)** Each training fold has $500 - 100 = 400$ examples.

**(c)** Total model fits = 5 (one per fold).

**(d)** Each example is used for validation exactly once (and for training $k - 1 = 4$ times).

**Grading:** 0–3 scale.  
- 3: All four parts correct.  
- 2: Three parts correct.  
- 1: One or two parts correct.  
- 0: No parts correct.

**Common mistakes to watch for:**
- Saying 500 total model fits (confusing 5-fold with LOOCV where $k = n = 500$).
- Saying each example is used for validation 5 times (it's once — each example is in exactly one validation fold).
- Saying 250 training (confusing with a 50/50 split instead of 5-fold).

### Q4. Solution

**Data leakage** occurs when information from the validation or test set "leaks" into the training process, causing the model's evaluation to be optimistically biased.

**Example (any one of the following is acceptable):**
- Normalizing/preprocessing all data before splitting, so training data statistics include test data.
- Having duplicate examples in both training and test sets (e.g., the same patient appearing in both).
- Feature selection using all data before splitting.
- Temporal leakage: training on future data and testing on past data.

**Prevention rule:** Always split the data FIRST. Do ALL preprocessing (normalization, feature selection, imputation) using ONLY training data. Apply the same transformations to validation/test data.

**Grading:** 0–3 scale.  
- 3: Correct definition + valid example + correct prevention rule.  
- 2: Two of three correct (e.g., definition + example but no prevention rule).  
- 1: One of three correct.  
- 0: Nothing correct.

**Acceptable variations:**
- Definition: "when test data influences training" ✓ / "when the model sees test data indirectly" ✓
- Example: any of the four types from the handout ✓
- Prevention: "split first, then preprocess" ✓ / "fit preprocessing on training data only" ✓

**Common mistakes to watch for:**
- Confusing data leakage with overfitting. Overfitting is fitting noise in the training data; data leakage is information from test/validation reaching training. They're related but different.
- Not mentioning the prevention rule. The rule ("split first") is the practical takeaway — make sure students know it.

### Q5. Solution

**Answer: (b)** Computing the mean and standard deviation of ALL data (including test) for normalization, then splitting.

**Justification:** The normalization statistics (mean, std) are computed using the test data. When the model is trained on the normalized training data, those statistics "contain" information about the test set. The training data has "seen" the test data through the shared statistics. This is data leakage.

**Grading:** 0–3 scale.  
- 3: Correct answer + correct justification explaining that test data statistics leak into training.  
- 2: Correct answer, weak justification.  
- 1: Wrong answer but reasonable justification.  
- 0: Wrong answer, no justification.

**Common mistakes to watch for:**
- Choosing (a): Shuffling before splitting is GOOD practice — it ensures the splits are random. It's not leakage.
- Choosing (c): Cross-validation is a validation technique, not leakage. (Though CV can leak if preprocessing is done wrong — but the technique itself is fine.)
- Choosing (d): Setting aside the test set before preprocessing is the CORRECT approach — it prevents leakage.

### ★ Challenge Solution

**(a)** $k = n$ means each fold is a single example. So $n$ model fits are required. For 500 examples, that's 500 model fits.

**(b)** Advantage: LOOCV trains on $n - 1$ examples (almost all the data), so the bias of the error estimate is very low. Each model sees nearly the full dataset, so the estimate reflects the model's performance when trained on (almost) all data.

**(c)** Disadvantage: High variance — the $n$ training sets are almost identical (they differ by only one example), so the $n$ validation errors are highly correlated. Averaging correlated values doesn't reduce variance much. Also, $n$ model fits is computationally expensive for large $n$.

**(d)** Choose LOOCV when the dataset is very small ($n < 50$ approximately), where every data point matters and you can't afford to hold out 20% for validation. For larger datasets, 5-fold or 10-fold CV is preferred — it's faster and has lower variance.

**Grading:** Bonus — not counted toward the base score.  
- "Excellent": All four parts correct with clear explanations.  
- "Good attempt": 2–3 parts correct or correct intuition without full explanation.  
- "Attempted": Tried but mostly incorrect.

---

---

## Quiz Statistics Tracking

| Question | Topic | Avg Score (fill in) | Common Mistakes (fill in) |
|----------|-------|---------------------|---------------------------|
| Q1 | Training error ≠ test error | | |
| Q2 | Role of the test set | | |
| Q3 | k-fold CV fold sizes | | |
| Q4 | Data leakage definition + prevention | | |
| Q5 | Identifying data leakage | | |
| ★ | LOOCV tradeoffs | | |

---

## Post-Quiz Notes for Instructor

### After grading, check:

- [ ] Did students confuse the validation set with the test set? → Re-emphasize at the start of Session 2.
- [ ] Can students compute fold sizes correctly? → If not, practice with different $k$ and $n$ values.
- [ ] Do students understand the prevention rule for data leakage ("split first")? → If not, present a worked example at the start of Session 2.
- [ ] Did any students attempt the challenge? How did they do? → Note for differentiation.

### Topics to spiral back in future quizzes:

- Train/val/test roles → spiral back in Week 5 (probability) when discussing MLE vs. MAP
- k-fold CV → spiral back in Week 8 (matrix LR, choosing degree/λ via CV) and Week 9 (k-NN, choosing k via CV)
- Data leakage → spiral back in Week 7 (logistic regression, preprocessing pipeline)
- LOOCV → spiral back in Week 8 (closed-form LOOCV for linear regression)
