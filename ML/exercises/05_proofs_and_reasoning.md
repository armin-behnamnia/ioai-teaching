# Set Algebra — Proofs and Reasoning

## Learning Objectives

- Practice writing **rigorous proofs** about sets using element-wise arguments.
- Learn to prove set **equalities** (both $\subseteq$ and $\supseteq$ directions).
- Develop the skill of **algebraic manipulation** of set expressions.
- Tackle **challenging** multi-step problems.

---

## Problem 1 — Element-wise Proofs

Prove each equality by showing both $\subseteq$ and $\supseteq$ (element-wise argument).

1. $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ — **distributive law**
2. $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ — **distributive law**
3. $(A \cup B)^c = A^c \cap B^c$ — **De Morgan's law**
4. $(A \cap B) \cup (A \cap B^c) = A$ — **partition law**

---

## Problem 2 — Algebraic Proofs

Prove each equality **algebraically** (using set algebra laws, naming each step).

1. $(A \cap B) \cup (A^c \cap B) = B$
2. $(A \cup B) \cap (A \cup C) = A \cup (B \cap C)$
3. $(A \cap B) \cup (A^c \cap C) = (A \cap B) \cup (A^c \cap C) \cup (B \cap C)$
4. $A \cup (A^c \cap B) = A \cup B$
5. $(A \cap B)^c \cap A = A \cap B^c$
6. $(A \cup B^c) \cap (B \cup A^c) = (A \cap B) \cup (A^c \cap B^c)$

---

## Problem 3 — Proving Inequalities (Subset)

Prove each subset relationship. For each, determine whether **equality** also holds (if not, give a counterexample).

1. $A \cap (B \cup C) \subseteq (A \cap B) \cup C$
2. $(A \cup B) \cap C \subseteq (A \cap C) \cup B$
3. $A \setminus (B \cap C) = (A \setminus B) \cup (A \setminus C)$, where $X \setminus Y = X \cap Y^c$
4. $A \setminus (B \cup C) = (A \setminus B) \cap (A \setminus C)$
5. $(A \cap B) \setminus C = A \cap (B \setminus C)$

---

## Problem 4 — Set Equality via Characteristic Functions

*(Optional — for students who want a different perspective.)*

The **characteristic function** of a set $A$ is $\chi_A(x) = 1$ if $x \in A$, and $\chi_A(x) = 0$ if $x \notin A$.

Set operations correspond to logical operations on characteristic functions:

| Set Operation | Characteristic Function |
|---|---|
| $A \cap B$ | $\chi_A \cdot \chi_B$ (multiplication) |
| $A \cup B$ | $\chi_A + \chi_B - \chi_A \cdot \chi_B$ |
| $A^c$ | $1 - \chi_A$ |

1. Verify the distributive law $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ by showing both sides have the same characteristic function.
2. Verify De Morgan's law $(A \cup B)^c = A^c \cap B^c$ using characteristic functions.
3. Verify the absorption law $A \cup (A \cap B) = A$ using characteristic functions.

---

## Problem 5 — Conditional Identities

These identities hold **under the given conditions**. Prove each one.

1. **Given** $A \subseteq B$, prove: $A \cup B = B$ and $A \cap B = A$.
2. **Given** $A \cap B = \emptyset$, prove: $A \subseteq B^c$ and $B \subseteq A^c$.
3. **Given** $A \cup B = U$, prove: $A^c \subseteq B$ and $B^c \subseteq A$.
4. **Given** $A \subseteq B \cap C$, prove: $A \subseteq B$ and $A \subseteq C$.
5. **Given** $A \subseteq B$ and $C \subseteq D$, prove: $A \cup C \subseteq B \cup D$ and $A \cap C \subseteq B \cap D$.
6. **Given** $A \cap B = A$ (i.e., $A \subseteq B$), prove: $A \cup B = B$.
7. **Given** $A \cup B = A$ (i.e., $B \subseteq A$), prove: $A \cap B = B$.

---

## Problem 6 — Symmetric Difference

The **symmetric difference** of $A$ and $B$ is defined as:
$$A \triangle B = (A \setminus B) \cup (B \setminus A) = (A \cap B^c) \cup (A^c \cap B)$$

This is the set of elements in **exactly one** of $A$ or $B$.

