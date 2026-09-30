# Actual Teaching Log — Weeks 1–6

> **Course:** Machine Learning for IOAI Preparation
> **Document purpose:** Precise record of what has been actually taught in class, week by week. This reflects the reality of classroom coverage, not the syllabus plan. Use this to identify gaps and plan future sessions.

---

## Week 1: What is Machine Learning? (Fully Covered)

**Status:** Complete — matches syllabus.

### Topics Taught

**Session 1:**
- What is learning? The ML problem setup: input space X, output space Y, hypothesis space H, loss function L
- Supervised vs. unsupervised vs. reinforcement learning — overview
- The "learning = function approximation" framing

**Session 2:**
- The supervised learning pipeline: training data, model, loss, optimization
- Worked visual example: fitting a line to 2D data by hand
- Concept of generalization: we care about unseen data
- Overfitting teaser (draw a wiggly curve through points)

---

## Week 2: Scalar Linear Regression (Fully Covered)

**Status:** Complete — matches syllabus.

### Topics Taught

**Session 1:**
- The linear model: ŷ = wx + b
- MSE loss in scalar form
- Deriving the optimal w and b from scratch using only algebra: w = Cov(x,y)/Var(x), b = ȳ − w·x̄
- Worked example: fitting a line to 3 data points by hand
- Intuition: the best line minimizes vertical distances

**Session 2:**
- Overfitting in linear regression (too many polynomial features vs. data points)
- Ridge regression in scalar form: add penalty λw² to the loss, solve for w
- L1 (lasso) brief mention — why it gives sparsity (geometry)
- Choosing λ: the overfitting-underfitting tradeoff

---

## Week 3: Overfitting & Regularization — Going Deeper (Fully Covered)

**Status:** Complete — matches syllabus.

### Topics Taught

**Session 1:**
- Polynomial regression: linear in parameters, nonlinear in features
- The degree-vs-data-size tradeoff
- Visual: degree 1 vs degree n−1 on the same data
- Training error always decreases with complexity — why this is misleading
- The generalization gap: training error ↓ but test error ↑

**Session 2:**
- Ridge regression in depth: the λ knob, how shrinkage works (denominator +λ), choosing λ visually
- Lasso (L1): sparsity, feature selection, why no closed form
- Geometric comparison: L2 ball vs. L1 diamond
- Elastic Net brief mention
- The overfitting-underfitting tradeoff as a unifying principle: complexity controls (degree, λ) all do the same thing

---

## Week 4: Model Evaluation & Validation (Fully Covered)

**Status:** Complete — matches syllabus.

### Topics Taught

**Session 1:**
- Training vs. validation vs. test sets
- The fundamental principle: never touch test data during model selection
- k-fold cross-validation
- Leave-one-out (LOOCV)
- Overfitting to the validation set
- Data leakage — what it is and why it destroys your evaluation

**Session 2:**
- Classification metrics: accuracy, precision, recall, F1-score, confusion matrix
- Why accuracy can be misleading (class imbalance)
- ROC curve and AUC (intuition + construction)
- Regression metrics: MSE, RMSE, MAE, R²
- Choosing the right metric for the problem

---

## Week 5: Probability for ML (Partially Covered)

**Status:** Partial — significant content deferred to Week 6.

### Topics Taught

**Classification metrics review:**
- TP, FP, TN, FN
- TPR, FPR
- Precision, recall, F1
- Negative recall and precision

**Train/validation/test pipeline:**
- Train, validation, and test phases and their pipeline
- The reasoning behind each phase
- The golden rule (never touch test during model selection)
- K-fold validation

**MLE and MAP (concepts only — no derivations):**
- MLE: the principle of finding the parameter that makes the data most likely
- MAP: MLE + prior
- Avg Posterior Distribution Estimation (concept mentioned, no concrete examples)

**Bias-variance decomposition (started, not finished):**
- Began decomposing the expected squared error of the estimator w.r.t. the true variable
- Identified that this leads to the Expected Posterior Distribution
- Did NOT complete the derivation

