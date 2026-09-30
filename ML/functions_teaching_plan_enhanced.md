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

#### 7. Ceiling Function: `f(x) = ⌈x⌉`

```
Domain: ℝ         Range: ℤ (integers)
Graph: staircase (steps go up-left, closed on left, open on right)
```
- `⌈x⌉` = the smallest integer `≥ x`
- `⌈3.2⌉ = 4`, `⌈−1.5⌉ = −1`, `⌈5⌉ = 5`
- Relationship: `⌈x⌉ = −⌊−x⌋`

#### 8. Fractional Part Function: `f(x) = {x} = x − ⌊x⌋`

```
Domain: ℝ         Range: [0, 1)
Graph: sawtooth — ramps from 0 to 1, then jumps back to 0
```
- `{3.7} = 0.7`, `{−2.3} = 0.7`, `{5} = 0`
- Always satisfies `0 ≤ {x} < 1`
- Identity: `x = ⌊x⌋ + {x}`

#### 9. Sign Function: `f(x) = sgn(x)`

```
          ⎧  1,   if x > 0
sgn(x) =  ⎨  0,   if x = 0
          ⎩  −1,  if x < 0

Domain: ℝ         Range: {−1, 0, 1}
```
- Useful identity: `|x| = x · sgn(x)`

#### 10. Cubic Function: `f(x) = x³`

```
Domain: ℝ         Range: ℝ
Graph: S-shaped curve through origin, increasing everywhere
```
- Odd function: `(−x)³ = −x³`
- Key difference from `x²`: cubic takes both positive and negative values, always increasing

#### 11. Cube Root Function: `f(x) = ∛x`

