# Week 6 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): The Gradient and Gradient Descent

### Learning Objectives

By the end of this session, students should be able to:
1. Define the gradient as the vector of partial derivatives and explain it points in the direction of steepest ascent.
2. Write the GD update rule: $\mathbf{w} \leftarrow \mathbf{w} - \eta \nabla L(\mathbf{w})$.
3. Perform GD step-by-step on a 1D quadratic ($f(w) = w^2$).
4. Explain the three learning rate regimes (too small, too large, just right).
5. State the convergence condition for quadratics and the role of convexity.

### Materials Needed

- Whiteboard / blackboard with multiple sections
- Desmos or Python notebook (for the learning rate demo — see `visual_demos.md`)
- Printed or projected handout Sections 2–3
- Quiz S1 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:08 | **Recap of Week 5 + Hook.** | See Hook section below. |
| 0:08–0:15 | **The gradient: quick recap + ML interpretation.** | Students know derivatives. Just connect to ML: gradient = uphill, $-\nabla f$ = downhill. |
| 0:15–0:32 | **GD update rule + 1D quadratic example.** | Step-by-step on the board. The core of Session 1. |
| 0:32–0:48 | **Learning rate regimes (Desmos demo).** | Three runs: too small, just right, too large. |
| 0:48–0:55 | **Convergence condition + convexity.** | Why GD works for MSE. Non-convex preview. |
| 0:55–0:62 | **Learning rate schedules.** | Brief. Preview of Week 17. |
| 0:62–0:68 | **The 2D gradient (vector field, contour plot).** | Visual: gradient points outward, GD steps inward. |
| 0:68–0:72 | **Wrap-up + preview of Session 2.** | "Next: GD on MSE + SGD." |
| 0:72–0:80 | **Quiz (end-of-session).** 8 min. See `quiz_S1.md`. |

> **Note:** We do NOT review derivative rules (power, product, chain rule). Students have had 5 weeks of calculus. If any student is struggling, refer them to their calculus course. We start directly with the gradient as a concept and immediately apply it to ML.

### Hook: "Why Not Just Use the Formula?" (8 min)

1. "In Week 2, we derived the OLS solution: $w^* = \text{Cov}(x,y)/\text{Var}(x)$. In Week 3, we noted that lasso has no closed-form solution. In Week 5, we showed MLE = MSE — but what if the model is too complex for a closed form?"

2. Write on the board: "Closed-form exists for: OLS, ridge. Does NOT exist for: lasso, logistic regression, neural networks, most models."

3. "When there's no formula, how do we find the minimum? We use an **iterative method**: start somewhere, take a step downhill, repeat. This is gradient descent."

4. **The punchline:** "Gradient descent is the engine that powers almost all modern ML. Your calculus course has given you the tools. This week, we put them to work."

### Board Work: The Gradient (7 min)

**Fast.** Students know derivatives.

1. "The gradient $\nabla f$ is the vector of partial derivatives. It points UPHILL. To go DOWNHILL, use $-\nabla f$."

2. Draw a hill. $\nabla f$ points to the peak. $-\nabla f$ points to the valley.

3. "For a 1D function, the gradient is just the derivative $f'(w)$. For multivariable, it's a vector of partial derivatives."

4. Mention the chain rule: "The chain rule is the most important calculus tool for ML. Backpropagation = repeated chain rule. We'll see this in Week 16."

### Board Work: GD on 1D Quadratic (17 min)

**This is the most important part of Session 1.**

Minimize $f(w) = w^2$. $f'(w) = 2w$. Update: $w \leftarrow w - \eta \cdot 2w$.

Start: $w_0 = 3$, $\eta = 0.1$.

| Step | $w$ | $f(w)$ | $f'(w)$ | Step size |
|------|-----|--------|---------|-----------|
| 0 | 3.000 | 9.000 | 6.000 | 0.6 |
| 1 | 2.400 | 5.760 | 4.800 | 0.48 |
| 2 | 1.920 | 3.686 | 3.840 | 0.384 |
| 3 | 1.536 | 2.359 | 3.072 | 0.307 |