1. Compute $A \triangle B$ for $A = \{1,2,3,4\}$, $B = \{3,4,5,6\}$, $U = \{1,2,3,4,5,6,7,8\}$.
2. Prove: $A \triangle B = (A \cup B) \setminus (A \cap B)$, i.e., $(A \cup B) \cap (A \cap B)^c$.
3. Prove: $A \triangle B = (A \cup B) \cap (A^c \cup B^c)$.
4. Prove: $A \triangle \emptyset = A$.
5. Prove: $A \triangle A = \emptyset$.
6. Prove: $A \triangle U = A^c$.
7. Prove: $A \triangle A^c = U$.
8. **Challenge:** Prove: $A \triangle B = (A \cap B^c) \cup (B \cap A^c)$ implies $(A \triangle B)^c = (A \cap B) \cup (A^c \cap B^c)$.

---

## Problem 7 — Multi-step Challenge Problems

Simplify each expression as much as possible. Show all steps.

1. $(A \cup B) \cap (A^c \cup B) \cap (A \cup B^c) \cap (A^c \cup B^c)$
2. $[(A \cap B) \cup (A \cap C)] \cap [(B \cap C) \cup A^c]$
3. $(A \cup B \cup C) \cap (A^c \cup B \cup C) \cap (A \cup B^c \cup C) \cap (A \cup B \cup C^c)$
4. $(A \cap B^c) \cup (A^c \cap B) \cup (A \cap B)$
5. $(A \cap B \cap C) \cup (A \cap B \cap C^c) \cup (A \cap B^c \cap C) \cup (A^c \cap B \cap C)$

---

## Problem 8 — Proving the Consensus Theorem

The **Consensus Theorem** states:
$$(A \cap B) \cup (A^c \cap C) \cup (B \cap C) = (A \cap B) \cup (A^c \cap C)$$

The term $B \cap C$ is called the **consensus** term — it is "absorbed" by the other two.

1. Prove the Consensus Theorem algebraically.
2. Prove the dual form: $(A \cup B) \cap (A^c \cup C) \cap (B \cup C) = (A \cup B) \cap (A^c \cup C)$
3. Use the Consensus Theorem to simplify: $(A \cap B) \cup (A^c \cap C) \cup (B \cap C \cap D)$
4. Use the Consensus Theorem to simplify: $(A \cap B) \cup (A^c \cap B^c) \cup (B \cap C)$

---

## Problem 9 — Comprehensive Proof Challenge

Prove or disprove each statement. For true statements, provide a full proof. For false ones, give a specific counterexample.

1. $(A \cap B) \cup C = A \cap (B \cup C)$ if and only if $C \subseteq A$.
2. $(A \cup B) \cap C = A \cup (B \cap C)$ if and only if $A \subseteq C$.
3. $A \triangle B = \emptyset$ if and only if $A = B$. *(Recall: $\triangle$ is symmetric difference.)*
4. If $A \subseteq B$ and $A \subseteq C$ and $B \cap C = \emptyset$, then $A = \emptyset$.
5. $(A \setminus B) \setminus C = A \setminus (B \setminus C)$. *(Recall: $X \setminus Y = X \cap Y^c$.)*
6. $(A \cup B) \setminus (A \cap B) = (A \setminus B) \cup (B \setminus A)$.
7. $A \cap (B \triangle C) = (A \cap B) \triangle (A \cap C)$. *(Intersection distributes over symmetric difference.)*

---

---

# Solutions

## Solution 1

**1. Prove: $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$**

**($\subseteq$):** Let $x \in A \cap (B \cup C)$. Then $x \in A$ and ($x \in B$ or $x \in C$).
- If $x \in B$: then $x \in A \cap B$, so $x \in (A \cap B) \cup (A \cap C)$.
- If $x \in C$: then $x \in A \cap C$, so $x \in (A \cap B) \cup (A \cap C)$.
Either way, $x \in (A \cap B) \cup (A \cap C)$.

**($\supseteq$):** Let $x \in (A \cap B) \cup (A \cap C)$. Then $x \in A \cap B$ or $x \in A \cap C$.
- If $x \in A \cap B$: then $x \in A$ and $x \in B \subseteq B \cup C$, so $x \in A \cap (B \cup C)$.
- If $x \in A \cap C$: then $x \in A$ and $x \in C \subseteq B \cup C$, so $x \in A \cap (B \cup C)$.
Either way, $x \in A \cap (B \cup C)$. ✅

**2. Prove: $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$**

**($\subseteq$):** Let $x \in A \cup (B \cap C)$. Then $x \in A$ or ($x \in B$ and $x \in C$).
- If $x \in A$: then $x \in A \cup B$ and $x \in A \cup C$, so $x \in (A \cup B) \cap (A \cup C)$.
- If $x \in B$ and $x \in C$: then $x \in A \cup B$ and $x \in A \cup C$, so $x \in (A \cup B) \cap (A \cup C)$.

