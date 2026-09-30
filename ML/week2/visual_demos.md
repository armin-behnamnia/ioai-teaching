# Week 2 — Visual Demos

> **Purpose:** Interactive visual demonstrations to use in class. Each demo includes the setup, what to show, and key teaching points. These are designed to make abstract concepts visceral.

---

## Demo 1: Line-Fitting with Sliders — Minimizing MSE Visually

**Tool:** Desmos Graphing Calculator (https://www.desmos.com/calculator)  
**Used in:** Session 1, minutes 8–20 (during the model + MSE introduction)  
**Prep time:** 5 minutes

### Setup

Open Desmos and create the following:

**Step 1: Enter the ice cream data points**

Create a table (use Desmos table feature or type each point):

| x (temp) | y (sales) |
|----------|-----------|
| 15 | 120 |
| 20 | 180 |
| 25 | 200 |
| 30 | 280 |
| 35 | 320 |

In Desmos, type each point as `(15, 120)` on separate lines, or use the table feature (`+` → Table).

**Step 2: Create the line model with sliders**

Enter:
```
f(x) = w·x + b
```
Add sliders for `w` (range 0–20, step 0.1) and `b` (range -100–200, step 1).

**Step 3: Create the MSE display**

Enter the MSE as a function of the current $w$ and $b$:
```
MSE = (1/5) · ((f(15) - 120)^2 + (f(20) - 180)^2 + (f(25) - 200)^2 + (f(30) - 280)^2 + (f(35) - 320)^2)
```

Display the MSE value on screen. You can also add a visual indicator: colored squares at each data point representing the squared error.

**Optional — show squared errors visually:**

For each point, add a line segment showing the residual:
```
segment: (15, 120) to (15, f(15))
segment: (20, 180) to (20, f(20))
...
```
Set the segment color to red. These are the "residuals" — the vertical distances being squared and summed.

### What to Show

**Part A: Manual Line Fitting (4 min)**

1. Show the data points and the line $f(x) = wx + b$ with sliders.
2. Start with $w = 0, b = 220$ (a flat line at the mean of $y$). Ask: "How good is this?" → MSE is high. The line ignores the trend.
3. Slowly increase $w$. Watch the line tilt up. Ask students to call out when the line "looks best."
4. Adjust $b$ to shift the line up and down. Ask: "Where should the line sit vertically?"
5. Let 2–3 students come up and adjust the sliders themselves. They'll converge near $w \approx 10, b \approx -30$.
6. Display the MSE value as they adjust. "Watch the number — it goes down as the line gets better."
7. **Key message:** "The best line minimizes the MSE. Right now you're finding it by trial and error. Today we'll derive the EXACT formula for the best $w$ and $b$."

**Part B: The Optimal Line (2 min)**

1. After deriving $w^*$ and $b^*$ on the board, set the sliders to $w = 10, b = -30$.
2. Show the MSE value: 120.
3. Ask: "Can anyone get a lower MSE by adjusting the sliders?" → Let them try. They can't (it's the optimum).
4. Point to the red residual segments. "Some are positive, some negative. They sum to zero."
5. Mark the centroid: add the point `(25, 220)` in a distinct color. Show the line passes through it.
6. **Key message:** "The optimal line passes through the centroid $(\bar{x}, \bar{y})$. The residuals sum to zero. These are not coincidences — they're consequences of the math."

**Part C: What Squared Error Penalizes (2 min)**

1. Move one data point far away (e.g., change (25, 200) to (25, 400) — an outlier).
2. Ask: "What happens to the MSE?" → It jumps dramatically. "The squared error amplifies large errors."
3. Ask: "What happens to the line?" → It shifts toward the outlier. "MSE is sensitive to outliers — the square makes large errors very costly."
4. Move the point back. "This is one downside of MSE. We'll discuss robust alternatives (Huber loss) in the exercises."
5. **Key message:** "Squaring the error means we care MORE about large errors than small ones. This is a design choice with consequences."

### Quick Setup Alternative

