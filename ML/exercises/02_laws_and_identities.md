# Set Algebra — Laws and Identities

## Learning Objectives

- Internalize the **fundamental laws** of set algebra: commutative, associative, distributive, identity, complement, idempotent, and De Morgan's laws.
- Learn to **simplify** set expressions using these laws.
- Understand **why** these laws hold, not just that they hold.

---

## Problem 1 — Commutative & Associative Laws

Simplify each expression using the commutative and associative laws.

1. $(A \cup B) \cup (C \cup A)$
2. $(A \cap B) \cap (B \cap C)$
3. $A \cup (B \cup (A \cup C))$
4. $A \cap (B \cap (A \cap C))$

---

## Problem 2 — Distributive Laws

Use the distributive law to expand each expression.

1. $A \cap (B \cup C)$
2. $A \cup (B \cap C)$
3. $(A \cap B) \cup (C \cap D)$
4. $A^c \cap (B \cup C^c)$

Then, use the distributive law in reverse to **factor** each expression:

5. $(A \cap B) \cup (A \cap C)$
6. $(A \cup C) \cap (B \cup C)$
7. $(A \cap B^c) \cup (A \cap C^c)$

---

## Problem 3 — Identity and Universal Laws

Simplify each expression. Assume all sets are subsets of a universal set $U$.

1. $A \cup \emptyset$
2. $A \cap U$
3. $A \cap \emptyset$
4. $A \cup U$
5. $A \cup A^c$
6. $A \cap A^c$
7. $\emptyset^c$
8. $U^c$
9. $(A^c)^c$

---

## Problem 4 — Idempotent Laws

Simplify each expression.

1. $A \cup A$
2. $A \cap A$
3. $(A \cup A) \cap (A \cup A)$
4. $A \cup (A \cap B)$
5. $A \cap (A \cup B)$

> **Hint for 4 and 5:** These are the **absorption laws**. Try to prove them using the distributive law and idempotent law.

---

## Problem 5 — De Morgan's Laws

Simplify each expression using De Morgan's laws.

1. $(A \cup B)^c$
2. $(A \cap B)^c$
3. $(A \cup B \cup C)^c$
4. $(A \cap B \cap C)^c$
5. $(A^c \cup B^c)^c$
6. $(A^c \cap B^c)^c$

---

## Problem 6 — Multi-step Simplification

Simplify each expression as far as possible. Show each step and name the law used.

1. $(A \cup B) \cap (A \cup B^c)$
2. $(A \cap B) \cup (A \cap B^c)$
3. $(A \cup B) \cap (A^c \cup B)$
4. $(A \cup B^c) \cap (A^c \cup B) \cap (A \cup B) \cap (A^c \cup B^c)$
5. $A \cap (A^c \cup B)$
6. $(A \cup B) \cup (A \cap B^c)$
7. $(A \cap B) \cup (A^c \cap B) \cup (A \cap B^c)$
8. $((A \cup B) \cap (A \cup C)) \cap (A \cup B \cup C)$

---

## Problem 7 — Proving Identities

**Prove** each identity using the set algebra laws. Justify each step by naming the law used.

1. $(A \cap B) \cup (A \cap B^c) = A$
2. $(A \cup B) \cap (A^c \cup B) = B$
3. $(A \cap B) \cup (A^c \cap B) = B$
4. $A \cup (A^c \cap B) = A \cup B$
5. $A \cap (A^c \cup B) = A \cap B$
6. $(A \cup B) \cap (A \cup B^c) = A$
7. $(A \cap B^c) \cup (B \cap A^c) = (A \cup B) \cap (A \cap B)^c$

---

## Problem 8 — True or False?

For each statement, determine if it is **always true**. If true, prove it. If not, provide a counterexample.

