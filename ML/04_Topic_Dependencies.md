# Topic Dependencies & Teaching Order Rationale

## Why This Order?

The syllabus order is carefully designed around five principles:

1. **Every concept is motivated before it's introduced.** Students should never ask "why are we learning this?"
2. **Each topic builds on the previous one.** Dependencies are explicit — no topic requires knowledge from a later week.
3. **Exam-critical topics come first.** The national qualification exam (~month 5–6) must cover the most frequently tested material.
4. **Mathematical maturity grows gradually.** Early derivations are simple (1D, scalar). Later derivations use full matrix calculus.
5. **The story has a narrative arc.** Linear models → their limitations → nonlinear extensions → neural networks → deep learning → generative models → RL → modern AI. Each phase answers a question raised by the previous one.

## Dependency Graph

```
Legend: A → B means "A is prerequisite for B"

W1: ML Setup
├──→ W2: Scalar Linear Regression
│    ├──→ W3: Overfitting & Regularization (polynomials, ridge/lasso deep dive)
│    │    ├──→ W4: Model Evaluation (overfitting detection via train/test)
│    │    ├──→ W9: k-NN (overfitting concept applied to new algorithm)
│    │    └──→ W10: Decision Trees (pruning = regularization analog)
│    ├──→ W5: Probability for ML (MSE ↔ Gaussian noise preview from W2)
│    │    ├──→ W6: Gradient Descent (probability not strictly needed, but same point in course)
│    │    ├──→ W7: Logistic Regression (MLE → cross-entropy)
│    │    ├──→ W8: Matrix LR (MLE → MSE, MAP → ridge)
│    │    ├──→ W11: Information Theory (entropy, KL from probability)
│    │    │    ├──→ W12: Feature Engineering (information gain)
│    │    │    ├──→ W19: Clustering (KL in GMM)
│    │    │    ├──→ W20: PCA (explained variance, information)
│    │    │    └── W30: Generative Models (VAE ELBO, diffusion score)
│    │    ├──→ W19: Clustering (GMM = MLE on mixture model)
│    │    └── W32: RL (policy gradient = likelihood ratio)
│    ├──→ W6: Gradient Descent (calculus now ready)
│    │    ├──→ W7: Logistic Regression (GD on cross-entropy)
│    │    ├──→ W8: Matrix LR (GD on matrix formulation)
│    │    ├──→ W15: Neural Networks (GD on nonconvex loss)
│    └──→ W17: Training NNs (advanced optimizers)
│    ├──→ W7: Logistic Regression (second complete model)
│    │    └──→ W15: Neural Networks (LR = 0-layer NN)
│    └──→ W8: Matrix LR + Consolidation
│         (depends on W2: scalar LR, W5: probability/MLE, W6: GD)
├──→ W4: Model Evaluation (no calculus needed; pulled forward)
│    ├──→ W8: Consolidation (metrics, cross-validation)
│    ├──→ W9: k-NN (evaluate k choice via cross-validation)
│    ├──→ W10: Decision Trees (evaluate depth/pruning via cross-validation)
│    └──→ W18: Generalization (bias-variance, learning curves)
├──→ W9: k-NN (nonlinear methods begin)
│    └──→ W12: Feature Engineering (curse of dimensionality from W9)
├──→ W10: Decision Trees
│    ├──→ W11: Information Theory (Gini ↔ entropy connection)
│    └──→ W12: Feature Engineering (tree-based feature importance)
├──→ W12: Feature Engineering
│    ├──→ W13: SVM Part 1 (nonlinear via features → kernels)
│    │    └──→ W14: SVM Part 2 (kernel trick)
├──→ W15: Neural Networks
│    ├──→ W16: Backpropagation
│    │    └──→ W17: Training NNs
│         └──→ W18: Generalization
│              └──→ (all advanced topics depend on W15-18)
├──→ W19: Clustering (unsupervised learning)
│    └──→ W20: PCA (dimensionality reduction + Phase 2 consolidation)
├──→ W26: CNNs (depends on W15-17: NN + training)
├──→ W28: RNNs (depends on W15-17: NN + training)
│    └──→ W29: Attention/Transformers (depends on W28: sequence models)
│         ├──→ W35: LLMs (depends on W29: transformers)
│         └──→ W35: LLMs detailed (depends on W29, W35)
├──→ W30: VAEs (depends on W11: KL, W15: NN, W5: MLE)
│    └──→ W31: GANs/Diffusion (depends on W30: generative framework)
├──→ W32: RL (depends on W5: probability, W15: NN)
│    └──→ W33: RL advanced (depends on W32)
│         └──→ W35: RLHF (depends on W29: transformers, W33: PPO)
└──→ W34: Representation Learning (depends on W11: contrastive loss, W20: embeddings)
```

## Detailed Rationale for Key Ordering Decisions

### 1. Why Scalar Linear Regression Before Everything Else?