If you don't have time to set up the MSE display, just use the line with sliders and have students eyeball the fit. You can compute the MSE by hand on the board after. The visual fitting is the main point.

---

## Demo 2: Polynomial Overfitting — Degree 1 vs. Degree n−1

**Tool:** Desmos  
**Used in:** Session 2, minutes 10–25  
**Prep time:** 5 minutes

### Setup

**Step 1: Enter slightly noisy data points**

Use 6–7 points that roughly follow a linear trend but with noise:

| x | y |
|---|---|
| 1 | 2.5 |
| 2 | 3.8 |
| 3 | 7.2 |
| 4 | 7.9 |
| 5 | 11.1 |
| 6 | 11.8 |

These follow $y \approx 2x$ with noise.

**Step 2: Create three models**

1. **Degree 1 (linear):**
   ```
   f_1(x) = m·x + b
   ```
   Use Desmos regression: `y1 ~ m·x1 + b` (Desmos fits automatically). Or use sliders.

2. **Degree 3 (moderate):**
   ```
   f_3(x) = a·x^3 + b·x^2 + c·x + d
   ```
   Use Desmos regression: `y1 ~ a·x1^3 + b·x1^2 + c·x1 + d`

3. **Degree 5 (interpolation — passes through all points):**
   ```
   f_5(x) = a·x^5 + b·x^4 + c·x^3 + d·x^2 + e·x + f
   ```
   Use Desmos regression: `y1 ~ a·x1^5 + b·x1^4 + c·x1^3 + d·x1^2 + e·x1 + f`
   
   With 6 data points and 6 parameters, this polynomial passes through every point exactly.

### What to Show

**Part A: The Good Fit — Degree 1 (3 min)**

1. Show only the data and `f_1(x)`. The line captures the upward trend.
2. Ask: "Is this perfect?" → No. Some points are above, some below.
3. Ask: "What's the training error?" → Small but nonzero.
4. Ask: "Would you trust this to predict $y$ at $x = 4.5$?" → Yes, it would give ~9.5, reasonable.
5. **Key message:** "A line with 2 parameters captures the trend without chasing noise. This is a good fit."

**Part B: The Overfit — Degree 5 (4 min)**

1. Add `f_5(x)`. The curve passes through EVERY data point exactly.
2. Ask: "What's the training error?" → Zero!
3. Ask: "Look at the curve between $x = 3$ and $x = 4$. What's happening?" → The curve dips or spikes wildly between data points.
4. Ask: "If I asked you to predict $y$ at $x = 4.5$, what would this model predict?" → Point to the curve. It might give something like 15 or -3 — wildly wrong.
5. Ask: "Which model would you trust: the line or the degree-5 polynomial?" → The line!
6. **Key message:** "Zero training error does NOT mean a good model. The degree-5 polynomial memorized the data — including the noise. It will make terrible predictions on new data. This is overfitting."

**Part C: The Middle Ground — Degree 3 (2 min)**

1. Add `f_3(x)`. The curve is smoother than degree 5 but more flexible than degree 1.
2. Ask: "Is this better or worse than the line?" → Hard to tell from training error alone. This is the model selection problem.
3. Ask: "How could we decide?" → We need a test set. We'll learn this in Week 4.
4. **Key message:** "As we increase the polynomial degree, training error always decreases. But test error may increase. The question is: where is the sweet spot?"

**Part D: The Complexity Spectrum (2 min)**

Show all three models overlaid:
- Degree 1: too simple → may underfit
- Degree 3: moderate → may be just right
- Degree 5: too complex → overfits

Draw (or point to) the complexity spectrum:

```
Degree 1 (2 params)    Degree 3 (4 params)    Degree 5 (6 params)
   ←── underfitting ──?── good fit ──?── overfitting ──→
   
Training error:   HIGH      MEDIUM      ZERO
Test error:       HIGH      LOW (?)     HIGH
```

5. **Key message:** "Overfitting depends on the ratio of model complexity (number of parameters) to data size ($n$). More parameters = more flexibility = more overfitting risk. We need a way to control complexity. That's regularization."

