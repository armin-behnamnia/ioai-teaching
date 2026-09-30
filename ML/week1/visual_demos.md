# Week 1 — Visual Demos

> **Purpose:** Interactive visual demonstrations to use in class. Each demo includes the setup, what to show, and key teaching points. These are designed to make abstract concepts visceral.

---

## Demo 1: Fitting Lines and Curves — Overfitting Made Visceral

**Tool:** Desmos Graphing Calculator (https://www.desmos.com/calculator)  
**Used in:** Session 2, minutes 20–35  
**Prep time:** 5 minutes

### Setup

Open Desmos and create the following:

**Step 1: Enter data points**

Create a table of 8 points that roughly follow $y \approx 2x$ with noise:

| x | y |
|---|---|
| 1 | 2.1 |
| 2 | 3.9 |
| 3 | 5.8 |
| 4 | 8.2 |
| 5 | 10.1 |
| 6 | 11.7 |
| 7 | 14.3 |
| 8 | 15.8 |

In Desmos, type each point as `(1, 2.1)` on separate lines, or use the table feature.

**Step 2: Create three models**

Enter each as a separate equation with sliders:

1. **Constant model (underfitting):**  
   `f_1(x) = c`  
   Add slider for `c`. Set range 0–20.

2. **Linear model (good fit):**  
   `f_2(x) = m·x + b`  
   Add sliders for `m` (range 0–5) and `b` (range -5–5).`

3. **Degree-7 polynomial (overfitting):**  
   ```
   f_3(x) = a_7·x^7 + a_6·x^6 + a_5·x^5 + a_4·x^4 + a_3·x^3 + a_2·x^2 + a_1·x + a_0
   ```  
   Add sliders for all 8 coefficients. (Tedious but worth it.)  
   *Alternative:* Use Desmos regression: `f_3(x) ~ a_7·x^7 + a_6·x^6 + ... + a_0` and Desmos will fit automatically.

### What to Show

**Part A: Underfitting (3 min)**

1. Show only the data points and `f_1(x) = c`.
2. Adjust `c` to ~9 (the mean of y values). The line is flat.
3. Ask: "How well does this fit?" → Students: "Terribly."
4. Ask: "Can we do better with this model?" → No. A constant function is the best we can do. The model is too simple.
5. **Key message:** "This is underfitting. The hypothesis space (constants) is too small to capture the pattern."

**Part B: Good Fit (3 min)**

1. Add `f_2(x) = m·x + b`.
2. Adjust `m` to ~2 and `b` to ~0. The line passes through the cloud of points.
3. Ask: "Is this perfect?" → No. Some points are above, some below.
4. Ask: "Is this better than the constant?" → Yes! Much lower error.
5. Ask: "Could we reduce the error further?" → Yes, by using a more complex model. But should we?
6. **Key message:** "This is a good fit. The model captures the trend. The residual errors look random — that's what we want."

**Part C: Overfitting (4 min)**

1. Add the degree-7 polynomial. Use Desmos regression to fit it.
2. The curve will pass through EVERY data point exactly.
3. Ask: "What's the training error?" → Zero!
4. Ask: "Look at the curve between x=4 and x=5. What's happening?" → The curve swings wildly between data points.
5. Ask: "If I asked you to predict y at x=4.5, what would this model predict?" → Point to the curve. It might give a value like 20 or -5 — wildly wrong.
6. Ask: "Which model would you trust for predictions: the line or the polynomial?" → The line!
7. **Key message:** "This is overfitting. Zero training error, terrible predictions. More flexibility is NOT always better."

**Part D: The Lesson (2 min)**

Show all three models overlaid:
- Constant: too simple → high training error, high test error
- Linear: just right → moderate training error, low test error
- Degree-7: too complex → zero training error, high test error

Draw (or point to) the overfitting-underfitting picture from the handout. Connect the visual to the table:

```
Underfit (constant)  →  Good fit (linear)  →  Overfit (degree-7)
   too simple            balanced              too complex
   stable but wrong      good predictions      unstable, fits noise
```

### Quick Setup Alternative

If you don't have time to set up sliders manually, use this pre-made Desmos activity:

1. Go to https://www.desmos.com/calculator
2. Paste the following data points as a table
3. Use regression syntax `y1 ~ m x1 + b` for linear fit
4. Use `y1 ~ a x1^7 + b x1^6 + c x1^5 + d x1^4 + e x1^3 + f x1^2 + g x1 + h` for polynomial fit

Or, prepare the activity in advance, save it, and open the saved version in class.

---

## Demo 2: Neural Network Playground — Visualizing Learning

**Tool:** TensorFlow Playground (https://playground.tensorflow.org)  
**Used in:** Session 2 (optional, if time permits — or as a "teaser" at the end)  
**Prep time:** 2 minutes (just open the website)

### Setup

1. Open https://playground.tensorflow.org
2. Select the "Spiral" dataset (bottom-left of the dataset selection).
3. Set features to $X_1$ and $X_2$ only (the two original features).

### What to Show

**Part A: Underfitting (2 min)**

1. Set the network to **0 hidden layers** (just the output layer).
2. Set activation to linear.
3. Click Play.
4. The model tries to separate the spiral classes with a straight line. It fails completely.
5. **Key message:** "A linear model can't separate a spiral. The hypothesis space is too small."

**Part B: Good Fit (2 min)**

1. Add **2 hidden layers** with 4 neurons each.
2. Set activation to ReLU (or tanh).
3. Click Play.
4. The network gradually learns the spiral pattern. The decision boundary curves around the spiral.
5. Point out: "Watch the loss curve go down. The model is learning!"
6. **Key message:** "A nonlinear model with enough capacity can capture complex patterns."

**Part C: Overfitting (2 min)**

1. Increase to **4 hidden layers** with 8 neurons each.
2. Turn OFF regularization (set regularization rate to 0).
3. Reset and Play.
4. The decision boundary becomes very complex — it may fit the training data perfectly but have jagged, unreasonable boundaries.
5. Turn ON L2 regularization (set rate to 0.1). Reset and Play.
6. The boundary becomes smoother.
7. **Key message:** "More neurons = more capacity = overfitting risk. Regularization constrains the model to be simpler."

### Teaching Tips

- **This is a teaser.** Don't explain how neural networks work. Just say: "We'll learn exactly how this works in Weeks 14–16. For now, just watch the model learn."
- **Focus on the visual.** Students should SEE: (1) the data, (2) the model getting better over time, (3) the effect of complexity and regularization.
- **Connect to Demo 1.** "The spiral with a linear boundary is like our constant model. The spiral with a good network is like our linear fit. The over-complex network is like our degree-7 polynomial."

---

## Demo 3: The Learning Rate Visual

**Tool:** Desmos  
**Used in:** Session 2, briefly (1–2 min) — as a preview of Week 3  
**Prep time:** 1 minute

### Setup

Enter: `L(w) = (w - 3)^2`  
Add a point at `w_0` and show the tangent line.

### What to Show

1. Show the parabola $L(w) = (w-3)^2$. The minimum is at $w = 3$.
2. Place a point at $w = 0$ (starting point).
3. "Imagine you're a ball at $w = 0$. You want to roll to the bottom at $w = 3$. Which direction do you go?"
4. Students: "Right!" (toward increasing $w$).
5. "How do you know?" → "Because the slope is negative, so going right decreases the loss."
6. **Preview:** "This is gradient descent. We'll formalize it in Week 3."

**Keep this very brief** — it's a teaser, not a lesson. 1–2 minutes maximum.

---

## Demo 4: Spam vs. Not Spam — Decision Boundary Intuition

**Tool:** Whiteboard drawing (no software needed)  
**Used in:** Session 1, during the "Why not just write rules?" section  
**Prep time:** None

### What to Draw

Draw a 2D plane with:
- X-axis: "Contains word 'FREE'" (0 or 1)
- Y-axis: "Contains word 'MONEY'" (0 or 1)

Plot:
- Red dots (spam) in the upper-right quadrant (both words present)
- Blue dots (not spam) in the lower-left quadrant (neither word present)
- A few red dots and blue dots scattered near the boundary

Draw a diagonal line separating the two classes. This is a **decision boundary**.

### Teaching Points

1. "This line is our model. Points above the line → spam. Below → not spam."
2. "Where should we put the line? That's the learning problem."
3. "What if we add more features — sender, time of day, subject length? Now it's not a 2D plane anymore. It's high-dimensional. We can't draw it, but the math works the same."
4. **Connect to the framework:** "The line is our hypothesis. The distance from each point to the line (on the wrong side) is related to our loss. Moving the line to minimize total error is learning."

---

## Demo 5: The Stability-Accuracy Bullseye

**Tool:** Whiteboard drawing (or project the classic image)  
**Used in:** Session 2, during overfitting-underfitting discussion  
**Prep time:** None

### What to Draw

Draw four bullseye targets, each with a cluster of dart marks:

```
  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐
  │    ⊕    │   │    ⊕    │   │  ⊕      │   │      ⊕  │
  │   · ·   │   │ ·     · │   │   · · · │   │  ·  ·   │
  │  ·   ·  │   │·   ⊕   ·│   │  ·   ·  │   │   ·  ·  │
  │   · ·   │   │ ·     · │   │   · · · │   │  ·  ·   │
  │    ·    │   │    ·    │   │         │   │      ·  │
  └─────────┘   └─────────┘   └─────────┘   └─────────┘
   Accurate      Consistently  Right on      Wrong AND
   & Stable      Wrong         Average but   Inconsistent
                               Scattered
   "Ideal"       "Underfit"    "Overfit"     "Worst Case"
   (hits center  (like our      (like a bad   (both problems
    reliably)     constant)      degree-7      at once)
                                poly)
```

### Teaching Points

- **Accurate & stable (top-left):** Darts hit the center, tightly clustered. This is what we want — the model is correct and reliable.
- **Consistently wrong (top-right):** Darts are off-center but clustered. The model is stable but always wrong. This is **underfitting** — like our constant model. It's too simple to capture the pattern.
- **Right on average but scattered (bottom-left):** Darts are centered but spread out. The model sometimes gets it right but is unreliable. This is **overfitting** — like our degree-7 polynomial. It fits one dataset perfectly but would fit a different dataset differently.
- **Wrong and inconsistent (bottom-right):** The worst case. Both problems at once.

**Key message:** "There are two ways to fail: being consistently wrong (too simple) or being unreliable (too complex). We can't just make the model more complex to fix being wrong, because that makes it unreliable. This tension — between accuracy and stability — is the central challenge of ML. In Week 5, after we learn probability, we'll formalize this mathematically as the 'bias-variance decomposition.'"

---

## Demo 6: What Does a Neural Network See? (Optional Teaser)

**Tool:** Projected images (no software needed)  
**Used in:** Session 1, during the hook (if time permits)  
**Prep time:** Find 2–3 images

### What to Show

1. Show a photo of a cat. "You see a cat. What does a computer see?" 
2. Show the same photo as a grid of numbers (pixel values). "A computer sees a grid of numbers. 0 = black, 255 = white."
3. "How do we get from numbers to 'cat'? That's what neural networks do. They learn to transform numbers into concepts."
4. **Don't explain how.** Just plant the seed. "We'll see exactly how in Weeks 26–27."

### Alternative

Use the "Edge Detection" visualization from Distill or 3Blue1Brown:
- Show how early layers detect edges
- Later layers detect textures
- Even later layers detect object parts (ears, eyes)
- Final layer: "cat"

This gives students an intuition for *why* deep learning works without any math.

---

## Summary of Demos

| # | Demo | Session | Time | Tool | Purpose |
|---|------|---------|------|------|---------|
| 1 | Fitting lines and curves | S2 | 15 min | Desmos | Overfitting made visceral |
| 2 | Neural Network Playground | S2 | 6 min | TF Playground | See learning happen; teaser for NNs |
| 3 | The learning rate visual | S2 | 2 min | Desmos | Teaser for gradient descent |
| 4 | Spam decision boundary | S1 | 5 min | Whiteboard | Decision boundary intuition |
| 5 | Stability-accuracy bullseye | S2 | 3 min | Whiteboard | Overfitting-underfitting intuition |
| 6 | What a NN sees | S1 | 3 min | Images | Motivate deep learning |

**Total demo time:** ~34 minutes across both sessions. This leaves ~46 minutes per session for lecture, discussion, and quizzes.

---

## Pre-Class Tech Check

Before each session, verify:

- [ ] Desmos loads and the saved graph works
- [ ] TensorFlow Playground loads (check internet connection)
- [ ] Images display correctly on the projector
- [ ] Whiteboard has enough space for drawings and formulas
- [ ] Quiz printed or ready to project
