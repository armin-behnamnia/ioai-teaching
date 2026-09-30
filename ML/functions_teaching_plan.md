# Problem-Based Teaching Plan: Functions, Graphs & Transformations

**Format:** 3 sessions × 60 minutes
**Approach:** Problem-Based Learning (PBL) — each session opens with a motivating problem, develops theory through guided discovery, and closes with consolidation.

---

## Session 1 — The Concept of a Function, Domain & Range (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Explain what a function is and identify valid vs. invalid function definitions.
- Determine the domain and range of a function from its formula and its graph.
- Recognize and work with common functions (linear, quadratic, square root, absolute value, reciprocal).
- Identify functions from tables, mappings, and graphs (the vertical line test).

### Materials
- Whiteboard / projector
- Graph paper handout
- Colored markers
- Mini-whiteboards for pair work

---

### Part A: Hook — The Vending Machine Problem (8 min)

**Present this scenario:**

> You walk up to a vending machine. The machine has buttons labeled **A1, A2, B1, B2**. Each button corresponds to a specific product:
>
> | Button | Product |
> |---|---|
> | A1 | Water |
> | A2 | Chips |
> | B1 | Water |
> | B2 | Chocolate |
>
> You press **A1** and get Water. You press **A1** again and get Water again.
>
> **Question 1:** Can you press **A1** and sometimes get Water, sometimes get Chips?
>
> **Question 2:** Can two different buttons give the same product? (Look at A1 and B1 — both give Water.)

**Key realization:**
- A button always gives the **same** product → this is what makes it a *function*.
- Two buttons can give the *same* product → that's fine for a function.
- One button giving *different* products on different presses → **not** a function.

**Write the formal definition:**

> ### What Is a Function?
> A **function** `f` from a set `A` to a set `B` is a rule that assigns to **each** element of `A` **exactly one** element of `B`.
>
> - `A` is called the **domain** (the set of inputs).
> - `B` is called the **codomain** (the set of possible outputs).
> - The set of actual outputs is called the **range**.
> - Notation: `f: A → B`, or `y = f(x)`.

**The vending machine analogy:**
- Domain = set of buttons `{A1, A2, B1, B2}`
- Range = set of products `{Water, Chips, Chocolate}`
- Rule: button → product
- One button → one product (always): **function** ✓

---

### Part B: Identifying Functions (12 min)

#### Activity 1: Is It a Function? (5 min — pairs)

For each, determine if it's a function. If not, explain why.

1. `f(x) = 2x + 3`
2. `f(x) = x²`
3. `f(x) = ±√x` *(takes both positive and negative roots)*
4. `y² = x` *(given `x`, find `y`)*
5. `f(x) = |x|`
6. `x = 5` *(a vertical line)*

**Debrief:**

| # | Function? | Why? |
|---|---|---|
| 1 | Yes ✓ | Each `x` gives exactly one `2x+3` |
| 2 | Yes ✓ | Each `x` gives exactly one `x²` |
| 3 | **No** ✗ | `f(4) = ±2` — one input gives two outputs |
| 4 | **No** ✗ | `x = 1` → `y = ±1` — one input gives two outputs |
| 5 | Yes ✓ | `|x|` is uniquely defined for each `x` |
| 6 | **No** ✗ | `x = 5` means infinitely many `y`-values for one `x` |

#### The Vertical Line Test (4 min)

**Present the rule:**

> ### Vertical Line Test
> A graph represents a function if and only if **no vertical line** intersects the graph at more than one point.
>
> - A vertical line that hits the graph twice means one `x`-value has two `y`-values → not a function.

**Show on the board:** Quick sketches of:
- A parabola `y = x²` → passes the test ✓
- A circle `x² + y² = 1` → vertical line hits twice ✗
- A sideways parabola `x = y²` → vertical line hits twice ✗
- `y = √x` → passes ✓ (only the upper half)
- `y = |x|` → passes ✓

#### Activity 2: Function Notation (3 min)

Evaluate `f(x) = 3x² − 2x + 1` at:

1. `f(0) = 1`
2. `f(1) = 3 − 2 + 1 = 2`
3. `f(−1) = 3 + 2 + 1 = 6`
4. `f(2) = 12 − 4 + 1 = 9`
5. `f(a) = 3a² − 2a + 1`
6. `f(x+h) = 3(x+h)² − 2(x+h) + 1 = 3x²+6xh+3h²−2x−2h+1`

**Teaching note:** Problem 6 is important — students will need this when they learn derivatives (difference quotient). Don't rush it.

---

### Part C: Domain & Range (20 min)

#### The Big Idea (5 min)

> ### Domain = "What can I put in?"
> ### Range = "What comes out?"

**Two ways to find domain:**

1. **From a formula:** Look for things that are **impossible** or **undefined**:
   - Division by zero (denominator = 0)
   - Square root of a negative number (for real-valued functions)
   - Log of zero or negative (covered later)

2. **From a graph:** Domain = projection onto the `x`-axis; Range = projection onto the `y`-axis.

**Write on the board:**

> ### Domain Restrictions to Remember
> | Expression | Problem | Domain condition |
> |---|---|---|
> | `1/(g(x))` | Division by zero | `g(x) ≠ 0` |
> | `√(g(x))` | Negative under root | `g(x) ≥ 0` |
> | `polynomial` | None | All real numbers (`ℝ`) |
> | `|g(x)|` | None | All real numbers |

#### Activity 3: Find the Domain (8 min — individual)

1. `f(x) = 3x² − 5x + 2`
   → Polynomial → **Domain: ℝ (all reals)**

2. `f(x) = 1/(x − 4)`
   → Denominator ≠ 0 → `x ≠ 4` → **Domain: `ℝ \ {4}`**

3. `f(x) = √(x + 3)`
   → `x + 3 ≥ 0` → `x ≥ −3` → **Domain: `[−3, ∞)`**

4. `f(x) = √(4 − x²)`
   → `4 − x² ≥ 0` → `x² ≤ 4` → `|x| ≤ 2` → **Domain: `[−2, 2]`**

5. `f(x) = 1/(x² − 9)`
   → `x² − 9 ≠ 0` → `x ≠ ±3` → **Domain: `ℝ \ {−3, 3}`**

6. `f(x) = √(x − 1) / (x − 3)`
   → `x − 1 ≥ 0` AND `x − 3 ≠ 0` → `x ≥ 1` and `x ≠ 3` → **Domain: `[1, 3) ∪ (3, ∞)`**

7. `f(x) = √(x² − 5x + 6)`
   → `x² − 5x + 6 ≥ 0` → `(x−2)(x−3) ≥ 0` → **Domain: `(−∞, 2] ∪ [3, ∞)`**
   *(This connects directly to the inequality unit!)*