### Teaching Tips

- **Don't show the degree-5 polynomial first.** Always start with the line. Students need to see the "good" before the "bad."
- **Emphasize the wild oscillations.** The visual impact of a polynomial swinging between data points is the most memorable image of Week 2. Linger on it.
- **Connect to Week 1.** "This is the SAME overfitting we saw last week — but now in a concrete model. Last week it was abstract; today it's a polynomial."

---

## Demo 3: Ridge Regression — Shrinking the Slope with λ

**Tool:** Desmos  
**Used in:** Session 2, minutes 25–40 (during ridge regression section)  
**Prep time:** 5 minutes

### Setup

**Step 1: Use the same ice cream data**

Keep the 5 data points from Demo 1:
(15, 120), (20, 180), (25, 200), (30, 280), (35, 320).

**Step 2: Create the ridge line with a λ slider**

The ridge solution is $w^*_{\text{ridge}} = \text{Cov}(x,y) / (\text{Var}(x) + \lambda) = 500 / (50 + \lambda)$ and $b^*_{\text{ridge}} = 220 - w^*_{\text{ridge}} \cdot 25$.

In Desmos, enter:
```
w_r = 500 / (50 + λ)
b_r = 220 - w_r · 25
f_ridge(x) = w_r · x + b_r
```
Add a slider for `λ` (range 0–500, step 1).

**Step 3: Also show the OLS line for comparison**

```
f_ols(x) = 10·x - 30
```

**Step 4: Show both MSE values**

```
MSE_ridge = (1/5) · ((f_ridge(15) - 120)^2 + (f_ridge(20) - 180)^2 + (f_ridge(25) - 200)^2 + (f_ridge(30) - 280)^2 + (f_ridge(35) - 320)^2)
MSE_ols = 120
```

### What to Show

**Part A: λ = 0 — Ridge Equals OLS (2 min)**

1. Set $\lambda = 0$. The ridge line overlaps the OLS line exactly.
2. "When $\lambda = 0$, there's no penalty. Ridge is just OLS."
3. Show both MSE values are 120.

**Part B: Increasing λ — The Slope Shrinks (4 min)**

1. Slowly increase $\lambda$. Watch the ridge line rotate toward horizontal.
2. At $\lambda = 25$: $w_r \approx 6.67$. The line is less steep. "The slope shrinks — the model is more conservative."
3. At $\lambda = 100$: $w_r \approx 3.33$. Even flatter.
4. At $\lambda = 450$: $w_r = 1$. The line is nearly flat.
5. At $\lambda = 1000$ (or large): $w_r \approx 0.48$. The line is almost horizontal at $\bar{y} = 220$.
6. **Key observation:** "As $\lambda$ increases, the slope shrinks toward zero. At $\lambda \to \infty$, the model predicts $\bar{y}$ for everything — it ignores $x$ entirely. This is extreme underfitting."

**Part C: The Tradeoff (3 min)**

1. Watch the MSE_ridge value as you increase $\lambda$. It increases monotonically.
2. "The training MSE goes UP as $\lambda$ increases. Ridge fits the training data WORSE than OLS."
3. "So why use ridge? Because we care about TEST error, not training error. If OLS was overfitting, ridge's worse training fit might correspond to BETTER test performance."
4. Draw (or sketch on the board) the expected test error curve:

```
   Test MSE
   │  ╲           ╱
   │   ╲         ╱
   │    ╲       ╱
   │     ╲     ╱
   │      ╲___╱  ← optimal λ
   │             ↑
   └──────────────────── λ
   0           
   
   OLS    sweet spot    underfit
```

5. **Key message:** "$\lambda$ controls the overfitting-underfitting tradeoff. Too small → overfit. Too large → underfit. Just right → good generalization. We'll learn how to find the sweet spot (cross-validation) in Week 4."

**Part D: The Centroid (1 min)**

