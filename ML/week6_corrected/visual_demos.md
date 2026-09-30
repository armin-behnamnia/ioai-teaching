# Week 6 (Corrected) — Visual Demos

> **Purpose:** Interactive visual demonstrations for in-class use. Each demo includes setup, what to show, and key teaching points.

> **Note:** Session 1 demos focus on probability/Bayes/MLE/MAP/bias-variance (Week 5 catch-up). Session 2 demos focus on gradient descent (Week 6 content).

---

## Session 1 Demos (Week 5 Catch-Up)

### Demo 1: Bayes' Theorem — Medical Testing Tree Diagram

**Tool:** Whiteboard
**Used in:** Session 1, minutes 5–13
**Prep time:** None

### Setup

Draw the medical testing tree diagram:

```
                    ┌── P(pos|D) = 0.99 ── P(D∩pos) = 0.0099
  P(D) = 0.01 ────┤
                    └── P(neg|D) = 0.01

                    ┌── P(pos|¬D) = 0.05 ── P(¬D∩pos) = 0.0495
  P(¬D) = 0.99 ────┤
                    └── P(neg|¬D) = 0.95
```

### What to Show

1. Compute: $P(\text{disease}|\text{positive}) = 0.0099 / 0.0594 = 1/6 \approx 16.7\%$.
2. "Even with a 99% sensitive test, a positive result means only 16.7% chance of disease!"
3. **Connect to Week 4:** "What is $P(\text{disease}|\text{positive})$ in Week 4 terms?" → **Precision!**

### Teaching Points

- The prior dominates the posterior for rare events.
- This is EXACTLY the class imbalance problem from Week 4.
- Bayes' theorem connects probability to classification metrics.

---

### Demo 2: The MLE = MSE Proof (Visual)

**Tool:** Whiteboard
**Used in:** Session 1, minutes 28–35
**Prep time:** None

### Setup

Write the log-likelihood on the board:

$$\ell(w, b) = \text{const} - \frac{1}{2\sigma^2}\sum_{i=1}^{n}(y_i - wx_i - b)^2$$

### What to Show

1. Circle the constant term: "This doesn't depend on $w$ or $b$."
2. Circle the sum: "This IS $n \times \text{MSE}$!"
3. Draw the connection:

```
  Log-likelihood          MSE
  ┌───────────┐          ┌───────────┐
  │ const -   │          │  1   ___  │
  │ 1/(2σ²) × │ ══════▶  │ ─   ╲    │
  │   n·MSE   │          │ n    ╲___│
  └───────────┘          └───────────┘
       ↑                       ↑
  Maximize this          Minimize this
  (same thing!)
```

### Teaching Points

- MSE is not arbitrary — it IS the negative log-likelihood under Gaussian noise.
- Every loss function corresponds to a noise model.

---

### Demo 3: MAP = Ridge (Visual)

**Tool:** Whiteboard
**Used in:** Session 1, minutes 38–48
**Prep time:** None

### Setup

Draw the decomposition of the MAP objective:

```
  MAP objective  =  Log-likelihood  +  Log-prior
       │                  │                │
       │                  │                │
       ▼                  ▼                ▼
  Minimize:        -1/(2σ²) × MSE    -w²/(2τ²)
  MSE + λw²            ↑                ↑
                   Data term        Prior term
                                    (penalty)
                                    
  Multiply by 2σ²:
  MSE + (σ²/τ²)w²  =  MSE + λw²
                         ↑
                    λ = σ²/τ²
```

### What to Show

1. "The log-prior becomes the penalty term."
2. "Gaussian prior → L2 penalty → Ridge."
3. "Laplacian prior → L1 penalty → Lasso."
4. Show the prior/regularization correspondence table.

### Teaching Points

- Regularization is not arbitrary — it encodes a prior belief about parameters.
- $\lambda = \sigma^2/\tau^2$ is the noise-to-prior ratio.

---

### Demo 4: Bias-Variance Tradeoff Diagram

**Tool:** Whiteboard
**Used in:** Session 1, minutes 55–65
**Prep time:** None

### Setup

Draw the classic bias-variance tradeoff:

```
  Error
    │  Total = Bias² + Var + Noise
    │  ╲                          ╱
    │   ╲                        ╱
    │    ╲                      ╱
    │     ╲        ╱╲          ╱
    │      ╲      ╱  ╲        ╱
    │       ╲    ╱    ╲      ╱
    │        ╲  ╱      ╲    ╱
    │         ╲╱        ╲  ╱
    │                    ╲╱
    │
    │  Bias²          Variance
    │  (decreasing)    (increasing)
    │
    └────────────────────────────── Model complexity
    Simple                   Complex
    (underfit)               (overfit)
              ↑
          Sweet spot
```

### What to Show

1. "As complexity increases: bias decreases, variance increases."
2. "Total error = bias² + variance + noise. The minimum is the sweet spot."
3. Draw the decomposition arrows:
   - $\lambda = 0$ (OLS): low bias, high variance (right side)
   - $\lambda$ moderate (ridge): balanced (sweet spot)
   - $\lambda \to \infty$: high bias, low variance (left side)

### Teaching Points

- Regularization trades bias for variance.
- More data reduces variance but not bias.
- The decomposition is a theorem, not just intuition.

---

## Session 2 Demos (Gradient Descent)

### Demo 5: The Gradient (Quick Visual)

**Tool:** Whiteboard drawing
**Used in:** Session 2, minutes 10–12
**Prep time:** None

### Setup

Draw $f(w) = w^2$ with a tangent line at $w = 2$.

```
  f(w) = w²
    │        ╱
    │       ╱     ← Tangent at w=2: f'(2)=4 (slope)
    │      ●
    │     ╱
    │    ╱
    │   ╱
    │  ╱
    │ ╱
    │╱
    └────────── w
         2
```

### What to Show

1. "Derivative = slope. Positive → function increasing → go left to decrease."
2. "At $w = -1$: $f'(-1) = -2$. Negative → decreasing → go right."
3. "At $w = 0$: $f'(0) = 0$. Minimum!"
4. "The gradient tells you which way is uphill. Go opposite to go downhill."

### Teaching Points

- Derivative = slope. Gradient points uphill. $-\nabla f$ points downhill.
- Zero gradient = at the minimum.

---

### Demo 6: GD on 1D Quadratic (Step by Step)

**Tool:** Whiteboard + Desmos
**Used in:** Session 2, minutes 12–22
**Prep time:** 5 minutes

### Setup

In Desmos, plot $f(w) = w^2$. Mark $w_0 = 3$.

### What to Show

**Part A: First Step (3 min)**

1. $f'(3) = 6$. Gradient points uphill (right).
2. $w_1 = 3 - 0.1 \times 6 = 2.4$. Moved LEFT (downhill). Loss: 9 → 5.76.

**Part B: Multiple Steps (3 min)**

| Step | $w$ | $f(w)$ | $f'(w)$ |
|------|-----|--------|---------|
| 0 | 3.000 | 9.000 | 6.000 |
| 1 | 2.400 | 5.760 | 4.800 |
| 2 | 1.920 | 3.686 | 3.840 |
| 3 | 1.536 | 2.359 | 3.072 |
| 20 | 0.036 | 0.001 | 0.072 |

**Part C: The Pattern (3 min)**

$w_{t+1} = w_t(1 - 2\eta) = 0.8\, w_t$. Geometric decay.

### Teaching Points

- GD follows $-\nabla f$ (downhill).
- Steps shrink near the minimum (gradient → 0).
- Geometric decay: $w_t = w_0(1-2\eta)^t$.

---

### Demo 7: Learning Rate Regimes (Three Runs)

**Tool:** Desmos
**Used in:** Session 2, minutes 22–32
**Prep time:** 10 minutes

### Setup

Three GD runs on $f(w) = w^2$, $w_0 = 3$:
1. $\eta = 0.01$ (too small)
2. $\eta = 0.1$ (just right)
3. $\eta = 1.1$ (too large)

### What to Show

**$\eta = 0.01$:** After 50 steps, $w \approx 1.1$. Very slow.

**$\eta = 0.1$:** After 20 steps, $w \approx 0.04$. Smooth.

**$\eta = 1.1$:** $w$ bounces: $3 \to -3.6 \to 4.32 \to \ldots$ Loss INCREASES. Divergence!

### What to Draw

```
  f(w)
  30 │                    ●              ●
     │              ●              ●
  10 │  ●
     │    ●  ●                    ← η=0.1 (good)
   5 │      ●  ●●●
     │              ●●●●●●●●●
   1 │                        ●●●●●●●●●●●●●●●  ← η=0.01 (slow)
   0 └──────────────────────────────────────── Steps
              ↑
     η=1.1 (diverge): bounces up
```