**($\supseteq$):** Let $x \in (A \cup B) \cap (A \cup C)$. Then $x \in A \cup B$ and $x \in A \cup C$.
- If $x \in A$: then $x \in A \cup (B \cap C)$.
- If $x \notin A$: then from $x \in A \cup B$, we get $x \in B$. From $x \in A \cup C$, we get $x \in C$. So $x \in B \cap C \subseteq A \cup (B \cap C)$.
Either way, $x \in A \cup (B \cap C)$. ✅

**3.** See Solution 7 in `04_de_morgan_deep_dive.md`.

**4. Prove: $(A \cap B) \cup (A \cap B^c) = A$**

**($\subseteq$):** Let $x \in (A \cap B) \cup (A \cap B^c)$. Then $x \in A \cap B$ or $x \in A \cap B^c$. In either case, $x \in A$.

**($\supseteq$):** Let $x \in A$. Then either $x \in B$ or $x \notin B$.
- If $x \in B$: $x \in A \cap B$.
- If $x \notin B$: $x \in A \cap B^c$.
Either way, $x \in (A \cap B) \cup (A \cap B^c)$. ✅

## Solution 2

1. $(A \cap B) \cup (A^c \cap B)$
   $= (B \cap A) \cup (B \cap A^c)$ — *commutative*
   $= B \cap (A \cup A^c)$ — *distributive*
   $= B \cap U$ — *complement*
   $= B$ — *identity* ✅

2. $(A \cup B) \cap (A \cup C) = A \cup (B \cap C)$ — *distributive law* ✅

3. $(A \cap B) \cup (A^c \cap C) \cup (B \cap C)$

   This is the **Consensus Theorem**. See Solution 8.1 below. The result is $(A \cap B) \cup (A^c \cap C)$.

4. $A \cup (A^c \cap B) = (A \cup A^c) \cap (A \cup B) = U \cap (A \cup B) = A \cup B$ — *distributive → complement → identity* ✅

5. $(A \cap B)^c \cap A$
   $= (A^c \cup B^c) \cap A$ — *De Morgan*
   $= (A^c \cap A) \cup (B^c \cap A)$ — *distributive*
   $= \emptyset \cup (A \cap B^c)$ — *complement + identity*
   $= A \cap B^c$ ✅

6. $(A \cup B^c) \cap (B \cup A^c)$
   $= (A \cap B) \cup (A \cap A^c) \cup (B^c \cap B) \cup (B^c \cap A^c)$ — *distributive (expand all four terms)*
   $= (A \cap B) \cup \emptyset \cup \emptyset \cup (A^c \cap B^c)$ — *complement*
   $= (A \cap B) \cup (A^c \cap B^c)$ — *identity* ✅

## Solution 3

1. **$A \cap (B \cup C) \subseteq (A \cap B) \cup C$: True.**

   Let $x \in A \cap (B \cup C)$. Then $x \in A$ and ($x \in B$ or $x \in C$).
   - If $x \in B$: $x \in A \cap B \subseteq (A \cap B) \cup C$.
   - If $x \in C$: $x \in C \subseteq (A \cap B) \cup C$.

   **Equality?** No. Counterexample: $A = \{1,2\}, B = \{3\}, C = \{3\}$. LHS: $A \cap (B \cup C) = \{1,2\} \cap \{3\} = \emptyset$. RHS: $(A \cap B) \cup C = \emptyset \cup \{3\} = \{3\}$. Not equal.

2. **$(A \cup B) \cap C \subseteq (A \cap C) \cup B$: True.**

   Let $x \in (A \cup B) \cap C$. Then $x \in A \cup B$ and $x \in C$.
   - If $x \in A$: then $x \in A \cap C \subseteq (A \cap C) \cup B$.
   - If $x \in B$: $x \in B \subseteq (A \cap C) \cup B$.

   **Equality?** No. Counterexample: $A = \emptyset, B = \{1\}, C = \{2\}$. LHS: $\{1\} \cap \{2\} = \emptyset$. RHS: $\emptyset \cup \{1\} = \{1\}$. Not equal.

3. **$A \setminus (B \cap C) = (A \setminus B) \cup (A \setminus C)$: Prove it's True.**

   $A \setminus (B \cap C) = A \cap (B \cap C)^c = A \cap (B^c \cup C^c)$ — *De Morgan*
   $= (A \cap B^c) \cup (A \cap C^c)$ — *distributive*
   $= (A \setminus B) \cup (A \setminus C)$ ✅

4. **$A \setminus (B \cup C) = (A \setminus B) \cap (A \setminus C)$: Prove it's True.**

   $A \setminus (B \cup C) = A \cap (B \cup C)^c = A \cap (B^c \cap C^c)$ — *De Morgan*
   $= (A \cap B^c) \cap (A \cap C^c)$ — *associative/commutative*
   $= (A \setminus B) \cap (A \setminus C)$ ✅

