# Week 3 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): Polynomial Regression & the Generalization Gap

### Learning Objectives

By the end of this session, students should be able to:
1. Explain how polynomial regression is linear in parameters but nonlinear in features.
2. Describe the degree-vs-data tradeoff and identify when a model is underdetermined.
3. State why training error is monotonically non-increasing with model complexity.
4. Explain why test error has a U-shape and identify the sweet spot.
5. Diagnose underfitting vs. overfitting from training and test errors alone.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos open in browser with polynomial regression demo pre-loaded (see `visual_demos.md`, Demos 1–2)
- Printed or projected handout Sections 1–3
- Week 2 quiz results reviewed (spiral-back topics identified)

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Week 2.** Quick: "What is the ridge slope formula? What does λ do?" |
| 0:05–0:15 | **Hook: "If training error always goes down, why not use the most complex model?"** | See Hook section below. |
| 0:15–0:30 | **Polynomial regression: linear in parameters, nonlinear in features.** | Core concept. Write the polynomial model on the board. Emphasize: OLS machinery still applies. |
| 0:30–0:45 | **Visual demo: degree 1 vs. 3 vs. n−1 on same data.** | Use Desmos (Demo 1). This is the centerpiece. Make overfitting visceral. |
| 0:45–0:55 | **The degree-vs-data table and the fundamental observation.** | Board work. Training error monotonically decreases; test error is U-shaped. |
| 0:55–0:65 | **The generalization gap and the diagnostic table.** | Fill in the table WITH students. This is exam-critical. |
| 0:65–0:72 | **The complexity curve (U-shaped test error).** | Draw it on the board. Label axes, zones, sweet spot. |
| 0:72–0:80 | **Quiz (end-of-session).** 8–10 min. See `quiz_S1.md`. |

### Hook: "Why Not Always Use the Most Complex Model?" (10 min)

**Goal:** Create intellectual tension. Students know from Week 1 that overfitting exists, but they haven't seen *why* training error is misleading.

**Instructions:**

1. Remind students: "Last week, we saw that a degree-7 polynomial through 8 points gives zero training error. We said that's bad. But *why* is it bad? The training error is literally zero — isn't that the best possible?"
2. Let students struggle with this for a minute. They'll say things like "it doesn't generalize" — push them: "What does 'generalize' mean? Why doesn't zero training error guarantee good test performance?"
3. Write the central question on the board: **"If training error always goes down when we make the model more complex, why doesn't the most complex model always win?"**
4. Say: "Today we answer this rigorously. By the end of this session, you'll be able to diagnose any model's health from two numbers: training error and test error."
5. Transition: "First, let's see how to make our linear model nonlinear."

**Common student responses to watch for:**
- "Just use cross-validation." → Acknowledge, but say "that's next week. Today we need to understand *why* it works, not just the recipe."
- "More parameters = more overfitting." → Partially right, but push: "Is it the number of parameters alone, or the ratio of parameters to data?" Lead them to the degree-vs-data table.

### Board Work: Polynomial Regression (15 min)

**Draw on the board (keep visible for the rest of the session):**

```
Linear model:       ŷ = w₁x + w₀                    (2 parameters)

Polynomial model:   ŷ = w_d x^d + ... + w₁x + w₀    (d+1 parameters)

KEY INSIGHT: Still LINEAR in the parameters (w₀, w₁, ..., w_d).
             NONLINEAR in the feature x (because x², x³, etc.)
             
The OLS machinery from Week 2 applies — we just have more features.
(Week 8: matrix form makes this precise.)
```

**Key teaching moves:**
1. Write the polynomial model and circle the parameters. "These are what we solve for. The model is linear in these."
2. Write x, x², x³ as separate "features." Say: "We haven't changed the algorithm — we've changed the features. The model is still a linear combination, just of transformed inputs."
3. Connect to Week 2: "Ridge regression works here too. The penalty applies to all the w's. We'll see this in Session 2."
4. Emphasize the parameter count: "A degree-d polynomial has d+1 parameters. With n data points, when d+1 = n, the model can pass through every point."

### Board Work: The Degree-vs-Data Table (10 min)

**Draw this table on the board and fill it in WITH students (ask them what happens at each stage):**

```
Condition         | What happens
──────────────────|──────────────────────────────────────────
d+1 ≪ n          | Model can't fit all patterns → underfitting risk
d+1 ≈ n          | Model fits well → good if pattern is polynomial
d+1 = n          | Passes through every point → zero training error
d+1 > n          | Infinitely many perfect fits → underdetermined
```

**Then add the fundamental observation below the table:**

```
TRAINING ERROR: monotonically ↓ with degree (never goes up)
TEST ERROR:     U-shaped (↓ then ↑) — the generalization gap
```

**Key teaching moves:**
- Ask: "Why can't training error go up when you increase degree?" → Lead to: a higher-degree polynomial can always do everything a lower-degree one can (set extra coefficients to zero) plus more.
- Ask: "What happens between data points when d+1 = n?" → The polynomial oscillates wildly. Those oscillations are the model inventing patterns in noise.
- Use the memorization analogy from the handout (Section 2.6). Students remember it from Week 1 — reinforce it here.

### Board Work: The Diagnostic Table (7 min)

**This is the exam-critical table.** Students must be able to look at training/test errors and immediately diagnose.

**Draw and fill in WITH students:**

