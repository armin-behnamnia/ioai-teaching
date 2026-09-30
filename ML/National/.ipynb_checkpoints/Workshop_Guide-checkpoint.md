# Machine Learning Workshop Guide
## AI Olympiad — From Scratch Implementation

**Instructor:** Workshop Lead
**Audience:** AI Olympiad participants
**Prerequisites:** Python, basic linear algebra, basic calculus, basic probability

---

## Table of Contents

1. [Introduction to Machine Learning](#1-introduction-to-machine-learning)
2. [Linear Regression](#2-linear-regression)
3. [Gradient Descent](#3-gradient-descent)
4. [Logistic Regression](#4-logistic-regression)
5. [The Perceptron](#5-the-perceptron)
6. [Generalization: Overfitting, Underfitting & Bias-Variance](#6-generalization-overfitting-underfitting--bias-variance)
7. [Regularization](#7-regularization)
8. [Multi-Layer Perceptron (MLP)](#8-multi-layer-perceptron-mlp)
9. [Decision Trees](#9-decision-trees)
10. [Ensemble Methods](#10-ensemble-methods)
11. [Workshop Schedule](#11-workshop-schedule)
12. [Required Libraries](#12-required-libraries)

---

## 1. Introduction to Machine Learning

### 1.1 What is Machine Learning?

> *"A computer program is said to learn a task from experience if its performance improves with experience."* — Tom Mitchell (1998)

The essence of machine learning:
- A **pattern** exists in the data.
- We **cannot** describe it mathematically (otherwise we'd just write a formula).
- We **have data** to learn from.

### 1.2 Components of Learning

Every supervised learning problem has these components:

| Component | Description |
|---|---|
| **Unknown target function** `t: X → Y` | The true relationship we want to learn |
| **Training examples** `D = {(x⁽¹⁾, y⁽¹⁾), ..., (x⁽ⁿ⁾, y⁽ⁿ⁾)}` | Observed data |
| **Hypothesis set** `H = {h}` | The family of functions we consider |
| **Learning algorithm** | Searches H for the best `g ≈ t` |
| **Final hypothesis** `g ∈ H` | Our learned model |

### 1.3 ML Paradigms

| Paradigm | Input | Feedback | Example |
|---|---|---|---|
| **Supervised** | input, correct output | Full label | Heart attack risk prediction |
| **Unsupervised** | input, ? | No labels | Clustering, customer segmentation |
| **Reinforcement** | input, some output, grade | Partial/reward | AlphaZero, autonomous driving |
| **Semi-supervised** | input, few labels | Mixed | Protein function prediction |
| **Active learning** | input, ? (queries) | Selective | Medical diagnosis with expert queries |

### 1.4 Feature Representation

Before learning, we must represent data as numerical vectors. Example: a protein sequence of 1000 amino acids can be represented as 1000 one-hot vectors, forming a feature matrix.

---

## 2. Linear Regression

### 2.1 Problem Setup

**Goal:** Predict a continuous target `y` from input features `x`.

**Hypothesis (linear model):**

```
h_w(x) = w₀ + w₁x₁ + w₂x₂ + ... + w_d·x_d = wᵀx
```

where we set `x₀ = 1` (intercept term) and `w = [w₀, w₁, ..., w_d]ᵀ`.

### 2.2 Cost Function: Sum of Squared Errors (SSE)

```
J(w) = Σᵢ₌₁ⁿ (y⁽ⁱ⁾ - h_w(x⁽ⁱ⁾))² = Σᵢ₌₁ⁿ (y⁽ⁱ⁾ - wᵀx⁽ⁱ⁾)²
```

In matrix form:

```
J(w) = ‖y - Xw‖²
```

where `X` is the design matrix (n × (d+1)) and `y` is the target vector (n × 1).

### 2.3 Closed-Form Solution (Normal Equations)

Taking the gradient and setting to zero:

```
∇_w J(w) = -2Xᵀ(y - Xw) = 0
⟹ XᵀXw = Xᵀy
⟹ w = (XᵀX)⁻¹ Xᵀy
```

**Caveat:** `XᵀX` must be invertible. If features are collinear, use pseudo-inverse or regularization.

### 2.4 Univariate vs. Multivariate

| Type | Hypothesis | Input Space |
|---|---|---|
| Univariate | `h(x) = w₀ + w₁x` | `x ∈ ℝ` |
| Multivariate | `h(x) = w₀ + w₁x₁ + ... + w_d·x_d` | `x ∈ ℝᵈ` |

### 2.5 Key Concepts
- **Convexity:** SSE with linear hypothesis is convex → unique global minimum.
- **Design matrix:** Each row is a training example with a prepended `1` for the bias.

---

## 3. Gradient Descent

### 3.1 The Algorithm

When closed-form solutions are infeasible (high dimensions, non-convex costs, large datasets), we use **iterative optimization**.

```
Initialize w₀
Repeat:
    w_{t+1} = w_t - η ∇_w J(w_t)
    t ← t + 1
Until convergence
```

where `η` is the **learning rate** (step size).

### 3.2 Intuition

- The gradient `∇J(w)` points in the direction of steepest **ascent**.
- We move in the **opposite** direction to descend the cost surface.
- `J(w)` decreases fastest in the direction of `-∇J(w)`.

### 3.3 Learning Rate

| η too small | η too large | η just right |
|---|---|---|
| Slow convergence | May overshoot, diverge | Steady convergence |

- `η` can be fixed or adaptive (`η_t`).
- If `η` is small enough, then `J(w_{t+1}) ≤ J(w_t)` is guaranteed.

### 3.4 Batch Gradient Descent (for Linear Regression)

Weight update rule:

```
w_{t+1} = w_t + η Σᵢ₌₁ⁿ (y⁽ⁱ⁾ - wᵀx⁽ⁱ⁾) x⁽ⁱ⁾
```

**Batch mode:** each step considers **all** training data.

### 3.5 Variants

| Variant | Update uses | Pros | Cons |
|---|---|---|---|
| **Batch GD** | All n samples | Stable | Slow on large data |
| **Stochastic GD (SGD)** | 1 random sample | Fast, escapes local minima | Noisy |
| **Mini-batch GD** | k samples (e.g. 32) | Balance of both | Need to tune batch size |

### 3.6 Local Minima Problem

- For **convex** cost functions (e.g., linear regression with SSE), all local minima are global minima → GD converges to global optimum.
- For **non-convex** costs (e.g., neural networks), GD may get stuck in local minima.

---

## 4. Logistic Regression

### 4.1 Classification Problem

**Goal:** Predict a discrete label (e.g., binary: yes/no, +1/-1).

### 4.2 Sigmoid Function

Instead of a raw linear output, we apply the **sigmoid** (logistic) function:

```
h_w(x) = σ(wᵀx) = 1 / (1 + exp(-wᵀx))
```

This squashes the output to `(0, 1)`, interpretable as `P(y=1 | x)`.

### 4.3 Cross-Entropy Loss

```
J(w) = -Σᵢ₌₁ⁿ [y⁽ⁱ⁾ log(h_w(x⁽ⁱ⁾)) + (1 - y⁽ⁱ⁾) log(1 - h_w(x⁽ⁱ⁾))]
```

- This is **convex** in `w` → GD finds global optimum.
- The gradient has a clean form: `∇_w J = Σᵢ (h_w(x⁽ⁱ⁾) - y⁽ⁱ⁾) x⁽ⁱ⁾`

### 4.4 Decision Boundary

- Classify as `1` if `h_w(x) ≥ 0.5` (i.e., `wᵀx ≥ 0`), else `0`.
- The boundary is a **hyperplane** in feature space.

### 4.5 Multi-class Extension

- **One-vs-Rest (OvR):** Train K binary classifiers.
- **Softmax (Multinomial):** Generalize sigmoid to K classes.

---

## 5. The Perceptron

### 5.1 The Model

The perceptron is the simplest linear classifier:

```
h(x) = sign(wᵀx)
```

where `x₀ = 1` absorbs the threshold/bias.

### 5.2 Learning Algorithm

```
Repeat:
    Pick a misclassified point (x⁽ⁱ⁾, y⁽ⁱ⁾) where sign(wᵀx⁽ⁱ⁾) ≠ y⁽ⁱ⁾
    Update: w ← w + y⁽ⁱ⁾ x⁽ⁱ⁾
Until all training points are correctly classified
```

### 5.3 Properties
- **Convergence guarantee:** If data is linearly separable, the perceptron converges in finite steps.
- **Limitation:** If data is not linearly separable, the algorithm never converges.
- **Historical significance:** Building block of neural networks.

---

## 6. Generalization: Overfitting, Underfitting & Bias-Variance

### 6.1 Training Error vs. Test Error

- **Training error:** Error on the data the model was trained on.
- **Test error:** Error on **unseen** data. This is what matters most.
- The test error is not necessarily close to the training error.

### 6.2 Overfitting

> Training error is small but test error is large.

The model **memorizes** the training data, including noise, and fails to generalize.

### 6.3 Underfitting

> Training error is large (and typically test error is also large).

The model is too simple to capture the underlying pattern.

### 6.4 Bias-Variance Tradeoff

Given a true target function `t(x)` with noise `y = t(x) + ε`:

| Concept | Definition |
|---|---|
| **Bias** | Error from wrong assumptions. High bias → underfitting. The test error when trained on infinite data. |
| **Variance** | Sensitivity to training set. High variance → overfitting. Variation across models trained on different datasets from the same distribution. |

**Tradeoff:**
- **Simple model** (few parameters): High bias, low variance → underfitting.
- **Complex model** (many parameters): Low bias, high variance → overfitting.

**Example:** Fitting a linear model to quadratic data → high bias (underfitting). Fitting a 5th-degree polynomial to a few points → high variance (overfitting).

### 6.5 The Fundamental Goal

> We don't intend to memorize data but want to distinguish the **pattern**. A core objective of learning is to **generalize** from experience.

---

## 7. Regularization

### 7.1 Motivation

To combat overfitting, we add a **penalty term** to the cost function:

```
J_regularized(w) = J(w) + λ · R(w)
```

where `λ` controls the strength of regularization.

### 7.2 L2 Regularization (Ridge / Weight Decay)

```
R(w) = ‖w‖² = Σⱼ wⱼ²
```

- Shrinks weights toward zero (but never exactly zero).
- In deep learning, called **weight decay**.
- Closed-form for linear regression: `w = (XᵀX + λI)⁻¹ Xᵀy` (always invertible).

### 7.3 L1 Regularization (Lasso)

```
R(w) = ‖w‖₁ = Σⱼ |wⱼ|
```

- Can drive weights to **exactly zero** → feature selection.
- Produces sparse models.

### 7.4 Regularization in Deep Learning

| Technique | Description |
|---|---|
| **Weight decay (L2)** | Penalize large weights in the loss |
| **Dropout** | Randomly zero out neurons during training; prevents co-adaptation |
| **Early stopping** | Stop training when validation loss starts increasing |
| **Data augmentation** | Artificially expand training data with transformations |
| **Batch normalization** | Normalize layer inputs; stabilizes training and acts as mild regularizer |

### 7.5 Choosing λ

- Use **cross-validation** to find the best `λ`.
- Large `λ` → underfitting (too much regularization).
- Small `λ` → overfitting (too little regularization).

---

## 8. Multi-Layer Perceptron (MLP)

### 8.1 Architecture

```
Input Layer → Hidden Layer(s) → Output Layer
```

Each layer:
```
z = W·a_prev + b
a = activation(z)
```

### 8.2 Activation Functions

| Function | Formula | Range | Use |
|---|---|---|---|
| **Sigmoid** | `σ(z) = 1/(1+e⁻ᶻ)` | (0, 1) | Binary classification output |
| **Tanh** | `tanh(z) = (eᶻ - e⁻ᶻ)/(eᶻ + e⁻ᶻ)` | (-1, 1) | Hidden layers |
| **ReLU** | `max(0, z)` | [0, ∞) | Hidden layers (default choice) |
| **Softmax** | `eᶻᵢ / Σⱼ eᶻⱼ` | (0, 1), sums to 1 | Multi-class output |

### 8.3 Forward Propagation

For layer `l`:
```
z⁽ˡ⁾ = W⁽ˡ⁾ a⁽ˡ⁻¹⁾ + b⁽ˡ⁾
a⁽ˡ⁾ = f(z⁽ˡ⁾)
```

### 8.4 Backpropagation

Using the chain rule, compute gradients of the loss w.r.t. all weights:

```
δ⁽ᴸ⁾ = ∇_a L ⊙ f'(z⁽ᴸ⁾)          (output layer error)
δ⁽ˡ⁾ = (W⁽ˡ⁺¹⁾)ᵀ δ⁽ˡ⁺¹⁾ ⊙ f'(z⁽ˡ⁾)  (hidden layer error)
∂L/∂W⁽ˡ⁾ = δ⁽ˡ⁾ (a⁽ˡ⁻¹⁾)ᵀ
∂L/∂b⁽ˡ⁾ = δ⁽ˡ⁾
```

Update: `W ← W - η · ∂L/∂W`

### 8.5 MLP for Classification vs. Regression

| Task | Output Activation | Loss Function |
|---|---|---|
| Binary classification | Sigmoid | Binary cross-entropy |
| Multi-class classification | Softmax | Categorical cross-entropy |
| Regression | Linear (identity) | Mean squared error |

### 8.6 Why Non-Linearity Matters

Without activation functions, an MLP collapses to a single linear transformation. Non-linear activations allow learning complex, non-linear decision boundaries.

---

## 9. Decision Trees

### 9.1 Concept

A tree-like structure where:
- Each **internal node** tests a feature.
- Each **branch** represents a test outcome.
- Each **leaf** gives a prediction.

### 9.2 Building a Tree (Top-Down, Greedy)

1. Start with all data at the root.
2. Find the best feature and split point that **best separates** the classes (or reduces variance for regression).
3. Split data into subsets.
4. Recurse on each subset.
5. Stop when: pure node, max depth reached, or too few samples.

### 9.3 Split Criteria (Classification)

| Criterion | Formula | Description |
|---|---|---|
| **Gini Impurity** | `1 - Σₖ pₖ²` | Probability of misclassification |
| **Entropy** | `-Σₖ pₖ log₂ pₖ` | Information content |
| **Information Gain** | `Entropy(parent) - weighted avg Entropy(children)` | Reduction in entropy |

### 9.4 Split Criteria (Regression)

- **Variance reduction:** Split that minimizes weighted average variance of children.

### 9.5 Properties

| Pros | Cons |
|---|---|
| Interpretable | Prone to overfitting |
| Handles mixed data types | Unstable (small data changes → different tree) |
| No feature scaling needed | Greedy → not globally optimal |
| Non-linear boundaries | |

### 9.6 Pruning

- **Pre-pruning:** Stop early (max depth, min samples per leaf).
- **Post-pruning:** Grow full tree, then remove subtrees that don't improve validation performance.

---

## 10. Ensemble Methods

### 10.1 Motivation

> "Wisdom of the crowd" — combine multiple weak learners into a strong learner.

### 10.2 Bagging (Bootstrap Aggregating)

- Train **multiple** models on **bootstrap samples** (random samples with replacement).
- Aggregate predictions: **majority vote** (classification) or **average** (regression).
- Reduces **variance** without increasing bias.

### 10.3 Random Forest

A bagging ensemble of **decision trees** with extra randomness:
- At each split, only consider a **random subset of features**.
- This decorrelates trees, further reducing variance.

### 10.4 Boosting

Train models **sequentially**, each focusing on the **errors** of the previous ones:
- Each new model corrects mistakes of the ensemble so far.
- Reduces **bias** (and sometimes variance).

| Method | Description |
|---|---|
| **AdaBoost** | Reweight misclassified samples; combine with weighted vote |
| **Gradient Boosting** | Fit new models to **residuals** (negative gradient of loss) |

### 10.5 Comparison

| Property | Bagging | Boosting |
|---|---|---|
| Training | Parallel | Sequential |
| Focus | Reduce variance | Reduce bias |
| Base learner | Usually high-variance (deep trees) | Usually high-bias (shallow trees) |
| Overfitting risk | Low | Higher (especially boosting) |

---

## 11. Workshop Schedule

| Session | Topic | Duration |
|---|---|---|
| **Session 1** | ML Intro, Paradigms, Linear Regression (closed-form) | 2 hours |
| **Session 2** | Gradient Descent, Learning Rate, Convergence | 2 hours |
| **Session 3** | Logistic Regression, Perceptron | 2 hours |
| **Session 4** | Generalization, Bias-Variance, Overfitting/Underfitting | 1.5 hours |
| **Session 5** | Regularization (L1, L2, Dropout, Early Stopping) | 1.5 hours |
| **Session 6** | MLP: Forward Prop, Backprop, Activations | 3 hours |
| **Session 7** | MLP Classification & Regression (from scratch) | 3 hours |
| **Session 8** | Decision Trees (from scratch) | 2 hours |
| **Session 9** | Ensemble Methods: Bagging, Random Forest, AdaBoost | 3 hours |
| **Session 10** | Mini-Competition / Review | 2 hours |

**Total:** ~22 hours

---

## 12. Required Libraries

The entire workshop is implemented **from scratch** using only:

```
numpy      # Numerical computation (arrays, matrix ops)
matplotlib # Plotting
```

No sklearn, no tensorflow, no pytorch. Students learn the **mathematics and algorithms** by implementing every line themselves.

---

## References

1. Abu-Mostafa, Y. S., Magdon-Ismail, M., & Lin, H. T. *Learning From Data*. AMLBook.
2. Bishop, C. M. *Pattern Recognition and Machine Learning*. Springer.
3. Goodfellow, I., Bengio, Y., & Courville, A. *Deep Learning*. MIT Press.
4. Hastie, T., Tibshirani, R., & Friedman, J. *The Elements of Statistical Learning*. Springer.
5. Seyyedsalehi, F. *Introduction to Machine Learning* (lecture slides).
6. Seyyedsalehi, F. *Linear Regression and Gradient Descent* (lecture slides).
7. Seyyedsalehi, F. *Generalization* (lecture slides).