5. **$(A \cap B) \setminus C = A \cap (B \setminus C)$: Prove it's True.**

   LHS: $(A \cap B) \setminus C = (A \cap B) \cap C^c = A \cap B \cap C^c$ — *associative*
   RHS: $A \cap (B \setminus C) = A \cap (B \cap C^c) = A \cap B \cap C^c$ — *associative*
   LHS = RHS ✅

## Solution 4

1. **LHS:** $\chi_{A \cap (B \cup C)} = \chi_A \cdot \chi_{B \cup C} = \chi_A(\chi_B + \chi_C - \chi_B\chi_C)$
   $= \chi_A\chi_B + \chi_A\chi_C - \chi_A\chi_B\chi_C$

   **RHS:** $\chi_{(A\cap B)\cup(A\cap C)} = \chi_{A\cap B} + \chi_{A\cap C} - \chi_{A\cap B}\cdot\chi_{A\cap C}$
   $= \chi_A\chi_B + \chi_A\chi_C - (\chi_A\chi_B)(\chi_A\chi_C)$
   $= \chi_A\chi_B + \chi_A\chi_C - \chi_A^2\chi_B\chi_C$
   $= \chi_A\chi_B + \chi_A\chi_C - \chi_A\chi_B\chi_C$ (since $\chi_A^2 = \chi_A$)

   LHS = RHS ✅

2. **LHS:** $\chi_{(A\cup B)^c} = 1 - \chi_{A\cup B} = 1 - (\chi_A + \chi_B - \chi_A\chi_B)$
   $= 1 - \chi_A - \chi_B + \chi_A\chi_B$
   $= (1-\chi_A)(1-\chi_B)$
   $= \chi_{A^c}\cdot\chi_{B^c}$
   $= \chi_{A^c \cap B^c}$

   **RHS:** $\chi_{A^c \cap B^c} = \chi_{A^c} \cdot \chi_{B^c} = (1-\chi_A)(1-\chi_B) = 1 - \chi_A - \chi_B + \chi_A\chi_B$

   LHS = RHS ✅

3. **LHS:** $\chi_{A \cup (A \cap B)} = \chi_A + \chi_{A\cap B} - \chi_A \cdot \chi_{A\cap B}$
   $= \chi_A + \chi_A\chi_B - \chi_A \cdot \chi_A\chi_B$
   $= \chi_A + \chi_A\chi_B - \chi_A\chi_B$ (since $\chi_A^2 = \chi_A$)
   $= \chi_A$

   **RHS:** $\chi_A$

   LHS = RHS ✅

## Solution 5

1. **Given $A \subseteq B$:**
   - $A \cup B = B$: Since $A \subseteq B$, every element of $A \cup B$ is in $B$, and $B \subseteq A \cup B$. So $A \cup B = B$.
   - $A \cap B = A$: Since $A \subseteq B$, $A \cap B = A$ (every element of $A$ is already in $B$).

2. **Given $A \cap B = \emptyset$:**
   - $A \subseteq B^c$: Let $x \in A$. If $x \in B$, then $x \in A \cap B = \emptyset$ — contradiction. So $x \notin B$, meaning $x \in B^c$.
   - $B \subseteq A^c$: By symmetry (swap $A$ and $B$).

3. **Given $A \cup B = U$:**
   - $A^c \subseteq B$: Let $x \in A^c$, so $x \notin A$. Since $A \cup B = U$, $x \in A \cup B$, so $x \in B$.
   - $B^c \subseteq A$: By symmetry.

4. **Given $A \subseteq B \cap C$:**
   - $A \subseteq B$: Let $x \in A \subseteq B \cap C$. Then $x \in B \cap C$, so $x \in B$.
   - $A \subseteq C$: Similarly, $x \in B \cap C$ implies $x \in C$.

5. **Given $A \subseteq B$ and $C \subseteq D$:**
   - $A \cup C \subseteq B \cup D$: Let $x \in A \cup C$. If $x \in A \subseteq B$, then $x \in B \cup D$. If $x \in C \subseteq D$, then $x \in B \cup D$.
   - $A \cap C \subseteq B \cap D$: Let $x \in A \cap C$. Then $x \in A \subseteq B$ and $x \in C \subseteq D$, so $x \in B \cap D$.

6. **Given $A \cap B = A$ (i.e., $A \subseteq B$):** This means $A \subseteq B$, so by part 1, $A \cup B = B$.

7. **Given $A \cup B = A$ (i.e., $B \subseteq A$):** This means $B \subseteq A$, so by part 1 (with roles swapped), $A \cap B = B$.

