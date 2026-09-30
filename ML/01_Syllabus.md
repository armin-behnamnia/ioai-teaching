# Detailed Syllabus — Week-by-Week Breakdown

## Phase Overview

| Phase | Weeks | Months | Sessions/Week | Focus |
|-------|-------|--------|---------------|-------|
| Phase 1: Foundations | W1–W8 | Month 1–3 | W1–W6: 2× 80min; W7–W8: 4× 70min | ML framework, scalar linear regression, overfitting & regularization, model evaluation, probability, gradient descent, logistic regression, matrix regression |
| Phase 2: Core ML | W9–W20 | Month 3–5 | 4× 70min | k-NN, decision trees, information theory, feature engineering, SVMs, neural networks, training, generalization, clustering, PCA |
| Phase 3: Exam Prep | W21–W24 | Month 5–6 | 4× 70min | Review, practice exams, weak-topic reinforcement |
| **Checkpoint** | | **Month 5–6** | | **National Qualification Exam** |
| Phase 4: Advanced ML | W25–W36 | Month 7–9 | 4× 70min | Deep learning, generative models, RL, representation learning |
| Phase 5: IOAI Prep | W37–W44 | Month 10–12 | 4× 70min | Past IOAI problems, advanced topics, competition strategy |

---

## PHASE 1: Foundations (Weeks 1–8; Weeks 1–6: 2 sessions/week, Weeks 7–8: 4 sessions/week)

> **Restructuring note:** Phase 1 builds the fundamentals deeply before introducing new algorithms. Weeks 1–4 use only basic algebra and statistics (mean, variance, fractions) — no calculus or matrix operations required. Calculus-based topics (gradient descent, logistic regression) come in Weeks 6–7 when students' calculus courses have caught up. k-NN and decision trees are deferred to Phase 2 (Weeks 9–10) where they fit naturally as nonlinear methods.

> **Pacing note (actual coverage):** Weeks 5–6 were partially covered (see `actual_teaching_log_w1_w6.md`): the probability derivations (MAP = Ridge, Laplacian → Lasso, full bias-variance) and most of the gradient-descent practice (GD by hand, learning-rate regimes, the MSE gradient, SGD/mini-batch, feature scaling) were introduced conceptually but not completed. A **two-week break** follows Week 6. Week 7 (now 4× 70-min sessions) opens with a review of Weeks 1–6 and completes all pending material before starting logistic regression.

### Week 1: What is Machine Learning?

**Goals:** Establish the ML problem formulation. Differentiate supervised/unsupervised/reinforcement learning. Build intuition for "learning from data."

| Session | Topics |
|---------|--------|
| S1 | What is learning? The ML problem setup: input space X, output space Y, hypothesis space H, loss function L. supervised vs. unsupervised vs. reinforcement learning — overview. The "learning = function approximation" framing. |
| S2 | The supervised learning pipeline: training data, model, loss, optimization. Worked visual example: fitting a line to 2D data by hand. Concept of generalization: we care about unseen data. Overfitting teaser (draw a wiggly curve through points). |

**Handout:** ML problem formulation, notation, vocabulary glossary.
**Paper:** None (first week — focus on handout).
**Quiz topics:** Identify supervised vs. unsupervised problems. Define hypothesis space. What does a loss function measure?

---

### Week 2: Scalar Linear Regression

**Goals:** First complete ML model. Taught entirely in scalar notation — no matrices. Introduces the closed-form solution using only mean, variance, and covariance.

| Session | Topics |
|---------|--------|
| S1 | The linear model: ŷ = wx + b. MSE loss in scalar form. Deriving the optimal w and b from scratch using only algebra: w = Cov(x,y)/Var(x), b = ȳ − w·x̄. Worked example: fitting a line to 3 data points by hand. Intuition: the best line minimizes vertical distances. |
| S2 | Overfitting in linear regression (too many polynomial features vs. data points). Ridge regression in scalar form: add penalty λw² to the loss, solve for w. L1 (lasso) brief mention — why it gives sparsity (geometry). Choosing λ: the overfitting-underfitting tradeoff. |

**Handout:** Scalar derivation of OLS and ridge. All formulas in scalar form. Worked examples.
**Paper:** "A Few Useful Things to Know about Machine Learning" — Domingos (2012). See paper roadmap.
**Quiz topics:** Compute w = Cov/Var for a small dataset. What does MSE measure? Why does ridge help? What is the overfitting-underfitting tradeoff?

---

### Week 3: Overfitting & Regularization — Going Deeper

**Goals:** Deepen the linear regression story. Understand overfitting mechanistically, master regularization, and build the intuition for the bias-variance tradeoff (without the formal probability-based derivation, which comes in Week 5).

| Session | Topics |
|---------|--------|
| S1 | Polynomial regression: linear in parameters, nonlinear in features. The degree-vs-data-size tradeoff. Visual: degree 1 vs degree n−1 on the same data. Training error always decreases with complexity — why this is misleading. The generalization gap: training error ↓ but test error ↑. |
| S2 | Ridge regression in depth: the λ knob, how shrinkage works (denominator +λ), choosing λ visually. Lasso (L1): sparsity, feature selection, why no closed form. Geometric comparison: L2 ball vs. L1 diamond. Elastic Net brief mention. The overfitting-underfitting tradeoff as a unifying principle: complexity controls (degree, λ) all do the same thing. |

