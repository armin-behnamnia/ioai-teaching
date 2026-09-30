# Problem-Based Teaching Plan: Algebra Preparation & Quadratic Equations

**Format:** 3 sessions × 60 minutes
**Approach:** Problem-Based Learning (PBL) — each session opens with a motivating problem, develops theory through guided discovery, and closes with consolidation.

---

## Session 1 — Algebraic Expressions, Identities, and Factoring (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Read and manipulate algebraic expressions (expand, combine like terms).
- Recognize and apply standard algebraic identities.
- Factor expressions using common factoring techniques.
- Understand why factoring and expanding are inverse processes.

### Materials
- Whiteboard / projector
- Handout of problem sets (one per student)
- Mini-whiteboards or scratch paper for pair work

---

### Part A: Hook & Motivating Problem (10 min)

**Present this problem on the board:**

> A rectangular garden has a length that is 3 meters longer than its width. A second garden is created by extending *both* dimensions of the first garden by 2 meters. The area of the second garden is **40 m²** larger than the first. Find the dimensions of the first garden.

**Do NOT solve it yet.** Ask students:
- *What expressions can we write down?*
- *What equation do we get?*

Let students stumble. They will produce something like:
- First garden: `w` and `w + 3`, area = `w(w+3)`
- Second garden: `w + 2` and `w + 5`, area = `(w+2)(w+5)`
- Equation: `(w+2)(w+5) - w(w+3) = 40`

**Key realization:** To solve this, we need to *expand* and *simplify* algebraic expressions. This is the engine that drives the entire session.

---

### Part B: Guided Discovery — Expanding & Identities (15 min)

#### Activity 1: Expand These (5 min — individual, then check with neighbor)

1. `(x + 2)(x + 5)`
2. `(x − 3)(x + 3)`
3. `(x + 4)²`
4. `(2x − 1)(x + 6)`
5. `(3x + 2)(3x − 2)`

**After students attempt these, debrief on the board.** Highlight three identities that emerged naturally:

| Identity | Expanded Form | Name |
|---|---|---|
| `(a + b)²` | `a² + 2ab + b²` | Square of a sum |
| `(a − b)²` | `a² − 2ab + b²` | Square of a difference |
| `(a + b)(a − b)` | `a² − b²` | Difference of squares |

**Teaching note:** Do not just state these identities — point to where they appeared in problems 2, 3, and 5 above. Students should see that they *discovered* them.

#### Activity 2: Use Identities to Compute Mentally (3 min)

Ask students to compute these *without* a calculator, using identities:

1. `101²` → `(100 + 1)² = 10000 + 200 + 1 = 10201`
2. `99 × 101` → `(100−1)(100+1) = 10000 − 1 = 9999`
3. `98²` → `(100 − 2)² = 10000 − 400 + 4 = 9604`

This builds the intuition that identities are *tools*, not memorization burdens.

---

### Part C: Guided Discovery — Factoring (20 min)

**Transition statement:**
> "Expanding takes `(...)(...)` and turns it into a single expression. What if we want to go backwards?"

#### Activity 3: Factor These (8 min — pairs)

1. `x² + 7x + 12`
2. `x² − 5x + 6`
3. `x² − 9`
4. `x² + 6x + 9`
5. `2x² + 7x + 3`
6. `x² − 4x − 12`

**Debrief** by categorizing the techniques students used:

| Technique | Example | Result |
|---|---|---|
| Common factor (GCF) | `3x² + 6x` | `3x(x + 2)` |
| Difference of squares | `x² − 9` | `(x+3)(x−3)` |
| Perfect square | `x² + 6x + 9` | `(x+3)²` |
| Trial / grouping (`ac`-method) | `2x² + 7x + 3` | `(2x+1)(x+3)` |

#### Activity 4: Factor with a Twist (7 min)

Present these to challenge students:

1. `x² − 5x` → *GCF first:* `x(x − 5)`
2. `2x³ − 8x` → *GCF then difference of squares:* `2x(x²−4) = 2x(x+2)(x−2)`
3. `x² + 2xy + y² − 4` → *Group as perfect square, then difference of squares:* `(x+y)² − 4 = (x+y+2)(x+y−2)`