```
Domain: ℝ         Range: ℝ
Graph: S-shaped curve through origin, increasing everywhere
```
- Inverse of `x³` (we'll study inverse functions later)
- Unlike `√x`, the cube root is defined for **all** real numbers: `∛(−8) = −2`

#### 12. General Power Function: `f(x) = xⁿ` (n a positive integer)

```
Domain: ℝ         Range: depends on n
```
| `n` | Example | Range | Symmetry |
|---|---|---|---|
| even | `x², x⁴, x⁶` | `[0, ∞)` | Even |
| odd | `x³, x⁵, x⁷` | ℝ | Odd |

- `x⁴` is "flatter" near 0 and "steeper" away from 0 compared to `x²`
- `x⁵` grows much faster than `x³`

#### 13. Rational Function: `f(x) = P(x) / Q(x)` where `P, Q` are polynomials

```
Domain: ℝ \ {zeros of Q}
```
- `f(x) = 1/x` is the simplest example (already covered)
- `f(x) = (x²−1)/(x−1)` simplifies to `x+1` for `x ≠ 1` — but the domain excludes `x = 1`
- Vertical asymptotes at zeros of `Q` (that don't cancel)
- Horizontal asymptote determined by degrees of `P` and `Q`

#### 14. General Polynomial Function: `f(x) = aₙxⁿ + aₙ₋₁xⁿ⁻¹ + ... + a₁x + a₀`

```
Domain: ℝ
Range: depends on degree and leading coefficient
```
| Degree | Name | Example | Range |
|---|---|---|---|
| 0 | Constant | `f(x) = 5` | `{5}` |
| 1 | Linear | `f(x) = 2x+1` | ℝ |
| 2 | Quadratic | `f(x) = x²−3` | `[−3, ∞)` |
| 3 | Cubic | `f(x) = x³−x` | ℝ |
| 4 | Quartic | `f(x) = x⁴−2x²` | `[−1, ∞)` |

**Key rule:** Odd-degree polynomials have range ℝ. Even-degree polynomials have range `[min, ∞)` or `(−∞, max]`.

#### 15. Max and Min Functions: `f(x) = max(g(x), h(x))`, `f(x) = min(g(x), h(x))`

```
max(a, b) = (a + b + |a − b|) / 2
min(a, b) = (a + b − |a − b|) / 2
```
- `f(x) = max(x, 0)` is the **ReLU function** — important in machine learning
- `f(x) = max(x, 2x−1)` — find where the two pieces cross

#### 16. Distance Function: `f(x) = |x − a|`

```
Domain: ℝ         Range: [0, ∞)
```
- `|x − a|` = distance from `x` to `a` on the number line
- `f(x) = |x − 2| + |x + 3|` = sum of distances to 2 and −3
- Minimized when `x` is between −3 and 2 (value = 5)

#### 17. Indicator (Characteristic) Function: `f(x) = 𝟙_A(x)`

```
          ⎧  1,   if x ∈ A
𝟙_A(x) =  ⎨
          ⎩  0,   if x ∉ A
```
- Connects to **set algebra**: `𝟙_{A∪B} = max(𝟙_A, 𝟙_B)`, `𝟙_{A∩B} = 𝟙_A · 𝟙_B`, `𝟙_{Aᶜ} = 1 − 𝟙_A`
- The **Dirichlet function** `𝟙_ℚ(x)` (1 if `x` is rational, 0 otherwise) is a famous example — it's discontinuous everywhere

#### 18. Gaussian Error Function (preview): `f(x) = e^(−x²)`

```
Domain: ℝ         Range: (0, 1]
Graph: bell curve, max at x = 0
```
- This is the "bell curve" shape — students will see it in statistics and machine learning
- Even function, always positive, approaches 0 as `x → ±∞`

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
| `f(x) = ⌈x⌉` | ℝ | ℤ | Staircase (reversed) |
| `f(x) = {x}` | ℝ | `[0, 1)` | Sawtooth |
| `f(x) = sgn(x)` | ℝ | `{−1, 0, 1}` | Step at 0 |
| `f(x) = x³` | ℝ | ℝ | S-curve |
| `f(x) = ∛x` | ℝ | ℝ | S-curve |
| `f(x) = xⁿ` (n even) | ℝ | `[0, ∞)` | U-shape |
| `f(x) = xⁿ` (n odd) | ℝ | ℝ | S-shape |
| `f(x) = P(x)/Q(x)` | `ℝ \ {zeros of Q}` | varies | Rational |
| `f(x) = e^(−x²)` | ℝ | `(0, 1]` | Bell curve |
| `f(x) = max(g, h)` | varies | varies | Upper envelope |

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

## Session 4 — Inverse Functions, Function Algebra & Monotonicity (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Determine whether a function is one-to-one (injective) using the horizontal line test.
- Find the inverse of a function algebraically and graphically.
- Perform arithmetic on functions: `(f+g)(x)`, `(f−g)(x)`, `(f·g)(x)`, `(f/g)(x)`.
- Determine where a function is increasing, decreasing, or constant.
- Identify monotonic functions and understand their connection to invertibility.

### Materials
- Whiteboard / projector
- Graph paper handout
- Colored markers

---

### Part A: Hook — The Code and the Key (8 min)

**Present this scenario:**

> A spy encodes a message using the rule: replace each letter with the letter 3 positions ahead (A→D, B→E, ..., X→A, Y→B, Z→C). This is a function `E: letter → letter`.
>
> To **decode**, the recipient needs a function `D` that **undoes** `E`.
>
> **Question:** What is the decoding rule? How is it related to `E`?

Students will figure out: shift 3 positions back. So `D` is the **inverse** of `E`.

**Write the key idea:**

> An **inverse function** `f⁻¹` undoes what `f` does.
> - If `f(3) = 10`, then `f⁻¹(10) = 3`.
> - If `f: x → y`, then `f⁻¹: y → x`.

**But not every function has an inverse!** (This is the central mystery of the session.)

---

### Part B: One-to-One Functions & The Horizontal Line Test (12 min)

#### The Problem (5 min)

> Does `f(x) = x²` have an inverse?

Ask students to try: If `f(2) = 4`, what should `f⁻¹(4)` be? It should be 2. But `f(−2) = 4` too! So `f⁻¹(4)` should also be `−2`.

**A function can only give ONE output for each input.** So `f⁻¹(4)` can't be both 2 and −2. **`f(x) = x²` does not have an inverse on all of ℝ.**

**But if we restrict the domain to `[0, ∞)`:** then only `f(2) = 4`, and `f⁻¹(4) = 2` works. The restricted function `f: [0, ∞) → [0, ∞)` with `f(x) = x²` **does** have an inverse: `f⁻¹(x) = √x`.

#### Definition: One-to-One (Injective) (3 min)

> ### One-to-One Function
> A function `f` is **one-to-one** (injective) if **different inputs give different outputs**:
>
> `f(a) = f(b)` implies `a = b`.
>
> Equivalently: if `a ≠ b`, then `f(a) ≠ f(b)`.

**A function has an inverse if and only if it is one-to-one.**

#### The Horizontal Line Test (4 min)

> ### Horizontal Line Test
> A function is one-to-one if and only if **no horizontal line** intersects its graph more than once.
>
> - `f(x) = x²` → fails (horizontal line at `y = 4` hits twice) → no inverse
> - `f(x) = x³` → passes (always increasing, no horizontal line hits twice) → has inverse
> - `f(x) = 2x + 1` → passes → has inverse

#### Activity 17: One-to-One or Not? (4 min — pairs)

1. `f(x) = 3x − 7` → **Yes** (linear with nonzero slope)
2. `f(x) = x⁴` → **No** (fails on all of ℝ; even power)
3. `f(x) = |x|` → **No** (`|2| = |−2| = 2`)
4. `f(x) = √x` → **Yes** (always increasing)
5. `f(x) = 1/x` → **Yes** (always decreasing on each branch)
6. `f(x) = x³ − x` → **No** (goes up, then down, then up — a horizontal line can hit 3 times)

---

### Part C: Finding Inverses Algebraically (15 min)

#### The Protocol (5 min)

> ### How to Find `f⁻¹(x)`
> 1. Verify `f` is one-to-one (or restrict the domain).
> 2. Write `y = f(x)`.
> 3. **Swap** `x` and `y` (solve for the old input in terms of the old output).
> 4. Solve for `y`.
> 5. Replace `y` with `f⁻¹(x)`.

**Worked example:** `f(x) = 2x + 5`

```
y = 2x + 5
x = 2y + 5      (swap x and y)
x − 5 = 2y
y = (x − 5) / 2
f⁻¹(x) = (x − 5) / 2
```

**Check:** `f⁻¹(f(3)) = f⁻¹(11) = (11−5)/2 = 3` ✓

**Worked example:** `f(x) = x³ + 1`

```
y = x³ + 1
x = y³ + 1
y³ = x − 1
y = ∛(x − 1)
f⁻¹(x) = ∛(x − 1)
```

#### The Graph of `f⁻¹` (3 min)

> ### Graphical Relationship
> The graph of `y = f⁻¹(x)` is the **reflection of `y = f(x)`** over the line `y = x`.

Sketch on the board: `f(x) = x²` (restricted to `[0,∞)`) and `f⁻¹(x) = √x`, showing the reflection over `y = x`.

#### Activity 18: Find the Inverse (7 min — individual)

1. `f(x) = 3x − 2` → `f⁻¹(x) = (x+2)/3`
2. `f(x) = (x − 4)/5` → `f⁻¹(x) = 5x + 4`
3. `f(x) = x³` → `f⁻¹(x) = ∛x`
4. `f(x) = 1/x` → `f⁻¹(x) = 1/x` (self-inverse!)
5. `f(x) = √(x − 1)` → `f⁻¹(x) = x² + 1` (domain of `f⁻¹`: `[0, ∞)`)
6. `f(x) = (2x + 3)/(x − 1)` → `f⁻¹(x) = (x + 3)/(x − 2)`
7. `f(x) = 5 − x` → `f⁻¹(x) = 5 − x` (self-inverse!)
8. `f(x) = −x + 7` → `f⁻¹(x) = 7 − x` (self-inverse!)

**Note on problems 4, 7, 8:** These functions are their own inverses — called **involutions**. Geometrically, they are symmetric about the line `y = x`.

---

### Part D: Function Arithmetic & Monotonicity (15 min)

#### Function Arithmetic (5 min)

Given `f(x)` and `g(x)`:

| Operation | Definition |
|---|---|
| `(f + g)(x)` | `f(x) + g(x)` |
| `(f − g)(x)` | `f(x) − g(x)` |
| `(f · g)(x)` | `f(x) · g(x)` |
| `(f / g)(x)` | `f(x) / g(x)`, `g(x) ≠ 0` |

**Domain:** The domain of `f + g`, `f − g`, `f · g` is the **intersection** of the domains of `f` and `g`. For `f / g`, also exclude where `g(x) = 0`.

**Example:** `f(x) = √x`, `g(x) = x − 3`
- `(f + g)(x) = √x + x − 3`, domain: `[0, ∞) ∩ ℝ = [0, ∞)`
- `(f / g)(x) = √x / (x − 3)`, domain: `[0, 3) ∪ (3, ∞)` (must have `x ≥ 0` AND `x ≠ 3`)

#### Monotonicity — Increasing and Decreasing (10 min)

> ### Definitions
> A function `f` is **increasing** on an interval `I` if:
> `a < b` in `I` implies `f(a) < f(b)`.
>
> A function `f` is **decreasing** on an interval `I` if:
> `a < b` in `I` implies `f(a) > f(b)`.
>
> A function is **monotonic** if it is entirely increasing or entirely decreasing on its domain.

**Visual rule:** As you move left to right:
- Increasing: graph goes **up** →
- Decreasing: graph goes **down** ↓

**Key connection:** A monotonic function is always one-to-one (and therefore invertible).

#### Activity 19: Determine Monotonicity (5 min)

1. `f(x) = 3x + 1` → Increasing on ℝ (positive slope)
2. `f(x) = −2x + 5` → Decreasing on ℝ
3. `f(x) = x²` → Decreasing on `(−∞, 0]`, increasing on `[0, ∞)`
4. `f(x) = x³` → Increasing on ℝ (monotonic → invertible!)
5. `f(x) = |x|` → Decreasing on `(−∞, 0]`, increasing on `[0, ∞)`
6. `f(x) = 1/x` → Decreasing on `(−∞, 0)` and on `(0, ∞)` (but NOT on all of `ℝ \ {0}` — the function jumps from −∞ to +∞ at 0)
7. `f(x) = ⌊x⌋` → Non-decreasing (constant on each interval `[n, n+1)`, then jumps up)

**Teaching note on problem 6:** This is a subtle and important point. `1/x` is decreasing on each piece separately, but if you take `a = −1 < b = 1`, then `f(a) = −1 < f(b) = 1`, so the function is NOT decreasing on the whole domain. This shows why we must specify the interval.

---

### Part E: Wrap-Up & Exit Ticket (10 min)

#### Summary (3 min)

> ### Key Takeaways
> - A function has an inverse **iff** it is one-to-one.
> - The **horizontal line test** checks one-to-one-ness.
> - `f⁻¹` undoes `f`: `f⁻¹(f(x)) = x` and `f(f⁻¹(x)) = x`.
> - The graph of `f⁻¹` is the reflection of `f` over `y = x`.
> - Monotonic functions are always invertible.

#### Exit Ticket (7 min)

1. Is `f(x) = x⁴ + x²` one-to-one? Justify.
2. Find `f⁻¹(x)` if `f(x) = (3x − 1) / 2`.
3. `f(x) = √x` and `g(x) = x² + 1`. Find `(f ∘ g)(x)` and its domain.
4. On what interval(s) is `f(x) = −x² + 6x − 5` increasing?
5. Show that `f(x) = (x + 1)/(x − 1)` is its own inverse.

**Answers:**
1. No — `f(1) = f(−1) = 2`. Fails horizontal line test.
2. `y = (3x−1)/2 → x = (3y−1)/2 → 2x = 3y − 1 → y = (2x+1)/3`. `f⁻¹(x) = (2x+1)/3`.
3. `(f∘g)(x) = √(x²+1)`. Domain: ℝ (since `x²+1 > 0` always).
4. Vertex at `x = −6/(2·(−1)) = 3`. Opens down. Increasing on `(−∞, 3)`.
5. `f(f(x)) = f((x+1)/(x−1)) = [(x+1)/(x−1) + 1] / [(x+1)/(x−1) − 1] = [(x+1+x−1)/(x−1)] / [(x+1−x+1)/(x−1)] = [2x/(x−1)] / [2/(x−1)] = x`. ✓

---

### Session 4 — Summary Table

| Concept | Rule | Example |
|---|---|---|
| One-to-one | `f(a)=f(b) ⟹ a=b` | `x³` is 1-1; `x²` is not |
| Horizontal line test | No horizontal line hits twice | `x³` passes; `x²` fails |
| Inverse `f⁻¹` | `f⁻¹(f(x)) = x` | `f(x)=2x → f⁻¹(x)=x/2` |
| Graph of inverse | Reflect over `y = x` | `√x` is reflection of `x²` (restricted) |
| Self-inverse (involution) | `f(f(x)) = x` | `1/x`, `−x`, `a−x` |
| Increasing/decreasing | Up/down as `x` increases | `x²` decreases then increases |
| Monotonic ⟹ invertible | Always increasing or decreasing | `x³` monotonic → has inverse |

---

## Session 5 — Functional Equations, Symmetry & Advanced Techniques (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve basic functional equations by substitution.
- Use even/odd symmetry to decompose and reconstruct functions.
- Work with functions defined by recursive or self-referential relations.
- Apply the Cauchy functional equation and understand its implications.
- Recognize and exploit functional symmetries (periodicity, symmetry about a point/line).

### Materials
- Whiteboard
- Handout with challenge problems
- Graph paper

---

### Part A: Hook — The Mystery Function (8 min)

**Present this problem:**

> A function `f` satisfies: `f(x + y) = f(x) + f(y)` for all real `x, y`.
> Also, `f(1) = 3`.
>
> What is `f(2)?` What is `f(10)?` What is `f(x)?`

Guide students:
- `f(2) = f(1+1) = f(1) + f(1) = 6`
- `f(3) = f(2+1) = f(2) + f(1) = 9`
- `f(n) = 3n` for positive integers
- `f(0) = f(0+0) = f(0) + f(0)` → `f(0) = 0`
- `f(−1)`: `0 = f(0) = f(1 + (−1)) = f(1) + f(−1)` → `f(−1) = −3`
- So `f(x) = 3x` for all integers, and (with continuity) for all reals.

This is the **Cauchy functional equation** — the starting point of functional equation theory.

---

### Part B: Solving Functional Equations by Substitution (15 min)

#### Technique 1: Strategic Substitution (8 min)

> ### Strategy
> In a functional equation, substitute specific values (`x = 0`, `y = 0`, `y = x`, `y = −x`, `y = 1`, etc.) to extract information about `f`.

**Worked example 1:** `f(x) + 2f(1/x) = 3x` (for `x ≠ 0`). Find `f(x)`.

```
Original:  f(x) + 2f(1/x) = 3x         ... (1)
Replace x with 1/x:  f(1/x) + 2f(x) = 3/x   ... (2)
```

From (1): `f(1/x) = (3x − f(x))/2`. Substitute into (2):
```
(3x − f(x))/2 + 2f(x) = 3/x
3x − f(x) + 4f(x) = 6/x
3f(x) = 6/x − 3x
f(x) = 2/x − x
```

**Check:** `f(x) + 2f(1/x) = (2/x − x) + 2(2x − 1/x) = 2/x − x + 4x − 2/x = 3x` ✓

**Worked example 2:** `f(xy) = f(x) + f(y)` for all `x, y > 0`, and `f(2) = 1`. Find `f(8)`.

```
f(4) = f(2·2) = f(2) + f(2) = 2
f(8) = f(2·4) = f(2) + f(4) = 1 + 2 = 3
```

(This is `f(x) = log₂(x)` — the logarithm! But we don't need to know that to compute `f(8)`.)

**Worked example 3:** `f(x + y) = f(x) · f(y)` for all real `x, y`, and `f(1) = 2`. Find `f(3)`.

```
f(2) = f(1) · f(1) = 4
f(3) = f(2) · f(1) = 8
```

(This is `f(x) = 2ˣ` — the exponential function!)

#### Activity 20: Solve These (7 min — pairs)

1. `f(x) + f(−x) = 2x²`. Find `f(x)` if `f` is even.
2. `f(x) − f(1/x) = x − 1/x` (for `x ≠ 0`). Find `f(x)`.
3. `f(2x) = 2f(x) + 3` and `f(0) = 1`. Find `f(1), f(2), f(4)`.
4. `f(x + y) = f(x) + f(y)` and `f(3) = 12`. Find `f(1)` and `f(10)`.

**Answers:**
1. If `f` is even, `f(x) = f(−x)`, so `2f(x) = 2x²` → `f(x) = x²`.
2. Replace `x` with `1/x`: `f(1/x) − f(x) = 1/x − x`. Add to original: `0 = 0` (useless). Instead, add the two equations: `[f(x) − f(1/x)] + [f(1/x) − f(x)] = [x − 1/x] + [1/x − x] = 0`. This gives 0 = 0. So subtract: from original `f(x) = f(1/x) + x − 1/x`. From substituted: `f(1/x) = f(x) + 1/x − x`. Sub: `f(x) = [f(x) + 1/x − x] + x − 1/x = f(x)`. Consistent but doesn't determine `f`. **The equation determines `f(x) − f(1/x)` but not `f` uniquely.** Any function with `f(x) = g(x) + (x − 1/x)/2` where `g` satisfies `g(x) = g(1/x)` works. **Simplest solution: `f(x) = (x − 1/x)/2`.**
3. `f(0) = 1`. `f(0) = 2f(0) + 3 → 1 = 2+3 = 5`? That's a contradiction! **No such function exists.** *(Check: `f(0) = 2f(0) + 3` → `−f(0) = 3` → `f(0) = −3`, contradicting `f(0) = 1`.)*
4. `f(3) = f(1) + f(2) = f(1) + f(1) + f(1) = 3f(1) = 12` → `f(1) = 4`. `f(10) = 10f(1) = 40`.

---

### Part C: Symmetry of Functions — Even, Odd, and Beyond (15 min)

#### Review and Extension (5 min)

**Every function can be decomposed into even + odd parts:**

> ### Even-Odd Decomposition
> Any function `f(x)` can be written as `f(x) = f_e(x) + f_o(x)` where:
> ```
> f_e(x) = [f(x) + f(−x)] / 2    (even part)
> f_o(x) = [f(x) − f(−x)] / 2    (odd part)
> ```

**Example:** `f(x) = x² + 3x + 1`
- `f(−x) = x² − 3x + 1`
- Even part: `(f(x) + f(−x))/2 = x² + 1`
- Odd part: `(f(x) − f(−x))/2 = 3x`
- Check: `x² + 1 + 3x = f(x)` ✓

#### Symmetry About a Vertical Line (5 min)

> A function `f` is **symmetric about `x = a`** if `f(a + h) = f(a − h)` for all `h`.
>
> This generalizes even functions: `f` symmetric about `x = 0` means `f(h) = f(−h)` — that's just "even."

**Example:** `f(x) = (x − 3)²` is symmetric about `x = 3`. Check: `f(3 + h) = h² = f(3 − h)` ✓

#### Symmetry About a Point (5 min)

> A function `f` is **symmetric about the point `(a, b)`** if `f(a + h) + f(a − h) = 2b` for all `h`.
>
> This generalizes odd functions: `f` symmetric about `(0, 0)` means `f(h) + f(−h) = 0` — that's just "odd."

**Example:** `f(x) = (x − 2)³ + 5` is symmetric about `(2, 5)`. Check: `f(2+h) + f(2−h) = h³ + 5 + (−h)³ + 5 = 10 = 2·5` ✓

#### Activity 21: Find the Symmetry (5 min)

1. `f(x) = x⁴ − 4x²` → Even (symmetric about `x = 0`)
2. `f(x) = (x − 1)² + 2` → Symmetric about `x = 1`
3. `f(x) = x³ − 3x` → Odd (symmetric about origin)
4. `f(x) = (x + 2)³ − 1` → Symmetric about `(−2, −1)`
5. `f(x) = 1/(x − 3)` → Symmetric about `(3, 0)` *(translation of odd function `1/x`)*

---

### Part D: Periodicity and Functional Properties (10 min)

#### Periodic Functions (5 min)

> A function `f` is **periodic with period `T > 0`** if `f(x + T) = f(x)` for all `x`.

**Examples:**
- `f(x) = {x} = x − ⌊x⌋` has period `T = 1`
- `f(x) = sgn(sin(x))` — square wave, period `2π`
- Constant functions are periodic with ANY period

**Key property:** If you know `f` on one period `[0, T)`, you know it everywhere.

#### Activity 22: Properties of Combined Functions (5 min)

1. If `f` is even and `g` is even, is `f ∘ g` even? → **Yes**: `f(g(−x)) = f(g(x))` since `g` is even.
2. If `f` is odd and `g` is odd, is `f ∘ g` odd? → **Yes**: `f(g(−x)) = f(−g(x)) = −f(g(x))`.
3. If `f` is even and `g` is odd, is `f ∘ g` even or odd? → **Even**: `f(g(−x)) = f(−g(x)) = f(g(x))` since `f` is even.
4. If `f` and `g` are both increasing, is `f + g` increasing? → **Yes**: `(f+g)(a) = f(a)+g(a) < f(b)+g(b) = (f+g)(b)`.
5. If `f` and `g` are both increasing, is `f ∘ g` increasing? → **Yes**: `a < b → g(a) < g(b) → f(g(a)) < f(g(b))`.

---

### Part E: Wrap-Up & Exit Ticket (12 min)

#### Challenge Problem (5 min)

> **Problem:** A function `f: ℝ → ℝ` satisfies `f(x + y) + f(x − y) = 2f(x)f(y)` for all real `x, y`, and `f(1) = 2`. Find `f(0)` and determine `f(x)`.

**Guide students through the solution:**

Set `x = y = 0`: `f(0) + f(0) = 2f(0)²` → `2f(0) = 2f(0)²` → `f(0)(1 − f(0)) = 0` → `f(0) = 0` or `f(0) = 1`.

**Case 1: `f(0) = 0`.** Set `y = 0`: `f(x) + f(x) = 2f(x)·0 = 0` → `f(x) = 0` for all `x`. But `f(1) = 2 ≠ 0`. Contradiction.

**Case 2: `f(0) = 1`.** Set `x = 0`: `f(y) + f(−y) = 2f(0)f(y) = 2f(y)` → `f(−y) = f(y)`. So `f` is even.

Set `x = y`: `f(2x) + f(0) = 2f(x)²` → `f(2x) = 2f(x)² − 1`.

`f(2) = 2·4 − 1 = 7`. `f(3)`: set `x = 2, y = 1`: `f(3) + f(1) = 2f(2)f(1) = 2·7·2 = 28` → `f(3) = 26`.

The pattern: `f(n) = (2ⁿ + 2⁻ⁿ)/2` for integers. (This is `f(x) = cosh(x·ln 2)` — the hyperbolic cosine — but students need not know this.)

#### Exit Ticket (7 min)

1. If `f(x + 1) = f(x) + 2x + 1` and `f(0) = 3`, find `f(3)`.
2. Decompose `f(x) = x³ + x² + x + 1` into even and odd parts.
3. If `f` is odd and `f(3) = 7`, find `f(−3)`.
4. The function `f(x) = |x − 2| + |x + 2|` has a special symmetry. What is it?

**Answers:**
1. `f(1) = f(0) + 0 + 1 = 4`. `f(2) = f(1) + 2 + 1 = 7`. `f(3) = f(2) + 4 + 1 = 12`.
2. `f(−x) = −x³ + x² − x + 1`. Even part: `(f(x)+f(−x))/2 = x² + 1`. Odd part: `(f(x)−f(−x))/2 = x³ + x`.
3. `f(−3) = −f(3) = −7` (odd function).
4. Even: `f(−x) = |−x−2| + |−x+2| = |x+2| + |x−2| = f(x)`. Symmetric about `x = 0`.

---

### Session 5 — Summary Table

| Technique | When to use | Example |
|---|---|---|
| Substitution (`x=0, y=0, y=x, y=−x`) | Functional equations | `f(x)+f(1/x)=...` → substitute `1/x` |
| Even-odd decomposition | Splitting a function | `f = f_e + f_o` |
| Symmetry about `x = a` | `f(a+h) = f(a−h)` | `(x−3)²` symmetric about `x=3` |
| Symmetry about `(a, b)` | `f(a+h) + f(a−h) = 2b` | `(x−2)³+5` symm. about `(2,5)` |
| Periodicity | `f(x+T) = f(x)` | `{x}` has period 1 |
| Cauchy equation | `f(x+y) = f(x)+f(y)` | Solution: `f(x) = cx` (if continuous) |

---

## Session 6 — Introductory Olympiad Problems on Functions (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve olympiad-style functional equations using systematic substitution.
- Prove that a function has (or doesn't have) specific properties.
- Work with the Cauchy, Jensen, and exponential functional equations.
- Apply fixed-point and contraction reasoning.
- Tackle competition-level problems involving function properties.

### Materials
- Whiteboard
- Handout with olympiad problems
- Colored markers

---

### Part A: Hook — The Three Famous Equations (10 min)

**Present the "big three" functional equations** that appear throughout mathematics:

> ### 1. Cauchy's Equation (Additive)
> `f(x + y) = f(x) + f(y)` for all `x, y ∈ ℝ`
> 
> **Solution (assuming continuity):** `f(x) = cx` for some constant `c`.
> *Without continuity, there are pathological solutions (using the axiom of choice).*

> ### 2. Exponential Equation (Multiplicative)
> `f(x + y) = f(x) · f(y)` for all `x, y ∈ ℝ`
>
> **Solution (assuming continuity and `f ≠ 0`):** `f(x) = aˣ` for some `a > 0`.

> ### 3. Logarithmic Equation
> `f(xy) = f(x) + f(y)` for all `x, y > 0`
>
> **Solution (assuming continuity):** `f(x) = c·ln(x)` for some constant `c`.

**The key insight:** These three equations encode the fundamental properties of linear, exponential, and logarithmic functions — derived purely from functional relations, not from formulas.

**Quick derivation of Cauchy (sketch on board):**
- `f(0) = f(0+0) = 2f(0)` → `f(0) = 0`
- `f(−x) = −f(x)` (set `y = −x`)
- `f(nx) = nf(x)` for integers `n` (by induction)
- `f(p/q) = (p/q)f(1)` for rationals
- With continuity: `f(x) = xf(1) = cx` for all real `x`

---

### Part B: Olympiad Problem Set 1 — Direct Substitution (20 min)

Present these problems one at a time. Give students 3–4 minutes per problem before discussing.

#### Problem 1: The Linear Cauchy (5 min)

> Find all functions `f: ℝ → ℝ` satisfying `f(x + y) = f(x) + f(y)` and `f(1) = 5`.

**Solution:** By Cauchy (assuming continuity, or the problem implicitly assumes it): `f(x) = 5x`.

*Without continuity, the problem should state "find all continuous functions" or "find all functions" (the latter is much harder).*

#### Problem 2: The Double Substitution (5 min)

> Find all `f: ℝ → ℝ` such that `f(x + y) = f(x) + f(y) + xy` and `f(1) = 4`.

**Solution:**

Set `y = 0`: `f(x) = f(x) + f(0) + 0` → `f(0) = 0`.

Set `x = y = 1`: `f(2) = 2f(1) + 1 = 9`.

**Guess:** `f(x) = ax² + bx`. Check: `f(x+y) = a(x+y)² + b(x+y) = ax² + 2axy + ay² + bx + by`. And `f(x) + f(y) + xy = ax² + bx + ay² + by + xy`. Comparing: `2axy = xy` → `a = 1/2`. Then `f(1) = 1/2 + b = 4` → `b = 7/2`.

**`f(x) = x²/2 + 7x/2`**. Verify: `f(x+y) = (x+y)²/2 + 7(x+y)/2`. `f(x)+f(y)+xy = x²/2+7x/2 + y²/2+7y/2 + xy = (x²+y²+2xy)/2 + 7(x+y)/2 = (x+y)²/2 + 7(x+y)/2`. ✓

#### Problem 3: The Quadratic Functional Equation (5 min)

> Find all `f: ℝ → ℝ` such that `f(x + y) + f(x − y) = 2f(x) + 2f(y)` and `f(1) = 1, f(0) = 0`.

**Solution:**

Set `x = y = 0`: `2f(0) = 4f(0)` → `f(0) = 0` ✓.

Set `x = 0`: `f(y) + f(−y) = 2f(0) + 2f(y) = 2f(y)` → `f(−y) = f(y)`. So `f` is even.

Set `x = y`: `f(2x) + f(0) = 2f(x) + 2f(x) = 4f(x)` → `f(2x) = 4f(x)`.

Set `y = 1`: `f(x+1) + f(x−1) = 2f(x) + 2f(1) = 2f(x) + 2`.

**Guess:** `f(x) = x²`. Check: `(x+y)² + (x−y)² = 2x² + 2y²` ✓. And `f(1) = 1` ✓.

**`f(x) = x²`** is the unique continuous solution.

#### Problem 4: The Exponential Cauchy (5 min)

> Find all continuous `f: ℝ → ℝ` such that `f(x + y) = f(x) · f(y)` and `f(1) = 3`.

**Solution:**

Set `x = y = 0`: `f(0) = f(0)²` → `f(0) = 0` or `f(0) = 1`.

If `f(0) = 0`: `f(x) = f(x+0) = f(x)·f(0) = 0` for all `x`. But `f(1) = 3 ≠ 0`. Contradiction.

So `f(0) = 1`. Then `f(n) = 3ⁿ` for integers, `f(p/q) = 3^(p/q)` for rationals, and by continuity `f(x) = 3ˣ`.

**`f(x) = 3ˣ`**.

---

### Part C: Olympiad Problem Set 2 — Fixed Points & Inequalities (15 min)

#### Problem 5: Fixed Points (5 min)

> A function `f: ℝ → ℝ` satisfies `f(f(x)) = x + 1` for all `x`. Prove that `f` has no fixed point (i.e., there is no `x` with `f(x) = x`).

**Solution:** Suppose `f(a) = a` for some `a`. Then `f(f(a)) = f(a) = a`. But `f(f(a)) = a + 1`. So `a = a + 1` → `0 = 1`, contradiction. ∎

#### Problem 6: Monotonicity from Composition (5 min)

> If `f(f(x)) = x` for all `x` (i.e., `f` is an involution) and `f` is increasing, prove that `f(x) = x` for all `x`.

**Solution:** Suppose `f(a) > a` for some `a`. Since `f` is increasing, `f(f(a)) > f(a)`. But `f(f(a)) = a`. So `a > f(a) > a`, contradiction. Similarly, `f(a) < a` leads to `a < f(a) < a`, contradiction. Therefore `f(x) = x` for all `x`. ∎

**Corollary:** Every non-trivial involution (like `f(x) = 1/x` or `f(x) = −x`) must be **decreasing**.

#### Problem 7: Range from Functional Relation (5 min)

> If `f(x) = (x² + 1)/(x + 1)` for `x ≠ −1`, find the range of `f`.

**Solution:**

Let `y = (x² + 1)/(x + 1)`. Then `y(x + 1) = x² + 1` → `x² − yx + (1 − y) = 0`.

For real `x`, need discriminant `≥ 0`: `y² − 4(1 − y) ≥ 0` → `y² + 4y − 4 ≥ 0`.

Roots: `y = (−4 ± √(16+16))/2 = (−4 ± 4√2)/2 = −2 ± 2√2`.

So `y ≤ −2 − 2√2` or `y ≥ −2 + 2√2`.

**Range: `(−∞, −2−2√2] ∪ [−2+2√2, ∞)`**.

---

### Part D: Olympiad Problem Set 3 — Advanced Challenges (10 min)

#### Problem 8: The Classic (5 min)

> Find all functions `f: ℝ → ℝ` such that `f(f(x)) = −x` for all `x`.

**Solution (sketch):**

`f` must be a bijection (it's invertible: `f⁻¹(x) = −f(x)`).

`f(f(f(x))) = f(−x)`. Also `f(f(f(x))) = −f(x)`. So `f(−x) = −f(x)` — `f` is odd.

If `f` were continuous, it would be either increasing or decreasing. If increasing: `f(f(x))` is increasing, but `−x` is decreasing — contradiction. If decreasing: `f(f(x))` is increasing — again contradicts `−x` decreasing.

**No continuous solution exists.** (Discontinuous solutions exist but require the axiom of choice.)

**Teaching note:** This is a beautiful result — the equation `f(f(x)) = −x` looks simple but has no "nice" solution. It's a gateway to deeper mathematics.

#### Problem 9: Bounded Implies Constant (5 min)

> If `f: ℝ → ℝ` satisfies `f(x + y) = f(x) + f(y)` (Cauchy's equation) and `f` is bounded on some interval `[a, b]`, prove that `f(x) = cx` for some constant `c`.

**Solution (sketch):**

From Cauchy: `f(q) = qf(1)` for all rational `q`. If `f` is bounded on `[a, b]`, then for any `x` and any rational `q` close to `x`:

`|f(x) − f(q)| = |f(x − q)|` (using `f(x) = f(q) + f(x−q)`).

As `q → x`, `x − q → 0`, and `f(x−q) → 0` (bounded + Cauchy implies continuity). So `f(x) = f(q)` in the limit → `f(x) = xf(1)`. ∎

---

### Part E: Wrap-Up & Exit Ticket (5 min)

#### Exit Ticket

1. Find all continuous `f: ℝ → ℝ` with `f(x + y) = f(x) · f(y)` and `f(0) = 1`.
2. If `f(f(x)) = x + 2`, find `f(f(f(f(x))))`.
3. If `f` is an involution (`f(f(x)) = x`) and `f(3) = 7`, find `f(7)`.

**Answers:**
1. `f(x) = aˣ` for some `a > 0` (since `f(0) = 1` and `f(x+y) = f(x)f(y)`). If also `f(1)` is given, then `f(x) = f(1)ˣ`.
2. `f(f(f(f(x)))) = f(f(x+2)) = (x+2)+2 = x+4`.
3. `f(7) = f(f(3)) = 3`.

---

### Session 6 — Summary Table

| Functional Equation | Solution (continuous) | Key substitution |
|---|---|---|
| `f(x+y) = f(x)+f(y)` | `f(x) = cx` | `x=y=0`, `y=−x` |
| `f(x+y) = f(x)·f(y)` | `f(x) = aˣ` | `x=y=0`, `y=−x` |
| `f(xy) = f(x)+f(y)` | `f(x) = c·ln(x)` | `x=y=1`, `y=1/x` |
| `f(x+y)+f(x−y) = 2f(x)+2f(y)` | `f(x) = cx²` | `x=y=0`, `x=0`, `x=y` |
| `f(f(x)) = x` (involution) | Many solutions; must be decreasing if non-trivial | — |
| `f(f(x)) = x+1` | No fixed point exists | Assume `f(a)=a` |

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

## H. Inverse Functions & Monotonicity

101. Find the inverse of `f(x) = (2x − 5)/(x + 3)` and state its domain.
102. If `f(x) = x³ + 2x + 1`, is `f` one-to-one? Justify without finding the inverse.
103. Find the inverse of `f(x) = 3 − √(x + 4)` and state the domain and range of both `f` and `f⁻¹`.
104. Show that `f(x) = (x + a)/(x − 1)` is its own inverse if and only if `a = −1`.
105. If `f(x) = 2x + 3` and `g(x) = (x − 3)/2`, show that `(f ∘ g)(x) = (g ∘ f)(x) = x`.
106. A function `f` is strictly increasing on `[0, 5]` with `f(0) = 2` and `f(5) = 9`. What is the domain and range of `f⁻¹`?
107. If `f(x) = x² − 4x + 3` for `x ≥ 2`, find `f⁻¹(x)`.
108. If `f(x) = ⌊x⌋`, does `f` have an inverse? Why or why not?
109. Prove: if `f` is strictly decreasing, then `f ∘ f` is strictly increasing.
110. Let `f(x) = x + 1/x` for `x > 0`. Is `f` one-to-one? If not, restrict the domain to make it one-to-one, then find the inverse.

### I. Function Arithmetic & Domain Intersection

111. Let `f(x) = √(x − 2)` and `g(x) = √(5 − x)`. Find `(f + g)(x)`, `(f · g)(x)`, `(f/g)(x)` and their domains.
112. Let `f(x) = 1/(x − 1)` and `g(x) = 1/(x + 2)`. Find `(f + g)(x)` and simplify. What is the domain?
113. Let `f(x) = x² − 9` and `g(x) = x − 3`. Find `(f/g)(x)` and simplify. Compare the domain of `(f/g)` with the domain of the simplified expression.
114. Let `f(x) = √(x + 3)` and `g(x) = x²`. Find `(f ∘ g)(x)`, `(g ∘ f)(x)`, and their domains.
115. Let `f(x) = 1/x` and `g(x) = √x`. Find `(f ∘ g ∘ g)(x)` and state the domain.
116. Given `f(x) = x² + 1` and `g(x) = x − 3`, find `(f − g)(x)` and `((f · g))(x)`. State the domains.
117. Let `f(x) = √(4 − x²)` and `g(x) = √(x² − 1)`. Find the domain of `(f + g)(x)`.
118. If `(f + g)(x) = 3x² + 5x − 2` and `f(x) = x² + 3x + 1`, find `g(x)`.

### J. Functional Equations

119. If `f(x + 1) = x² + 2x + 3`, find `f(x)`.
120. If `f(2x + 1) = 4x² + 12x + 7`, find `f(x)`.
121. If `f(x) + 2f(1/x) = 3x` (for `x ≠ 0`), find `f(x)`.
122. If `f(x) + f(−x) = 2` and `f(x) · f(−x) = 1` for all `x`, find all possible `f`.
123. If `f(x + y) = f(x) + f(y)` for all `x, y` and `f(1) = 7`, find `f(10)`, `f(−3)`, and `f(1/2)`.
124. If `f(x + y) = f(x) · f(y)` for all `x, y` and `f(1) = 5`, find `f(3)` and `f(−1)`.
125. If `f(xy) = f(x) + f(y)` for `x, y > 0` and `f(2) = 3`, find `f(8)` and `f(1/4)`.
126. Find all functions `f: ℝ → ℝ` satisfying `f(x + y) + f(x − y) = 2f(x)` for all `x, y`, given `f(0) = 5`.
127. If `f(f(x)) = 4x + 3` and `f` is linear, find `f(x)`.
128. If `f(f(f(x))) = 8x + 21` and `f` is linear, find `f(x)`.
129. If `f(x + 2) = f(x) + 2x + 3` and `f(0) = 1`, find `f(5)`.
130. Find all continuous `f: ℝ → ℝ` such that `f(x + y) = f(x) + f(y) + 2xy` and `f(1) = 4`.

### K. Symmetry, Even/Odd & Advanced Properties

131. Decompose `f(x) = x⁴ + 3x³ − 2x² + 5x + 7` into even and odd parts.
132. If `f` is even and `g` is odd, determine whether `f ∘ g` is even, odd, or neither. Prove your answer.
133. If `f` is even and `g` is even, is `f ∘ g` even? Is `g ∘ f` even?
134. Find the axis of symmetry of `f(x) = x⁴ − 6x³ + 11x² − 6x + 1`. *(Hint: write `f(x) = g(x − a)` for some even function `g`.)*
135. The function `f(x) = (x − 3)³ + 2` is symmetric about the point `(3, 2)`. Verify this algebraically.
136. If `f` is periodic with period `T = 4` and `f(1) = 7`, find `f(−3)`, `f(5)`, `f(9)`, `f(101)`.
137. Prove: if `f` is odd and `g` is odd, then `f · g` is even.
138. Prove: if `f` is odd and `g` is even, then `f · g` is odd.
139. A function satisfies `f(2 − x) = f(2 + x)` for all `x`. What symmetry does the graph of `f` have? If `f(1) = 5` and `f(4) = 9`, find `f(3)` and `f(0)`.
140. A function satisfies `f(x) + f(2 − x) = 6` for all `x`. If `f(0) = 4`, find `f(2)`, `f(1)`, and `f(4)`. What point is `f` symmetric about?

### L. Introductory Olympiad Problems on Functions

141. Find all functions `f: ℝ → ℝ` such that `f(x + y) = f(x) + f(y) + 1` and `f(1) = 4`.
142. Find all functions `f: ℝ → ℝ` such that `f(x + y) = f(x) · f(y)` and `f(2) = 9`.
143. Find all functions `f: ℝ → ℝ` such that `f(f(x)) = x² − 2`. *(Hint: try a quadratic `f(x) = x² + c` and find `c`.)*
144. Find all functions `f: ℝ → ℝ` such that `f(f(x)) = (x + 1)²`. *(Hint: try `f(x) = (x + a)² + b`.)*
145. Find all functions `f: ℝ → ℝ` satisfying `f(x)f(y) = f(x) + f(y) + f(xy) − 2` for all `x, y`.
146. Find all functions `f: ℝ → ℝ` satisfying `f(x + y) + f(x − y) = 2f(x)cos(y)` for all `x, y`. *(Hint: try `f(x) = a·cos(bx) + c·sin(bx)` or simply `f(x) = A·cos(kx)`.)*
147. Find all continuous `f: ℝ → ℝ` satisfying `f(x)f(y) − f(xy) = x + y` for all `x, y`.
148. A function `f: ℝ → ℝ` satisfies `f(f(f(x))) = x` for all `x`. Prove that `f(f(x)) = x` or find a counterexample showing `f(f(x)) ≠ x` is possible.
149. Find all functions `f: ℝ → ℝ` satisfying `f(x + f(y)) = f(x) + y` for all `x, y`.
150. Find all functions `f: ℝ → ℝ` satisfying `f(x + f(y)) = y + f(x)` for all `x, y`.
151. If `f: ℝ → ℝ` satisfies `f(x + y) ≤ f(x) + f(y)` for all `x, y` (subadditivity) and `f(x) = mx` is a candidate, for which values of `m` is `f` subadditive?
152. Find all functions `f: ℚ → ℚ` (rationals to rationals) such that `f(x + y) = f(x) + f(y)` and `f(f(x)) = x` for all `x, y ∈ ℚ`.
153. Find all functions `f: ℝ → ℝ` such that `|f(x) − f(y)| = |x − y|` for all `x, y`. *(Isometries of the line.)*
154. Find all functions `f: ℝ → ℝ` such that `f(x + y) = f(x) + f(y)` and `f(xy) = f(x) · f(y)` for all `x, y`. *(Ring homomorphisms of ℝ.)*
155. Find all functions `f: ℝ → ℝ` satisfying `f(x² + f(y)) = f(x)² + y` for all `x, y`.

### M. Challenging Function Problems — All Tricks

156. **Domain trap:** Find the domain of `f(x) = √(x² − 4) / √(4 − x²)`. Is the domain empty?
157. **Range via discriminant:** Find the range of `f(x) = (x² + x + 1)/(x² + x + 2)`.
158. **Composition with absolute value:** Let `f(x) = |x² − 5x + 6|`. Solve `f(x) = 2`.
159. **Self-referential:** If `f(x) = x² + f(x − 1)` and `f(0) = 0`, find `f(4)`.
160. **Piecewise inverse:** Find the inverse of `f(x) = |x − 2| + 1` by first writing it as a piecewise function.
161. **Functional inequality:** If `f(x) = x² − 4x + 3`, solve `f(f(x)) ≤ 0`.
162. **Nested absolute values:** Solve `f(x) = ||x − 1| − |x + 1|| = 2`.
163. **Composition cycle:** If `f(x) = (x − 1)/(x + 1)`, compute `f(f(f(f(x))))`. What do you notice?
164. **Floor function equation:** Solve `⌊x²⌋ = 5` for `x ∈ [0, 10]`.
165. **Range with parameters:** For what values of `k` does `f(x) = (x² + k)/(x + 1)` have range `ℝ`?
166. **Transformed domain/range:** If `f` has domain `[1, 4]` and range `[2, 7]`, find the domain and range of `g(x) = f(2x − 1) + 3`.
167. **Even/odd construction:** Find a function `f` such that `f(x) + f(−x) = x²` and `f(x) − f(−x) = 2x³`.
168. **Fixed point hunt:** Find all `x` such that `f(x) = x` for `f(x) = x³ − 3x + 1`.
169. **Inverse of a piecewise function:** Find `f⁻¹(x)` if:
    ```
              ⎧  x + 1,   if x < 0
    f(x) =   ⎨
              ⎩  x²,      if x ≥ 0
    ```
170. **Max of two functions:** Let `f(x) = max(x, x²)` for `x ∈ [0, 2]`. Write `f` as a piecewise function and find its range.
171. **Functional equation with floor:** Find all `x` such that `f(x) = {x} + ⌊x⌋ = 2x`. Is this always true?
172. **Composition domain trap:** Let `f(x) = √x` and `g(x) = x² − 5`. Find `(f ∘ g)(x)` and its domain. *(Note: the domain is NOT all of ℝ just because `x²` is defined everywhere.)*
173. **Recursive function:** Define `f(0) = 1`, `f(n) = f(n − 1) + n` for `n ≥ 1`. Find a closed-form formula for `f(n)`.
174. **Two-variable functional equation:** Find all `f: ℝ → ℝ` such that `f(x + y) = f(x)² + f(y)² − 2` and `f(0) = 2`.
175. **Sign analysis on functions:** Solve `f(x) = x² − 3|x| + 2 ≤ 0`.

---

## Answer Key: Sections H–M

### H. Inverse Functions & Monotonicity

| # | Answer |
|---|---|
| 101 | `y = (2x−5)/(x+3) → x = (2y−5)/(y+3) → xy+3x = 2y−5 → y(x−2) = −5−3x → y = (−5−3x)/(x−2) = (3x+5)/(2−x)`. **`f⁻¹(x) = (3x+5)/(2−x)`**, domain: `ℝ \ {2}`. |
| 102 | `f'(x) = 3x² + 2 > 0` for all `x`. So `f` is strictly increasing on ℝ, hence one-to-one. ✓ |
| 103 | `y = 3 − √(x+4) → √(x+4) = 3−y → x+4 = (3−y)² → x = (3−y)² − 4 = y² − 6y + 5`. **`f⁻¹(x) = x² − 6x + 5`**, domain: `x ≤ 3` (range of `f`), range: `x ≥ −4` (domain of `f`). `f`: domain `[−4, ∞)`, range `(−∞, 3]`. |
| 104 | `f(f(x)) = f((x+a)/(x−1)) = ((x+a)/(x−1) + a) / ((x+a)/(x−1) − 1) = [(x+a + a(x−1))/(x−1)] / [(x+a − x+1)/(x−1)] = [x + a + ax − a] / [a + 1] = [x(1+a)] / (a+1) = x` (if `a ≠ −1`). So `f(f(x)) = x` for ALL `a ≠ −1`. Wait — let's recheck. Numerator: `x + a + ax − a = x + ax = x(1+a)`. Denominator: `a + 1`. So `f(f(x)) = x(1+a)/(1+a) = x` for `a ≠ −1`. For `a = −1`: `f(x) = (x−1)/(x−1) = 1` (constant, for `x ≠ 1`). `f(f(x)) = f(1)` which is undefined. So `f` is its own inverse for all `a ≠ −1`. **The statement should be: `f` is its own inverse for all `a ≠ −1`. For `a = −1`, `f` is not a valid function (degenerate).** |
| 105 | `f(g(x)) = 2·((x−3)/2) + 3 = x − 3 + 3 = x`. `g(f(x)) = (2x+3 − 3)/2 = 2x/2 = x`. ✓ |
| 106 | Domain of `f⁻¹`: `[2, 9]` (range of `f`). Range of `f⁻¹`: `[0, 5]` (domain of `f`). |
| 107 | `y = x² − 4x + 3 = (x−2)² − 1 → (x−2)² = y+1 → x = 2 + √(y+1)` (take `+` since `x ≥ 2`). **`f⁻¹(x) = 2 + √(x+1)`**, domain: `[−1, ∞)`. |
| 108 | No. `⌊1.5⌋ = ⌊1.7⌋ = 1`, so multiple inputs give the same output. Not one-to-one. |
| 109 | If `a < b`, then `f(a) > f(b)` (decreasing). Apply `f` again: since `f(a) > f(b)` and `f` is decreasing, `f(f(a)) < f(f(b))`. So `a < b → f(f(a)) < f(f(b))` → `f ∘ f` is increasing. ∎ |
| 110 | `f'(x) = 1 − 1/x² = 0 → x = 1` (for `x > 0`). `f` decreases on `(0, 1)`, increases on `(1, ∞)`. Min at `x = 1`: `f(1) = 2`. Not one-to-one on all `(0, ∞)`. Restrict to `[1, ∞)`: `y = x + 1/x → x² − yx + 1 = 0 → x = (y + √(y²−4))/2` (take `+` root for `x ≥ 1`). **`f⁻¹(x) = (x + √(x²−4))/2`**, domain `[2, ∞)`. |

### I. Function Arithmetic & Domain Intersection

| # | Answer |
|---|---|
| 111 | `(f+g)(x) = √(x−2) + √(5−x)`, domain `[2, 5]`. `(f·g)(x) = √((x−2)(5−x))`, domain `[2, 5]`. `(f/g)(x) = √((x−2)/(5−x))`, domain `[2, 5)` (exclude `x=5`). |
| 112 | `(f+g)(x) = 1/(x−1) + 1/(x+2) = [(x+2) + (x−1)] / [(x−1)(x+2)] = (2x+1)/[(x−1)(x+2)]`. Domain: `ℝ \ {1, −2}`. |
| 113 | `(f/g)(x) = (x²−9)/(x−3) = (x+3)(x−3)/(x−3) = x+3` for `x ≠ 3`. Domain of `(f/g)`: `ℝ \ {3}`. The simplified expression `x+3` has domain ℝ, but the original is undefined at `x = 3`. |
| 114 | `(f∘g)(x) = √(x²+3)`. Domain: `x²+3 ≥ 0` → always true → **ℝ**. `(g∘f)(x) = (√(x+3))² = x+3`. Domain: `x ≥ −3` (from `f`). Range: `[0, ∞)` (since `g∘f` maps `[−3,∞)` to `[0,∞)`). |
| 115 | `(f∘g∘g)(x) = f(g(g(x))) = f(g(x²)) = f(√(x²)) = f(|x|) = 1/|x|`. Domain: `x ≠ 0` (need `g(x) = x²` defined ✓, then `g(x²) = √(x²) = |x|` defined ✓, then `f(|x|) = 1/|x|` need `|x| ≠ 0`). **Domain: `ℝ \ {0}`.** |
| 116 | `(f−g)(x) = x² − x + 4`, domain ℝ. `(f·g)(x) = (x²+1)(x−3) = x³ − 3x² + x − 3`, domain ℝ. |
| 117 | Need `4−x² ≥ 0` (so `|x| ≤ 2`) AND `x²−1 ≥ 0` (so `|x| ≥ 1`). Domain: `[−2,−1] ∪ [1, 2]`. |
| 118 | `g(x) = (f+g)(x) − f(x) = (3x²+5x−2) − (x²+3x+1) = 2x² + 2x − 3`. |

### J. Functional Equations

| # | Answer |
|---|---|
| 119 | Let `u = x+1`, `x = u−1`. `f(u) = (u−1)² + 2(u−1) + 3 = u² − 2u + 1 + 2u − 2 + 3 = u² + 2`. **`f(x) = x² + 2`** |
| 120 | Let `u = 2x+1`, `x = (u−1)/2`. `f(u) = 4((u−1)/2)² + 12((u−1)/2) + 7 = (u−1)² + 6(u−1) + 7 = u² − 2u + 1 + 6u − 6 + 7 = u² + 4u + 2`. **`f(x) = x² + 4x + 2`** |
| 121 | From Session 5, Problem 2: `f(x) + 2f(1/x) = 3x` ... (1). Replace `x→1/x`: `f(1/x) + 2f(x) = 3/x` ... (2). From (1): `f(1/x) = (3x−f(x))/2`. Sub into (2): `(3x−f(x))/2 + 2f(x) = 3/x → 3x − f(x) + 4f(x) = 6/x → 3f(x) = 6/x − 3x`. **`f(x) = 2/x − x`** |
| 122 | Let `y = f(−x)`. Then `f(x) + y = 2` and `f(x) · y = 1`. So `f(x)` and `y` are roots of `t² − 2t + 1 = 0 → (t−1)² = 0`. So `f(x) = 1` for all `x`. **`f(x) = 1` (constant function).** |
| 123 | Cauchy: `f(x) = 7x`. `f(10) = 70`, `f(−3) = −21`, `f(1/2) = 7/2`. |
| 124 | Exponential: `f(x) = 5ˣ`. `f(3) = 125`, `f(−1) = 1/5`. |
| 125 | Logarithmic: `f(x) = 3·log₂(x)`. `f(8) = f(2·4) = f(2)+f(4) = 3+6 = 9`. `f(1/4) = f(1/2) + f(1/2) = −3 + (−3) = −6`. **`f(8) = 9, f(1/4) = −6`** |
| 126 | Set `x = 0`: `f(y) + f(−y) = 2f(0) = 10`. Set `y = 0`: `f(x) + f(x) = 2f(x)` (trivial). Set `x = 0, y = 0`: `2f(0) = 2f(0)` ✓. From `f(y) + f(−y) = 10`: `f` has the property that its even part is `5`. **General solution: `f(x) = 5 + g(x)` where `g` is any odd function** (since `f(y)+f(−y) = 10 + g(y) + g(−y) = 10 + 0 = 10` ✓). The simplest solution: **`f(x) = 5` (constant)**. |
| 127 | Let `f(x) = ax + b`. `f(f(x)) = a(ax+b)+b = a²x + ab + b = 4x + 3`. So `a² = 4` → `a = ±2`. If `a = 2`: `2b + b = 3 → b = 1`. If `a = −2`: `−2b + b = 3 → b = −3`. **`f(x) = 2x + 1` or `f(x) = −2x − 3`**. |
| 128 | Let `f(x) = ax + b`. `f(f(f(x))) = a³x + a²b + ab + b = 8x + 21`. `a³ = 8 → a = 2`. `4b + 2b + b = 21 → 7b = 21 → b = 3`. **`f(x) = 2x + 3`** |
| 129 | `f(2) = f(0) + 0 + 3 = 4`. `f(4) = f(2) + 4 + 3 = 11`. `f(6) = f(4) + 8 + 3 = 22`. `f(5)`: use `x=3`: `f(5) = f(3) + 6 + 3`. `f(3) = f(1) + 2 + 3`. `f(1) = f(−1) + 0 + 3`. Hmm, need odd values. `f(2) = f(0) + 0 + 3 = 4` ✓. `f(4) = f(2) + 4 + 3 = 11` ✓. For odd: `f(1) = f(−1) + 0 + 3`, but we need `f(−1)`. Instead, use `f(1) = f(−1) + 0 + 3` and `f(−1) = f(−3) + (−3)·(−2)... ` — this doesn't terminate nicely for odd `x`. Instead: `f(x+2) − f(x) = 2x + 3`. Sum from `x = 0, 2, 4`: `f(6) − f(0) = 3 + 7 + 11 = 21 → f(6) = 22`. For `f(5)`: `f(5) = f(3) + 9`, `f(3) = f(1) + 5`, `f(1) = f(−1) + 3`, `f(−1) = f(−3) + (−1)`. This telescopes indefinitely for odd values. Alternatively, guess `f(x) = x²/2 + ax + b`... actually, summing: `f(n) = f(0) + Σ(2k+3)` for `k = 0, 2, 4, ..., n−2` (even `n`) or `k = 1, 3, 5, ..., n−2` (odd `n`). For `n = 5`: `f(5) = f(1) + 2·3 + 3 = f(1) + 9`. `f(1) = f(−1) + 3`. Not well-determined from even values alone. But the functional equation only relates `f(x+2)` to `f(x)`, so odd and even parts are independent. With `f(0) = 1`: even values determined: `f(2) = 4, f(4) = 11, f(6) = 22`. Odd values: `f(1)` is free. **For even `n`**: `f(n) = 1 + Σ_{k=0}^{n/2−1} (4k+3) = 1 + n²/2 + n/2 = (n² + n + 2)/2`. Check: `f(2) = (4+2+2)/2 = 4` ✓. `f(4) = (16+4+2)/2 = 11` ✓. `f(6) = (36+6+2)/2 = 22` ✓. For `f(5)`: `f(5) = f(3) + 9`, `f(3) = f(1) + 5`, so `f(5) = f(1) + 14`. Without `f(1)` given, **`f(5)` is not uniquely determined.** If we assume `f` is a polynomial: `f(x) = x²/2 + x/2 + 1` works for even `x`. Check `f(5) = 25/2 + 5/2 + 1 = 15 + 1 = 16`. **Assuming polynomial: `f(5) = 16`** |
| 130 | Try `f(x) = cx² + dx`. `f(x+y) = c(x+y)² + d(x+y) = cx² + 2cxy + cy² + dx + dy`. `f(x)+f(y)+2xy = cx²+dx + cy²+dy + 2xy`. Comparing: `2c = 2 → c = 1`. `d` is free from the equation. `f(1) = 1 + d = 4 → d = 3`. **`f(x) = x² + 3x`** |

### K. Symmetry, Even/Odd & Advanced Properties

| # | Answer |
|---|---|
| 131 | `f(−x) = x⁴ − 3x³ − 2x² − 5x + 7`. Even part: `(f(x)+f(−x))/2 = x⁴ − 2x² + 7`. Odd part: `(f(x)−f(−x))/2 = 3x³ + 5x`. |
| 132 | `(f∘g)(−x) = f(g(−x)) = f(−g(x))` (g is odd) `= f(g(x))` (f is even). So `f∘g` is **even**. |
| 133 | `f(g(−x)) = f(g(x))` (g even) → `f∘g` is even ✓. `g(f(−x)) = g(f(x))` (f even) → `g∘f` is even ✓. Both are even. |
| 134 | Try `f(x) = g(x − a)` where `g` is even. Expand `f(x) = (x−a)⁴ − 6(x−a)³ + 11(x−a)² − 6(x−a) + 1`. For `g` to be even, odd powers must vanish. Coefficient of `(x−a)³` is `−6` (nonzero), so we need a shift. Alternatively: `f(x) = (x² − 3x)² − 2(x² − 3x) + 1`... Let `u = x² − 3x`. `f = u² − 2u + 1 = (u−1)²`. The axis of `x² − 3x` is `x = 3/2`. So `f` is symmetric about `x = 3/2`. Check: `f(3/2 + h) = ((3/2+h)² − 3(3/2+h) − 1)² = (h² − 9/4 − 1)² = (h² − 13/4)²`. `f(3/2 − h) = ((3/2−h)² − 3(3/2−h) − 1)² = (h² − 9/4 − 1)² = (h² − 13/4)²`. ✓ **Axis: `x = 3/2`** |
| 135 | `f(3 + h) = h³ + 2`. `f(3 − h) = (−h)³ + 2 = −h³ + 2`. Sum: `f(3+h) + f(3−h) = 4 = 2·2`. ✓ Symmetric about `(3, 2)`. |
| 136 | `f(−3) = f(−3 + 4) = f(1) = 7`. `f(5) = f(1 + 4) = f(1) = 7`. `f(9) = f(5 + 4) = f(5) = 7`. `f(101) = f(101 − 25·4) = f(1) = 7`. **All equal 7.** |
| 137 | `(f·g)(−x) = f(−x)·g(−x) = (−f(x))·(−g(x)) = f(x)·g(x) = (f·g)(x)`. Even ✓ ∎ |
| 138 | `(f·g)(−x) = f(−x)·g(−x) = (−f(x))·g(x) = −f(x)g(x) = −(f·g)(x)`. Odd ✓ ∎ |
| 139 | Symmetric about `x = 2` (vertical line). `f(2 + h) = f(2 − h)`. `f(3) = f(2 + 1) = f(2 − 1) = f(1) = 5`. `f(0) = f(2 − 2) = f(2 + 2) = f(4) = 9`. **`f(3) = 5, f(0) = 9`** |
| 140 | Set `x = 0`: `f(0) + f(2) = 6 → f(2) = 2`. Set `x = 1`: `f(1) + f(1) = 6 → f(1) = 3`. Set `x = 2`: `f(2) + f(0) = 6 → 2 + 4 = 6` ✓. Set `x = 4`: `f(4) + f(−2) = 6`. Set `x = −2`: `f(−2) + f(4) = 6` (same). Need another relation. Set `x = 3`: `f(3) + f(−1) = 6`. Not determined individually. But: the condition `f(x) + f(2−x) = 6` means `f(2−x) = 6 − f(x)`. Let `g(x) = f(x) − 3`. Then `g(x) + g(2−x) = f(x)−3 + f(2−x)−3 = 6−6 = 0`. So `g(2−x) = −g(x)`, meaning `g` is symmetric about `(2, 0)`, hence `f` is symmetric about `(2, 3)`. **`f(2) = 2, f(1) = 3, f(4) = 4` (since `f(4) = 6 − f(−2) = 6 − f(4) → 2f(4) = 6 → ` wait: `f(−2) = 6 − f(4)`. And `f(4) = 6 − f(−2)`. So `f(4) + f(−2) = 6` but we can't determine `f(4)` alone. However, if `f` is symmetric about `(2, 3)`: `f(4) = f(0) + 2·(3 − f(0))`... actually `f(2 + h) + f(2 − h) = 6`. `f(4) + f(0) = 6 → f(4) = 2`. Wait: `f(0) = 4`, so `f(4) = 6 − 4 = 2`. **`f(2) = 2, f(1) = 3, f(4) = 2`. Symmetric about `(2, 3)`** |

### L. Introductory Olympiad Problems

| # | Answer |
|---|---|
| 141 | Let `g(x) = f(x) + 1`. Then `g(x+y) = f(x+y) + 1 = f(x) + f(y) + 2 = g(x) + g(y)`. So `g` satisfies Cauchy: `g(x) = cx`. `g(1) = f(1) + 1 = 5 → c = 5`. `g(x) = 5x`, `f(x) = 5x − 1`. **`f(x) = 5x − 1`** |
| 142 | Exponential Cauchy: `f(x) = aˣ`. `f(2) = a² = 9 → a = 3`. **`f(x) = 3ˣ`** |
| 143 | Try `f(x) = x² + c`. `f(f(x)) = (x²+c)² + c = x⁴ + 2cx² + c² + c`. Need `x⁴ + 2cx² + c² + c = x² − 2`. Coefficients: `x⁴`: 1 = 0? **No — `x⁴` term doesn't appear on RHS.** So `f` can't be purely quadratic of this form. Try `f(x) = (x² − 2)`: `f(f(x)) = (x²−2)² − 2 = x⁴ − 4x² + 2 ≠ x² − 2`. Try `f(x) = −x² + c`: `f(f(x)) = −(−x²+c)² + c = −x⁴ + 2cx² − c² + c`. Also has `x⁴` term. **No polynomial solution exists.** This is a famous equation related to the Chebyshev polynomial. The actual solution involves `f(x) = 2cos(2arccos(x/2))` (Chebyshev), but over reals, a simpler answer: consider `x = 2cos(θ)`. Then `x² − 2 = 4cos²θ − 2 = 2cos(2θ)`. So `f(2cosθ) = 2cos(2θ)`, meaning `f(x) = 2cos(2·arccos(x/2))`. But `2cos(2θ) = 2(2cos²θ − 1) = x² − 2`... so `f(x) = x² − 2` IS a solution! Check: `f(f(x)) = (x²−2)² − 2 = x⁴ − 4x² + 2`. This should equal `x² − 2`. So `x⁴ − 5x² + 4 = 0 → (x²−1)(x²−4) = 0`. This is NOT true for all `x`. **So `f(x) = x² − 2` does NOT work.** The problem is harder than it looks — the equation `f(f(x)) = x² − 2` has no solution expressible as a polynomial. **The Chebyshev solution works only on `[−2, 2]`: `f(x) = 2cos(2·arccos(x/2)) = x² − 2`. But `f(f(x)) = (x²−2)² − 2 = x⁴−4x²+2 ≠ x²−2` in general.** So there is no real-valued function satisfying this for ALL `x ∈ ℝ`. **No solution exists** (over all of ℝ). |
| 144 | Try `f(x) = (x + a)² + b`. `f(f(x)) = ((x+a)² + b + a)² + b`. Need `((x+a)² + a + b)² + b = (x+1)²`. For the outer square to give `(x+1)²`, need `(x+a)² + a + b = ±(x+1)`. Case `+`: `(x+a)² + a + b = x + 1 → x² + 2ax + a² + a + b = x + 1`. This requires `x²` coefficient 0 — impossible. Case `−`: `(x+a)² + a + b = −x − 1 → x² + (2a+1)x + a² + a + b + 1 = 0`. Also needs `x²` coefficient 0. **No quadratic solution.** Try `f(x) = x + a`: `f(f(x)) = x + 2a`. Need `x + 2a = (x+1)² = x² + 2x + 1`. Impossible. Try `f(x) = x² + ax + b`: `f(f(x))` is degree 4. Need degree 2. **No polynomial solution.** Similar to 143, this likely has no solution over all ℝ. |
| 145 | Set `x = y = 0`: `f(0)² = 2f(0) + f(0) − 2 → f(0)² − 3f(0) − 2 = 0`. Hmm, let's try `f(x) = x² + 1`: `f(x)f(y) = (x²+1)(y²+1) = x²y² + x² + y² + 1`. `f(x) + f(y) + f(xy) − 2 = x²+1 + y²+1 + x²y²+1 − 2 = x²y² + x² + y² + 1`. ✓ **`f(x) = x² + 1`** Try `f(x) = 1 − x²`: `f(x)f(y) = (1−x²)(1−y²) = 1 − x² − y² + x²y²`. `f(x)+f(y)+f(xy)−2 = (1−x²)+(1−y²)+(1−x²y²)−2 = 1−x²−y²−x²y²`. These are NOT equal. Try `f(x) = x² + c`: `f(x)f(y) = (x²+c)(y²+c) = x²y² + c(x²+y²) + c²`. `f(x)+f(y)+f(xy)−2 = x²+c + y²+c + x²y²+c − 2 = x²y² + x² + y² + 3c − 2`. Comparing: `c = 1` and `c² = 3c − 2 → c² − 3c + 2 = 0 → (c−1)(c−2) = 0 → c = 1` or `c = 2`. Check `c = 1`: `c(x²+y²) = x²+y²` ✓ and `c² = 1`, `3c−2 = 1` ✓. Check `c = 2`: `c(x²+y²) = 2(x²+y²)` but we need `x²+y²`. ✗. **`f(x) = x² + 1`** is the unique solution of this form. Also check `f(x) = 2`: `f(x)f(y) = 4`, `f(x)+f(y)+f(xy)−2 = 2+2+2−2 = 4` ✓. So **`f(x) = 2`** is also a solution. |
| 146 | Try `f(x) = A·cos(kx)`. `f(x+y) + f(x−y) = A·cos(k(x+y)) + A·cos(k(x−y)) = 2A·cos(kx)·cos(ky)`. Need `2A·cos(kx)·cos(ky) = 2A·cos(kx)·cos(y)`. So `cos(ky) = cos(y)` for all `y` → `k = 1`. **`f(x) = A·cos(x)`** for any constant `A`. Also `f(x) = 0` works. |
| 147 | Set `y = 0`: `f(x)f(0) − f(0) = x`. So `(f(x) − 1)f(0) = x`. If `f(0) ≠ 0`: `f(x) = 1 + x/f(0)`. Let `c = f(0)`: `f(x) = 1 + x/c`. Check: `f(x)f(y) − f(xy) = (1+x/c)(1+y/c) − (1+xy/c) = 1 + x/c + y/c + xy/c² − 1 − xy/c = (x+y)/c + xy(1/c² − 1/c) = (x+y)/c + xy(1−c)/c²`. Need this to equal `x + y`. So `(x+y)/c = x+y → c = 1`, and `xy(1−1)/1 = 0` ✓. **`f(x) = x + 1`** (with `f(0) = 1`). If `f(0) = 0`: `0 = x` for all `x` — contradiction. **Unique solution: `f(x) = x + 1`** |
| 148 | Consider `f(x) = x + 1`. `f(f(f(x))) = x + 3 ≠ x`. Consider `f(x) = −x`. `f(f(f(x))) = f(f(−x)) = f(x) = −x ≠ x`. Consider a rotation by `2π/3` on a partition of ℝ into triples. It IS possible to have `f(f(f(x))) = x` without `f(f(x)) = x`. **Counterexample:** Partition ℝ into sets of 3: `{a, b, c}` and define `f(a) = b, f(b) = c, f(c) = a`. Then `f(f(f(a))) = a` but `f(f(a)) = c ≠ a`. So **`f(f(x)) = x` does NOT necessarily hold.** |
| 149 | Set `x = 0`: `f(f(y)) = f(0) + y`. Set `y = 0`: `f(x + f(0)) = f(x)`. So `f` is periodic with period `f(0)` — but `f(f(y)) = f(0) + y` shows `f` is a bijection (since `y → f(0)+y` is bijective). A periodic bijection must have period 0, so `f(0) = 0`. Then `f(f(y)) = y` (involution) and `f(x + f(y)) = f(x) + y`. Set `y = f(z)` (valid since `f` is bijective): `f(x + f(f(z))) = f(x) + f(z) → f(x + z) = f(x) + f(z)`. Cauchy! So `f(x) = cx` (continuous) and `f(f(x)) = x → c²x = x → c = ±1`. **`f(x) = x` or `f(x) = −x`** |
| 150 | Set `x = 0`: `f(f(y)) = y + f(0)`. Set `y = 0`: `f(x + f(0)) = f(0) + f(x)`. So `g(x) = f(x) − f(0)` satisfies `g(x + f(0)) = g(x)`, i.e., `g` is periodic with period `f(0)`. From `f(f(y)) = y + f(0)`, `f` is bijective. A periodic bijection has period 0: `f(0) = 0`. Then `f(f(y)) = y` and `f(x + f(y)) = y + f(x)`. This is the same as problem 149. **`f(x) = x` or `f(x) = −x`** |
| 151 | `f(x+y) = m(x+y) ≤ mx + my = f(x) + f(y)`. So `m(x+y) ≤ mx + my` → `0 ≤ 0`. Always true! **`f(x) = mx` is subadditive for ALL values of `m`.** |
| 152 | From Cauchy: `f(x) = cx` for `x ∈ ℚ` (since `f: ℚ → ℚ`, no continuity needed). `f(f(x)) = c²x = x → c² = 1 → c = ±1`. **`f(x) = x` or `f(x) = −x`** |
| 153 | The condition `|f(x) − f(y)| = |x − y|` means `f` preserves distances. Set `y = 0`: `|f(x) − f(0)| = |x|`, so `f(x) = f(0) ± x` (sign could depend on `x`). But the sign must be consistent: if `f(a) = f(0) + a` and `f(b) = f(0) − b` for `a, b > 0`, check: `|f(a) − f(b)| = |a + b|` and `|a − b|`. Need `a + b = |a − b|` only if one is zero. So the sign is globally consistent. **`f(x) = x + c` or `f(x) = −x + c`** for some constant `c ∈ ℝ`. |
| 154 | From `f(x+y) = f(x)+f(y)`: Cauchy → `f(x) = cx` (continuous, since `f(xy)=f(x)f(y)` implies `f` is continuous or zero). From `f(xy) = f(x)f(y)`: `cxy = c²xy` → `c = c²` → `c = 0` or `c = 1`. Also `f(1) = f(1·1) = f(1)²` → `f(1) = 0` or `1`. **`f(x) = 0` (trivial) or `f(x) = x` (identity)**. |
| 155 | Set `x = 0, y = 0`: `f(f(0)) = f(0)²`. Set `x = 0`: `f(f(y)) = f(0)² + y`. So `f(f(y)) = f(0)² + y` — `f` is a bijection. Set `y = 0`: `f(x² + f(0)) = f(x)²`. Set `x = 0`: `f(f(y)) = f(0)² + y` (already known). Let `c = f(0)`. Then `f(f(y)) = c² + y` and `f(x² + c) = f(x)² + 0`... wait, `f(x² + f(0)) = f(x)²`. If `c = 0`: `f(f(y)) = y` (involution) and `f(x²) = f(x)²`. Try `f(x) = x`: `f(x² + f(y)) = x² + y` and `f(x)² + y = x² + y` ✓. **`f(x) = x` works.** Try `f(x) = −x`: `f(x² + f(y)) = f(x² − y) = −(x² − y) = −x² + y`. `f(x)² + y = x² + y`. Need `−x² = x²` → no. Try `f(x) = x + c`: `f(x² + f(y)) = x² + y + c + c = x² + y + 2c`. `f(x)² + y = (x+c)² + y = x² + 2cx + c² + y`. Need `2c = 0` and `2c = c²` → `c = 0`. **`f(x) = x` is the unique solution.** |

### M. Challenging Function Problems

| # | Answer |
|---|---|
| 156 | Need `x² − 4 ≥ 0` AND `4 − x² > 0` (strict, since denominator can't be zero). `x² ≥ 4` AND `x² < 4` — **impossible. Domain is empty (∅).** |
| 157 | Let `t = x² + x`. Then `f = (t + 1)/(t + 2)`. `t = x² + x ≥ −1/4` (min at `x = −1/2`). As `t → ∞`: `f → 1`. At `t = −1/4`: `f = (3/4)/(7/4) = 3/7`. So `f` ranges from `3/7` to `1` (exclusive of 1). **Range: `[3/7, 1)`** |
| 158 | `|x² − 5x + 6| = 2`. Case 1: `x² − 5x + 6 = 2 → x² − 5x + 4 = 0 → (x−1)(x−4) = 0 → x = 1, 4`. Case 2: `x² − 5x + 6 = −2 → x² − 5x + 8 = 0 → Δ = 25−32 = −7 < 0`. **`x = 1, 4`** |
| 159 | `f(1) = 1 + f(0) = 1`. `f(2) = 4 + f(1) = 5`. `f(3) = 9 + f(2) = 14`. `f(4) = 16 + f(3) = 30`. **`f(4) = 30`** |
| 160 | Piecewise: `f(x) = |x−2| + 1`. For `x ≥ 2`: `f(x) = x − 2 + 1 = x − 1`. For `x < 2`: `f(x) = 2 − x + 1 = 3 − x`. Range: `[1, ∞)`. For `x ≥ 2`: `y = x − 1 → x = y + 1` (valid `x ≥ 2`, i.e., `y ≥ 1`). For `x < 2`: `y = 3 − x → x = 3 − y` (valid `x < 2`, i.e., `y > 1`). So: `f⁻¹(y) = y + 1` for `y = 1` (from `x ≥ 2` piece: `f(2) = 1`); for `y > 1`: two preimages? `x = y+1` and `x = 3−y`. Check `y = 2`: `x = 3` and `x = 1`. `f(3) = |1|+1 = 2` ✓, `f(1) = |−1|+1 = 2` ✓. So `f` is NOT one-to-one! **`f` does not have an inverse** (fails horizontal line test for `y > 1`). If restricted to `[2, ∞)`: `f⁻¹(x) = x + 1` for `x ≥ 1`. |
| 161 | `f(x) ≤ 0` when `x ∈ [1, 3]`. So `f(f(x)) ≤ 0` when `f(x) ∈ [1, 3]`. `f(x) = x²−4x+3 = (x−2)²−1`. `f(x) = 1` when `(x−2)² = 2 → x = 2±√2`. `f(x) = 3` when `(x−2)² = 4 → x = 0, 4`. So `f(x) ∈ [1,3]` when `x ∈ [2−√2, 2+√2]` (values 1 to 3) but also need to check: `f` has min `−1` at `x=2`. `f(x) ≥ 1` when `(x−2)² ≥ 2`, i.e., `x ≤ 2−√2` or `x ≥ 2+√2`. `f(x) ≤ 3` when `(x−2)² ≤ 4`, i.e., `0 ≤ x ≤ 4`. So `1 ≤ f(x) ≤ 3` when `x ∈ [0, 2−√2] ∪ [2+√2, 4]`. **`x ∈ [0, 2−√2] ∪ [2+√2, 4]`** |
| 162 | `||x−1| − |x+1|| = 2`. Let `g(x) = |x−1| − |x+1|`. For `x ≥ 1`: `g = (x−1)−(x+1) = −2`. For `−1 < x < 1`: `g = (1−x)−(x+1) = −2x`. For `x ≤ −1`: `g = (1−x)−(−x−1) = 2`. So `|g(x)| = 2` when: `x ≥ 1` (g = −2, |g| = 2 ✓), `x ≤ −1` (g = 2, |g| = 2 ✓), `|−2x| = 2` → `x = ±1` (boundary). **Solution: `x ≤ −1` or `x ≥ 1`, i.e., `|x| ≥ 1`** |
| 163 | `f(x) = (x−1)/(x+1)`. `f(f(x)) = f((x−1)/(x+1)) = ((x−1)/(x+1) − 1) / ((x−1)/(x+1) + 1) = [(x−1−x−1)/(x+1)] / [(x−1+x+1)/(x+1)] = (−2)/(2x) = −1/x`. `f(f(f(x))) = f(−1/x) = (−1/x − 1)/(−1/x + 1) = (−1−x)/(−1+x) = (x+1)/(1−x) = −(x+1)/(x−1)`. `f(f(f(f(x)))) = f((x+1)/(1−x)) = ((x+1)/(1−x) − 1) / ((x+1)/(1−x) + 1) = [(x+1−1+x)/(1−x)] / [(x+1+1−x)/(1−x)] = (2x)/2 = x`. **`f(f(f(f(x)))) = x`** — the function has order 4 under composition. |
| 164 | `⌊x²⌋ = 5` → `5 ≤ x² < 6` → `√5 ≤ |x| < √6` → `x ∈ [−√6, −√5] ∪ [√5, √6)`... wait: `5 ≤ x² < 6`. `x² ≥ 5 → |x| ≥ √5`. `x² < 6 → |x| < √6`. So `x ∈ (−√6, −√5] ∪ [√5, √6)`... actually `x² ≥ 5` gives `x ≤ −√5` or `x ≥ √5`, and `x² < 6` gives `−√6 < x < √6`. Intersection: `x ∈ (−√6, −√5] ∪ [√5, √6)`. For `x ∈ [0, 10]`: **`x ∈ [√5, √6)`**, i.e., approximately `[2.236, 2.449)`. |
| 165 | For range to be ℝ, `f(x) = (x²+k)/(x+1)` must take all real values. Let `y = (x²+k)/(x+1)`. Then `x² − yx + (k − y) = 0`. Discriminant: `y² − 4(k−y) = y² + 4y − 4k ≥ 0`. For ALL `y`: `y² + 4y − 4k ≥ 0` → discriminant of this in `y` must be `≤ 0`: `16 + 16k ≤ 0 → k ≤ −1`. **`k ≤ −1`** |
| 166 | Domain of `g`: need `1 ≤ 2x−1 ≤ 4 → 1 ≤ x ≤ 5/2`. So domain of `g` is `[1, 5/2]`. Range: `f` maps `[1, 4]` to `[2, 7]`. `f(2x−1)` maps to `[2, 7]`. Then `+3` shifts to `[5, 10]`. **Domain: `[1, 5/2]`, Range: `[5, 10]`** |
| 167 | Add the equations: `2f(x) = x² + 2x³ → f(x) = x²/2 + x³`. Check: `f(−x) = x²/2 − x³`. `f(x) + f(−x) = x²` ✓. `f(x) − f(−x) = 2x³` ✓. **`f(x) = x³ + x²/2`** |
| 168 | `x³ − 3x + 1 = x → x³ − 4x + 1 = 0`. Rational roots: `±1`. `1 − 4 + 1 = −2 ≠ 0`. `−1 + 4 + 1 = 4 ≠ 0`. No rational roots. Three real roots (discriminant of cubic is positive). Approximate: `x ≈ −2.11, 0.27, 1.84`. |
| 169 | For `x < 0`: `f(x) = x + 1`, range `(−∞, 1)`. For `x ≥ 0`: `f(x) = x²`, range `[0, ∞)`. Combined range: ℝ. For `y < 1` from the first piece: `x = y − 1` (valid if `y − 1 < 0 → y < 1` ✓). For `y ≥ 0` from the second piece: `x = √y` (valid if `√y ≥ 0 → y ≥ 0` ✓). Overlap: `0 ≤ y < 1` has two preimages. **`f` is not one-to-one** (e.g., `f(0) = 0` and `f(−1) = 0`). Restrict domain to `x ≥ 0`: `f⁻¹(x) = √x`, domain `[0, ∞)`. |
| 170 | `x² > x` when `x > 1` or `x < 0`. On `[0, 2]`: `x² > x` for `x > 1`, `x² < x` for `0 < x < 1`, equal at `x = 0, 1`. So `f(x) = x` for `0 ≤ x ≤ 1`, `f(x) = x²` for `1 < x ≤ 2`. At `x = 1`: both give 1. Range: `[0, 4]` (min 0 at `x=0`, max 4 at `x=2`). **Piecewise: `f(x) = x` on `[0,1]`, `f(x) = x²` on `(1,2]`. Range: `[0, 4]`** |
| 171 | `{x} + ⌊x⌋ = (x − ⌊x⌋) + ⌊x⌋ = x`. So `f(x) = 2x` becomes `x = 2x → x = 0`. **Only `x = 0`.** The identity `{x} + ⌊x⌋ = x` is **always true** for all `x`, so the equation becomes `x = 2x → x = 0`. |
| 172 | `(f∘g)(x) = √(x² − 5)`. Domain: `x² − 5 ≥ 0 → |x| ≥ √5 → x ∈ (−∞, −√5] ∪ [√5, ∞)`. **Domain: `(−∞, −√5] ∪ [√5, ∞)`** — NOT all of ℝ, even though `g(x) = x²` is defined everywhere. |
| 173 | `f(0) = 1`. `f(1) = 1 + 1 = 2`. `f(2) = 2 + 2 = 4`. `f(3) = 4 + 3 = 7`. `f(4) = 7 + 4 = 11`. Pattern: `f(n) = 1 + (1 + 2 + ... + n) = 1 + n(n+1)/2`. **`f(n) = n(n+1)/2 + 1 = (n² + n + 2)/2`** |
| 174 | Set `x = y = 0`: `f(0) = 2f(0)² − 2 → 2f(0)² − f(0) − 2 = 0 → f(0) = (1 ± √17)/4`. Set `y = 0`: `f(x) = f(x)² + f(0)² − 2`. Let `c = f(0)`. `f(x)² − f(x) + c² − 2 = 0`. For this to have a solution for ALL `x`, the discriminant `1 − 4(c²−2) = 9 − 4c² ≥ 0 → |c| ≤ 3/2`. Also `f(x)` must be constant (since the quadratic in `f(x)` has at most 2 roots, but `f` takes values for all `x` — unless `f` is constant). If `f` is constant: `f(x) = c` for all `x`. Then `c = 2c² − 2 → 2c² − c − 2 = 0 → c = (1 ± √17)/4`. **`f(x) = (1+√17)/4` or `f(x) = (1−√17)/4`** (both constants). |
| 175 | `x² − 3|x| + 2 ≤ 0`. Let `u = |x| ≥ 0`: `u² − 3u + 2 ≤ 0 → (u−1)(u−2) ≤ 0 → 1 ≤ u ≤ 2`. So `1 ≤ |x| ≤ 2 → x ∈ [−2, −1] ∪ [1, 2]`. **`x ∈ [−2, −1] ∪ [1, 2]`** |

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
| `⌊f(x)⌋` / `⌈f(x)⌉` | Same as `f` | ℤ (integers) |
| `{f(x)} = f(x) − ⌊f(x)⌋` | Same as `f` | `[0, 1)` |
| `max(f, g)` / `min(f, g)` | `dom(f) ∩ dom(g)` | Upper/lower envelope |
| `f(x) + g(x)` | `dom(f) ∩ dom(g)` | Union of possible sums |

### Quick Reference: Functional Equation Techniques

| Equation type | Strategy | Solution (continuous) |
|---|---|---|
| `f(x+y) = f(x)+f(y)` | Substitute `x=y=0`, `y=−x`, build rationals | `f(x) = cx` (Cauchy) |
| `f(x+y) = f(x)·f(y)` | Check `f(0)`, build `f(n)`, extend to rationals | `f(x) = aˣ` |
| `f(xy) = f(x)+f(y)` | Substitute `x=y=1`, `y=1/x` | `f(x) = c·ln(x)` |
| `f(f(x)) = x` | Involution; must be decreasing if non-trivial | Many solutions |
| `f(f(x)) = g(x)` | Try `f` of same degree/type as `g` | Depends on `g` |
| `f(x) + f(1/x) = ...` | Substitute `x → 1/x`, solve system | Eliminate `f(1/x)` |
| `f(x+y) + f(x−y) = ...` | Set `x=0`, `y=0`, `x=y` | Often `f(x) = ax²+bx` |
| `f(x + f(y)) = f(x) + y` | Set `x=0`, prove bijection, reduce to Cauchy | `f(x) = x` or `f(x) = −x` |
| `|f(x)−f(y)| = |x−y|` | Isometry; set `y=0` | `f(x) = x+c` or `f(x) = −x+c` |

### Quick Reference: Function Properties Decision Guide

| Property | Test | Example |
|---|---|---|
| One-to-one (injective) | Horizontal line test / `f(a)=f(b) ⟹ a=b` | `x³` ✓, `x²` ✗ |
| Onto (surjective) | Range = codomain | `x³: ℝ→ℝ` ✓, `x²: ℝ→ℝ` ✗ |
| Even | `f(−x) = f(x)` | `x²`, `|x|`, `cos(x)` |
| Odd | `f(−x) = −f(x)` | `x³`, `1/x`, `sin(x)` |
| Periodic (period T) | `f(x+T) = f(x)` | `{x}` (T=1), `sin(x)` (T=2π) |
| Monotonic increasing | `a < b ⟹ f(a) < f(b)` | `x³`, `eˣ` |
| Monotonic decreasing | `a < b ⟹ f(a) > f(b)` | `−x`, `1/x` (on each branch) |
| Involution | `f(f(x)) = x` | `x`, `−x`, `1/x`, `a−x` |
| Subadditive | `f(x+y) ≤ f(x)+f(y)` | `√x`, `|x|`, `⌊x⌋` |
| Symmetric about `x=a` | `f(a+h) = f(a−h)` | `(x−3)²` about `x=3` |
| Symmetric about `(a,b)` | `f(a+h)+f(a−h) = 2b` | `(x−2)³+5` about `(2,5)` |