**Handout:** Polynomial overfitting walkthrough. Ridge/lasso comparison. The "complexity dial" unifying diagram.
**Paper:** "A Few Useful Things to Know about Machine Learning" — Domingos (2012), re-read Section 5 (overfitting has many faces). See paper roadmap.
**Quiz topics:** Why does training error always decrease with degree? How does ridge shrink the slope? L1 vs. L2 geometry. What does λ control?

---

### Week 4: Model Evaluation & Validation

**Goals:** How do we know if a model is good? Exam-critical and essential for any real ML practice. No calculus required — only counting, ratios, and basic algebra.

| Session | Topics |
|---------|--------|
| S1 | Training vs. validation vs. test sets. The fundamental principle: never touch test data during model selection. k-fold cross-validation. Leave-one-out (LOOCV). Overfitting to the validation set. Data leakage — what it is and why it destroys your evaluation. |
| S2 | Classification metrics: accuracy, precision, recall, F1-score, confusion matrix. Why accuracy can be misleading (class imbalance). ROC curve and AUC (intuition + construction). Regression metrics: MSE, RMSE, MAE, R². Choosing the right metric for the problem. |

**Handout:** Evaluation metrics reference card. ROC curve construction example. Cross-validation guide.
**Paper:** "The Relationship Between Precision-Recall and ROC Curves" — Davis & Goadrich (2006). See paper roadmap.
**Quiz topics:** When is F1 better than accuracy? Construct a confusion matrix. What does AUC measure? What is k-fold cross-validation?

---

### Week 5: Probability for ML

**Goals:** Bridge students' concurrent probability course to ML-specific applications. By this point, their stats course should have covered basic distributions and Bayes' theorem.

| Session | Topics |
|---------|--------|
| S1 | Random variables, PMF/PDF, expectation, variance. Joint, marginal, conditional distributions. Bayes' theorem (derivation + intuition). Examples: medical testing, spam filtering setup. |
| S2 | Maximum Likelihood Estimation (MLE): the principle. MLE for Bernoulli → mean of data. MLE for Gaussian → sample mean and variance. Connection: MLE for Gaussian noise model = MSE loss (deep connection). Maximum a Posteriori (MAP): Bayes + MLE. Connection: MAP with Gaussian prior = ridge regression. Bias-variance decomposition (formal treatment, now that probability is ready). |

**Handout:** Probability toolkit for ML. MLE/MAP derivations. The MLE↔loss-function correspondence table. Bias-variance decomposition.
**Paper:** "Visual Information Theory" — Christopher Olah (blog post). See paper roadmap.
**Quiz topics:** State Bayes' theorem. Derive MLE for Bernoulli. Show that MSE = MLE under Gaussian noise. What does a prior do in MAP? Decompose expected error into bias² + variance + irreducible noise.

---

### Week 6: Optimization Basics — Gradient Descent

**Goals:** Teach gradient descent from scratch. By this point, students' calculus course has covered derivatives and the chain rule.

| Session | Topics |
|---------|--------|
| S1 | Why not just use closed-form? Motivation for iterative methods. Gradient of a scalar function. Geometric meaning: direction of steepest ascent. Gradient descent update rule: w ← w − η∇L(w). Step-by-step on a 1D quadratic. Learning rate: too large, too small, just right (visual). |
| S2 | Gradient descent on linear regression (batch GD). Derive ∇L for MSE in scalar form. Convergence intuition: convexity guarantees. Stochastic gradient descent (SGD) and mini-batch GD. Trade-offs: variance, speed, memory. Feature scaling. |

**Handout:** Gradient descent derivation for linear regression (scalar). Learning rate schedules. SGD vs. batch GD comparison table.
**Paper:** "An Overview of Gradient Descent Optimization Algorithms" — Ruder (2016). See paper roadmap.
**Quiz topics:** Write the GD update rule. Derive gradient of MSE. What happens if learning rate is too large? Difference between SGD and batch GD?

---

### Week 7: Logistic Regression — From Regression to Classification

**Goals:** Second complete ML model. Bridges regression and classification. Connects MLE (Week 5), gradient descent (Week 6), and introduces the sigmoid and cross-entropy.

| Session | Topics |
|---------|--------|
| S1 | Binary classification setup. The sigmoid function σ(z) = 1/(1+e⁻ᶻ): properties, derivative. Logistic regression model: P(y=1|x) = σ(wx + b). Decision boundary is linear. Visual: decision boundary in 2D. Cross-entropy loss = negative log-likelihood (connection to MLE from Week 5). |
| S2 | Training logistic regression: derive gradient of cross-entropy w.r.t. w (the beautiful cancellation). Apply gradient descent (from Week 6). Multi-class: softmax regression, softmax function, cross-entropy for multi-class. Why not use MSE for classification. Logistic regression = 0-hidden-layer neural network (preview). |