Linear regression is the **simplest non-trivial ML model**. Starting with the **scalar** formulation (no matrices) allows us to introduce:
- The supervised learning setup (input, output, model, loss)
- A closed-form solution using only mean, variance, and covariance — no calculus, no matrix inversion
- Regularization (ridge in scalar form — just adding a penalty to a fraction)
- The overfitting-underfitting tradeoff (qualitatively)

All of these concepts reappear in every subsequent topic. The matrix formulation and gradient descent are deferred to Weeks 7–8 when students' calculus and linear algebra courses have caught up.

### 1b. Why Deepen Fundamentals Before Introducing New Algorithms?

After Week 2 (scalar linear regression), the standard ML curriculum deepens the story before jumping to new algorithms. Week 3 goes deep on overfitting and regularization (polynomial features, ridge/lasso in depth, the complexity dial). Week 4 covers model evaluation (train/test split, cross-validation, metrics). This ensures students have a **solid foundation** before seeing k-NN, trees, SVMs, and neural networks.

By the time students reach k-NN (Week 9) and decision trees (Week 10), they already understand overfitting, regularization, bias-variance, evaluation metrics, and cross-validation. This makes the new algorithms much easier to understand — students can immediately ask "how does this overfit?" and "how do I evaluate it?"

### 1c. Why Logistic Regression (Week 7) Before k-NN and Trees?

Logistic regression is the natural "second model" after linear regression. It:
- Uses the same framework (model + loss + optimizer) as linear regression
- Connects directly to MLE (Week 5) and gradient descent (Week 6)
- Introduces classification, cross-entropy, and the sigmoid — concepts needed for neural networks
- Is a 0-layer neural network, creating a bridge to Phase 2

k-NN and trees, while simpler algorithmically, introduce a **different paradigm** (non-parametric, instance-based, rule-based). Placing them in Phase 2 (Weeks 9–10) positions them as "nonlinear methods" that lead naturally into SVMs and neural networks.

### 2. Why Probability Before Information Theory?

Information theory requires probability (entropy is an expectation). MLE is the bridge:
- Week 6: MLE (probability → loss functions)
- Week 9: Entropy, KL, cross-entropy (probability → information measures)
- Week 10: Logistic regression (uses cross-entropy from Week 9, MLE from Week 6)

This creates a tight 3-week sequence where each topic flows naturally into the next.

### 3. Why Information Theory Before Logistic Regression?

Logistic regression's loss function (cross-entropy) is an information-theoretic quantity. If students understand entropy and KL divergence first, then:
- Cross-entropy = H(p) + D_KL(p‖q) makes immediate sense
- The gradient derivation shows a beautiful cancellation that students can appreciate
- The "why not MSE for classification" question has a rigorous answer (non-convex loss)

Without information theory, cross-entropy is just a formula to memorize. With it, cross-entropy is "the extra surprise from using the wrong distribution."

### 4. Why Decision Trees (Week 4) Before Feature Engineering (Week 11)?

