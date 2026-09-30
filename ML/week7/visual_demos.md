# Week 7 — Visual Demos

> **Purpose:** Interactive visual demonstrations for in-class use. Each demo includes setup, what to show, and key teaching points.

> **Note:** Demos for Sessions 1–2 are whiteboard-driven (review + derivations). Sessions 3–4 use Desmos for gradient descent and the sigmoid.

---

## Session 1 Demos (Review: Weeks 1–4)

### Demo 1: The Course Pipeline Map

**Tool:** Whiteboard
**Used in:** Session 1, minutes 0–5 (hook)
**Prep time:** None

### Setup

Draw once, keep on a side board all week:

```
   data → [model] → [loss] → [solver] → [evaluate]
   W1      W2       W2/W5     W6/W7      W4
                    ↑                      ↓
              overfitting? → W3 (regularize)
```

### What to Show

1. Point at each box; students name the week and the concept.
2. In Session 4, physically swap two labels: model → sigmoid, loss → cross-entropy. "Same skeleton, new task."

### Teaching Points

- ML knowledge compounds: new tasks are re-combinations of the same pipeline.
- Every future topic (CNNs, Transformers) is a variation on this diagram.

---

### Demo 2: The Complexity Dial (Reprised from Week 3)

**Tool:** Whiteboard or Desmos (scatter + polynomial fit sliders)
**Used in:** Session 1, minutes 35–45
**Prep time:** 5 min (or reuse Week 3 demo)

### Setup

A small scatter of ~10 points with mild quadratic trend. Fit polynomials of degree 1, 3, and 9.

### What to Show

1. Degree 1: too stiff — underfitting (high bias).
2. Degree 3: tracks the trend.
3. Degree 9: wiggles through every point — training error 0, test error large.
4. Plot training vs. test error against degree: the U.

### Teaching Points

- Training error is monotonically decreasing — a misleading compass.
- The U-curve is Week 3's dial; Session 2 turns it into the bias-variance theorem.

---

### Demo 3: Confusion Matrix as a Physical Grid

**Tool:** Whiteboard 2×2 grid + the fresh patient-screening problem
**Used in:** Session 1, minutes 45–58
**Prep time:** None (numbers in teaching_notes.md)

### Setup

Empty 2×2 grid on the board. Read the problem aloud sentence by sentence; students tell you where each number goes.

```
                    predicted +    predicted −
   actual +            TP=?           FN=?
   actual −            FP=?           TN=?
```

### What to Show

1. Fill the matrix from the story (TP = 42, FN = 8, FP = 78, TN = 872 — see teaching notes).
2. Compute accuracy first (91.4%) — let it look impressive.
3. Then precision (35%) and recall (84%) — the reversal.
4. Ask: "screening or confirmation — which metric matters?"

### Teaching Points

- Accuracy is a majority-class mirage under imbalance (prevalence 5%).
- The metric choice encodes the *cost* of errors (preview of threshold dial, Session 4).

---

## Session 2 Demos (Probability: MAP, Lasso, Bias-Variance)

### Demo 4: The Prior Shape Dictionary

**Tool:** Whiteboard, colored markers
**Used in:** Session 2, minutes 37–42 (Laplacian → Lasso)
**Prep time:** None

### Setup

Two panels side by side:

```
   Gaussian prior p(w)          Laplacian prior p(w)
        _.-""-._                       /\
      .'        '.                     /  \
     /            \                   /    \
    |              |       vs        |      |
  ──┴──────┬───────┴──  w          ──┴──────┴──  w
      smooth at 0                  corner at 0

   penalty: w²                      penalty: |w|
   ball: circle                      ball: diamond
   → shrink toward 0                → exact zeros
```

### What to Show

1. Trace the prior shape with your finger; overlay (in another color) the induced penalty — same shape, flipped.
2. Zoom in on the origin: smooth vs. corner.
3. Re-sketch Week 3's L2 circle / L1 diamond tangent to the loss contours.

### Teaching Points

- **The shape of the prior IS the shape of the penalty.** This dictionary is the whole content of MAP-regularization.
- Sparsity is a geometric accident of the corner — no magic.

---

### Demo 5: Bias-Variance as Dart Throws

