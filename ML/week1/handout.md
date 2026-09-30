# Week 1 Handout: What is Machine Learning?

> **Course:** Machine Learning for IOAI Preparation  
> **Week:** 1 of 44  
> **Sessions:** 2 (80 min each)  
> **Prerequisites:** None — this is where we begin.

---

## 1. Motivation

### 1.1 What Does It Mean to "Learn"?

Consider the following scenarios:

- A child sees ten cats and ten dogs. After that, they can correctly classify new animals they've never seen before.
- A chess player loses a game due to a bad opening. In the next game, they avoid that opening.
- A spam filter receives thousands of emails labeled "spam" or "not spam." After that, it can filter new emails automatically.

In each case, **experience improves performance on a task**. This is the essence of learning. Machine Learning is the field that studies how to make computers do this.

> **Tom Mitchell (1997):** "A computer program is said to *learn* from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

**Example:** For the spam filter:
- Task T: classify emails as spam or not spam
- Experience E: a collection of labeled emails
- Performance P: percentage of emails correctly classified

### 1.2 Why Not Just Program the Rules?

For some problems, we can write explicit rules. For example, "if the subject line contains 'FREE MONEY,' mark as spam." But this approach fails when:

1. **Rules are too complex.** How do you write rules to distinguish a cat from a dog in an image? There's no simple if-then logic for pixel patterns.
2. **Rules are unknown.** Even experts may not be able to articulate how they make a medical diagnosis.
3. **The world changes.** Spammers adapt their tactics. A fixed rule set becomes obsolete.

Machine learning addresses these by **learning patterns from data** rather than requiring humans to specify all rules.

### 1.3 Real-World Examples

| Application | Input (X) | Output (Y) | Type |
|-------------|-----------|------------|------|
| Spam filter | Email text | Spam / Not spam | Supervised (classification) |
| House price prediction | House features (area, location, rooms) | Price | Supervised (regression) |
| Image recognition | Pixels | Object label | Supervised (classification) |
| Customer segmentation | Customer behavior data | Group label | Unsupervised (clustering) |
| Game playing (AlphaGo) | Board state | Move | Reinforcement learning |
| Machine translation | English sentence | French sentence | Supervised (sequence-to-sequence) |
| ChatGPT | Text prompt | Text response | Supervised + Reinforcement learning |

---

## 2. Mathematical Setup

Machine learning has a precise mathematical formulation. We'll build it piece by piece.

### 2.1 Notation Conventions

Throughout this course, we use the following notation:

| Symbol | Meaning | Example |
|--------|---------|---------|
| $\mathbf{x}$ | An input (feature vector) | $\mathbf{x} = [2100, 3, 2]^T$ (area, bedrooms, bathrooms) |
| $y$ | An output (target) | $y = 500000$ (price) |
| $(\mathbf{x}_i, y_i)$ | The $i$-th training example | The $i$-th house in our dataset |
| $\hat{y}$ | A prediction (what our model outputs) | $\hat{y} = 490000$ |
| $\mathcal{D}$ | Dataset | $\mathcal{D} = \{(\mathbf{x}_1, y_1), \ldots, (\mathbf{x}_n, y_n)\}$ |
| $n$ | Number of training examples | $n = 1000$ houses |
| $d$ | Number of features (input dimension) | $d = 3$ (area, bedrooms, bathrooms) |
| $\mathbf{X}$ | Design matrix ($n \times d$) | All inputs stacked as rows |
| $f$ | A model / function | $f(\mathbf{x}) = \mathbf{w}^T \mathbf{x} + b$ |
| $\theta$ | Parameters of the model | $\theta = \{\mathbf{w}, b\}$ |
| $L$ | Loss function | $L(\hat{y}, y) = (\hat{y} - y)^2$ |
| $\mathcal{H}$ | Hypothesis space | All linear functions of $\mathbf{x}$ |

> **Note on vectors:** Throughout this course, vectors are **column vectors**. So $\mathbf{x} \in \mathbb{R}^d$ means $\mathbf{x}$ is a $d \times 1$ matrix. We write $\mathbf{x} = [x_1, x_2, \ldots, x_d]^T$ where $T$ denotes transpose.

### 2.2 The Input Space and Output Space