**Key teaching moves:**
1. Compute each step with students. "What's $f'(3)$?" → "6." "What's the update?" → "$w = 3 - 0.1 \times 6 = 2.4$."
2. "The weight is decreasing toward 0. The loss is decreasing. Good."
3. "Notice: $w_{t+1} = w_t(1 - 2\eta) = w_t \times 0.8$. Each step multiplies by 0.8. After 20 steps: $3 \times 0.8^{20} \approx 0.036$."
4. "For convergence: $|1 - 2\eta| < 1$, so $0 < \eta < 1$."

### Board Work: Learning Rate Regimes (16 min)

**Use Desmos** (see `visual_demos.md`). Show three runs:

1. **$\eta = 0.01$ (too small):** After 50 steps, $w \approx 1.1$. Very slow.
2. **$\eta = 0.1$ (just right):** After 20 steps, $w \approx 0.04$. Smooth.
3. **$\eta = 1.1$ (too large):** $w$ bounces: $3 \to -3.6 \to 4.32 \to \ldots$ Diverging!

**Key teaching moves:**
1. "The learning rate is the MOST IMPORTANT hyperparameter."
2. "Too small: safe but slow. Too large: divergent. Just right: fast and stable."
3. "How to choose? Try values (0.001, 0.01, 0.1, 1.0) and monitor the loss."

### Convergence and Convexity (7 min)

1. **Convergence condition:** For $f(w) = aw^2$, GD converges iff $0 < \eta < 1/a$.
2. **Convexity:** "MSE is convex — bowl-shaped. One global minimum. GD is GUARANTEED to find it."
3. Draw convex (bowl) vs. non-convex (bumpy). "Neural networks are non-convex. GD might get stuck. We'll discuss why it still works in Week 17."

### Discussion Prompts

1. **(After 1D example):** "If $\eta = 0.5$, what happens?" → $w_1 = 3(1-1) = 0$. One step! Optimal learning rate.

2. **(After learning rates):** "In practice, you don't know the curvature $a$. How do you choose $\eta$?" → Try values. Monitor loss. Use schedules.

3. **(After convexity):** "Why doesn't GD always reach the exact minimum?" → Numerical precision, learning rate decay, convergence threshold. We get "close enough."

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "Is GD the only optimization method?" | No (Newton, BFGS, etc.), but GD scales to millions of parameters. Standard for ML. (1 min.) |
| "How many steps?" | Depends. Linear regression: hundreds-thousands. Neural networks: millions. Measured in epochs. (30 sec.) |
| "What if I don't know the derivative?" | In ML, we always know the loss (we chose it!). For complex models, autograd computes derivatives. (1 min.) |
| "Does the starting point matter?" | Convex: no. Non-convex: yes. This is why initialization matters for neural networks. (30 sec.) |
| "Difference between GD and backprop?" | Backprop computes gradients (chain rule). GD uses them. Backprop = how to compute; GD = how to update. (30 sec.) |

---

## Session 2 (80 min): GD on Linear Regression, SGD, Feature Scaling

### Learning Objectives

By the end of this session, students should be able to:
1. Derive the gradient of MSE w.r.t. $w$ and $b$ using the chain rule.
2. Explain the residual and its role in the gradient (optimality condition).
3. Apply GD to ridge (shrinkage term) and lasso (subgradient).
4. Compare batch GD, SGD, and mini-batch GD.
5. Explain why feature scaling helps and how to avoid data leakage.

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** "Write the GD update rule." |
| 0:05–0:10 | **Paper discussion (5 min).** Ruder (2016). See `suggested_paper.md`. |
| 0:10–0:28 | **GD on MSE: derive the gradient (chain rule).** | Key derivation. |
| 0:28–0:35 | **The residual + optimality condition.** | $\sum x_i r_i = 0$ = OLS. |
| 0:35–0:45 | **Ridge GD + lasso subgradient.** | Connect to Week 3. |
| 0:45–0:57 | **SGD and mini-batch GD.** | Comparison table. Noisy trajectory. |
| 0:57–0:65 | **Feature scaling.** | Week 4 connection (data leakage). |
| 0:65–0:70 | **Monitoring training: loss curves.** | Week 4 connection (learning curves). |
| 0:70–0:80 | **Quiz (end-of-session).** 10 min. See `quiz_S2.md`. |

