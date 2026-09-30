# Week 7 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

> **Context:** Two-week break since Week 6. Week 6 (corrected) covered: Bayes for ML, MLE (Bernoulli + Gaussian), MLE = MSE, bias-variance *formulation* (not full derivation), and gradient descent *conceptually* (update rule only — no worked example, no learning-rate regimes, no MSE gradient derivation, no SGD comparison, no feature scaling, no loss curves). MAP = Ridge and Laplacian → Lasso were NOT covered. There is also a Weeks 1–6 exam that was taken; the review sessions should leverage it.

> **New format:** Starting this week, the course runs **4 sessions of 70 minutes** per week (previously 2 × 80 min). Quizzes stay 8 minutes. Total weekly contact time is slightly up (280 vs. 160 min), which is why this week can both review *and* complete pending material *and* start logistic regression.

---

## Session 1 (70 min): Review I — The Regression Story (Weeks 1–4)

### Learning Objectives

By the end of this session, students should be able to:
1. State the four components of the ML problem setup and give an example of each.
2. Re-derive OLS ($w^* = \text{Cov}/\text{Var}$) and the ridge solution on the board.
3. Explain the overfitting/underfitting tradeoff and the role of every complexity dial (degree, $\lambda$, k).
4. Reconstruct the train/validation/test pipeline, k-fold CV, and the golden rule.
5. Compute precision/recall/F1 from a confusion matrix and explain when accuracy misleads.

### Materials Needed

- Whiteboard (multiple sections)
- Copies of the exam review sheet (`exam_review_weeks_1-6.md`) or the handout formula sheet (Section 2)
- Quiz S1 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Welcome back. New format. The week's roadmap.** | Show the 4-session plan. Energize — this is a consolidation week. |
| 0:05–0:15 | **Retrieval warm-up (individual, written).** | 6 questions from Section 3 of the handout, 90 sec each. No notes. This is a diagnostic. |
| 0:15–0:20 | **Discuss warm-up answers (peer + whole class).** | Swap papers, discuss in pairs, then whole class. Collect common errors on the board. |
| 0:20–0:35 | **Board re-derivation: OLS and ridge (students drive).** | Ask students to dictate each step. You write. Deliberately make one error for them to catch. |
| 0:35–0:45 | **The complexity dial: overfitting, L1 vs L2, bias-variance language.** | Draw the U-shaped test-error curve. Label regions with Week 3 vocabulary. |
| 0:45–0:58 | **Evaluation rapid-fire: pipeline, metrics, a full worked confusion-matrix problem.** | New numbers than the exam (fresh practice). Include an imbalanced-data twist. |
| 0:58–1:02 | **Exam debrief (topline).** | Only 2–3 most frequent exam errors. Individual issues → office hours. |
| 1:02–1:10 | **Quiz S1** (8 min). | Mostly spiral-back questions (Weeks 1–4). |

### Hook: "The Map" (5 min)

1. Draw a single large diagram on the board — the whole course so far as a pipeline:

```
   data → [model: y = wx+b] → [loss: MSE] → [solve: closed form / GD] → [evaluate: val/test]
                ↑                      ↑                                      ↓
   Week 1    Week 2          Week 2/5 (MLE)                        Week 4
                                                overfitting? → Week 3 (regularize)
```

2. "Everything we do for the rest of this course — neural networks included — is a variation on this pipeline. Change the model, change the loss, change the solver. The skeleton never changes."

3. "After two weeks off, today we re-own Weeks 1–4. Next session: the probability lens. Session 3: gradient descent for real. Session 4: our first classifier."

### Retrieval Warm-Up (write on board or project; students answer individually)

1. Write the four components of the ML problem setup. (W1)
2. Write the closed-form OLS solution for $w^*$. (W2)
3. Sketch (or describe) training error and test error vs. model complexity. (W3)
4. State the golden rule of the test set. (W4)
5. When does accuracy fail as a metric? (W4)
6. Write the ridge solution and say what $\lambda$ controls. (W2/W3)

> **Do not grade this.** Its purpose: (a) wake up retrieval after the break, (b) give YOU a diagnostic of what has decayed, (c) show students what has decayed — motivating the review.

### Board Work: OLS Re-derivation, Students Drive (15 min)

1. **Setup:** $\text{MSE}(w,b) = \frac{1}{n}\sum (y_i - wx_i - b)^2$.
2. Ask: "What do we do first?" → Set partial derivatives to zero.
3. From $\partial/\partial b = 0$: $b^* = \bar{y} - w\bar{x}$. "Everyone substituting this back into $\partial/\partial w = 0$ gets the same simplification — mean-centered data."
4. Result: $w^* = \text{Cov}(x,y)/\text{Var}(x)$.
5. **Ridge:** replace $\text{Var}(x) \to \text{Var}(x) + \lambda$ in the denominator. "The shrinkage is literally one extra term in the denominator."
6. **Deliberate error:** write $b^* = \bar{y} + w^*\bar{x}$ (wrong sign). See who catches it. If nobody does after 30 seconds, circle it and ask them to check dimensions/units.

**Common misconceptions to hunt:**
- "$\lambda$ is learned from the data" → No: it's a *hyperparameter*, chosen on validation data (W4 connection).
- "Ridge improves training error" → It usually *worsens* training error to improve *test* error.
- Confusing validation set (used for model selection) with test set (used once, at the end).

### Board Work: The Complexity Dial (10 min)

1. Draw axes: complexity (degree, $1/\lambda$, ...) vs. error. Two curves: training (monotone ↓), test (U-shape).
2. Label left region: **underfitting / high bias**. Right region: **overfitting / high variance**. "You now have the *words* for these; next session we make them a *theorem*."
3. L1 diamond vs. L2 ball sketch — corners on the axes → sparsity.
4. Ask: "Name every complexity dial we've met." → polynomial degree, $\lambda$ (ridge/lasso), (later: k in k-NN, tree depth, network size).