We define:
- **Input space** $\mathcal{X}$: the set of all possible inputs. For house prediction, $\mathcal{X} = \mathbb{R}^3$ (area, bedrooms, bathrooms).
- **Output space** $\mathcal{Y}$: the set of all possible outputs. For house prediction, $\mathcal{Y} = \mathbb{R}$ (price). For spam detection, $\mathcal{Y} = \{0, 1\}$ (not spam, spam).

The goal is to find a function $f: \mathcal{X} \to \mathcal{Y}$ that maps inputs to outputs.

### 2.3 The Hypothesis Space

We can't search over **all possible functions** from $\mathcal{X}$ to $\mathcal{Y}$ — there are infinitely many. Instead, we restrict our search to a **hypothesis space** $\mathcal{H}$, which is a family of functions parameterized by $\theta$:

$$\mathcal{H} = \{f_\theta : \theta \in \Theta\}$$

where $\Theta$ is the parameter space.

**Example:** If we believe the relationship between house features and price is approximately linear:
$$f_\theta(\mathbf{x}) = w_1 x_1 + w_2 x_2 + w_3 x_3 + b$$

Then $\theta = (w_1, w_2, w_3, b)$ and $\mathcal{H}$ is the set of all linear functions. The learning problem becomes: **find the best $\theta$**.

> **Key insight:** The choice of $\mathcal{H}$ is a **modeling assumption**. It encodes our prior belief about what kind of function could map inputs to outputs. If $\mathcal{H}$ is too small, the true function might not be in it (underfitting). If $\mathcal{H}$ is too large, we might find a function that fits the training data but doesn't generalize (overfitting).

### 2.4 The Loss Function

How do we measure "best"? We need a **loss function** (also called cost function or objective function):

$$L: \mathcal{Y} \times \mathcal{Y} \to \mathbb{R}_{\geq 0}$$

The loss $L(\hat{y}, y)$ measures how bad the prediction $\hat{y}$ is compared to the true value $y$. A loss of 0 means perfect prediction.

**Common loss functions:**

| Loss | Formula | Used For |
|------|---------|----------|
| Squared error | $L(\hat{y}, y) = (\hat{y} - y)^2$ | Regression |
| Absolute error | $L(\hat{y}, y) = |\hat{y} - y|$ | Regression |
| 0-1 loss | $L(\hat{y}, y) = \mathbb{1}[\hat{y} \neq y]$ | Classification |
| Cross-entropy | $L(\hat{y}, y) = -y \log \hat{y} - (1-y)\log(1-\hat{y})$ | Classification (probabilistic) |

### 2.5 The Empirical Risk

On the training data, the **average loss** is called the **empirical risk** (or training loss):

$$R_{\text{emp}}(\theta) = \frac{1}{n} \sum_{i=1}^{n} L(f_\theta(\mathbf{x}_i), y_i)$$

The learning goal is:

$$\theta^* = \arg\min_{\theta \in \Theta} R_{\text{emp}}(\theta)$$

In words: **find the parameters that minimize the average loss on the training data.**

This principle is called **Empirical Risk Minimization (ERM)**.

### 2.6 The True Risk (and Why It Matters)

The empirical risk measures performance on **training data**. But we care about performance on **new, unseen data**. The **true risk** (also called expected risk or generalization error) is:

$$R(\theta) = \mathbb{E}_{(\mathbf{x}, y) \sim \mathcal{P}}[L(f_\theta(\mathbf{x}), y)]$$

where $\mathcal{P}$ is the true (unknown) joint distribution over inputs and outputs.

> **The fundamental challenge of ML:** We want to minimize $R(\theta)$, but we only have access to $R_{\text{emp}}(\theta)$ (computed on our finite sample). The gap between these two is the **generalization gap**.

We'll spend much of this course understanding when and why minimizing the empirical risk also leads to a small true risk.

---

## 3. The Three Types of Learning

### 3.1 Supervised Learning

**Setup:** We have labeled data $\mathcal{D} = \{(\mathbf{x}_1, y_1), \ldots, (\mathbf{x}_n, y_n)\}$.

**Goal:** Learn $f: \mathcal{X} \to \mathcal{Y}$.

Two sub-types:

| Sub-type | Output Space | Example |
|----------|-------------|---------|
| **Regression** | $\mathcal{Y} = \mathbb{R}$ | Predict house price |
| **Classification** | $\mathcal{Y} = \{1, 2, \ldots, K\}$ | Classify email as spam/not spam |