1. Mark the centroid `(25, 220)`.
2. As you vary $\lambda$, the ridge line ALWAYS passes through the centroid.
3. "The ridge line passes through $(\bar{x}, \bar{y})$ just like OLS. The penalty is on the slope, not the intercept — so the intercept still centers the line."

### Teaching Tips

- **The visual of the line rotating toward horizontal is the key image.** Students should see ridge regression as "the line getting lazier" — less reactive to $x$.
- **Emphasize: training error goes UP.** Students expect regularization to "improve" the model. It improves TEST error, not training error. This is counterintuitive and important.
- **Connect to the formula.** "The only difference between OLS and ridge is the $+\lambda$ in the denominator. OLS: $500/50 = 10$. Ridge ($\lambda = 25$): $500/75 = 6.67$. The denominator gets bigger, the slope gets smaller. It's that simple."

---

## Demo 4: The Centroid — The Line Through the Center of the Data

**Tool:** Desmos (or whiteboard)  
**Used in:** Session 2, minutes 52–57 (during geometric perspective)  
**Prep time:** 3 minutes

### Setup

**Step 1: Use the ice cream data**

Same 5 points: (15, 120), (20, 180), (25, 200), (30, 280), (35, 320).

**Step 2: Mark the centroid**

Add the point `(25, 220)` — this is $(\bar{x}, \bar{y})$. Make it a distinct color (green or orange) and larger.

**Step 3: Show the OLS line**

```
f(x) = 10·x - 30
```

**Step 4: Add a "wrong" line that doesn't pass through the centroid**