**Problem 3 is the crown jewel of this section.** It shows that factoring is *creative* — sometimes you group terms, sometimes you recognize a hidden structure.

**Teaching note:** If students struggle with problem 3, scaffold by asking: *"Can you see a perfect square hiding in the first three terms?"*

---

### Part D: Return to the Garden Problem & Wrap-Up (15 min)

**Now return to the motivating problem.** Students have the tools.

```
(w+2)(w+5) - w(w+3) = 40
```

**Expand:**
```
w² + 7w + 10 − w² − 3w = 40
4w + 10 = 40
4w = 30
w = 7.5
```

Dimensions of the first garden: **7.5 m × 10.5 m**.

**Discussion question:** *Notice — the x² terms cancelled. What if they hadn't? What kind of equation would we get?* → This plants the seed for Session 3 (quadratic equations).

#### Quick Exit Check (5 min)

Have students factor these on mini-whiteboards and hold up:

1. `x² − 16`
2. `x² + 8x + 16`
3. `x² + 3x − 10`
4. `3x² − 12`

---

### Session 1 — Summary Table (leave on board or handout)

| Operation | What it does | Example |
|---|---|---|
| Expand | `(a+b)(c+d)` → single polynomial | `(x+2)(x+3) = x²+5x+6` |
| Factor | single polynomial → `(…)(…)` | `x²+5x+6 = (x+2)(x+3)` |
| Identity: `(a±b)²` | Shortcut for squaring | `(x+3)² = x²+6x+9` |
| Identity: `(a+b)(a−b)` | Difference of squares | `(x+4)(x−4) = x²−16` |

---

## Session 2 — Solving Equations & The Danger of Losing Solutions (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve linear and simple quadratic equations by factoring.
- Recognize **exactly when** simplifying both sides of an equation can destroy solutions.
- Explain *why* dividing or canceling can lose solutions.
- Apply safe strategies to avoid losing solutions.

### Materials
- Whiteboard
- Red marker (for highlighting "danger zones")
- Handout with trap problems

---

### Part A: Hook — A Vanishing Solution (10 min)

**Write this on the board:**

> Solve for `x`:
> ```
> x² + 5x = x + 5
> ```

**Let a volunteer solve it the "natural" way.** A common student approach:

```
x² + 5x = x + 5
x² + 5x − x − 5 = 0        ← subtract x+5 from both sides  ✓
x² + 4x − 5 = 0
(x + 5)(x − 1) = 0
x = −5  or  x = 1
```

This is correct — subtracting is always safe. **Now show the DANGEROUS approach:**

```
x² + 5x = x + 5
x(x + 5) = 1(x + 5)        ← factor both sides
x(x + 5) / (x + 5) = 1      ← "cancel" (x+5) from both sides  ⚠️
x = 1
```

**The solution `x = −5` has vanished!**

Ask: *Where did `x = −5` go? What went wrong?*

**This is the central mystery of the session.** Students now have a reason to care about the rule.

---

### Part B: Understanding the Danger — When and Why (15 min)

#### The Core Principle (5 min)

Write on the board in **red**:

> **Rule:** You may ADD or SUBTRACT the same expression from both sides of an equation — always safe.
>
> **Rule:** You may NOT divide both sides by an expression containing a variable — UNLESS you check whether that expression can equal zero. If it can, you may be losing a solution.

Explain the mechanism:

- When you divide both sides by `(x + 5)`, you are implicitly assuming `x + 5 ≠ 0`, i.e., `x ≠ −5`.
- If `x = −5` is actually a solution, you have **excluded it by assumption**.
- This is not just a "rule violation" — it is a *logical error*: you added an unstated assumption.

#### Activity 5: Spot the Trap (10 min — pairs)

Give students three "solutions." In each case, the student work contains an error that may lose a solution. Students must:

1. Find the dangerous step.
2. Find the lost solution.
3. Rewrite the solution correctly.