### Board Work: Deriving the MSE Gradient (18 min)

**The key derivation of Session 2.**

**Step 1:** $\text{MSE} = \frac{1}{n}\sum_i (y_i - wx_i - b)^2$. Let $r_i = y_i - wx_i - b$.

**Step 2:** $\frac{\partial}{\partial w}(r_i^2) = 2r_i \cdot \frac{\partial r_i}{\partial w} = 2r_i \cdot (-x_i) = -2x_i r_i$ (chain rule).

$$\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i$$

**Step 3:** $\frac{\partial r_i}{\partial b} = -1$.

$$\frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$$

**Step 4:** Update rules: $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i$, $b \leftarrow b + \frac{2\eta}{n}\sum r_i$.

**Key teaching moves:**
1. At each step: "What rule do we use?" → "Chain rule!"
2. Define the residual. "The gradient is the (negative) correlation between inputs and residuals."
3. **Optimality condition:** "At the minimum, $\sum x_i r_i = 0$. Residuals uncorrelated with inputs. Same as OLS from Week 2!"

### Board Work: Ridge and Lasso GD (10 min)

**Ridge:** $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - 2\eta\lambda w$.

"The $-2\eta\lambda w$ term is shrinkage. Same as Week 2's closed form, but step by step."

**Lasso:** $w \leftarrow w + \frac{2\eta}{n}\sum x_i r_i - \eta\lambda \, \text{sgn}(w)$.

"The $-\eta\lambda \, \text{sgn}(w)$ drives $w$ to exactly 0. At $w = 0$, subgradient is 0, stays there. This is why lasso produces exact zeros."

**Connect to Week 3:** "L1 diamond's corners are on the axes — that's why the solution lands on an axis ($w_j = 0$)."

### Board Work: SGD vs Batch GD (12 min)

**Comparison table** (handout Section 5.4).

**Key teaching moves:**
1. "Batch GD: all $n$ examples per step. Expensive for large $n$."
2. "SGD: one random example. Super fast, noisy."
3. "Mini-batch: $B = 32$–$128$. Standard for ML/DL."
4. **Noisy trajectory:** Draw smooth (batch) vs. bouncy (SGD) loss curves.
5. "The noise is GOOD for non-convex problems — helps escape local minima."
6. **Epochs:** "1 epoch = 1 pass through data. Batch: 1 step. SGD: $n$ steps. Mini-batch: $n/B$ steps."

### Board Work: Feature Scaling (8 min)

1. "Different scales → elongated loss surface → GD zigzags."
2. Draw elongated vs. spherical contours.
3. "Standardize: $x \to (x - \bar{x})/\sigma_x$. Spherical surface. Smooth convergence."
4. **CRITICAL:** "Compute $\bar{x}$, $\sigma_x$ on training data ONLY. Statistics from all data = data leakage (Week 4). Split FIRST."

### Discussion Prompts

1. **(After MSE gradient):** "At the minimum, $\sum x_i r_i = 0$. What does this mean?" → Residuals uncorrelated with inputs. Model has extracted all linear information.

2. **(After SGD):** "If SGD is noisy, why does it work?" → Expected value equals batch gradient (unbiased). Noise averages out. And helps escape local minima.

3. **(After feature scaling):** "How does scaling connect to Week 4's data leakage?" → Compute stats on training only. Apply to all sets. Split first.

### Things NOT to Cover

| Topic | When |
|-------|------|
| Adam optimizer | Week 17 |
| Backpropagation | Week 16 |
| Newton's method | Beyond scope |
| Autograd | Week 16 |

---

## Challenge Questions for Advanced Students

### Session 1

**Challenge 6-1A: Optimal Learning Rate for Quadratics**
*(Give after the 1D example — around minute 30)*

> For $f(w) = \frac{1}{2}aw^2$, the update is $w \leftarrow w(1 - \eta a)$. (a) What $\eta$ reaches the minimum in one step? (b) What happens at $\eta = 2/a$? (c) Derive $0 < \eta < 2/a$ for convergence.

