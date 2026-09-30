# Week 5 — Suggested Paper

## "Visual Information Theory"

**Author:** Christopher Olah  
**Year:** 2015  
**Type:** Blog post (research-quality exposition with interactive visualizations)  
**Difficulty:** ★★ (accessible, but the ideas go deep)

---

## Where to Find It

- **URL:** https://colah.github.io/posts/2015-09-Visual-Information/

---

## Why This Paper?

1. **It makes probability visual.** Olah's diagrams turn abstract probability concepts (joint distributions, marginalization, conditional distributions) into intuitive pictures. You already know the algebra — this gives you the geometry.

2. **It introduces information theory visually.** Entropy, KL divergence, and cross-entropy are usually presented with formulas. Olah presents them with pictures. This builds intuition for Week 11 (Information Theory).

3. **It connects probability to ML.** The post shows how joint distributions, marginalization, and conditional distributions appear in ML — the exact tools we're using this week for Bayes' theorem and MLE.

4. **It previews cross-entropy.** The visual explanation of cross-entropy and KL divergence is the best available. This directly connects to Week 7 (logistic regression: cross-entropy loss).

---

## Reading Guide

### Reading Time

**20–30 minutes**. The post is long but richly illustrated — skim the visuals and read the text that catches your eye.

### Minimal Reading (for all students)

1. **Introduction** (2 min) — Motivation: probability is about quantifying uncertainty, and visualizing it helps.

2. **Visualizing Probability Distributions** (5 min) — The key visual idea: represent a distribution over two variables as a 2D grid of squares, where the size of each square represents probability. This is how Olah visualizes joint distributions.

3. **Marginal Probability** (3 min) — How to get marginals by "summing out" — visually, projecting the 2D grid onto one axis. Connect to handout Section 2.

4. **Conditional Probability** (3 min) — How to get conditionals by "slicing" the joint distribution. Connect to Bayes' theorem.

5. **Entropy** (5 min) — Visual definition: "how spread out is the distribution?" A peaked Gaussian has low entropy; a flat one has high entropy.

6. **Cross-Entropy and KL Divergence** (5 min) — Cross-entropy = entropy + KL divergence. This previews Week 7 (cross-entropy loss) and Week 11 (information theory).

---

## Key Sections and Their Connections

### Visualizing Joint Distributions

Olah represents $P(X, Y)$ as a 2D grid where each cell's area represents $P(X=x, Y=y)$.

- **Marginalization** = projecting onto one axis.
- **Conditioning** = taking one row/column and renormalizing.
- **Independence** = the grid is "rectangular."

**Connection to Bayes' theorem:** The medical testing example is a 2×2 grid (disease × test). Bayes' theorem goes from a row-conditional to a column-conditional. The grid makes it obvious that false positives can outnumber true positives.

### Cross-Entropy and KL Divergence

Cross-entropy measures how well one distribution "explains" another. KL divergence is the *extra* surprise from using the wrong distribution.

**Connection to MLE:** MLE finds the $\theta$ that minimizes the KL divergence between the data distribution and the model distribution. This is the deeper meaning of MLE: find the model closest to the data.

**Connection to Week 7:** Cross-entropy loss in classification = minimizing KL divergence. This is MLE for the Bernoulli.

---

## Paper Reading Template

```
PAPER READING NOTES
===================
Title: Visual Information Theory
Author: Christopher Olah
Year: 2015

1. Key idea: Probability distributions and information-theoretic
   quantities can be visualized as geometric objects (grids,
   areas, volumes), making their relationships obvious.

2. Key visuals:
   - 2D grid for joint distributions (marginalization = projection)
   - Entropy illustration (how spread out is the distribution?)
   - Cross-entropy/KL divergence (extra "surprise" from wrong model)

3. Connections to class:
   - Bayes' theorem: going from row-conditional to column-conditional
   - MLE: minimizing KL divergence between data and model
   - Cross-entropy: preview of Week 7 (logistic regression)

4. Questions: (Student fills in)
```

---

## In-Class Discussion (5 min — at the start of Session 2)

1. **"Olah represents joint distributions as 2D grids. How would you draw the medical testing example as a grid?"** → 2×2 grid: rows = disease/no disease, columns = positive/negative. The "positive" column total is the evidence. $P(\text{disease}|\text{positive})$ = one cell divided by the column total.

2. **"Which has higher entropy: Bernoulli(0.5) or Bernoulli(0.01)?"** → Bernoulli(0.5) — maximally uncertain. Entropy is maximized at the uniform distribution.

3. **"Olah shows cross-entropy = entropy + KL divergence. In MLE, what are we minimizing?"** → KL divergence between data and model. Since the data distribution is fixed, minimizing cross-entropy = minimizing KL divergence.

---

## Advanced Follow-Up

1. **Read about maximum entropy distributions.** The Gaussian is the maximum entropy distribution for a given mean and variance. This is why we use it as a default noise model — it makes the fewest assumptions.

2. **Connect KL divergence to cross-entropy loss.** In Week 7, cross-entropy loss = MLE for Bernoulli = minimizing KL divergence. Try to derive this before Week 7.

3. **Explore mutual information.** How much information one variable tells you about another. Connects to feature selection. We'll revisit in Week 11.
