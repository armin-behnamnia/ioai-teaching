# Set Algebra — Basic Operations

## Learning Objectives

- Practice computing **union**, **intersection**, **complement**, and testing **subset** relationships.
- Build fluency with concrete sets before moving to abstract identities.

---

## Problem 1

Let $A = \{1, 2, 3, 5, 7\}$, $B = \{2, 4, 6, 8\}$, and $C = \{1, 2, 3, 4, 5\}$, all subsets of the universal set $U = \{1, 2, 3, 4, 5, 6, 7, 8\}$.

Find:

1. $A \cup B$
2. $A \cap B$
3. $A^c$ (the complement of $A$)
4. $B \cap C$
5. $(A \cup B)^c$

---

## Problem 2

Let $U = \{a, b, c, d, e, f, g, h\}$, $X = \{a, c, e, g\}$, $Y = \{b, c, d, e\}$, $Z = \{a, b, c, d, e, f\}$.

Find:

1. $X \cup Y$
2. $X \cap Y$
3. $X^c$
4. $Z^c$
5. $(X \cap Y) \cup Z^c$
6. Is $X \subseteq Z$? Justify.
7. Is $Y \subseteq X$? Justify.

---

## Problem 3

Let $U = \mathbb{Z}$ (the set of all integers). Define:

- $A = \{n \in \mathbb{Z} \mid n \text{ is even}\}$
- $B = \{n \in \mathbb{Z} \mid n \text{ is odd}\}$
- $C = \{n \in \mathbb{Z} \mid n \geq 0\}$

Find:

1. $A \cup B$
2. $A \cap B$
3. $A^c$
4. $C^c$
5. $A \cap C$ (describe the elements in words)

---

## Problem 4

Let $U = \{1, 2, 3, \ldots, 20\}$, $P = \{n \in U \mid n \text{ is prime}\}$, $Q = \{n \in U \mid n \text{ is divisible by } 3\}$, $R = \{n \in U \mid n \text{ is divisible by } 5\}$.

Find:

1. $P \cap Q$
2. $P \cap R$
3. $Q \cup R$
4. $Q \cap R$
5. $P^c \cap R$
6. Is $P \subseteq Q$? Justify.

---

## Problem 5

Let $U = \{1, 2, 3, 4, 5, 6\}$. Consider the sets:

- $A = \{1, 3, 5\}$
- $B = \{2, 4, 6\}$
- $C = \{1, 2, 3\}$

Find:

1. $A \cup C$
2. $B \cap C$
3. $(A \cup B)^c$
4. $(A \cap B)^c$
5. $A^c \cap B^c$
6. What do you notice about your answers to parts 3 and 5? Can you explain why?

---

## Problem 6

Let $U = \{x \in \mathbb{R} \mid 0 \leq x \leq 10\}$. Define:

- $A = \{x \in U \mid x < 3\}$
- $B = \{x \in U \mid x > 7\}$
- $C = \{x \in U \mid 2 \leq x \leq 5\}$

Find (describe using interval notation):

1. $A \cup B$
2. $A \cap C$
3. $A^c$
4. $B^c$
5. $A \cap B$
6. Is $C \subseteq A$? Justify.

---

## Problem 7

Determine whether each statement is **true** or **false**. If false, give a counterexample.

1. For any sets $A$ and $B$, $A \cap B \subseteq A$.
2. For any sets $A$ and $B$, $A \subseteq A \cup B$.
3. For any set $A$, $A \subseteq A^c$ is always false.
4. If $A \subseteq B$ and $B \subseteq C$, then $A \subseteq C$.
5. If $A \cap B = \emptyset$, then $A \subseteq B^c$.
6. For any sets $A$ and $B$, $A \cap B \subseteq A \cup B$.

---

## Problem 8

Let $A = \{1, 2, 3\}$, $B = \{3, 4, 5\}$, $C = \{2, 3, 4\}$, and $U = \{1, 2, 3, 4, 5, 6\}$.

For each expression below, first **predict** the answer without computing, then **verify** by computing:

1. $(A \cap B) \cap C$ and $A \cap (B \cap C)$
2. $(A \cup B) \cap C$ and $(A \cap C) \cup (B \cap C)$
3. $(A \cap B)^c$ and $A^c \cup B^c$

---

---

# Solutions

## Solution 1

1. $A \cup B = \{1, 2, 3, 4, 5, 6, 7, 8\} = U$
2. $A \cap B = \{2\}$
3. $A^c = \{4, 6, 8\}$
4. $B \cap C = \{2, 4\}$
5. $(A \cup B)^c = U^c = \emptyset$

