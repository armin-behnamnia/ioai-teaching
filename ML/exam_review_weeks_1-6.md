# Final Exam Review: Weeks 1–6

\newpage

## Week 1 — What is Machine Learning?

- The ML framework: data, model, loss, optimizer, prediction
- Supervised vs. unsupervised learning
- Regression vs. classification
- Overfitting and underfitting (intuition)
- The overfitting-underfitting table (complexity vs. training/test error)
- The "no free lunch" intuition
- Features, targets, training set, parameters, hyperparameters

\newpage

## Week 2 — Scalar Linear Regression

- The linear model: $\hat{y} = wx + b$
- Mean Squared Error (MSE): $\frac{1}{n}\sum(y_i - \hat{y}_i)^2$
- Deriving OLS algebraically (completing the square): $w^* = \text{Cov}(x,y)/\text{Var}(x)$, $b^* = \bar{y} - w^*\bar{x}$
- Ridge regression (L2): MSE + $\lambda w^2$, closed-form solution
- The regularization parameter $\lambda$ as a "complexity dial"
- Train vs. test error: the U-shaped curve
- $R^2$ and MSE as regression metrics
- Residuals and what they tell us

\newpage

## Week 3 — Overfitting & Regularization (Deeper)

- Polynomial regression: linear in parameters, nonlinear in features
- Degree vs. data size tradeoff
- Training error always decreases with complexity — why this is misleading
- The generalization gap (training ↓, test ↑ after sweet spot)
- Ridge in depth: how shrinkage works, choosing $\lambda$ visually
- Lasso (L1): sparsity, feature selection, why no closed form
- Geometric comparison: L2 ball vs. L1 diamond
- Elastic Net (brief)
- The "complexity dial" unifying principle (degree, $\lambda$ all control the same tradeoff)
- Bias-variance tradeoff (qualitative/intuition only)

\newpage

## Week 4 — Model Evaluation & Validation

- Train / validation / test split: three sets, three purposes
- The Golden Rule: never touch the test set during development
- k-fold cross-validation: procedure, fold sizes, CV error
- Leave-One-Out CV (LOOCV): when to use, bias-variance tradeoff vs. k-fold
- Data leakage: types and prevention ("split first, preprocess on training only")
- Overfitting to the validation set
- Classification metrics: confusion matrix (TP, FP, FN, TN)
- Accuracy, precision, recall, F1-score (formulas and intuition)
- Why accuracy fails with class imbalance
- ROC curves: construction, TPR vs. FPR, threshold sweeping
- AUC: interpretation ($P(\text{score}(+) > \text{score}(-))$)
- Precision-recall tradeoff and PR curves
- When to use PR vs. ROC (imbalanced data → PR)
- Regression metrics recap: MSE, RMSE, MAE, $R^2$
- Choosing the right metric for a given problem
- Learning curves: error vs. training set size
- Diagnosing overfitting vs. underfitting from learning curves

\newpage

## Week 5 — Probability for ML (ML-Specific, Not Probability Review)

- Bayes' theorem applied to ML: prior, likelihood, evidence, posterior
- The Bayesian view of learning: prior + data → posterior
- Medical testing example; connection to class imbalance (Week 4)
- Maximum Likelihood Estimation (MLE): the principle and why we use log-likelihood
- MLE for Bernoulli → sample mean (quick derivation)
- MLE for Gaussian → sample mean and variance (quick)
- **MLE under Gaussian noise = MSE loss** (the key proof)
- MLE ↔ loss-function correspondence: Gaussian→MSE, Bernoulli→cross-entropy, Laplacian→MAE
- Maximum a Posteriori (MAP): MLE + prior
- **MAP with Gaussian prior = ridge regression** (the key proof)
- MAP with Laplacian prior = lasso
- $\lambda = \sigma^2/\tau^2$ (noise-to-prior ratio): what it means
- Bias-variance decomposition (formal): $\mathbb{E}[(y-\hat{f})^2] = \text{Bias}^2 + \text{Variance} + \text{Irreducible noise}$
- Why cross terms vanish (independence + zero-mean noise)
- What reduces each term: more data → ↓variance; more complexity → ↓bias ↑variance; irreducible → nothing
- Connection to Week 3 (qualitative table → formal theorem) and Week 4 (learning curves)

\newpage

## Week 6 — Gradient Descent

- Motivation: why closed-form solutions don't always exist (lasso, logistic regression, neural networks)
- The gradient: direction of steepest ascent; $-\nabla L$ = steepest descent
- Gradient descent update rule: $\mathbf{w} \leftarrow \mathbf{w} - \eta\,\nabla L(\mathbf{w})$
- Step-by-step GD on $f(w) = w^2$ (geometric decay)
- Learning rate regimes: too small (slow), too large (diverge), just right
- Convergence condition for quadratics: $0 < \eta < 1/a$
- Convexity: one global minimum, GD guaranteed to converge
- Non-convex: local minima, role of initialization (preview for neural networks)
- Learning rate schedules: step decay, exponential, cosine
- **Deriving the MSE gradient** (chain rule): $\partial\text{MSE}/\partial w = -\frac{2}{n}\sum x_i r_i$, $\partial\text{MSE}/\partial b = -\frac{2}{n}\sum r_i$
- The residual $r_i = y_i - \hat{y}_i$ and its role in the gradient
- Optimality condition: $\sum x_i r_i = 0$ (residuals uncorrelated with inputs = OLS solution)
- Ridge GD: the shrinkage term $-2\eta\lambda w$
- Lasso GD: subgradient $\text{sgn}(w)$, why it drives weights to exactly 0
- Batch GD vs. SGD vs. mini-batch GD: cost, variance, when to use each
- Epochs: one pass through the data
- SGD's noisy trajectory and why noise can help (non-convex escape)
- Feature scaling: standardization, why it speeds convergence (elongated → spherical loss surface)
- Data leakage in scaling (Week 4 connection: split first, compute stats on training only)
- Monitoring training: loss curves (steady decrease = good, oscillation/divergence = reduce $\eta$)
- Training vs. validation loss: diagnosing overfitting from the gap
