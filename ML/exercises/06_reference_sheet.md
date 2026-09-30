# Set Algebra — Reference Sheet of Valid Statements

> A comprehensive list of identities and laws used to simplify set expressions.
> All sets $A, B, C, D$ are subsets of a universal set $U$.
> The notation $A^c$ denotes the complement of $A$ relative to $U$.
> The notation $A \setminus B$ denotes set difference, defined as $A \cap B^c$.

---

## 1. Identity Laws

$$A \cup \emptyset = A$$

$$A \cap U = A$$

---

## 2. Domination (Annihilation) Laws

$$A \cup U = U$$

$$A \cap \emptyset = \emptyset$$

---

## 3. Idempotent Laws

$$A \cup A = A$$

$$A \cap A = A$$

---

## 4. Complement Laws

$$A \cup A^c = U$$

$$A \cap A^c = \emptyset$$

---

## 5. Double Complement (Involution) Law

$$(A^c)^c = A$$

---

## 6. Complement of the Universal Set and Empty Set

$$U^c = \emptyset$$

$$\emptyset^c = U$$

---

## 7. Commutative Laws

$$A \cup B = B \cup A$$

$$A \cap B = B \cap A$$

---

## 8. Associative Laws

$$(A \cup B) \cup C = A \cup (B \cup C)$$

$$(A \cap B) \cap C = A \cap (B \cap C)$$

> Because of associativity, we can drop parentheses and write $A \cup B \cup C$ and $A \cap B \cap C$ without ambiguity.

---

## 9. Distributive Laws

$$A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$$

$$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$

> Intersection distributes over union, **and** union distributes over intersection.

---

## 10. De Morgan's Laws

$$(A \cup B)^c = A^c \cap B^c$$

$$(A \cap B)^c = A^c \cup B^c$$

**Generalized to $n$ sets:**

$$(A_1 \cup A_2 \cup \cdots \cup A_n)^c = A_1^c \cap A_2^c \cap \cdots \cap A_n^c$$

$$(A_1 \cap A_2 \cap \cdots \cap A_n)^c = A_1^c \cup A_2^c \cup \cdots \cup A_n^c$$

---

## 11. Absorption Laws

$$A \cup (A \cap B) = A$$

$$A \cap (A \cup B) = A$$

> **Proof of the first:** $A \cup (A \cap B) = (A \cup A) \cap (A \cup B) = A \cap (A \cup B) = A$ (distributive → idempotent → absorption).

---

## 12. Partition (Extraction) Laws

$$(A \cap B) \cup (A \cap B^c) = A$$

$$(A \cup B) \cap (A \cup B^c) = A$$

> These express the idea that $B$ and $B^c$ partition $U$, so intersecting $A$ with both parts and combining gives back $A$.

---

## 13. Simplification Laws

These are derived identities that frequently appear in simplification problems.

### 13a. Adding a redundant term

$$A \cup (A^c \cap B) = A \cup B$$

$$A \cap (A^c \cup B) = A \cap B$$

> **Proof of the first:** $A \cup (A^c \cap B) = (A \cup A^c) \cap (A \cup B) = U \cap (A \cup B) = A \cup B$ (distributive → complement → identity).

### 13b. Common factor extraction

$$(A \cap B) \cup (A^c \cap B) = B$$

$$(A \cup B) \cap (A^c \cup B) = B$$

> **Proof of the first:** $(A \cap B) \cup (A^c \cap B) = (A \cup A^c) \cap B = U \cap B = B$ (distributive → complement → identity).

### 13c. Complement interaction

$$(A \cap B)^c \cap A = A \cap B^c$$

$$(A \cup B)^c \cup A = A \cup B^c$$

> **Proof of the first:** $(A \cap B)^c \cap A = (A^c \cup B^c) \cap A = (A^c \cap A) \cup (B^c \cap A) = \emptyset \cup (A \cap B^c) = A \cap B^c$ (De Morgan → distributive → complement → identity).

---

## 14. Consensus Theorem

$$(A \cap B) \cup (A^c \cap C) \cup (B \cap C) = (A \cap B) \cup (A^c \cap C)$$

**Dual form:**

$$(A \cup B) \cap (A^c \cup C) \cap (B \cup C) = (A \cup B) \cap (A^c \cup C)$$

> The term $B \cap C$ is called the **consensus** term and is redundant (absorbed by the other two). This is extremely useful for simplifying expressions with three terms.

---

## 15. Set Difference Identities

$$A \setminus B = A \cap B^c$$

$$A \setminus (B \cup C) = (A \setminus B) \cap (A \setminus C)$$

$$A \setminus (B \cap C) = (A \setminus B) \cup (A \setminus C)$$

$$(A \cap B) \setminus C = A \cap (B \setminus C)$$

$$(A \setminus B) \setminus C = A \setminus (B \cup C)$$

$$A \setminus (A \setminus B) = A \cap B$$

> **Note:** $(A \setminus B) \setminus C \neq A \setminus (B \setminus C)$ in general.

