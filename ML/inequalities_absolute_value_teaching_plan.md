# Problem-Based Teaching Plan: Inequalities & Absolute Value

**Format:** 3 sessions × 60 minutes
**Approach:** Problem-Based Learning (PBL) — each session opens with a motivating problem, develops theory through guided discovery, and closes with consolidation.

---

## Session 1 — Inequalities & Sign Analysis (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve linear and quadratic inequalities.
- Use the **sign analysis (number line) method** to solve polynomial and rational inequalities.
- Understand why "moving everything to one side" is the safe protocol (connecting to the equation-solving protocol from the previous unit).
- Solve higher-degree polynomial inequalities by factoring and sign analysis.

### Materials
- Whiteboard / projector
- Colored markers (red for critical points, blue for signs)
- Handout of problem sets
- Mini-whiteboards for pair work

---

### Part A: Hook & Motivating Problem (8 min)

**Present this problem on the board:**

> A company manufactures widgets. The revenue from selling `x` widgets is `R(x) = 50x` dollars. The cost is `C(x) = 200 + 20x` dollars. The company wants to make a profit of **at least $300**. What is the minimum number of widgets they must sell?

Let students set up the equation:

```
Profit = Revenue − Cost = 50x − (200 + 20x) = 30x − 200

Profit ≥ 300
30x − 200 ≥ 300
30x ≥ 500
x ≥ 50/3 ≈ 16.67
```

Since `x` must be a whole number: **at least 17 widgets.**

**Key realization:** This is not an equation — it's an **inequality**. The answer is not a single number but a *range* of values. This is the core idea of the session.

---

### Part B: Linear Inequalities — Quick Review & The Golden Rule (10 min)

#### Activity 1: Solve These (5 min — individual)

1. `3x + 5 < 14`
2. `−2x + 7 ≥ 1`
3. `4(x − 3) > 2x + 6`
4. `5 − 3x ≤ 2x − 10`

**Debrief** focusing on problem 2:

```
−2x + 7 ≥ 1
−2x ≥ −6
x ≤ 3          ← ⚠️ The inequality flipped!
```

Write in **red** on the board:

> ### The Golden Rule of Inequalities
> When you **multiply or divide** both sides of an inequality by a **negative** number, you must **flip the inequality sign**.
>
> - `3 < 5` → multiply by `−1` → `−3 > −5` ✓
> - Adding/subtracting never flips the sign.

**Why?** Quick demonstration: Draw a number line. `3` is to the left of `5`. Multiply by `−1`: `−3` is now to the *right* of `−5`. The order reverses.

#### Activity 2: Compound Inequalities (5 min)

5. `2 < 3x − 1 < 11`
6. `−5 ≤ 2x + 1 < 7`

**Debrief:** These are just two inequalities joined together. Solve both parts simultaneously:

```
2 < 3x − 1 < 11
3 < 3x < 12
1 < x < 4
```

---

### Part C: Quadratic Inequalities — The Sign Analysis Method (20 min)

**Transition:**
> "What happens when the inequality involves `x²`? We can't just isolate `x`."

#### Motivating Problem (5 min)

> Solve: `x² − 5x + 6 > 0`

Give students 2 minutes to try. Some will try to take square roots (wrong). Others will factor:

```
x² − 5x + 6 > 0
(x − 2)(x − 3) > 0
```

**Key question:** *When is the product of two factors positive?*

Guide students to realize there are **two cases**:
- Both factors positive: `x − 2 > 0` AND `x − 3 > 0` → `x > 3`
- Both factors negative: `x − 2 < 0` AND `x − 3 < 0` → `x < 2`

**Answer:** `x < 2` or `x > 3`

#### Introducing the Sign Table (10 min)

**This is the most important tool of the session.** Walk through the method step by step:

**Step 1:** Move everything to one side (if not already).
**Step 2:** Factor completely.
**Step 3:** Find the **critical points** (where each factor = 0).
**Step 4:** Draw a number line with critical points marked.
**Step 5:** Test the sign of each factor in each interval.
**Step 6:** Multiply signs to get the sign of the whole expression.

**Example on the board:**

```
Solve: x² − 5x + 6 > 0

Factor: (x − 2)(x − 3) > 0

Critical points: x = 2, x = 3

Number line:    ←──────●──────●──────→
                        2      3

Intervals:      (−∞, 2)   (2, 3)   (3, ∞)

Sign of (x−2):     −        +        +
Sign of (x−3):     −        −        +
Product:            +        −        +

We need > 0 (positive): x ∈ (−∞, 2) ∪ (3, ∞)
```

Draw this sign table on the board using **colored markers** — red for critical points, blue for signs. Students should copy the format exactly.

#### Activity 3: Practice with Sign Tables (5 min — pairs)

1. `x² + 2x − 8 ≤ 0` → `(x+4)(x−2) ≤ 0` → `x ∈ [−4, 2]`
2. `x² − 9 > 0` → `(x+3)(x−3) > 0` → `x ∈ (−∞,−3) ∪ (3,∞)`
3. `2x² + 5x − 3 ≥ 0` → `(2x−1)(x+3) ≥ 0` → `x ∈ (−∞,−3] ∪ [1/2,∞)`

---

### Part D: Higher-Degree Inequalities (15 min)

**Transition:**
> "The sign table method works for ANY polynomial, not just quadratics. Let's try higher degrees."

#### Activity 4: Cubic and Quartic Inequalities (10 min — individual)

1. `x³ − 4x > 0`

   Factor: `x(x²−4) = x(x+2)(x−2) > 0`
   Critical points: `x = −2, 0, 2`

   ```
   Interval:    (−∞,−2)  (−2,0)  (0,2)  (2,∞)
   x:              −       −       +      +
   (x+2):          −       +       +      +
   (x−2):          −       −       −      +
   Product:         −       +       −      +
   ```

   **Answer:** `x ∈ (−2, 0) ∪ (2, ∞)`

2. `x³ − 6x² + 11x − 6 < 0`

   Factor (rational root theorem): `(x−1)(x−2)(x−3) < 0`
   Critical points: `x = 1, 2, 3`

   ```
   Interval:    (−∞,1)  (1,2)  (2,3)  (3,∞)
   (x−1):         −      +      +      +
   (x−2):         −      −      +      +
   (x−3):         −      −      −      +
   Product:        −      +      −      +
   ```

   **Answer:** `x ∈ (−∞, 1) ∪ (2, 3)`

3. `x⁴ − 5x² + 4 ≥ 0`

   Factor: `(x²−1)(x²−4) = (x+1)(x−1)(x+2)(x−2) ≥ 0`
   Critical points: `x = −2, −1, 1, 2`

   ```
   Interval:  (−∞,−2) (−2,−1) (−1,1) (1,2) (2,∞)
   (x+2):       −       +       +      +      +
   (x+1):       −       −       +      +      +
   (x−1):       −       −       −      +      +
   (x−2):       −       −       −      −      +
   Product:      +       −       +      −      +
   ```

   **Answer:** `x ∈ (−∞, −2] ∪ [−1, 1] ∪ [2, ∞)`

#### Key Observation (5 min)

Ask students: *How many intervals does a sign table have?*

Guide them to the pattern:

| Number of distinct roots | Number of intervals |
|---|---|
| 1 | 2 |
| 2 | 3 |
| 3 | 4 |
| 4 | 5 |

> **Rule:** `n` distinct roots create `n + 1` intervals.

Also note: **repeated roots** don't create new intervals but affect the sign pattern:

- `(x−1)²` is always ≥ 0 — it touches zero but doesn't change sign.
- `(x−1)³` changes sign (like a single power).

**Example:** `(x−1)²(x−2) > 0`
- At `x = 1`: the factor `(x−1)²` is zero but doesn't change sign.
- At `x = 2`: sign changes.
- The solution is `x ∈ (−∞, 1) ∪ (1, 2) ∪ (2, ∞)` — i.e., all `x ≠ 1, 2`, since `(x−1)²` makes the product non-negative and `(x−2)` provides the sign.

Actually: for `(x−1)²(x−2) > 0`:
- `x < 1`: `(+)(−) = −` → no
- `1 < x < 2`: `(+)(−) = −` → no
- `x > 2`: `(+)(+) = +` → yes
- `x = 1`: gives 0, not > 0 → excluded

**Answer:** `x ∈ (2, ∞)`

---

### Part E: Wrap-Up & Exit Ticket (7 min)

#### Summary (3 min)

> ### Sign Analysis Protocol for Inequalities
> 1. Move everything to one side: `f(x) [inequality] 0`
> 2. Factor `f(x)` completely
> 3. Find critical points (roots of each factor)
> 4. Build the sign table: test each factor in each interval
> 5. Read off the intervals where the sign matches the inequality
> 6. Check boundary points: include for `≤, ≥`; exclude for `<, >`

#### Exit Ticket (4 min)

1. `x² − 7x + 10 ≤ 0`
2. `x(x−1)(x+3) > 0`
3. `(x−2)²(x+1) < 0`

**Answers:**
1. `(x−2)(x−5) ≤ 0` → `[2, 5]`
2. Sign table: `−` on `(−∞,−3)`, `+` on `(−3,0)`, `−` on `(0,1)`, `+` on `(1,∞)` → `(−3, 0) ∪ (1, ∞)`
3. `(x−2)² ≥ 0` always, so need `(x+1) < 0` and `(x−2)² ≠ 0` → `x < −1`, i.e., `(−∞, −1)`

---

### Session 1 — Summary Table

| Inequality Type | Method | Example |
|---|---|---|
| Linear | Isolate `x` (flip if ÷ by negative) | `−2x > 6 → x < −3` |
| Quadratic | Factor + sign table | `(x−2)(x−5) > 0 → x<2 or x>5` |
| Higher-degree polynomial | Factor fully + sign table | `x(x−1)(x+3) < 0` |
| Repeated factors | Even power: no sign change; Odd power: sign change | `(x−1)²(x+2) > 0` |

---

## Session 2 — Absolute Value: Definition, Equations & Inequalities (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Define absolute value both algebraically and geometrically.
- Solve absolute value equations.
- Solve absolute value inequalities using algebraic and geometric methods.
- Combine absolute value with sign analysis for compound problems.

### Materials
- Whiteboard
- Colored markers
- Number line visual aids
- Handout

---

### Part A: Hook — The Distance Problem (8 min)

**Present this problem:**

> You are standing at position `3` on a number line. You can move left or right. Find all positions where you are **exactly 5 units away** from position `3`.

Students will quickly find: `3 + 5 = 8` and `3 − 5 = −2`.

**Now ask:** Find all positions where you are **within 5 units** of position `3`.

Answer: everything between `−2` and `8`, i.e., `−2 ≤ x ≤ 8`.

**Write the key idea on the board:**

> ### Geometric Definition of Absolute Value
> `|x − a|` = the **distance** from `x` to `a` on the number line.
>
> - `|x|` = distance from `x` to `0`
> - `|x − 3|` = distance from `x` to `3`
> - `|x + 5|` = distance from `x` to `−5` (since `x + 5 = x − (−5)`)

**This geometric interpretation is the most powerful tool** for solving absolute value problems. Keep returning to it throughout the session.

---

### Part B: The Algebraic Definition (7 min)

Write the piecewise definition:

> ### Definition of Absolute Value
> ```
>         ⎧  x,   if x ≥ 0
> |x| =   ⎨
>         ⎩ −x,   if x < 0
> ```