## Solution 6

1. $A \triangle B = (A \cap B^c) \cup (A^c \cap B) = \{1,2\} \cup \{5,6\} = \{1,2,5,6\}$.

2. **Prove: $A \triangle B = (A \cup B) \cap (A \cap B)^c$**

   $(A \cup B) \cap (A \cap B)^c = (A \cup B) \cap (A^c \cup B^c)$ — *De Morgan*
   $= (A \cap (A^c \cup B^c)) \cup (B \cap (A^c \cup B^c))$ — *distributive*
   $= (A \cap A^c) \cup (A \cap B^c) \cup (B \cap A^c) \cup (B \cap B^c)$ — *distributive*
   $= \emptyset \cup (A \cap B^c) \cup (A^c \cap B) \cup \emptyset$ — *complement*
   $= (A \cap B^c) \cup (A^c \cap B) = A \triangle B$ ✅

3. **Prove: $A \triangle B = (A \cup B) \cap (A^c \cup B^c)$**

   This is exactly what we derived in Solution 6.2 above (the second line). ✅

4. $A \triangle \emptyset = (A \cap \emptyset^c) \cup (A^c \cap \emptyset) = (A \cap U) \cup \emptyset = A \cup \emptyset = A$ ✅

5. $A \triangle A = (A \cap A^c) \cup (A^c \cap A) = \emptyset \cup \emptyset = \emptyset$ ✅

6. $A \triangle U = (A \cap U^c) \cup (A^c \cap U) = (A \cap \emptyset) \cup A^c = \emptyset \cup A^c = A^c$ ✅

7. $A \triangle A^c = (A \cap (A^c)^c) \cup (A^c \cap A^c) = (A \cap A) \cup A^c = A \cup A^c = U$ ✅

8. **Prove: $(A \triangle B)^c = (A \cap B) \cup (A^c \cap B^c)$**

   $A \triangle B = (A \cap B^c) \cup (A^c \cap B)$

   $(A \triangle B)^c = ((A \cap B^c) \cup (A^c \cap B))^c$
   $= (A \cap B^c)^c \cap (A^c \cap B)^c$ — *De Morgan*
   $= (A^c \cup B) \cap (A \cup B^c)$ — *De Morgan + double complement*
   $= (A \cap B) \cup (A^c \cap B^c)$ — *See Solution 2.6* ✅

   **Interpretation:** The complement of the symmetric difference is the set of elements that are in **both** $A$ and $B$, or in **neither** — i.e., elements where $A$ and $B$ "agree."

## Solution 7

1. $(A \cup B) \cap (A^c \cup B) \cap (A \cup B^c) \cap (A^c \cup B^c)$

   Group: $[(A \cup B) \cap (A \cup B^c)] \cap [(A^c \cup B) \cap (A^c \cup B^c)]$

   First: $(A \cup B) \cap (A \cup B^c) = A \cup (B \cap B^c) = A \cup \emptyset = A$ — *distributive → complement → identity*

   Second: $(A^c \cup B) \cap (A^c \cup B^c) = A^c \cup (B \cap B^c) = A^c \cup \emptyset = A^c$ — *same*

   Result: $A \cap A^c = \emptyset$ ✅

2. $[(A \cap B) \cup (A \cap C)] \cap [(B \cap C) \cup A^c]$

   First: $(A \cap B) \cup (A \cap C) = A \cap (B \cup C)$ — *distributive*

   So: $[A \cap (B \cup C)] \cap [(B \cap C) \cup A^c]$
   $= A \cap (B \cup C) \cap (B \cap C) \cup A \cap (B \cup C) \cap A^c$
   $= A \cap (B \cap C) \cup \emptyset$ — *second term: $A \cap A^c = \emptyset$; first term: $B \cap C \subseteq B \cup C$*
   $= A \cap B \cap C$

   Result: $A \cap B \cap C$ ✅

