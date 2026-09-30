# Week 6 (Corrected) — Suggested Paper

## "An Overview of Gradient Descent Optimization Algorithms"

**Author:** Sebastian Ruder
**Year:** 2016
**Type:** Survey blog post (widely cited)
**Difficulty:** ★★

---

## Where to Find It

- **URL:** https://www.ruder.io/optimizing-gradient-descent/
- **arXiv:** 1609.04747

---

## Why This Paper?

1. **Best single overview of GD variants.** Covers momentum, Nesterov, Adagrad, RMSprop, Adam — all in one place.
2. **Directly relevant.** We learned batch GD and SGD in Session 2. Ruder extends to the variants used in modern deep learning (Week 17).
3. **Practical.** Explains *when* to use each method and *why*. The "Which optimizer to use?" section is gold.
4. **Well-written.** Clear, organized, accessible. Good figures and tables.
5. **Creates anticipation.** Most variants are designed for neural networks. Reading now builds a foundation for Weeks 15–17.

> **Correction note:** This paper was originally assigned for Week 6 but was not discussed (Week 5 material spilled over). It is now assigned for Session 2 of this corrected Week 6.

---

## Reading Guide

### Reading Time

**20–30 minutes**. The post is long but well-structured.

### Minimal Reading

1. **Introduction** (2 min) — GD variants: batch, stochastic, mini-batch. Recaps what we covered in Session 2.
2. **Section 1: GD variants** (5 min) — Skim; confirms class material. Focus on challenges (learning rate selection).
3. **Section 2: Optimization algorithms** (10 min) — The core:
   - **Momentum** (2.1): accumulates gradients, damps oscillation.
   - **Adagrad** (2.3): per-parameter learning rates.
   - **RMSprop** (2.4): fixes Adagrad's decreasing rates.
   - **Adam** (2.5): momentum + adaptive rates. Most popular for DL.
4. **"Which optimizer to use?"** (3 min) — Adam as default.

---

## Key Connections to Our Course

### Section 1: GD Variants

Matches our handout Section 9. The key tradeoff: cost per step vs. gradient variance.

**Question:** "Ruder says SGD's noise helps escape local minima. When does this matter?" → Only for non-convex problems (neural networks). For linear regression (convex), there's one minimum.

### Section 2.1: Momentum

$v_t = \gamma v_{t-1} + \eta \nabla L$. Consistent directions build up; oscillating directions damp out. Directly addresses the zigzag problem from our handout Section 10.

**Question:** "How does momentum relate to feature scaling?" → Both address zigzagging. Scaling changes the surface; momentum changes the optimizer. Can use together.

### Section 2.5: Adam

Combines momentum + per-parameter adaptive learning rates. The default for neural networks (Week 17).

**Question:** "Should we use Adam for linear regression?" → For simple convex problems, plain GD is sufficient. Adam shines for complex, high-dimensional, non-convex problems.

### Connection to Session 1

In Session 1, we proved that MSE = MLE under Gaussian noise, and ridge = MAP with a Gaussian prior. In Session 2, we learned GD — the tool that minimizes these loss functions. Ruder's paper shows how GD itself can be improved. The optimizers (Adam, momentum, etc.) are all trying to minimize the same negative log-likelihoods we derived — just more efficiently.

---

## Paper Reading Template

```
PAPER READING NOTES
===================
Title: An Overview of Gradient Descent Optimization Algorithms
Author: Sebastian Ruder
Year: 2016

1. Key idea: GD variants improve on vanilla GD via (1) momentum
   (accumulating gradients) and (2) adaptive per-parameter
   learning rates. Adam combines both.

2. Key concepts:
   - Momentum: v_t = γv_{t-1} + η∇L
   - Adagrad: per-parameter η, decreasing
   - RMSprop: fixes Adagrad
   - Adam: momentum + adaptive. Default for DL.

3. Connections to class:
   - Batch/SGD/mini-batch (handout Section 9)
   - Learning rate (handout Section 7): adaptive methods as alternative
   - Feature scaling (handout Section 10): Adam partially replaces need
   - Zigzag problem: momentum addresses it
   - Session 1: GD minimizes the negative log-likelihoods (MSE, cross-entropy)
     that we derived from MLE/MAP

4. Questions: (Student fills in)
```

---

## In-Class Discussion (5 min — start of Session 2)

1. **"Which GD variant is standard in practice?"** → Mini-batch ($B = 32$–$128$).
2. **"What is momentum?"** → Accumulates past gradients. Consistent directions amplified, oscillating damped.
3. **"What makes Adam different from vanilla GD?"** → Per-parameter adaptive learning rates + momentum.
4. **"Should we use Adam for linear regression?"** → Overkill for simple convex problems. Save for neural networks.
5. **"How does this connect to Session 1?"** → GD is how we minimize the loss functions (MSE, cross-entropy) that MLE/MAP tell us to use. Better optimizers = faster convergence to the same MLE/MAP solution.

---

## Advanced Follow-Up

1. **Implement momentum** in your GD code. Compare convergence with/without on unscaled features.
2. **Compare Adam and GD** on the same problem. Does Adam handle different scales automatically?
3. **Read about Newton's method** (Boyd & Vandenberghe, Section 9.5). Uses second derivatives. Why too expensive for large neural networks?
4. **Read about SGD and generalization.** "The Implicit Regularization of Stochastic Gradient Flow" (Barrett & Dherin, 2021). Connects to Week 18.
5. **Read about learning rate warmup.** "Accurate, Large Minibatch SGD" (Goyal et al., 2017). Why start with small $\eta$ and increase?

---

## Also Recommended from Session 1

### "Visual Information Theory" — Christopher Olah (2015)

- **URL:** https://colah.github.io/posts/visual-information/
- **Difficulty:** ★
- **Reading time:** 15–20 minutes

This was originally assigned for Week 5 but was not discussed. It provides an intuitive visual introduction to probability distributions, entropy, and KL divergence — topics that connect Session 1's probability material to information theory (Week 11).

**Key idea:** Probability distributions can be visualized as "boxes" of area. Entropy measures "how spread out" a distribution is. KL divergence measures "how different" two distributions are.

**Connection:** In Session 1, we showed that different noise models (Gaussian, Bernoulli, Laplacian) give different loss functions (MSE, cross-entropy, MAE). Olah's post visualizes *why* — the shape of the distribution determines the shape of the loss.
