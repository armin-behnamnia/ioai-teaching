# Week 3 — Visual Demos

> **Purpose:** Interactive visual demonstrations to use in class. Each demo includes the setup, what to show, and key teaching points. These are designed to make abstract concepts visceral.

---

## Demo 1: Polynomial Overfitting — Degree 1 vs. 3 vs. n−1 on Same Data

**Tool:** Desmos Graphing Calculator (https://www.desmos.com/calculator)  
**Used in:** Session 1, minutes 30–45  
**Prep time:** 10 minutes

### Setup

Open Desmos and create the following:

**Step 1: Enter data points**

Create a table of 8 points that roughly follow $y \approx 0.3x^2$ with noise:

| x | y |
|---|---|
| 1 | 0.5 |
| 2 | 1.2 |
| 3 | 2.8 |
| 4 | 4.8 |
| 5 | 7.5 |
| 6 | 10.8 |
| 7 | 14.7 |
| 8 | 19.2 |

In Desmos, use the table feature (click the "+" button and select "table").

**Step 2: Create three models using Desmos regression**

Enter each as a regression (Desmos fits automatically):

1. **Degree 1 (line — underfitting):**  
   `y1 ~ a·x1 + b`

2. **Degree 3 (cubic — good fit):**  
   `y1 ~ a·x1^3 + b·x1^2 + c·x1 + d`

3. **Degree 7 (through all points — overfitting):**  
   `y1 ~ a·x1^7 + b·x1^6 + c·x1^5 + d·x1^4 + e·x1^3 + f·x1^2 + g·x1 + h`

*Tip:* To make the three models visible separately, color-code them and toggle visibility on/off during the demo.

### What to Show

**Part A: Underfitting — Degree 1 (3 min)**

1. Show only the data points and the degree-1 fit.
2. Ask: "How well does this line fit?" → Students: "Not great — the data curves, the line doesn't."
3. Ask: "What's the training error?" → Moderate/high. The line misses the curvature.
4. Ask: "Can we do better?" → Yes, by using a higher degree.
5. **Key message:** "This is underfitting. The hypothesis space (lines) is too small. The model can't capture the quadratic pattern."

**Part B: Good Fit — Degree 3 (3 min)**

1. Turn on the degree-3 fit. It should curve nicely through the data.
2. Ask: "Is this perfect?" → No, but close. Small residuals.
3. Ask: "Would you trust this to predict y at x = 4.5?" → Yes. The curve is smooth and reasonable between data points.
4. Ask: "What's the training error?" → Low.
5. **Key message:** "This is a good fit. The model captures the pattern. The residuals are small and random."

**Part C: Overfitting — Degree 7 (4 min)**

1. Turn on the degree-7 fit. It passes through EVERY data point exactly.
2. Ask: "What's the training error?" → Zero!
3. Ask: "Look at the curve between x=4 and x=5. What's happening?" → The curve oscillates wildly between data points.
4. Ask: "If I asked you to predict y at x = 4.5, what would this model predict?" → Point to the curve. It might give a value like 30 or -10 — wildly wrong.
5. Zoom out to show the oscillations more clearly.
6. Ask: "Which model would you trust: degree 3 or degree 7?" → Degree 3!
7. **Key message:** "This is overfitting. Zero training error, terrible predictions. The model memorized the training data — including the noise."

**Part D: The Lesson (2 min)**

Show all three models overlaid:
- Degree 1: too simple → high training error, high test error
- Degree 3: just right → low training error, low test error
- Degree 7: too complex → zero training error, high test error

**Key message:** "More complexity does NOT mean better. There's a sweet spot. The art of ML is finding it."

### Quick Setup Alternative

Pre-build the Desmos graph in advance, save it, and open the saved version in class. This avoids typing during the demo.

---

## Demo 2: The U-Shaped Test Error Curve

**Tool:** Desmos (or whiteboard drawing)  
**Used in:** Session 1, minutes 55–65  
**Prep time:** 5 minutes

### Setup

**Option A: Desmos (preferred)**

Create a plot showing both training error and test error as functions of polynomial degree.

**Training error** (monotonically decreasing):  
`R_train(d) = 10·0.5^d` (decreases exponentially toward 0)

**Test error** (U-shaped):  
`R_test(d) = 10·0.5^d + 2·(d-2)^2·0.3` (decreases then increases)

Add sliders or just plot for integer d = 1, 2, 3, ..., 10.

*Alternative:* Use the actual data from the handout (Section 2.3, the worked example with 8 points). Compute train/test MSE for degrees 1–10 and plot as a table + scatter.

**Option B: Whiteboard**

Draw the curve by hand. This is faster and sufficient if Desmos is not set up.

### What to Show

1. **Show the training error curve first.** It goes down monotonically.  
   Ask: "Will this ever go up?" → No! More complexity = lower (or equal) training error.

2. **Add the test error curve.** It goes down, reaches a minimum, then goes back up.  
   Ask: "Why does test error go up?" → The model starts fitting noise, not signal.

3. **Label the three zones:**
   - Left: underfitting zone (both errors high)
   - Middle: sweet spot (test error minimized)
   - Right: overfitting zone (train ≈ 0, test high)

4. **Mark the generalization gap:** the vertical distance between the two curves.  
   Ask: "Where is the gap largest?" → In the overfitting zone (right side).  
   Ask: "Where is the gap smallest?" → In the underfitting zone (left side) — both errors are similar (both high).

5. **Point to the sweet spot.**  
   "This is where we want to be. Every model has this curve — not just polynomials."

### Teaching Tips

- **This is the most important figure in ML.** Spend time here. Make students draw it themselves on paper.
- Emphasize: "The x-axis could be degree, 1/λ, 1/k, depth, or number of parameters. The shape is always the same."
- Connect to Demo 1: "Degree 1 is here (left), degree 3 is here (middle), degree 7 is here (right)." Point to the corresponding locations on the curve.

---

## Demo 3: Ridge Shrinking Weights — The λ Slider

**Tool:** Desmos  
**Used in:** Session 2, minutes 15–25  
**Prep time:** 5 minutes

### Setup

Open Desmos and set up the following:

**Data points (same quadratic data as Demo 1):**

| x | y |
|---|---|
| 1 | 0.5 |
| 2 | 1.2 |
| 3 | 2.8 |
| 4 | 4.8 |
| 5 | 7.5 |
| 6 | 10.8 |
| 7 | 14.7 |
| 8 | 19.2 |

**Model:** Degree-7 polynomial with ridge regularization.

In Desmos, set up a regression with a regularization term. Desmos doesn't directly support ridge regression, so use this workaround:

**Step 1:** Define the OLS degree-7 fit (for reference):
`y1 ~ a·x1^7 + b·x1^6 + c·x1^5 + d·x1^4 + e·x1^3 + f·x1^2 + g·x1 + h`

**Step 2:** Create a manual polynomial with a λ slider that shrinks all coefficients:
```
L = 0  (slider: 0 to 100, step 0.1)
f(x) = (1-L/(L+100))·(a·x^7 + b·x^6 + c·x^5 + d·x^4 + e·x^3 + f·x^2 + g·x + h) + (L/(L+100))·(mean_y)
```

*Note:* This is a simplified approximation. The true ridge solution requires matrix algebra (Week 8). For the demo, the key is showing the *effect* of λ: as λ increases, the curve smooths out.

**Alternative (simpler and more accurate for scalar case):**

Use the scalar ridge formula from the handout:
```
w_ridge = Cov(x,y) / (Var(x) + λ)
```

Plot the data, the OLS line, and the ridge line with a λ slider. As λ increases, the slope shrinks toward zero.

### What to Show

**Part A: λ = 0 (OLS) — 2 min**

1. Show the OLS degree-7 fit. It oscillates wildly (same as Demo 1).
2. Ask: "What's the training error?" → Zero. "Test error?" → High.
3. **Key message:** "No regularization = full overfitting."

**Part B: λ = 0.1 (moderate) — 2 min**

1. Increase λ to 0.1. The curve smooths dramatically.
2. The oscillations disappear. The curve looks like a nice quadratic.
3. Ask: "What happened?" → The penalty forced the coefficients to be small, preventing oscillations.
4. Ask: "Did the training error go up or down?" → Up (the model no longer passes through every point).
5. Ask: "Did the test error go up or down?" → Down! The model generalizes better.
6. **Key message:** "A small amount of regularization dramatically improves generalization."

**Part C: λ = 100 (extreme) — 2 min**

1. Increase λ to 100. The curve becomes almost flat.
2. Ask: "What does the model predict now?" → Approximately ȳ (the mean of y) for everything.
3. Ask: "Is this good?" → No! It's underfitting. The model is too constrained.
4. **Key message:** "Too much regularization = underfitting. The model can't even capture the real pattern."

**Part D: The Lesson — 1 min**

"λ is a dial:
- λ = 0: full complexity (OLS, overfit)
- λ moderate: sweet spot
- λ → ∞: zero complexity (constant, underfit)

The validation curve (which we'll see next) tells us where the sweet spot is."

### Teaching Tips

- If using the scalar version (simple linear regression with ridge), the effect is less dramatic but mathematically precise. Show both if time permits: the scalar version for understanding, the polynomial version for impact.
- Connect to the bias-variance table: "λ = 0 is low bias, high variance. λ = 100 is high bias, low variance. The sweet spot is in between."

---

## Demo 4: L1 vs. L2 Constraint Geometry — Diamond vs. Circle

**Tool:** Desmos (or whiteboard drawing)  
**Used in:** Session 2, minutes 40–55  
**Prep time:** 5 minutes

### Setup

**Option A: Desmos (preferred for animation)**

Open Desmos and plot:

1. **L2 constraint (circle):**  
   `x^2 + y^2 = 1`  
   (This is $\|\mathbf{w}\|^2 = 1$ in 2D: $w_1^2 + w_2^2 = 1$.)

2. **L1 constraint (diamond):**  
   `|x| + |y| = 1`  
   (This is $\|\mathbf{w}\|_1 = 1$ in 2D: $|w_1| + |w_2| = 1$.)

3. **OLS solution point (arbitrary, for illustration):**  
   Plot a point at (2, 2) — this represents the unregularized OLS solution, "outside" the constraint region.

4. **Contours of the loss function (concentric circles around OLS):**  
   `(x-2)^2 + (y-2)^2 = r^2` with a slider for r.  
   The optimal regularized solution is where the smallest loss contour touches the constraint region.

### What to Show

**Part A: The L2 Ball (Circle) — 3 min**

1. Show only the circle (`x^2 + y^2 = 1`) and the OLS point at (2, 2).
2. Ask: "The OLS solution is at (2,2), but the constraint says we must be inside the circle. Where's the closest point on the circle to (2,2)?"
3. Students will point to the northeast part of the circle — roughly (0.7, 0.7).
4. Mark this point. Note: BOTH coordinates are nonzero.
5. **Key message:** "Ridge shrinks the weights toward zero, but they stay nonzero. The solution lands on the circle, not on an axis."

**Part B: The L1 Ball (Diamond) — 4 min**

1. Turn on the diamond (`|x| + |y| = 1`). Turn off the circle.
2. Ask: "Now the constraint is the diamond. Where's the closest point on the diamond to (2,2)?"
3. Students may point to the corner at (1, 0) or (0, 1). The closest point is on the corner!
4. Mark the corner at (1, 0). Note: $w_2 = 0$ exactly!
5. **Key message:** "Lasso's diamond has CORNERS on the axes. The solution often lands on a corner, where one weight is exactly zero. That feature is eliminated — automatic feature selection!"

**Part C: Side by Side — 2 min**

1. Show both the circle and the diamond simultaneously.
2. Plot the OLS point at (2, 2).
3. Show the ridge solution (on circle, both nonzero) and lasso solution (on diamond corner, one zero).
4. **Key message:** "Same OLS point, different constraint shapes → different solutions. The geometry determines the behavior."

**Part D: Moving the OLS Point — 2 min**

1. Move the OLS point to different locations: (2, 0.5), (0.5, 2), (1, 1).
2. For each, ask: "Where does the lasso solution land? Still on a corner?"
3. When the OLS point is near an axis (e.g., (2, 0.1)), the lasso solution is on the corner (1, 0). When it's at (1, 1), the lasso solution might be on the edge (0.5, 0.5), not a corner.
4. **Key message:** "Lasso doesn't ALWAYS produce zeros. It depends on the data. But the diamond geometry makes zeros MUCH more likely than the circle."

### Teaching Tips

- **This is the most important visual of Session 2.** Students must SEE the diamond vs. circle to understand why lasso gives sparsity.
- If Desmos is unavailable, draw both shapes on the whiteboard. The key features are: circle (smooth, no corners) vs. diamond (sharp corners on axes).
- Emphasize: "The corners are the key. Corners = axes = zero weights = feature selection."
- Connect to the nondifferentiability discussion: "The corners of the diamond are the same corners where |w| is not differentiable. The geometry and the calculus are telling the same story."

---

## Demo 5: Residual Analysis — Good Fit vs. Underfit

**Tool:** Desmos (or whiteboard drawing)  
**Used in:** Session 2, minutes 70–72 (brief)  
**Prep time:** 5 minutes

### Setup

**In Desmos:**

**Data:** Same 8 quadratic points from Demo 1.

**Model 1: Good fit (degree 3):**  
`y1 ~ a·x1^3 + b·x1^2 + c·x1 + d`

**Model 2: Underfit (degree 1):**  
`y1 ~ a·x1 + b`

**Compute residuals for each:**

For the good fit, plot residuals: `(x1, y1 - f(x1))` as a scatter plot.
For the underfit, plot residuals: `(x1, y1 - g(x1))` as a scatter plot.

Where `f(x)` is the degree-3 fit and `g(x)` is the degree-1 fit.

### What to Show

**Part A: Good Fit Residuals (1 min)**

1. Show the residual plot for the degree-3 model.
2. The residuals should scatter randomly around zero — no pattern.
3. Ask: "Do you see a pattern?" → No. Random scatter.
4. **Key message:** "Random residuals = good fit. The model captured all the signal. What's left is noise."

**Part B: Underfit Residuals (1 min)**

1. Show the residual plot for the degree-1 model.
2. The residuals should show a clear U-shaped pattern (positive at the ends, negative in the middle, or vice versa).
3. Ask: "Do you see a pattern?" → Yes! A clear curve.
4. **Key message:** "Pattern in residuals = underfitting. The model missed a nonlinear pattern. We need polynomial features (higher degree)."

**Part C: The Connection (30 sec)**

"Residual analysis is a diagnostic tool. It tells you WHAT's wrong:
- Random residuals → good fit (or fully overfit — check the test error to distinguish)
- Pattern in residuals → underfitting (add complexity)
- Random residuals + high test error → overfitting (the model fit the training noise)"

### Teaching Tips

- Keep this demo BRIEF — 2 minutes maximum. It's a preview, not a deep dive. Residual analysis is covered more in Week 4 (model evaluation).
- Connect to Week 2: "Remember from Week 2: OLS residuals are uncorrelated with x. If they ARE correlated (show a pattern), the linear model is inadequate."
- If time is short, draw the two residual plots on the whiteboard instead of using Desmos.

---

## Demo 6: The Complexity Dial — Unifying Diagram

**Tool:** Whiteboard drawing (no software needed)  
**Used in:** Session 2, minutes 65–70  
**Prep time:** None

### What to Draw

Draw the universal complexity table and the U-curve side by side:

**Left side — the table:**

```
Model                  | Knob     | Low ←────────→ High
───────────────────────|──────────|─────────────────────
Polynomial regression  | Degree d | d=1         d=n−1
Ridge regression       | λ        | λ→∞         λ=0
Lasso                  | λ        | λ→∞         λ=0
k-NN (Week 9)          | k        | k=n         k=1
Decision trees (W10)   | Depth    | Depth 1     Depth ∞
Neural networks (W15)  | # params | Few         Millions
```

**Right side — the curve:**

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
     ← simple    complex →
     (underfit)  (overfit)
```

### Teaching Points

1. **"Every model has a complexity dial."** Point to each row of the table. "Degree, λ, k, depth, number of parameters — they're all the same knob."

2. **"The curve is always the same."** Point to the U-curve. "No matter what model you use, test error goes down then up. The x-axis label changes, but the shape doesn't."

3. **"The art of ML is finding the sweet spot."** Point to the minimum of the U-curve. "This is what model selection and hyperparameter tuning are about. We'll formalize this in Week 4 with cross-validation."

4. **"Direction matters."** For ridge, increasing λ means moving LEFT (simpler). For degree, increasing d means moving RIGHT (more complex). The x-axis is "complexity," which may be proportional or inversely proportional to the knob.

5. **Connect to future weeks:** Point to the k-NN and decision tree rows. "When we learn these models, you'll see the same U-curve. k=1 overfits (memorizes); k=n underfits (predicts ȳ). Tree depth=1 underfits; depth=∞ overfits. Same story, different knobs."

### Teaching Tips

- **Leave this diagram on the board for the rest of the session.** Students should see it while taking the quiz. It's the unifying mental model.
- Ask students to fill in the k-NN and decision tree rows themselves (they haven't learned these yet, but they can guess from the pattern). This creates anticipation for Weeks 9–10.
- Say: "If you remember one thing from this week, remember this diagram. Every ML model, every technique, every research paper is ultimately about this curve."

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Polynomial overfitting (deg 1 vs 3 vs 7) | S1 | 15 min | Desmos | See overfitting/underfitting viscerally |
| 2 | U-shaped test error curve | S1 | 10 min | Desmos/Whiteboard | The most important figure in ML |
| 3 | Ridge shrinking weights (λ slider) | S2 | 10 min | Desmos | See λ control model complexity |
| 4 | L1 vs. L2 constraint geometry | S2 | 15 min | Desmos | Why lasso gives sparsity |
| 5 | Residual analysis (good vs. underfit) | S2 | 2 min | Desmos/Whiteboard | Diagnose underfitting from residuals |
| 6 | The complexity dial (unifying diagram) | S2 | 5 min | Whiteboard | All knobs are the same knob |

**Total demo time:** ~57 minutes across both sessions. This leaves ~23 minutes per session for lecture, discussion, and quizzes.

---

## Pre-Class Tech Check

Before each session, verify:

- [ ] Desmos loads and the saved graphs work (Demos 1–4)
- [ ] Data points are entered correctly in Desmos tables
- [ ] Regression syntax works (test `y1 ~ ...` before class)
- [ ] λ slider is set up with appropriate range (Demo 3)
- [ ] L1/L2 geometry graph renders correctly (Demo 4)
- [ ] Whiteboard has enough space for the complexity dial diagram (Demo 6)
- [ ] Quiz printed or ready to project
- [ ] Challenge questions printed on sticky notes (if using)
