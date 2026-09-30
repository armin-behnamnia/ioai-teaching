# Set Algebra — De Morgan's Laws Deep Dive

## Learning Objectives

- Develop a **deep, intuitive** understanding of De Morgan's Laws.
- Practice applying De Morgan's Laws in **both directions**.
- See how De Morgan's Laws connect **complement** with **union** and **intersection**.
- Translate between **set-builder notation** and **logical connectives** (and/or/not).

---

## Problem 1 — Intuitive Understanding

Consider the universal set $U = \{1, 2, \ldots, 12\}$, $A = \{n \in U \mid n \text{ is even}\}$, $B = \{n \in U \mid n \text{ is greater than } 6\}$.

1. Describe in plain English: what does $A \cup B$ represent?
2. Describe in plain English: what does $(A \cup B)^c$ represent?
3. Describe in plain English: what does $A^c$ represent?
4. Describe in plain English: what does $B^c$ represent?
5. Describe in plain English: what does $A^c \cap B^c$ represent?
6. Compare your answers to parts 2 and 5. Are they the same? **Why?**
7. Now describe $(A \cap B)^c$ in plain English and compare to $A^c \cup B^c$.

---

## Problem 2 — Applying De Morgan's Laws

Use De Morgan's Laws to rewrite each expression **without parentheses** (i.e., express the complement of a union/intersection as a combination of complements).

1. $(A \cup B)^c$
2. $(A \cap B)^c$
3. $(A \cup B \cup C)^c$
4. $(A \cap B \cap C)^c$
5. $(A^c \cup B)^c$
6. $(A \cap B^c)^c$
7. $(A^c \cup B^c)^c$
8. $((A \cup B) \cap C)^c$
9. $((A \cap B) \cup (C \cap D))^c$
10. $(A \cup (B \cap C^c))^c$

---

## Problem 3 — Reverse Application

Use De Morgan's Laws to **combine** complements into a single complemented expression.

1. $A^c \cap B^c$
2. $A^c \cup B^c$
3. $A^c \cap B^c \cap C^c$
4. $A^c \cup B^c \cup C^c$
5. $A \cap B^c$ → rewrite as a single complemented union
6. $A^c \cup B$ → rewrite as a single complemented intersection

> **Hint for 5 and 6:** First note that $A = (A^c)^c$ and $B = (B^c)^c$, then apply De Morgan.

---

## Problem 4 — Simplifying with De Morgan

Simplify each expression as much as possible.

1. $(A \cup B)^c \cap (A^c \cup B^c)$
2. $(A \cap B)^c \cap (A^c \cap B^c)$
3. $(A^c \cup B^c) \cap A$
4. $(A \cup B^c)^c \cup A$
5. $(A \cap B)^c \cap A$
6. $(A \cup B)^c \cup A$
7. $((A \cup B)^c \cup (A \cap B)^c)^c$

---

## Problem 5 — Connecting to Logic

De Morgan's Laws in **logic** state:
- $\neg(P \land Q) \equiv \neg P \lor \neg Q$
- $\neg(P \lor Q) \equiv \neg P \land \neg Q$

Each set operation corresponds to a logical connective:

| Set Operation | Logical Connective | Meaning |
|---|---|---|
| $x \in A \cap B$ | $P \land Q$ | $x \in A$ **and** $x \in B$ |
| $x \in A \cup B$ | $P \lor Q$ | $x \in A$ **or** $x \in B$ |
| $x \in A^c$ | $\neg P$ | $x \notin A$ |

**Task:** For each of the following set expressions, (a) translate to a logical statement, (b) apply De Morgan's Law in logic, (c) translate back to set notation.

1. $(A \cup B)^c$
2. $(A \cap B)^c$
3. $(A \cup B \cup C)^c$
4. $(A^c \cap B)^c$

---

## Problem 6 — De Morgan with Three Sets

Let $U = \{1, 2, \ldots, 15\}$, $A = \{1, 2, 3, 4, 5\}$, $B = \{3, 4, 5, 6, 7\}$, $C = \{5, 6, 7, 8, 9\}$.

Compute **both sides** of each De Morgan identity and verify they are equal:

1. $(A \cup B \cup C)^c$ and $A^c \cap B^c \cap C^c$
2. $(A \cap B \cap C)^c$ and $A^c \cup B^c \cup C^c$
3. $((A \cup B) \cap C)^c$ and $(A \cap C)^c \cup (B \cap C)^c$ — this combines distributive + De Morgan
4. $((A \cap B) \cup C)^c$ and $(A \cup C)^c \cap (B \cup C)^c$ — this combines distributive + De Morgan

---

## Problem 7 — Proving De Morgan's Laws

**Prove** De Morgan's Laws using element-wise arguments (i.e., show that each element of one side is in the other, and vice versa).

1. Prove: $(A \cup B)^c = A^c \cap B^c$
2. Prove: $(A \cap B)^c = A^c \cup B^c$

> **Template for a proof:**
> 
> **($\subseteq$ direction):** Let $x$ be an arbitrary element of the left side. Show $x$ is in the right side.
>
> **($\supseteq$ direction):** Let $x$ be an arbitrary element of the right side. Show $x$ is in the left side.

---

## Problem 8 — Real-World Interpretation

A survey of 100 students finds:
- 60 students take **Math** (set $M$)
- 50 students take **Physics** (set $P$)
- 40 students take **Chemistry** (set $C$)

Express each group using set notation and **simplify using De Morgan's Laws**:

1. Students who take **none** of the three subjects.
2. Students who do **not** take both Math and Physics.
3. Students who don't take Math **or** don't take Physics.
4. Students who take at least one subject but not all three. *(Express using complement.)*
5. Students who take **exactly one** subject. *(Express using only union, intersection, and complement.)*

---

## Problem 9 — Challenge: Generalized De Morgan

**Prove by induction** (or by repeated application) that for any $n$ sets $A_1, A_2, \ldots, A_n$:

1. $(A_1 \cup A_2 \cup \cdots \cup A_n)^c = A_1^c \cap A_2^c \cap \cdots \cap A_n^c$
2. $(A_1 \cap A_2 \cap \cdots \cap A_n)^c = A_1^c \cup A_2^c \cup \cdots \cup A_n^c$

> **Hint:** Use the base case $n = 2$ (which you proved in Problem 7), then for the inductive step, treat $A_1 \cup \cdots \cup A_{n+1}$ as $(A_1 \cup \cdots \cup A_n) \cup A_{n+1}$ and apply the two-set version.

---

---

# Solutions

## Solution 1

1. $A \cup B$: numbers that are even **or** greater than 6.
2. $(A \cup B)^c$: numbers that are **neither** even **nor** greater than 6 — i.e., odd numbers $\leq 6$.
3. $A^c$: odd numbers.
4. $B^c$: numbers $\leq 6$.
5. $A^c \cap B^c$: odd numbers **and** $\leq 6$ — i.e., $\{1, 3, 5\}$.
6. **Yes, they are the same.** $(A \cup B)^c = A^c \cap B^c$ by De Morgan's Law. "Not (even or $>6$)" is the same as "not even **and** not $>6$," i.e., "odd and $\leq 6$."
7. $A \cap B = \{8, 10, 12\}$ (even numbers $> 6$). $(A \cap B)^c = \{1,2,3,4,5,6,7,9,11\}$ — numbers that are odd **or** $\leq 6$. $A^c \cup B^c = \{1,3,5,7,9,11\} \cup \{1,2,3,4,5,6\} = \{1,2,3,4,5,6,7,9,11\}$. **Same!** This is De Morgan's other law: $(A \cap B)^c = A^c \cup B^c$.

## Solution 2

1. $(A \cup B)^c = A^c \cap B^c$
2. $(A \cap B)^c = A^c \cup B^c$
3. $(A \cup B \cup C)^c = A^c \cap B^c \cap C^c$
4. $(A \cap B \cap C)^c = A^c \cup B^c \cup C^c$
5. $(A^c \cup B)^c = (A^c)^c \cap B^c = A \cap B^c$
6. $(A \cap B^c)^c = A^c \cup (B^c)^c = A^c \cup B$
7. $(A^c \cup B^c)^c = (A^c)^c \cap (B^c)^c = A \cap B$
8. $((A \cup B) \cap C)^c = (A \cup B)^c \cup C^c = A^c \cap B^c \cup C^c$
9. $((A \cap B) \cup (C \cap D))^c = (A \cap B)^c \cap (C \cap D)^c = (A^c \cup B^c) \cap (C^c \cup D^c)$
10. $(A \cup (B \cap C^c))^c = A^c \cap (B \cap C^c)^c = A^c \cap (B^c \cup C)$