**The supervised learning pipeline:**

```
Training Data          Model                     Prediction
┌─────────────┐      ┌──────────────┐          ┌─────────────┐
│ (x₁, y₁)   │      │              │          │             │
│ (x₂, y₂)   │ ───→ │  f_θ(x)      │ ───→     │ ŷ = f_θ(x)  │
│  ...        │      │  (hypothesis)│          │             │
│ (xₙ, yₙ)   │      │              │          │             │
└─────────────┘      └──────────────┘          └─────────────┘
      ↑                     ↑                       ↑
   Experience            Task                   Performance
                          (find best θ)         (minimize loss)
```

### 3.2 Unsupervised Learning

**Setup:** We have unlabeled data $\mathcal{D} = \{\mathbf{x}_1, \ldots, \mathbf{x}_n\}$ (no $y$).

**Goal:** Find structure in the data.

| Task | Description | Example |
|------|-------------|---------|
| **Clustering** | Group similar examples | Customer segmentation |
| **Dimensionality reduction** | Find lower-dimensional representation | Visualize high-dim data |
| **Density estimation** | Estimate the data distribution P(x) | Generative models |

### 3.3 Reinforcement Learning

**Setup:** An **agent** interacts with an **environment** over time.

| Component | Description |
|-----------|-------------|
| State $s_t$ | Current situation |
| Action $a_t$ | What the agent does |
| Reward $r_t$ | Feedback (how good the action was) |
| Policy $\pi$ | Strategy: $\pi(a\|s)$ = which action to take in state $s$ |

**Goal:** Learn a policy $\pi$ that maximizes cumulative reward over time.

$$\max_\pi \mathbb{E}\left[\sum_{t=0}^{T} \gamma^t r_t\right]$$

where $\gamma \in [0, 1)$ is a discount factor (rewards sooner are worth more).

**Key difference from supervised learning:** There is no labeled "correct answer." The agent must **explore** to discover which actions lead to rewards.

---

## 4. The Supervised Learning Pipeline in Detail

Let's walk through the full pipeline for a concrete example: predicting house prices.

### Step 1: Define the Problem

- **Input** $\mathbf{x}$: house features — area (sq ft), number of bedrooms, number of bathrooms
- **Output** $y$: price (in dollars)
- **Type:** Supervised regression

### Step 2: Collect Data

Gather $n$ examples of houses with known features and sale prices:

$$\mathcal{D} = \left\{ \begin{pmatrix} 2100 \\ 3 \\ 2 \end{pmatrix}, 500000 \right\}, \left\{ \begin{pmatrix} 1400 \\ 2 \\ 1 \end{pmatrix}, 300000 \right\}, \ldots \right\}$$

### Step 3: Choose the Hypothesis Space

Assume a linear relationship:
$$f_\theta(\mathbf{x}) = w_1 x_1 + w_2 x_2 + w_3 x_3 + b = \mathbf{w}^T \mathbf{x} + b$$

Hypothesis space: $\mathcal{H} = \{\mathbf{w}^T \mathbf{x} + b : \mathbf{w} \in \mathbb{R}^3, b \in \mathbb{R}\}$

### Step 4: Choose the Loss Function

Use squared error:
$$L(\hat{y}, y) = (\hat{y} - y)^2$$

### Step 5: Define the Training Objective

Minimize the empirical risk (mean squared error):
$$R_{\text{emp}}(\mathbf{w}, b) = \frac{1}{n} \sum_{i=1}^{n} (\mathbf{w}^T \mathbf{x}_i + b - y_i)^2$$

### Step 6: Optimize

Find $(\mathbf{w}^*, b^*) = \arg\min_{(\mathbf{w}, b)} R_{\text{emp}}(\mathbf{w}, b)$.

(In Week 2, we'll solve this analytically. In Week 6, we'll solve it with gradient descent.)

### Step 7: Evaluate

Test the model on **new data** that wasn't used for training. If the predictions are good on new data, the model **generalizes**.

### Step 8: Deploy and Monitor

Use the model to predict prices of new houses. Monitor performance over time; retrain if the data distribution shifts.

---

## 5. The Concept of Generalization

### 5.1 Training vs. Generalization