3. $(A \cup B \cup C) \cap (A^c \cup B \cup C) \cap (A \cup B^c \cup C) \cap (A \cup B \cup C^c)$

   **Step 1:** Pair the first two (which differ only in $A$ vs $A^c$):
   $(A \cup B \cup C) \cap (A^c \cup B \cup C) = (A \cap A^c) \cup (B \cup C) = \emptyset \cup (B \cup C) = B \cup C$
   — *distributive (factor out $B \cup C$) → complement → identity*

   **Step 2:** Pair the last two (which differ in $B$ vs $B^c$ and $C$ vs $C^c$). Instead, pair the 1st with the 3rd and the 2nd with the 4th:

   $(A \cup B \cup C) \cap (A \cup B^c \cup C) = A \cup C \cup (B \cap B^c) = A \cup C$
   — *distributive (factor out $A \cup C$) → complement → identity*

   $(A^c \cup B \cup C) \cap (A \cup B \cup C^c)$ — these don't pair as neatly. Let's use a different approach.

   **Alternative approach:** After Step 1, we have $(B \cup C) \cap (A \cup B^c \cup C) \cap (A \cup B \cup C^c)$.

   **Step 2a:** $(B \cup C) \cap (A \cup B^c \cup C)$: factor out $C$ using $(X \cup C) \cap (Y \cup C) = C \cup (X \cap Y)$ with $X = B$, $Y = A \cup B^c$:
   $= C \cup (B \cap (A \cup B^c)) = C \cup ((B \cap A) \cup (B \cap B^c)) = C \cup (A \cap B) \cup \emptyset = C \cup (A \cap B)$
   — *distributive → complement → identity*

   **Step 2b:** $(C \cup (A \cap B)) \cap (A \cup B \cup C^c)$
   $= (C \cap (A \cup B \cup C^c)) \cup ((A \cap B) \cap (A \cup B \cup C^c))$ — *distributive*

   $C \cap (A \cup B \cup C^c) = (A \cap C) \cup (B \cap C) \cup (C \cap C^c) = (A \cap C) \cup (B \cap C)$ — *distributive → complement*

   $(A \cap B) \cap (A \cup B \cup C^c) = (A \cap B) \cup (A \cap B \cap C^c) = A \cap B$ — *distributive → absorption ($A \cap B \cap C^c \subseteq A \cap B$)*

   **Step 3:** Combine: $(A \cap C) \cup (B \cap C) \cup (A \cap B)$

   **Result:** $(A \cap B) \cup (B \cap C) \cup (A \cap C)$ — the set of elements in **at least two** of the three sets. ✅

4. $(A \cap B^c) \cup (A^c \cap B) \cup (A \cap B)$
   $= (A \cap B^c) \cup (A^c \cap B) \cup (A \cap B)$
   $= (A \cap B^c) \cup [(A^c \cap B) \cup (A \cap B)]$ — *associative*
   $= (A \cap B^c) \cup [B \cap (A^c \cup A)]$ — *distributive*
   $= (A \cap B^c) \cup [B \cap U]$ — *complement*
   $= (A \cap B^c) \cup B$ — *identity*
   $= (A \cup B) \cap (B^c \cup B)$ — *distributive*
   $= (A \cup B) \cap U$ — *complement*
   $= A \cup B$ — *identity* ✅

   **Interpretation:** Elements in exactly one of $A, B$ plus elements in both = elements in at least one = $A \cup B$.

5. $(A \cap B \cap C) \cup (A \cap B \cap C^c) \cup (A \cap B^c \cap C) \cup (A^c \cap B \cap C)$

   These are the 4 Venn diagram regions where an element is in **at least two** of the three sets.

   **Step 1:** Combine the first two terms:
   $(A \cap B \cap C) \cup (A \cap B \cap C^c) = A \cap B \cap (C \cup C^c) = A \cap B \cap U = A \cap B$
   — *distributive → complement → identity*

   **Step 2:** Now simplify $(A \cap B) \cup (A \cap B^c \cap C) \cup (A^c \cap B \cap C)$.

   Expand $A \cap B = (A \cap B) \cap (C \cup C^c) = (A \cap B \cap C) \cup (A \cap B \cap C^c)$:
   
   $(A \cap B \cap C) \cup (A \cap B \cap C^c) \cup (A \cap B^c \cap C) \cup (A^c \cap B \cap C)$

   Now regroup:
   $= [(A \cap B \cap C) \cup (A \cap B^c \cap C)] \cup [(A \cap B \cap C^c) \cup (A \cap B \cap C)] \cup [(A^c \cap B \cap C) \cup (A \cap B \cap C)]$

   Simpler approach — group by pairs:
   $(A \cap B \cap C^c) \cup (A \cap B^c \cap C) = A \cap [(B \cap C^c) \cup (B^c \cap C)] = A \cap (B \triangle C)$

   So: $(A \cap B) \cup (A \cap (B \triangle C)) \cup (A^c \cap B \cap C)$

   Alternatively, recognize that the four original terms are exactly the **at-least-two** regions of the Venn diagram, which equals $(A \cap B) \cup (B \cap C) \cup (A \cap C)$ (as shown in Solution 7.3).

   **Direct verification:** $(A \cap B) \cup (B \cap C) \cup (A \cap C)$ expanded:
   $= (A \cap B \cap (C \cup C^c)) \cup (B \cap C \cap (A \cup A^c)) \cup (A \cap C \cap (B \cup B^c))$
   $= (A \cap B \cap C) \cup (A \cap B \cap C^c) \cup (A \cap B \cap C) \cup (A^c \cap B \cap C) \cup (A \cap B \cap C) \cup (A \cap B^c \cap C)$
   $= (A \cap B \cap C) \cup (A \cap B \cap C^c) \cup (A^c \cap B \cap C) \cup (A \cap B^c \cap C)$ (removing duplicates by idempotence)

   **Result:** $(A \cap B) \cup (B \cap C) \cup (A \cap C)$ — the set of elements in **at least two** of the three sets. ✅