## Solution 3

1. $A^c \cap B^c = (A \cup B)^c$
2. $A^c \cup B^c = (A \cap B)^c$
3. $A^c \cap B^c \cap C^c = (A \cup B \cup C)^c$
4. $A^c \cup B^c \cup C^c = (A \cap B \cap C)^c$
5. $A \cap B^c = (A^c \cup B)^c$ — since $A = (A^c)^c$, so $A \cap B^c = (A^c)^c \cap B^c = (A^c \cup B)^c$.
6. $A^c \cup B = (A \cap B^c)^c$ — since $B = (B^c)^c$, so $A^c \cup (B^c)^c = (A \cap B^c)^c$.

## Solution 4

1. $(A \cup B)^c \cap (A^c \cup B^c)$
   $= (A^c \cap B^c) \cap (A^c \cup B^c)$ — *De Morgan on first term*
   $= A^c \cap B^c$ — *since $A^c \cap B^c \subseteq A^c \cup B^c$, intersection is the smaller set*
   $= (A \cup B)^c$

2. $(A \cap B)^c \cap (A^c \cap B^c)$
   $= (A^c \cup B^c) \cap (A^c \cap B^c)$ — *De Morgan on first term*
   $= A^c \cap B^c$ — *since $A^c \cap B^c \subseteq A^c \cup B^c$, intersection is the smaller set*
   $= (A \cup B)^c$

3. $(A^c \cup B^c) \cap A$
   $= (A \cap B)^c \cap A$ — *De Morgan (reverse)*
   $= (A \cup (A \cap B)^c) \cap A$ — *not helpful directly; let's try another way*
   
   Better: $(A^c \cup B^c) \cap A = (A^c \cap A) \cup (B^c \cap A) = \emptyset \cup (A \cap B^c) = A \cap B^c$ — *distributive → complement → identity*

4. $(A \cup B^c)^c \cup A$
   $= (A^c \cap B) \cup A$ — *De Morgan*
   $= (A \cup A^c) \cap (A \cup B)$ — *distributive*
   $= U \cap (A \cup B)$ — *complement*
   $= A \cup B$ — *identity*

5. $(A \cap B)^c \cap A$
   $= (A^c \cup B^c) \cap A$ — *De Morgan*
   $= (A^c \cap A) \cup (B^c \cap A)$ — *distributive*
   $= \emptyset \cup (A \cap B^c)$ — *complement + identity*
   $= A \cap B^c$

6. $(A \cup B)^c \cup A$
   $= (A^c \cap B^c) \cup A$ — *De Morgan*
   $= (A^c \cup A) \cap (B^c \cup A)$ — *distributive*
   $= U \cap (A \cup B^c)$ — *complement*
   $= A \cup B^c$ — *identity*

7. $((A \cup B)^c \cup (A \cap B)^c)^c$
   First simplify the inside:
   $(A \cup B)^c \cup (A \cap B)^c = (A^c \cap B^c) \cup (A^c \cup B^c)$ — *De Morgan on both*
   Since $A^c \cap B^c \subseteq A^c \cup B^c$, this equals $A^c \cup B^c = (A \cap B)^c$.
   
   Now: $((A \cap B)^c)^c = A \cap B$ — *double complement*

## Solution 5

1. $(A \cup B)^c$:
   - (a) $x \in (A \cup B)^c$ means $\neg(x \in A \lor x \in B)$, i.e., $\neg(P \lor Q)$ where $P = (x \in A), Q = (x \in B)$.
   - (b) $\neg(P \lor Q) \equiv \neg P \land \neg Q$.
   - (c) $\neg P \land \neg Q$ means $x \notin A$ **and** $x \notin B$, i.e., $x \in A^c \cap B^c$.
   - **Result:** $(A \cup B)^c = A^c \cap B^c$ ✅

2. $(A \cap B)^c$:
   - (a) $\neg(P \land Q)$
   - (b) $\neg P \lor \neg Q$
   - (c) $x \in A^c \cup B^c$
   - **Result:** $(A \cap B)^c = A^c \cup B^c$ ✅

