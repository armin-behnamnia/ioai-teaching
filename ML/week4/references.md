# Week 4 — References for Further Reading

> **Purpose:** Curated references for students who want to go deeper. These are optional — all required material is in the handout. References are organized by topic and tagged with difficulty.

---

## 1. Train / Test Split and Model Evaluation

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2, "Assessing Model Accuracy" and Section 5.1, "Cross-Validation" | The best accessible introduction to model evaluation. Starts with the train/test split, explains why training error is misleading, and introduces the validation set approach. Free PDF. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 5, "Generalization" | Very friendly explanation of why training error ≠ test error and how to split data. Free: ciml.info | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Chapter 3, "Foundations of Learning Algorithms" | Concise overview of train/validation/test split and the role of each. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.3, "Model Selection" | How to use validation data for model selection. Connects to the bias-variance tradeoff. | ★★ |
| **ESL** — Hastie et al. | Section 7.2, "Bias, Variance, and Model Complexity" | Statistical perspective on why we need separate evaluation. Discusses the "optimism" of training error. Free PDF. | ★★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Chapter 2, "A Formal Learning Model" and Chapter 4, "Learning via Uniform Convergence" | Rigorous treatment of generalization and the relationship between training and true error. Free. | ★★★ |

---

## 2. Cross-Validation

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 5.1, "Cross-Validation" (entire section) | **The best starting point.** Walks through LOOCV and k-fold CV with a concrete example (auto mpg data). Figures 5.2–5.6 are excellent. Free PDF. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 5, "Generalization" (cross-validation section) | Friendly explanation of k-fold CV and why it works. Free. | ★ |
| **Neural Networks and Deep Learning** — Nielsen | Chapter 3, "Overfitting and Regularization" (the section on hold-out data) | Intuitive explanation in the context of neural networks. Free online. | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 7.10, "Cross-Validation" | Detailed statistical treatment of CV, including bias and variance of the CV estimate. Discusses when CV fails. Free. | ★★★ |
| **PRML** — Bishop | Section 1.3, "Model Selection" | CV as a model selection tool. Connects to the Bayesian approach (marginal likelihood). | ★★ |
| **MML** — Deisenroth et al. | Section 8.5, "Cross-Validation to Assess Generalization Performance" | Clean mathematical treatment of k-fold CV with pseudocode. Free. | ★★ |

---

## 3. Leave-One-Out Cross-Validation (LOOCV)

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 5.1.3, "Leave-One-Out Cross-Validation" | Excellent accessible explanation with the auto data example. Discusses the bias-variance tradeoff between LOOCV and k-fold. Free. | ★ |
| **ESL** — Hastie et al. | Section 7.10.1, "Leave-One-Out Cross-Validation" | Statistical analysis of LOOCV bias and variance. Shows the closed-form shortcut for linear regression (the hat matrix formula). Free. | ★★★ |
| **PRML** — Bishop | Section 1.3 (mentions LOOCV) | Brief mention in the context of model selection. | ★★ |

---

## 4. Classification Metrics (Confusion Matrix, Accuracy, Precision, Recall, F1)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 4.4.3, "Classification Error Rate" and Section 4.4.4, "An Alternative to Classification Error Rate" | Introduces the confusion matrix and discusses why accuracy can be misleading. Uses the default dataset. Free. | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Chapter 5, "Classification" | Concise definitions of precision, recall, F1 with examples. | ★ |
| **Dive into Deep Learning (D2L)** — Zhang et al. | Section 3.4, "Softmax Regression from Scratch" (the section on classification metrics) | Practical introduction to classification metrics. Free: d2l.ai | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.5.4, "Loss Functions for Classification" | Theoretical framework for classification metrics. Shows how different metrics arise from different loss functions. | ★★ |
| **ESL** — Hastie et al. | Section 2.4, "Linear Regression of an Indicator Matrix" and Section 9.3, "Linear Discriminant Analysis" | Discusses classification metrics in the context of specific classifiers. Free. | ★★★ |
| **Evaluation of Machine Learning Models** — Kohavi (1995) | Entire paper | Classic paper on cross-validation and evaluation methodology. Introduces concepts like stratified sampling. | ★★★ |