---

## 16. Subset-Related Identities

If $A \subseteq B$, then:

| Identity | Name / Explanation |
|---|---|
| $A \cap B = A$ | Intersection with a superset |
| $A \cup B = B$ | Union with a subset |
| $B^c \subseteq A^c$ | Complement reverses inclusion |
| $A \setminus B = \emptyset$ | Nothing in $A$ is outside $B$ |
| $A \cap C \subseteq B \cap C$ | Intersection preserves inclusion |
| $A \cup C \subseteq B \cup C$ | Union preserves inclusion |
| $C \setminus B \subseteq C \setminus A$ | Difference reverses inclusion |

---

## 17. Equivalent Characterizations

The following are equivalent:

| Statement | Meaning |
|---|---|
| $A \subseteq B$ | Every element of $A$ is in $B$ |
| $A \cap B = A$ | $A$ "absorbs" into $B$ via intersection |
| $A \cup B = B$ | $A$ "absorbs" into $B$ via union |
| $A \setminus B = \emptyset$ | $A$ has nothing outside $B$ |
| $A \cap B^c = \emptyset$ | $A$ and $B^c$ are disjoint |
| $B^c \subseteq A^c$ | Complement reverses inclusion |

Similarly:

| Statement | Meaning |
|---|---|
| $A \cap B = \emptyset$ | $A$ and $B$ are disjoint |
| $A \subseteq B^c$ | $A$ is contained in the complement of $B$ |
| $B \subseteq A^c$ | $B$ is contained in the complement of $A$ |

And:

| Statement | Meaning |
|---|---|
| $A \cup B = U$ | $A$ and $B$ cover the universal set |
| $A^c \subseteq B$ | Everything outside $A$ is in $B$ |
| $B^c \subseteq A$ | Everything outside $B$ is in $A$ |

---

## 18. Duality Principle

Every set algebra identity has a **dual** obtained by swapping:
- $\cup \leftrightarrow \cap$
- $\emptyset \leftrightarrow U$

| Identity | Dual |
|---|---|
| $A \cup \emptyset = A$ | $A \cap U = A$ |
| $A \cup U = U$ | $A \cap \emptyset = \emptyset$ |
| $A \cup A = A$ | $A \cap A = A$ |
| $A \cup A^c = U$ | $A \cap A^c = \emptyset$ |
| $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ | $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ |
| $(A \cup B)^c = A^c \cap B^c$ | $(A \cap B)^c = A^c \cup B^c$ |
| $A \cup (A \cap B) = A$ | $A \cap (A \cup B) = A$ |
| $(A \cap B) \cup (A \cap B^c) = A$ | $(A \cup B) \cap (A \cup B^c) = A$ |
| $A \cup (A^c \cap B) = A \cup B$ | $A \cap (A^c \cup B) = A \cap B$ |

> If an identity is true, its dual is also true. This **doubles** the number of identities you know for free!

---

## 19. Symmetric Difference Identities

The symmetric difference is defined as $A \triangle B = (A \cap B^c) \cup (A^c \cap B) = (A \cup B) \cap (A \cap B)^c$.

| Identity | Name |
|---|---|
| $A \triangle \emptyset = A$ | Identity |
| $A \triangle U = A^c$ | Universal |
| $A \triangle A = \emptyset$ | Idempotent (nilpotent) |
| $A \triangle A^c = U$ | Complement |
| $A \triangle B = B \triangle A$ | Commutative |
| $(A \triangle B) \triangle C = A \triangle (B \triangle C)$ | Associative |
| $A \cap (B \triangle C) = (A \cap B) \triangle (A \cap C)$ | Distributive |
| $(A \triangle B)^c = (A \cap B) \cup (A^c \cap B^c)$ | Complement |

---

## Quick Simplification Strategy

When simplifying a set expression, try these steps in order:

1. **Apply De Morgan's Laws** to push complements inward (toward individual sets).
2. **Apply the double complement law** $(A^c)^c = A$ to remove nested complements.
3. **Apply the distributive law** to expand or factor expressions.
4. **Apply complement laws** ($A \cap A^c = \emptyset$, $A \cup A^c = U$) to create $\emptyset$ or $U$ terms.
5. **Apply identity/domination laws** to eliminate $\emptyset$ and $U$ ($A \cup \emptyset = A$, $A \cap U = A$, $A \cup U = U$, $A \cap \emptyset = \emptyset$).
6. **Apply idempotent laws** ($A \cup A = A$, $A \cap A = A$) to remove duplicates.
7. **Apply absorption laws** ($A \cup (A \cap B) = A$, $A \cap (A \cup B) = A$) to remove redundant terms.
8. **Look for consensus patterns** $(A \cap B) \cup (A^c \cap C) \cup (B \cap C)$ and drop the consensus term.
9. **Use subset information** if known (e.g., $A \subseteq B$ implies $A \cup B = B$ and $A \cap B = A$).
10. **Check your result** with a small concrete example.
