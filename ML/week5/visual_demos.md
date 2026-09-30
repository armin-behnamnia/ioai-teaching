# Week 5 — Visual Demos

> **Purpose:** Interactive visual demonstrations to use in class. Each demo includes the setup, what to show, and key teaching points.

---

## Demo 1: Bayes' Theorem with the Medical Testing Tree

**Tool:** Whiteboard drawing  
**Used in:** Session 1, minutes 8–22  
**Prep time:** None

### Setup

Draw a probability tree for the medical testing example: 1% prevalence, 99% sensitivity, 95% specificity.

### What to Draw

```
                    ┌── P(pos|D) = 0.99 ── P(D∩pos) = 0.0099
  P(D) = 0.01 ──────┤
                    └── P(neg|D) = 0.01

                    ┌── P(pos|¬D) = 0.05 ── P(¬D∩pos) = 0.0495
  P(¬D) = 0.99 ─────┤
                    └── P(neg|¬D) = 0.95

  Evidence: P(pos) = 0.0099 + 0.0495 = 0.0594
  
  Posterior: P(D|pos) = 0.0099 / 0.0594 = 1/6 ≈ 16.7%
```

### What to Show

**Part A: The Tree (4 min)**

1. Draw the tree. First branch: disease (0.01) vs no disease (0.99).
2. From each branch, split: positive vs negative test.
3. Multiply along each path: $P(D \cap \text{pos}) = 0.01 \times 0.99 = 0.0099$.

**Part B: The Evidence (3 min)**

1. Circle the two "positive" leaves: 0.0099 and 0.0495.
2. "$P(\text{positive}) = 0.0099 + 0.0495 = 0.0594$. This is the evidence."

**Part C: The Posterior (3 min)**

1. "$P(\text{disease}|\text{positive}) = 0.0099 / 0.0594 = 1/6 \approx 16.7\%$"
2. "Only 16.7%! Despite a 99% sensitive test!"

**Part D: Connect to Week 4 (4 min)**

1. "What is $P(\text{disease}|\text{positive})$ in Week 4 terms?" → **Precision!**
2. "When the positive class is rare, false positives dominate. The prior dominates the posterior. This IS the class imbalance problem."

### Teaching Points

- Bayes' theorem = updating beliefs with data.
- The prior matters enormously when the event is rare.
- $P(\text{disease}|\text{positive})$ = precision (Week 4).

---

## Demo 2: MLE = MSE (The Key Derivation)

**Tool:** Whiteboard (step-by-step)  
**Used in:** Session 1, minutes 52–68  
**Prep time:** None

### What to Draw

**Step 1: The model**

```
  y_i = wx_i + b + ε_i,   ε_i ~ N(0, σ²)
  → y_i | x_i, w, b ~ N(wx_i + b, σ²)
```

**Step 2: The likelihood**

```
  p(D | w, b) = Π_i N(y_i | wx_i + b, σ²)
```

**Step 3: The log-likelihood**

```
  ℓ(w, b) = const − (1/2σ²) Σ_i (y_i − wx_i − b)²
             ↑ const          ↑ this is n × MSE!
```

**Step 4: The key insight**

```
  ℓ(w, b) = const − (1/2σ²) × n × MSE(w, b)
  max ℓ  ⟺  min MSE  ✓
```

Draw a big box around this result.

### What to Show

1. Write each step, asking students "what do we do next?"
2. At Step 3, circle the sum: "What does this look like?" → "MSE times $n$!"
3. Show the correspondence table: Gaussian→MSE, Bernoulli→cross-entropy, Laplacian→MAE.

### Teaching Points

- The loss function IS the negative log-likelihood.
- MSE ↔ Gaussian noise is a theorem, not a coincidence.
- Every loss function corresponds to a noise model.

---

## Demo 3: MAP = Ridge (The Second Key Derivation)

**Tool:** Whiteboard  
**Used in:** Session 2, minutes 10–28  
**Prep time:** None

### What to Draw

**Step 1: MAP principle**

```
  θ_MAP = argmax_θ [log p(D|θ) + log p(θ)]
                    ↑ MLE        ↑ prior (penalty)
```

**Step 2: Gaussian prior on w**

```
  w ~ N(0, τ²)
  log p(w) = −w² / 2τ² + const
```

**Step 3: Combine**

