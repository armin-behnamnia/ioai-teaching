# Set Algebra — Subsets and Complements

## Learning Objectives

- Deepen understanding of the **subset** relation and its interaction with union, intersection, and complement.
- Practice **proving** subset relationships.
- Reason about **chains of inclusions** and **equivalent characterizations** of subset.

---

## Problem 1 — Basic Subset Checks

Let $U = \{1, 2, 3, 4, 5, 6, 7, 8, 9, 10\}$, $A = \{1, 2, 3, 4\}$, $B = \{2, 4, 6, 8\}$, $C = \{1, 2, 3, 4, 5, 6\}$.

Determine whether each is **true** or **false**:

1. $A \subseteq C$
2. $B \subseteq A$
3. $A \cap B \subseteq A$
4. $A \subseteq A \cup B$
5. $A^c \subseteq B^c$
6. $A \cap B \subseteq A \cup B$
7. $C^c \subseteq A^c$
8. $A \cap C \subseteq B$

---

## Problem 2 — Subset and Set Operations

Let $A, B, C$ be arbitrary subsets of a universal set $U$. **Prove or disprove** each statement.

1. If $A \subseteq B$, then $A \cap C \subseteq B \cap C$.
2. If $A \subseteq B$, then $A \cup C \subseteq B \cup C$.
3. If $A \subseteq B$, then $B^c \subseteq A^c$.
4. If $A \subseteq B$ and $A \subseteq C$, then $A \subseteq B \cap C$.
5. If $A \subseteq B \cap C$, then $A \subseteq B$ and $A \subseteq C$.
6. If $A \subseteq C$ and $B \subseteq C$, then $A \cup B \subseteq C$.
7. If $A \cap B \subseteq C$, then $A \subseteq C$.
8. If $A \subseteq B \cup C$, then $A \subseteq B$ or $A \subseteq C$.

---

## Problem 3 — Complement and Subset

Let $A, B \subseteq U$. **Prove or disprove:**

1. $A \subseteq B$ if and only if $B^c \subseteq A^c$.
2. $A \subseteq B^c$ if and only if $A \cap B = \emptyset$.
3. $A^c \subseteq B$ if and only if $A \cup B = U$.
4. $A \cap B = \emptyset$ if and only if $A \subseteq B^c$.
5. $(A \subseteq B) \iff (A \setminus B = \emptyset)$, where $A \setminus B = A \cap B^c$.

---

## Problem 4 — Finding All Subsets

1. List **all subsets** of $S = \{a, b, c\}$. How many are there?
2. List **all subsets** of $T = \{1, 2, 3, 4\}$. How many are there?
3. If a set has $n$ elements, how many subsets does it have? Explain **why**.

---

## Problem 5 — Subset Chains

Let $A, B, C, D$ be sets such that $A \subseteq B \subseteq C \subseteq D$.

1. Prove that $A \subseteq D$.
2. Prove that $A \cap D = A$.
3. Prove that $A \cup D = D$.
4. What is $A \cap B \cap C \cap D$?
5. What is $A \cup B \cup C \cup D$?

---

## Problem 6 — Working with Complements

Let $U = \{1, 2, 3, \ldots, 12\}$. Define:

- $A = \{n \in U \mid 2 \mid n\}$ (multiples of 2)
- $B = \{n \in U \mid 3 \mid n\}$ (multiples of 3)
- $C = \{n \in U \mid 4 \mid n\}$ (multiples of 4)

Find:

1. $A^c$ (describe in words and list elements)
2. $B^c$ (describe in words and list elements)
3. $(A \cap B)^c$ (describe in words and list elements)
4. $A^c \cap B^c$ (describe in words and list elements)
5. What do you notice about parts 3 and 4? Why?
6. Is $C \subseteq A$? Prove your answer.
7. Is $A \subseteq C$? Prove your answer.

---

## Problem 7 — Venn Diagram Reasoning

Three sets $A, B, C$ divide the universal set $U$ into **8 regions**. Label the regions of a Venn diagram and describe each region using set operations (union, intersection, complement). For example:

- Region in $A$ only (not $B$, not $C$): $A \cap B^c \cap C^c$
- Region in $A$ and $B$ but not $C$: $A \cap B \cap C^c$

Write expressions for **all 8 regions**.

---

## Problem 8 — Complement interacts with Union and Intersection

Let $A, B, C \subseteq U$. Assume $A \subseteq B$. Prove each of the following:

1. $A \cap C \subseteq B \cap C$
2. $A \cup C \subseteq B \cup C$
3. $B^c \subseteq A^c$
4. $C \setminus B \subseteq C \setminus A$ *(where $X \setminus Y = X \cap Y^c$)*
5. $A \cup (B \cap C) = B \cap (A \cup C)$

> **Hint for 5:** Use the fact that $A \subseteq B$ means $A \cup B = B$ and $A \cap B = A$.

---

---

# Solutions

## Solution 1