3. $(A \cup B \cup C)^c$:
   - (a) $\neg(P \lor Q \lor R)$ where $R = (x \in C)$
   - (b) $\neg P \land \neg Q \land \neg R$ (applying De Morgan twice)
   - (c) $x \in A^c \cap B^c \cap C^c$
   - **Result:** $(A \cup B \cup C)^c = A^c \cap B^c \cap C^c$ ✅

4. $(A^c \cap B)^c$:
   - (a) $\neg(\neg P \land Q)$
   - (b) $\neg(\neg P) \lor \neg Q = P \lor \neg Q$
   - (c) $x \in A \cup B^c$
   - **Result:** $(A^c \cap B)^c = A \cup B^c$ ✅

## Solution 6

$A = \{1,2,3,4,5\}$, $B = \{3,4,5,6,7\}$, $C = \{5,6,7,8,9\}$, $U = \{1,\ldots,15\}$.

1. $A \cup B \cup C = \{1,2,3,4,5,6,7,8,9\}$.
   - LHS: $(A \cup B \cup C)^c = \{10,11,12,13,14,15\}$
   - RHS: $A^c = \{6,7,8,9,10,11,12,13,14,15\}$, $B^c = \{1,2,8,9,10,11,12,13,14,15\}$, $C^c = \{1,2,3,4,10,11,12,13,14,15\}$.
   $A^c \cap B^c \cap C^c = \{10,11,12,13,14,15\}$
   - **Equal** ✅

2. $A \cap B \cap C = \{5\}$.
   - LHS: $(A \cap B \cap C)^c = U \setminus \{5\} = \{1,2,3,4,6,7,8,9,10,11,12,13,14,15\}$
   - RHS: $A^c \cup B^c \cup C^c = \{6,7,8,9,10,11,12,13,14,15\} \cup \{1,2,8,9,10,11,12,13,14,15\} \cup \{1,2,3,4,10,11,12,13,14,15\}$
   $= \{1,2,3,4,6,7,8,9,10,11,12,13,14,15\}$
   - **Equal** ✅

3. $A \cup B = \{1,2,3,4,5,6,7\}$, so $(A \cup B) \cap C = \{5,6,7\}$.
   - LHS: $((A \cup B) \cap C)^c = \{1,2,3,4,8,9,10,11,12,13,14,15\}$
   - $A \cap C = \{5\}$, $B \cap C = \{5,6,7\}$.
   - $(A \cap C)^c = \{1,2,3,4,6,7,8,9,10,11,12,13,14,15\}$
   - $(B \cap C)^c = \{1,2,3,4,8,9,10,11,12,13,14,15\}$
   - RHS: $(A \cap C)^c \cup (B \cap C)^c = \{1,2,3,4,6,7,8,9,10,11,12,13,14,15\}$
   - **Equal** ✅

4. $A \cap B = \{3,4,5\}$, so $(A \cap B) \cup C = \{3,4,5,6,7,8,9\}$.
   - LHS: $((A \cap B) \cup C)^c = \{1,2,10,11,12,13,14,15\}$

   The correct De Morgan application is:
   $((A \cap B) \cup C)^c = (A \cap B)^c \cap C^c = (A^c \cup B^c) \cap C^c$

   - $(A \cap B)^c = \{1,2,6,7,8,9,10,11,12,13,14,15\}$
   - $C^c = \{1,2,3,4,10,11,12,13,14,15\}$
   - RHS: $(A^c \cup B^c) \cap C^c = \{1,2,6,7,8,9,10,11,12,13,14,15\} \cap \{1,2,3,4,10,11,12,13,14,15\} = \{1,2,10,11,12,13,14,15\}$
   - **Equal** ✅

   > **Note:** The expression $(A \cup C)^c \cap (B \cup C)^c$ would be the complement of $(A \cup C) \cup (B \cup C) = A \cup B \cup C$, giving $(A \cup B \cup C)^c = \{10,11,12,13,14,15\}$, which is **not** the same as $((A \cap B) \cup C)^c$. This illustrates that De Morgan's law applies to the **structure** of the expression — the complement of a union becomes an intersection of complements, and vice versa.

## Solution 7

**1. Prove: $(A \cup B)^c = A^c \cap B^c$**

**($\subseteq$):** Let $x \in (A \cup B)^c$. Then $x \notin A \cup B$, meaning $x \notin A$ **and** $x \notin B$. Therefore $x \in A^c$ and $x \in B^c$, so $x \in A^c \cap B^c$.