A model can perfectly fit the training data and still be useless. Consider:

```
Overfitting Example:
                        
Data points: • • • • •     (true pattern: roughly linear)
                          
Underfit:    ──────────     (linear, but wrong slope — high bias)
Good fit:      ────         (linear, right slope — balanced)  
Overfit:    ╱╲╱╲╱╲╱╲       (wiggly curve through every point — fits noise)
```

- **Underfitting:** The model is too simple. It can't capture the true pattern. Both training and test loss are high.
- **Overfitting:** The model is too complex. It memorizes the training data, including noise. Training loss is low, but test loss is high.
- **Good fit:** The model captures the true pattern without fitting noise. Both training and test loss are reasonable.

### 5.2 The Overfitting-Underfitting Tradeoff (Preview)

This is the most important conceptual idea in ML. We'll do the full mathematical treatment (called the "bias-variance decomposition") in Week 5, after we've studied probability. For now, the intuition:

| | Low Complexity Model | High Complexity Model |
|---|---|---|
| **Training error** | High | Low |
| **Test error** | High | Can be high (overfitting) |
| **Sensitive to data?** | No (stable but wrong) | Yes (changes drastically with different training data) |

- A **too-simple model** is consistently wrong — it misses the pattern. It's stable but inaccurate.
- A **too-complex model** is unstable — it fits the noise in one dataset but would fit different noise in another. It's accurate on training data but unreliable on new data.

The art of ML is finding the **sweet spot** — a model complex enough to capture the true pattern, but not so complex that it fits noise.

### 5.3 How to Combat Overfitting (Preview)

| Technique | Idea | When We'll Cover It |
|-----------|------|---------------------|
| More data | More examples → noise averages out | Throughout |
| Simpler model | Restrict $\mathcal{H}$ | Week 2 (ridge), Week 10 (tree depth) |
| Regularization | Penalize complex models | Week 2 (L2), Week 13–14 (SVM C) |
| Cross-validation | Estimate test error to choose model | Week 4 |
| Early stopping | Stop training before overfitting | Week 17 |
| Dropout | Randomly deactivate neurons | Week 17 |

---

## 6. The Triality of Machine Learning

Every supervised ML problem can be viewed from three perspectives. This is a central theme of the course:

### Perspective 1: Geometric

The model $f_\theta(\mathbf{x})$ defines a **surface** in the input-output space. Learning means finding the surface that best fits the data points.

```
   y
   │      •
   │    • ──── (model surface)
   │  •
   │•
   └──────── x
```

### Perspective 2: Probabilistic

The data is generated by some unknown distribution $P(\mathbf{x}, y)$. Learning means estimating this distribution (or the conditional $P(y|\mathbf{x})$). The loss function often comes from a probabilistic assumption (Week 5: MLE).

### Perspective 3: Optimization

Learning is an **optimization problem**: minimize some objective function over the parameter space. The geometry of this objective (convex vs. non-convex) determines how hard it is to solve (Week 6: gradient descent).

```
┌─────────────────────────────────────────────────┐
│                                                   │
│   GEOMETRY              PROBABILITY              │
│   (model surface)       (data distribution)      │
│        \                     /                   │
│         \                   /                    │
│          \                 /                     │
│           \               /                      │
│            \             /                       │
│             \           /                        │
│              \         /                         │
│               \       /                          │
│                \     /                           │
│                 \   /                            │
│                  \ /                             │
│                   X                              │
│            OPTIMIZATION                          │
│            (minimize loss)                       │
│                                                   │
└─────────────────────────────────────────────────┘
```

We'll see this triality concretely in Week 2: linear regression as (1) projection, (2) MLE under Gaussian noise, (3) a convex optimization problem.

---

## 7. Connections

### What This Week Enables

| Next Week | How It Uses Week 1 |
|-----------|-------------------|
| Week 2: Linear Regression | We'll instantiate the full pipeline for the first concrete model |
| Week 3: Overfitting & Regularization | We'll go deeper into overfitting and the complexity dial |
| Week 4: Model Evaluation | We'll learn how to properly measure generalization |
| Week 5: Probability for ML | We'll derive the loss function from probability (MLE/MAP) |
| Week 6: Gradient Descent | We'll solve the optimization problem iteratively |
| Week 7: Logistic Regression | We'll apply the same pipeline to classification |