```
Symptom                    | Diagnosis     | Prescription
───────────────────────────|───────────────|──────────────────────────
Both high, small gap       | Underfitting  | Increase complexity
Low train, high test,      | Overfitting   | Decrease complexity or
  large gap                |               | add regularization
Both low, small gap        | Good fit      | Done! (Check with more data)
```

**Key teaching moves:**
- Write three example (train MSE, test MSE) pairs on the board: (15, 16), (2, 3), (0.01, 28). Ask students to diagnose each.
- Emphasize: "You don't need to see the model. Two numbers tell you everything."
- Warning: "Both low, small gap" could also mean the test set is too easy or leaked. We'll cover this in Week 4.

### Discussion Prompts

Use these at the indicated times to keep students engaged:

1. **(After the degree-vs-data table):** "You have 10 data points. What's the highest degree polynomial you'd consider? What would degree 9 do? What about degree 15?" — Tests whether they understand the interpolation threshold and the underdetermined regime.

2. **(After the diagnostic table):** "I give you a model with training MSE = 0.5 and test MSE = 0.7. Is this overfitting?" — Answer: No! The gap is small. Both errors are low. This is a good fit. Many students will say "overfitting" because test > train. The gap must be *large* relative to the errors to indicate overfitting.

3. **(After the complexity curve):** "Where on the U-curve would you rather be — slightly left of the sweet spot (underfit) or slightly right (overfit)?" — Answer: slightly left (underfit). Underfit models are stable and interpretable; overfit models are fragile and can fail catastrophically on new data. This is a practitioner's instinct.

### Things NOT to Cover (Save for Later)

| Topic | When |
|-------|------|
| Cross-validation, train/test split methodology | Week 4 |
| Formal bias-variance decomposition (with probability) | Week 5 |
| Gradient descent (how to actually solve) | Week 6 |
| Matrix form of polynomial regression | Week 8 |
| Double descent phenomenon (beyond teaser) | Week 18 |
| VC dimension, Rademacher complexity | Week 18 |

**Resist the urge to formalize the bias-variance tradeoff with probability.** Students don't have probability yet. The intuition (stable vs. unstable, consistently wrong vs. fits noise) is sufficient this week.

---

## Session 2 (80 min): Regularization in Depth — Ridge, Lasso, and the Complexity Dial

### Learning Objectives

By the end of this session, students should be able to:
1. Explain how ridge regression shrinks weights and why this prevents overfitting.
2. Describe the bias-variance intuition (without probability): how λ trades bias for variance.
3. Explain why lasso produces sparsity using the L1 diamond geometry.
4. Compare ridge, lasso, and elastic net: when to use each.
5. State the complexity dial principle: degree, λ, k, depth are all the same knob.
6. Perform basic residual analysis and diagnose underfitting from residual patterns.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos open with ridge regression demo and L1/L2 geometry demo (see `visual_demos.md`, Demos 3–4)
- Printed or projected handout Sections 4–8
- Session 1 quiz results reviewed

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** Quick: "Diagnose: train MSE = 0.01, test MSE = 28. What's the problem?" |
| 0:05–0:15 | **Ridge regression revisited: the λ knob.** | Review Week 2 ridge formula. Show the λ table. |
| 0:15–0:25 | **Visual demo: ridge shrinking weights.** | Desmos (Demo 3). Show how slope changes with λ. |
| 0:25–0:35 | **Bias-variance intuition (without probability).** | Board work. Fill in the bias-variance table. |
| 0:35–0:40 | **The validation curve.** | How to choose λ. Preview of cross-validation (Week 4). |
| 0:40–0:55 | **Lasso: sparsity and L1 geometry.** | Core concept. Draw the diamond vs. circle. Use Desmos (Demo 4). |
| 0:55–0:60 | **No closed form for lasso.** | Explain nondifferentiability at w=0. Preview gradient descent (Week 6). |
| 0:60–0:65 | **Elastic net.** | Brief. Best of both worlds. |
| 0:65–0:70 | **The complexity dial: unifying diagram.** | Board work. Draw the universal table. |
| 0:70–0:72 | **Residual analysis (brief).** | Use Demo 5 if time permits, or board drawings. |
| 0:72–0:80 | **Quiz (end-of-session).** 10 min. See `quiz_S2.md`. |