**Handout:** Full derivation of logistic regression gradients. Softmax regression. Connection between sigmoid and softmax.
**Paper:** "Machine Learning that Matters" — Wagstaff (2012). See paper roadmap.
**Quiz topics:** Derive gradient of binary cross-entropy. What is softmax? Why not use MSE for classification? What is the decision boundary of logistic regression?

---

### Week 8: Matrix Linear Regression & Phase 1 Consolidation

**Goals:** Revisit linear regression in matrix notation (now that linear algebra is ready). Consolidate all Phase 1 concepts. Introduce the triality.

| Session | Topics |
|---------|--------|
| S1 | Matrix formulation: design matrix X, vector y. The normal equation w* = (XᵀX)⁻¹Xᵀy (derivation using matrix calculus identities — taught from scratch). Ridge regression in matrix form. Geometric interpretation: projection onto column space. The hat matrix. |
| S2 | The triality of linear regression: geometry (projection), probability (MLE/MAP from Week 5), optimization (gradient descent from Week 6). Comprehensive review of Weeks 1–7. Practice problems integrating all topics. Preview of Phase 2. |

**Handout:** Matrix formulation of OLS and ridge. Phase 1 summary "cheat sheet."
**Paper:** "A High-Bias, Low-Variance Introduction to Machine Learning for Physicists" — Mehta et al. (2019), Sections 1–3. See paper roadmap.
**Quiz topics:** Comprehensive mini-exam (20 min, covers W1–W7).

---

## PHASE 2: Core ML (Weeks 9–20, 4 sessions/week)

### Week 9: k-Nearest Neighbors & Instance-Based Learning

**Goals:** Simplest nonlinear method. Purely algorithmic. Deepens understanding of distance, dimensionality, and overfitting. Now that students have solid fundamentals (evaluation, bias-variance), k-NN illustrates these concepts in a new paradigm.

| Session | Topics |
|---------|--------|
| S1 | k-NN algorithm: classify by majority vote of k nearest neighbors. Distance metrics: Euclidean, Manhattan, cosine. Choice of k: k=1 → overfitting, k=n → underfitting. Visual: decision boundaries for different k. k-NN for regression (average of neighbors). |
| S2 | Weighted k-NN. The curse of dimensionality: distance becomes less meaningful in high dimensions (intuition + the "all points are roughly equidistant" phenomenon). The "No Free Lunch" theorem (statement + intuition). Connection to bias-variance (Week 5): k controls the bias-variance tradeoff. |
| S3 | Worked examples: classify points by hand for k=3 and k=5. Compute k-NN regression predictions. |
| S4 | Problem-solving session. |

**Handout:** k-NN algorithm, distance metrics, curse of dimensionality, No Free Lunch theorem.
**Paper:** "The Lack of A Priori Distinctions Between Learning Algorithms" — Wolpert (1996). See paper roadmap.
**Quiz topics:** How does k affect overfitting in k-NN? What is the curse of dimensionality? What is the No Free Lunch theorem? Connect k to the bias-variance tradeoff.

---

### Week 10: Decision Trees & Random Forests

**Goals:** Tree-based methods are interpretable, exam-relevant, and introduce ensemble learning. Builds on evaluation (Week 4) and bias-variance (Week 5).

| Session | Topics |
|---------|--------|
| S1 | Decision tree structure: internal nodes = feature tests, leaves = predictions. Splitting criteria: Gini impurity (1 − Σpᵢ²), information gain. Building a tree: recursive greedy splitting. Stopping criteria. Worked example: build a small tree by hand. |
| S2 | Overfitting in trees (a depth-∞ tree memorizes data). Pruning. Ensemble methods: bagging (bootstrap aggregating). Random forests: bagging + random feature selection. Why randomization helps. Feature importance. |
| S3 | Bias-variance decomposition of bagging: averaging reduces variance, not bias. Why random feature selection de-correlates trees. Out-of-bag error. |
| S4 | Problem-solving session. Build a tree by hand. Compute Gini impurity for candidate splits. |

**Handout:** Decision tree construction walkthrough. Gini impurity derivation. Random forest algorithm.
**Paper:** "Random Forests" — Breiman (2001). See paper roadmap.
**Quiz topics:** Compute Gini impurity for a split. Why do random forests reduce overfitting? What is bagging? Why do deep trees overfit? How does bagging reduce variance?

---

### Week 11: Information Theory Basics

**Goals:** Entropy, KL divergence, cross-entropy. Essential for understanding classification loss functions and generative models later. By this point, students' probability course (Week 5) provides enough foundation.