8. `f(x) = 1/√(x + 2)`
   → `x + 2 > 0` (strict — can't have zero in denominator or negative under root) → **Domain: `(−2, ∞)`**

#### Activity 4: Find the Range (7 min)

**Method:** For simple functions, think about what outputs are possible.

1. `f(x) = x²`
   → Squares are ≥ 0 → **Range: `[0, ∞)`**

2. `f(x) = x² + 3`
   → Shifted up → **Range: `[3, ∞)`**

3. `f(x) = −x² + 5`
   → Opens downward, max at 5 → **Range: `(−∞, 5]`**

4. `f(x) = |x| − 2`
   → `|x| ≥ 0`, so `|x|−2 ≥ −2` → **Range: `[−2, ∞)`**

5. `f(x) = √(x + 3)`
   → Square root ≥ 0 → **Range: `[0, ∞)`**

6. `f(x) = 1/(x − 4)`
   → Reciprocal never equals 0 → **Range: `ℝ \ {0}`**

7. `f(x) = 1/√(x + 2)`
   → `√(x+2) > 0` (strictly), so `1/√(x+2) > 0` → **Range: `(0, ∞)`**

---

### Part D: Common Functions — Gallery Walk (12 min)

**Present these on the board (or handout) one at a time.** For each, sketch the graph and note key features.

#### 1. Linear Function: `f(x) = mx + b`

```
Domain: ℝ        Range: ℝ
Graph: straight line with slope m, y-intercept b
```
- `m > 0`: increasing →
- `m < 0`: decreasing ←
- `m = 0`: constant (horizontal line)

#### 2. Quadratic Function: `f(x) = ax² + bx + c`

```
Domain: ℝ        Range: [vertex, ∞) if a > 0; (−∞, vertex] if a < 0
Graph: parabola
```
- Vertex at `x = −b/(2a)`
- Opens up if `a > 0`, down if `a < 0`

#### 3. Square Root Function: `f(x) = √x`

```
Domain: [0, ∞)     Range: [0, ∞)
Graph: starts at origin, curves right and up
```

#### 4. Absolute Value Function: `f(x) = |x|`

```
Domain: ℝ         Range: [0, ∞)
Graph: V-shape, vertex at origin
```

#### 5. Reciprocal Function: `f(x) = 1/x`

```
Domain: ℝ \ {0}     Range: ℝ \ {0}
Graph: hyperbola, two branches
Asymptotes: x = 0 (vertical), y = 0 (horizontal)
```

#### 6. Piecewise Linear (Step/Staircase): `f(x) = ⌊x⌋` (floor function)

```
Domain: ℝ         Range: ℤ (integers)
Graph: staircase
```

**Quick sketch each function on the board.** Students should copy them into a reference sheet.

---

### Part E: Wrap-Up & Exit Ticket (8 min)

#### Summary (3 min)

> ### Key Takeaways
> - A function maps each input to **exactly one** output.
> - **Domain** = valid inputs; **Range** = actual outputs.
> - Domain restrictions come from: division by zero, negative under √, negative under log.
> - The **vertical line test** identifies functions from graphs.

#### Exit Ticket (5 min)

1. Is `y² = 4 − x²` a function? Justify.
2. Find the domain: `f(x) = √(x² − 9)`
3. Find the domain and range: `f(x) = |x − 3| + 1`
4. `f(x) = 2x + 5`. Find `f(3)`, `f(0)`, `f(a)`, `f(x+h)`.

**Answers:**
1. No — it's a circle. A vertical line hits it twice (fails vertical line test).
2. `x² − 9 ≥ 0` → `|x| ≥ 3` → Domain: `(−∞, −3] ∪ [3, ∞)`
3. `|x−3| ≥ 0` → `|x−3|+1 ≥ 1` → Domain: ℝ, Range: `[1, ∞)`
4. `f(3) = 11`, `f(0) = 5`, `f(a) = 2a+5`, `f(x+h) = 2(x+h)+5 = 2x+2h+5`

---

### Session 1 — Summary Table

| Function | Domain | Range | Graph |
|---|---|---|---|
| `f(x) = mx + b` | ℝ | ℝ | Line |
| `f(x) = ax² + bx + c` | ℝ | `[vertex, ∞)` or `(−∞, vertex]` | Parabola |
| `f(x) = √x` | `[0, ∞)` | `[0, ∞)` | Half-parabola |
| `f(x) = |x|` | ℝ | `[0, ∞)` | V-shape |
| `f(x) = 1/x` | `ℝ \ {0}` | `ℝ \ {0}` | Hyperbola |
| `f(x) = ⌊x⌋` | ℝ | ℤ | Staircase |

---

## Session 2 — Function Composition & Piecewise Functions (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Compose functions: compute `f(g(x))` and `(f∘g)(x)`.
- Decompose a composite function into its inner and outer parts.
- Determine the domain of a composite function.
- Define, evaluate, and graph piecewise functions.
- Solve problems involving piecewise-defined functions.

### Materials
- Whiteboard
- Graph paper handout
- Colored markers

---

### Part A: Hook — The Pricing Problem (8 min)

**Present this problem:**

> A store sells t-shirts. The wholesale cost of a t-shirt depends on the quantity ordered:
>
> `cost per shirt = 20 − 0.01q` (where `q` is the quantity, in dollars)
>
> You order `q` shirts. The **total cost** is:
>
> `C(q) = q × (cost per shirt) = q(20 − 0.01q) = 20q − 0.01q²`
>
> You then sell each shirt for `$25`. Your **revenue** is:
>
> `R(q) = 25q`
>
> Your **profit** is:
>
> `P(q) = R(q) − C(q) = 25q − (20q − 0.01q²) = 5q + 0.01q²`

**Ask:** *How did we build the profit function?*

We took the output of `R(q)` and `C(q)` and combined them. This is the idea of **function composition** — the output of one function becomes the input of another.

---

### Part B: Function Composition (20 min)

#### The Definition (5 min)

> ### Function Composition
> If `f` and `g` are functions, the **composition** `f ∘ g` is defined as:
>
> ```
> (f ∘ g)(x) = f(g(x))
> ```
>
> **"Apply g first, then apply f to the result."**
>
> Think of it as an **assembly line**: `x` → `g` → `g(x)` → `f` → `f(g(x))`

**Order matters!** In general, `f(g(x)) ≠ g(f(x))`.

#### Activity 5: Compute Compositions (8 min — individual)

Let `f(x) = x² + 1` and `g(x) = 2x − 3`. Find:

1. `(f ∘ g)(x) = f(g(x)) = f(2x−3) = (2x−3)² + 1 = 4x²−12x+9+1 = 4x²−12x+10`
2. `(g ∘ f)(x) = g(f(x)) = g(x²+1) = 2(x²+1)−3 = 2x²+2−3 = 2x²−1`
3. `(f ∘ g)(1) = f(g(1)) = f(−1) = 1+1 = 2`
4. `(g ∘ f)(1) = g(f(1)) = g(2) = 4−3 = 1`
5. `(f ∘ f)(x) = f(f(x)) = f(x²+1) = (x²+1)²+1 = x⁴+2x²+2`
6. `(g ∘ g)(x) = g(g(x)) = g(2x−3) = 2(2x−3)−3 = 4x−9`

**Key observation:** Problems 1 and 2 give different answers → **composition is not commutative**.

#### Activity 6: Decomposition (4 min)

> "Given `h(x) = (3x − 7)²`, express `h` as a composition `f(g(x))`."

Guide students to identify the **inner** and **outer** operations:
- Inner: `g(x) = 3x − 7` (what's inside the square)
- Outer: `f(x) = x²` (the squaring operation)

So `h(x) = f(g(x))` where `f(x) = x²` and `g(x) = 3x − 7`.

**More decomposition practice:**

7. `h(x) = √(x² + 1)` → `g(x) = x²+1`, `f(x) = √x`
8. `h(x) = |2x + 5|` → `g(x) = 2x+5`, `f(x) = |x|`
9. `h(x) = 1/(x³ − 8)` → `g(x) = x³−8`, `f(x) = 1/x`
10. `h(x) = (x + 1)⁴` → `g(x) = x+1`, `f(x) = x⁴`

#### Domain of Compositions (3 min)

> ### Domain of `f ∘ g`
> The domain of `(f∘g)(x) = f(g(x))` consists of all `x` such that:
> 1. `x` is in the domain of `g` (so `g(x)` is defined), AND
> 2. `g(x)` is in the domain of `f` (so `f(g(x))` is defined).

**Example:** `f(x) = √x`, `g(x) = x − 5`.

`f(g(x)) = √(x−5)`. Domain: `x−5 ≥ 0` → `x ≥ 5` → `[5, ∞)`.

**Example:** `f(x) = 1/x`, `g(x) = x² − 4`.

`f(g(x)) = 1/(x²−4)`. Domain: `x²−4 ≠ 0` → `x ≠ ±2` → `ℝ \ {−2, 2}`.

---

### Part C: Piecewise Functions (17 min)

#### The Idea (3 min)

> A **piecewise function** is defined by **different rules for different parts of the domain**.
>
> Think of it like a menu: the price depends on what you order.

**Example on the board:**

```
         ⎧  x + 2,   if x < 0
f(x) =   ⎨
         ⎩  x²,      if x ≥ 0
```

**Evaluate:**
- `f(−3) = −3 + 2 = −1` (use first piece since `−3 < 0`)
- `f(0) = 0² = 0` (use second piece since `0 ≥ 0`)
- `f(3) = 3² = 9` (use second piece since `3 ≥ 0`)

#### Activity 7: Evaluate Piecewise Functions (4 min)

```
         ⎧  2x − 1,   if x ≤ 1
g(x) =   ⎨
         ⎩  3 − x,    if x > 1
```

1. `g(0) = 2(0)−1 = −1`
2. `g(1) = 2(1)−1 = 1` *(at the boundary, use `≤`)*
3. `g(2) = 3−2 = 1`
4. `g(−1) = 2(−1)−1 = −3`

#### Graphing Piecewise Functions (6 min)

**Graph on the board together:**

```
         ⎧  x + 2,   if x < 1
f(x) =   ⎨  2,       if x = 1
         ⎩  x²,      if x > 1
```

Steps:
1. Graph `y = x+2` for `x < 1` → a line segment, open circle at `x = 1`
2. Plot the point `(1, 2)` → a single dot
3. Graph `y = x²` for `x > 1` → a curve starting with open circle at `x = 1`

**Key vocabulary:**
- **Open circle** (○): the point is NOT included
- **Closed/filled circle** (●): the point IS included

#### Activity 8: Graph These (4 min — pairs, on graph paper)

1. ```
        ⎧  −x,    if x ≤ 0
   f(x)=⎨
        ⎩   x,    if x > 0
   ```
   → This is `f(x) = |x|`! *(Disguised as a piecewise function.)*

2. ```
        ⎧  3,    if x < 2
   g(x)=⎨  1,    if x = 2
        ⎩  x−1,  if x > 2
   ```

3. ```
        ⎧  x²,     if x < 0
   h(x)=⎨  0,      if 0 ≤ x ≤ 2
        ⎩  x − 2,  if x > 2
   ```

---

### Part D: Applications (10 min)

#### The Tax Bracket Problem (5 min)

> Income tax (simplified):
>
> ```
>          ⎧  0,           if income ≤ 0
> tax(x) = ⎨  0.10x,       if 0 < x ≤ 10000
>          ⎩  1000 + 0.20(x − 10000),   if x > 10000
> ```
>
> (a) How much tax on income of $5,000? → `0.10(5000) = $500`
> (b) How much tax on income of $15,000? → `1000 + 0.20(5000) = $2000`
> (c) How much tax on income of $10,000? → `0.10(10000) = $1000`
> (d) Is the function continuous at `x = 10000`?

**Check continuity at `x = 10000`:**
- Left: `0.10(10000) = 1000`
- Right: `1000 + 0.20(0) = 1000`
- They match → **continuous** ✓

#### The Postage Problem (3 min)

> ```
>              ⎧  1.50,   if 0 < w ≤ 100
> postage(w) = ⎨  2.50,   if 100 < w ≤ 500
>              ⎩  4.00,   if w > 500
> ```
> (where `w` is weight in grams)

This is a **step function**. It has jump discontinuities at `w = 100` and `w = 500`.

---

### Part E: Wrap-Up & Exit Ticket (5 min)

#### Exit Ticket

Let `f(x) = x + 3`, `g(x) = x²`.

1. Find `(f ∘ g)(x)`
2. Find `(g ∘ f)(x)`
3. Find the domain of `f(g(x))`
4. Evaluate:
   ```
          ⎧  x²,   if x < 1
   h(x) = ⎨
          ⎩  2x,   if x ≥ 1
   ```
   Find `h(−2)`, `h(1)`, `h(3)`.

**Answers:**
1. `f(g(x)) = f(x²) = x² + 3`
2. `g(f(x)) = g(x+3) = (x+3)² = x² + 6x + 9`
3. Both `f` and `g` have domain ℝ, so domain of `f∘g` is **ℝ**
4. `h(−2) = (−2)² = 4`; `h(1) = 2(1) = 2`; `h(3) = 2(3) = 6`

---

### Session 2 — Summary Table

| Concept | Formula/Rule | Example |
|---|---|---|
| Composition | `(f∘g)(x) = f(g(x))` | `f(x)=x², g(x)=x+1 → f(g(x))=(x+1)²` |
| Order matters | `f(g(x)) ≠ g(f(x))` in general | `(x+1)² ≠ x²+1` |
| Decomposition | Identify inner & outer | `√(3x+1) = f(g(x))` where `g=3x+1, f=√x` |
| Domain of `f∘g` | `x ∈ dom(g)` AND `g(x) ∈ dom(f)` | `f=√x, g=x−5 → dom: [5,∞)` |
| Piecewise | Different rules for different `x` | Tax brackets, postage rates |

---

## Session 3 — Function Transformations & Graphing (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Apply translations (shifts) to function graphs: `f(x ± h)`, `f(x) ± k`.
- Apply reflections: `f(−x)`, `−f(x)`.
- Apply stretches and compressions: `af(x)`, `f(bx)`.
- Combine multiple transformations in the correct order.
- Sketch transformed graphs of common functions.

### Materials
- Whiteboard
- Graph paper
- Colored markers (different colors for each transformation)
- Desmos or graphing calculator (optional but highly recommended)

---

### Part A: Hook — The Twin Parabolas (6 min)

**Draw `y = x²` on the board.** Then ask:

> *Can you draw a parabola with the same shape, but shifted 3 units to the right?*

Students may suggest `y = x² + 3` (wrong — that shifts UP). Draw it to show it goes up.

The correct answer is `y = (x − 3)²`.

**Now ask:**

> *Can you shift it 3 units right AND 2 units up?*

Answer: `y = (x − 3)² + 2`.

**The mystery:** Why does `(x − 3)` shift right, when `−3` usually means "left"?

This is the central puzzle of the session. By the end, students will understand why.

---

### Part B: Translations (Shifts) (15 min)

#### Activity 9: Discover the Rules (8 min — with Desmos or graph paper)

Using `f(x) = x²` as the base, graph each and describe the transformation:

| Function | What happened? |
|---|---|
| `g(x) = f(x) + 3 = x² + 3` | Shifted **up** 3 |
| `h(x) = f(x) − 4 = x² − 4` | Shifted **down** 4 |
| `k(x) = f(x − 2) = (x − 2)²` | Shifted **right** 2 |
| `m(x) = f(x + 5) = (x + 5)²` | Shifted **left** 5 |

**Write the rules on the board:**

> ### Translation Rules
> | Transformation | Effect | Form |
> |---|---|---|
> | `f(x) + k` | Vertical shift **up** by `k` (if `k > 0`) | Outside the function |
> | `f(x) − k` | Vertical shift **down** by `k` | Outside the function |
> | `f(x − h)` | Horizontal shift **right** by `h` | Inside the function |
> | `f(x + h)` | Horizontal shift **left** by `h` | Inside the function |

**Explaining the "backward" horizontal shift (4 min):**

Why does `f(x − 2)` shift right? Think of it this way:

> `f(x − 2)` asks: *"What value of the old input gives the current output?"*
>
> If I want `f(0)` (the original y-intercept), I need `x − 2 = 0`, so `x = 2`.
> The y-intercept that was at `x = 0` has moved to `x = 2` → shifted right.

**Alternative explanation (substitution):** Let `g(x) = f(x − 2)`. To get the same output as `f(0)`, I need `g(2) = f(0)`. So the point that was at `x = 0` is now at `x = 2`.

#### Activity 10: Quick Practice (3 min)

If `f(x) = √x`, describe the graph of:

1. `f(x) + 4 = √x + 4` → Shift up 4
2. `f(x − 1) = √(x − 1)` → Shift right 1
3. `f(x + 3) − 2 = √(x + 3) − 2` → Shift left 3 and down 2

---

### Part C: Reflections (10 min)

#### Activity 11: Discover Reflections (5 min)

| Function | What happened? |
|---|---|
| `g(x) = −f(x) = −x²` | Reflected over the **x-axis** (flipped upside down) |
| `h(x) = f(−x) = (−x)² = x²` | Reflected over the **y-axis** (no visible change for `x²`!) |
| `k(x) = −f(−x) = −(−x)² = −x²` | Both reflections = point reflection through origin |

**Try with `f(x) = x³`:**
- `f(−x) = (−x)³ = −x³` → reflected over y-axis
- `−f(−x) = −(−x³) = x³` → back to original (odd function!)

**Write the rules:**

> ### Reflection Rules
> | Transformation | Effect |
> |---|---|
> | `−f(x)` | Reflect over the **x-axis** (flip vertically) |
> | `f(−x)` | Reflect over the **y-axis** (flip horizontally) |
> | `−f(−x)` | Reflect through the **origin** (both) |

**Key terminology:**
- **Even function:** `f(−x) = f(x)` → symmetric about y-axis (e.g., `x²`, `|x|`)
- **Odd function:** `f(−x) = −f(x)` → symmetric about origin (e.g., `x³`, `1/x`)

#### Activity 12: Even or Odd? (3 min)

1. `f(x) = x²` → `f(−x) = x² = f(x)` → **Even**
2. `f(x) = x³` → `f(−x) = −x³ = −f(x)` → **Odd**
3. `f(x) = x² + x` → `f(−x) = x² − x ≠ f(x)` and `≠ −f(x)` → **Neither**
4. `f(x) = |x|` → `f(−x) = |x| = f(x)` → **Even**
5. `f(x) = 1/x` → `f(−x) = −1/x = −f(x)` → **Odd**

---

### Part D: Stretches & Compressions (10 min)

#### Activity 13: Discover Stretches (5 min)

Using `f(x) = x²`:

| Function | What happened? |
|---|---|
| `g(x) = 3f(x) = 3x²` | Stretched **vertically** by factor 3 (taller, narrower-looking) |
| `h(x) = (1/2)f(x) = x²/2` | Compressed **vertically** by factor 1/2 (shorter, wider-looking) |
| `k(x) = f(2x) = (2x)² = 4x²` | Compressed **horizontally** by factor 2 |
| `m(x) = f(x/3) = (x/3)²` | Stretched **horizontally** by factor 3 |

**Write the rules:**

> ### Stretch/Compression Rules
> | Transformation | Effect |
> |---|---|
> | `a·f(x)` where `a > 1` | Vertical **stretch** by factor `a` |
> | `a·f(x)` where `0 < a < 1` | Vertical **compression** by factor `a` |
> | `f(b·x)` where `b > 1` | Horizontal **compression** by factor `b` (squeezes inward) |
> | `f(b·x)` where `0 < b < 1` | Horizontal **stretch** by factor `1/b` (spreads out) |

**The "backward" horizontal rule explained:**
- `f(2x)` reaches the same output in half the input distance → compressed.
- `f(x/2)` takes twice the input distance to reach the same output → stretched.

#### Activity 14: Quick Practice (3 min)

Describe the transformation from `f(x) = √x` to:

1. `2√x` → Vertical stretch by 2
2. `√(3x)` → Horizontal compression by 3
3. `−√x` → Reflect over x-axis
4. `√(−x)` → Reflect over y-axis

---

### Part E: Combining Transformations (14 min)

#### The Order of Operations (5 min)

**Present the general form:**

> ```
> g(x) = a · f(b(x − h)) + k
> ```
>
> This applies, in order:
> 1. **Horizontal shift** by `h` (right if `h > 0`)
> 2. **Horizontal stretch/compression** by `1/b`
> 3. **Vertical stretch/compression** by `a`
> 4. **Vertical shift** by `k`
> 5. (If `a < 0`: reflect over x-axis; if `b < 0`: reflect over y-axis)

**Recommended order for graphing:**
1. Start with the base graph of `f(x)`
2. Apply horizontal transformations (shift, then stretch/compress, then reflect)
3. Apply vertical transformations (stretch/compress, then reflect, then shift)

**Or more simply:** Work from the **inside out** — do what's inside the function first, then what's outside.

#### Activity 15: Describe and Sketch (6 min)

The base function is `f(x) = x²`. Describe the transformations and sketch:

1. `g(x) = 2(x − 3)² + 1`
   - Shift right 3
   - Vertical stretch by 2
   - Shift up 1
   - Vertex: `(3, 1)`, opens up, narrower

2. `h(x) = −(x + 4)² − 2`
   - Shift left 4
   - Reflect over x-axis (opens down)
   - Shift down 2
   - Vertex: `(−4, −2)`, opens down

3. `k(x) = (1/2)(x − 1)² + 3`
   - Shift right 1
   - Vertical compression by 1/2
   - Shift up 3
   - Vertex: `(1, 3)`, opens up, wider

4. `m(x) = −2|x + 3| − 4`
   - Base: `|x|`
   - Shift left 3
   - Vertical stretch by 2
   - Reflect over x-axis (opens down)
   - Shift down 4
   - Vertex: `(−3, −4)`

5. `p(x) = √(−(x − 2)) + 1`
   - Base: `√x`
   - Shift right 2
   - Reflect over y-axis (domain changes!)
   - Shift up 1
   - Starts at `(2, 1)`, goes left
   - Domain: `x ≤ 2`

#### Activity 16: Reverse Engineering (3 min)

> The graph of `y = x²` was transformed to produce a parabola with vertex at `(−2, 5)` that opens downward and is twice as "steep." Find the equation.

**Answer:** `g(x) = −2(x + 2)² + 5`

---

### Part F: Exit Ticket (5 min)

The base function is `f(x) = |x|`.

1. Describe: `g(x) = 3|x − 2| − 4`
2. Describe: `h(x) = −|x + 5| + 1`
3. Find the equation: shift `f` left 1, reflect over x-axis, stretch vertically by 3, shift up 2.

**Answers:**
1. Shift right 2, vertical stretch by 3, shift down 4. Vertex: `(2, −4)`.
2. Shift left 5, reflect over x-axis, shift up 1. Vertex: `(−5, 1)`.
3. `g(x) = −3|x + 1| + 2`

---

## Weekly Challenge Problem Set: Functions, Graphs & Transformations

### A. Function Identification & Notation

1. Is each of the following a function? Justify.
   (a) `y = 3x − 7`
   (b) `x² + y² = 25`
   (c) `y = x³`
   (d) `|y| = x`
   (e) `y = √(9 − x²)` (principal root only)
   (f) `x = |y|`

2. For `f(x) = 2x² − 3x + 1`, find:
   (a) `f(0)`
   (b) `f(−1)`
   (c) `f(1/2)`
   (d) `f(a)`
   (e) `f(x + h)`
   (f) `[f(x+h) − f(x)] / h`

3. For `f(x) = √(x + 4)`, find:
   (a) `f(0)`
   (b) `f(5)`
   (c) `f(−4)`
   (d) `f(a² − 4)`

4. If `f(x) = x² + 2x`, find all `x` such that `f(x) = 3`.

5. If `g(x) = |x − 3|`, find all `x` such that `g(x) = 5`.

### B. Domain & Range

Find the domain and range of each function.

6. `f(x) = 4x − 7`
7. `f(x) = x² − 6x + 5`
8. `f(x) = √(2x − 5)`
9. `f(x) = √(9 − x²)`
10. `f(x) = 1/(x + 3)`
11. `f(x) = 1/√(x − 2)`
12. `f(x) = |2x + 1| − 3`
13. `f(x) = (x² − 4)/(x − 2)`
14. `f(x) = √(x² − 7x + 12)`
15. `f(x) = x/(x² + 1)`
16. `f(x) = 1/(x² − 4x + 3)`
17. `f(x) = √(x + 2) + √(5 − x)`
18. `f(x) = |x|/x`
19. `f(x) = x² + 1/x`
20. `f(x) = √(16 − x²)/√(x² − 1)`

### C. Function Composition

Let `f(x) = x + 2`, `g(x) = x²`, `h(x) = 1/x`, `k(x) = √x`.

21. Find `(f ∘ g)(x)`
22. Find `(g ∘ f)(x)`
23. Find `(f ∘ h)(x)`
24. Find `(h ∘ f)(x)`
25. Find `(g ∘ k)(x)`
26. Find `(k ∘ g)(x)`
27. Find `(f ∘ f ∘ f)(x)`
28. Find `(h ∘ g ∘ k)(x)`
29. Find `(g ∘ g)(x)` and simplify
30. Find `(k ∘ h ∘ g)(x)` and state the domain

Decompose each as a composition of two simpler functions.

31. `H(x) = (3x − 1)⁴`
32. `H(x) = √(x² + 7)`
33. `H(x) = 1/(x³ + 2)`
34. `H(x) = |5x + 1|`
35. `H(x) = (x + 1)² − 3`
36. `H(x) = √(|x| − 2)`
37. `H(x) = 2/(√(x + 1))`
38. `H(x) = (1/(x − 3))²`

### D. Piecewise Functions

39. Evaluate `f(x)` at `x = −2, 0, 1, 3, 5`:
    ```
            ⎧  x + 3,   if x < 0
    f(x) =  ⎨  x²,      if 0 ≤ x ≤ 2
            ⎩  5 − x,   if x > 2
    ```

40. Evaluate `g(x)` at `x = −3, −1, 1, 2`:
    ```
            ⎧  |x|,     if x ≤ −1
    g(x) =  ⎨  x + 1,   if −1 < x < 2
            ⎩  x² − 1,  if x ≥ 2
    ```

41. Graph:
    ```
            ⎧  −2,    if x < −1
    f(x) =  ⎨  x,     if −1 ≤ x ≤ 1
            ⎩  2,     if x > 1
    ```

42. Graph:
    ```
            ⎧  x²,     if x < 0
    g(x) =  ⎨  2,      if 0 ≤ x < 3
            ⎩  x − 1,  if x ≥ 3
    ```

43. Write a piecewise function for the following: "A parking garage charges $5 for the first hour or part thereof, and $3 for each additional hour or part thereof, up to a maximum of $20."

44. Write a piecewise function for: `f(x) = |2x − 3|` (without using absolute value).

45. Find the domain and range of:
    ```
            ⎧  x + 1,   if x < 0
    h(x) =  ⎨  0,       if 0 ≤ x ≤ 3
            ⎩  x − 3,   if x > 3
    ```

46. Is the function in problem 41 continuous? Check at `x = −1` and `x = 1`.

47. Graph: `f(x) = ⌊x⌋` (the floor function) for `−3 ≤ x ≤ 3`. Find its domain and range.

48. Write a piecewise function for the sign function: `sgn(x) = −1` if `x < 0`, `0` if `x = 0`, `1` if `x > 0`.

### E. Transformations

For each, describe the transformation(s) from the base function and sketch.

49. `f(x) = x²` → `g(x) = (x − 3)² + 4`
50. `f(x) = x²` → `g(x) = −2(x + 1)² − 3`
51. `f(x) = √x` → `g(x) = √(x + 2) − 1`
52. `f(x) = √x` → `g(x) = −√(x − 3)`
53. `f(x) = |x|` → `g(x) = 3|x − 1| + 2`
54. `f(x) = |x|` → `g(x) = −(1/2)|x + 4|`
55. `f(x) = 1/x` → `g(x) = 1/(x − 2) + 1`
56. `f(x) = x³` → `g(x) = (x − 1)³ + 2`
57. `f(x) = x²` → `g(x) = (2x)²`
58. `f(x) = x²` → `g(x) = f(x/3)`

Find the equation of the transformed function.

59. `f(x) = x²`: shifted left 4, shifted up 3.
60. `f(x) = x²`: shifted right 2, reflected over x-axis, shifted down 5.
61. `f(x) = |x|`: shifted left 1, vertical stretch by 3, shifted up 4.
62. `f(x) = √x`: shifted right 2, reflected over x-axis.
63. `f(x) = √x`: reflected over y-axis, shifted up 3.
64. `f(x) = 1/x`: shifted right 3, shifted up 2.
65. `f(x) = x²`: horizontal compression by 2, vertical stretch by 3, shifted right 1.

Determine if each function is even, odd, or neither.

66. `f(x) = x⁴`
67. `f(x) = x⁵`
68. `f(x) = x² + x`
69. `f(x) = x³ − x`
70. `f(x) = |x| + x²`
71. `f(x) = 1/(x² + 1)`
72. `f(x) = x³ + 1`
73. `f(x) = x|x|`
74. `f(x) = x² + |x|`

### F. Mixed & Applied Problems

75. If `f(x) = 2x − 1` and `g(x) = x + 4`, find `x` such that `f(g(x)) = g(f(x))`.

76. If `f(x) = x²` and `g(x) = x + 3`, find all `x` such that `(f ∘ g)(x) = (g ∘ f)(x)`.

77. A ball is thrown upward. Its height (in meters) after `t` seconds is `h(t) = −5t² + 20t + 1`.
    (a) Find the domain and range of `h` (in the physical context).
    (b) When does the ball reach maximum height? What is the maximum height?
    (c) When does the ball hit the ground?

78. The cost of a taxi ride is: $3 flag fall plus $2 per km for the first 10 km, then $1.50 per km after that.
    (a) Write a piecewise function for the cost `C(d)` where `d` is distance in km.
    (b) Find `C(5)`, `C(10)`, `C(15)`.
    (c) Is `C` continuous at `d = 10`?

79. Let `f(x) = √(x − 2)` and `g(x) = x² − 4`.
    (a) Find `(f ∘ g)(x)` and its domain.
    (b) Find `(g ∘ f)(x)` and its domain.

80. The temperature in degrees Celsius, `C(h)`, at height `h` (in km) above ground is approximately:
    ```
             ⎧  20 − 7h,     if 0 ≤ h ≤ 12
    C(h) =   ⎨  −64,          if 12 < h ≤ 20
             ⎩  −64 + 3(h−20), if h > 20
    ```
    (a) Find `C(0)`, `C(10)`, `C(15)`, `C(25)`.
    (b) Is `C` continuous at `h = 12`? At `h = 20`?

### G. Challenge Problems

81. Find all functions `f` such that `f(f(x)) = x` for all `x` (involutions). Give at least 3 examples.

82. If `f(x + 1) = x² − 3x + 2`, find `f(x)`.

83. If `f(x) = 2x + 3` and `f(g(x)) = 4x² + 12x + 9`, find `g(x)`.

84. If `f(2x − 1) = 4x² + 8x`, find `f(x)`.

85. Let `f(x) = x² + x + 1`. Find `f(f(1))`, `f(f(2))`, `f(f(3))`. Do you notice a pattern?

86. Find the domain and range of `f(x) = 1/(x² − 3x + 2)`.

87. Find the domain and range of `f(x) = √(−x² + 4x + 5)`.

88. If `f(x) = (ax + b)/(cx + d)` and `f(f(x)) = x` for all `x` (where defined), find a relationship among `a, b, c, d`.

89. Given `f(x) = |x − 2| + |x + 3|`, find:
    (a) `f(0)`
    (b) `f(−5)`
    (c) `f(10)`
    (d) The minimum value of `f(x)` and where it occurs.
    (e) The range of `f`.

90. The function `f` satisfies `f(x) + f(1/x) = x` for all `x ≠ 0`. Find `f(x)`.

91. Given `f(x) = x² − 4x + 3`:
    (a) Write `f(x)` in vertex form `a(x − h)² + k`.
    (b) Describe the transformations from `y = x²`.
    (c) Find the domain and range.
    (d) Find the intervals where `f` is increasing and decreasing.

92. The graph of `y = f(x)` passes through `(0, 3)` and `(1, 5)`. Find points that the following must pass through:
    (a) `y = f(x − 2)`
    (b) `y = f(x) + 1`
    (c) `y = −f(x)`
    (d) `y = 2f(x) + 1`
    (e) `y = f(−x)`
    (f) `y = f(2x)`

93. A function `f` has domain `[−2, 5]` and range `[−1, 7]`. Find the domain and range of:
    (a) `g(x) = f(x − 3)`
    (b) `g(x) = f(x) + 2`
    (c) `g(x) = −f(x)`
    (d) `g(x) = f(2x)`
    (e) `g(x) = 2f(x) − 3`

94. Let `f(x) = ⌊x⌋` (floor function). Find:
    (a) `f(3.7)`
    (b) `f(−2.3)`
    (c) `f(f(f(−0.5)))`
    (d) All `x` such that `f(x) = 0`
    (e) Is `f(x)` even, odd, or neither?

95. Sketch the graph of `f(x) = x² − 2|x| − 3`. (Hint: use even symmetry or piecewise definition.)
    (a) Find all zeros of `f`.
    (b) Find the range of `f`.
    (c) Find the intervals where `f` is increasing.

96. Given `f(x) = |x|` and `g(x) = x²`:
    (a) Show that `f(g(x)) = g(f(x))` for all `x`.
    (b) Are there any other pairs of "standard" functions that commute under composition?

97. The function `f(x) = x²` is transformed to `g(x) = a(x − h)² + k`. If `g` has vertex at `(3, −2)` and passes through `(5, 6)`, find `a`, `h`, `k`.

98. Let `f(x) = x² + bx + c`. If `f(1) = 4` and `f(2) = 7`, find `b` and `c`.

99. A piecewise function is defined as:
    ```
             ⎧  ax + b,    if x ≤ 1
    f(x) =   ⎨
             ⎩  cx² + d,   if x > 1
    ```
    Given that `f` is continuous at `x = 1` and `f(0) = 2`, `f(2) = 5`, `f'(1) = 0` (the left and right derivatives match):
    (a) Find `a`, `b`, `c`, `d`.
    (b) Find `f(−1)` and `f(3)`.

100. The function `f(x) = (x − 1)(x − 3)(x − 5)` is a cubic.
     (a) Find the domain and range.
     (b) Describe the transformations needed to obtain `g(x) = 2f(x + 1) − 3`.
     (c) Find the zeros of `g`.

---

## Answer Key: Weekly Challenge Set

### A. Function Identification & Notation

| # | Answer |
|---|---|
| 1 | (a) Yes (b) No (circle, fails VLT) (c) Yes (d) No (one x can give two y) (e) Yes (upper semicircle) (f) No |
| 2 | (a) 1 (b) 6 (c) 1/2 (d) `2a²−3a+1` (e) `2x²+4xh+2h²−3x−3h+1` (f) `4x+2h−3` |
| 3 | (a) 2 (b) 3 (c) 0 (d) `|a|` (since `√(a²−4+4) = √(a²) = |a|`) |
| 4 | `x²+2x = 3 → x²+2x−3 = 0 → (x+3)(x−1) = 0 → x = −3, 1` |
| 5 | `|x−3| = 5 → x−3 = ±5 → x = 8, −2` |

### B. Domain & Range

| # | Domain | Range |
|---|---|---|
| 6 | ℝ | ℝ |
| 7 | ℝ | `[−4, ∞)` (vertex at `x=3`: `9−18+5 = −4`) |
| 8 | `[5/2, ∞)` | `[0, ∞)` |
| 9 | `[−3, 3]` | `[0, 3]` |
| 10 | `ℝ \ {−3}` | `ℝ \ {0}` |
| 11 | `(2, ∞)` | `(0, ∞)` |
| 12 | ℝ | `[−3, ∞)` |
| 13 | `ℝ \ {2}` (simplifies to `x+2` for `x≠2`) | `ℝ \ {4}` |
| 14 | `(−∞, 3] ∪ [4, ∞)` | `[0, ∞)` |
| 15 | ℝ | `[−1/2, 1/2]` *(max at `x=1`: `1/2`; min at `x=−1`: `−1/2`)* |
| 16 | `ℝ \ {1, 3}` | `(−∞, −1] ∪ (0, ∞)` *(denominator `(x−1)(x−3)` has min `−1` at `x=2`)* |
| 17 | `[−2, 5]` | `[√7, √14]` *(max at `x=3/2` by symmetry of the two radicals)* |
| 18 | `ℝ \ {0}` | `{−1, 1}` |
| 19 | `ℝ \ {0}` | `(−∞, ∞)`... as `x→0+`: `→∞`; as `x→0−`: `→−∞`; as `x→±∞`: `→∞`. Min exists somewhere. `f'(x) = 2x − 1/x² = 0 → x³ = 1/2 → x = 2^{−1/3}`. `f(2^{−1/3}) = 2^{−2/3} + 2^{1/3}`. Range: `[2^{−2/3}+2^{1/3}, ∞)`... but for `x < 0`: `f(x) = x² + 1/x → x² → ∞` and `1/x → −∞`. Is there a max for `x < 0`? `f'(x) = 2x − 1/x²`. For `x < 0`: `2x < 0` and `−1/x² < 0`, so `f'(x) < 0` always → `f` is decreasing on `(−∞, 0)`. So `f → ∞` as `x → −∞` and `f → −∞` as `x → 0−`. Range for `x < 0`: `(−∞, ∞)`. Combined: **Range: ℝ** |
| 20 | Need `16−x² ≥ 0` (so `|x| ≤ 4`) and `x²−1 > 0` (so `|x| > 1`). Domain: `[−4,−1)∪(1,4]`. Range: `f = √(16−x²)/√(x²−1)`. At `x=1+`: `→√15/0+ = ∞`. At `x=4`: `0/√15 = 0`. Min at some point. Range: `[0, ∞)`... but is 0 achieved? `x=4` gives `0/√15 = 0`. So range: `[0, ∞)` |

### C. Function Composition

| # | Answer |
|---|---|
| 21 | `(f∘g)(x) = f(x²) = x² + 2` |
| 22 | `(g∘f)(x) = g(x+2) = (x+2)² = x² + 4x + 4` |
| 23 | `(f∘h)(x) = f(1/x) = 1/x + 2` |
| 24 | `(h∘f)(x) = h(x+2) = 1/(x+2)` |
| 25 | `(g∘k)(x) = g(√x) = x` (for `x ≥ 0`) |
| 26 | `(k∘g)(x) = k(x²) = |x|` (i.e., `√(x²) = |x|`) |
| 27 | `f(f(f(x))) = f(f(x+2)) = f(x+4) = x+6` |
| 28 | `(h∘g∘k)(x) = h(g(√x)) = h(x) = 1/x` (for `x > 0`) |
| 29 | `(g∘g)(x) = g(x²) = x⁴` |
| 30 | `(k∘h∘g)(x) = k(h(x²)) = k(1/x²) = √(1/x²) = 1/|x|` (for `x ≠ 0`). Domain: `ℝ \ {0}` |

### C. Decomposition

| # | Inner `g(x)` | Outer `f(x)` |
|---|---|---|
| 31 | `g = 3x−1` | `f = x⁴` |
| 32 | `g = x²+7` | `f = √x` |
| 33 | `g = x³+2` | `f = 1/x` |
| 34 | `g = 5x+1` | `f = |x|` |
| 35 | `g = x+1` | `f = x²−3` |
| 36 | `g = |x|−2` | `f = √x` |
| 37 | `g = x+1` | `f = 2/√x` |
| 38 | `g = 1/(x−3)` | `f = x²` |

### D. Piecewise Functions

| # | Answer |
|---|---|
| 39 | `f(−2) = −2+3 = 1`; `f(0) = 0`; `f(1) = 1`; `f(3) = 5−3 = 2`; `f(5) = 5−5 = 0` |
| 40 | `g(−3) = |−3| = 3`; `g(−1) = |−1| = 1`; `g(1) = 1+1 = 2`; `g(2) = 4−1 = 3` |
| 41 | Graph: horizontal line `y=−2` for `x<−1` (open at `x=−1`); line `y=x` from `(−1,−1)` to `(1,1)` (closed both ends); horizontal line `y=2` for `x>1` (open at `x=1`). |
| 42 | Graph: parabola `y=x²` for `x<0` (open at `x=0`); horizontal line `y=2` from `[0,3)` (closed at 0, open at 3); line `y=x−1` for `x≥3` (closed at 3, starts at `(3,2)`). |
| 43 | `C(h) = 5` for `0 < h ≤ 1`; `C(h) = 5 + 3⌈h−1⌉` for `h > 1`, capped at 20. Or piecewise: `C(h) = min(5 + 3⌈h−1⌉, 20)` for `h > 0`. |
| 44 | `f(x) = 2x−3` if `x ≥ 3/2`; `f(x) = 3−2x` if `x < 3/2` |
| 45 | Domain: ℝ. Range: For `x < 0`: `x+1 ∈ (−∞, 1)`. For `0 ≤ x ≤ 3`: `0`. For `x > 3`: `x−3 ∈ (0, ∞)`. The first piece covers `(−∞, 1)`, the third covers `(0, ∞)` which includes `1` (e.g., `f(4) = 1`). Union: **Range: ℝ** |
| 46 | At `x=−1`: left limit `= −2`, right value `= f(−1) = −1`. Not continuous. At `x=1`: left value `= f(1) = 1`, right limit `= 2`. Not continuous. **Not continuous at either point.** |
| 47 | Staircase graph. Domain: ℝ. Range: ℤ (integers). |
| 48 | `sgn(x) = −1` if `x < 0`; `0` if `x = 0`; `1` if `x > 0` |

### E. Transformations

| # | Description |
|---|---|
| 49 | Right 3, up 4. Vertex: `(3, 4)` |
| 50 | Left 1, reflect over x-axis, vertical stretch 2, down 3. Vertex: `(−1, −3)` |
| 51 | Left 2, down 1. Starts at `(−2, −1)` |
| 52 | Right 3, reflect over x-axis. Starts at `(3, 0)`, goes down |
| 53 | Right 1, vertical stretch 3, up 2. Vertex: `(1, 2)` |
| 54 | Left 4, reflect over x-axis, vertical compression 1/2. Vertex: `(−4, 0)` |
| 55 | Right 2, up 1. Asymptotes: `x=2`, `y=1` |
| 56 | Right 1, up 2. Inflection at `(1, 2)` |
| 57 | Horizontal compression by 2. `g(x) = 4x²` |
| 58 | Horizontal stretch by 3. `g(x) = x²/9` |
| 59 | `g(x) = (x+4)² + 3` |
| 60 | `g(x) = −(x−2)² − 5` |
| 61 | `g(x) = 3|x+1| + 4` |
| 62 | `g(x) = −√(x−2)` |
| 63 | `g(x) = √(−x) + 3` |
| 64 | `g(x) = 1/(x−3) + 2` |
| 65 | `g(x) = 3(2(x−1))² = 12(x−1)²` |
| 66 | Even (`(−x)⁴ = x⁴`) |
| 67 | Odd (`(−x)⁵ = −x⁵`) |
| 68 | Neither (`(−x)²+(−x) = x²−x ≠ x²+x`) |
| 69 | Odd (`(−x)³−(−x) = −x³+x = −(x³−x)`) |
| 70 | Even (`|−x|+(−x)² = |x|+x²`) |
| 71 | Even (`1/((−x)²+1) = 1/(x²+1)`) |
| 72 | Neither (`(−x)³+1 = −x³+1 ≠ x³+1` and `≠ −(x³+1)`) |
| 73 | Odd (`(−x)|−x| = −x|x| = −(x|x|)`) |
| 74 | Even (`(−x)²+|−x| = x²+|x|`) |

### F. Mixed & Applied Problems

| # | Answer |
|---|---|
| 75 | `f(g(x)) = 2(x+4)−1 = 2x+7`. `g(f(x)) = (2x−1)+4 = 2x+3`. `2x+7 = 2x+3` → `7 = 3` → **No solution.** |
| 76 | `(f∘g)(x) = (x+3)² = x²+6x+9`. `(g∘f)(x) = x²+3`. `x²+6x+9 = x²+3 → 6x = −6 → x = −1` |
| 77 | (a) Domain: `t ≥ 0` until ball hits ground. `h = 0` when `−5t²+20t+1 = 0 → t = (20+√420)/10 ≈ 4.05s`. Domain: `[0, 4.05]`. Range: `[1, 21]` (max at `t=2: h=−20+40+1=21`). (b) `t=2s`, max height `21m`. (c) `t ≈ 4.05s` |
| 78 | (a) `C(d) = 3+2d` for `0 ≤ d ≤ 10`; `C(d) = 23+1.5(d−10)` for `d > 10`. (b) `C(5) = 13`, `C(10) = 23`, `C(15) = 30.5`. (c) Left: `23`. Right: `23+0 = 23`. **Continuous ✓** |
| 79 | (a) `f(g(x)) = √(x²−4−2) = √(x²−6)`. Domain: `x²−6 ≥ 0` → `|x| ≥ √6`. (b) `g(f(x)) = (√(x−2))²−4 = x−2−4 = x−6`. Domain: `x ≥ 2` (from `f`). |
| 80 | (a) `C(0) = 20`, `C(10) = 20−70 = −50`, `C(15) = −64`, `C(25) = −64+15 = −49`. (b) At `h=12`: left `= 20−84 = −64`, right `= −64`. **Continuous ✓**. At `h=20`: left `= −64`, right `= −64+0 = −64`. **Continuous ✓** |

### G. Challenge Problems

| # | Answer |
|---|---|
| 81 | Examples: `f(x) = x` (trivial), `f(x) = −x`, `f(x) = 1/x` (for `x ≠ 0`), `f(x) = a−x` for any constant `a`. These are called **involutions**. |
| 82 | Let `u = x+1`, so `x = u−1`. `f(u) = (u−1)²−3(u−1)+2 = u²−2u+1−3u+3+2 = u²−5u+6`. So `f(x) = x²−5x+6` |
| 83 | `f(g(x)) = 2g(x)+3 = 4x²+12x+9 → g(x) = (4x²+12x+9−3)/2 = (4x²+12x+6)/2 = 2x²+6x+3` |
| 84 | Let `u = 2x−1`, so `x = (u+1)/2`. `f(u) = 4((u+1)/2)²+8((u+1)/2) = (u+1)²+4(u+1) = u²+2u+1+4u+4 = u²+6u+5`. So `f(x) = x²+6x+5` |
| 85 | `f(1) = 3`, `f(f(1)) = f(3) = 13`. `f(2) = 7`, `f(f(2)) = f(7) = 57`. `f(3) = 13`, `f(f(3)) = f(13) = 183`. The pattern: `f(f(n))` grows very rapidly since `f` is quadratic — iterating a quadratic produces fast-growing sequences (related to dynamical systems). |
| 86 | `1/((x−1)(x−2))`. Domain: `ℝ \ {1, 2}`. Denominator min at `x=3/2`: `(1/2)(−1/2) = −1/4`. So denominator ∈ `[−1/4, 0) ∪ (0, ∞)`. Reciprocal: `(−∞, −4] ∪ (0, ∞)`. **Range: `(−∞, −4] ∪ (0, ∞)`** |
| 87 | `−x²+4x+5 ≥ 0 → x²−4x−5 ≤ 0 → (x−5)(x+1) ≤ 0 → x ∈ [−1, 5]`. Max of `−x²+4x+5` at `x=2`: `−4+8+5 = 9`. Range: `[0, 3]` (since `√9 = 3`). **Domain: `[−1, 5]`, Range: `[0, 3]`** |
| 88 | `f(x) = (ax+b)/(cx+d)`. Computing `f(f(x))` and setting it equal to `x` yields the conditions: `c(a+d) = 0`, `a² = d²` (i.e., `a = ±d`), and `b(a+d) = 0`. **Simplest sufficient condition: `a = −d`** (then all three conditions are satisfied for any `b, c`). Examples: `f(x) = 1/x` (`a=0, b=1, c=1, d=0`, so `a = −d = 0`), `f(x) = (x+1)/(x−1)` (`a=1, b=1, c=1, d=−1`, so `a = −d`). |
| 89 | (a) `f(0) = 2+3 = 5`. (b) `f(−5) = 7+2 = 9`. (c) `f(10) = 8+13 = 21`. (d) Min value: **5**, for all `x ∈ [−3, 2]` (between the critical points, `f(x) = 5`). (e) Range: `[5, ∞)` |
| 90 | `f(x) + f(1/x) = x` ... (1). Replace `x` with `1/x`: `f(1/x) + f(x) = 1/x` ... (2). From (1) and (2): `x = 1/x` → only works if `x² = 1`. This seems contradictory. Actually (1) and (2) give: `x = 1/x` which is not true for all `x`. So we need: from (1): `f(x) = x − f(1/x)`. From (2): `f(1/x) = 1/x − f(x)`. Sub (2) into (1): `f(x) = x − (1/x − f(x)) = x − 1/x + f(x)` → `0 = x − 1/x` → contradiction. **No such function exists** that satisfies `f(x) + f(1/x) = x` for ALL `x ≠ 0`. *(The system is inconsistent.)* |
| 91 | (a) `f(x) = (x−2)² − 1`. (b) Right 2, down 1. (c) Domain: ℝ, Range: `[−1, ∞)`. (d) Decreasing on `(−∞, 2)`, increasing on `(2, ∞)` |
| 92 | (a) `(2, 3)` and `(3, 5)` (b) `(0, 4)` and `(1, 6)` (c) `(0, −3)` and `(1, −5)` (d) `(0, 7)` and `(1, 11)` (e) `(0, 3)` and `(−1, 5)` (f) `(0, 3)` and `(1/2, 5)` |
| 93 | (a) Domain: `[1, 8]`, Range: `[−1, 7]` (b) Domain: `[−2, 5]`, Range: `[1, 9]` (c) Domain: `[−2, 5]`, Range: `[−7, 1]` (d) Domain: `[−1, 5/2]`, Range: `[−1, 7]` (e) Domain: `[−2, 5]`, Range: `[−5, 11]` |
| 94 | (a) 3 (b) −3 (c) `f(−0.5) = −1`, `f(−1) = −1`, `f(−1) = −1`. **Answer: −1** (d) `x ∈ [0, 1)` (e) Neither (not symmetric) |
| 95 | `f(x) = x²−2|x|−3`. Piecewise: `x²−2x−3 = (x−3)(x+1)` for `x ≥ 0`; `x²+2x−3 = (x+3)(x−1)` for `x < 0`. (a) For `x ≥ 0`: `(x−3)(x+1) = 0 → x = 3`. For `x < 0`: `(x+3)(x−1) = 0 → x = −3`. **Zeros: `x = ±3`** (b) Vertex of right piece at `x=1`: `−4`; vertex of left piece at `x=−1`: `−4`. **Range: `[−4, ∞)`** (c) For `x < 0`: decreasing on `(−∞, −1)`, increasing on `(−1, 0)`. For `x ≥ 0`: decreasing on `(0, 1)`, increasing on `(1, ∞)`. **Increasing on `(−1, 0) ∪ (1, ∞)`** |
| 96 | (a) `f(g(x)) = |x²| = x²`. `g(f(x)) = |x|² = x²`. ✓ (b) Yes: e.g., `f(x) = x³` and `g(x) = ∛x` (cube root): `f(g(x)) = (∛x)³ = x`, `g(f(x)) = ∛(x³) = x`. They commute. Also `f(x) = x+1, g(x) = x−1`: `f(g(x)) = x`, `g(f(x)) = x`. |
| 97 | `h = 3, k = −2`. `g(5) = a(5−3)²−2 = 4a−2 = 6 → a = 2`. **`a = 2, h = 3, k = −2`** |
| 98 | `f(1) = 1+b+c = 4 → b+c = 3`. `f(2) = 4+2b+c = 7 → 2b+c = 3`. Subtract: `b = 0, c = 3`. **`b = 0, c = 3`** |
| 99 | Continuity at `x=1`: `a(1)+b = c(1)²+d → a+b = c+d`. `f(0) = 2 → b = 2`. `f(2) = 5 → 4c+d = 5`. Derivative match: left derivative at `x=1` is `a`; right derivative is `2c`. So `a = 2c`. Four equations: `b = 2`, `a = 2c`, `a+b = c+d`, `4c+d = 5`. From `a = 2c` and `a+b = c+d`: `2c+2 = c+d → d = c+2`. From `4c+d = 5`: `4c+c+2 = 5 → 5c = 3 → c = 3/5`. `d = 3/5+2 = 13/5`. `a = 6/5`. `b = 2`. **`a = 6/5, b = 2, c = 3/5, d = 13/5`**. `f(−1) = (6/5)(−1)+2 = 4/5`. `f(3) = (3/5)(9)+13/5 = 27/5+13/5 = 40/5 = 8` |
| 100 | (a) Domain: ℝ. Range: ℝ (odd-degree polynomial). (b) `g(x) = 2f(x+1)−3 = 2((x+1−1)(x+1−3)(x+1−5))−3 = 2x(x−2)(x−4)−3`. Left 1, vertical stretch 2, down 3. (c) Zeros of `g`: solve `2x(x−2)(x−4) = 3`. Numerically: `x ≈ 0.22, 1.61, 4.17` (three real roots). |

---

## Quick Reference: Function Transformation Decision Guide

| Transformation | Form | Effect on graph |
|---|---|---|
| Vertical shift | `f(x) + k` | Up by `k` (if `k > 0`) |
| Horizontal shift | `f(x − h)` | Right by `h` (if `h > 0`) |
| Vertical stretch | `a·f(x)`, `a > 1` | Taller/narrower |
| Vertical compression | `a·f(x)`, `0 < a < 1` | Shorter/wider |
| Horizontal compression | `f(bx)`, `b > 1` | Squeezed inward |
| Horizontal stretch | `f(bx)`, `0 < b < 1` | Spread outward |
| Reflect over x-axis | `−f(x)` | Flipped upside down |
| Reflect over y-axis | `f(−x)` | Flipped left-right |
| Combined form | `a·f(b(x−h)) + k` | Apply inside-out: shift → scale → reflect → shift |

| Function type | Domain check | Range check |
|---|---|---|
| Polynomial | Always ℝ | Even degree: `[min, ∞)` or `(−∞, max]`; Odd: ℝ |
| `1/f(x)` | `f(x) ≠ 0` | Typically `ℝ \ {0}` |
| `√(f(x))` | `f(x) ≥ 0` | `[0, ∞)` |
| `|f(x)|` | Same as `f` | `[0, ∞)` if range of `f` crosses 0 |
| Composition `f(g(x))` | `x ∈ dom(g)` AND `g(x) ∈ dom(f)` | Depends on range of `g` ∩ domain of `f` |