## Solution 8

**1. Consensus Theorem: $(A \cap B) \cup (A^c \cap C) \cup (B \cap C) = (A \cap B) \cup (A^c \cap C)$**

We need to show $B \cap C$ is absorbed. Add and subtract nothing:

$(A \cap B) \cup (A^c \cap C) \cup (B \cap C)$

$= (A \cap B) \cup (A^c \cap C) \cup [(B \cap C) \cap (A \cup A^c)]$ — *since $A \cup A^c = U$*

$= (A \cap B) \cup (A^c \cap C) \cup [(B \cap C \cap A) \cup (B \cap C \cap A^c)]$ — *distributive*

$= (A \cap B) \cup (A^c \cap C) \cup (A \cap B \cap C) \cup (A^c \cap B \cap C)$

Now, $A \cap B \cap C \subseteq A \cap B$, so $(A \cap B) \cup (A \cap B \cap C) = A \cap B$ (absorption).

Similarly, $A^c \cap B \cap C \subseteq A^c \cap C$, so $(A^c \cap C) \cup (A^c \cap B \cap C) = A^c \cap C$ (absorption).

$= (A \cap B) \cup (A^c \cap C)$ ✅

**2. Dual form: $(A \cup B) \cap (A^c \cup C) \cap (B \cup C) = (A \cup B) \cap (A^c \cup C)$**

This follows by the **duality principle** (swap $\cap \leftrightarrow \cup$ and $\emptyset \leftrightarrow U$). But let's verify directly:

$(A \cup B) \cap (A^c \cup C) \cap (B \cup C)$

$= (A \cup B) \cap (A^c \cup C) \cap [(B \cup C) \cap (A \cup A^c)]$

$= (A \cup B) \cap (A^c \cup C) \cap [(A \cap B \cup A \cap C \cup A^c \cap B \cup A^c \cap C)]$

This gets messy. Instead, use the first form and duality:

By the duality principle, if $(X \cap Y) \cup (X^c \cap Z) \cup (Y \cap Z) = (X \cap Y) \cup (X^c \cap Z)$, then replacing $\cap$ with $\cup$ and vice versa: $(X \cup Y) \cap (X^c \cup Z) \cap (Y \cup Z) = (X \cup Y) \cap (X^c \cup Z)$. ✅

**3. Simplify: $(A \cap B) \cup (A^c \cap C) \cup (B \cap C \cap D)$**

$B \cap C \cap D \subseteq B \cap C$, so by the Consensus Theorem, $B \cap C$ would be absorbed. Since $B \cap C \cap D \subseteq B \cap C$, it is also absorbed:

$(A \cap B) \cup (A^c \cap C) \cup (B \cap C \cap D) \subseteq (A \cap B) \cup (A^c \cap C) \cup (B \cap C) = (A \cap B) \cup (A^c \cap C)$

And clearly $(A \cap B) \cup (A^c \cap C) \subseteq (A \cap B) \cup (A^c \cap C) \cup (B \cap C \cap D)$.

**Result:** $(A \cap B) \cup (A^c \cap C)$ ✅

**4. Simplify: $(A \cap B) \cup (A^c \cap B^c) \cup (B \cap C)$**

The consensus of $(A \cap B)$ and $(A^c \cap B^c)$ would be $B \cap B^c = \emptyset$, which is trivial. So $B \cap C$ is **not** a consensus term and cannot be absorbed.

$(A \cap B) \cup (A^c \cap B^c) \cup (B \cap C)$
$= [B \cap (A \cup C)] \cup (A^c \cap B^c)$ — *distributive (factor $B$ from first and third terms)*
$= (A \cap B) \cup (B \cap C) \cup (A^c \cap B^c)$

No further simplification is possible using the standard laws.

**Result:** $(A \cap B) \cup (A^c \cap B^c) \cup (B \cap C)$ — cannot be simplified further.

## Solution 9