**($\supseteq$):** Let $x \in A^c \cap B^c$. Then $x \in A^c$ and $x \in B^c$, meaning $x \notin A$ and $x \notin B$. Therefore $x \notin A \cup B$, so $x \in (A \cup B)^c$.

Since both directions hold, $(A \cup B)^c = A^c \cap B^c$. ✅

**2. Prove: $(A \cap B)^c = A^c \cup B^c$**

**($\subseteq$):** Let $x \in (A \cap B)^c$. Then $x \notin A \cap B$, meaning it is **not** the case that $x \in A$ **and** $x \in B$. So $x \notin A$ **or** $x \notin B$ (negation of "and" is "or"). Therefore $x \in A^c$ or $x \in B^c$, so $x \in A^c \cup B^c$.

**($\supseteq$):** Let $x \in A^c \cup B^c$. Then $x \in A^c$ or $x \in B^c$, meaning $x \notin A$ or $x \notin B$. If $x \notin A$, then $x \notin A \cap B$. If $x \notin B$, then $x \notin A \cap B$. Either way, $x \notin A \cap B$, so $x \in (A \cap B)^c$.

Since both directions hold, $(A \cap B)^c = A^c \cup B^c$. ✅

## Solution 8

1. Students taking **none**: $(M \cup P \cup C)^c = M^c \cap P^c \cap C^c$ (De Morgan).

2. Students who do **not** take both Math and Physics: $(M \cap P)^c = M^c \cup P^c$ (De Morgan) — i.e., those who don't take Math or don't take Physics.

3. Students who don't take Math **or** don't take Physics: $M^c \cup P^c = (M \cap P)^c$ (De Morgan, reverse) — same as part 2!

4. Students who take at least one but not all three: $(M \cup P \cup C) \cap (M \cap P \cap C)^c$
   $= (M \cup P \cup C) \cap (M^c \cup P^c \cup C^c)$ (De Morgan).

5. Students who take **exactly one** subject: $(M \cap P^c \cap C^c) \cup (M^c \cap P \cap C^c) \cup (M^c \cap P^c \cap C)$.

   This uses only complement, intersection, and union. Each term picks out students in exactly one subject (in that subject, not in the other two).

## Solution 9

**1. Prove: $(A_1 \cup A_2 \cup \cdots \cup A_n)^c = A_1^c \cap A_2^c \cap \cdots \cap A_n^c$**

**Base case ($n = 2$):** Proved in Solution 7.1.

**Inductive step:** Assume $(A_1 \cup \cdots \cup A_k)^c = A_1^c \cap \cdots \cap A_k^c$ holds for some $k \geq 2$.

Consider $n = k + 1$:
$$(A_1 \cup \cdots \cup A_k \cup A_{k+1})^c = \left((A_1 \cup \cdots \cup A_k) \cup A_{k+1}\right)^c$$

Apply the two-set De Morgan's law (treating $A_1 \cup \cdots \cup A_k$ as one set):
$$= (A_1 \cup \cdots \cup A_k)^c \cap A_{k+1}^c$$

By the inductive hypothesis:
$$= (A_1^c \cap \cdots \cap A_k^c) \cap A_{k+1}^c = A_1^c \cap \cdots \cap A_k^c \cap A_{k+1}^c$$

By induction, the identity holds for all $n \geq 2$. ✅

**2. Prove: $(A_1 \cap A_2 \cap \cdots \cap A_n)^c = A_1^c \cup A_2^c \cup \cdots \cup A_n^c$**

**Base case ($n = 2$):** Proved in Solution 7.2.

**Inductive step:** Assume $(A_1 \cap \cdots \cap A_k)^c = A_1^c \cup \cdots \cup A_k^c$ holds for some $k \geq 2$.

Consider $n = k + 1$:
$$(A_1 \cap \cdots \cap A_k \cap A_{k+1})^c = \left((A_1 \cap \cdots \cap A_k) \cap A_{k+1}\right)^c$$

Apply the two-set De Morgan's law:
$$= (A_1 \cap \cdots \cap A_k)^c \cup A_{k+1}^c$$

By the inductive hypothesis:
$$= (A_1^c \cup \cdots \cup A_k^c) \cup A_{k+1}^c = A_1^c \cup \cdots \cup A_k^c \cup A_{k+1}^c$$

By induction, the identity holds for all $n \geq 2$. ✅