### Board Work: Full Metrics Problem (13 min)

New problem, exam-style but fresh numbers:

> A model screens 1000 patients for a disease with 5% prevalence. It predicts "positive" 120 times. It correctly identifies 42 of the 50 true cases. Build the confusion matrix. Compute accuracy, precision, recall, F1. Would you deploy this model? What should we ask before deciding?

- $TP = 42$, $FN = 8$, $FP = 78$, $TN = 872$.
- Accuracy $= 914/1000 = 91.4\%$ ("impressive" — but useless alone).
- Precision $= 42/120 = 35\%$; Recall $= 42/50 = 84\%$; F1 $= 2 \cdot \frac{0.35 \times 0.84}{0.35 + 0.84} \approx 49.6\%$.
- Discussion: for screening (missing a case is catastrophic) recall matters most; for confirmation, precision. Connect to threshold choice — "next session we'll see the model that outputs probabilities, and in Session 4 the dial that sets the threshold."

### Discussion Prompts

1. "Why can't we just use the training error to choose the degree?" → Training error always decreases with complexity (W3).
2. "Why does the test set lose its 'purity' if we use it twice?" → Model selection adapts to test data — overfitting to the evaluator (W4).
3. "Your model has 99% accuracy and the exam problem says 'should you trust it?' — what's the first thing you check?" → Class balance / prevalence.

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "Did everyone forget everything?" | Normalize: decay after a break is expected and exactly why we spiral. Today's quiz will look better than the warm-up. |
| "Will the exam be curved / re-administered?" | Defer to your exam policy; keep the focus on learning, not the score. |
| "Why review instead of new material?" | All of Phase 2 (Weeks 9–20) stands on Weeks 1–6. A crack here becomes a hole there. |

### Quiz S1 Design Notes

Spiral-back heavy: OLS closed form, complexity-dial sketch, confusion matrix computation, golden rule. One calculation (confusion matrix) to keep them honest. See `quiz_S1.md`.

---

## Session 2 (70 min): Review II — The Probability Lens + Completing It (Weeks 5–6)

### Learning Objectives

By the end of this session, students should be able to:
1. Interpret Bayes' theorem for ML (prior/likelihood/evidence/posterior) and re-run the medical testing example.
2. Reproduce MLE for Bernoulli and the MLE = MSE correspondence.
3. **Prove MAP with a Gaussian prior = ridge regression (full derivation).**
4. **Show Laplacian prior → lasso and explain sparsity via the corner.**
5. **Complete the bias-variance derivation (cross terms vanishing).**
6. State the three deep connections (geometry / probability / optimization).

### Materials Needed

- Whiteboard, colored markers (for $A$, $B$, $C$ terms in the decomposition)
- Colored sticky notes or cards for the "standing vote" activity
- Quiz S2 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:03 | **Recap of Session 1 + today's goal.** | "Yesterday: the map. Today: the probability lens — including the two derivations we owed since Week 5." |
| 0:03–0:13 | **Bayes for ML + medical testing (rapid re-run).** | Tree diagram. Students compute the answer before you reveal. |
| 0:13–0:22 | **MLE Bernoulli + MLE = MSE (students re-derive in pairs).** | One pair presents at the board. You timebox: 6 min re-derive, 3 min present. |
| 0:22–0:37 | **MAP = Ridge — the full derivation (NEW).** | Core new content of the session. Step by step; do not rush the $\lambda = \sigma^2/\tau^2$ interpretation. |
| 0:37–0:42 | **Laplacian prior → Lasso (NEW, quick).** | Mirror image of the previous proof. Students predict each step. |
| 0:42–0:58 | **Bias-variance: the full derivation (NEW).** | $A + B + C$, expand, cross terms vanish, name the terms, draw the tradeoff. |
| 0:58–1:04 | **The three deep connections + traffic-light self-assessment.** | Each student holds up green/yellow/red per derivation. |
| 1:04–1:10 | **Quiz S2** (6 min, short — derivation-heavy day). | One derivation (MAP=Ridge sketch) + one conceptual. |

### Hook: "The Debt List" (3 min)

Write on the board:

> **OWED SINCE WEEK 5:**
> 1. MAP = Ridge — proof
> 2. Laplacian → Lasso — proof
> 3. Bias-variance — the cross terms
> **TODAY WE PAY ALL THREE.**

"Every one of these three is a 10-point exam question in national qualifiers. They look like three separate facts; they are actually one idea: *regularization is a prior in disguise.*"

### Board Work: MAP = Ridge (15 min) — THE key derivation

**Do not lecture through it. Build it with questions.**

1. "MAP maximizes what?" → the posterior $p(w \mid \mathcal{D}) \propto p(\mathcal{D}\mid w)p(w)$.
2. "We have the first factor already — what is it?" → Gaussian likelihood from MLE = MSE (Session 1 warm-back: $\text{const} - \frac{1}{2\sigma^2}\sum r_i^2$).
3. "What does a Gaussian prior on $w$ look like?" → $w \sim \mathcal{N}(0, \tau^2)$. Log: $-w^2/(2\tau^2)$.
4. "Add them. Minimize the negative. What do you get?" → $\frac{1}{2\sigma^2}\sum r_i^2 + \frac{1}{2\tau^2}w^2$.
5. "Multiply by $2\sigma^2$. What do you see?" → $\sum r_i^2 + \frac{\sigma^2}{\tau^2}w^2$. Circle the last term: "What is this called?" → **Ridge.**