1. **True.** $(A \cap B) \cup C = A \cap (B \cup C) \iff C \subseteq A$.

   **($\Leftarrow$) If $C \subseteq A$:** $A \cap (B \cup C) = (A \cap B) \cup (A \cap C) = (A \cap B) \cup C$ (since $C \subseteq A$ implies $A \cap C = C$).

   **($\Rightarrow$) If $(A \cap B) \cup C = A \cap (B \cup C)$:** We need to show $C \subseteq A$.
   
   RHS $= (A \cap B) \cup (A \cap C)$. So the equation becomes $(A \cap B) \cup C = (A \cap B) \cup (A \cap C)$.
   
   Let $x \in C$. Then $x \in (A \cap B) \cup C = (A \cap B) \cup (A \cap C)$. If $x \in A \cap B$, then $x \in A$. If $x \in A \cap C$, then $x \in A$. Either way $x \in A$. So $C \subseteq A$. ✅

2. **True.** $(A \cup B) \cap C = A \cup (B \cap C) \iff A \subseteq C$.

   **($\Leftarrow$) If $A \subseteq C$:** $A \cup (B \cap C) = (A \cup B) \cap (A \cup C) = (A \cup B) \cap C$ (since $A \subseteq C$ implies $A \cup C = C$).

   **($\Rightarrow$) If $(A \cup B) \cap C = A \cup (B \cap C)$:** LHS $= (A \cap C) \cup (B \cap C)$. So $(A \cap C) \cup (B \cap C) = A \cup (B \cap C)$.
   
   Let $x \in A$. Then $x \in A \cup (B \cap C) = (A \cap C) \cup (B \cap C)$. If $x \in A \cap C$, then $x \in C$. If $x \in B \cap C$, then $x \in C$. Either way $x \in C$. So $A \subseteq C$. ✅

3. **True.** $A \triangle B = \emptyset \iff A = B$.

   **($\Rightarrow$)** If $A \triangle B = \emptyset$, then no element is in exactly one of $A, B$. So every element is in both or neither: $A = B$.

   **($\Leftarrow$)** If $A = B$, then $A \triangle B = A \triangle A = \emptyset$. ✅

4. **True.** If $A \subseteq B$, $A \subseteq C$, and $B \cap C = \emptyset$, then $A \subseteq B \cap C = \emptyset$, so $A = \emptyset$. ✅

5. **False.** $(A \setminus B) \setminus C = (A \cap B^c) \cap C^c = A \cap B^c \cap C^c = A \cap (B \cup C)^c = A \setminus (B \cup C)$.
   
   But $A \setminus (B \setminus C) = A \cap (B \cap C^c)^c = A \cap (B^c \cup C)$.
   
   These are different. Counterexample: $A = \{1,2,3\}, B = \{2\}, C = \{3\}$.
   - LHS: $A \setminus B = \{1,3\}$, then $\{1,3\} \setminus \{3\} = \{1\}$.
   - RHS: $B \setminus C = \{2\}$, then $A \setminus \{2\} = \{1,3\}$.
   - $\{1\} \neq \{1,3\}$. ✅

6. **True.** $(A \cup B) \setminus (A \cap B) = (A \cup B) \cap (A \cap B)^c = (A \cup B) \cap (A^c \cup B^c)$.
   
   $(A \setminus B) \cup (B \setminus A) = (A \cap B^c) \cup (B \cap A^c)$.
   
   These are both equal to $A \triangle B$ (see Solution 6.2). ✅

7. **True.** $A \cap (B \triangle C) = (A \cap B) \triangle (A \cap C)$.

   $B \triangle C = (B \cap C^c) \cup (B^c \cap C)$.
   
   LHS: $A \cap [(B \cap C^c) \cup (B^c \cap C)] = (A \cap B \cap C^c) \cup (A \cap B^c \cap C)$ — *distributive*
   
   RHS: $(A \cap B) \triangle (A \cap C) = ((A \cap B) \cap (A \cap C)^c) \cup ((A \cap B)^c \cap (A \cap C))$

   $(A \cap C)^c = A^c \cup C^c$ — *De Morgan*.

   $(A \cap B) \cap (A^c \cup C^c) = (A \cap B \cap A^c) \cup (A \cap B \cap C^c) = \emptyset \cup (A \cap B \cap C^c) = A \cap B \cap C^c$
   — *distributive → complement → identity*

   Similarly, $(A \cap B)^c = A^c \cup B^c$.

   $(A \cap C) \cap (A^c \cup B^c) = (A \cap C \cap A^c) \cup (A \cap C \cap B^c) = \emptyset \cup (A \cap B^c \cap C) = A \cap B^c \cap C$
   — *distributive → complement → identity*

   So RHS $= (A \cap B \cap C^c) \cup (A \cap B^c \cap C)$ = LHS. ✅