1. **True.** Every element of $A = \{1,2,3,4\}$ is in $C = \{1,2,3,4,5,6\}$.
2. **False.** $6 \in B$ but $6 \notin A$.
3. **True.** Always true: $A \cap B \subseteq A$ for any sets.
4. **True.** Always true: $A \subseteq A \cup B$ for any sets.
5. **False.** $A^c = \{5,6,7,8,9,10\}$, $B^c = \{1,3,5,7,9\}$. Is $A^c \subseteq B^c$? $6 \in A^c$ but $6 \notin B^c$. False.
6. **True.** Always true: $A \cap B \subseteq A \subseteq A \cup B$.
7. **True.** $C^c = \{7,8,9,10\}$, $A^c = \{5,6,7,8,9,10\}$. Every element of $C^c$ is in $A^c$.
8. **False.** $A \cap C = A = \{1,2,3,4\}$. Is $A \subseteq B = \{2,4,6,8\}$? $1 \in A$ but $1 \notin B$. False.

## Solution 2

1. **True.** Let $x \in A \cap C$. Then $x \in A$ and $x \in C$. Since $A \subseteq B$, $x \in B$. So $x \in B \cap C$.

2. **True.** Let $x \in A \cup C$. Then $x \in A$ or $x \in C$. If $x \in A$, then $x \in B$ (since $A \subseteq B$), so $x \in B \cup C$. If $x \in C$, then $x \in B \cup C$. Either way, $x \in B \cup C$.

3. **True.** Let $x \in B^c$. Then $x \notin B$. Since $A \subseteq B$, $x \notin A$ (contrapositive: if $x \in A$ then $x \in B$). So $x \in A^c$.

4. **True.** Let $x \in A$. Then $x \in B$ (since $A \subseteq B$) and $x \in C$ (since $A \subseteq C$). So $x \in B \cap C$.

5. **True.** Let $x \in A$. Since $A \subseteq B \cap C$, $x \in B \cap C$, so $x \in B$ and $x \in C$.

6. **True.** Let $x \in A \cup B$. Then $x \in A$ or $x \in B$. If $x \in A \subseteq C$, done. If $x \in B \subseteq C$, done. Either way $x \in C$.

7. **False.** Counterexample: $A = \{1, 2\}, B = \{3, 4\}, C = \{2\}$. Then $A \cap B = \emptyset \subseteq C$. But $A = \{1, 2\} \not\subseteq \{2\} = C$ since $1 \in A, 1 \notin C$.

8. **False.** Counterexample: $A = \{1, 3\}, B = \{1, 2\}, C = \{3, 4\}$. Then $A \subseteq B \cup C = \{1, 2, 3, 4\}$. But $A \not\subseteq B$ (since $3 \notin B$) and $A \not\subseteq C$ (since $1 \notin C$).

## Solution 3

1. **True.**
   - ($\Rightarrow$) See Solution 2.3 above.
   - ($\Leftarrow$) Suppose $B^c \subseteq A^c$. Then by the same argument with $A^c$ and $B^c$ swapped (and noting $(A^c)^c = A$): if $B^c \subseteq A^c$, then $(A^c)^c \subseteq (B^c)^c$, i.e., $A \subseteq B$.

2. **True.**
   - ($\Rightarrow$) Suppose $A \subseteq B^c$. Let $x \in A \cap B$. Then $x \in A \subseteq B^c$, so $x \in B^c$, meaning $x \notin B$. But $x \in B$ — contradiction. So $A \cap B = \emptyset$.
   - ($\Leftarrow$) Suppose $A \cap B = \emptyset$. Let $x \in A$. Then $x \notin B$ (otherwise $x \in A \cap B$). So $x \in B^c$. Thus $A \subseteq B^c$.

3. **True.**
   - ($\Rightarrow$) Suppose $A^c \subseteq B$. Then $U = A^c \cup A \subseteq B \cup A = A \cup B$. Since $A \cup B \subseteq U$, we get $A \cup B = U$.
   - ($\Leftarrow$) Suppose $A \cup B = U$. Let $x \in A^c$. Then $x \notin A$. Since $A \cup B = U$, $x \in A \cup B$, so $x \in B$. Thus $A^c \subseteq B$.

4. **True.** This is the same as Problem 3.2 (just stated with "if and only if"). See above.

5. **True.**
   - ($\Rightarrow$) Suppose $A \subseteq B$. Then $A \setminus B = A \cap B^c$. If $x \in A \cap B^c$, then $x \in A \subseteq B$ and $x \in B^c$, so $x \in B$ and $x \notin B$ — contradiction. So $A \setminus B = \emptyset$.
   - ($\Leftarrow$) Suppose $A \setminus B = \emptyset$, i.e., $A \cap B^c = \emptyset$. Let $x \in A$. If $x \notin B$, then $x \in B^c$, so $x \in A \cap B^c = \emptyset$ — contradiction. So $x \in B$, meaning $A \subseteq B$.

## Solution 4

1. Subsets of $\{a, b, c\}$: $\emptyset, \{a\}, \{b\}, \{c\}, \{a,b\}, \{a,c\}, \{b,c\}, \{a,b,c\}$. **8 subsets** ($2^3 = 8$).