---

## 5. ROC Curves and AUC

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 4.4.3, "The ROC Curve" (within Section 4.4) | Accessible introduction to ROC and AUC. Figure 4.7 is excellent — shows ROC curves for two classifiers. Free. | ★ |
| **D2L** — Zhang et al. | Section 3.6, "Generalization" (ROC discussion within classification evaluation) | Practical ROC construction and AUC interpretation. Free. | ★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Section 3.4, "Summary" (mentions AUC in the context of learnability) | Brief theoretical mention. | ★★★ |

### Foundational Papers

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"The Relationship Between Precision-Recall and ROC Curves"** — Davis & Goadrich (2006) | Sections 1–2, Figure 1 | **This week's suggested paper.** Shows when PR curves are more informative than ROC. The key theorem: a curve dominates in ROC space iff it dominates in PR space. | ★★★ |
| **"An Introduction to ROC Analysis"** — Fawcett (2006) | Sections 1–4 | Excellent tutorial on ROC curves. Covers construction, interpretation, and AUC. Very accessible for a research paper. Free. | ★★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 9.2.5, "The ROC Curve" | Statistical treatment of ROC and AUC. Connects to the class-conditional distributions. Free. | ★★★ |
| **PRML** — Bishop | Section 1.5.4, "Loss Functions for Classification" (discusses rejection thresholds and ROC) | Theoretical framework connecting ROC to decision theory. | ★★ |

---

## 6. Precision-Recall Curves

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"The Relationship Between Precision-Recall and ROC Curves"** — Davis & Goadrich (2006) | Section 2, "Relationship Between ROC Space and PR Space" | **The definitive reference.** Proves the equivalence of dominance in ROC and PR space, and explains why PR is better for imbalanced data. | ★★★ |
| **"An Introduction to ROC Analysis"** — Fawcett (2006) | Section 5, "PR Curves" | Comparison of ROC and PR curves. Accessible. Free. | ★★ |
| **ESL** — Hastie et al. | Section 9.2.5 (mentions precision-recall in the context of class imbalance) | Brief discussion of PR curves in the statistical learning framework. Free. | ★★★ |
| **Information Retrieval** — Manning, Raghavan, Schütze | Chapter 8, "Evaluation in Information Retrieval" | The IR perspective on precision, recall, and F1. The standard reference for these metrics in the search/retrieval context. | ★★ |

---

## 7. Regression Metrics (MSE, RMSE, MAE, R²)

### Accessible

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 3.1.3, "Assessing the Accuracy of the Coefficients" and Section 3.2.2, "Measuring the Quality of Fit" | R² and RSE (residual standard error) explained accessibly. The best starting point for regression metrics. Free. | ★ |
| **A Course in Machine Learning** — Daumé | Chapter 2, "Linear Regression" (loss function section) | MSE and MAE compared. Free. | ★ |

### More Rigorous

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **PRML** — Bishop | Section 1.3.5, "Loss Functions for Regression" | Theoretical framework. Shows MSE arises from Gaussian noise (preview of Week 5). | ★★ |
| **ESL** — Hastie et al. | Section 3.2, "Linear Regression Models and Least Squares" | Statistical properties of MSE/RMSE. Discusses bias and variance of the coefficients. Free. | ★★★ |
| **MML** — Deisenroth et al. | Section 9.2, "Maximum Likelihood Estimation" | Derives MSE from the Gaussian likelihood. Good preparation for Week 5. Free. | ★★ |

---