### Topics NOT Taught (deferred to Week 6)

- Bayes' theorem applied to ML (prior/likelihood/evidence/posterior interpretation)
- Medical testing example, spam filtering setup
- MLE for Bernoulli (derivation → sample mean)
- MLE for Gaussian (derivation → sample mean and variance)
- MLE = MSE proof (Gaussian noise → MSE loss)
- MLE ↔ loss-function correspondence table
- MAP = Ridge proof (Gaussian prior → L2 penalty)
- Laplacian prior → Lasso proof
- Complete bias-variance derivation (cross terms vanishing, final formula)
- Bias-variance tradeoff diagram and connection to Week 3

---

## Week 6: Corrected Week — Probability Catch-Up + Gradient Descent (Partially Covered)

**Status:** Partial — Session 1 material partially covered; Session 2 material only introduced conceptually.

### Topics Taught

**Bayes' theorem applied to ML (Section 1 of corrected handout):**
- The ML interpretation of Bayes' theorem: prior, likelihood, evidence, posterior
- The Bayesian learning loop: prior → observe data → posterior
- Why the evidence can be dropped for optimization (MLE and MAP)
- Medical testing example: disease prevalence 1%, 99% sensitive test → only 16.7% precision
- Connection to class imbalance (Week 4): P(disease|positive) = precision

**Maximum Likelihood Estimation (Section 2 of corrected handout):**
- The MLE principle: find θ that makes the data most probable
- The log-likelihood trick: products become sums, numerical stability
- MLE for Bernoulli — full derivation: likelihood → log-likelihood → differentiate → solve → sample mean
- MLE for Gaussian — full derivation: → sample mean and sample variance

**The Deep Connection: MLE = MSE (Section 3 of corrected handout):**
- The setup: y_i = wx_i + b + ε_i, ε_i ~ N(0, σ²)
- The likelihood and log-likelihood derivation
- The key proof: maximizing log-likelihood = minimizing MSE
- The MLE ↔ loss-function correspondence table (Gaussian → MSE, Bernoulli → cross-entropy, Laplacian → MAE)

**Bias-Variance (formulation and intuition, not full derivation):**
- The decomposition formula: Expected error = Bias² + Variance + Irreducible noise
- Intuition for each term:
  - Bias²: systematic error (average prediction vs. truth)
  - Variance: sensitivity to training data
  - Irreducible noise: σ², the noise floor
- The tradeoff: as model complexity increases, bias decreases but variance increases
- Connection to Week 3: λ=0 (low bias/high variance), λ→∞ (high bias/low variance)
- Note: the full derivation (cross terms vanishing) was NOT completed

**Gradient Descent (general idea and math formulation only):**
- Motivation: why not always use closed-form? (Lasso, logistic regression, neural networks have no closed form)
- The concept of iterative optimization: start somewhere, take a step downhill, repeat
- The gradient: vector of partial derivatives, points in direction of steepest ascent
- The GD update rule: w ← w − η∇L(w)
- Intuition: "look at the slope, take a step downhill, repeat"

### Topics NOT Taught (still pending)

**From Week 5/6 catch-up (Session 1 material):**
- MAP = Ridge proof (Gaussian prior → L2 penalty, λ = σ²/τ²)
- Laplacian prior → Lasso proof
- Full bias-variance derivation (the A+B+C decomposition, cross terms vanishing)
- The three deep connections summary (formal)