### Key Vocabulary to Master

Make sure you can define each of these in one sentence:

- [ ] Supervised learning
- [ ] Unsupervised learning
- [ ] Reinforcement learning
- [ ] Regression vs. classification
- [ ] Feature vector
- [ ] Label / target
- [ ] Hypothesis space
- [ ] Loss function
- [ ] Empirical risk
- [ ] True risk / generalization error
- [ ] Overfitting
- [ ] Underfitting
- [ ] Overfitting-underfitting tradeoff (formal "bias-variance" treatment in Week 5)
- [ ] Parameter
- [ ] Training set / test set
- [ ] Prediction

---

## 8. Worked Examples

### Example 1: Identifying the Type of Learning

For each scenario, identify: (a) the type of learning, (b) the input $\mathbf{x}$, (c) the output $y$, (d) the loss function (qualitatively).

**Scenario A:** A Netflix algorithm recommends movies. It has data of which movies each user has watched and rated.

- **Type:** Supervised (rating prediction) or unsupervised (clustering similar users)
- **Input $\mathbf{x}$:** User features + movie features
- **Output $y$:** Rating (1–5 stars) — if supervised
- **Loss:** Squared error between predicted and actual rating

**Scenario B:** A robot learns to walk by trial and error in a simulator.

- **Type:** Reinforcement learning
- **Input $\mathbf{x}$ (state $s$):** Robot joint angles, velocities, ground contact
- **Output $y$ (action $a$):** Torques to apply to joints
- **Loss (negative reward):** Negative distance walked (+ penalty for falling)

**Scenario C:** A bank has transaction data and wants to identify groups of similar customers.

- **Type:** Unsupervised (clustering)
- **Input $\mathbf{x}$:** Transaction features (amount, frequency, merchant type, time)
- **Output $y$:** None — the algorithm finds groups
- **Loss:** Within-cluster variance (e.g., k-means objective — we'll see this in Week 18)

### Example 2: Computing Empirical Risk

Given the following dataset:

| $i$ | $x_i$ | $y_i$ |
|-----|-------|-------|
| 1 | 1 | 3 |
| 2 | 2 | 5 |
| 3 | 3 | 7 |

And model $f(x) = 2x + 1$ (so $w = 2, b = 1$).

**Compute the empirical risk using squared error:**

$$\hat{y}_i = f(x_i) = 2x_i + 1$$

| $i$ | $x_i$ | $y_i$ | $\hat{y}_i$ | $L(\hat{y}_i, y_i) = (\hat{y}_i - y_i)^2$ |
|-----|-------|-------|-------------|------------------------------------------|
| 1 | 1 | 3 | $2(1)+1=3$ | $(3-3)^2 = 0$ |
| 2 | 2 | 5 | $2(2)+1=5$ | $(5-5)^2 = 0$ |
| 3 | 3 | 7 | $2(3)+1=7$ | $(7-7)^2 = 0$ |

$$R_{\text{emp}} = \frac{1}{3}(0 + 0 + 0) = 0$$

The model fits perfectly! (This is because the data was generated by $y = 2x + 1$.)

**Now try model $f(x) = x + 2$ (so $w = 1, b = 2$):**

| $i$ | $x_i$ | $y_i$ | $\hat{y}_i$ | $L(\hat{y}_i, y_i)$ |
|-----|-------|-------|-------------|---------------------|
| 1 | 1 | 3 | $1+2=3$ | $(3-3)^2 = 0$ |
| 2 | 2 | 5 | $2+2=4$ | $(4-5)^2 = 1$ |
| 3 | 3 | 7 | $3+2=5$ | $(5-7)^2 = 4$ |

$$R_{\text{emp}} = \frac{1}{3}(0 + 1 + 4) = \frac{5}{3} \approx 1.67$$

So $f(x) = 2x + 1$ is better than $f(x) = x + 2$ on this data, as expected.

### Example 3: Hypothesis Space and Flexibility

Consider three hypothesis spaces for a 1D regression problem:

| Hypothesis Space | Functions | Flexibility |
|-----------------|-----------|-------------|
| $\mathcal{H}_1$ | $f(x) = b$ (constant) | Very low — can only predict one value |
| $\mathcal{H}_2$ | $f(x) = wx + b$ (linear) | Moderate — can fit lines |
| $\mathcal{H}_3$ | $f(x) = a x^2 + bx + c$ (quadratic) | Higher — can fit parabolas |
| $\mathcal{H}_4$ | $f(x) = \sum_{k=0}^{10} w_k x^k$ (degree-10 polynomial) | Very high — can fit complex curves |

If the true relationship is $y = 2x + 1$:
- $\mathcal{H}_1$: cannot represent it → **underfitting**
- $\mathcal{H}_2$: can represent it exactly → **good fit**
- $\mathcal{H}_3, \mathcal{H}_4$: can represent it, but with only 3 data points, might fit noise → **overfitting risk**

> **Lesson:** A more flexible hypothesis space is not always better. The right hypothesis space is one that can represent the true pattern but not so much that it fits noise.

---

## 9. Exercises

### [Basic]

**E1.** For each of the following, identify the type of learning (supervised/unsupervised/reinforcement) and whether it's regression or classification (if supervised):

a) Predicting temperature tomorrow given today's weather data.  
b) Grouping news articles by topic.  
c) A self-driving car learning to stay in its lane.  
d) Detecting fraudulent credit card transactions.  
e) Predicting the number of likes a social media post will receive.