**Problem A:**
```
Solve:  x² = 3x

Step 1:  x² / x = 3x / x
Step 2:  x = 3
```
✗ Lost solution: `x = 0` (because `x = 0` makes the divisor `x` equal to zero).
✓ Correct: `x² − 3x = 0 → x(x−3) = 0 → x = 0 or x = 3`

**Problem B:**
```
Solve:  x(x − 2) = 3(x − 2)

Step 1:  x = 3    (cancel x−2 from both sides)
```
✗ Lost solution: `x = 2`.
✓ Correct: `x(x−2) − 3(x−2) = 0 → (x−2)(x−3) = 0 → x = 2 or x = 3`

**Problem C:**
```
Solve:  (x + 1)(x − 4) = (x + 1)(2x + 3)

Step 1:  (x − 4) = (2x + 3)     (cancel x+1)
Step 2:  x − 4 = 2x + 3
Step 3:  −7 = x
```
✗ Lost solution: `x = −1`.
✓ Correct: `(x+1)[(x−4) − (2x+3)] = 0 → (x+1)(−x−7) = 0 → x = −1 or x = −7`

**Derief:** In every case, the safe method is:
1. Move everything to one side → get `… = 0`
2. Factor
3. Set each factor to zero

---

### Part C: The Safe Protocol — Factoring Method for Equations (15 min)

**Write the protocol on the board:**

> ### Safe Protocol for Solving Equations
> 1. Move all terms to one side so the equation reads `expression = 0`.
> 2. Factor the expression completely.
> 3. Set each factor equal to zero and solve.
> 4. **Never divide both sides by an expression containing a variable.**

#### Activity 6: Apply the Protocol (10 min — individual)

Solve each equation using the safe protocol:

1. `x² = 7x`
   → `x² − 7x = 0 → x(x−7) = 0 → x = 0 or x = 7`

2. `x² + 2x = x + 6`
   → `x² + x − 6 = 0 → (x+3)(x−2) = 0 → x = −3 or x = 2`

3. `2x² = x + 3`
   → `2x² − x − 3 = 0 → (2x−3)(x+1) = 0 → x = 3/2 or x = −1`

4. `x(x + 4) = 2(x + 4)`
   → `(x+4)(x−2) = 0 → x = −4 or x = 2`

5. `x³ = 4x`
   → `x³ − 4x = 0 → x(x²−4) = 0 → x(x+2)(x−2) = 0 → x = 0, 2, −2`

**Problem 5 is important** — it has three solutions and the "divide by x" shortcut would lose two of them.

---

### Part D: Synthesis & Exit Ticket (20 min)

#### Discussion: The Zero-Product Property (5 min)

Ask: *Why does setting each factor to zero work?*

Guide students to articulate the **Zero-Product Property**:

> If `A · B = 0`, then `A = 0` or `B = 0` (or both).

This is the logical backbone of the entire factoring method. It only works when the product equals **zero** — not when it equals some other expression. That is *why* we must move everything to one side first.

**Contrast:**
- `A · B = 0` → we can conclude `A = 0` or `B = 0` ✓
- `A · B = 15` → we CANNOT conclude `A = 15` or `B = 15` ✗ (e.g., `3 × 5 = 15`)

This is why the protocol says "get it to zero" — only zero has this special splitting power.

#### Exit Ticket (10 min)

Solve carefully. Show all steps. Watch for traps.