| Session | Topics |
|---------|--------|
| S1 | Why information theory in ML? Self-information: I(x) = -log p(x). Intuition: rare events carry more information. Entropy H(X) = -Σ p(x) log p(x). Examples: fair coin, biased coin, uniform distribution. |
| S2 | KL divergence: D_KL(p‖q) = Σ p(x) log(p(x)/q(x)). Intuition: penalty for approximating p with q. Non-negativity (Gibbs' inequality, sketch proof). Cross-entropy: H(p,q) = H(p) + D_KL(p‖q). Why cross-entropy is used as a loss in classification. |
| S3 | Worked examples: compute entropy and cross-entropy for simple distributions. Revisit logistic regression (Week 7): cross-entropy loss from the information-theoretic perspective. Connection to Gini impurity (Week 10): both measure "mixedness." |
| S4 | Problem-solving session. |

**Handout:** Information theory cheat sheet. All derivations. Entropy visualizations.
**Paper:** "Visual Information Theory" — Christopher Olah (blog post). See paper roadmap.
**Quiz topics:** Compute entropy of a Bernoulli(p). What is KL divergence and why is it non-negative? Why is cross-entropy a good loss function? How does entropy relate to Gini impurity?

---

### Week 12: From Linear to Nonlinear — Feature Engineering & Basis Functions

**Goals:** Bridge from linear models to nonlinear learning without neural networks yet.

| Session | Topics |
|---------|--------|
| S1 | Limitations of linear models (visual: XOR problem). Polynomial basis functions. Feature maps φ(x). The kernel trick (intuition only, full treatment with SVMs later). |
| S2 | Radial basis functions. Feature engineering in practice: interactions, binning, one-hot encoding. The overfitting-underfitting implications of adding features. |
| S3 | Curse of dimensionality (revisited in depth): distance becomes meaningless in high dimensions. Volume grows exponentially. Why high-d data is hard. (Introduced in Week 9 with k-NN; now deeper.) |
| S4 | Problem-solving session. Worked examples of feature design. |

**Handout:** Feature engineering guide. Curse of dimensionality visualizations.
**Paper:** "A Few Useful Things to Know about Machine Learning" — Domingos (2012), re-read Section 6 (feature engineering). See paper roadmap.
**Quiz topics:** What is a feature map? Why does the XOR problem break linear models? Explain the curse of dimensionality. How does feature engineering interact with overfitting?

---

### Week 13: Support Vector Machines — Part 1 (Linear SVM & Margins)

**Goals:** The margin concept, hard-margin SVM, the optimization problem.

| Session | Topics |
|---------|--------|
| S1 | Geometric margin: distance from a point to the decision boundary. Maximum margin classifier: the optimization problem. Formulation: maximize margin = minimize ‖w‖² subject to y_i(w^T x_i + b) ≥ 1. |
| S2 | The Lagrangian dual formulation (introduction). Why duality matters: it reveals the role of support vectors and enables kernels. KKT conditions (overview). |
| S3 | Support vectors: only points on the margin matter. The sparsity of SVM solutions vs. logistic regression. |
| S4 | Problem-solving session. |

**Handout:** SVM margin derivation. Lagrangian duality overview (at appropriate level).
**Paper:** See paper roadmap Week 11.
**Quiz topics:** Write the hard-margin SVM optimization problem. What are support vectors? Why is the SVM solution sparse?

---

### Week 14: Support Vector Machines — Part 2 (Kernels & Soft Margin)

**Goals:** Kernel trick, soft-margin SVM, practical SVM usage.

| Session | Topics |
|---------|--------|
| S1 | The kernel trick: replace φ(x_i)·φ(x_j) with K(x_i, x_j). Common kernels: linear, polynomial, RBF/Gaussian. Mercer's theorem (statement + intuition). |
| S2 | Soft-margin SVM: allow violations via slack variables ξ_i. The C parameter: trade-off between margin and violations. Hinge loss: L = max(0, 1 - y·f(x)). Connection: SVM minimizes hinge loss + L2 regularization. |
| S3 | SVM vs. logistic regression: hinge loss vs. cross-entropy. When to use each. |
| S4 | Problem-solving session. |

**Handout:** Kernel functions reference. Soft-margin SVM derivation. SVM vs. logistic regression comparison.
**Paper:** See paper roadmap Week 12.
**Quiz topics:** What is the kernel trick? What does the C parameter control? Compare hinge loss and cross-entropy. What is a valid kernel (Mercer's condition)?

---

### Week 15: Introduction to Neural Networks — Perceptron & Multi-Layer Perceptron

**Goals:** Build neural networks from the perceptron up. The historical and conceptual arc.

| Session | Topics |
|---------|--------|
| S1 | The perceptron (Rosenblatt, 1958): algorithm and update rule. Perceptron convergence theorem (statement + intuition). Why the perceptron can't solve XOR. |
| S2 | Multi-layer perceptron (MLP): hidden layers, nonlinear activations. Universal approximation theorem (statement + intuition: enough width → approximate any continuous function). Activation functions: sigmoid, tanh, ReLU, and their derivatives. Why ReLU dominates. |
| S3 | Forward propagation: computing the output of an MLP. Matrix formulation. Notation: weights W^(l), biases b^(l), activations a^(l). |
| S4 | Problem-solving session. Compute forward pass by hand on a tiny network. |

**Handout:** Neural network notation and forward propagation. Activation function comparison.
**Paper:** See paper roadmap Week 13.
**Quiz topics:** Why can't a perceptron solve XOR? State the universal approximation theorem (informally). Compute the output of a 2-layer network with ReLU activations.

---

### Week 16: Backpropagation — The Chain Rule at Scale

**Goals:** Complete mathematical derivation of backpropagation. Every student must understand this deeply.

| Session | Topics |
|---------|--------|
| S1 | The chain rule refresher. Computational graphs: representing a neural network as a DAG of operations. Forward mode vs. reverse mode automatic differentiation. Why reverse mode (backprop) is efficient for neural networks. |
| S2 | Backpropagation derivation step-by-step for a 2-layer network. The four fundamental equations of backprop: δ^(L), δ^(l) in terms of δ^(l+1), gradients of W and b. The elegance of δ^(l) = (W^(l+1))^T δ^(l+1) ⊙ σ'(z^(l)). |
| S3 | Full derivation on a 3-layer network. Matrix calculus notation. Common pitfalls: transposing correctly, broadcasting. |
| S4 | Problem-solving session. Derive gradients by hand for small networks. |

**Handout:** The complete backpropagation derivation. Computational graph examples.
**Paper:** See paper roadmap Week 14.
**Quiz topics:** Derive backpropagation for a 2-layer network. What is a computational graph? Why is reverse-mode autodiff preferred? Write the four fundamental equations of backprop.

---

### Week 17: Training Neural Networks — Optimization & Practical Considerations

**Session | Topics |
|---------|--------|
| S1 | Mini-batch SGD revisited for neural networks. Momentum: v_t = γv_{t-1} + η∇L. Nesterov momentum. RMSprop: adaptive learning rates per parameter. Adam: momentum + adaptive rates (derive the update). |
| S2 | Weight initialization: why it matters. Xavier/Glorot initialization (derivation: preserve variance across layers). He initialization for ReLU. Vanishing and exploding gradients: why they happen, how initialization and activation choices affect them. |
| S3 | Regularization for neural networks: L2 (weight decay), dropout (randomly zero neurons during training — why it works as ensemble), early stopping, batch normalization (conceptual: stabilize training, reduce internal covariate shift). |
| S4 | Problem-solving session. Adam update computation by hand. |

**Handout:** Optimizer comparison table. Initialization derivations. Regularization methods overview.
**Paper:** See paper roadmap Week 15.
**Quiz topics:** Write the Adam update rule. Why does Xavier initialization help? How does dropout work? What causes vanishing gradients?

---

### Week 18: Generalization Theory — Why Does Deep Learning Work?

| Session | Topics |
|---------|--------|
| S1 | The puzzle: neural networks have millions of parameters but don't overfit as badly as expected. Double descent phenomenon (visual). Classical generalization bounds (VC dimension — statement + intuition). |
| S2 | Regularization revisited: explicit (L2, dropout) vs. implicit (SGD itself regularizes). The role of architecture inductive bias. |
| S3 | Learning curves: training loss vs. validation loss over epochs. Diagnosing: underfitting (both high), overfitting (gap), good fit. What to do for each case. |
| S4 | Problem-solving session. Analyze learning curve scenarios. |

**Handout:** Generalization theory intuitions. Diagnostic guide for learning curves.
**Paper:** See paper roadmap Week 16.
**Quiz topics:** What is the double descent phenomenon? What is VC dimension (intuitively)? How do you diagnose overfitting from learning curves? Why does SGD have a regularizing effect?

---

### Week 19: Unsupervised Learning — Clustering

| Session | Topics |
|---------|--------|
| S1 | Unsupervised learning setup: no labels, find structure. k-means clustering: algorithm, objective function (inertia), Lloyd's algorithm. Convergence properties. Choosing k: elbow method, silhouette score. |
| S2 | Gaussian Mixture Models (GMM): a probabilistic clustering model. The generative story. The likelihood is intractable (log-sum-exp). |
| S3 | Expectation-Maximization (EM) algorithm for GMM: E-step (compute responsibilities), M-step (update parameters). Connection to k-means: k-means is "hard" EM for GMM. |
| S4 | Problem-solving session. Run EM by hand on a tiny example. |

**Handout:** k-means and GMM derivations. EM algorithm general framework.
**Paper:** See paper roadmap Week 17.
**Quiz topics:** Write the k-means objective. What is the E-step and M-step in EM? How is k-means related to GMM? What is the silhouette score?

---

### Week 20: Dimensionality Reduction, Phase 2 Consolidation & Integration

| Session | Topics |
|---------|--------|
| S1 | Principal Component Analysis (PCA): motivation (reduce dimensionality while preserving variance). PCA via eigendecomposition of covariance matrix. The projection that maximizes variance. Derivation: Lagrangian → eigenvalue problem. PCA via SVD. Choosing number of components: explained variance ratio. |
| S2 | t-SNE (conceptual): nonlinear dimensionality reduction for visualization. The KL divergence objective. Why t-SNE is for visualization, not as a general preprocessing step. UMAP (brief overview). |
| S3 | The full ML toolkit: a decision framework. Given a problem, how to choose a model. Flowchart: classification vs. regression vs. clustering, linear vs. nonlinear, interpretability vs. performance, data size considerations. Cross-cutting review: loss functions (MSE, cross-entropy, hinge, KL) — when to use each. |
| S4 | Phase 2 comprehensive quiz (30 min) + integration problems. |

**Handout:** PCA derivation. t-SNE intuition. Phase 2 summary. Model selection decision flowchart.
**Paper:** See paper roadmap Week 20.
**Quiz topics:** Derive PCA as a variance-maximization problem. What is the relationship between PCA and SVD? Full comprehensive quiz covering Phase 2.

---

## PHASE 3: Exam Preparation (Weeks 21–24, 4 sessions/week)

### Week 21: Review of High-Frequency Exam Topics — Part 1

| Session | Topics |
|---------|--------|
| S1 | Linear regression, logistic regression, MLE/MAP — rapid-fire derivation review. |
| S2 | Gradient descent, backpropagation — re-derive from scratch. Common exam variations. |
| S3 | Evaluation metrics, bias-variance, regularization — conceptual rapid fire. |
| S4 | Practice problems (timed, exam-style). |

**Handout:** "Exam derivation checklist" — every derivation students should be able to reproduce.
**Paper:** See paper roadmap Week 20.

---

### Week 22: Review of High-Frequency Exam Topics — Part 2

| Session | Topics |
|---------|--------|
| S1 | SVMs, kernels, decision trees, random forests — rapid review. |
| S2 | Neural networks, optimizers, initialization, regularization — rapid review. |
| S3 | Unsupervised: k-means, GMM/EM, PCA — rapid review. |
| S4 | Practice problems (timed). |

---

### Week 23: Mock Exam 1 & Review

| Session | Topics |
|---------|--------|
| S1 | Mock exam (full length, 80 min). |
| S2 | Detailed review of mock exam solutions. Identify common mistakes. |
| S3 | Targeted review of weak topics identified from mock exam. |
| S4 | Additional practice on weak areas. |

---

### Week 24: Mock Exam 2 & Final Preparation

| Session | Topics |
|---------|--------|
| S1 | Mock exam 2 (full length, 80 min). |
| S2 | Detailed review. |
| S3 | Exam strategy: time management, problem selection, how to approach derivations under pressure. |
| S4 | Last-minute Q&A. Confidence building. |

**Handout:** Exam strategy guide. Common pitfalls checklist.
**Paper:** See paper roadmap Week 21.

---

## >>> NATIONAL QUALIFICATION EXAM <<<

### Week 25: Post-Exam Debrief & Transition

| Session | Topics |
|---------|--------|
| S1 | Exam review and discussion. What worked, what didn't. |
| S2 | Preview of advanced topics. What the IOAI competition looks like. |
| S3 | Introduction to the advanced phase: how it differs (more research-oriented, more reading). |
| S4 | Setting up study groups and paper reading clubs for the advanced phase. |

---

## PHASE 4: Advanced ML (Weeks 25–36, 4 sessions/week)

### Week 26–27: Convolutional Neural Networks (CNNs)

| Week | Session | Topics |
|------|---------|--------|
| W26 | S1 | The vision problem: why MLPs fail on images (parameter explosion, no spatial inductive bias). |
| | S2 | Convolution operation: mathematical definition. 1D and 2D convolution. Filters/kernels. Stride, padding. Output size formula. |
| | S3 | Pooling: max pooling, average pooling. Why pooling: translation invariance, dimensionality reduction. |
| | S4 | Classic architectures: LeNet, AlexNet, VGG. Key ideas: stacking convolutions, ReLU, depth matters. |
| W27 | S1 | Deeper architectures: ResNet and residual connections (the identity shortcut). Why very deep networks are hard to train and how residuals help. |
| | S2 | Modern architectures overview: Inception/GoogLeNet (multi-scale), depthwise separable convolutions (MobileNet). |
| | S3 | Transfer learning: pretraining + fine-tuning. Feature extraction vs. fine-tuning. |
| | S4 | Problem-solving session. Compute output sizes, parameter counts for CNN architectures. |

**Handout:** CNN mathematics. Architecture comparison table. Parameter counting guide.
**Paper:** See paper roadmap Weeks 22–23.
**Quiz topics:** Compute conv output size. Why do residual connections help? What is transfer learning? Why not use MLPs for images?

---

### Week 28–29: Sequence Models — RNNs, LSTMs, and Attention

| Week | Session | Topics |
|------|---------|--------|
| W28 | S1 | Sequential data: time series, text. Why feedforward networks fail (no temporal structure, variable length). |
| | S2 | Recurrent Neural Networks (RNNs): h_t = f(W_h h_{t-1} + W_x x_t + b). Unrolling through time. Backpropagation through time (BPTT). The vanishing gradient problem in RNNs. |
| | S3 | LSTM: the cell state, input gate, forget gate, output gate. How LSTMs mitigate vanishing gradients. GRU as a simplification. |
| | S4 | Problem-solving session. Trace an RNN forward. Identify gate computations. |
| W29 | S1 | The attention mechanism: query, key, value. Attention as weighted retrieval. Scaled dot-product attention: Attention(Q,K,V) = softmax(QK^T/√d_k)V. |
| | S2 | Self-attention: attending to one's own sequence. Multi-head attention: multiple representation subspaces. |
| | S3 | Positional encoding: why attention needs position information. Sinusoidal encodings. Learned positional embeddings. |
| | S4 | The Transformer architecture: encoder, decoder, encoder-decoder attention. The "Attention is All You Need" architecture walkthrough. |

**Handout:** RNN/LSTM equations. Attention mechanism derivation. Transformer architecture diagram walkthrough.
**Paper:** See paper roadmap Weeks 24–25.
**Quiz topics:** Write the RNN update equation. How does an LSTM forget gate work? Write scaled dot-product attention. Why is there a √d_k scaling? What is multi-head attention?

---

### Week 30–31: Generative Models

| Week | Session | Topics |
|------|---------|--------|
| W30 | S1 | Generative vs. discriminative models. The taxonomy: explicit vs. implicit, tractable vs. approximated. |
| | S2 | Autoencoders: encoder z = f(x), decoder x̂ = g(z), loss = ‖x - x̂‖². Denoising autoencoders. Variational autoencoders (VAE): the variational lower bound (ELBO). Reparameterization trick. |
| | S3 | VAE continued: the KL divergence term and reconstruction term. The trade-off (β-VAE). |
| | S4 | Problem-solving session. Derive ELBO. |
| W31 | S1 | Generative Adversarial Networks (GANs): generator G, discriminator D. The minimax game: min_G max_D E[log D(x)] + E[log(1 - D(G(z)))]. |
| | S2 | GAN training dynamics: the Nash equilibrium. Mode collapse. Wasserstein GAN (intuition: use Wasserstein distance instead of JS divergence for better gradients). |
| | S3 | Diffusion models (conceptual): forward process (add noise), reverse process (learn to denoise). The DDPM formulation. Connection to score matching. |
| | S4 | Comparison: VAEs vs. GANs vs. Diffusion. Strengths and weaknesses. |

**Handout:** Generative model taxonomy. VAE ELBO derivation. GAN minimax derivation. Diffusion model overview.
**Paper:** See paper roadmap Weeks 26–27.
**Quiz topics:** Derive the ELBO. Write the GAN minimax objective. What is mode collapse? How does a diffusion model work (forward/reverse)?

---

### Week 32–33: Reinforcement Learning

| Week | Session | Topics |
|------|---------|--------|
| W32 | S1 | RL setup: agent, environment, state, action, reward, policy. MDP formalism: (S, A, P, R, γ). Episodes, returns, discounting. |
| | S2 | Value functions: V^π(s) (state value), Q^π(s,a) (action value). The Bellman equations (expectation form). Bellman optimality equations. |
| | S3 | Policy evaluation: iterative policy evaluation. Policy improvement: greedy policy. Policy iteration. Value iteration. |
| | S4 | Problem-solving session. Compute value iteration on a small gridworld. |
| W33 | S1 | Q-learning: off-policy TD learning. The Q-learning update rule. Exploration: ε-greedy, softmax. |
| | S2 | Deep Q-Networks (DQN): Q(s,a) approximated by a neural network. Experience replay. Target network. Why these stabilize training. |
| | S3 | Policy gradient methods: REINFORCE algorithm. The policy gradient theorem (derivation). The log-derivative trick. Actor-Critic methods (overview). PPO (overview). |
| | S4 | RLHF (Reinforcement Learning from Human Feedback): the three steps (SFT, reward model, PPO optimization). How ChatGPT uses RLHF. |

**Handout:** RL equation sheet. MDP examples. Q-learning algorithm. Policy gradient theorem derivation. RLHF pipeline.
**Paper:** See paper roadmap Weeks 28–29.
**Quiz topics:** Write the Bellman equation. What is the difference between policy iteration and value iteration? Write the Q-learning update. Derive the policy gradient theorem. Explain the three steps of RLHF.

---

### Week 34: Representation Learning & Embeddings

| Session | Topics |
|---------|--------|
| S1 | What is a representation? Learning useful features. Word embeddings: Word2Vec (skip-gram and CBOW). The distributional hypothesis. |
| S2 | Word2Vec training: negative sampling. The embedding matrix. GloVe (count-based vs. prediction-based). |
| S3 | Contrastive learning (SimCLR, CLIP): learn representations by contrasting positive vs. negative pairs. The InfoNCE loss. |
| S4 | Dimensionality reduction revisited: UMAP, autoencoder-based reduction. The manifold hypothesis. |

**Handout:** Embedding methods overview. Contrastive learning loss functions.
**Paper:** See paper roadmap Week 30.
**Quiz topics:** What is the distributional hypothesis? How does Word2Vec skip-gram work? What is contrastive learning? What is the InfoNCE loss?

---

### Week 35: Large Language Models & The Transformer Era

| Session | Topics |
|---------|--------|
| S1 | Scaling laws: model size, data size, compute — how loss scales (power laws). The emergent abilities of large models. |
| | S2 | The decoder-only Transformer (GPT family): causal/masked self-attention, autoregressive generation. Tokenization (BPE). |
| | S3 | Training pipeline for LLMs: pretraining (next-token prediction), supervised fine-tuning (SFT), RLHF. Instruction tuning. |
| | S4 | The BERT family: encoder-only, masked language modeling. Bidirectional context. BERT vs. GPT comparison. |

**Handout:** LLM training pipeline. Transformer architecture variants (encoder-only, decoder-only, encoder-decoder).
**Paper:** See paper roadmap Week 31.
**Quiz topics:** What are scaling laws? Explain the three training stages of an LLM. Compare BERT and GPT. What is causal self-attention?

---

### Week 36: Phase 4 Consolidation & Advanced Topics Seminar

| Session | Topics |
|---------|--------|
| S1 | The unified view: all ML as "model + loss + optimizer + data." How CNNs, RNNs, Transformers, GANs, VAEs, and RL fit this mold. |
| S2 | Advanced topics lightning talks (students present a 5-min summary of a self-chosen topic). |
| S3 | Ethics and societal impact: bias in ML, fairness, privacy, environmental cost. Responsible AI. |
| S4 | Phase 4 comprehensive review. |

**Handout:** Phase 4 summary. The unified ML framework.
**Paper:** See paper roadmap Week 32.

---

## PHASE 5: IOAI Competition Preparation (Weeks 37–44, 4 sessions/week)

### Week 37–38: IOAI Format & Strategy

| Week | Session | Topics |
|------|---------|--------|
| W37 | S1 | IOAI competition structure: theory round, practical round. What to expect. Time management strategy. |
| | S2 | Topic mapping: which IOAI topics map to which course weeks. Quick self-assessment. |
| | S3 | Past IOAI / similar competition problems — start solving. |
| | S4 | Continue problem solving. |
| W38 | S1–S4 | Intensive problem-solving sessions. Past competition problems. Focus on speed and accuracy. |

**Handout:** IOAI competition guide. Self-assessment checklist.
**Paper:** See paper roadmap Weeks 33–34.

---

### Week 39–40: Advanced Topics for IOAI

| Week | Session | Topics |
|------|---------|--------|
| W39 | S1 | Advanced optimization: second-order methods (Newton's method), conjugate gradient. |
| | S2 | Probabilistic ML: Bayesian linear regression, Gaussian processes (conceptual). |
| | S3 | Graph neural networks (conceptual): message passing, spectral vs. spatial methods. |
| | S4 | Problem-solving. |
| W40 | S1 | Advanced computer vision: object detection (YOLO concept), image segmentation. |
| | S2 | Advanced NLP: attention variants, efficient transformers, retrieval-augmented generation (RAG). |
| | S3 | Multi-modal learning: vision-language models. |
| | S4 | Problem-solving. |

**Handout:** Advanced topics reference sheets.
**Paper:** See paper roadmap Weeks 35–36.

---

### Week 41–43: Full Mock IOAI Exams

| Week | Sessions |
|------|----------|
| W41 | 2× mock theory exams (80 min each) + 2× review sessions |
| W42 | 2× mock theory exams (80 min each) + 2× review sessions |
| W43 | 2× mock theory exams (80 min each) + 2× review sessions |

Each review session: detailed solution walkthrough, mistake analysis, targeted re-teaching.

---

### Week 44: Final Review & Confidence Building

| Session | Topics |
|---------|--------|
| S1 | "One-page cheat sheet" creation: each student creates their own summary of all ML. |
| S2 | Final Q&A. Address any remaining gaps. |
| S3 | Competition mindset: staying calm, strategic guessing, partial credit. |
| S4 | Course reflection. What they've learned. Life-long learning in ML. |

**Handout:** Master cheat sheet template. Final advice document.
**Paper:** See paper roadmap Week 37.

---

## Topic Coverage Summary

### Exam-Critical Topics (must be solid before Week 21):

- [x] Linear regression (OLS, ridge, GD)
- [x] Logistic regression (binary + multinomial)
- [x] Gradient descent, SGD
- [x] MLE / MAP
- [x] Bias-variance tradeoff
- [x] Overfitting, regularization (L1, L2)
- [x] Cross-validation, evaluation metrics
- [x] k-NN
- [x] Decision trees, random forests
- [x] SVM (linear, kernels, soft margin)
- [x] Neural networks (MLP, forward, backprop)
- [x] Training: optimizers, initialization, dropout
- [x] k-means, GMM/EM
- [x] PCA
- [x] Information theory: entropy, KL, cross-entropy

### Advanced Topics (post-exam):

- [x] CNNs (convolution, pooling, ResNet)
- [x] RNNs, LSTMs
- [x] Attention and Transformers
- [x] VAEs
- [x] GANs
- [x] Diffusion models
- [x] Reinforcement learning (MDP, Q-learning, policy gradients)
- [x] RLHF
- [x] Word embeddings, contrastive learning
- [x] Large language models
- [x] Scaling laws
- [x] Bayesian methods (conceptual)
- [x] GNNs (conceptual)
- [x] Multi-modal learning (conceptual)