**Tool:** Whiteboard (four targets)
**Used in:** Session 2, after the derivation (minutes 55–58)
**Prep time:** None

### Setup

Four dartboard-style targets:

```
   1. clustered at center   2. clustered, off-center
        (low bias,               (high bias,
         low variance)            low variance)

   3. scattered around center   4. scattered, off-center
        (low bias,                  (high bias,
         high variance)              high variance)
```

### What to Show

1. Each throw = one model trained on one random training set.
2. The bullseye = the true $f(x)$.
3. Ask students to label each target with Bias²/Variance levels — then map to model complexity (simple model → 2; huge model → 3).

### Teaching Points

- Bias = systematic offset of the *cluster center*; variance = spread of the cluster.
- Increasing complexity moves you from target 2 toward target 3 — trading one error for the other.

---

## Session 3 Demos (Gradient Descent)

### Demo 6: Three Learning Rates on $f(w) = w^2$

**Tool:** Desmos (or any graphing tool)
**Used in:** Session 3, minutes 16–24
**Prep time:** 10 min (setup below)

### Setup

Desmos: plot $f(w) = w^2$. Add a point at $w_0 = 3$. Compute iterations for $\eta \in \{0.01, 0.1, 1.1\}$ (a spreadsheet or table column helps):

| $t$ | $\eta=0.01$ | $\eta=0.1$ | $\eta=1.1$ |
|-----|-------------|------------|------------|
| 0 | 3.000 | 3.000 | 3.000 |
| 1 | 2.940 | 2.400 | −3.600 |
| 2 | 2.881 | 1.920 | 4.320 |
| 3 | 2.824 | 1.536 | −5.184 |
| 4 | 2.767 | 1.229 | 6.221 |
| ... | ... | ... | ... |
| 20 | 2.451 | 0.036 | (exploded) |

### What to Show

1. **Before each run, students predict** the trajectory.
2. $\eta = 0.01$: crawl (after 20 steps still $w \approx 2.45$).
3. $\eta = 0.1$: smooth geometric decay ($w_{20} \approx 0.036$).
4. $\eta = 1.1$: sign-flipping explosion — $3, -3.6, 4.32, -5.18, \ldots$
5. Mark the multiplication factors: $0.98$, $0.8$, $|1-2\cdot 1.1| = 1.2$.

### Teaching Points

- One number changes crawl → converge → explode.
- Convergence $\iff |1 - \eta a| < 1$: derive it live from the table's factors.
- The loss curve alone diagnoses the regime — no need to see the surface.

---

### Demo 7: The Valley — Why Feature Scaling Matters

**Tool:** Whiteboard sketch (or contour plot printout)
**Used in:** Session 3, minutes 60–64
**Prep time:** None

### Setup

Two contour maps side by side:

```
   Elongated valley (unscaled)      Spherical bowl (standardized)
   ┌────────────────────┐           ┌────────────────────┐
   │  ╲ ╲ ╲             │           │       ◎ ◎          │
   │   ╲ ╲ ╲   ← zigzag │           │     ◎ ◎ ◎ ◎        │
   │    ╲ ╲ ╲           │           │    ◎ ◎ + ◎ ◎       │
   │     ╲ ╲ ╲          │           │     ◎ ◎ ◎ ◎        │
   │      ★             │           │       ◎ ◎          │
   └────────────────────┘           └────────────────────┘
```

### What to Show

1. On the valley: draw GD stepping across the narrow direction, overshooting, zigzagging down the long direction.
2. On the bowl: straight descent.
3. Annotate: "feature 1 ∈ [0, 1], feature 2 ∈ [0, 1000]" → valley.

### Teaching Points

- Different scales → different curvatures $a_1, a_2$ → no single $\eta$ satisfies both stability limits.
- Standardization makes one $\eta$ work everywhere.
- The leakage trap: compute $\bar{x}, \sigma$ on training only — split first.

---

### Demo 8: Batch vs. SGD Trajectories

**Tool:** Whiteboard sketch
**Used in:** Session 3, minutes 52–60
**Prep time:** None

### Setup

One loss curve plot, two paths drawn over it:

```
   loss
    │╲
    │ ╲ ── smooth monotone path (batch GD)
    │  ╲＿＿＿＿
    │ ╱╲  ╱╲   ╱╲ ── noisy path (SGD, same average slope)
    │╱  ╲╱  ╲╱   ╲＿＿＿＿
    └──────────────────────→ steps
```

### What to Show

1. Same average descent rate, very different texture.
2. Zoom conceptually: each SGD step uses ONE point's gradient $-2x_i r_i$; batch uses the average.
3. On a non-convex sketch (two valleys): the noisy path escapes the shallow valley.

### Teaching Points

- SGD gradient is unbiased but noisy; variance $\propto 1/B$.
- The noise is a feature for non-convex problems (neural networks), a nuisance for convex ones.

---

## Session 4 Demos (Logistic Regression I)

### Demo 9: The Sigmoid Live

**Tool:** Desmos with slider
**Used in:** Session 4, minutes 12–25
**Prep time:** 5 min

### Setup

Plot $\sigma(z) = 1/(1+e^{-z})$. Add slider for $z$ from $-8$ to $8$, displaying $\sigma(z)$ and the tangent-line slope at that point (Desmos can show the derivative $d/dz$).

### What to Show

1. Slide $z$: point rides the S-curve; read off $\sigma$.
2. $z = 0$: value $1/2$, steepest slope ($1/4$). Verify against the formula $\sigma(1-\sigma) = 0.25$.
3. $z = \pm 6$: value pinned near 0/1, slope ≈ 0 — **saturation**.
4. Toggle on the plot of $\sigma'(z)$: a bump, max at 0, dies at the tails.

### Teaching Points

- The sigmoid squashes $\mathbb{R} \to (0,1)$ — probabilities.
- $\sigma' = \sigma(1-\sigma)$: derivative written in terms of the function itself.
- Saturation: slope vanishes when confident — the seed of the vanishing-gradient story (Week 15).

---

### Demo 10: Decision Boundary in 2D

**Tool:** Whiteboard (or Desmos scatter with $\sigma(w_1x_1 + w_2x_2 + b) > 0.5$ region shaded)
**Used in:** Session 4, minutes 25–33
**Prep time:** 5 min

### Setup

Scatter of two classes (e.g., "pass" ● and "fail" ○ on (hours studied, hours sleep)). Draw a separating line. Mark the normal vector $w$.

### What to Show

1. Shade the $\sigma > 1/2$ side: the line is the decision boundary.
2. Walk a point toward the line: $P \to 1/2$. "The model announces uncertainty at the border."
3. Walk a point far from the line on the wrong side: $P \approx 0$ for its class — "confidently wrong; cross-entropy will punish this without mercy" (Session 4, Section 19).
4. Rotate the line (different $w$): which points change side?
5. Sketch the un-separable case (XOR / concentric circles): no line works → preview W12 (features) and W15 (neural nets).

### Teaching Points

- Linear boundary; $w$ = normal; distance from boundary = confidence.
- Probability output ≠ bare label: thresholds are a *dial* (cost-sensitive classification, Challenge 7-4C).

---

### Demo 11: Cross-Entropy vs. Squared Error on a Probability

**Tool:** Desmos
**Used in:** Session 4, minutes 50–58
**Prep time:** 5 min

### Setup

Plot, for a fixed true label $y = 1$, two curves against the model's predicted probability $\hat p \in (0,1)$:

- $L_{\text{CE}}(\hat p) = -\log \hat p$
- $L_{\text{MSE}}(\hat p) = (1 - \hat p)^2$

### What to Show

1. Both vanish at $\hat p = 1$.
2. As $\hat p \to 0$: MSE → 1; cross-entropy → ∞. Zoom out to show the CE curve blowing up.
3. Near $\hat p = 1$: CE has slope $-1/\hat p$ — still nonzero gradient; MSE flattens (slope $-2(1-\hat p) \to 0$).

### Teaching Points

- Cross-entropy keeps a strong learning signal even when the model is nearly right (and an unbounded penalty when confidently wrong).
- MSE on probabilities loses gradient exactly when the sigmoid saturates — the pathology cross-entropy's cancellation removes (Session 4 preview / Week 8 derivation).