Decision trees introduce the concept of **feature testing** — splitting on one feature at a time. This is a concrete, visual introduction to the idea that some features are more informative than others. When students encounter feature engineering later, they already understand:
- Information gain (from tree splitting criteria — Gini/entropy)
- Feature importance (trees give a natural ranking)
- The curse of dimensionality (revisited from Week 3's k-NN treatment)

The deeper information-theoretic connection (information gain ↔ entropy) is revealed in Week 9, creating a satisfying "aha" moment when students realize Gini impurity and entropy are related.

### 5. Why Feature Engineering / k-NN Before Neural Networks?

Neural networks are the answer to "how do we learn nonlinear features automatically?" Students need to first experience:
- The **problem**: linear models can't solve XOR (Week 11)
- The **manual solution**: feature engineering (Week 11)
- The **simple nonlinear solution**: k-NN (Week 3)
- The **tree-based solution**: decision trees (Week 4)
- The **margin-based solution**: SVMs with kernels (Week 12–13)

Only then do neural networks (Week 14) appear as the **learned feature** solution. This builds appreciation for what neural networks actually contribute: they automate feature engineering through learned representations.

### 5b. Why SVMs Before Neural Networks?

SVMs introduce several concepts that are essential for understanding neural networks:
- **Kernels**: implicit feature maps (neural networks learn explicit ones)
- **Regularization**: the C parameter is a regularizer (same concept as weight decay)
- **Hinge loss**: an alternative to cross-entropy (students should know multiple loss functions)
- **Optimization**: constrained optimization and duality (broadens mathematical toolkit)

SVMs are also a common exam topic, and their mathematical structure (convex optimization, global optimum) provides a clean contrast to the non-convex world of neural networks.

### 6. Why Backpropagation Gets a Full Week (Week 15)?

Backpropagation is the **single most important algorithm** in this course. It is:
- Frequently tested in exams
- The computational heart of all deep learning
- A beautiful application of the chain rule
- Essential for understanding how gradients flow through architectures (CNNs, RNNs, Transformers)

Giving it a full week ensures every student can derive it from scratch. The four fundamental equations of backprop should be as familiar as the quadratic formula.

### 7. Why Generalization Comes After Training (Week 17)?

Students need to have trained neural networks (Week 16) to appreciate generalization issues. The sequence is:
1. Build the model (Week 14)
2. Learn to train it (Week 15–16)
3. Ask: does it generalize? (Week 17)

The double descent phenomenon and the "memorization of random labels" result (Zhang et al.) are much more impactful when students have hands-on intuition for training.

### 8. Why Unsupervised Learning (Week 18–19) Before Deep Learning (Week 26+)?

PCA and clustering introduce:
- **Latent structure**: data has lower-dimensional representations
- **Probabilistic models**: GMM is a generative model (preview of VAEs)
- **EM algorithm**: a general optimization framework (reappears in VAEs, hidden variable models)

These concepts create scaffolding for:
- Autoencoders (VAEs are "deep PCA" + probabilistic)
- Representation learning (embeddings are learned low-dimensional representations)
- Generative models (GMM is the simplest generative model)

### 9. Why CNNs Before RNNs/Transformers?

CNNs are structurally simpler:
- Fixed computation graph (no recurrence)
- Spatial inductive bias is visually intuitive
- Backpropagation through convolutions is a straightforward extension of Week 15

RNNs introduce **temporal** complexity:
- Variable-length sequences
- Backpropagation through time (BPTT)
- Vanishing gradients in a new context

Starting with CNNs lets students extend their neural network knowledge in the simpler (spatial, feedforward) direction before tackling temporal/recurrent structure.

### 10. Why RL Comes After Generative Models?

RL requires:
- Probability (Week 4) — MDPs, policies
- Neural networks (Week 14) — function approximation
- Optimization (Week 16) — policy gradient methods
- Loss functions beyond supervised learning — reward is different from a labeled target

By placing RL in Weeks 32–33, students have all the prerequisites. RLHF (Week 33) then connects RL to the LLM topic (Week 35), creating a powerful synthesis: RL + Transformers = modern AI.

### 11. Why RLHF Gets Explicit Treatment?

RLHF is mentioned in the course overview as something some students already know about. By Week 33, students will understand:
- Supervised learning (SFT) — from Weeks 2–16
- Reward modeling — from Weeks 6–7 (classification/evaluation)
- Reinforcement learning (PPO) — from Weeks 32–33

RLHF ties together the entire course: supervised learning, neural networks, and RL. It's the capstone that shows how all the pieces fit together. Students who came in knowing "RLHF" as a buzzword will now understand it deeply.

## Cross-Topic Connections to Emphasize in Class

These "aha!" moments should be explicitly highlighted when teaching:

| Connection | When to Reveal | Insight |
|-----------|---------------|---------|
| MSE = MLE under Gaussian noise | Week 5 (after W2) | Loss functions come from probability |
| Ridge regression = MAP with Gaussian prior | Week 5 | Regularization = prior belief |
| Cross-entropy = KL divergence + entropy | Week 11 | Classification loss is information-theoretic |
| Logistic regression = 0-hidden-layer neural network | Week 15 | Neural networks generalize linear models |
| k-NN curse of dimensionality ↔ feature engineering | Week 12 | High dimensions hurt distance-based methods |
| Gini impurity ↔ entropy | Week 11 (after W10) | Tree splitting criteria are information-theoretic |
| k-means = hard EM for GMM | Week 19 | Simple algorithms are special cases of deeper ones |
| SVM hinge loss vs. cross-entropy | Week 14 | Different losses → different margins |
| PCA = linear autoencoder | Week 20/30 | Dimensionality reduction unifies linear and nonlinear |
| Attention = weighted retrieval | Week 29 | Transformers are "differentiable databases" |
| GAN minimax = two-player game | Week 31 | Generative models connect to game theory |
| RLHF = SFT + reward model + PPO | Week 33/35 | The entire course synthesizes into modern AI |
| Pruning α ↔ ridge λ | Week 10 (after W3) | Same regularization principle across algorithms |
| k in k-NN ↔ λ in ridge ↔ depth in trees | Week 10 | All are "complexity dials" controlling overfitting |

## Topics NOT Covered (and Why)

| Topic | Reason | Where to Self-Study |
|-------|--------|---------------------|
| Bayesian optimization | Too specialized for exam; requires mature probability | Gaussian Processes for Machine Learning (Rasmussen) |
| Gaussian processes | Conceptually important but math-heavy; mentioned conceptually | Bishop Ch. 6 |
| Markov logic networks | Not relevant to IOAI | — |
| Causal inference | Important but not in IOAI scope | Pearl, "Causality" |
| Federated learning | Important but not exam-critical | — |
| Quantum ML | Too advanced | — |
| Detailed hardware (GPU, TPU) | Out of scope for a theory course | — |

These topics can be mentioned in passing or offered as optional self-study for very advanced students.