> **Note:** This session is dense. If running behind, trim the residual analysis section (it's covered in the handout and can be reviewed independently). Do NOT cut the L1/L2 geometry — it's the conceptual core of Session 2.

### Board Work: Ridge Regression — The λ Knob (10 min)

**Start by recalling the ridge formula from Week 2 (write it on the board):**

```
Ridge loss:  R(w,b) = (1/n)Σ(wxᵢ + b - yᵢ)² + λw²

Ridge slope: w*_ridge = Cov(x,y) / (Var(x) + λ)

λ = 0:      OLS (no penalty) → can overfit
λ small:    slight penalty → weights somewhat constrained
λ moderate: sweet spot → weights controlled, fits signal not noise
λ → ∞:     w → 0 → predicts ȳ for everything (extreme underfitting)
```

**Key teaching moves:**
- Ask: "What happens to the slope as λ increases?" → It shrinks toward zero. The denominator grows.
- Ask: "When λ → ∞, what does the model predict?" → ȳ for everything. The model becomes a constant.
- Emphasize: "λ is a dial. 0 = full complexity (OLS), ∞ = zero complexity (constant). The art is finding the right setting."
- Connect to Session 1: "Ridge with polynomial features prevents the wild oscillations we saw. The penalty keeps coefficients small, so the polynomial can't oscillate."

### Board Work: Bias-Variance Intuition (10 min)

**Draw this table on the board and fill it in WITH students:**

```
                    λ=0 (OLS)    λ moderate    λ→∞
                    ─────────    ──────────    ────
Training error      Lowest       Slightly ↑    Highest (≈Var(y))
Test error          Can be high  Lowest        High
Weights             Large        Moderate      ≈ 0
Stability           Low          Moderate      High (always ȳ)
Bias                Low          Moderate      High
Variance            High         Moderate      Low
```

**Key teaching moves:**
- Emphasize: "We're using 'bias' and 'variance' informally. Bias = how far off the model is on average. Variance = how much the model changes with different training data. The formal mathematical decomposition comes in Week 5 with probability."
- Say the key intuition aloud: "OLS has low bias (tries hard to fit data) but high variance (fits noise, so changes wildly with different data). Ridge trades a small increase in bias for a large decrease in variance. The net effect is lower test error."
- Ask: "Where is the sweet spot?" → Moderate λ. Low bias + low variance. The minimum of Bias² + Variance.
- Use the bullseye analogy from Week 1 (Demo 5) to reinforce: OLS = scattered around center (low bias, high variance); large λ = clustered but off-center (high bias, low variance); moderate λ = clustered near center (good).

### Board Work: The Validation Curve (5 min)

**Draw on the board:**

```
  Validation error
    │
    │  ╱╲
    │ ╱  ╲
    │╱    ╲
    │      ╲──────
    │
    └────────────── λ (log scale)
    0   small   large
    
    ← overfit  sweet  underfit →
              spot
```

**Key teaching moves:**
- "We try several λ values and plot the validation error. We pick the λ that minimizes it."
- "Notice: this is also a U-shape! Same as the polynomial degree curve. It's the same phenomenon — too little regularization overfits, too much underfits."
- Preview: "Next week, we'll formalize this with cross-validation — a systematic way to estimate validation error."

### Board Work: L1 vs. L2 Geometry (15 min)

**This is the most important board work of Session 2.** Draw the constraint geometry carefully.

**Step 1: Write the two penalties side by side:**

```
Ridge (L2):  penalty = λ Σ wⱼ²     constraint: ‖w‖² ≤ t  (ball/sphere)
Lasso (L1):  penalty = λ Σ |wⱼ|    constraint: ‖w‖₁ ≤ t  (diamond/cross-polytope)
```

**Step 2: Draw the geometry (2D, w₁-w₂ plane):**

```
     L2 (Ridge)                    L1 (Lasso)
        w₂                            w₂
        │  ╱                          │  ╱
        │ ╱●  ← solution              │●  ← solution (on a corner!)
        │╱╲                           │╲ ╲
   ─────●──●──── w₁             ─────●  ●──── w₁
       ╱│╱                           ╱│ ╲
      ╱ │                          ╱  │  ╲ ← diamond
     ●  │                         ●   │   ●
        │                              │
```

**Step 3: Explain the key difference:**

```
Ridge: solution touches the CIRCLE at the closest point to OLS.
       Usually NOT on an axis → all weights nonzero (but small).

Lasso: solution touches the DIAMOND at a CORNER.
       Corners are ON the axes → some weights are EXACTLY ZERO.
       → Feature selection! Lasso eliminates irrelevant features.
```

**Key teaching moves:**
- Walk slowly through the geometry. Point to the circle and say: "The OLS solution is somewhere out there. Ridge pulls it back to the nearest point on the circle — usually not on an axis."
- Point to the diamond: "The lasso solution often lands on a corner. At a corner, one of the w's is zero. That feature is eliminated."
- Ask: "Why does the lasso solution land on a corner?" → Because the diamond's corners stick out along the axes. The closest point on the diamond to the OLS solution is often a corner.
- Emphasize: "This is a GEOMETRIC explanation. No calculus needed. The shape of the constraint determines the type of solution."

### Board Work: No Closed Form for Lasso (5 min)

**Write on the board:**

```
|w| is NOT differentiable at w = 0.

  Left derivative:  -1
  Right derivative: +1
  
  At w = 0, there's a "corner" — no unique derivative.

→ Can't set gradient = 0 and solve (unlike ridge).
→ Lasso has NO closed-form solution.
→ Requires iterative optimization (coordinate descent, proximal gradient).

This is EXACTLY why lasso produces sparsity:
the optimum often occurs AT a corner (where some wⱼ = 0).
```

**Key teaching moves:**
- Draw the absolute value function |w| and point to the corner at w = 0. Contrast with w² (smooth parabola).
- Say: "The nondifferentiability is not a bug — it's the feature. The corners are where weights become zero. If |w| were smooth, lasso wouldn't produce sparsity."
- Preview: "When we learn gradient descent in Week 6, we'll see how to handle nonsmooth functions with subgradient methods."

### Board Work: The Complexity Dial (5 min)

**Draw this table on the board (the unifying principle):**

```
Model                  | Knob     | Low complexity   | High complexity
───────────────────────|──────────|──────────────────|──────────────────
Polynomial regression  | Degree d | d=1 (line)       | d=n−1 (through all)
Ridge regression       | λ        | λ→∞ (w→0)        | λ=0 (OLS)
Lasso                  | λ        | λ→∞ (w→0)        | λ=0 (OLS)
k-NN (Week 9)          | k        | k=n (predict ȳ)  | k=1 (memorize)
Decision trees (W10)   | Depth    | Depth 1 (stump)  | Depth ∞ (memorize)
Neural networks (W15)  | # params | Few neurons      | Millions of neurons
```

**Then draw the universal curve:**

```
  Error
    │
    │  Test ╱╲
    │      ╱  ╲
    │     ╱    ╲
    │    ╱      ╲
    │   ╱        ╲
    │  ╱ Train    ╲
    │ ╱  (always ↓) ╲
    │╱                ╲
    └────────────────── Complexity
     (degree, 1/λ, 1/k, depth, ...)
```

**Key teaching moves:**
- "This is the most important picture in machine learning. Every model, every knob — same curve."
- Ask: "For ridge, which direction on the x-axis is 'more complex'?" → Left (λ small) is more complex. So the x-axis would be 1/λ, not λ.
- Ask: "For k-NN, which direction is more complex?" → k small is more complex. The x-axis would be 1/k.
- Emphasize: "The x-axis label changes, but the shape never does. This is the universal law of the overfitting-underfitting tradeoff."

### Residual Analysis (Brief — 2 min)

If time permits, draw the two residual plots on the board:

```
  Good fit (random):      Underfit (U-shape):
  e                       e
  │  • •                  │      •
  │•   •                  │    •   •
  │ • •                   │  •       •  ← pattern!
  │  • •                  │•           •
  │    •                  │
  └────── x               └────────── x
```

**Key message:** "If residuals show a pattern, the model is systematically wrong — it's underfitting. If residuals are random, the model captured all the signal. This connects to Week 2: the OLS residuals are uncorrelated with x. If they ARE correlated (show a pattern), we need polynomial features or a different model."

### Anticipated Questions from Students

| Question | How to Answer |
|----------|--------------|
| "Why not just always use elastic net?" | Good default in practice. But elastic net has TWO hyperparameters (λ₁, λ₂) instead of one — harder to tune. If you know you want sparsity, use lasso. If you know all features matter, use ridge. Elastic net is the "I'm not sure" choice. (30 seconds.) |
| "How do you know the true relationship is polynomial?" | You don't. Polynomial regression is one hypothesis space. The true relationship could be anything. We use polynomials because they're flexible and well-understood. Neural networks (Week 15) can approximate any continuous function. But the overfitting tradeoff is the same. (30 seconds.) |
| "What's the difference between validation and test data?" | Validation data is used to choose λ (or degree). Test data is used ONCE at the end to estimate final performance. You should never look at the test set during model development. We'll formalize this in Week 4. (30 seconds.) |
| "Is deep learning immune to overfitting?" | No! Deep learning is MORE prone to overfitting because neural networks have millions of parameters. That's why techniques like dropout, weight decay (which is L2 regularization!), and data augmentation exist. We'll see these in Weeks 15–16. (30 seconds.) |
| "Why is λ on a log scale?" | Because the effect of λ is multiplicative, not additive. Going from λ=0.01 to 0.1 is the same "step" as going from 0.1 to 1. The log scale makes the U-curve symmetric. In practice, we always search λ on a log grid: 0.001, 0.01, 0.1, 1, 10, 100. (30 seconds.) |
| "Can you combine polynomial features with lasso?" | Yes! And it's a great idea. Lasso with polynomial features will select the most important degrees and zero out the rest. This is automatic model selection — the lasso decides which polynomial terms matter. (15 seconds.) |
| A sharp student asks about double descent | "Great question! We previewed this in Week 1. The U-curve is the classical picture. In the over-parameterized regime (d+1 ≫ n), test error can decrease again. We'll cover this in Week 18. For now, the U-curve is the right mental model." Write it on the parking lot board. |
| "Why isn't the intercept regularized?" | The intercept b just shifts all predictions by a constant. It doesn't cause oscillations or overfitting in the way that large slopes do. Regularizing the intercept would just force the model to predict ȳ, which is too aggressive. (15 seconds.) |

### Common Misconceptions to Address Proactively

| Misconception | Correction |
|---------------|------------|
| "Overfitting means test error > training error" | Not necessarily. Overfitting means a LARGE gap between train and test. A small gap with test slightly above train is normal and healthy. |
| "More data always fixes overfitting" | More data helps, but it doesn't always fix overfitting. If the model is complex enough to memorize, it will. More data relative to parameters reduces overfitting, but the ratio matters, not the absolute amount. |
| "Ridge and lasso do the same thing" | They both regularize, but differently. Ridge shrinks all weights toward zero (none become exactly zero). Lasso pushes some weights to exactly zero (feature selection). The geometry is different (circle vs. diamond). |
| "Lasso is always better because it does feature selection" | No. If all features are genuinely relevant (many small effects), ridge is better. Lasso is better when only a few features matter. Using lasso when all features matter will drop useful features. |
| "The U-curve only applies to polynomials" | No! The U-curve is universal. It applies to every model and every complexity knob. This is the complexity dial principle. |
| "Bias and variance are opposites" | They're related but not opposites. They're two components of error. Increasing one doesn't always decrease the other. The goal is to minimize their SUM (plus irreducible error), not to zero out either one. |
| "Training error going down is always good" | No! Training error going down while test error goes up means you're overfitting. Training error is a misleading metric on its own. |

### Differentiation Notes

**For struggling students:**
- The L1/L2 geometry is the hardest concept. After class, offer to redraw the diamond and circle one more time. Give them the comparison table from the handout (Section 5.4) as a reference.
- Focus them on the diagnostic table (Section 3.4) and the complexity dial table (Section 6.1). These are the most testable concepts.
- Reassure them: "The bias-variance decomposition will be formalized in Week 5. For now, you only need the intuition: ridge makes the model more stable (less variance) at the cost of being slightly more wrong on average (more bias)."
- If they're confused by lasso's nondifferentiability, say: "Just remember: lasso has corners, ridge doesn't. Corners = zeros. That's all you need for now."

**For advanced students:**
- They may find the bias-variance intuition too informal. Redirect them to the ★ exercises (E9–E12) in the handout, especially the double descent question (E10) and the bias-variance sketching question (E11).
- Mention: "If you already know about L1 regularization, try to derive WHY the lasso solution lands on a corner. Think about the Lagrangian and the KKT conditions. We'll cover this formally in Week 8."
- In class, when asking questions, direct the diagnostic questions to struggling students and the geometric/probabilistic questions to advanced students. Example: "Diagnose this model from its errors" (anyone) → "Why does the L1 penalty produce zeros but L2 doesn't? Explain geometrically." (advanced).

---

## Challenge Questions for Advanced Students

> **How to use these:** Give these to sharp students *during* class when they finish an activity early, or as "think about this while I explain the basics to others" prompts. They are NOT extra homework — they are conversation starters. Follow up with these students individually or in a small group during breaks or after class.
>
> **Delivery:** Write the question on a sticky note, slip it to the student, or display it on a side board. Say: "While we review [topic], think about this. Let's discuss after class or during the break."
>
> **Principle:** Every challenge is tied to a Week 3 concept but pushes *deeper* — either toward a topic we'll cover later (creating anticipation) or toward a subtlety that most students won't notice (building analytical thinking).

---

### Session 1 Challenges

**Challenge 3-A: Proving Monotonicity**
*(Give after the degree-vs-data table — around minute 50)*

> We claimed that training error is a monotonically non-increasing function of polynomial degree $d$. That is, if $d_1 < d_2$, then $R_{\text{train}}(d_2) \leq R_{\text{train}}(d_1)$.
>
> **Question:** Prove this. *(Hint: A degree-$d_1$ polynomial is a special case of a degree-$d_2$ polynomial. Think about what the optimizer can do with the extra parameters.)*

**Instructor notes:**
- Key argument: The set of degree-$d_2$ polynomials CONTAINS the set of degree-$d_1$ polynomials (just set the extra coefficients to zero). So the minimum of the loss over degree-$d_2$ polynomials is at most the minimum over degree-$d_1$ polynomials.
- Formal version: $\mathcal{H}_{d_1} \subset \mathcal{H}_{d_2}$, so $\min_{f \in \mathcal{H}_{d_2}} R_{\text{emp}}(f) \leq \min_{f \in \mathcal{H}_{d_1}} R_{\text{emp}}(f)$.
- This is a nested hypothesis space argument. It's the same logic as: "searching a bigger space can only find something better (or equal)."
- **Follow-up:** "Does this argument work for k-NN? Is training error monotonic in k?" → No! k-NN is not nested in the same way. k=1 has zero training error, but k=2 has higher training error. The monotonicity is specific to nested hypothesis spaces (like polynomials).

---

**Challenge 3-B: The Interpolation Threshold**
*(Give after the complexity curve — around minute 60)*

> We said that when $d+1 = n$ (parameters = data points), the polynomial passes through every point exactly. When $d+1 > n$, there are infinitely many such polynomials.
>
> **Question:** When $d+1 > n$ and there are infinitely many zero-training-error polynomials, which one does OLS pick? Is the choice unique? What happens to the test error? Can you reason about this without knowing the matrix form of OLS?

**Instructor notes:**
- When $d+1 > n$, the system is underdetermined. OLS (in matrix form) uses the pseudoinverse, which picks the minimum-norm solution: the polynomial with the smallest $\sum w_j^2$ among all zero-error solutions.
- This is actually implicit regularization! The minimum-norm solution tends to be "simple" among the infinitely many perfect-fit solutions.
- In the scalar case, this is hard to see without matrices. The key intuition: OLS doesn't just find *a* solution — it finds a specific one with desirable properties.
- **Follow-up:** "This connects to double descent (Week 18). In the over-parameterized regime, the minimum-norm solution can actually generalize well. The U-curve isn't the whole story." Seeds Week 18.

---

**Challenge 3-C: The Double Descent Teaser (Revisited)**
*(Give after the complexity curve — around minute 65)*

> Last week (Week 1), we previewed double descent: test error goes down AGAIN past the interpolation threshold. Now you understand the classical U-curve. Let's think deeper.
>
> **Question:** (a) Sketch the full double-descent curve (test error vs. degree), labeling the interpolation threshold $d+1 = n$. (b) Why might having MORE parameters than data points lead to BETTER generalization? (c) What does this imply about the classical overfitting tradeoff? Is it wrong?

**Instructor notes:**
- (a) The curve: test error goes up as $d+1 \to n$ (the U-curve peak), then at $d+1 = n$ there's a spike (the interpolation threshold — the unique interpolating polynomial can be wild), then as $d+1 > n$ and increases further, test error decreases again.
- (b) In the over-parameterized regime, there are many zero-training-error solutions. The optimizer (or OLS pseudoinverse) picks a "good" one — the minimum-norm solution. This implicit regularization can lead to better generalization than any solution in the under-parameterized regime.
- (c) The classical tradeoff isn't wrong — it applies in the under-parameterized regime. But it's incomplete. The full picture includes the over-parameterized regime where more parameters can help. This is an active research area (Belkin et al., 2019).
- **Follow-up:** "Does this mean we should always use the biggest model possible?" → Not necessarily. The over-parameterized regime requires lots of data and careful optimization. And the spike at the interpolation threshold can be catastrophic. Seeds Week 18.

---

**Challenge 3-D: The Noise Membrane**
*(Give after the generalization gap discussion — around minute 60)*

> We said that overfitting happens because the model fits noise. But what IS noise? Is it a property of the data, or a property of the model?
>
> **Question:** Consider data generated by $y = f(x) + \epsilon$ where $f$ is the true function and $\epsilon$ is random noise. If I use a degree-1 model and the true function is degree-3, is the "noise" from the model's perspective the same as the $\epsilon$ in the data-generating process? What does this mean for the concept of "fitting noise"?

**Instructor notes:**
- From the degree-1 model's perspective, everything it can't capture is "noise" — including both the random $\epsilon$ AND the higher-order terms ($x^2$, $x^3$) of the true function.
- So "noise" is model-relative. What looks like noise to a degree-1 model is signal to a degree-3 model.
- The true irreducible noise is only $\epsilon$. The rest is "model misspecification noise" — the model is too simple to capture the real pattern.
- This is a deep point: underfitting looks like noise to the model. The model can't distinguish "random fluctuation" from "pattern I can't represent."
- **Follow-up:** "This is why residual analysis matters. If the residuals show a pattern (not random), the 'noise' isn't really noise — it's signal the model is missing." Connects to Section 7 of the handout.

---

**Challenge 3-E: The Data Size Question**
*(Give during the degree-vs-data table — around minute 50)*

> The degree-vs-data table says $d+1 \ll n$ is good and $d+1 = n$ is overfitting. But how many data points do you ACTUALLY need for a degree-$d$ polynomial to generalize well?
>
> **Question:** (a) As a rule of thumb, how many data points per parameter would you want? (b) Does this depend on the noise level? (c) Does this depend on the true function? (d) What if the true function IS a degree-$d$ polynomial with no noise — how many points do you need then?

**Instructor notes:**
- (a) A common rule of thumb is 10× data points per parameter (so ~10(d+1) data points for a degree-$d$ polynomial). But this is highly problem-dependent.
- (b) Yes. More noise → more data needed to distinguish signal from noise. With zero noise, $d+1$ points suffice (the polynomial is uniquely determined).
- (c) Yes. If the true function is simple (e.g., degree 2) and you're using degree 10, the extra coefficients should be near zero — you need less data to "confirm" they're zero than to estimate nonzero coefficients.
- (d) If the true function is exactly a degree-$d$ polynomial with no noise, $d+1$ points suffice (the interpolating polynomial IS the true function). But in practice, we never know the true degree or whether there's noise.
- **Follow-up:** "This is why sample complexity theory (Week 17) is important. It tells us how much data we need as a function of model complexity and noise level."

---

### Session 2 Challenges

**Challenge 3-F: Deriving the Ridge Solution**
*(Give after the ridge formula recap — around minute 10)*

> Last week, we used the ridge formula $w^*_{\text{ridge}} = \text{Cov}(x,y) / (\text{Var}(x) + \lambda)$ without deriving it. Now you know enough to derive it yourself.
>
> **Question:** The ridge loss is $R(w) = \frac{1}{n}\sum_{i=1}^n (wx_i + b - y_i)^2 + \lambda w^2$. Set $b = \bar{y} - w\bar{x}$ (from the centroid property) and minimize over $w$. You should get the ridge formula. *(Hint: After substituting $b$, the loss becomes a quadratic in $w$. Complete the square or take the derivative and set it to zero.)*

**Instructor notes:**
- After substituting $b = \bar{y} - w\bar{x}$, the residual becomes $w(x_i - \bar{x}) - (y_i - \bar{y})$, so:
  $R(w) = \frac{1}{n}\sum_i [w\tilde{x}_i - \tilde{y}_i]^2 + \lambda w^2$
  where $\tilde{x}_i = x_i - \bar{x}$, $\tilde{y}_i = y_i - \bar{y}$.
- Expanding: $R(w) = w^2 \text{Var}(x) - 2w\text{Cov}(x,y) + \text{Var}(y) + \lambda w^2$
- This is a quadratic in $w$: $(\text{Var}(x) + \lambda)w^2 - 2\text{Cov}(x,y)w + \text{Var}(y)$.
- Minimum at $w^* = \text{Cov}(x,y) / (\text{Var}(x) + \lambda)$. ✓
- This is a great exercise for students who know derivatives. It's a simple quadratic minimization.
- **Follow-up:** "Now try to derive the lasso solution the same way. What goes wrong?" → The derivative of $|w|$ is $\pm 1$ (or undefined at 0). You can't solve $w^* = \text{Cov}(x,y) / (\text{Var}(x) + \text{something})$ because the penalty isn't quadratic. The solution is a soft-thresholding operator, but it requires case analysis (is $w > 0$, $w < 0$, or $w = 0$?). Seeds Week 6.

---

**Challenge 3-G: The Ridge–OLS Relationship**
*(Give after the bias-variance table — around minute 30)*

> The ridge slope is $w^*_{\text{ridge}} = \text{Cov}(x,y) / (\text{Var}(x) + \lambda)$ and the OLS slope is $w^*_{\text{OLS}} = \text{Cov}(x,y) / \text{Var}(x)$.
>
> **Question:** (a) Express $w^*_{\text{ridge}}$ in terms of $w^*_{\text{OLS}}$. (b) What is the "shrinkage factor"? (c) As $\lambda \to 0$, what happens? As $\lambda \to \infty$? (d) Is the shrinkage factor always between 0 and 1? Why?

**Instructor notes:**
- (a) $w^*_{\text{ridge}} = w^*_{\text{OLS}} \cdot \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$
- (b) Shrinkage factor $= \frac{\text{Var}(x)}{\text{Var}(x) + \lambda}$. It's always in $(0, 1)$ for $\lambda > 0$.
- (c) $\lambda \to 0$: shrinkage factor → 1, ridge = OLS. $\lambda \to \infty$: shrinkage factor → 0, $w \to 0$.
- (d) Yes, because $\text{Var}(x) > 0$ and $\lambda > 0$, so $\frac{\text{Var}(x)}{\text{Var}(x) + \lambda} \in (0, 1)$. Ridge always shrinks the OLS slope toward zero, never past it.
- **Follow-up:** "In the multi-feature case (Week 8), the shrinkage isn't a simple scalar — it's a matrix operation. But the principle is the same: ridge shrinks the OLS solution toward zero." Seeds Week 8.

---

**Challenge 3-H: The Elastic Net Geometry**
*(Give after the L1/L2 geometry — around minute 55)*

> We drew the L2 constraint (circle) and L1 constraint (diamond). Elastic net combines both: $\lambda_1 \sum |w_j| + \lambda_2 \sum w_j^2$.
>
> **Question:** (a) What is the constraint shape for elastic net? Sketch it in 2D. (b) Does elastic net produce sparsity? Why or why not? (c) If $\lambda_1 = 0$, what happens? If $\lambda_2 = 0$? If both are positive?

**Instructor notes:**
- (a) The constraint is a "rounded diamond" — between the L1 diamond and the L2 circle. It has corners (from L1) but they're softened (from L2).
- (b) Yes, elastic net can produce sparsity because the rounded diamond still has regions near the axes where the solution can land. But it's less aggressive than pure lasso — the corners are rounded, so the solution is less likely to be exactly on an axis.
- (c) $\lambda_1 = 0$: pure ridge (circle). $\lambda_2 = 0$: pure lasso (diamond). Both positive: rounded diamond.
- **Follow-up:** "Why use elastic net instead of lasso?" → Lasso has a problem with correlated features: it picks one and zeros the other (arbitrarily). Elastic net keeps both (small but nonzero) because the L2 part stabilizes the solution. This is why elastic net is preferred when features are correlated.

---

**Challenge 3-I: L1 Loss vs. L1 Regularization**
*(Give after the lasso discussion — around minute 60)*

> This week we discussed L1 regularization (lasso): penalizing $\sum |w_j|$. Last week, we discussed L1 loss: $|\hat{y} - y|$ (absolute error instead of squared error).
>
> **Question:** (a) Are L1 loss and L1 regularization related? They share the "L1" name — is that a coincidence? (b) The Huber loss transitions from L2 (small errors) to L1 (large errors). Why is this a good compromise for robust regression? (c) If you use L1 loss WITH L1 regularization, what kind of model do you get? What are its properties?

**Instructor notes:**
- (a) They're different concepts but share the L1 geometry. L1 loss = $|\hat{y} - y|$ (robust to outliers in the target). L1 regularization = $|w|$ (produces sparse weights). They both involve absolute values, which creates corners/nondifferentiability.
- (b) L2 loss penalizes outliers heavily (squared error amplifies large errors). L1 loss is robust but has a corner at zero (harder to optimize). Huber gets the best of both: smooth near zero (easy to optimize, like L2) and linear for large errors (robust, like L1).
- (c) L1 loss + L1 regularization = "LAD-Lasso" (Least Absolute Deviation Lasso). It's robust to outliers in BOTH the target (L1 loss) and produces sparse weights (L1 regularization). It's used in robust sparse regression. But it requires iterative optimization (no closed form for either part).
- **Follow-up:** "This shows that the choice of loss and the choice of regularization are independent. You can mix and match: L2 loss + L2 reg (ridge), L2 loss + L1 reg (lasso), L1 loss + L2 reg (robust ridge), L1 loss + L1 reg (robust lasso), etc." Seeds Weeks 5–6.

---

**Challenge 3-J: The Probabilistic Preview**
*(Give during the probabilistic perspective section — around minute 68, or at the end)*

> We said (Section 8 of the handout) that MSE corresponds to Gaussian noise, ridge corresponds to a Gaussian prior, and lasso corresponds to a Laplace prior.
>
> **Question:** (a) What does it mean for a model to have a "prior"? (b) The Laplace distribution has heavier tails than the Gaussian. What does "heavier tails" mean? (c) Why might a Laplace prior (lasso) be more appropriate than a Gaussian prior (ridge) when you believe most features are irrelevant? (d) What prior would correspond to elastic net?

**Instructor notes:**
- (a) A "prior" is a belief about the parameters before seeing data. In Bayesian ML (Week 5), the prior encodes what we think the weights should look like. A Gaussian prior says "weights should be small, centered at zero." A Laplace prior says "most weights should be exactly zero, with a few large ones."
- (b) Heavier tails = the distribution puts more probability mass on extreme values. A Laplace distribution allows larger weights with higher probability than a Gaussian. But it also concentrates more mass at zero (sharper peak).
- (c) If most features are irrelevant, you want most weights to be zero. The Laplace prior has a sharp peak at zero (encouraging sparsity) and heavy tails (allowing a few large weights for the relevant features). The Gaussian prior is smooth at zero (doesn't push weights to exactly zero).
- (d) Elastic net corresponds to a prior that is a mixture of Gaussian and Laplace — a "rounded" version of the Laplace. Formally, it's not a standard named distribution, but it combines the sparsity of Laplace with the stability of Gaussian.
- **Follow-up:** "In Week 5, we'll derive all of this formally using Maximum a Posteriori (MAP) estimation. The connection between regularization and priors is one of the most beautiful results in ML." Seeds Week 5.

---

### Ongoing Challenges (Cross-Week)

These are longer-form questions that advanced students can think about throughout the week. Mention them at the end of Session 2 and discuss during office hours or the start of Week 4.

**Ongoing 1: The "Best λ" Question**

> We said to choose λ by minimizing validation error. But the validation curve is computed on a finite validation set — it's noisy. If you re-run with different data, the optimal λ changes. How do you make a robust choice? What if the curve is flat near the minimum — does it matter which λ you pick?

**Instructor notes:** This leads directly to cross-validation (Week 4). The "one standard error rule" (pick the most regularized model within one standard error of the minimum) is a practical answer. The flat region near the minimum is actually a good sign — it means the model is insensitive to λ in that range, which is robust. Seeds Week 4.

---

**Ongoing 2: The "True Model" Question (Revisited)**

> In Week 1, we asked whether the "true model" is a meaningful concept. This week, we saw that overfitting = fitting noise. But what if what looks like noise is actually a signal from features we didn't measure? If we added those features, the "noise" would become "signal" and the overfitting would disappear. Is overfitting always a model problem, or could it be a data problem?

**Instructor notes:** This is a deep point. Overfitting can be caused by (a) too complex a model relative to data, or (b) missing features that would explain the "noise." In practice, adding relevant features is often more effective than regularization. This connects to feature engineering (Week 9) and representation learning (Week 34). The "irreducible error" is only truly irreducible if you have all possible features — which you never do.

---

**Ongoing 3: The Complexity Dial Across Algorithms**

> We showed that degree, λ, k, and depth are all "complexity dials." But they control complexity in different ways. Degree controls the hypothesis space directly (more functions). λ controls the weight magnitudes (restricting to a ball). k controls local averaging. Depth controls the partition granularity.
>
> **Question:** Are these really the "same knob"? Or are there situations where one type of complexity control works and another doesn't? Can you think of a case where increasing polynomial degree helps but increasing tree depth hurts (or vice versa)?

**Instructor notes:** The complexity dial is a unifying *principle*, but the mechanisms are different. Polynomial degree adds global flexibility (the polynomial is defined everywhere). Tree depth adds local flexibility (each region is independent). k-NN's k controls local averaging. These different mechanisms mean the U-curve can have different shapes (e.g., trees can have sharp transitions). The principle is: all complexity knobs produce the U-curve, but the location and width of the sweet spot differ. Seeds Weeks 9–10.

---

### Managing Advanced Students: Practical Tips

| Situation | Strategy |
|-----------|----------|
| Student finishes the diagnostic table early | Hand them Challenge 3-A (proving monotonicity). It's a proof they can attempt with algebra alone. |
| Student says "I already know about lasso" | Give them Challenge 3-F (deriving ridge) or 3-H (elastic net geometry). Push them to derive, not just know. |
| Student asks about Bayesian priors | Give them Challenge 3-J. This is their gateway to Week 5. |
| Student seems bored during the L1/L2 geometry | Give them Challenge 3-H (elastic net shape) or 3-I (L1 loss vs. L1 reg). These extend the geometry they already understand. |
| Student already solved double descent in Week 1 | Push deeper: "Why does the minimum-norm interpolator generalize? What if you used a different optimizer?" Seeds Week 18. |
| Multiple advanced students | Give them Challenge 3-F as a group exercise. Have them derive the ridge solution together and present it. This is a concrete, checkable result that builds confidence. |

---

## Post-Session Checklist

After each session, the instructor should:

- [ ] Review quiz results and note common mistakes
- [ ] Update the student progress tracker
- [ ] Prepare spiral-back questions for the next quiz
- [ ] Check if any student needs intervention (⚠ or ✗ on the tracker)
- [ ] Preview next session's material and adjust if needed
- [ ] Note which challenge questions were given out and to whom
- [ ] Check if any "parking lot" questions from this week need addressing in Week 4

---

## Preparation Checklist for Week 3

### Before Session 1

- [ ] Read handout Sections 1–3
- [ ] Review Week 2 quiz results — identify spiral-back topics
- [ ] Open Desmos and pre-load the polynomial regression demo (Demo 1)
- [ ] Prepare the U-shaped test error curve demo (Demo 2)
- [ ] Prepare board layout for: polynomial model, degree-vs-data table, diagnostic table, complexity curve
- [ ] Print quiz S1 (or have it ready to project)
- [ ] Have challenge questions 3-A through 3-E ready on sticky notes

### Before Session 2

- [ ] Read handout Sections 4–8
- [ ] Review Session 1 quiz results — address common mistakes at start of Session 2
- [ ] Open Desmos and pre-load the ridge shrinking demo (Demo 3) and L1/L2 geometry demo (Demo 4)
- [ ] Prepare board layout for: ridge formula, bias-variance table, L1/L2 geometry, complexity dial table
- [ ] Print quiz S2
- [ ] Have challenge questions 3-F through 3-J ready on sticky notes
- [ ] Prepare the residual analysis demo (Demo 5) if time permits