**From Week 6 gradient descent (Session 2 material):**
- Step-by-step GD on 1D quadratic (f(w) = w², the iteration table, geometric decay)
- Learning rate regimes (too small, too large, just right — visual demo)
- Convergence condition for quadratics (0 < η < 1/a)
- Convexity and why GD is guaranteed to converge for MSE
- Learning rate schedules (fixed, step decay, inverse, cosine)
- GD on linear regression: deriving the MSE gradient via chain rule (∂MSE/∂w, ∂MSE/∂b)
- The residual and the optimality condition (Σ x_i r_i = 0 = OLS)
- Ridge regression with GD (shrinkage term −2ηλw)
- Lasso subgradient descent (sgn(w), why it drives weights to exactly 0)
- Stochastic Gradient Descent (SGD): one example at a time, noisy but unbiased
- Mini-batch GD: the standard for modern ML
- Batch GD vs SGD vs mini-batch comparison table
- Epochs (1 epoch = 1 pass through data)
- Feature scaling: why it helps (elongated vs spherical loss surface), standardization
- Data leakage risk in scaling (compute stats on training only)
- Monitoring training: loss curves (steady decrease, plateau, oscillation, divergence)
- Training vs validation loss (diagnosing overfitting, underfitting)

---

## Summary: Cumulative Coverage Status

| Week | Syllabus Topic | Status |
|------|---------------|--------|
| W1 | What is ML? Problem formulation, supervised/unsupervised/RL, generalization | ✅ Complete |
| W2 | Scalar linear regression, MSE, OLS closed form, ridge, lasso mention | ✅ Complete |
| W3 | Polynomial overfitting, ridge/lasso depth, L1 vs L2 geometry, complexity dial | ✅ Complete |
| W4 | Train/val/test, k-fold, LOOCV, data leakage, classification metrics, ROC/AUC, regression metrics | ✅ Complete |
| W5 | Probability for ML: Bayes, MLE, MAP, bias-variance | ⚠️ Partial (concepts only, no derivations; metrics review was re-taught) |
| W6 | Corrected: Bayes/MLE derivations + MLE=MSE proof + bias-variance formulation + GD concept | ⚠️ Partial (Sections 1–3 done; bias-variance intuition only; GD introduced conceptually) |

### What Students Can Currently Do

- Formulate the ML problem (input/output/hypothesis space/loss)
- Derive OLS and ridge in scalar form (closed form)
- Explain overfitting, regularization, L1 vs L2 geometry
- Evaluate models: train/val/test, k-fold, classification metrics, ROC/AUC, regression metrics
- State Bayes' theorem with ML interpretation (prior/likelihood/evidence/posterior)
- Derive MLE for Bernoulli (→ sample mean) and Gaussian (→ sample mean/variance)
- Prove that MLE under Gaussian noise = minimizing MSE
- State the bias-variance decomposition formula and explain each term
- State the GD update rule and explain the concept of iterative optimization
- Explain why closed-form solutions don't always exist

### What Students Cannot Yet Do (Critical Gaps)

- Prove MAP with Gaussian prior = ridge regression (λ = σ²/τ²)
- Prove Laplacian prior → lasso
- Complete the bias-variance derivation (cross terms vanishing)
- Perform GD step-by-step on a concrete example
- Derive the gradient of MSE using the chain rule
- Explain learning rate regimes and convergence conditions
- Compare batch GD, SGD, and mini-batch GD
- Explain feature scaling and its connection to data leakage
- Apply GD to ridge and lasso (shrinkage term, subgradient)
- Monitor training via loss curves

---

## Recommended Priority for Week 7

The following topics are **critical prerequisites** for Week 7 (Logistic Regression) and must be taught before or during the next session:

1. **MAP = Ridge proof** — needed because logistic regression uses MAP with Gaussian prior → L2 regularized logistic regression
2. **GD on MSE: the gradient derivation** — the chain rule pattern (outer derivative × inner derivative) is exactly what's needed for the cross-entropy gradient in logistic regression
3. **Learning rate regimes** — students need to understand what happens when η is too small/large
4. **SGD vs batch GD** — logistic regression is trained with GD/SGD; students need this before Week 7
5. **The residual / optimality condition** — the "beautiful cancellation" in logistic regression mirrors the MSE gradient structure

Topics that can be deferred slightly (Week 8+):
- Feature scaling (can be introduced when training actual models)
- Learning rate schedules (can come with neural network training in Week 17)
- Full bias-variance derivation (the intuition is sufficient for now; formal proof can be revisited)
