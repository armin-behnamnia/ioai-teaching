# Week 6 — Visual Demos

> **Purpose:** Interactive visual demonstrations for in-class use. Each demo includes setup, what to show, and key teaching points.

---

## Demo 1: The Gradient (Quick Visual)

**Tool:** Whiteboard drawing  
**Used in:** Session 1, minutes 8–12  
**Prep time:** None

### Setup

Draw $f(w) = w^2$ with a tangent line at $w = 2$.

### What to Draw

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

## Demo 2: GD on 1D Quadratic (Step by Step)

**Tool:** Whiteboard + Desmos  
**Used in:** Session 1, minutes 15–32  
**Prep time:** 5 minutes

### Setup

In Desmos, plot $f(w) = w^2$. Mark $w_0 = 3$.

### What to Show

**Part A: First Step (5 min)**

1. $f'(3) = 6$. Gradient points uphill (right).
2. $w_1 = 3 - 0.1 \times 6 = 2.4$. Moved LEFT (downhill). Loss: 9 → 5.76.

**Part B: Multiple Steps (5 min)**

| Step | $w$ | $f(w)$ | $f'(w)$ |
|------|-----|--------|---------|
| 0 | 3.000 | 9.000 | 6.000 |
| 1 | 2.400 | 5.760 | 4.800 |
| 2 | 1.920 | 3.686 | 3.840 |
| 3 | 1.536 | 2.359 | 3.072 |
| 20 | 0.036 | 0.001 | 0.072 |

**Part C: The Pattern (5 min)**

$w_{t+1} = w_t(1 - 2\eta) = 0.8\, w_t$. Geometric decay. "Steps get smaller as $w \to 0$ — gradient vanishes at the minimum."

### Teaching Points

- GD follows $-\nabla f$ (downhill).
- Steps shrink near the minimum (gradient → 0).
- Geometric decay: $w_t = w_0(1-2\eta)^t$.

---

## Demo 3: Learning Rate Regimes (Three Runs)

**Tool:** Desmos  
**Used in:** Session 1, minutes 32–48  
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
- If loss decreases too slowly: increase $\eta$. If it oscillates/increases: decrease $\eta$.

---

## Demo 4: 2D Gradient (Vector Field + Contour)

**Tool:** Desmos  
**Used in:** Session 1, minutes 55–62  
**Prep time:** 5 minutes

### Setup

Plot contour of $f(w_1, w_2) = w_1^2 + 4w_2^2$ (elongated bowl). Add gradient arrows.

### What to Draw

```
  w₂
    │
  2 │ ← ─ ─ ─ ─ →     ← Gradients point UPHILL (outward)
    │   ↗      ↖
  1 │ ←    ●    →     ← At minimum (0,0), gradient = 0
    │   ↙      ↘
  0 │──────────●──────── w₁
```

### What to Show

1. "Gradient points AWAY from center (uphill). GD steps INWARD (downhill)."
2. "Ellipses are elongated: steeper in $w_2$ than $w_1$. GD will zigzag."

### Teaching Points

- Gradient = vector pointing uphill.
- GD follows $-\nabla f$ (toward center).
- Elongated surface → zigzag → motivates feature scaling and momentum.

---

## Demo 5: SGD vs Batch GD Trajectory

**Tool:** Desmos or Python  
**Used in:** Session 2, minutes 45–57  
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

## Demo 6: Feature Scaling (Elongated vs Spherical)

**Tool:** Whiteboard  
**Used in:** Session 2, minutes 57–65  
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

## Demo 7: Training Loss Curves

**Tool:** Whiteboard  
**Used in:** Session 2, minutes 65–70  
**Prep time:** None

### What to Draw

**Good Convergence:**
```
  Loss
    │ ●
    │  ●●●●●●●●●●●  ← Plateau (converged)
    └────────────────── Steps
```

**Overfitting:**
```
  Loss
    │ ●  Training
    │  ●     ╱── Validation
    │   ●   ╱
    │    ● ╱
    │     ●──╲
    └────────── Steps    ← Gap = overfitting
```

**Divergence:**
```
  Loss
    │ ●
    │  ●
    │     ●
    │       ●         ← INCREASING
    │           ●     ← Divergence!
    └────────── Steps
```

### Teaching Points

- Steady decrease = good. Oscillation/divergence = reduce $\eta$.
- Training ↓ val ↑ = overfitting (regularize).
- Stuck at high loss = $\eta$ too small or model too simple.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Gradient as slope | S1 | 4 min | Whiteboard | Gradient = uphill, go opposite |
| 2 | GD on 1D quadratic | S1 | 17 min | Whiteboard + Desmos | Step-by-step GD |
| 3 | Learning rate regimes | S1 | 16 min | Desmos | Three runs: small/good/large |
| 4 | 2D gradient vector field | S1 | 7 min | Desmos | Contour, gradient direction |
| 5 | SGD vs batch GD | S2 | 12 min | Desmos | Noisy vs smooth |
| 6 | Feature scaling | S2 | 8 min | Whiteboard | Elongated vs spherical |
| 7 | Training loss curves | S2 | 5 min | Whiteboard | Monitoring: good/overfit/diverge |

**Total:** ~69 minutes. Leaves ~11 min/session for lecture, discussion, quizzes.

---

## Pre-Class Tech Check

- [ ] Desmos has $f(w) = w^2$ with point and tangent (Session 1)
- [ ] Desmos has three GD runs at different $\eta$ (Session 1)
- [ ] Desmos has 2D contour with gradient arrows (Session 1)
- [ ] Desmos/Python has SGD vs batch loss curves (Session 2)
- [ ] Whiteboard space for step-by-step GD table (Session 1)
- [ ] Whiteboard space for MSE gradient derivation (Session 2)
- [ ] Quiz printed or ready