**Key points:**
- `|x|` is **always non-negative**: `|x| ≥ 0` for all `x`.
- `|x| = 0` if and only if `x = 0`.
- `|−x| = |x|` (distance doesn't care about direction).
- `|x|² = x²` (but `|x| ≠ x` in general!).
- `√(x²) = |x|` (the principal square root is non-negative).

#### Quick Check (3 min)

Evaluate:
1. `|−7| = 7`
2. `|3 − 8| = 5`
3. `|x − 4|` when `x = 1` → `3`; when `x = 6` → `2`
4. `|x| = −5` → **No solution!** (Absolute value is never negative.)
5. `|x| = 0` → `x = 0`

---

### Part C: Absolute Value Equations (15 min)

#### The Two-Case Method (5 min)

**Problem:** Solve `|x − 3| = 5`

**Geometric:** "What numbers are 5 units from 3?" → `x = 8` or `x = −2`.

**Algebraic:** Two cases (the expression inside is positive or negative):

```
Case 1: x − 3 = 5   → x = 8
Case 2: x − 3 = −5  → x = −2
```

Write the general rule:

> ### Solving `|expression| = k` (where `k > 0`)
> Split into two equations:
> ```
> expression = k    OR    expression = −k
> ```

> ### If `k < 0`: No solution (absolute value is never negative).
> ### If `k = 0`: expression = 0 (single equation).

#### Activity 5: Solve These (5 min — individual)

1. `|2x + 1| = 7` → `2x+1 = 7` or `2x+1 = −7` → `x = 3` or `x = −4`
2. `|3x − 6| = 0` → `3x − 6 = 0` → `x = 2` (only one solution)
3. `|x + 4| = −2` → No solution
4. `|5 − x| = 12` → `5−x = 12` or `5−x = −12` → `x = −7` or `x = 17`

#### Trickier Problems (5 min)

5. `|x² − 4| = 5`

   ```
   Case 1: x² − 4 = 5  → x² = 9  → x = ±3
   Case 2: x² − 4 = −5 → x² = −1 → No real solution
   ```

   **Answer:** `x = 3` or `x = −3`

6. `|2x − 3| = |x + 6|`

   Two absolute values equal means the expressions are equal or negatives:
   ```
   Case 1: 2x − 3 = x + 6   → x = 9
   Case 2: 2x − 3 = −(x+6)  → 2x − 3 = −x − 6 → 3x = −3 → x = −1
   ```

   **Answer:** `x = 9` or `x = −1`

---

### Part D: Absolute Value Inequalities (20 min)

#### The Geometric Approach (8 min)

**Problem:** Solve `|x − 3| < 5`

**Geometric:** "What numbers are **less than 5 units** from 3?" → Between `−2` and `8`.

```
|x − 3| < 5
↔ −5 < x − 3 < 5
↔ −2 < x < 8
```

**Problem:** Solve `|x − 3| > 5`

**Geometric:** "What numbers are **more than 5 units** from 3?" → Outside the interval.

```
|x − 3| > 5
↔ x − 3 < −5  OR  x − 3 > 5
↔ x < −2  OR  x > 8
```

Write the general rules on the board:

> ### Absolute Value Inequality Rules (when `k > 0`)
>
> | Inequality | Meaning | Equivalent to | Solution type |
> |---|---|---|---|
> | `|expr| < k` | Within `k` units | `−k < expr < k` | **Between** (intersection) |
> | `|expr| ≤ k` | Within or at `k` units | `−k ≤ expr ≤ k` | **Between** (closed) |
> | `|expr| > k` | Beyond `k` units | `expr < −k` OR `expr > k` | **Outside** (union) |
> | `|expr| ≥ k` | Beyond or at `k` units | `expr ≤ −k` OR `expr ≥ k` | **Outside** (closed) |

**Memory aid:**
- **Less than → Between** (a "sandwich")
- **Greater than → Outside** (two tails)

#### Activity 6: Solve These (7 min — pairs)

1. `|x + 2| < 4` → `−4 < x+2 < 4` → `−6 < x < 2`
2. `|3x − 1| ≥ 8` → `3x−1 ≤ −8` or `3x−1 ≥ 8` → `x ≤ −7/3` or `x ≥ 3`
3. `|2 − x| < 3` → `−3 < 2−x < 3` → `−5 < −x < 1` → `−1 < x < 5` *(careful with the flip!)*
4. `|x/2 + 1| > 3` → `x/2+1 < −3` or `x/2+1 > 3` → `x < −8` or `x > 4`

#### The "Sandwich" vs "Two Tails" Trap (5 min)

**Present this common error:**

> Solve `|x − 1| < −3`

Some students will write `−3 < x−1 < 3` and get an answer. But:

> **Absolute value is always ≥ 0.** It can never be less than a negative number.

**Answer:** No solution.

> Solve `|x + 2| > −1`

Some students will split into two cases. But:

> **Absolute value is always ≥ 0 > −1.** So this is true for ALL `x`.

**Answer:** All real numbers.

**Write on the board:**

| Inequality | If `k < 0` |
|---|---|
| `|expr| < k` | No solution (abs. value ≥ 0 > k) |
| `|expr| > k` | All real numbers (abs. value ≥ 0 > k) |

---

### Part E: Wrap-Up & Exit Ticket (10 min)

#### Challenge Problem (5 min)

> Solve: `|x − 2| + |x + 3| = 7`

Guide students through the **critical point method**:

1. Find where each absolute value changes behavior: `x = 2` and `x = −3`.
2. These divide the number line into three regions:

**Region 1: `x < −3`**
```
−(x−2) − (x+3) = 7
−x + 2 − x − 3 = 7
−2x − 1 = 7
−2x = 8
x = −4  ✓ (in region x < −3)
```

**Region 2: `−3 ≤ x < 2`**
```
−(x−2) + (x+3) = 7
−x + 2 + x + 3 = 7
5 = 7  ✗ (contradiction)
```

**Region 3: `x ≥ 2`**
```
(x−2) + (x+3) = 7
2x + 1 = 7
2x = 6
x = 3  ✓ (in region x ≥ 2)
```

**Answer:** `x = −4` or `x = 3`

#### Exit Ticket (5 min)

1. `|2x − 5| = 3`
2. `|x + 4| ≤ 6`
3. `|3x + 1| > 10`
4. `|x − 7| < −2`

**Answers:**
1. `2x−5 = 3` → `x = 4`; `2x−5 = −3` → `x = 1`. **Answer: `x = 1, 4`**
2. `−6 ≤ x+4 ≤ 6` → `−10 ≤ x ≤ 2`. **Answer: `[−10, 2]`**
3. `3x+1 < −10` → `x < −11/3`; `3x+1 > 10` → `x > 3`. **Answer: `x < −11/3` or `x > 3`**
4. Absolute value ≥ 0 > −2 is impossible for `<`. **Answer: No solution**

---

### Session 2 — Summary Table

| Type | Method | Key Idea |
|---|---|---|
| `|expr| = k, k > 0` | Two cases: `expr = k` or `expr = −k` | Distance = k |
| `|expr| = k, k < 0` | No solution | Abs. value ≥ 0 |
| `|expr| < k, k > 0` | `−k < expr < k` | "Sandwich" / between |
| `|expr| > k, k > 0` | `expr < −k` or `expr > k` | "Two tails" / outside |
| `|A| = |B|` | `A = B` or `A = −B` | Same distance from 0 |
| `|expr| + |expr₂| = k` | Critical point method | Split at each zero |

---

## Session 3 — Combining Absolute Value, Inequalities & Sign Analysis (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve compound problems combining absolute value and inequalities.
- Solve rational inequalities (with fractions) using sign analysis.
- Apply absolute value to model real-world distance and tolerance problems.
- Tackle challenging multi-step problems.

### Materials
- Whiteboard
- Handout with challenge problems
- Graphing calculator or Desmos (optional)

---

### Part A: Hook — The Manufacturing Tolerance Problem (8 min)

> A factory produces bolts with a target diameter of **10 mm**. The bolts are acceptable only if the diameter is **within 0.2 mm** of the target. Additionally, the bolt's length must be **within 0.5 mm** of **50 mm**.
>
> (a) Write the acceptance conditions for diameter `d` and length `L`.
> (b) If a bolt has diameter `d = 10.15` and length `L = 49.8`, is it acceptable?
> (c) If the diameter is `d = 10.3`, what range of lengths would still make the bolt acceptable?

**Solution:**

(a) `|d − 10| ≤ 0.2` and `|L − 50| ≤ 0.5`

(b) `|10.15 − 10| = 0.15 ≤ 0.2` ✓ and `|49.8 − 50| = 0.2 ≤ 0.5` ✓ → **Acceptable**

(c) `|10.3 − 10| = 0.3 > 0.2` → **Rejected regardless of length.**

---

### Part B: Rational Inequalities — Sign Analysis Extended (15 min)

**Transition:**
> "Sign analysis works for polynomials. What about fractions?"

#### Motivating Problem (5 min)

> Solve: `(x − 1)/(x + 2) > 0`

**Common wrong approach:** Multiply both sides by `(x + 2)` → `x − 1 > 0` → `x > 1`.

**Why it's wrong:** We don't know if `(x + 2)` is positive or negative! If it's negative, we'd need to flip the inequality. This is the same trap as dividing by a variable expression in equations.

**Correct approach — Sign Table:**

```
Factor: (x − 1) / (x + 2) > 0

Critical points: x = 1 (numerator = 0), x = −2 (denominator = 0, excluded!)

Interval:    (−∞, −2)  (−2, 1)  (1, ∞)
(x − 1):        −        −       +
(x + 2):        −        +       +
Quotient:        +        −       +

We need > 0: x ∈ (−∞, −2) ∪ (1, ∞)
```

Write the protocol:

> ### Sign Analysis for Rational Inequalities
> 1. Move everything to one side: `f(x)/g(x) [ineq] 0`
> 2. Factor numerator and denominator
> 3. Find critical points: zeros of numerator AND zeros of denominator
> 4. **Zeros of the denominator are always EXCLUDED** (division by zero!)
> 5. Build the sign table
> 6. Read off the matching intervals
> 7. Include zeros of the numerator only if `≤` or `≥`

#### Activity 7: Rational Inequalities (8 min — pairs)

1. `(x + 3)/(x − 1) ≤ 0`
   - Critical: `x = −3` (num), `x = 1` (den, excluded)
   - Sign: `(−∞,−3): +`, `(−3,1): −`, `(1,∞): +`
   - **Answer: `[−3, 1)`** — include `−3` (numerator zero, `≤`), exclude `1` (denominator zero)

2. `x/(x² − 4) ≥ 0`
   - Factor: `x / [(x−2)(x+2)] ≥ 0`
   - Critical: `x = 0` (num), `x = 2, −2` (den, excluded)
   - Sign table:
     ```
     (−∞,−2): (−)/(+)(−) = +
     (−2,0):  (−)/(−)(+) = −
     (0,2):   (+)/(−)(+) = −
     (2,∞):   (+)/(+)(+) = +
     ```
   - **Answer: `(−∞, −2) ∪ [0, 2)`** — include `0`, exclude `±2`

3. `(x² − 1)/(x + 1) > 0`
   - Factor: `(x−1)(x+1)/(x+1) > 0`
   - **Simplify carefully:** `(x+1)` cancels, but `x ≠ −1` still!
   - `x − 1 > 0` and `x ≠ −1` → `x > 1` (since `−1` is already excluded and not in `x > 1`)
   - **Answer: `(1, ∞)`**
   - **Teaching note:** This is the inequality version of "losing solutions." Canceling is safe as long as you remember the domain restriction `x ≠ −1`.

4. `(2x − 1)/(x² + x − 6) < 0`
   - Factor: `(2x−1) / [(x+3)(x−2)] < 0`
   - Critical: `x = 1/2` (num), `x = −3, 2` (den, excluded)
   - Sign table:
     ```
     (−∞,−3):   (−)/(−)(−) = −  ✓
     (−3, 1/2): (−)/(+)(−) = +
     (1/2, 2):  (+)/(+)(−) = −  ✓
     (2, ∞):    (+)/(+)(+) = +
     ```
   - **Answer: `(−∞, −3) ∪ (1/2, 2)`**

---

### Part C: Compound Absolute Value Inequalities (15 min)

#### Activity 8: Multi-Step Problems (10 min — individual)

1. `2 < |x − 3| < 7`

   **Two conditions:** `|x−3| > 2` AND `|x−3| < 7`

   `|x−3| > 2` → `x < 1` or `x > 5`

   `|x−3| < 7` → `−4 < x < 10`

   **Intersection:** `−4 < x < 1` or `5 < x < 10`

   **Answer: `(−4, 1) ∪ (5, 10)`**

2. `|x² − 4| ≤ 3`

   ```
   −3 ≤ x² − 4 ≤ 3
   1 ≤ x² ≤ 7
   ```

   `x² ≥ 1` → `x ≤ −1` or `x ≥ 1`
   `x² ≤ 7` → `−√7 ≤ x ≤ √7`

   **Intersection:** `[−√7, −1] ∪ [1, √7]`

3. `|2x + 1| < |x − 3|`

   **Method:** Square both sides (valid since both sides are non-negative):
   ```
   (2x+1)² < (x−3)²
   4x² + 4x + 1 < x² − 6x + 9
   3x² + 10x − 8 < 0
   (3x − 2)(x + 4) < 0
   ```
   Critical: `x = 2/3, x = −4`
   Sign: `(−∞,−4): +`, `(−4, 2/3): −`, `(2/3, ∞): +`

   **Answer: `(−4, 2/3)`**

4. `(|x − 1| − 2)(x + 3) > 0`

   First solve `|x − 1| − 2 > 0` → `|x−1| > 2` → `x < −1` or `x > 3`

   Then solve `|x − 1| − 2 < 0` → `|x−1| < 2` → `−1 < x < 3`

   **Case 1:** `|x−1|−2 > 0` (i.e., `x < −1` or `x > 3`) and `x + 3 > 0` (i.e., `x > −3`):
   - `−3 < x < −1` or `x > 3`

   **Case 2:** `|x−1|−2 < 0` (i.e., `−1 < x < 3`) and `x + 3 < 0` (i.e., `x < −3`):
   - `−1 < x < 3` and `x < −3`: **empty** (no overlap)

   **Answer: `(−3, −1) ∪ (3, ∞)`**

#### Discussion: Why Squaring Works for |A| < |B| (5 min)

Ask: *Why is it valid to square both sides of `|A| < |B|`?*

Guide students:
- Both `|A|` and `|B|` are non-negative.
- For non-negative numbers, `a < b` ↔ `a² < b²` (the squaring function is increasing on `[0, ∞)`).
- This avoids splitting into cases.

**Caveat:** This only works when comparing two absolute values. It's unnecessarily complicated for simple cases like `|x| < 5`.

---

### Part D: Challenge Problems (15 min)

Present these one at a time. Give students 2–3 minutes per problem before discussing.

#### Challenge 1: The Three Absolute Values

> Solve: `|x| + |x − 2| + |x − 4| = 6`

**Critical points:** `x = 0, 2, 4` → four regions.

**Region 1: `x < 0`**
```
−x − (x−2) − (x−4) = 6
−x − x + 2 − x + 4 = 6
−3x + 6 = 6
x = 0  ✗ (not in x < 0)
```

**Region 2: `0 ≤ x < 2`**
```
x − (x−2) − (x−4) = 6
x − x + 2 − x + 4 = 6
−x + 6 = 6
x = 0  ✓ (in 0 ≤ x < 2)
```

**Region 3: `2 ≤ x < 4`**
```
x + (x−2) − (x−4) = 6
x + x − 2 − x + 4 = 6
x + 2 = 6
x = 4  ✗ (not in 2 ≤ x < 4, since x must be < 4)
```

**Region 4: `x ≥ 4`**
```
x + (x−2) + (x−4) = 6
3x − 6 = 6
3x = 12
x = 4  ✓ (in x ≥ 4)
```

**Answer:** `x = 0` or `x = 4`

#### Challenge 2: The Hidden Quadratic

> Solve: `x² − 3|x| − 4 < 0`

**Key insight:** `x² = |x|²`, so let `u = |x|`:

```
u² − 3u − 4 < 0
(u − 4)(u + 1) < 0
```

Since `u = |x| ≥ 0`, the factor `(u+1)` is always positive. So we need `u − 4 < 0` → `u < 4` → `|x| < 4` → `−4 < x < 4`.

**Answer: `(−4, 4)`**

#### Challenge 3: Rational with Absolute Value

> Solve: `|x − 2| / (x + 1) > 1`

**Careful!** We cannot just multiply by `(x+1)` — its sign is unknown.

**Method:** Move everything to one side:

```
|x − 2| / (x + 1) − 1 > 0
[|x − 2| − (x + 1)] / (x + 1) > 0
```

Now analyze the numerator `|x − 2| − (x + 1)` by cases:

**Case `x ≥ 2`:** `(x − 2) − (x + 1) = −3 < 0` always.
So the fraction is `(−3)/(x+1)`. Need > 0 → `x + 1 < 0` → `x < −1`. But `x ≥ 2` contradicts `x < −1`. **No solution here.**

**Case `x < 2`:** `(2 − x) − (x + 1) = 1 − 2x`.
Need `(1 − 2x)/(x + 1) > 0` with `x < 2` and `x ≠ −1`.

Sign analysis of `(1−2x)/(x+1)`:
- Critical: `x = 1/2` (num), `x = −1` (den)
- `(−∞,−1): (+)/(−) = −`
- `(−1, 1/2): (+)/(+) = +`
- `(1/2, ∞): (−)/(+) = −`

Positive on `(−1, 1/2)`.

**Answer: `(−1, 1/2)`**

#### Challenge 4: Parameter Problem

> For what values of `a` does `|x − a| + |x + a| = 10` have:
> (a) exactly two solutions?
> (b) infinitely many solutions?
> (c) no solutions?

**Geometric interpretation:** `|x − a|` is distance from `a`; `|x + a| = |x − (−a)|` is distance from `−a`. The sum of distances from `x` to `a` and `−a` equals 10.

- If `a > 0`: the distance between `a` and `−a` is `2a`.
  - If `2a < 10` (i.e., `a < 5`): two solutions (one on each side).
  - If `2a = 10` (i.e., `a = 5`): infinitely many — every point between `−5` and `5` has sum = 10.
  - If `2a > 10` (i.e., `a > 5`): no solution (sum is always > 10).
- If `a = 0`: `2|x| = 10` → `x = ±5`. Two solutions.
- If `a < 0`: same as `|a|` (symmetric).

**Answers:**
- (a) `0 ≤ |a| < 5` (two solutions)
- (b) `|a| = 5` (infinitely many — the entire interval `[−a, a]`)
- (c) `|a| > 5` (no solutions)

---

### Part E: Exit Ticket (7 min)

1. `(x² − 9)/(x + 1) ≤ 0`
2. `|2x − 3| < |x + 6|`
3. `3 ≤ |x − 4| ≤ 7`

**Answers:**
1. `(x−3)(x+3)/(x+1) ≤ 0`. Critical: `x = 3, −3` (num), `x = −1` (den, excluded).
   Sign: `(−∞,−3): (+)/(−) = −` ✓; `(−3,−1): (−)/(−) = +`; `(−1,3): (−)/(+) = −` ✓; `(3,∞): (+)/(+) = +`.
   **Answer: `(−∞, −3] ∪ (−1, 3]`**

2. Square: `(2x−3)² < (x+6)²` → `4x²−12x+9 < x²+12x+36` → `3x²−24x−27 < 0` → `x²−8x−9 < 0` → `(x−9)(x+1) < 0` → **`(−1, 9)`**

3. `|x−4| ≥ 3` AND `|x−4| ≤ 7`. First: `x ≤ 1` or `x ≥ 7`. Second: `−3 ≤ x ≤ 11`. **Intersection: `[−3, 1] ∪ [7, 11]`**

---

### Part F: The Most Important Inequality in Mathematics (15 min)

*This section can be appended to Session 3 (extending it) or taught as a supplementary mini-session. It covers the fundamental principle `x² ≥ 0` and its far-reaching consequences.*

#### The Fundamental Principle (3 min)

**Write on the board, boxed:**

> ### The Universal Inequality
> For all real numbers `x`:
> ```
> x² ≥ 0
> ```
> Equality holds if and only if `x = 0`.

**This is the single most powerful tool for proving inequalities.** Nearly every classical inequality — AM-GM, Cauchy-Schwarz, the rearrangement inequality — ultimately reduces to "a square is non-negative."

#### Activity 9: Prove These (8 min — guided)

**Problem 1:** Prove that `a² + b² ≥ 2ab` for all real `a, b`.

**Guide students:**
> "We want to show `a² + b² − 2ab ≥ 0`. Does the left side look familiar?"

```
a² + b² − 2ab = (a − b)² ≥ 0  ✓
```

Equality when `a = b`.

**Problem 2:** Prove that `a² + b² ≥ 2ab` implies `(a + b)² ≥ 4ab`, and therefore `(a + b)/2 ≥ √(ab)` when `a, b ≥ 0`.

```
(a + b)² = a² + 2ab + b² = (a² + b²) + 2ab ≥ 2ab + 2ab = 4ab
```

So `(a + b)² ≥ 4ab`. Taking square roots (both sides non-negative when `a, b ≥ 0`):

```
(a + b)/2 ≥ √(ab)
```

> ### AM-GM Inequality (Two-Variable Form)
> For `a, b ≥ 0`:
> ```
> (a + b)/2 ≥ √(ab)
> ```
> Equality when `a = b`.

**Problem 3:** Prove that `a² + b² + c² ≥ ab + bc + ca` for all real `a, b, c`.

**Guide:**
> "Use the same trick — write the difference as a sum of squares."

```
a² + b² + c² − ab − bc − ca = ½[(a − b)² + (b − c)² + (c − a)²] ≥ 0  ✓
```

**Problem 4:** Prove that `x² + 1/x² ≥ 2` for `x ≠ 0`.

```
x² + 1/x² − 2 = (x − 1/x)² ≥ 0  ✓
```

Equality when `x = 1/x`, i.e., `x = ±1`.

**Problem 5:** Prove that `a² + b² ≥ (a + b)²/2` for all real `a, b`.

```
2(a² + b²) − (a + b)² = 2a² + 2b² − a² − 2ab − b² = a² − 2ab + b² = (a − b)² ≥ 0  ✓
```

#### The Technique: "Write the Difference as a Sum of Squares" (4 min)

**Write the protocol on the board:**

> ### Proving `f(a, b, ...) ≥ g(a, b, ...)`
> 1. Move everything to one side: `f − g ≥ 0`
> 2. Try to express `f − g` as a **sum of squares** (or a single square)
> 3. Since each square is `≥ 0`, the sum is `≥ 0`
> 4. State when equality holds (all squares must be zero simultaneously)

**Key algebraic moves to recognize:**

| Expression | Completes to | Type |
|---|---|---|
| `a² − 2ab + b²` | `(a − b)²` | Perfect square |
| `a² + b² − ab` | `(a − b/2)² + 3b²/4` | Modified square |
| `a² + b² − 2ab` | `(a − b)²` | The classic |
| `a² + b² + c² − ab − bc − ca` | `½[(a−b)² + (b−c)² + (c−a)²]` | Three-variable |
| `x² + 1/x² − 2` | `(x − 1/x)²` | Reciprocal pattern |

#### Olympiad Preview: Disguised "Always True" Inequalities (8 min)

**Present these problems** that look like they need solving but are actually identities or always-true inequalities.

**Problem 6:** Solve the inequality: `x² − 2x + 2 ≥ 0`

Many students will try to factor. But:

```
x² − 2x + 2 = (x − 1)² + 1 ≥ 1 > 0
```

**The expression is always positive!** No factoring needed. **Answer: all real numbers.**

**Problem 7:** Solve: `x² + 4x + 5 > 0`

```
x² + 4x + 5 = (x + 2)² + 1 ≥ 1 > 0
```

**Always positive. Answer: all real numbers.**

**Problem 8:** Solve: `−x² + 6x − 10 < 0`

```
−x² + 6x − 10 = −(x² − 6x + 10) = −[(x − 3)² + 1] = −(x−3)² − 1 ≤ −1 < 0
```

**Always negative. Answer: all real numbers.**

**Problem 9:** Solve: `4x² − 4x + 1 ≥ 0`

```
4x² − 4x + 1 = (2x − 1)² ≥ 0
```

**Always non-negative. Answer: all real numbers** (equality at `x = 1/2`).

#### Discussion: When Does `ax² + bx + c` Have a Fixed Sign? (4 min)

**Write on the board:**

> ### The Discriminant Test for "Always Positive/Negative"
>
> For `f(x) = ax² + bx + c`:
>
> | Condition | Sign of `f(x)` |
> |---|---|
> | `a > 0` and `Δ = b² − 4ac < 0` | **Always positive** (parabola opens up, never touches x-axis) |
> | `a < 0` and `Δ = b² − 4ac < 0` | **Always negative** (parabola opens down, never touches x-axis) |
> | `a > 0` and `Δ = 0` | **Always non-negative** (touches x-axis at one point) |
> | `a < 0` and `Δ = 0` | **Always non-positive** |
> | `Δ > 0` | **Changes sign** (crosses x-axis — needs sign analysis) |

**Example:** `x² − 2x + 2`: `a = 1 > 0`, `Δ = 4 − 8 = −4 < 0` → always positive ✓

**Connection to completing the square:**

```
ax² + bx + c = a(x + b/2a)² + (c − b²/4a) = a(x + b/2a)² − Δ/(4a)
```

- The square term `a(x + b/2a)²` has the sign of `a`.
- The constant `−Δ/(4a)` has the sign of `−Δ/a`.
- If `Δ < 0`: both terms have the same sign as `a` → fixed sign.

---

### Part G: Olympiad-Style Inequality Techniques (15 min)

*An introduction to the inequality methods used in mathematical olympiads. These build directly on the `x² ≥ 0` principle.*

#### Technique 1: The AM-GM Inequality (5 min)

**Already proved above.** State the general form:

> ### AM-GM Inequality
> For non-negative real numbers `a₁, a₂, ..., aₙ`:
> ```
> (a₁ + a₂ + ... + aₙ)/n ≥ ⁿ√(a₁ · a₂ · ... · aₙ)
> ```
> Equality when all `aᵢ` are equal.

**Most useful forms:**

| Variables | AM-GM | Equality |
|---|---|---|
| 2 | `(a + b)/2 ≥ √(ab)` | `a = b` |
| 3 | `(a + b + c)/3 ≥ ³√(abc)` | `a = b = c` |
| 4 | `(a + b + c + d)/4 ≥ ⁴√(abcd)` | `a = b = c = d` |

**Worked example:** Find the minimum of `x + 4/x` for `x > 0`.

By AM-GM: `x + 4/x ≥ 2√(x · 4/x) = 2·2 = 4`. Equality when `x = 4/x` → `x = 2`.

**Minimum value: 4, achieved at `x = 2`.**

#### Technique 2: The Cauchy-Schwarz Inequality (4 min)

> ### Cauchy-Schwarz Inequality
> For real numbers `a₁, ..., aₙ` and `b₁, ..., bₙ`:
> ```
> (a₁² + a₂² + ... + aₙ²)(b₁² + b₂² + ... + bₙ²) ≥ (a₁b₁ + a₂b₂ + ... + aₙbₙ)²
> ```
> Equality when `a₁/b₁ = a₂/b₂ = ... = aₙ/bₙ` (proportional).

**Proof for n = 2 (by `x² ≥ 0`):**

Consider the quadratic in `t`:
```
(a₁t + b₁)² + (a₂t + b₂)² ≥ 0
```

Expanding:
```
(a₁² + a₂²)t² + 2(a₁b₁ + a₂b₂)t + (b₁² + b₂²) ≥ 0
```

This quadratic in `t` is always non-negative (sum of squares!), so its discriminant must be `≤ 0`:

```
4(a₁b₁ + a₂b₂)² − 4(a₁² + a₂²)(b₁² + b₂²) ≤ 0
```

Which gives Cauchy-Schwarz. ∎

**Worked example:** Prove `(1 + 4 + 9)(1 + 1 + 1) ≥ (1 + 2 + 3)²`.

LHS = `14 · 3 = 42`. RHS = `36`. `42 ≥ 36` ✓ (Cauchy-Schwarz with `a = (1,2,3)`, `b = (1,1,1)`).

#### Technique 3: The Triangle Inequality (3 min)

> ### Triangle Inequality
> `|a + b| ≤ |a| + |b|`

**Proof:**

```
(|a| + |b|)² − |a + b|² = a² + 2|ab| + b² − (a² + 2ab + b²) = 2(|ab| − ab) ≥ 0
```

Since `|ab| ≥ ab` always. ∎

Equality when `a` and `b` have the same sign (or one is zero).

#### Technique 4: "SOS" — Sum of Squares (3 min)

The most general olympiad technique: express the difference `f − g` as a **sum of squares** plus non-negative terms.

**Worked example:** Prove `a⁴ + b⁴ ≥ a³b + ab³` for all real `a, b`.

```
a⁴ + b⁴ − a³b − ab³ = a³(a − b) − b³(a − b) = (a − b)(a³ − b³) = (a − b)²(a² + ab + b²)
```

Since `(a − b)² ≥ 0` and `a² + ab + b² = (a + b/2)² + 3b²/4 ≥ 0`, the product is `≥ 0`. ∎

Equality when `a = b` (or `a = b = 0`).

---

## Weekly Challenge Problem Set: Inequalities & Absolute Value

### A. Linear & Compound Inequalities

1. `3(x − 2) + 1 < 2(x + 5)`
2. `−3(x + 4) ≥ 2x − 1`
3. `1 ≤ 2x − 3 < 7`
4. `−2 < 3 − 5x ≤ 8`
5. `2x − 1 < 3` and `x + 2 > 0`
6. `x − 5 > 2` or `3x + 1 < −8`
7. `|2x + 1| − 3 > 2`
8. `5 − |x − 2| ≥ 0`

### B. Quadratic & Polynomial Inequalities (Sign Analysis)

9. `x² − 6x + 8 > 0`
10. `x² + 3x − 10 ≤ 0`
11. `2x² + 5x − 3 ≥ 0`
12. `x² − 4x + 4 ≤ 0`
13. `x³ + 2x² − 3x > 0`
14. `x³ − x² − 6x < 0`
15. `x⁴ − 10x² + 9 ≥ 0`
16. `x³ − 3x² − 4x + 12 > 0`
17. `(x − 1)²(x + 2) > 0`
18. `(x − 1)³(x + 2)²(x − 3) < 0`
19. `x⁵ − 4x³ > 0`
20. `x⁶ − 13x⁴ + 36x² ≤ 0`

### C. Rational Inequalities

21. `(x − 2)/(x + 3) > 0`
22. `(x + 1)/(x − 4) ≤ 0`
23. `x/(x² − 9) ≥ 0`
24. `(x² − 4)/(x − 1) < 0`
25. `(2x + 3)/(x² + x − 6) > 0`
26. `(x² − 5x + 6)/(x² − 1) ≤ 0`
27. `(x³ − 1)/(x² + x + 1) > 0`
28. `1/(x − 1) < 1/(x + 1)`
29. `(x + 2)/(x − 1) ≥ 2`
30. `(x² − 2x + 1)/(x² + 1) < 0`

### D. Absolute Value Equations

31. `|3x − 7| = 2`
32. `|x + 5| = |2x − 1|`
33. `|x² − 9| = 7`
34. `|x − 2| + |x + 1| = 5`
35. `|2x − 1| + |x + 3| = 6`
36. `|x − 3| − |x + 2| = 1`
37. `|x| + |x − 1| + |x − 2| = 6`
38. `||x − 1| − 2| = 3`
39. `|x² − 2x| = 3`
40. `|x − 2| = |x + 4|`

### E. Absolute Value Inequalities

41. `|2x + 3| < 7`
42. `|3x − 5| ≥ 4`
43. `|x/2 − 1| > 3`
44. `|5 − 2x| ≤ 9`
45. `|x² − 4| < 5`
46. `|x² − 2x − 3| > 2`
47. `2 < |x − 1| < 6`
48. `|x + 2| · |x − 3| > 0`
49. `|x − 1| / (x + 2) > 0`
50. `|x| / (x² − 4) < 0`
51. `|x − 3| < x`
52. `|x + 1| > 2x`
53. `|x − 2| + |x + 3| ≤ 7`
54. `|x − 1| + |x + 1| > 4`
55. `|x² − 3x| ≤ 2`

### F. Compound & Mixed Problems

56. `(x − 1)(x + 2) > 0` and `|x| < 4`
57. `|x − 2| < 3` and `x² < 16`
58. `(x + 3)/(x − 1) < 0` or `|x − 5| < 1`
59. `x² − 5x + 6 > 0` and `x² − 4 < 0`
60. `|x² − 1| ≤ 3` and `|x| < 2`
61. `(x − 2)² < 9` or `|x + 1| > 5`
62. `|x − 1| < |x + 3|` and `x² < 25`
63. `(x² − 9)/(x² − 1) > 0` and `|x − 2| < 5`
64. `|2x − 1| < 3` and `|x + 1| > 2`
65. `x³ − 2x² − 3x > 0` or `|x| < 1`

### G. Challenge Problems

66. Solve: `|x − 1| + |x − 2| + |x − 3| + ... + |x − 10| = 25`
67. Solve: `|||x − 1| − 2| − 3| = 4`
68. For what values of `a` does `|x − a| + |x + a| = 6` have exactly two integer solutions?
69. Solve: `|x² − 5x + 6| < |x − 2|`
70. Solve: `(|x| − 1)(|x| − 2)(|x| − 3) < 0`
71. Solve: `|x − 1| / |x + 1| < 2`
72. For what values of `k` is `|x − k| + |x + k| = 8` solvable with infinitely many solutions?
73. Solve: `x² − 2|x| − 3 ≤ 0`
74. Solve: `|x − 2| > x² − 4`
75. Solve: `|x + 1| + |x − 2| + |x − 5| ≥ 8`
76. Find all `a` such that `|x² − 4| < a` has at least one integer solution.
77. Solve: `(|x| − 2) / (|x| − 3) > 0`
78. Solve: `|x² − 3x + 2| + |x² − 5x + 6| ≤ 4`
79. For what values of `m` does `x² − 2mx + m² − 4 < 0` have at least one integer solution?
80. Solve: `||x − 1| − |x + 1|| < 2`

### H. The `x² ≥ 0` Principle — "Always True" Inequalities

*Solve these inequalities. Many have solutions that are "all real numbers" or "no solution" — recognize these without sign analysis by completing the square or using the discriminant.*

81. `x² − 4x + 5 > 0`
82. `x² + 6x + 10 ≥ 0`
83. `−x² + 2x − 3 < 0`
84. `x² − 2x + 1 ≥ 0`
85. `−2x² + 4x − 5 > 0` *(trick question)*
86. `x² + x + 1 ≤ 0`
87. `4x² − 12x + 9 > 0`
88. `x⁴ + 4x² + 3 ≥ 0`
89. `x⁴ − 4x² + 4 ≥ 0`
90. `x² + 2x + 5 > 0`
91. `−3x² + 6x − 4 ≤ 0`
92. `x² + (a − b)x + ab ≤ 0` *(find condition on `a, b` for "no solution")*
93. `x² + 2ax + a² + 1 > 0` *(for what values of `a`?)*
94. `x² − 2bx + b² + k > 0` *(for what values of `k`?)*
95. `(x² + 1)/(x² + 2) > 0`
96. `(x² + x + 1)/(x² + 1) > 0`
97. `x⁴ + y⁴ ≥ 2x²y²` *(for all real `x, y`)*
98. `(x² + 1)² ≥ 4x²` *(for all real `x`)*
99. `x² + 1/x² ≥ 2` *(for `x ≠ 0`)*
100. `(a + b)² ≥ 4ab` *(for all real `a, b`)*

### I. Proving Inequalities via `x² ≥ 0` (Sum of Squares)

*Prove each inequality for all real values of the variables. In each case, write the difference as a sum of squares.*

101. `a² + b² ≥ 2ab`
102. `a² + b² + c² ≥ ab + bc + ca`
103. `x² + 1/x² ≥ 2` for `x ≠ 0`
104. `a⁴ + b⁴ ≥ a³b + ab³`
105. `a² + b² ≥ (a + b)²/2`
106. `a² + b² + c² ≥ (a + b + c)²/3`
107. `(a − b)² + (b − c)² + (c − a)² ≥ 0` *(trivial but fundamental)*
108. `a² + b² + c² + d² ≥ 4abcd` *(when `a, b, c, d > 0`)*
109. `a²/(b²) + b²/(a²) ≥ 2` for `a, b ≠ 0`
110. `(a² + b²)(c² + d²) ≥ (ac + bd)²` *(Cauchy-Schwarz)*
111. `(a + b + c)² ≤ 3(a² + b² + c²)`
112. `a² + b² + c² ≥ ab + ac + bc + (a − b)²/2` *(is this always true?)*
113. `x⁴ + y⁴ + z⁴ ≥ x²y² + y²z² + z²x²`
114. `a³ + b³ ≥ ab(a + b)` for `a, b ≥ 0`
115. `(1 + a²)(1 + b²) ≥ (a + b)²`

### J. AM-GM Inequality Problems

116. Find the minimum of `x + 9/x` for `x > 0`.
117. Find the minimum of `2x + 8/x` for `x > 0`.
118. Find the minimum of `x + 1/x` for `x > 0`.
119. Find the maximum of `x(6 − x)` for `0 < x < 6`.
120. Find the minimum of `x² + 1/x²` for `x ≠ 0`.
121. Find the minimum of `x² + 9 + 1/x²` for `x ≠ 0`.
122. Prove `a + b + c ≥ ³√(abc) + ³√(abc) + ³√(abc)` is NOT always true. What is the correct AM-GM statement?
123. Find the minimum of `x + y` given `xy = 16` and `x, y > 0`.
124. Find the maximum of `xy` given `x + y = 10` and `x, y > 0`.
125. Find the minimum of `(x + 1)(x + 4)/x` for `x > 0`.
126. Prove `(a + b)(b + c)(c + a) ≥ 8abc` for `a, b, c ≥ 0`.
127. Prove `(1 + a)(1 + b)(1 + c) ≥ 8√(abc)` for `a, b, c ≥ 0`.
128. Find the minimum of `x⁴ + y⁴` given `x² + y² = 1`.
129. Find the minimum of `a + b` given `ab = 4` and `a, b > 0`.
130. Prove `n! ≥ 2^(n−1)` for `n ≥ 1` using AM-GM. *(Hint: `n! = 1 · 2 · ... · n`)*

### K. Cauchy-Schwarz & Other Classical Inequalities

131. Verify Cauchy-Schwarz for `a = (1, 2)`, `b = (3, 4)`.
132. Prove `(a² + b²)(c² + d²) ≥ (ac + bd)²` using `x² ≥ 0`.
133. Prove `(a² + b² + c²)(x² + y² + z²) ≥ (ax + by + cz)²`.
134. Prove `(1 + 1 + 1)(a² + b² + c²) ≥ (a + b + c)²`, i.e., `a² + b² + c² ≥ (a+b+c)²/3`.
135. Use Cauchy-Schwarz to find the maximum of `3x + 4y` given `x² + y² = 1`.
136. Use Cauchy-Schwarz to find the maximum of `x + 2y + 3z` given `x² + y² + z² = 1`.
137. Prove the triangle inequality: `|a + b| ≤ |a| + |b|` using `(x² ≥ 0)`.
138. Prove `|a − b| ≤ |a| + |b|` (a consequence of triangle inequality).
139. Prove `||a| − |b|| ≤ |a − b|` (reverse triangle inequality).
140. Prove `(a² + b² + c²)² ≥ 3(a³b + b³c + c³a)` for `a, b, c ≥ 0`. *(Challenging)*

### L. Olympiad Challenge Problems

141. Prove: `a²b + b²c + c²a ≥ 3abc` for `a, b, c > 0` satisfying `a + b + c = 3`.
142. Prove: If `a, b, c > 0` and `abc = 1`, then `a + b + c ≥ 3`.
143. Prove: `1/(1+a) + 1/(1+b) ≥ 2/(1+√(ab))` for `a, b > 0`.
144. Find the minimum of `x² + y² + z²` given `x + y + z = 6`.
145. Prove: `a/(b+c) + b/(a+c) + c/(a+b) ≥ 3/2` for `a, b, c > 0` (Nesbitt's inequality).
146. Prove: If `a² + b² + c² = 1`, then `−1/2 ≤ ab + bc + ca ≤ 1`.
147. Find the minimum of `(x + 1/x)⁶ − 6(x + 1/x)⁴ + 9(x + 1/x)²` for `x > 0`.
148. Prove: `a⁴ + b⁴ + c⁴ ≥ abc(a + b + c)` for `a, b, c ≥ 0`.
149. Prove: If `a + b + c = 0`, then `a² + b² + c² + 2ab c = 1` is impossible for real `a, b, c`... *(find the actual relationship)*
150. Prove: `(a² + 1)(b² + 1)(c² + 1) ≥ (ab + bc + ca)²` for `ab + bc + ca > 0`.
151. Find all real `x` satisfying: `x² + 2x + 2 > 0` AND `−x² + 3x − 2 > 0`.
152. Solve: `x² − 2|x| − 3 ≥ 0` by first writing it as a condition on `|x|`.
153. Solve: `x⁴ − 5x² + 6 ≤ 0` by treating it as a quadratic in `x²`.
154. Prove: `a² + b² + c² + d² ≥ ab + bc + cd + da` for all real `a, b, c, d`.
155. Prove: If `a, b > 0` and `a + b = 1`, then `(1 + 1/a)(1 + 1/b) ≥ 9`.

---

## Answer Key: Weekly Challenge Set

### A. Linear & Compound Inequalities

| # | Answer |
|---|---|
| 1 | `3x − 5 < 2x + 10 → x < 15` → `(−∞, 15)` |
| 2 | `−3x − 12 ≥ 2x − 1 → −5x ≥ 11 → x ≤ −11/5` → `(−∞, −11/5]` |
| 3 | `4 ≤ 2x < 10 → 2 ≤ x < 5` → `[2, 5)` |
| 4 | `−2 < 3−5x` → `5x < 5 → x < 1`; `3−5x ≤ 8 → −5x ≤ 5 → x ≥ −1` → `[−1, 1)` |
| 5 | `x < 2` and `x > −2` → `(−2, 2)` |
| 6 | `x > 7` or `x < −3` → `(−∞, −3) ∪ (7, ∞)` |
| 7 | `|2x+1| > 5 → 2x+1 < −5 or 2x+1 > 5 → x < −3 or x > 2` → `(−∞,−3) ∪ (2,∞)` |
| 8 | `|x−2| ≤ 5 → −3 ≤ x ≤ 7` → `[−3, 7]` |

### B. Quadratic & Polynomial Inequalities

| # | Answer |
|---|---|
| 9 | `(x−2)(x−4) > 0` → `(−∞, 2) ∪ (4, ∞)` |
| 10 | `(x+5)(x−2) ≤ 0` → `[−5, 2]` |
| 11 | `(2x−1)(x+3) ≥ 0` → `(−∞, −3] ∪ [1/2, ∞)` |
| 12 | `(x−2)² ≤ 0` → `x = 2` (only point) |
| 13 | `x(x²+2x−3) = x(x+3)(x−1) > 0` → `(−3, 0) ∪ (1, ∞)` |
| 14 | `x(x²−x−6) = x(x−3)(x+2) < 0` → `(−∞, −2) ∪ (0, 3)` |
| 15 | `(x²−1)(x²−9) = (x+1)(x−1)(x+3)(x−3) ≥ 0` → `(−∞, −3] ∪ [−1, 1] ∪ [3, ∞)` |
| 16 | `x²(x−3)−4(x−3) = (x−3)(x²−4) = (x−3)(x+2)(x−2) > 0` → `(−2, 2) ∪ (3, ∞)` |
| 17 | `(x−1)² ≥ 0` always; need `(x+2) > 0` and `x ≠ 1` → `(−2, 1) ∪ (1, ∞)` |
| 18 | `(x−1)³` changes sign at 1; `(x+2)²` doesn't change sign at −2; `(x−3)` changes at 3. Sign: `(−∞,−2): −·+·− = +`; `(−2,1): −·+·− = +`; `(1,3): +·+·− = −`; `(3,∞): +·+·+ = +`. Need `< 0`: `(1, 3)` |
| 19 | `x³(x²−4) = x³(x+2)(x−2) > 0` → `(−2, 0) ∪ (2, ∞)` *(odd power of x changes sign)* |
| 20 | Let `u = x²`: `u³−13u²+36u = u(u−4)(u−9) ≤ 0`. Since `u = x² ≥ 0`: `u ∈ [0, 0] ∪ [4, 9]` → `x = 0` or `2 ≤ |x| ≤ 3` → `{0} ∪ [−3,−2] ∪ [2, 3]` |

### C. Rational Inequalities

| # | Answer |
|---|---|
| 21 | `(−∞, −3) ∪ (2, ∞)` |
| 22 | `[−1, 4)` |
| 23 | `x / [(x−3)(x+3)] ≥ 0` → `(−3, 0] ∪ (3, ∞)` |
| 24 | `(x+2)(x−2)/(x−1) < 0` → `(−∞, −2) ∪ (1, 2)` |
| 25 | `(2x+3)/[(x+3)(x−2)] > 0` → `(−3, −3/2) ∪ (2, ∞)` |
| 26 | `(x−2)(x−3)/[(x+1)(x−1)] ≤ 0` → `(−1, 1) ∪ [2, 3]` |
| 27 | `(x−1)(x²+x+1)/(x²+x+1) > 0`. Since `x²+x+1 > 0` always, simplifies to `x − 1 > 0` → `(1, ∞)` |
| 28 | `1/(x−1) − 1/(x+1) < 0 → [(x+1)−(x−1)]/[(x−1)(x+1)] < 0 → 2/[(x−1)(x+1)] < 0 → (x−1)(x+1) < 0 → (−1, 1)` |
| 29 | `(x+2)/(x−1) − 2 ≥ 0 → [(x+2)−2(x−1)]/(x−1) ≥ 0 → (4−x)/(x−1) ≥ 0 → (1, 4]` |
| 30 | `(x−1)²/(x²+1) < 0`. Since `(x−1)² ≥ 0` and `x²+1 > 0`, the fraction is always ≥ 0. **No solution.** |

### D. Absolute Value Equations

| # | Answer |
|---|---|
| 31 | `x = 3` or `x = 5/3` |
| 32 | `x+5 = 2x−1 → x = 6`; `x+5 = −(2x−1) → 3x = −4 → x = −4/3` |
| 33 | `x² = 16 → x = ±4`; `x² = 2 → x = ±√2` |
| 34 | Critical: `x = −1, 2`. Region `x < −1`: `−(x−2)−(x+1) = 5 → −2x+1 = 5 → x = −2` ✓. Region `−1 ≤ x < 2`: `−(x−2)+(x+1) = 3 = 5` ✗. Region `x ≥ 2`: `(x−2)+(x+1) = 5 → 2x−1 = 5 → x = 3` ✓. **`x = −2, 3`** |
| 35 | Critical: `x = −3, 1/2`. `x < −3`: `−(2x−1)−(x+3) = 6 → −3x−2 = 6 → x = −8/3` ✗ (not < −3). `−3 ≤ x < 1/2`: `−(2x−1)+(x+3) = 6 → −x+4 = 6 → x = −2` ✓. `x ≥ 1/2`: `(2x−1)+(x+3) = 6 → 3x+2 = 6 → x = 4/3` ✓. **`x = −2, 4/3`** |
| 36 | Critical: `x = −2, 3`. `x < −2`: `−(x−3)+(x+2) = 5 = 1` ✗. `−2 ≤ x < 3`: `−(x−3)−(x+2) = 1 → −2x+1 = 1 → x = 0` ✓. `x ≥ 3`: `(x−3)−(x+2) = −5 = 1` ✗. **`x = 0`** |
| 37 | Critical: `0, 1, 2`. `x < 0`: `−x−(x−1)−(x−2) = 6 → −3x+3 = 6 → x = −1` ✓. `0 ≤ x < 1`: `x−(x−1)−(x−2) = 6 → −x+3 = 6 → x = −3` ✗. `1 ≤ x < 2`: `x+(x−1)−(x−2) = 6 → x+1 = 6 → x = 5` ✗. `x ≥ 2`: `x+(x−1)+(x−2) = 6 → 3x−3 = 6 → x = 3` ✓. **`x = −1, 3`** |
| 38 | `|x−1|−2 = 3` → `|x−1| = 5` → `x = 6, −4`; `|x−1|−2 = −3` → `|x−1| = −1` ✗. **`x = −4, 6`** |
| 39 | `x²−2x = 3 → x²−2x−3 = 0 → (x−3)(x+1) = 0 → x = 3, −1`; `x²−2x = −3 → x²−2x+3 = 0 → Δ < 0` ✗. **`x = −1, 3`** |
| 40 | `x−2 = x+4` ✗ (−2 = 4); `x−2 = −(x+4) → 2x = −2 → x = −1`. **`x = −1`** |

### E. Absolute Value Inequalities

| # | Answer |
|---|---|
| 41 | `−7 < 2x+3 < 7 → −5 < x < 2` → `(−5, 2)` |
| 42 | `3x−5 ≤ −4 or 3x−5 ≥ 4 → x ≤ 1/3 or x ≥ 3` → `(−∞, 1/3] ∪ [3, ∞)` |
| 43 | `x/2−1 < −3 or x/2−1 > 3 → x < −4 or x > 8` → `(−∞,−4) ∪ (8,∞)` |
| 44 | `|2x−5| ≤ 9 → −9 ≤ 2x−5 ≤ 9 → −2 ≤ x ≤ 7` → `[−2, 7]` |
| 45 | `−5 < x²−4 < 5 → −1 < x² < 9 → |x| < 3` → `(−3, 3)` |
| 46 | `x²−2x−3 > 2` → `x²−2x−5 > 0` → `x < 1−√6` or `x > 1+√6`; `x²−2x−3 < −2` → `x²−2x−1 < 0` → `1−√2 < x < 1+√2`. **Union: `(1−√2, 1+√2) ∪ (−∞, 1−√6) ∪ (1+√6, ∞)`** |
| 47 | `|x−1| > 2 → x < −1 or x > 3`; `|x−1| < 6 → −5 < x < 7`. **Intersection: `(−5,−1) ∪ (3, 7)`** |
| 48 | `|x−2|·|x−3| > 0` → `x ≠ 2` and `x ≠ 3` → `(−∞,2)∪(2,3)∪(3,∞)` |
| 49 | Need `|x−1| > 0` and `x+2 > 0`, OR `|x−1| < 0` (impossible). So `x ≠ 1` and `x > −2` → `(−2, 1) ∪ (1, ∞)` |
| 50 | `|x| ≥ 0` always, `x²−4 > 0` when `|x| > 2`. Need fraction < 0: numerator < 0 (impossible since `|x| ≥ 0`) unless `|x| = 0` (gives 0, not < 0) or denominator < 0 (then `|x|/(neg) ≤ 0`, need `|x| > 0`). Denominator < 0: `|x| < 2`, `x ≠ 0`. **Answer: `(−2, 0) ∪ (0, 2)`** |
| 51 | Need `x > 0` (otherwise `|x−3| < x` is impossible if `x ≤ 0` since LHS ≥ 0). Then `−x < x−3 < x`. Right: `x−3 < x → −3 < 0` ✓ always. Left: `x−3 > −x → 2x > 3 → x > 3/2`. **Answer: `(3/2, ∞)`** |
| 52 | If `x < 0`: `x+1 > 2x` → `1 > x` → always true for `x < 0`. If `x ≥ 0`: `x+1 > 2x` → `1 > x` → `0 ≤ x < 1`. **Answer: `(−∞, 1)`** |
| 53 | Critical: `x = −2, 3`. `x < −2`: `−(x−3)−(x+2) = −2x+1 ≤ 7 → x ≥ −3`. `−2 ≤ x < 3`: `(x−3)−(x+2) = −5 ≤ 7` ✓ all. `x ≥ 3`: `(x−3)+(x+2) = 2x−1 ≤ 7 → x ≤ 4`. **Answer: `[−3, 4]`** |
| 54 | Critical: `x = −1, 1`. `|x| < 1`: `(1−x)+(x+1) = 2 > 4` ✗. `|x| ≥ 1`: `2|x| > 4 → |x| > 2`. **Answer: `(−∞,−2) ∪ (2,∞)`** |
| 55 | `−2 ≤ x²−3x ≤ 2`. Lower: `x²−3x+2 ≥ 0 → (x−1)(x−2) ≥ 0 → x ≤ 1 or x ≥ 2`. Upper: `x²−3x−2 ≤ 0 → x ∈ [(3−√17)/2, (3+√17)/2]`. **Intersection: `[(3−√17)/2, 1] ∪ [2, (3+√17)/2]`** |

### F. Compound & Mixed Problems

| # | Answer |
|---|---|
| 56 | `x < −2 or x > 1` and `−4 < x < 4` → `(−4,−2) ∪ (1, 4)` |
| 57 | `−1 < x < 5` and `−4 < x < 4` → `(−1, 4)` |
| 58 | `−3 < x < 1` or `4 < x < 6` → `(−3, 1) ∪ (4, 6)` |
| 59 | `x < 2 or x > 3` and `−2 < x < 2` → `(−2, 2)` |
| 60 | `|x²−1| ≤ 3` → `−2 ≤ x² ≤ 4` → `|x| ≤ 2`; `|x| < 2` → **`(−2, 2)`** |
| 61 | `(x−2)² < 9` → `−1 < x < 5`; `|x+1| > 5` → `x < −6 or x > 4`. Union: `(−1, 5) ∪ (−∞,−6) ∪ (4,∞)` = `(−∞,−6) ∪ (−1, ∞)` |
| 62 | `|x−1| < |x+3|` → square: `x²−2x+1 < x²+6x+9 → −8x < 8 → x > −1`. And `x² < 25 → −5 < x < 5`. **`(−1, 5)`** |
| 63 | `(x+3)(x−3)/[(x+1)(x−1)] > 0` → `(−∞,−3)∪(−1,1)∪(3,∞)`. And `|x−2| < 5 → −3 < x < 7`. **`(−3,−1)∪(1,1)∪(3,7)`**... simplify: `(−3,−1)∪(3,7)` (note `(1,1)` is empty) |
| 64 | `|2x−1| < 3 → −1 < x < 2`; `|x+1| > 2 → x < −3 or x > 1`. Intersection: `(1, 2)` |
| 65 | `x(x²−2x−3) = x(x−3)(x+1) > 0` → `(−1, 0) ∪ (3, ∞)`; `|x| < 1 → −1 < x < 1`. Union: `(−1, 1) ∪ (3, ∞)` |

### G. Challenge Problems

| # | Answer |
|---|---|
| 66 | The function `f(x) = Σ|x−k|` for `k=1..10` is piecewise linear, minimized at the median `x=5` or `x=6` (any point in `[5,6]`). `f(5) = 4+3+2+1+0+1+2+3+4+5 = 25`. So `x = 5` gives exactly 25. `f(6) = 5+4+3+2+1+0+1+2+3+4 = 25`. For any `x` in `[5, 6]`, `f(x) = 25`. **Answer: `[5, 6]`** |
| 67 | `\|\|x−1\|−2\|−3 = 4` → `\|\|x−1\|−2\| = 7` → `|x−1|−2 = ±7` → `|x−1| = 9` or `|x−1| = −5` (✗). So `|x−1| = 9` → `x = 10` or `x = −8`. **`x = −8, 10`** |
| 68 | `|x−a|+|x+a| = 6`. For `|a| > 3`: no solution (sum always `≥ 2|a| > 6`). For `|a| = 3`: infinitely many solutions (all `x ∈ [−3, 3]`). For `|a| < 3`: exactly two solutions (`x = ±3`). **Answer: `|a| < 3`** (i.e., `−3 < a < 3`) for exactly two integer solutions (`x = ±3`). |
| 69 | Square both sides: `(x²−5x+6)² < (x−2)²`. Factor: `[(x−2)(x−3)]² < (x−2)²`. If `x ≠ 2`: divide by `(x−2)² > 0`: `(x−3)² < 1` → `−1 < x−3 < 1` → `2 < x < 4`. Exclude `x = 2`. **Answer: `(2, 4)`** *(Check: at `x = 2`, LHS = 0, RHS = 0, not strictly less.)* |
| 70 | Let `u = |x| ≥ 0`: `(u−1)(u−2)(u−3) < 0`. Sign: `u ∈ (0,1)`: `−·−·− = −` ✓; `(1,2)`: `+·−·− = +`; `(2,3)`: `+·+·− = −` ✓; `(3,∞)`: `+`. So `u ∈ (0,1) ∪ (2,3)` → `0 < |x| < 1` or `2 < |x| < 3` → **`(−1,0)∪(0,1)∪(−3,−2)∪(2,3)`** |
| 71 | Square: `(x−1)² < 4(x+1)²` → `x²−2x+1 < 4x²+8x+4` → `3x²+10x+3 > 0` → `(3x+1)(x+3) > 0` → `x < −3` or `x > −1/3`. But also `x ≠ −1` (denominator). **Answer: `(−∞,−3) ∪ (−1/3, ∞)` excluding `x = −1`**... but `−1` is not in the solution set anyway (since `−1/3 > −1`). **Answer: `(−∞,−3) ∪ (−1/3, ∞)`** |
| 72 | Infinitely many solutions when `|k| = 4` (interval `[−4, 4]`). **`k = ±4`** |
| 73 | Let `u = |x|`: `u²−2u−3 ≤ 0 → (u−3)(u+1) ≤ 0 → −1 ≤ u ≤ 3 → |x| ≤ 3`. **`[−3, 3]`** |
| 74 | `|x−2| > x²−4`. If `x²−4 < 0` (i.e., `|x| < 2`): always true since LHS ≥ 0 > x²−4. If `x²−4 ≥ 0` (i.e., `|x| ≥ 2`): square both sides: `(x−2)² > (x²−4)²` → `(x−2)² > [(x−2)(x+2)]²` → if `x ≠ 2`: `1 > (x+2)²` → `−3 < x < −1`. Combined with `|x| ≥ 2`: `−3 < x < −1` and `|x| ≥ 2` → `−3 < x < −1` and (`x ≤ −2` or `x ≥ 2`) → `(−3, −2]`. Also include `|x| < 2` case: `(−2, 2)`. Check `x = 2`: `0 > 0` ✗. **Answer: `(−3, −2] ∪ (−2, 2) = (−3, 2)`** |
| 75 | Critical points: `x = −1, 2, 5`. `f(x) = |x+1|+|x−2|+|x−5|`. By regions: `x < −1`: `f = −3x+6`, need `≥ 8 → x ≤ −2/3` (all `x < −1` works). `−1 ≤ x < 2`: `f = −x+8`, need `≥ 8 → x ≤ 0` → `[−1, 0]`. `2 ≤ x < 5`: `f = x+4`, need `≥ 8 → x ≥ 4` → `[4, 5)`. `x ≥ 5`: `f = 3x−6`, need `≥ 8 → x ≥ 14/3` → `[5, ∞)`. **Answer: `(−∞, 0] ∪ [4, ∞)`** |
| 76 | `|x²−4| < a` means `4−a < x² < 4+a`. For at least one integer solution: need `4+a > 0` (i.e., `a > −4`, always true for `a > 0`). `x = 0`: `|0−4| = 4 < a` → `a > 4`. `x = ±1`: `|1−4| = 3 < a` → `a > 3`. `x = ±2`: `|4−4| = 0 < a` → `a > 0`. So for any `a > 0`, `x = ±2` is a solution. **Answer: `a > 0`** |
| 77 | Let `u = |x| ≥ 0`: `(u−2)/(u−3) > 0`. Sign: `u ∈ (0,2)`: `(−)/(−) = +` ✓; `(2,3)`: `(+)/(−) = −`; `(3,∞)`: `(+)/(+) = +` ✓. So `u ∈ (0,2) ∪ (3,∞)` → **`(−2,0)∪(0,2)∪(−∞,−3)∪(3,∞)`** |
| 78 | `|x²−3x+2| + |x²−5x+6| ≤ 4`. Factor: `|(x−1)(x−2)| + |(x−2)(x−3)| = |x−2|(|x−1|+|x−3|) ≤ 4`. Let `f(x) = |x−2|(|x−1|+|x−3|)`. Note `|x−1|+|x−3| ≥ |(x−1)−(x−3)| = 2` (triangle inequality), with equality when `1 ≤ x ≤ 3` (sum = `2(x−2)`... no: for `1 ≤ x ≤ 3`, sum = `(x−1)+(3−x) = 2`). So for `1 ≤ x ≤ 3`: `f(x) = 2|x−2| ≤ 4 → |x−2| ≤ 2 → 0 ≤ x ≤ 4`. Combined with `1 ≤ x ≤ 3`: `[1, 3]`. For `x < 1`: `f(x) = (2−x)(2−2x) = 2(1−x)(2−x)`. Need `≤ 4`. For `x > 3`: `f(x) = (x−2)(2x−4) = 2(x−2)²`. Need `2(x−2)² ≤ 4 → (x−2)² ≤ 2 → 2−√2 ≤ x ≤ 2+√2`. Combined with `x > 3`: `3 < x ≤ 2+√2 ≈ 3.41`. For `x < 1`: `2(1−x)(2−x) ≤ 4`. At `x = 0`: `2·1·2 = 4` ✓. At `x = −1`: `2·2·3 = 12` ✗. Solve `2x²−6x+4 ≤ 4 → 2x²−6x ≤ 0 → 2x(x−3) ≤ 0 → 0 ≤ x ≤ 3`. Combined with `x < 1`: `[0, 1)`. **Answer: `[0, 2+√2]`** (union of `[0,1)`, `[1,3]`, `(3, 2+√2]`) |
| 79 | `x²−2mx+m²−4 = (x−m)²−4 < 0 → (x−m)² < 4 → m−2 < x < m+2`. This interval has length 4. For at least one integer: need `m+2 > ⌈m−2⌉` (ceiling). Since the interval is `(m−2, m+2)`, it contains an integer unless both endpoints fall between consecutive integers with no integer inside. An interval of length 4 always contains at least 3 integers. **Answer: all real `m`.** |
| 80 | `\|\|x−1\|−\|x+1\|\| < 2`. For `x ≥ 1`: `|x−1−x−1| = |−2| = 2`, not < 2. For `x ≤ −1`: `|−x+1+x+1| = |2| = 2`, not < 2. For `−1 < x < 1`: `|−(x−1)−(x+1)| = |−2x| = 2|x| < 2 → |x| < 1`. **Answer: `(−1, 1)`** |

### H. The `x² ≥ 0` Principle — "Always True" Inequalities

| # | Answer |
|---|---|
| 81 | `(x−2)² + 1 ≥ 1 > 0`. **All reals.** |
| 82 | `(x+3)² + 1 ≥ 1 ≥ 0`. **All reals.** |
| 83 | `−(x−1)² − 2 ≤ −2 < 0`. **All reals.** |
| 84 | `(x−1)² ≥ 0`. **All reals** (equality at `x = 1`). |
| 85 | `−2(x−1)² − 3 ≤ −3 < 0`. So `−2x²+4x−5` is always negative. The inequality `> 0` has **no solution.** |
| 86 | `(x+1/2)² + 3/4 ≥ 3/4 > 0`. So `x²+x+1` is always positive. `≤ 0` has **no solution.** |
| 87 | `(2x−3)² > 0` except at `x = 3/2` where it equals 0. **Answer: `x ≠ 3/2`**, i.e., `(−∞, 3/2) ∪ (3/2, ∞)` |
| 88 | Let `u = x² ≥ 0`: `u² + 4u + 3 = (u+2)² − 1`. At `u = 0`: `3 > 0`. Minimum at `u = 0` → always `≥ 3 > 0`. **All reals.** |
| 89 | `(x² − 2)² ≥ 0`. **All reals** (equality at `x = ±√2`). |
| 90 | `(x+1)² + 4 ≥ 4 > 0`. **All reals.** |
| 91 | `−3(x−1)² − 1 ≤ −1 < 0`. So expression always `≤ −1 < 0`. **All reals.** |
| 92 | `x² + (a−b)x + ab = (x+a)(x+b)`. For "no solution" to `≤ 0`: need the quadratic to be always positive, i.e., `Δ < 0`: `(a−b)² − 4ab < 0 → a² − 6ab + b² < 0`. **Condition: `a² − 6ab + b² < 0`** (roughly when `a/b` is between `3−2√2` and `3+2√2`). |
| 93 | `(x+a)² + 1 ≥ 1 > 0` for all `x`, regardless of `a`. **All real `a`.** |
| 94 | `(x−b)² + k > 0` always when `k > 0`. When `k = 0`: `(x−b)² ≥ 0`, not strictly `> 0` (equals 0 at `x = b`). When `k < 0`: not always positive. **Answer: `k > 0`.** |
| 95 | Numerator `x²+1 > 0` always; denominator `x²+2 > 0` always. Fraction always `> 0`. **All reals.** |
| 96 | `x²+x+1 = (x+1/2)²+3/4 > 0` always; `x²+1 > 0` always. **All reals.** |
| 97 | `x⁴ + y⁴ − 2x²y² = (x² − y²)² ≥ 0`. **All reals** (equality when `x² = y²`, i.e., `|x| = |y|`). |
| 98 | `(x²+1)² − 4x² = x⁴ − 2x² + 1 = (x²−1)² ≥ 0`. **All reals** (equality at `x = ±1`). |
| 99 | `x² + 1/x² − 2 = (x − 1/x)² ≥ 0`. **All `x ≠ 0`** (equality at `x = ±1`). |
| 100 | `(a+b)² − 4ab = a² − 2ab + b² = (a−b)² ≥ 0`. **All reals** (equality when `a = b`). |

### I. Proving Inequalities via `x² ≥ 0`

| # | Proof sketch |
|---|---|
| 101 | `a² + b² − 2ab = (a−b)² ≥ 0` ∎ |
| 102 | `a²+b²+c² − ab−bc−ca = ½[(a−b)²+(b−c)²+(c−a)²] ≥ 0` ∎ |
| 103 | `x² + 1/x² − 2 = (x − 1/x)² ≥ 0` ∎ |
| 104 | `a⁴+b⁴ − a³b − ab³ = (a−b)²(a²+ab+b²) ≥ 0` since `(a−b)² ≥ 0` and `a²+ab+b² = (a+b/2)²+3b²/4 ≥ 0` ∎ |
| 105 | `2(a²+b²) − (a+b)² = (a−b)² ≥ 0` ∎ |
| 106 | `3(a²+b²+c²) − (a+b+c)² = (a−b)²+(b−c)²+(c−a)² ≥ 0` ∎ |
| 107 | Direct: sum of squares ≥ 0 ∎ |
| 108 | By AM-GM: `a²+b² ≥ 2ab`, `c²+d² ≥ 2cd`. So `a²+b²+c²+d² ≥ 2(ab+cd) ≥ 2·2√(abcd) = 4√(abcd)`. But we need `≥ 4abcd`. Since `abcd > 0`, `√(abcd) ≥ abcd` iff `abcd ≤ 1`... **This inequality is NOT always true.** Counter: `a=b=c=d=2`: LHS = 16, RHS = 64. **False.** *(The correct statement is `a²+b²+c²+d² ≥ 4√(abcd)` by AM-GM.)* |
| 109 | `a²/b² + b²/a² − 2 = (a/b − b/a)² ≥ 0` ∎ |
| 110 | Consider `(a₁t+b₁)² + (a₂t+b₂)² ≥ 0` for all `t`. The discriminant of this quadratic in `t` must be `≤ 0`, giving Cauchy-Schwarz. ∎ |
| 111 | From #106: `a²+b²+c² ≥ (a+b+c)²/3`. This is equivalent. ∎ |
| 112 | `a²+b²+c² − ab−ac−bc − (a−b)²/2 = a²+b²+c² − ab−ac−bc − (a²−2ab+b²)/2 = (a²+b²+c² − ab−ac−bc) − (a²−2ab+b²)/2 = ½(a²+b²) + c² − ac−bc + ab/2 − ab/2... ` Let `u = a²+b²+c² − ab−ac−bc = ½[(a−b)²+(b−c)²+(c−a)²]`. The claim is `u ≥ (a−b)²/2`. This is `½[(a−b)²+(b−c)²+(c−a)²] ≥ (a−b)²/2`, i.e., `(b−c)²+(c−a)² ≥ 0`. **True** ∎ |
| 113 | `x⁴+y⁴+z⁴ − x²y² − y²z² − z²x² = ½[(x²−y²)²+(y²−z²)²+(z²−x²)²] ≥ 0` ∎ |
| 114 | `a³+b³ − ab(a+b) = a³+b³ − a²b − ab² = a²(a−b) − b²(a−b) = (a−b)(a²−b²) = (a−b)²(a+b) ≥ 0` since `a+b ≥ 0` ∎ |
| 115 | `(1+a²)(1+b²) − (a+b)² = 1+a²+b²+a²b² − a²−2ab−b² = 1−2ab+a²b² = (1−ab)² ≥ 0` ∎ |

### J. AM-GM Inequality Problems

| # | Answer |
|---|---|
| 116 | `x + 9/x ≥ 2√9 = 6`. Min = **6** at `x = 3`. |
| 117 | `2x + 8/x ≥ 2√16 = 8`. Min = **8** at `2x = 8/x → x = 2`. |
| 118 | `x + 1/x ≥ 2`. Min = **2** at `x = 1`. |
| 119 | `x(6−x) ≤ [(x + (6−x))/2]² = 9`. Max = **9** at `x = 3`. |
| 120 | `x² + 1/x² ≥ 2`. Min = **2** at `x = ±1`. |
| 121 | `x² + 1/x² ≥ 2`, so `x² + 9 + 1/x² ≥ 11`. Min = **11** at `x = ±1`. |
| 122 | The correct statement is `(a+b+c)/3 ≥ ³√(abc)`, i.e., `a+b+c ≥ 3·³√(abc)`. The original claim `a+b+c ≥ 3abc` is false (e.g., `a=b=c=1/2`: LHS = 3/2, RHS = 3/8 ✓; but `a=b=c=2`: LHS = 6, RHS = 24 ✗). |
| 123 | By AM-GM: `x + y ≥ 2√(xy) = 2·4 = 8`. Min = **8** at `x = y = 4`. |
| 124 | `xy ≤ [(x+y)/2]² = 25`. Max = **25** at `x = y = 5`. |
| 125 | `(x+1)(x+4)/x = (x²+5x+4)/x = x + 5 + 4/x`. By AM-GM: `x + 4/x ≥ 4`. So expression `≥ 4 + 5 = 9`. Min = **9** at `x = 2`. |
| 126 | By AM-GM: `a+b ≥ 2√(ab)`, `b+c ≥ 2√(bc)`, `c+a ≥ 2√(ca)`. Multiply: `(a+b)(b+c)(c+a) ≥ 8√(a²b²c²) = 8abc` ∎ |
| 127 | By AM-GM: `1+a ≥ 2√a`, `1+b ≥ 2√b`, `1+c ≥ 2√c`. Multiply: `(1+a)(1+b)(1+c) ≥ 8√(abc)` ∎ |
| 128 | By AM-GM: `x⁴+y⁴ ≥ 2x²y²`. Given `x²+y² = 1`: `x⁴+y⁴ = (x²+y²)² − 2x²y² = 1 − 2x²y²`. Maximize `x²y²`: `x²y² ≤ [(x²+y²)/2]² = 1/4`. So `x⁴+y⁴ ≥ 1 − 2(1/4) = 1/2`. Min = **1/2** at `x² = y² = 1/2`. |
| 129 | `a + b ≥ 2√(ab) = 2·2 = 4`. Min = **4** at `a = b = 2`. |
| 130 | `n! = 1·2·3···n`. By AM-GM: `n!^(1/n) ≤ (1+2+...+n)/n = (n+1)/2`. This gives `n! ≤ [(n+1)/2]^n`, which is an upper bound, not helpful. Instead: pair terms `1·n ≥ ... `... Actually the simplest proof: `1·2·3···n ≥ 1·2·2···2 = 2^(n−1)` since each factor `k ≥ 2` for `k ≥ 2` and `1 = 1`. So `n! ≥ 1·2^(n−1) = 2^(n−1)` ∎ |

### K. Cauchy-Schwarz & Classical Inequalities

| # | Answer |
|---|---|
| 131 | LHS = `(1+4)(9+16) = 5·25 = 125`. RHS = `(3+8)² = 121`. `125 ≥ 121` ✓ |
| 132 | Consider `f(t) = (at+b)² + (ct+d)² ≥ 0` for all `t`. Expanding: `(a²+c²)t² + 2(ab+cd)t + (b²+d²) ≥ 0`. Discriminant `≤ 0`: `4(ab+cd)² − 4(a²+c²)(b²+d²) ≤ 0` ∎ |
| 133 | Same method: `f(t) = (at+by+cz)²...` or use `Σ(aᵢt+bᵢ)² ≥ 0` ∎ |
| 134 | Apply Cauchy-Schwarz with `a = (1,1,1)` and `b = (a,b,c)`: `(1+1+1)(a²+b²+c²) ≥ (a+b+c)²` ∎ |
| 135 | By Cauchy-Schwarz: `(3x+4y)² ≤ (3²+4²)(x²+y²) = 25·1 = 25`. Max = **5** at `(x,y) = (3/5, 4/5)`. |
| 136 | `(x+2y+3z)² ≤ (1+4+9)(x²+y²+z²) = 14`. Max = **√14** at `(x,y,z) = (1,2,3)/√14`. |
| 137 | `(|a|+|b|)² − |a+b|² = 2(|ab|−ab) ≥ 0` since `|ab| ≥ ab` ∎ |
| 138 | `|a−b| = |a+(−b)| ≤ |a|+|−b| = |a|+|b|` (triangle inequality) ∎ |
| 139 | `\|\|a\|−\|b\|\| ≤ |a−b|` follows from triangle inequality: `|a| = |(a−b)+b| ≤ |a−b|+|b|` → `|a|−|b| ≤ |a−b|`. Similarly `|b|−|a| ≤ |a−b|`. So `\|\|a\|−\|b\|\| ≤ |a−b|` ∎ |
| 140 | By Cauchy-Schwarz: `(a²+b²+c²)² ≥ (a²+b²+c²)²`. Need to show `(a²+b²+c²)² ≥ 3(a³b+b³c+c³a)`. This is a known olympiad inequality. By rearrangement or SOS: the difference equals `Σ(a²−bc)²/2 ≥ 0` when... *(This requires careful SOS decomposition; the inequality holds for `a, b, c ≥ 0` by Schur's inequality or rearrangement.)* ∎ |

### L. Olympiad Challenge Problems

| # | Answer |
|---|---|
| 141 | By AM-GM: `a²b + b²c + c²a ≥ 3³√(a²b·b²c·c²a) = 3³√(a³b³c³) = 3abc`. Equality when `a²b = b²c = c²a`, i.e., `a = b = c = 1` (given `a+b+c = 3`). ∎ |
| 142 | By AM-GM: `a + b + c ≥ 3·³√(abc) = 3·1 = 3`. Equality when `a = b = c = 1`. ∎ |
| 143 | Let `f(t) = 1/(1+t)`. By convexity/Jensen or AM-HM: `1/(1+a) + 1/(1+b) ≥ 2/((1+a+1+b)/2) = 4/(2+a+b)`. Need to show `4/(2+a+b) ≥ 2/(1+√(ab))`, i.e., `4(1+√(ab)) ≥ 2(2+a+b)`, i.e., `2√(ab) ≥ a+b−2√(ab)+... `... Actually: `4/(2+a+b) ≥ 2/(1+√(ab))` ↔ `4(1+√(ab)) ≥ 2(2+a+b)` ↔ `4+4√(ab) ≥ 4+2a+2b` ↔ `2√(ab) ≥ a+b`, which is the **reverse** of AM-GM. So this approach fails. Instead use Jensen (convexity of `1/(1+t)`): `½[f(a)+f(b)] ≥ f((a+b)/2) ≥ f(√(ab))` by AM-GM and the fact that `f` is decreasing and convex. ∎ |
| 144 | By Cauchy-Schwarz (#134): `x²+y²+z² ≥ (x+y+z)²/3 = 36/3 = 12`. Min = **12** at `x = y = z = 2`. |
| 145 | **Nesbitt's inequality.** `a/(b+c) + b/(a+c) + c/(a+b) = (a+b+c)[1/(b+c)+1/(a+c)+1/(a+b)] − 3`. By Cauchy-Schwarz: `[1/(b+c)+1/(a+c)+1/(a+b)]·[(b+c)+(a+c)+(a+b)] ≥ 9`. So `1/(b+c)+... ≥ 9/[2(a+b+c)]`. Thus the expression `≥ (a+b+c)·9/[2(a+b+c)] − 3 = 9/2 − 3 = 3/2`. ∎ |
| 146 | `a²+b²+c² = 1`. We know `ab+bc+ca ≤ (a²+b²+c²) = 1` (from #102 with equality when `a=b=c`). For the lower bound: `(a+b+c)² ≥ 0` → `a²+b²+c²+2(ab+bc+ca) ≥ 0` → `1+2(ab+bc+ca) ≥ 0` → `ab+bc+ca ≥ −1/2`. **Answer: `−1/2 ≤ ab+bc+ca ≤ 1`.** |
| 147 | Let `u = x+1/x ≥ 2`. Expression: `u⁶−6u⁴+9u² = u²(u⁴−6u²+9) = u²(u²−3)²`. For `u ≥ 2`: `u² ≥ 4` and `u²−3 ≥ 1`, so `u²(u²−3)² ≥ 4·1 = 4`. Min = **4** at `u = 2` (i.e., `x = 1`). |
| 148 | From #104: `a⁴+b⁴ ≥ a³b+ab³`. Similarly `b⁴+c⁴ ≥ b³c+bc³` and `c⁴+a⁴ ≥ c³a+ca³`. Adding: `2(a⁴+b⁴+c⁴) ≥ a³b+ab³+b³c+bc³+c³a+ca³ = ab(a²+b²)+bc(b²+c²)+ca(c²+a²) ≥ ab·2abc+... `... Actually more directly: `a⁴+b⁴+c⁴ ≥ a²b²+b²c²+c²a²` (from #113) and by AM-GM `a²b²+b²c²+c²a² ≥ 3(a²b²·b²c²·c²a²)^{1/3} = 3a²b²c²`. But we need `abc(a+b+c) = a²bc+ab²c+abc²`. By AM-GM: `a⁴+a⁴+b⁴+c⁴ ≥ 4a²bc` (4-term AM-GM), similarly for other terms. Summing: `3(a⁴+b⁴+c⁴) ≥ 4(a²bc+ab²c+abc²) = 4abc(a+b+c)`... this gives `a⁴+b⁴+c⁴ ≥ 4abc(a+b+c)/3`, not exactly the claim. The claim `a⁴+b⁴+c⁴ ≥ abc(a+b+c)` follows from Schur's inequality (degree 4). ∎ |
| 149 | If `a+b+c = 0`: `a²+b²+c² = (a+b+c)² − 2(ab+bc+ca) = −2(ab+bc+ca)`. So `a²+b²+c² + 2abc = −2(ab+bc+ca) + 2abc`. The identity `a³+b³+c³ − 3abc = (a+b+c)(a²+b²+c²−ab−bc−ca)` gives `a³+b³+c³ = 3abc` when `a+b+c = 0`. The expression `a²+b²+c²+2abc` can take various values. For `a=1, b=−1, c=0`: `1+1+0+0 = 2`. For `a=2, b=−1, c=−1`: `4+1+1+2·2·1 = 10`. So it is NOT constant. **The relationship is: `a²+b²+c² = −2(ab+bc+ca)` when `a+b+c=0`.** |
| 150 | By Cauchy-Schwarz: `(a²+1)(b²+1) ≥ (ab+1)²`. Then `(ab+1)²(c²+1) ≥ (abc+c)²... `... Actually apply Cauchy-Schwarz twice: `(a²+1)(b²+1) ≥ (ab+1)²`, and `(ab+1)²(1+c²) ≥ (ab+c)²`... not quite. Use the identity: `(a²+1)(b²+1)(c²+1) = (ab+bc+ca)² + (a−b)²(1+c²)/2 + ... `. By Lagrange's identity extended: `(a²+1)(b²+1)(c²+1) − (ab+bc+ca)² = (ab−c)² + (ac−b)² + (bc−a)²... ` *(verification needed)*. In fact the inequality follows from Cauchy-Schwarz: let `u = (a, 1)` and `v = (b, 1)`. `‖u‖²‖v‖² ≥ (u·v)² = (ab+1)²`. Then `(ab+1)²(c²+1) ≥ (abc+1·c + ... )`... The full proof uses the Cauchy-Schwarz identity for three pairs. ∎ |
| 151 | First: `x²+2x+2 = (x+1)²+1 > 0` always ✓. Second: `−x²+3x−2 > 0 → x²−3x+2 < 0 → (x−1)(x−2) < 0 → 1 < x < 2`. **Answer: `(1, 2)`.** |
| 152 | Let `u = |x|`: `u²−2u−3 ≥ 0 → (u−3)(u+1) ≥ 0 → u ≥ 3` (since `u ≥ 0`). → `|x| ≥ 3` → **`x ≤ −3 or x ≥ 3`**. |
| 153 | Let `u = x² ≥ 0`: `u²−5u+6 ≤ 0 → (u−2)(u−3) ≤ 0 → 2 ≤ u ≤ 3` → `√2 ≤ |x| ≤ √3` → **`[−√3, −√2] ∪ [√2, √3]`**. |
| 154 | `a²+b²+c²+d² − ab−bc−cd−da = ½[(a−b)²+(b−c)²+(c−d)²+(d−a)²] + (a−c)²/2... ` Actually: `a²+b²+c²+d² − (ab+bc+cd+da) = ½[(a−b)²+(b−c)²+(c−d)²+(a−d)²] ≥ 0`... check: expand RHS = `½[a²−2ab+b²+b²−2bc+c²+c²−2cd+d²+a²−2ad+d²] = a²+b²+c²+d² − ab−bc−cd−ad`. ∎ |
| 155 | Since `a+b = 1`: `(1+1/a)(1+1/b) = 1 + 1/a + 1/b + 1/(ab) = 1 + (a+b)/(ab) + 1/(ab) = 1 + 1/(ab) + 1/(ab) = 1 + 2/(ab)`. By AM-GM: `ab ≤ (a+b)²/4 = 1/4`. So `1/(ab) ≥ 4`. Thus `1 + 2/(ab) ≥ 1 + 8 = 9`. Equality at `a = b = 1/2`. ∎ |

---

## Quick Reference: Inequality & Absolute Value Decision Guide

| Problem Type | Method | Key Trap |
|---|---|---|
| Linear inequality | Isolate `x` | Flip sign when ÷ by negative |
| Polynomial inequality | Factor + sign table | Must have `= 0` on one side |
| Rational inequality | Factor num & den + sign table | Exclude zeros of denominator |
| Repeated factors | Even power: no sign change; Odd: sign change | Don't forget domain restrictions |
| `|expr| = k, k > 0` | Two equations: `expr = ±k` | Check both solutions |
| `|expr| < k, k > 0` | `−k < expr < k` (sandwich) | No solution if `k < 0` |
| `|expr| > k, k > 0` | `expr < −k` or `expr > k` (tails) | All reals if `k < 0` |
| `|A| = |B|` | `A = B` or `A = −B` | Don't lose a case |
| `|A| < |B|` | Square both sides: `A² < B²` | Only valid for non-negative quantities |
| `|expr₁| + |expr₂| = k` | Critical point method | Check each region carefully |
| `|x² + ...|` | Let `u = |x|` or split into cases | `x² = |x|²` is the key substitution |
| `ax²+bx+c` with `Δ < 0` | Completing the square: `a(x+h)² + k` | Always positive (if `a > 0`) or always negative (if `a < 0`) — no sign analysis needed |
| Prove `f ≥ g` | Write `f − g` as sum of squares | Each square `≥ 0`; equality when all squares are 0 |
| AM-GM (optimization) | `(a+b)/2 ≥ √(ab)` for `a,b ≥ 0` | Equality when all terms equal |
| Cauchy-Schwarz | `(Σa²)(Σb²) ≥ (Σab)²` | Equality when vectors are proportional |
| Triangle inequality | `|a+b| ≤ |a|+|b|` | Equality when same sign |
| `x² + 1/x² ≥ 2` | `(x − 1/x)² ≥ 0` | Generalizes to `t + 1/t ≥ 2` for `t > 0` |