### Teaching Points

- Too small: slow. Too large: diverge. Just right: smooth.
- $\eta$ is the MOST IMPORTANT hyperparameter. Monitor the loss.

---

### Demo 8: SGD vs Batch GD Trajectory

**Tool:** Desmos or Python
**Used in:** Session 2, minutes 62–70
**Prep time:** 10 minutes

### What to Draw

```
  Loss (Batch GD)           Loss (SGD)
    │ ●                        │ ●  ╱╲    ╱╲
    │  ●                       │  ╲╱  ╲  ╱  ╲
    │   ●●●●●●●                │       ╲╱    ╲──
    └──────────────────        └──────────────────
           Steps                     Steps
```

### What to Show

1. **Batch GD:** Smooth, steady decrease. But $O(n)$ per step.
2. **SGD:** Noisy, bouncy. Decreases ON AVERAGE. $O(1)$ per step.
3. "The noise is because each example gives a different gradient. On average, correct."
4. "Noise is GOOD for non-convex — helps escape local minima."
5. **Mini-batch:** Smoother than SGD, cheaper than batch. The standard.

### Teaching Points

- Batch: exact, expensive. SGD: noisy, cheap. Mini-batch: balanced, standard.
- SGD noise helps non-convex optimization.

---

### Demo 9: Feature Scaling (Elongated vs Spherical)

**Tool:** Whiteboard
**Used in:** Session 2, minutes 70–75
**Prep time:** None

### What to Draw

**Before Scaling:**
```
  w₂
  10 │ ┌──────────────┐
     │ │    ╱╲╱╲╱╲     │   ← GD zigzags!
   0 │─●────────────●─── w₁
  -10│ └──────────────┘
     x₁ ∈ [0,1], x₂ ∈ [0,1000] → elongated
```

**After Scaling:**
```
  w₂
   2 │      ┌──┐
     │    ╱      ╲
   0 │  ╱    ●     ╲   ← Smooth path!
  -2 │      └──┘
     Both standardized → spherical
```

### What to Show

1. "Different scales → elongated surface → zigzag."
2. "Standardize: $x \to (x-\bar{x})/\sigma_x$ → spherical → smooth."
3. **CRITICAL:** "Compute stats on TRAINING data only. Split first! (Week 4)"

### Teaching Points

- Unscaled → elongated → zigzag → slow.
- Scaled → spherical → smooth.
- Always split first, compute stats on training only.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Bayes' medical testing tree | S1 | 5 min | Whiteboard | Bayes' theorem + class imbalance |
| 2 | MLE = MSE proof visual | S1 | 5 min | Whiteboard | The key connection |
| 3 | MAP = Ridge decomposition | S1 | 5 min | Whiteboard | Prior → penalty |
| 4 | Bias-variance tradeoff diagram | S1 | 7 min | Whiteboard | Bias² + Variance + Noise |
| 5 | Gradient as slope | S2 | 2 min | Whiteboard | Gradient = uphill, go opposite |
| 6 | GD on 1D quadratic | S2 | 10 min | Whiteboard + Desmos | Step-by-step GD |
| 7 | Learning rate regimes | S2 | 10 min | Desmos | Three runs: small/good/large |
| 8 | SGD vs batch GD | S2 | 8 min | Desmos | Noisy vs smooth |
| 9 | Feature scaling | S2 | 5 min | Whiteboard | Elongated vs spherical |

**Total Session 1:** ~22 minutes of demos. Leaves ~58 min for lecture, derivation, discussion, quiz.

**Total Session 2:** ~35 minutes of demos. Leaves ~45 min for lecture, derivation, discussion, quiz.

---

## Pre-Class Tech Check

### Session 1

- [ ] Whiteboard space for Bayes' theorem tree diagram
- [ ] Whiteboard space for MLE=MSE proof
- [ ] Whiteboard space for MAP=Ridge decomposition
- [ ] Colored markers for bias-variance diagram
- [ ] Quiz S1 printed or ready

### Session 2

- [ ] Desmos has $f(w) = w^2$ with point and tangent (Session 2)
- [ ] Desmos has three GD runs at different $\eta$ (Session 2)
- [ ] Desmos/Python has SGD vs batch loss curves (Session 2)
- [ ] Whiteboard space for step-by-step GD table (Session 2)
- [ ] Whiteboard space for MSE gradient derivation (Session 2)
- [ ] Quiz S2 printed or ready