**E2.** Given the dataset:

| $x_i$ | $y_i$ |
|-------|-------|
| 0 | 1 |
| 1 | 3 |
| 2 | 5 |

Compute the empirical risk (using squared error) for the model $f(x) = x + 2$.

**E3.** Explain in your own words the difference between the empirical risk and the true risk. Why can't we directly minimize the true risk?

### [Intermediate]

**E4.** Suppose you have a dataset of 1000 emails, each labeled "spam" or "not spam." You train a model that achieves 99% accuracy on the training data but only 60% accuracy on new emails. What is happening? Name the phenomenon and suggest two ways to address it.

**E5.** Consider a hypothesis space $\mathcal{H}$ that contains only one function: $f(x) = 0$ for all $x$. Will this model overfit? Will it underfit? Explain.

**E6.** Write the empirical risk formula for a binary classification problem using the 0-1 loss function. Why is this loss function difficult to optimize? (Hint: think about differentiability.)

### [★ Advanced]

**E7.** Consider two hypothesis spaces: $\mathcal{H}_1 \subset \mathcal{H}_2$ (every function in $\mathcal{H}_1$ is also in $\mathcal{H}_2$). Let $\theta_1^*$ and $\theta_2^*$ be the empirical risk minimizers in each space. Prove that $R_{\text{emp}}(\theta_2^*) \leq R_{\text{emp}}(\theta_1^*)$. Then explain why this does NOT imply that $\theta_2^*$ will generalize better.

**E8.** The No Free Lunch Theorem (preview): Consider a binary classification problem with input space $\mathcal{X} = \{1, 2, \ldots, 2m\}$. We observe $m$ labeled examples. There are $2^{2m}$ possible labelings of the unseen $m$ points. Argue (informally) that for any fixed algorithm, averaged over all possible true labelings, the error rate on unseen data is exactly 50%. (We'll formalize this in Week 10.)

---

## 10. Summary

### Key Equations

> **Empirical Risk:**
> $$R_{\text{emp}}(\theta) = \frac{1}{n} \sum_{i=1}^{n} L(f_\theta(\mathbf{x}_i), y_i)$$

> **Learning Goal (ERM):**
> $$\theta^* = \arg\min_{\theta \in \Theta} R_{\text{emp}}(\theta)$$

> **True Risk:**
> $$R(\theta) = \mathbb{E}_{(\mathbf{x},y) \sim \mathcal{P}}[L(f_\theta(\mathbf{x}), y)]$$

### Key Intuition (If You Remember Nothing Else...)

1. **ML = learning patterns from data instead of hand-coding rules.**
2. **Every ML problem = hypothesis space + loss function + optimizer.** Choose all three carefully.
3. **We minimize training loss, but we care about test loss.** The gap is generalization.
4. **Overfitting vs. underfitting** is the central tension. More complex models fit training data better but may not generalize.
5. **Three perspectives:** geometric (fitting surfaces), probabilistic (estimating distributions), optimization (minimizing loss). We'll use all three throughout the course.

---

*Next week: Linear Regression — our first complete model. We'll derive the exact solution and connect geometry, probability, and optimization.*