## 8. Model Selection and Hyperparameter Tuning

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 5.1, "Cross-Validation" (model selection subsection) and Section 6.1, "Subset Selection" | How to use CV for model selection. The one-standard-error rule (Section 6.1.3) is a practical gem. Free. | ★ |
| **ESL** — Hastie et al. | Section 7.10.2, "k-Fold Cross-Validation" and Section 7.10.3, "Cross-Validation for Model Selection" | Statistical analysis of CV for model selection. Discusses the "one-standard-error rule." Free. | ★★★ |
| **PRML** — Bishop | Section 1.3, "Model Selection" | CV, penalized criteria (AIC, BIC), and Bayesian model selection. | ★★ |
| **Understanding Machine Learning** — Shalev-Shwartz & Ben-David | Chapter 11, "Model Selection" | Formal treatment of model selection and the structural risk minimization principle. Free. | ★★★ |

---

## 9. Data Leakage

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **"Leakage in Data Mining: Formulation, Detection, and Avoidance"** — Kaufman et al. (2012) | Sections 1–3 | The definitive paper on data leakage. Defines leakage types and prevention strategies. Accessible for a research paper. | ★★★ |
| **"A Few Useful Things to Know about Machine Learning"** — Domingos (2012) | Section 2, "It's Generalization That Counts" | Mentions leakage informally: "the most common mistake is to test on the training data." (This was the Week 2 suggested paper.) | ★ |
| **The Hundred-Page Machine Learning Book** — Burkov | Chapter 3, "Data Preparation" (leakage discussion) | Practical examples of data leakage and how to avoid it. | ★ |
| **D2L** — Zhang et al. | Section 5.8, "Environment and Distribution Shift" | Discusses distribution shift and data leakage in the context of model deployment. Free. | ★★ |

---

## 10. Learning Curves

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ISLR** — James et al. | Section 2.2.2, "The Bias-Variance Trade-Off" (implicitly discusses learning curves) | The bias-variance tradeoff that learning curves visualize. Figure 2.9–2.12 are excellent illustrations. Free. | ★ |
| **PRML** — Bishop | Figure 1.5 and surrounding text | Shows learning curves for polynomial regression. The canonical illustration. | ★★ |
| **ESL** — Hastie et al. | Section 7.3, "The Bias-Variance Decomposition" | The mathematical foundation for what learning curves display. Free. | ★★★ |
| **D2L** — Zhang et al. | Section 5.7, "Underfitting and Overfitting" | Practical learning curves in the context of neural networks. Free. | ★★ |
| **"Learning Curves for Confident Predictions"** — Cortes et al. (1994) | Sections 1–3 | Theoretical analysis of learning curves. Shows power-law behavior. Advanced but interesting. | ★★★ |

---

## 11. Overfitting to the Validation Set

| Reference | Section | What You'll Learn | Difficulty |
|-----------|---------|-------------------|------------|
| **ESL** — Hastie et al. | Section 7.10.2, "k-Fold Cross-Validation" (discussion of selection bias) | Discusses how selecting the best model from many candidates introduces optimistic bias. Free. | ★★★ |
| **"On Over-fitting in Model Selection and Subsequent Selection Bias in Performance Evaluation"** — Cawley & Talbot (2010) | Sections 1–3 | Rigorous treatment of overfitting to the validation set. Shows it's a form of multiple comparisons. | ★★★ |
| **"A Few Useful Things to Know about Machine Learning"** — Domingos (2012) | Section 5, "Overfitting Has Many Faces" (the "multiple comparisons" subsection) | Accessible discussion of overfitting via multiple comparisons. | ★ |

---

## Quick-Reference: Best Starting Points by Student Level

### For Students Who Want the Big Picture (Accessible)

1. **ISLR**, Section 5.1 — "Cross-Validation" ★ — Best overall introduction to CV and model evaluation
2. **ISLR**, Section 4.4 — "Classification" ★ — Confusion matrix, precision, recall, ROC
3. **A Course in Machine Learning**, Chapter 5 ★ — Generalization and overfitting, free
4. **Fawcett (2006)**, Sections 1–4 ★★ — Best ROC tutorial paper, free

### For Students Who Want Mathematical Rigor

1. **ESL**, Section 7.10 — "Cross-Validation" ★★★ — Statistical theory of CV
2. **PRML**, Section 1.3 — "Model Selection" ★★ — Bayesian perspective
3. **Understanding ML**, Chapters 2–4 ★★★ — Formal learning theory, generalization bounds