$$\boxed{\text{Ridge} = \text{MAP}(\text{Gaussian noise}, \text{Gaussian prior}), \qquad \lambda = \frac{\sigma^2}{\tau^2}}$$

6. **Interpretation table** (handout Section 4): noisy data or tight prior → big $\lambda$ → strong shrinkage. Clean data or loose prior → small $\lambda$.
7. **Punchline:** "Week 2 introduced ridge as a trick. Week 3 gave it geometry. Week 5 said it's MAP. Now it's proved: **regularization is Bayesian honesty about uncertainty.**"

**Common misconceptions:**
- $\lambda = \sigma^2/\tau^2$ — students swap numerator/denominator. Fix: "noise on top, belief below" (σ² over τ²) — or: noisy data (big σ²) should mean MORE regularization, so λ must grow with σ².
- "The prior is on the data" → No: on the *parameter* $w$.
- "MAP needs the evidence" → It doesn't (θ-independent constant).

### Board Work: Laplacian → Lasso (5 min)

Same skeleton, one change: $-\log p(w) = |w|/\tau$.

1. Students predict every step before you write it (it's the same algebra).
2. Result: $\lambda = \sigma^2/\tau$ (note: *not* $\tau^2$).
3. "Why zeros?" → corner at 0 (non-differentiable). Sketch Gaussian (smooth) vs. Laplacian (spike) side by side; overlay the L2 ball / L1 diamond from yesterday.

### Board Work: Bias-Variance, the Full Derivation (16 min)

**Setup (2 min):** $y = f(x) + \epsilon$, $\epsilon \sim \mathcal{N}(0,\sigma^2)$, independent of training data $\mathcal{D}$. Model $\hat{f}$ trained on $\mathcal{D}$. Target: $\mathbb{E}[(y - \hat{f}(x))^2]$ over *both* randomness of $\mathcal{D}$ and noise $\epsilon$.

**The A+B+C trick (3 min):** define $\bar{f} = \mathbb{E}_\mathcal{D}[\hat{f}]$ and insert $\bar{f}$ twice:

$$y - \hat{f} = \underbrace{(f - \bar{f})}_{A} + \underbrace{(\bar{f} - \hat{f})}_{B} + \underbrace{\epsilon}_{C}$$

"Three sources of error: the model class is systematically off ($A$), the model wobbles with the training set ($B$), the world is noisy ($C$)."

**Expansion (3 min):** $\mathbb{E}[(A+B+C)^2] = \mathbb{E}[A^2] + \mathbb{E}[B^2] + \mathbb{E}[C^2] + 2\mathbb{E}[AB] + 2\mathbb{E}[AC] + 2\mathbb{E}[BC]$.

**Cross terms vanish (5 min) — the step we owed:**
- $\mathbb{E}[AB] = 0$: $A$ is a constant; $\mathbb{E}[B] = 0$ *by definition of $\bar f$*.
- $\mathbb{E}[AC] = 0$: $A$ constant; $\mathbb{E}[\epsilon] = 0$.
- $\mathbb{E}[BC] = 0$: $\epsilon \perp \mathcal{D}$ and $\mathbb{E}[\epsilon] = 0$.

**Result + naming (3 min):**

$$\mathbb{E}[(y-\hat{f})^2] = \text{Bias}^2 + \text{Variance} + \sigma^2$$

Draw the classic two-curve diagram (bias ↓, variance ↑ with complexity; total is U-shaped). Connect: Week 3's U-curve is now a theorem. Week 4's learning-curve diagnosis maps onto the terms (gap = variance; both-high = bias).

### Discussion Prompts

1. **(After MAP=Ridge):** "If I *know* my weights should be small, what does that mean for $\tau^2$ and $\lambda$?" → Small $\tau^2$, large $\lambda$, stronger shrinkage.
2. **(After lasso):** "Feature selection = choosing which priors?" → Spiky (sparse) beliefs about which features matter.
3. **(After bias-variance):** "Can more data reduce bias?" → No — variance only. "What reduces irreducible noise?" → Nothing. It's in the world, not the model.
4. **(Connections):** "We've seen regularization algebraically (W2), geometrically (W3), probabilistically (today). Which is true?" → All. The probabilistic view is the deepest — it *explains* the other two.

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "Why can we drop the evidence?" | It doesn't depend on $w$ — a constant can't change the argmax. (30 sec.) |
| "Where does $\tau$ come from in practice?" | It's a hyperparameter (like $\lambda$) — chosen by validation. The math tells us the *form*, validation picks the *value*. (1 min.) |
| "Is $\hat{f}$ random?" | Yes — it depends on the random training set. That randomness IS the variance term. (1 min.) |
| "Does this hold for classification?" | The squared-loss version is regression; classification has analogues. We'll state the qualitative version for classifiers in Week 8+. (30 sec.) |

### Quiz S2 Design Notes

Short (6 min): (1) reconstruct the MAP = Ridge chain (prompted, 3 blanks), (2) which-term-of-bias-variance multiple choice. Full derivations assessed again in the Week 8 mini-exam. See `quiz_S2.md`.

---

## Session 3 (70 min): Completing Gradient Descent (Week 6, Part 2)

### Learning Objectives

By the end of this session, students should be able to:
1. Run GD by hand on $f(w) = w^2$ and on $f(w) = \frac{1}{2}aw^2$, and explain geometric decay.
2. Identify the three learning-rate regimes; state and use the convergence condition $0 < \eta < 2/a$.
3. Explain why convexity guarantees convergence to the global minimum for MSE.
4. **Derive the MSE gradient with the chain rule and write the residual form of the updates.**
5. Adapt GD to ridge (shrinkage term) and lasso (subgradient, constant-speed push).
6. Compare batch GD / SGD / mini-batch; explain epochs and why SGD noise can help.
7. Explain feature scaling and its data-leakage trap.

### Materials Needed

- Whiteboard
- Desmos (or equivalent) prepared with the three learning-rate runs (see `visual_demos.md`)
- Calculator-free iteration table pre-drawn on the board
- Quiz S3 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:03 | **Recap + the engine metaphor.** | "Session 2 gave us the losses to minimize. Today: the engine that minimizes them." |
| 0:03–0:16 | **GD by hand on $f(w)=w^2$ (iteration table) + geometric decay.** | Full table, students compute each row aloud. |
| 0:16–0:24 | **Learning-rate regimes (Desmos) + convergence condition $0 < \eta < 2/a$.** | Three runs; students predict before each reveal. |
| 0:24–0:28 | **Convexity in 3 minutes.** | One-bowl picture. Why we trust GD for MSE. |
| 0:28–0:45 | **The MSE gradient derivation (chain rule) + residual form + optimality condition.** | THE core derivation. Students dictate chain-rule steps. |
| 0:45–0:52 | **Ridge GD and lasso subgradient.** | Shrinkage term; constant-speed push to zero. |
| 0:52–1:00 | **SGD / mini-batch / epochs (+ why noise helps).** | Comparison table; bouncy vs. smooth trajectory sketch. |
| 1:00–1:04 | **Feature scaling + leakage trap (2-sentence version).** | Elongated vs. spherical contour sketch. |
| 1:04–1:10 | **Quiz S3** (6 min). | One GD iteration by hand + regimes MC. |

### Hook: "From Formula to Algorithm" (3 min)

1. "Week 2: OLS has a formula. Week 6: we said most models — logistic regression (tomorrow!), neural networks — have **no formula**. What do we do then?"
2. "Hiking in fog: feel the slope under your feet, step downhill, repeat. That's the whole algorithm. Today we make it precise — and then we *run* it, by hand, on real losses."

### Board Work: GD by Hand (13 min)

1. $f(w) = w^2$, $f'(w) = 2w$, update $w \leftarrow w - 2\eta w$. Start $w_0 = 3$, $\eta = 0.1$.
2. **Students compute every row aloud:** "What's $f'(3)$?" → 6. "The step?" → $3 - 0.6 = 2.4$. Fill the table to step 4, then jump to step 20.
3. **The pattern:** $w_{t} = 3(0.8)^t$. "Geometric decay — the ratio is constant."
4. Generalize immediately: $f(w) = \frac{1}{2}aw^2 \Rightarrow w_{t+1} = w_t(1 - \eta a)$. "One formula governs every quadratic."

**Watch for:** arithmetic slips (they'll be common after the break — that's fine, it's the point of doing it by hand), and students computing $f(w)$ but forgetting to use $f'(w)$ in the step.

### Board Work: Learning-Rate Regimes (8 min, Desmos)

Before each run, students *predict* the trajectory:

1. $\eta = 0.01$: crawl. "After 50 steps: $w \approx 1.1$. Pathetically slow."
2. $\eta = 0.1$: smooth geometric convergence.
3. $\eta = 1.1$: $3 \to -3.6 \to 4.32 \to \ldots$ **Divergence.**

Then derive: convergence $\iff |1 - \eta a| < 1 \iff 0 < \eta < 2/a$. Note $\eta = 1/a$ reaches the minimum in ONE step — "the optimal rate exists when you know the curvature; in real problems you don't, which is why we tune $\eta$ on validation data (W4 connection)."

**Diagnostic poster** (write once, refer to forever):

| Loss curve | Diagnosis | Fix |
|---|---|---|
| slow decrease | η too small | raise η |
| oscillation / explosion | η too large | lower η |
| steady decrease | healthy | done |

### Board Work: The MSE Gradient — Chain Rule (17 min) — THE core derivation

**Step 1:** $\text{MSE}(w,b) = \frac{1}{n}\sum_i r_i^2$ with $r_i = y_i - wx_i - b$. "One new symbol — the residual — and the whole derivation collapses."

**Step 2 (students dictate):**
- Outer: $\frac{d}{dr} r^2 = 2r$.
- Inner: $\frac{\partial r_i}{\partial w} = -x_i$, $\frac{\partial r_i}{\partial b} = -1$.
- Chain: $2r_i \cdot (-x_i) = -2x_i r_i$.

$$\frac{\partial \text{MSE}}{\partial w} = -\frac{2}{n}\sum_i x_i r_i, \qquad \frac{\partial \text{MSE}}{\partial b} = -\frac{2}{n}\sum_i r_i$$

**Step 3 — the updates in residual form:**

$$w \leftarrow w + \frac{2\eta}{n}\sum_i x_i r_i, \qquad b \leftarrow b + \frac{2\eta}{n}\sum_i r_i$$

**Read it aloud, in words:** "Every point pulls the line toward itself, with force proportional to how wrong we are on it ($r_i$) and how big its input is ($x_i$). Points we already get right pull with zero force."

**Step 4 — optimality condition:** set the gradient to zero: $\sum x_i r_i = 0$, $\sum r_i = 0$. "Residuals uncorrelated with inputs, zero mean. THIS IS OLS. The iterative route and the Week-2 formula route land on the same summit."

> **Plant the flag:** "Memorize the *structure*: gradient = (prediction − truth) × input. Tomorrow the same structure appears for logistic regression — with one breathtaking cancellation."

### Board Work: Ridge & Lasso GD (7 min)

1. Ridge: gradient gains $+2\lambda w$ → update gains $-2\eta\lambda w$. "Every step also multiplies $w$ by $(1-2\eta\lambda)$. Shrinkage, step by step — the closed-form denominator $\text{Var}+\lambda$ was the same idea in one shot."
2. Lasso: subgradient of $|w|$ is $\text{sgn}(w)$ (at 0: the whole interval $[-1,1]$ — take 0 there). Update gains $-\eta\lambda\,\text{sgn}(w)$.
3. "Ridge's pull is *proportional* to $w$ — it slows near zero and never quite arrives. Lasso's push is *constant* — near zero it does NOT slow down and slams to exactly zero. **That is the mechanism of sparsity.**"

### Board Work: SGD / Mini-batch (8 min)

1. Batch: all $n$ per step — exact gradient, expensive.
2. SGD: 1 random example — gradient $-2x_i r_i$ for one $i$. "Unbiased: its expectation is the batch gradient." Bouncy trajectory.
3. Mini-batch: $B = 32$–$128$ — the industry standard. Variance $\propto 1/B$.
4. **Epoch:** one pass over the data. $n = 1000, B = 100 \Rightarrow 10$ updates per epoch.
5. "The noise is not a bug: for non-convex problems (neural networks, Week 15+) it kicks us out of bad valleys. For convex problems it just makes the path bumpy."
6. Sketch smooth vs. bouncy loss curves side by side.

### Feature Scaling (4 min, the 2-sentence version)

1. Sketch elongated contours vs. circles. "Wrong scales ⇒ valley ⇒ zigzag. Standardize ⇒ bowl ⇒ straight descent."
2. **The trap:** compute $\bar{x}, \sigma$ on training only, after the split — otherwise it's Week-4 data leakage. "Split first, scale second."

### Discussion Prompts

1. **(After regimes):** "If $\eta = 1/a$ solves a quadratic in one step, why isn't GD one step in practice?" → We don't know $a$ (curvature) in real problems; and real losses aren't single quadratics.
2. **(After MSE gradient):** "At the optimum, residuals are uncorrelated with inputs. What pattern in a residual-vs-input plot would reveal a bad fit?" → Curvature/structure in residuals → model is missing something (preview of feature engineering, W12).
3. **(After SGD):** "SGD is noisy. Why would anyone *want* noise?" → Cheap steps + escaping shallow local minima in non-convex landscapes.
4. **(After scaling):** "Why is scaling on the full dataset leakage?" → Test statistics leak into training — the model sees information about the test world.

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "How do I pick $\eta$ in practice?" | Try a range (log scale), watch the loss curve, tune on validation. Schedules exist (decay) — Week 17. |
| "What if the loss isn't convex?" | GD still runs; no guarantee of the global minimum. Initialization and SGD noise start to matter — neural networks. |
| "What's a subgradient, really?" | The set of slopes of lines that stay below the function at a kink. At a smooth point: the derivative. Enough to run GD. (1 min.) |
| "Does GD always converge for lasso?" | With proper step-size rules, subgradient methods converge for convex nonsmooth problems — statement only, no proof here. |

### Quiz S3 Design Notes

Calculation-forward: one full GD iteration on a quadratic; regime identification; one conceptual (SGD vs. batch). See `quiz_S3.md`.

---

## Session 4 (70 min): Logistic Regression I — The Sigmoid, Cross-Entropy, and the Model

### Learning Objectives

By the end of this session, students should be able to:
1. Explain why linear regression is the wrong tool for 0/1 targets, and why accuracy (0-1 loss) can't be optimized directly.
2. State and prove the sigmoid's key properties, including $\sigma'(z) = \sigma(z)(1-\sigma(z))$.
3. Write the logistic model $P(y=1\mid x) = \sigma(wx+b)$ and show its decision boundary is the line $wx + b = 0$.
4. **Derive cross-entropy as the negative log-likelihood of the Bernoulli model (MLE).**
5. Connect: Gaussian → MSE, Bernoulli → cross-entropy (third row of the correspondence table).
6. ★ Attempt the gradient computation (the beautiful cancellation) — full treatment in Week 8.

### Materials Needed

- Whiteboard, colored markers
- Desmos with $\sigma(z)$ plotted (and $z$-slider) — see `visual_demos.md`
- Quiz S4 printed or ready to project

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:03 | **The pivot: "today we change the task."** | Regression → classification. |
| 0:03–0:12 | **Why not linear regression for classification? Why not accuracy as loss?** | Two failure sketches. Motivates probability + smooth surrogate. |
| 0:12–0:25 | **The sigmoid: definition, properties, the miracle derivative (proved).** | Desmos. Saturation. |
| 0:25–0:33 | **The model + decision boundary.** | 2D picture: line, normal vector $w$, confident vs. uncertain regions. |
| 0:33–0:50 | **Cross-entropy = negative log-likelihood (the derivation).** | Bernoulli → product → log → recognize the pattern. The correspondence table. |
| 0:50–0:58 | **Behavior of the loss + regularized logistic regression (one line).** | Confidently-wrong → ∞. MAP story carries over verbatim. |
| 0:58–1:04 | **★ The beautiful cancellation (guided preview).** | Set up the chain; let strong students complete it. Full derivation: Week 8 S1. |
| 1:04–1:10 | **Quiz S4** (6 min). | Sigmoid properties + cross-entropy identification. |

### Hook: "Same Skeleton, New Task" (3 min)

Draw the Week-1 pipeline (Session 1's map) on the board again:

```
   data → [model] → [loss] → [solver] → [evaluate]
```

"Today we swap exactly two boxes: the *model* (line → sigmoid-wrapped line) and the *loss* (MSE → cross-entropy). The solver is *the same GD you did by hand yesterday*. The evaluation is *the same metrics from Week 4*. This is how ML knowledge compounds: new tasks are mostly re-combinations."

### Board Work: Why Not Linear Regression? Why Not Accuracy? (9 min)

**Sketch 1 — line on 0/1 data:** predictions like $-0.3$ or $2.7$ — not probabilities; a single far-away point drags the line (leverage) and shifts predictions everywhere.

**Sketch 2 — 0-1 loss:** draw accuracy vs. $w$ — a staircase. "Nudge $w$: nothing changes, or one point flips. Gradient is 0 almost everywhere. The math is *blind* here." → We need a **smooth surrogate**: big penalty when confidently wrong, small when confidently right. "Keep this phrase — 'smooth surrogate for 0-1 loss' — it's also the story of SVMs (Week 13)."

**The design goal:** model $P(y = 1 \mid x) \in (0,1)$, then threshold.

### Board Work: The Sigmoid (13 min)

1. **Definition:** $\sigma(z) = 1/(1+e^{-z})$. Desmos: slide $z$ from $-6$ to $+6$.
2. **Properties checklist (students verify each):**
   - $\sigma(0) = 1/2$; limits 0 and 1.
   - $\sigma(-z) = 1 - \sigma(z)$ (symmetry: $1/(1+e^{z})$).
   - Monotone; S-shaped; "squashes" $\mathbb{R} \to (0,1)$.
3. **The miracle derivative — PROVE IT (this is the quiz question):**

$$\sigma'(z) = \frac{e^{-z}}{(1+e^{-z})^2} = \frac{1}{1+e^{-z}} \cdot \frac{e^{-z}}{1+e^{-z}} = \sigma(z)\big(1 - \sigma(z)\big)$$

   "The derivative of the sigmoid is written *in terms of the sigmoid itself*. No new computation. Remember this — tomorrow (Week 8) it triggers the most beautiful cancellation in basic ML."
4. **Saturation:** max slope $1/4$ at $z=0$; slope $\to 0$ at $\pm\infty$. "Confident neurons learn slowly — unless the loss compensates. File this away; it returns in Week 15 (why ReLU won)."

### Board Work: The Model and Decision Boundary (8 min)

1. $P(y=1\mid x) = \sigma(wx+b)$; predict 1 iff $wx + b > 0$ iff $P > 1/2$.
2. 2D picture: the line $w_1x_1 + w_2x_2 + b = 0$; $w$ is the normal; $|b|/\lVert w\rVert$ = distance to origin.
3. Far from the line on the + side: $P \approx 1$. On the line: $P = 1/2$ — "the model tells you when it doesn't know. That's worth more than a bare yes/no."
4. **Spiral-back:** "How would a threshold other than 0.5 change precision/recall?" → Lower threshold: recall ↑, precision ↓ (W4). ★ The optimal threshold under costs: $t^* = c_{FP}/(c_{FP}+c_{FN})$ — challenge problem 7-4C.

### Board Work: Cross-Entropy = Negative Log-Likelihood (17 min) — THE core derivation

**Build it as Week-5 MLE applied to a new likelihood — because that's all it is.**

1. "Given $x_i$, the label is a coin flip with success probability $\hat p_i = \sigma(wx_i+b)$. Write the Bernoulli PMF:"

$$P(y_i \mid x_i) = \hat{p}_i^{\,y_i}(1-\hat{p}_i)^{1-y_i}$$

2. "Likelihood of the dataset (i.i.d.):" — product.
3. "Log (the Week-5 trick):"

$$\ell(w,b) = \sum_i \big[y_i \log \hat p_i + (1-y_i)\log(1-\hat p_i)\big]$$

4. "MLE maximizes $\ell$. Equivalent: minimize the negative. **That object already has a name — cross-entropy:**"

$$L(w,b) = -\frac{1}{n}\sum_i \big[y_i \log \hat p_i + (1-y_i)\log(1-\hat p_i)\big]$$

5. **Box the correspondence table** (third row now filled):

| Label model | Loss |
|---|---|
| Gaussian | MSE |
| Laplacian | MAE |
| **Bernoulli** | **cross-entropy** |

   "Same miracle, third instance: **the loss function is the negative log-likelihood.** You don't memorize losses — you *derive* them from your beliefs about the noise."

### Board Work: Why Cross-Entropy Is the Right Shape (8 min)

1. Table (have students compute entries):
   - $y=1$, $\hat p \to 1$: loss $\to 0$.
   - $y=1$, $\hat p \to 0$: loss $\to \infty$. "Confidently wrong: punished without mercy. Unlike MSE, which is merely quadratic in the error."
   - $\hat p = 1/2$: loss $= \log 2 \approx 0.69$ — "honest ignorance has a fixed price."
2. Convexity (statement): cross-entropy in $(w,b)$ through the sigmoid is **convex** — GD finds the global optimum. "Same guarantee as linear regression. Enjoy it — it's the last convex model before neural networks."
3. **Regularization carries over (one line):** MAP with Gaussian prior → $+ \lambda w^2$; Laplacian → $+ \lambda|w|$. "Session 2's theorem wasn't about regression. It was about *all* of ML."

### ★ Guided Preview: The Beautiful Cancellation (6 min)

Write the chain on the board and stop:

$$\frac{\partial L_i}{\partial w} = \underbrace{\frac{\hat p_i - y_i}{\hat p_i(1-\hat p_i)}}_{\partial L_i/\partial \hat p_i} \cdot \underbrace{\sigma'(z_i)}_{=\ \hat p_i(1-\hat p_i)} \cdot x_i$$

"Predict what happens when we multiply." → The $\hat p(1-\hat p)$ factors cancel exactly:

$$\frac{\partial L_i}{\partial w} = (\hat p_i - y_i)\,x_i$$

"Prediction error × input — the SAME structure as the MSE gradient from yesterday, and no saturation factor survives. Full derivation and GD training: next session (Week 8 S1). Try to complete it at home if you dare — it's Challenge 7-4B."

### Discussion Prompts

1. **(After the model):** "The decision boundary is linear. What data can this model NOT separate?" → XOR, circles (draw them). "Fixes: features (W12) or neural nets (W15)."
2. **(After cross-entropy):** "Why is $\log 2$ the price of uncertainty?" → At $\hat p = 1/2$ the model assigns probability 1/2 to the truth; $-\log(1/2) = \log 2$. Information-theoretic preview (W11).
3. **(After the table):** "What loss would a Poisson likelihood give?" → (They can't know yet — the point is the *question*: losses come from likelihoods.)
4. **(Cancellation preview):** "Why is it a problem if the gradient carries a $\hat p(1-\hat p)$ factor?" → It vanishes when saturated — learning stops exactly when the model is confidently wrong. Cross-entropy removes this pathology.

### Anticipated Questions

| Question | How to Answer |
|----------|--------------|
| "Why is it called *regression* if it's classification?" | It regresses the *probability* (log-odds) — a regression of $\sigma(wx+b)$ onto $[0,1]$; classification comes from thresholding. ★ Section 21 of the handout has the log-odds view. |
| "Why 0.5 as the default threshold?" | Symmetric costs / balanced classes. With costs, $t^* = c_{FP}/(c_{FP}+c_{FN})$ (Challenge 7-4C). |
| "Can we use MSE on $\hat p$?" | You can — it's convex-ish and it works poorly: the $\hat p(1-\hat p)$ factor survives and saturating examples stop learning. Cross-entropy is *the* fix. |
| "Is cross-entropy KL divergence?" | Yes: $H(p,q) = H(p) + D_{KL}(p\|q)$; with one-hot labels $H(p)=0$, so minimizing cross-entropy = minimizing KL. Full story Week 11. |
| "Multi-class?" | Softmax regression — next session (Week 8 S2). |

### Quiz S4 Design Notes

Focus: sigmoid properties (including the derivative), identifying cross-entropy as negative log-likelihood, decision boundary. The gradient derivation is NOT quizzed yet (Week 8). See `quiz_S4.md`.

---

## Challenge Questions for Advanced Students

### Session 1 Challenges

**Challenge 7-1A: The Leverage Point**
*(Give after the OLS re-derivation — around minute 35)*

> One training point is moved far to the right (huge $x_i$) while keeping its $y_i$. Predict (before computing) what happens to $w^*$, $b^*$, and the training/test error. Then verify with the formulas.

**Instructor notes:**
- Large $x_i$ inflates both Cov and Var, but its residual dominates the fit — the line chases it (leverage).
- Prediction: slope tilts toward the point; test error typically worsens (variance ↑). Connects to W4 outliers and robustness (MAE vs. MSE — Laplacian noise).

**Challenge 7-1B: Averaging Learners**
*(Give after the bias-variance discussion preview — end of session)*

> Suppose you train the SAME model class on many random training sets and average the resulting predictions. Which term of the (upcoming) bias-variance decomposition does this reduce? What model family from Week 3 does this hint at?

**Instructor notes:**
- Averaging over datasets kills the variance term (B averages to $\bar f$) — bias survives.
- This is exactly bagging / random forests (Week 10). "You just invented ensembling."

---

### Session 2 Challenges

**Challenge 7-2A: The Generalized Prior**
*(Give after MAP = Ridge — around minute 37)*

> What penalty does the prior $p(w) \propto e^{-w^4 / \tau^4}$ (a "quartic" prior) induce? Predict its sparsity behavior (zeros or not?) and its treatment of large weights compared to ridge.

**Instructor notes:**
- Penalty $\propto w^4$: smoother than Gaussian at 0 (no sparsity), *harsher* on large weights (stronger shrinkage of outliers).
- Point: **the shape of the prior IS the shape of the penalty.** Students should see the dictionary at work.

**Challenge 7-2B: TheProsecutor's Fallacy (reprise)**
*(Give after the Bayes re-run — around minute 12)*

> DNA at a crime scene matches the suspect (random match probability 1/10,000). The prosecutor: "So the chance he's innocent is 1/10,000." What's wrong? What prior information do you need?

**Instructor notes:**
- Confuses $P(\text{match}\mid\text{innocent})$ with $P(\text{innocent}\mid\text{match})$.
- Needs the pool size $N$ of potential suspects: for $N = 100$, $P(\text{guilty}\mid\text{match}) \approx 50\%$.
- (This was Challenge 6C-1A; re-offer it — spaced repetition for the sharp students.)

---

### Session 3 Challenges

**Challenge 7-3A: GD on Ridge, Closed Form via Fixed Point**
*(Give after ridge GD — around minute 50)*

> For ridge with the update $w \leftarrow w(1 - 2\eta\lambda) + \frac{2\eta}{n}\sum x_i r_i$: at convergence ($w$ stops moving), write the fixed-point equation and solve for $w$ in terms of the data. Compare with Week 2's closed form.

**Instructor notes:**
- Fixed point: $w = w(1-2\eta\lambda) + \frac{2\eta}{n}\sum x_i r_i \Rightarrow 2\eta\lambda w = \frac{2\eta}{n}\sum x_i r_i \Rightarrow w = \frac{1}{n\lambda}\sum x_i r_i$.
- Consistent with the scalar ridge solution (with $\lambda$ scaled appropriately): "GD converges to the same place the formula points."

**Challenge 7-3B: Design a Divergence Detector**
*(Give after the loss-curve diagnostics — around minute 58)*

> You observe the loss: $10.0 \to 10.8 \to 11.6 \to 12.7 \to \ldots$ growing roughly geometrically (ratio $\approx 1.1$). Diagnosis? Which regime is $\eta$ in, relative to $2/a$? What is the *first* thing you try, and by what factor?

**Instructor notes:**
- Divergence: $|1 - \eta a| > 1$. $\eta$ beyond $2/a$ (or data not scaled).
- First fix: divide $\eta$ by 10; also check feature scaling.

---

### Session 4 Challenges

**Challenge 7-4A: Sigmoid Symmetries**
*(Give after the miracle derivative — around minute 25)*

> (a) Prove $\sigma(-z) = 1 - \sigma(z)$. (b) Using the product rule on $\sigma(z)\sigma(-z)$, give an alternative proof that $\sigma'(z) = \sigma(z)(1-\sigma(z))$.

**Instructor notes:**
- (a) Direct algebra: $1/(1+e^{z})$.
- (b) $\sigma(z)\sigma(-z)$ is constant? No — but differentiating $\sigma(-z) = 1-\sigma(z)$ with the chain rule gives $-\sigma'(-z) = -\sigma'(z)$... the clean route: differentiate the identity $\sigma(z) + \sigma(-z) = 1$? That yields $\sigma'(z) = \sigma'(-z)$. The intended clean proof: $y = \sigma(z) \iff z = \log\frac{y}{1-y}$; differentiate implicitly: $\frac{dy}{dz} = y(1-y)$. Any valid proof accepted — the *inverse-function* route is the gem.

**Challenge 7-4B: The Beautiful Cancellation (the real thing)**
*(Give at the preview — around minute 60)*

> Complete the derivation: for a single example, show $\frac{\partial L_i}{\partial w} = (\hat p_i - y_i)x_i$ and $\frac{\partial L_i}{\partial b} = \hat p_i - y_i$, where $\hat p_i = \sigma(wx_i+b)$. Then write the full-batch GD updates and compare their structure with linear regression's.

**Instructor notes:**
- The cancellation: $\frac{\hat p - y}{\hat p(1-\hat p)} \cdot \hat p(1-\hat p) \cdot x_i = (\hat p - y)x_i$.
- Updates: $w \leftarrow w + \frac{\eta}{n}\sum (\hat p_i - y_i) x_i$ — "probability error × input," mirroring "value error × input" for MSE.
- This IS next session's opener — early solvers get to present.

**Challenge 7-4C: The Optimal Threshold**
*(Give after the decision boundary discussion — around minute 33)*

> False positives cost $c_{FP}$, false negatives cost $c_{FN}$. Show that the expected cost is minimized by predicting "1" iff $P(y=1\mid x) > \frac{c_{FP}}{c_{FP}+c_{FN}}$.

**Instructor notes:**
- Predict 1 iff expected cost of 1 < expected cost of 0: $(1-p)c_{FP} < p\,c_{FN} \iff p > \frac{c_{FP}}{c_{FP}+c_{FN}}$.
- Cancer screening: $c_{FN} \gg c_{FP} \Rightarrow t^* \to$ small → recall-prioritizing. "Week 4's precision/recall dial, now with a formula."

---

## Homework (after Session 4, due Week 8)

1. **Re-derive** MAP = Ridge and the bias-variance cross-terms from memory (check against handout Sections 4 and 6).
2. **Compute by hand:** two full GD iterations on $f(w) = \frac{1}{2} \cdot 4w^2$ starting from $w_0 = 2$ with $\eta = 0.3$. Verify the ratio $|1 - \eta a|$ and predict the long-run behavior.
3. **Attempt** Challenge 7-4B (the cancellation) — it is next session's opener.
4. **Read** the suggested paper (Wagstaff, 2012 — see `suggested_paper.md`).
5. ★ **Log-odds:** verify handout Section 21 — show $\log\frac{P(y=1\mid x)}{P(y=0\mid x)} = wx + b$.

---

## Post-Session Checklist

- [ ] Review quiz results (all four sessions)
- [ ] Update the actual-teaching log (create `actual_teaching_log_w1_w7.md` or extend)
- [ ] Update student progress tracker — flag anyone red on MAP=Ridge or the MSE gradient
- [ ] Prepare Week 8 (matrix regression + logistic regression II + Phase 1 consolidation)

## Preparation Checklist

### Before Session 1
- [ ] Read handout Sections 1–3
- [ ] Prepare the retrieval warm-up (6 questions) — board or projector
- [ ] Prepare the fresh confusion-matrix problem (numbers from these notes)
- [ ] Have exam error statistics ready (top 2–3 issues only)
- [ ] Print quiz S1

### Before Session 2
- [ ] Read handout Sections 4–7
- [ ] Prepare the MAP=Ridge board work as a *question chain* (not a lecture)
- [ ] Prepare the A+B+C bias-variance board layout with colors
- [ ] Prepare sticky notes/cards for the traffic-light self-assessment
- [ ] Print quiz S2

### Before Session 3
- [ ] Read handout Sections 8–15
- [ ] Pre-draw the iteration table skeleton on the board (saves 5 min)
- [ ] Load the Desmos demo with the three learning-rate runs
- [ ] Rehearse the MSE-gradient chain-rule question chain
- [ ] Print quiz S3

### Before Session 4
- [ ] Read handout Sections 16–22
- [ ] Load the sigmoid Desmos demo (z-slider)
- [ ] Prepare the 2D decision-boundary sketch (line + normal vector)
- [ ] Prepare the correspondence table as a reveal (three rows, cover the third)
- [ ] Print quiz S4
- [ ] Read the suggested paper (Wagstaff, 2012) and skim `suggested_paper.md` discussion questions