```
g(x) = 10·x - 10
```
(Same slope, different intercept — doesn't pass through centroid.)

### What to Show

**Part A: The Centroid (2 min)**

1. Show the data and the centroid point. "The centroid is the 'center of mass' of the data: $(\bar{x}, \bar{y}) = (25, 220)$."
2. Show the OLS line. "Notice: the line passes EXACTLY through the centroid."
3. Verify: $f(25) = 250 - 30 = 220$. ✓

**Part B: Why the Centroid? (2 min)**

1. Show the "wrong" line $g(x) = 10x - 10$ (same slope, shifted up). It doesn't pass through the centroid.
2. Ask: "Is this line better or worse?" → Worse. The MSE is higher.
3. "Why? Because the intercept is wrong. The best intercept for ANY slope places the line through the centroid. $b^* = \bar{y} - w\bar{x}$ ensures this."
4. Demonstrate: change the slope of $f(x)$ to anything (5, 15, -3). The optimal intercept for that slope would still put the line through the centroid.
5. **Key message:** "No matter what slope you choose, the best intercept centers the line on the data's centroid. This is a geometric fact, not a coincidence."

**Part C: Residuals Sum to Zero (2 min)**

1. Show the OLS line with residual segments (vertical lines from each data point to the line).
2. Some residuals are positive (point above line), some negative (point below line).
3. "The residuals sum to zero: the positive and negative errors exactly balance."
4. This follows from the line passing through the centroid: if the line goes through the center, the average residual is zero.
5. **Key message:** "The OLS line doesn't systematically over- or under-predict. It's balanced. The positive and negative errors cancel."

### Teaching Tips

- **The centroid is the most memorable geometric fact of linear regression.** Students should leave knowing: "The best-fit line goes through the center of the data."
- **Connect to physics.** The centroid is like the center of mass. The residuals are like forces — they balance around the center.
- **Preview Week 8.** "In higher dimensions, the centroid becomes a projection of the data onto the feature space. The residuals being 'balanced' becomes 'perpendicular.' Same idea, fancier language."

---

## Demo 5: R² — Explained vs. Unexplained Variance

**Tool:** Desmos (or whiteboard)  
**Used in:** Session 2, minutes 57–62 (during R² section)  
**Prep time:** 5 minutes

### Setup

**Step 1: Use the ice cream data and OLS line**

Same setup as Demo 1: data points + $f(x) = 10x - 30$.

**Step 2: Add the "mean model" — a horizontal line at $\bar{y}$**

```
mean_line(x) = 220
```
This is the "baseline" model: predict $\bar{y}$ for everything.

**Step 3: Show two types of error segments**

- **Red segments:** from each data point to the OLS line (residuals = unexplained error)
- **Blue segments:** from each data point to the mean line (total deviation = total variance)

### What to Show

**Part A: The Mean Model — Total Variance (2 min)**

1. Show only the data and the mean line (`mean_line(x) = 220`).
2. Show blue segments from each point to the mean line. "These are the deviations from the mean — the total variance of $y$."
3. "If we had NO model, the best we could do is predict $\bar{y} = 220$. The total squared deviation is $\text{SS}_{\text{tot}} = 25600$."
4. "This is our baseline. Any model worth its salt should do better than this."

**Part B: The OLS Model — Residuals (2 min)**

1. Add the OLS line $f(x) = 10x - 30$.
2. Show red segments from each point to the OLS line. "These are the residuals — what the model DIDN'T explain."
3. "The total squared residual is $\text{SS}_{\text{res}} = 600$. Much smaller than 25600!"
4. "The model explained most of the variance. The red segments are much shorter than the blue ones."

**Part C: R² as a Ratio (2 min)**

1. Write the formula: $R^2 = 1 - \text{SS}_{\text{res}} / \text{SS}_{\text{tot}} = 1 - 600/25600 = 0.977$.
2. "R² = 97.7% means: 97.7% of the variance in $y$ is explained by the model. Only 2.3% is unexplained (residual)."
3. Visually: "Imagine the blue segments (total variance) as a pie. The model 'ate' 97.7% of that pie. Only 2.3% is left (the red segments)."
4. Ask: "What would $R^2 = 1$ look like?" → All red segments would be zero — every point on the line.
5. Ask: "What would $R^2 = 0$ look like?" → The red segments would be as long as the blue ones — the model is no better than predicting $\bar{y}$.
6. **Key message:** "$R^2$ measures what fraction of the variance the model explains. $R^2 = 1$ is perfect. $R^2 = 0$ is useless. $R^2 < 0$ means the model is worse than just predicting the average."

### Teaching Tips

- **The visual of red segments (residuals) being much shorter than blue segments (total deviations) is the key image.** Students should SEE that the model "explains" most of the variation.
- **The pie analogy works well.** Total variance = the whole pie. Explained variance = the slice the model accounts for. $R^2$ = fraction of the pie explained.
- **Connect to correlation.** "$R^2 = r^2$. If $r = 0.988$ (strong correlation), then $R^2 = 0.977$ (97.7% of variance explained). Correlation and regression are two views of the same thing."
- **Don't overcomplicate.** The formula $R^2 = 1 - \text{SS}_{\text{res}}/\text{SS}_{\text{tot}}$ is simple. The visual makes it visceral. Don't add more math than needed.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Line-fitting with sliders | S1 | 8 min | Desmos | MSE minimization made visceral |
| 2 | Polynomial overfitting | S2 | 11 min | Desmos | Overfitting in regression |
| 3 | Ridge regression shrinking | S2 | 10 min | Desmos | How λ controls the slope |
| 4 | Centroid visualization | S2 | 6 min | Desmos/Whiteboard | Geometric meaning of OLS |
| 5 | R² explained vs. unexplained | S2 | 6 min | Desmos/Whiteboard | What R² means visually |

**Total demo time:** ~41 minutes across both sessions. This leaves ~39 minutes per session for lecture, derivation, discussion, and quizzes.

> **Note:** Demos 1 and 2 can be combined into a single Desmos graph (same data points). Demos 3, 4, and 5 can also share one graph. This reduces transitions. Prepare one Desmos graph per session.

---

## Pre-Class Tech Check

Before each session, verify:

- [ ] Desmos loads and the saved graphs work (test the slider ranges)
- [ ] Data points display correctly on the projector
- [ ] The MSE formula in Desmos computes correctly (check the value at the optimal line)
- [ ] Whiteboard has enough space for both the derivation and the demo
- [ ] Quiz printed or ready to project
- [ ] Calculators available for students (for the worked example in Session 1)