1. `x² = 6x`
2. `x(x − 3) = 4(x − 3)`
3. `(x − 1)(x + 2) = 0`
4. `x² + 5x + 6 = 0`
5. **Challenge:** `x²(x − 5) = 9(x − 5)` *(Hint: don't cancel. Move to one side and factor.)*

**Answer key for exit ticket:**

1. `x = 0, 6`
2. `x = 3, 4`
3. `x = 1, −2`
4. `x = −2, −3`
5. `(x−5)(x²−9) = 0 → (x−5)(x−3)(x+3) = 0 → x = 5, 3, −3`

---

### Session 2 — Summary Table

| Safe Operation | Unsafe Operation |
|---|---|
| Add/subtract from both sides | ✗ Divide both sides by variable expression |
| Move everything to one side (`= 0`) | ✗ Cancel a common factor from both sides |
| Factor, then set each factor = 0 | ✗ Assume a factor is nonzero |

---

## Session 3 — Quadratic Equations: Formula, Delta, and Disguised Quadratics (60 min)

### Learning Objectives
By the end of this session, students will be able to:
- Solve quadratic equations by factoring (recap from Session 2).
- Derive and apply the quadratic formula.
- Interpret the discriminant (delta) to predict the number and type of solutions.
- Recognize and solve equations that are "disguised" quadratics via substitution.

### Materials
- Whiteboard
- Graphing calculator or Desmos (optional, for visualizing discriminant)
- Handout with mixed problems

---

### Part A: Hook — An Equation That Won't Factor (8 min)

**Write on the board:**

> Solve: `x² + 2x − 7 = 0`

Give students 2–3 minutes to try factoring. They will struggle — it does not factor nicely over the integers.

Ask: *What do we do when factoring fails?*

**Present a second one:**

> Solve: `x² − 6x + 2 = 0`

Again, no integer factors. Students feel the need for a **general method** — one that always works, regardless of whether the coefficients are "nice."

---

### Part B: The Quadratic Formula & Delta (20 min)

#### Derivation — Completing the Square (10 min)

**Walk through the derivation** on the board. This is not optional — students should see where the formula comes from.

```
Start with:     ax² + bx + c = 0      (a ≠ 0)

Divide by a:    x² + (b/a)x + (c/a) = 0

Move constant:  x² + (b/a)x = −c/a

Complete the square:
  Add (b/2a)² to both sides:

  x² + (b/a)x + (b/2a)² = −c/a + b²/(4a²)

  (x + b/2a)² = (b² − 4ac) / (4a²)

Take square root:

  x + b/2a = ± √(b² − 4ac) / (2a)

  x = (−b ± √(b² − 4ac)) / (2a)
```

**Box the formula:**

> ### The Quadratic Formula
> ```
> x = (−b ± √(b² − 4ac)) / (2a)
> ```
> For any equation `ax² + bx + c = 0` with `a ≠ 0`.

**Teaching note:** Emphasize that in the derivation, we divided by `a` — which is safe because `a ≠ 0` (if `a = 0`, it is not a quadratic). This connects back to Session 2's lesson about safe vs. unsafe operations.

#### Introducing Delta — The Discriminant (10 min)

Point to the expression under the square root:

> **Δ (Delta) = b² − 4ac** — called the **discriminant**.

Ask students: *What does the sign of Δ tell us?*

Guide them through three cases. Use Desmos or quick sketches to visualize:

| Value of Δ | Square root | Number of real solutions | Geometry (parabola vs. x-axis) |
|---|---|---|---|
| **Δ > 0** | √Δ is a positive real number | **2 distinct** real solutions | Parabola crosses x-axis at 2 points |
| **Δ = 0** | √Δ = 0 | **1** real solution (repeated root) | Parabola touches x-axis at 1 point (vertex) |
| **Δ < 0** | √Δ is not real | **0** real solutions | Parabola does not touch x-axis |

**Quick visualization (optional with Desmos):**

- `x² − 5x + 6 = 0` → Δ = 25−24 = 1 > 0 → two solutions (crosses x-axis twice)
- `x² − 4x + 4 = 0` → Δ = 16−16 = 0 → one solution (sits on x-axis)
- `x² + x + 1 = 0` → Δ = 1−4 = −3 < 0 → no real solutions (floats above x-axis)

---

### Part C: Practice — Solving with the Formula (12 min)

#### Activity 7: Solve These Using the Formula (8 min — individual)

1. `x² + 2x − 7 = 0`
   → `a=1, b=2, c=−7`
   → `Δ = 4 + 28 = 32`
   → `x = (−2 ± √32) / 2 = (−2 ± 4√2) / 2 = −1 ± 2√2`

2. `x² − 6x + 2 = 0`
   → `a=1, b=−6, c=2`
   → `Δ = 36 − 8 = 28`
   → `x = (6 ± √28) / 2 = (6 ± 2√7) / 2 = 3 ± √7`

3. `2x² + 3x − 5 = 0`
   → `a=2, b=3, c=−5`
   → `Δ = 9 + 40 = 49`
   → `x = (−3 ± 7) / 4`
   → `x = 1` or `x = −5/2`

4. `x² + x + 1 = 0`
   → `a=1, b=1, c=1`
   → `Δ = 1 − 4 = −3 < 0`
   → **No real solutions**

**Debrief point:** Problem 3 could have been solved by factoring: `(2x+5)(x−1) = 0`. But the formula gives the same answer and *always works*, even when factoring is hard or impossible. Problem 4 is impossible by factoring and the formula tells us *why* — the discriminant is negative.

#### Activity 8: Delta-First Strategy (4 min)

Present this efficient approach:

> **Before solving, compute Δ first.** It tells you what to expect:
> - If Δ is a perfect square → the roots are rational → try factoring first (faster).
> - If Δ > 0 but not a perfect square → two irrational roots → use the formula.
> - If Δ = 0 → one repeated root → `(x + b/2a)² = 0`.
> - If Δ < 0 → no real roots → stop. Don't waste time.

---

### Part D: Disguised Quadratics — Substitution (15 min)

**Transition:**
> "Not every quadratic *looks* like a quadratic. Sometimes it wears a disguise."

#### Motivating Problem (5 min)

> Solve: `x⁴ − 5x² + 4 = 0`

Let students stare at it. Then ask: *What if we let `u = x²`?*

```
Let u = x².  Then u² = x⁴.

The equation becomes:
u² − 5u + 4 = 0

Factor:
(u − 1)(u − 4) = 0

u = 1  or  u = 4

Back-substitute:
x² = 1  →  x = ±1
x² = 4  →  x = ±2

Solutions: x = 1, −1, 2, −2
```

**Key insight:** The substitution `u = x²` *reduced* a degree-4 equation to a quadratic. The structure `u² − 5u + 4` is a quadratic in disguise.

#### Activity 9: Find the Disguise (8 min — pairs)

For each equation, identify a substitution `u = …` that reduces it to a quadratic, then solve.

**Problem A:**
```
x⁶ − 7x³ − 8 = 0
```
Substitution: `u = x³` → `u² − 7u − 8 = 0` → `(u−8)(u+1) = 0`
→ `u = 8` or `u = −1`
→ `x³ = 8` → `x = 2`; `x³ = −1` → `x = −1`
**Solutions: `x = 2, −1`**

**Problem B:**
```
(x² − 3x)² − 4(x² − 3x) − 12 = 0
```
Substitution: `u = x² − 3x` → `u² − 4u − 12 = 0` → `(u−6)(u+2) = 0`
→ `u = 6` or `u = −2`

Back-substitute:
- `x² − 3x = 6` → `x² − 3x − 6 = 0` → `Δ = 9+24 = 33` → `x = (3 ± √33)/2`
- `x² − 3x = −2` → `x² − 3x + 2 = 0` → `(x−1)(x−2) = 0` → `x = 1, 2`

**Solutions: `x = (3±√33)/2, 1, 2`** — four solutions!

**Problem C (extension):**
```
(x + 1/x)² − 5(x + 1/x) + 6 = 0     (x ≠ 0)
```
Substitution: `u = x + 1/x` → `u² − 5u + 6 = 0` → `(u−2)(u−3) = 0`
→ `u = 2` or `u = 3`

Back-substitute:
- `x + 1/x = 2` → `x² − 2x + 1 = 0` → `(x−1)² = 0` → `x = 1`
- `x + 1/x = 3` → `x² − 3x + 1 = 0` → `Δ = 9−4 = 5` → `x = (3±√5)/2`

**Solutions: `x = 1, (3+√5)/2, (3−√5)/2`**

**Teaching note:** Problem C is powerful because `x + 1/x` doesn't look like a simple power of `x`, but the substitution still works. The *structure* is what matters — look for "something squared, minus something, plus constant."

---

### Part E: Synthesis & Exit Ticket (5 min)

#### Final Discussion

Present this decision flowchart verbally or on the board:

```
Given an equation that might be quadratic:

1. Can I move everything to one side and get = 0?
   → Yes: go to step 2.

2. Can I factor it?
   → Yes: factor and set each factor to 0. Done.
   → No: go to step 3.

3. Is it a quadratic ax² + bx + c = 0?
   → Yes: use the quadratic formula. Compute Δ first to know what to expect.
   → No, but it looks like a quadratic in disguise: try a substitution u = (expression).
```

#### Exit Ticket (5 min)

1. Compute Δ and state the number of real solutions (do not solve):
   `3x² + 2x + 1 = 0`

2. Solve using the quadratic formula:
   `x² + 6x − 3 = 0`

3. Solve by substitution:
   `x⁴ − 10x² + 9 = 0`

**Answer key:**

1. `Δ = 4 − 12 = −8 < 0` → **0 real solutions**

2. `Δ = 36 + 12 = 48` → `x = (−6 ± √48)/2 = (−6 ± 4√3)/2 = −3 ± 2√3`

3. `u = x²` → `u² − 10u + 9 = 0` → `(u−1)(u−9) = 0` → `u = 1` or `u = 9`
   → `x = ±1, ±3`

---

### Session 3 — Summary Table

| Tool | When to use | Example |
|---|---|---|
| **Factoring** | Δ is a perfect square, coefficients are "nice" | `x²−5x+6 = (x−2)(x−3) = 0` |
| **Quadratic formula** | Always works (when `ax²+bx+c=0`) | `x = (−b ± √Δ) / 2a` |
| **Discriminant (Δ)** | Predicts number/type of solutions before solving | Δ > 0: two; Δ = 0: one; Δ < 0: none |
| **Substitution** | Equation has the *structure* of a quadratic but higher degree | `u = x²` turns `x⁴−5x²+4=0` into `u²−5u+4=0` |

---

## Appendix: Complete Problem Set (for homework or self-study)

### Algebraic Manipulation
1. Expand: `(2x − 3)(x + 4)`
2. Expand: `(x + 5)²`
3. Expand: `(3x − 2)²`
4. Factor: `x² + 9x + 20`
5. Factor: `x² − 25`
6. Factor: `2x² − 5x − 3`
7. Factor: `x³ − x`
8. Factor: `x² + 4xy + 4y² − 9`

### Solving Equations (Safe Protocol)
9. `x² = 4x`
10. `x(x + 1) = 2(x + 1)`
11. `x² − 7x + 12 = 0`
12. `x³ = x`
13. `x² + 3x = x + 5`

### Quadratic Formula & Discriminant
14. `x² + 5x + 3 = 0`
15. `x² − 4x + 7 = 0`
16. `4x² − 12x + 9 = 0`
17. `3x² + x − 2 = 0`

### Disguised Quadratics
18. `x⁴ − 13x² + 36 = 0`
19. `x⁶ + 3x³ − 4 = 0`
20. `(x² + x)² − 8(x² + x) + 12 = 0`

---

### Answer Key (Appendix)

| # | Answer |
|---|---|
| 1 | `2x² + 5x − 12` |
| 2 | `x² + 10x + 25` |
| 3 | `9x² − 12x + 4` |
| 4 | `(x + 4)(x + 5)` |
| 5 | `(x + 5)(x − 5)` |
| 6 | `(2x + 1)(x − 3)` |
| 7 | `x(x + 1)(x − 1)` |
| 8 | `(x + 2y + 3)(x + 2y − 3)` |
| 9 | `x = 0, 4` |
| 10 | `x = −1, 2` |
| 11 | `x = 3, 4` |
| 12 | `x = 0, 1, −1` |
| 13 | `x = 1, −5` |
| 14 | `x = (−5 ± √13)/2` |
| 15 | No real solutions (Δ = −12) |
| 16 | `x = 3/2` (repeated, Δ = 0) |
| 17 | `x = 2/3, −1` |
| 18 | `x = ±2, ±3` |
| 19 | `x = 1, ³√(−4)` |
| 20 | `x = 1, 2, (−1±√13)/2` |