## Solution 2

1. $X \cup Y = \{a, b, c, d, e, g\}$
2. $X \cap Y = \{c, e\}$
3. $X^c = \{b, d, f, h\}$
4. $Z^c = \{g, h\}$
5. $(X \cap Y) \cup Z^c = \{c, e\} \cup \{g, h\} = \{c, e, g, h\}$
6. No. $g \in X$ but $g \notin Z$, so $X \not\subseteq Z$.
7. No. $b \in Y$ but $b \notin X$.

## Solution 3

1. $A \cup B = \mathbb{Z}$ (every integer is either even or odd)
2. $A \cap B = \emptyset$ (no integer is both even and odd)
3. $A^c = B$ (the complement of the evens is the odds)
4. $C^c = \{n \in \mathbb{Z} \mid n < 0\}$ (the negative integers)
5. $A \cap C = \{n \in \mathbb{Z} \mid n \geq 0 \text{ and } n \text{ is even}\}$ — the non-negative even integers $\{0, 2, 4, 6, \ldots\}$

## Solution 4

1. $P = \{2, 3, 5, 7, 11, 13, 17, 19\}$, $Q = \{3, 6, 9, 12, 15, 18\}$ → $P \cap Q = \{3\}$
2. $R = \{5, 10, 15, 20\}$ → $P \cap R = \{5\}$
3. $Q \cup R = \{3, 5, 6, 9, 10, 12, 15, 18, 20\}$
4. $Q \cap R = \{15\}$
5. $P^c = \{1, 4, 6, 8, 9, 10, 12, 14, 15, 16, 18, 20\}$ → $P^c \cap R = \{10, 15, 20\}$
6. No. $2 \in P$ but $2 \notin Q$ (2 is not divisible by 3).

## Solution 5

1. $A \cup C = \{1, 2, 3, 5\}$
2. $B \cap C = \{2\}$
3. $A \cup B = \{1, 2, 3, 4, 5, 6\} = U$ → $(A \cup B)^c = \emptyset$
4. $A \cap B = \emptyset$ → $(A \cap B)^c = U = \{1, 2, 3, 4, 5, 6\}$
5. $A^c = \{2, 4, 6\}$, $B^c = \{1, 3, 5\}$ → $A^c \cap B^c = \emptyset$
6. Parts 3 and 5 are both $\emptyset$. This illustrates **De Morgan's Law**: $(A \cup B)^c = A^c \cap B^c$.

## Solution 6

1. $A \cup B = [0, 3) \cup (7, 10]$
2. $A \cap C = [2, 3)$
3. $A^c = [3, 10]$
4. $B^c = [0, 7]$
5. $A \cap B = \emptyset$
6. No. $C = [2, 5]$, but elements in $[3, 5]$ are not in $A = [0, 3)$.

## Solution 7

1. **True.** If $x \in A \cap B$, then $x \in A$ by definition of intersection.
2. **True.** If $x \in A$, then $x \in A \cup B$ by definition of union.
3. **True.** If $x \in A$, then $x \notin A^c$ by definition. So no element of $A$ can be in $A^c$.
4. **True.** This is the **transitivity** of subset. If every element of $A$ is in $B$, and every element of $B$ is in $C$, then every element of $A$ is in $C$.
5. **True.** If $A \cap B = \emptyset$, no element of $A$ is in $B$, so every element of $A$ is in $B^c$, meaning $A \subseteq B^c$.
6. **True.** If $x \in A \cap B$, then $x \in A$, so $x \in A \cup B$.

## Solution 8

1. **Prediction:** Both should be equal (associativity of intersection). **Verification:** $A \cap B = \{3\}$, so $(A \cap B) \cap C = \{3\}$. $B \cap C = \{3, 4\}$, so $A \cap (B \cap C) = \{3\}$. ✅ Equal.
2. **Prediction:** Both should be equal (distributive law). **Verification:** $A \cup B = \{1, 2, 3, 4, 5\}$, so $(A \cup B) \cap C = \{2, 3, 4\}$. $A \cap C = \{2, 3\}$, $B \cap C = \{3, 4\}$, so $(A \cap C) \cup (B \cap C) = \{2, 3, 4\}$. ✅ Equal.
3. **Prediction:** Both should be equal (De Morgan's law). **Verification:** $A \cap B = \{3\}$, so $(A \cap B)^c = \{1, 2, 4, 5, 6\}$. $A^c = \{4, 5, 6\}$, $B^c = \{1, 2, 6\}$, so $A^c \cup B^c = \{1, 2, 4, 5, 6\}$. ✅ Equal.