1. $(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$
2. $(A \cap B) \cup C = (A \cup C) \cap (B \cup C)$
3. $A \setminus B = A \cap B^c$  *(where $A \setminus B$ means elements in $A$ but not in $B$)*
4. $(A \cup B)^c = A^c \cap B^c$
5. $(A \cap B) \cup (B \cap C) \cup (A \cap C) = A \cap B \cap C$
6. If $A \subseteq B$, then $A \cap B = A$ and $A \cup B = B$.
7. If $A \subseteq B$, then $B^c \subseteq A^c$.
8. $A \cap (B \cup C) = (A \cap B) \cup C$

---

---

# Solutions

## Solution 1

1. $(A \cup B) \cup (C \cup A) = A \cup B \cup C$ (commutative + associative)
2. $(A \cap B) \cap (B \cap C) = A \cap B \cap C$ (commutative + associative; the extra $B$ is absorbed by idempotence)
3. $A \cup (B \cup (A \cup C)) = A \cup B \cup C$ (associative + commutative + idempotent)
4. $A \cap (B \cap (A \cap C)) = A \cap B \cap C$ (associative + commutative + idempotent)

## Solution 2

1. $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$
2. $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
3. $(A \cap B) \cup (C \cap D)$ — already expanded; cannot simplify further without more information.
4. $A^c \cap (B \cup C^c) = (A^c \cap B) \cup (A^c \cap C^c)$
5. $(A \cap B) \cup (A \cap C) = A \cap (B \cup C)$
6. $(A \cup C) \cap (B \cup C) = (A \cap B) \cup C$
7. $(A \cap B^c) \cup (A \cap C^c) = A \cap (B^c \cup C^c) = A \cap (B \cap C)^c$

## Solution 3

1. $A \cup \emptyset = A$ (identity law)
2. $A \cap U = A$ (identity law)
3. $A \cap \emptyset = \emptyset$ (domination law)
4. $A \cup U = U$ (domination law)
5. $A \cup A^c = U$ (complement law)
6. $A \cap A^c = \emptyset$ (complement law)
7. $\emptyset^c = U$
8. $U^c = \emptyset$
9. $(A^c)^c = A$ (double complement / involution law)

## Solution 4

1. $A \cup A = A$ (idempotent law)
2. $A \cap A = A$ (idempotent law)
3. $A \cap A = A$ (idempotent, applied twice)
4. $A \cup (A \cap B) = A$ — **absorption law**. Proof: $A \cup (A \cap B) = (A \cup A) \cap (A \cup B) = A \cap (A \cup B) = A$ (distributive → idempotent → absorption).
5. $A \cap (A \cup B) = A$ — **absorption law**. Proof: $A \cap (A \cup B) = (A \cap A) \cup (A \cap B) = A \cup (A \cap B) = A$ (distributive → idempotent → absorption).

## Solution 5

1. $(A \cup B)^c = A^c \cap B^c$
2. $(A \cap B)^c = A^c \cup B^c$
3. $(A \cup B \cup C)^c = A^c \cap B^c \cap C^c$
4. $(A \cap B \cap C)^c = A^c \cup B^c \cup C^c$
5. $(A^c \cup B^c)^c = (A^c)^c \cap (B^c)^c = A \cap B$ (De Morgan + double complement)
6. $(A^c \cap B^c)^c = (A^c)^c \cup (B^c)^c = A \cup B$ (De Morgan + double complement)

## Solution 6

1. $(A \cup B) \cap (A \cup B^c) = A \cup (B \cap B^c) = A \cup \emptyset = A$
   *(distributive → complement → identity)*

2. $(A \cap B) \cup (A \cap B^c) = A \cap (B \cup B^c) = A \cap U = A$
   *(distributive → complement → identity)*

3. $(A \cup B) \cap (A^c \cup B) = (A \cap A^c) \cup B = \emptyset \cup B = B$
   *(distributive [factor out $B$] → complement → identity)*
   
   Detailed: $(A \cup B) \cap (A^c \cup B) = (A \cap A^c) \cup (A \cap B) \cup (B \cap A^c) \cup (B \cap B) = \emptyset \cup (A \cap B) \cup (A^c \cap B) \cup B = B$ (since $A \cap B \subseteq B$ and $A^c \cap B \subseteq B$, their union with $B$ is $B$).

4. $(A \cup B^c) \cap (A^c \cup B) \cap (A \cup B) \cap (A^c \cup B^c)$

   Group: $[(A \cup B^c) \cap (A \cup B)] \cap [(A^c \cup B) \cap (A^c \cup B^c)]$

   First group: $(A \cup B^c) \cap (A \cup B) = A \cup (B^c \cap B) = A \cup \emptyset = A$

   Second group: $(A^c \cup B) \cap (A^c \cup B^c) = A^c \cup (B \cap B^c) = A^c \cup \emptyset = A^c$

   Result: $A \cap A^c = \emptyset$

5. $A \cap (A^c \cup B) = (A \cap A^c) \cup (A \cap B) = \emptyset \cup (A \cap B) = A \cap B$
   *(distributive → complement → identity)*

6. $(A \cup B) \cup (A \cap B^c) = A \cup B \cup (A \cap B^c) = A \cup B$
   *(Since $A \cap B^c \subseteq A \subseteq A \cup B$, absorbing it changes nothing.)*

7. $(A \cap B) \cup (A^c \cap B) \cup (A \cap B^c)$

   First two: $(A \cap B) \cup (A^c \cap B) = (A \cup A^c) \cap B = U \cap B = B$

   Then: $B \cup (A \cap B^c) = (B \cup A) \cap (B \cup B^c) = (A \cup B) \cap U = A \cup B$
   *(distributive → complement → identity)*

8. $((A \cup B) \cap (A \cup C)) \cap (A \cup B \cup C)$

   First: $(A \cup B) \cap (A \cup C) = A \cup (B \cap C)$ *(distributive law)*

   Then: $(A \cup (B \cap C)) \cap (A \cup B \cup C)$
   
   $= A \cup ((B \cap C) \cap (B \cup C))$ *(distributive)*
   
   $= A \cup (B \cap C)$ *(since $B \cap C \subseteq B \cup C$, so $(B \cap C) \cap (B \cup C) = B \cap C$)*

   Result: $A \cup (B \cap C)$

## Solution 7

1. $(A \cap B) \cup (A \cap B^c)$
   $= A \cap (B \cup B^c)$ — *distributive law*
   $= A \cap U$ — *complement law*
   $= A$ — *identity law* ✅

2. $(A \cup B) \cap (A^c \cup B)$
   $= B \cup (A \cap A^c)$ — *distributive law (factoring out $B$)*
   $= B \cup \emptyset$ — *complement law*
   $= B$ — *identity law* ✅

3. $(A \cap B) \cup (A^c \cap B)$
   $= B \cap (A \cup A^c)$ — *distributive law (factoring out $B$)*
   $= B \cap U$ — *complement law*
   $= B$ — *identity law* ✅

4. $A \cup (A^c \cap B)$
   $= (A \cup A^c) \cap (A \cup B)$ — *distributive law*
   $= U \cap (A \cup B)$ — *complement law*
   $= A \cup B$ — *identity law* ✅

5. $A \cap (A^c \cup B)$
   $= (A \cap A^c) \cup (A \cap B)$ — *distributive law*
   $= \emptyset \cup (A \cap B)$ — *complement law*
   $= A \cap B$ — *identity law* ✅

6. $(A \cup B) \cap (A \cup B^c)$
   $= A \cup (B \cap B^c)$ — *distributive law*
   $= A \cup \emptyset$ — *complement law*
   $= A$ — *identity law* ✅

7. $(A \cap B^c) \cup (B \cap A^c)$

   Expand the right side: $(A \cup B) \cap (A \cap B)^c$
   $= (A \cup B) \cap (A^c \cup B^c)$ — *De Morgan's law*
   $= (A \cap (A^c \cup B^c)) \cup (B \cap (A^c \cup B^c))$ — *distributive law*
   $= (A \cap A^c) \cup (A \cap B^c) \cup (B \cap A^c) \cup (B \cap B^c)$ — *distributive law*
   $= \emptyset \cup (A \cap B^c) \cup (B \cap A^c) \cup \emptyset$ — *complement law*
   $= (A \cap B^c) \cup (B \cap A^c)$ — *identity law* ✅

## Solution 8

1. **True.** This is the distributive law: intersection distributes over union.
2. **True.** This is the distributive law: union distributes over intersection.
3. **True.** $A \setminus B = \{x \mid x \in A \text{ and } x \notin B\} = \{x \mid x \in A \text{ and } x \in B^c\} = A \cap B^c$.
4. **True.** This is De Morgan's law.
5. **False.** Counterexample: $A = \{1\}, B = \{1, 2\}, C = \{2\}$. Left side: $\{1\} \cup \{2\} \cup \emptyset = \{1, 2\}$. Right side: $\{1\} \cap \{1, 2\} \cap \{2\} = \emptyset$. Not equal.
6. **True.** If $A \subseteq B$: Every element of $A$ is in $B$, so $A \cap B = A$. Every element of $A \cup B$ is in $B$ (since $A \subseteq B$), and $B \subseteq A \cup B$, so $A \cup B = B$.
7. **True.** If $A \subseteq B$, then every element not in $B$ is certainly not in $A$ (contrapositive). So $B^c \subseteq A^c$.
8. **False.** Counterexample: $A = \{1\}, B = \{2\}, C = \{3\}$. Left: $\{1\} \cap \{2, 3\} = \emptyset$. Right: $\emptyset \cup \{3\} = \{3\}$. Not equal.