**Instructor notes:**
- (a) $\eta = 1/a$: $w_1 = 0$. One step.
- (b) $\eta = 2/a$: $w_1 = -w_0$. Oscillates forever.
- (c) $|1 - \eta a| < 1 \Rightarrow 0 < \eta < 2/a$.
- **Follow-up:** "This is why we standardize features. Large scale → large $a$ → small max $\eta$."

---

**Challenge 6-1B: GD on a Non-Convex Function**
*(Give after convexity — around minute 52)*

> $f(w) = w^4 - 3w^2 + 2$. (a) Find critical points. (b) Which are minima? (c) GD from $w_0 = 0$: where does it converge? (d) GD from $w_0 = 2$: where? (e) What does this tell you about initialization?

**Instructor notes:**
- $f'(w) = 4w^3 - 6w = 0 \Rightarrow w = 0, \pm\sqrt{3/2}$.
- $w = 0$ is a maximum (stuck!). $w = \pm\sqrt{3/2}$ are minima.
- Starting at 0: doesn't move (gradient = 0 at saddle/maximum).
- Starting at 2: converges to $\sqrt{3/2}$.
- "Initialization matters for non-convex problems."

---

### Session 2

**Challenge 6-2A: The SGD Variance**
*(Give after SGD — around minute 52)*

> Batch gradient: $g_{\text{batch}} = -\frac{2}{n}\sum x_i r_i$. SGD gradient: $g_i = -2x_i r_i$. (a) Show $\mathbb{E}[g_i] = g_{\text{batch}}$. (b) How does variance change with batch size $B$?

**Instructor notes:**
- (a) $\mathbb{E}_i[g_i] = \frac{1}{n}\sum(-2x_i r_i) = g_{\text{batch}}$. Unbiased.
- (b) $\text{Var}(g_{\text{batch}}) = \text{Var}(g_i)/B$. Larger $B$ → lower variance.

---

**Challenge 6-2B: The Soft-Thresholding Operator**
*(Give after lasso subgradient — around minute 42)*

> For $L(w) = \frac{1}{2}(w - c)^2 + \lambda|w|$ with $c > 0$: (a) Find the minimizer. (b) For what $\lambda$ is $w^* = 0$? (c) Write the solution as a single formula.

**Instructor notes:**
- (a) For $w > 0$: $w = c - \lambda$ (valid if $c > \lambda$).
- (b) $w^* = 0$ when $\lambda \geq c$.
- (c) $w^* = \text{sign}(c)(|c| - \lambda)_+$ (soft-thresholding).
- "Weights for irrelevant features (small $|c|$) are zeroed. This is lasso's feature selection."

---

**Challenge 6-2C: Momentum and the Zigzag Problem**
*(Give after feature scaling — around minute 62)*

> (a) Draw the zigzag trajectory on an elongated surface. (b) Why does momentum reduce zigzagging? (c) How does this differ from feature scaling?

**Instructor notes:**
- (a) Bounces in steep direction, crawls in shallow.
- (b) Momentum accumulates: consistent directions build up, oscillating directions cancel.
- (c) Scaling changes the surface. Momentum changes the optimizer. Both help; can use together.

---

## Post-Session Checklist

- [ ] Review quiz results
- [ ] Update student progress tracker
- [ ] Prepare spiral-back questions
- [ ] Preview next session

---

## Preparation Checklist

### Before Session 1

- [ ] Read handout Sections 1–3
- [ ] Prepare the 1D quadratic GD example (step-by-step table)
- [ ] Prepare the Desmos demo with three learning rates
- [ ] Prepare convex vs. non-convex diagram
- [ ] Print quiz S1

### Before Session 2

- [ ] Read handout Sections 4–7
- [ ] Prepare the MSE gradient derivation (chain rule steps)
- [ ] Prepare ridge/lasso GD derivation
- [ ] Prepare SGD vs batch GD comparison table
- [ ] Prepare feature scaling demo
- [ ] Print quiz S2
- [ ] Read the suggested paper (Ruder, 2016)