```
  Minimize:  (1/2σ²) Σ_i (y_i − wx_i − b)² + (1/2τ²) w²
  × 2σ²:    MSE + (σ²/τ²) w²  =  MSE + λ w²
  where λ = σ²/τ²
```

**Step 4: Correspondence table**

```
  Prior on w        → Regularization
  Gaussian N(0,τ²)  → L2 (Ridge): λw²
  Laplacian         → L1 (Lasso): λ|w|
  Uniform (flat)    → None: λ=0 (MLE)
```

### What to Show

1. "MAP = MLE + prior. The log-prior acts as a penalty."
2. Derive each step.
3. Write $\lambda = \sigma^2/\tau^2$ prominently.
4. "If the prior is strong ($\tau^2$ small), $\lambda$ is large → more regularization."
5. Connect to Week 3: "We tuned $\lambda$ with CV. Now we know what it IS."

### Teaching Points

- Ridge = MAP with Gaussian prior. Not arbitrary.
- $\lambda$ = noise-to-prior ratio.
- Lasso ↔ Laplacian prior (sparsity from the sharp peak at 0).

---

## Demo 4: Bias-Variance Decomposition (Visual)

**Tool:** Whiteboard  
**Used in:** Session 2, minutes 38–58  
**Prep time:** 5 minutes

### What to Draw

**Part A: The Tradeoff Diagram**

```
  Error
    │  Total = Bias² + Var + Noise
    │  ╲                          ╱
    │   ╲                        ╱
    │    ╲        ╱╲          ╱
    │     ╲      ╱  ╲        ╱
    │      ╲    ╱    ╲      ╱
    │       ╲  ╱      ╲    ╱
    │         ╲╱        ╲  ╱
    │                    ╲╱  ← Sweet spot
    │  Bias²          Variance
    └────────────────────────────── Model complexity
    Simple                   Complex
```

**Part B: The Decomposition (on the board)**

```
  E_D[(y − f̂(x))²] = (f − f̄)² + E[(f̂ − f̄)²] + σ²
                       ↑ Bias²     ↑ Variance   ↑ Irreducible
```

**Part C: Three Scenarios**

```
  λ = 0 (OLS)          λ moderate (ridge)     λ → ∞
  ┌─────────────┐      ┌─────────────┐       ┌─────────────┐
  │ Low bias    │      │ Mod. bias   │       │ High bias   │
  │ High var    │      │ Mod. var    │       │ Zero var    │
  │ Overfits    │      │ Sweet spot! │       │ Underfits   │
  └─────────────┘      └─────────────┘       └─────────────┘
```

### What to Show

1. Draw the tradeoff diagram. "Total error = bias² + variance + noise. Sweet spot exists."
2. Derive the decomposition: expand $(A+B+C)^2$ where $A = f - \bar{f}$, $B = \bar{f} - \hat{f}$, $C = \epsilon$.
3. Show cross terms vanish: $\mathbb{E}[AB] = 0$ ($\mathbb{E}[B]=0$), $\mathbb{E}[AC] = 0$ ($\mathbb{E}[\epsilon]=0$), $\mathbb{E}[BC] = 0$ ($\epsilon \perp \mathcal{D}$).
4. Show the three scenarios.
5. Connect to Week 3 (qualitative table → theorem) and Week 4 (learning curves).

### Teaching Points

- Expected error = Bias² + Variance + Irreducible noise.
- Regularization trades bias for variance.
- More data reduces variance but not bias.
- This justifies everything from Weeks 1–4.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Bayes' theorem medical tree | S1 | 14 min | Whiteboard | Bayes applied to ML, class imbalance |
| 2 | MLE = MSE derivation | S1 | 16 min | Whiteboard | The key proof |
| 3 | MAP = Ridge derivation | S2 | 18 min | Whiteboard | The second key proof |
| 4 | Bias-variance decomposition | S2 | 20 min | Whiteboard | Formal decomposition + tradeoff |

**Total demo time:** ~68 minutes across both sessions. Since we skipped the probability review, we have more time for derivations and connections.

---

## Pre-Class Tech Check

- [ ] Whiteboard has enough space for the tree diagram (Session 1)
- [ ] Whiteboard has enough space for three derivations (Session 2)
- [ ] Colored markers available (for the bias-variance diagram)
- [ ] Quiz printed or ready to project
- [ ] The MLE↔loss-function and prior↔regularization tables are ready