### For Students Who Want to Go Very Deep

1. **Davis & Goadrich (2006)** — This week's suggested paper ★★★ — ROC vs PR theory
2. **Kaufman et al. (2012)** — Data leakage ★★★ — The definitive treatment
3. **Cawley & Talbot (2010)** — Overfitting to the validation set ★★★ — Rigorous analysis
4. **ESL**, Sections 7.2–7.3 ★★★ — Bias-variance decomposition and model complexity

---

## How to Use These References

1. **Don't read everything.** Pick one reference that matches your level and read the indicated section.
2. **Read with the handout open.** The handout is your primary material. References fill gaps or go deeper.
3. **Focus on examples and figures** on first reading. Come back to proofs later.
4. **If a reference uses notation you don't understand**, check the notation table in the handout. If it's different from our notation, translate it.
5. **If you're confused by a reference**, ask in class or office hours. Different authors explain the same concept differently — sometimes a second explanation clicks.
6. **For the suggested paper** (Davis & Goadrich), use the reading guide in `suggested_paper.md`. This is your first real research paper — take it slow and use the "How to Read a Research Paper" guide.

---

## Reference Abbreviation Key

| Abbreviation | Full Title | Authors | Free? |
|--------------|-----------|---------|-------|
| PRML | Pattern Recognition and Machine Learning | Bishop (2006) | No (but widely available) |
| ESL | The Elements of Statistical Learning | Hastie, Tibshirani, Friedman (2009) | Yes: hastie.su.domains/ElemStatLearn/ |
| ISLR | An Introduction to Statistical Learning | James, Witten, Hastie, Tibshirani (2021) | Yes: statlearning.com |
| D2L | Dive into Deep Learning | Zhang, Lipton, Li, Smola (2023) | Yes: d2l.ai |
| Understanding ML | Understanding Machine Learning: From Theory to Algorithms | Shalev-Shwartz & Ben-David (2014) | Yes: authors' website |
| MML | Mathematics for Machine Learning | Deisenroth, Faisal, Ong (2020) | Yes: mml-book.github.io |
| Daumé | A Course in Machine Learning | Hal Daumé III (2017) | Yes: ciml.info |
| Nielsen | Neural Networks and Deep Learning | Michael Nielsen (2015) | Yes: neuralnetworksanddeeplearning.com |
| Goodfellow | Deep Learning | Goodfellow, Courville, Bengio (2016) | Yes: deeplearningbook.org |
| MacKay | Information Theory, Inference, and Learning Algorithms | David MacKay (2003) | Yes: inference.org.uk/mackay/itila/ |
| Mitchell | Machine Learning | Tom Mitchell (1997) | No |
| Burkov | The Hundred-Page Machine Learning Book | Andriy Burkov (2019) | No (but very short) |
| Manning et al. | Introduction to Information Retrieval | Manning, Raghavan, Schütze (2008) | Yes: nlp.stanford.edu/IR-book/ |
| Fawcett | "An Introduction to ROC Analysis" | Tom Fawcett (2006) | Yes (search Google Scholar) |
| Davis & Goadrich | "The Relationship Between Precision-Recall and ROC Curves" | Davis & Goadrich (2006) | Yes (search Google Scholar) |
| Kaufman et al. | "Leakage in Data Mining" | Kaufman, Rosset, Perlich (2012) | Yes (search Google Scholar) |
| Cawley & Talbot | "On Over-fitting in Model Selection" | Cawley & Talbot (2010) | Yes (search Google Scholar) |
| Cortes et al. | "Learning Curves for Confident Predictions" | Cortes, Jackel, Solla, Vapnik, Denker (1994) | Yes (search Google Scholar) |
| Kohavi | "A Study of Cross-Validation and Bootstrap for Accuracy Estimation and Model Selection" | Ron Kohavi (1995) | Yes (search Google Scholar) |