2. Subsets of $\{1,2,3,4\}$: $\emptyset, \{1\}, \{2\}, \{3\}, \{4\}, \{1,2\}, \{1,3\}, \{1,4\}, \{2,3\}, \{2,4\}, \{3,4\}, \{1,2,3\}, \{1,2,4\}, \{1,3,4\}, \{2,3,4\}, \{1,2,3,4\}$. **16 subsets** ($2^4 = 16$).

3. A set with $n$ elements has $2^n$ subsets. **Why:** For each element, it is either **in** or **out** of a given subset — 2 choices per element, $n$ elements, so $2 \times 2 \times \cdots \times 2 = 2^n$ total subsets.

## Solution 5

1. By transitivity of $\subseteq$: $A \subseteq B$ and $B \subseteq C$ and $C \subseteq D$ implies $A \subseteq D$.

2. Since $A \subseteq D$, we have $A \cap D = A$ (intersection with a superset returns the smaller set).

3. Since $A \subseteq D$, we have $A \cup D = D$ (union with a subset returns the larger set).

4. $A \cap B \cap C \cap D = A$. Since $A \subseteq B \subseteq C \subseteq D$, every element of $A$ is in all four sets, so the intersection is $A$. And any element not in $A$ is not in the intersection.

5. $A \cup B \cup C \cup D = D$. Since $A \subseteq B \subseteq C \subseteq D$, every set is a subset of $D$, so the union is $D$.

## Solution 6

$A = \{2, 4, 6, 8, 10, 12\}$, $B = \{3, 6, 9, 12\}$, $C = \{4, 8, 12\}$.

1. $A^c = \{1, 3, 5, 7, 9, 11\}$ — the numbers in $U$ **not** divisible by 2 (i.e., the odd numbers).

2. $B^c = \{1, 2, 4, 5, 7, 8, 10, 11\}$ — the numbers in $U$ **not** divisible by 3.

3. $A \cap B = \{6, 12\}$ (multiples of 6). $(A \cap B)^c = \{1, 2, 3, 4, 5, 7, 8, 9, 10, 11\}$ — numbers **not** divisible by 6.

4. $A^c \cap B^c = \{1, 3, 5, 7, 9, 11\} \cap \{1, 2, 4, 5, 7, 8, 10, 11\} = \{1, 5, 7, 11\}$ — numbers divisible by **neither** 2 nor 3.

5. Parts 3 and 4 are **equal**: $(A \cap B)^c = A^c \cap B^c$ — this is **De Morgan's Law**. The set of elements not divisible by both 2 and 3 equals the set of elements divisible by neither 2 nor 3.

6. **Yes, $C \subseteq A$.** $C = \{4, 8, 12\}$. Every element of $C$ is divisible by 4, hence divisible by 2, so every element of $C$ is in $A$. Formally: if $4 \mid n$, then $2 \mid n$, so $n \in A$.

7. **No, $A \not\subseteq C$.** $2 \in A$ (divisible by 2) but $2 \notin C$ (not divisible by 4).

## Solution 7

The 8 regions of a three-set Venn diagram:

| Region | Description | Expression |
|--------|-------------|------------|
| 1 | In $A$ only | $A \cap B^c \cap C^c$ |
| 2 | In $B$ only | $A^c \cap B \cap C^c$ |
| 3 | In $C$ only | $A^c \cap B^c \cap C$ |
| 4 | In $A$ and $B$, not $C$ | $A \cap B \cap C^c$ |
| 5 | In $A$ and $C$, not $B$ | $A \cap B^c \cap C$ |
| 6 | In $B$ and $C$, not $A$ | $A^c \cap B \cap C$ |
| 7 | In all three | $A \cap B \cap C$ |
| 8 | In none | $A^c \cap B^c \cap C^c$ |

## Solution 8

Given $A \subseteq B$:

1. **$A \cap C \subseteq B \cap C$.** Let $x \in A \cap C$. Then $x \in A \subseteq B$ and $x \in C$. So $x \in B \cap C$.

2. **$A \cup C \subseteq B \cup C$.** Let $x \in A \cup C$. If $x \in A \subseteq B$, then $x \in B \cup C$. If $x \in C$, then $x \in B \cup C$.

3. **$B^c \subseteq A^c$.** Let $x \in B^c$, so $x \notin B$. Since $A \subseteq B$, if $x \in A$ then $x \in B$ — contradiction. So $x \notin A$, meaning $x \in A^c$.

4. **$C \setminus B \subseteq C \setminus A$.** Let $x \in C \setminus B = C \cap B^c$. Then $x \in C$ and $x \notin B$. Since $A \subseteq B$, $x \notin B \Rightarrow x \notin A$ (contrapositive of $A \subseteq B$). So $x \in C$ and $x \notin A$, i.e., $x \in C \cap A^c = C \setminus A$.

5. **$A \cup (B \cap C) = B \cap (A \cup C)$.**

   Since $A \subseteq B$, we know $A \cup B = B$.

   **Right side:** $B \cap (A \cup C) = (B \cap A) \cup (B \cap C)$ — *distributive law*
   
   Since $A \subseteq B$, $B \cap A = A$. So:
   
   $= A \cup (B \cap C)$ — *using $A \cap B = A$ when $A \subseteq B$*
   
   This equals the left side. ✅
