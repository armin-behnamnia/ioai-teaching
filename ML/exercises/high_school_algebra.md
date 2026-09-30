# High School Algebra — Challenging Practice Problems

## Topics Covered

0. [Algebraic Identities & Formulas (Reference)](#0-algebraic-identities--formulas-reference)
1. [Linear Equations & Inequalities](#1-linear-equations--inequalities)
2. [Quadratics & Parabolas](#2-quadratics--parabolas)
3. [Polynomials](#3-polynomials)
4. [Rational Expressions & Equations](#4-rational-expressions--equations)
5. [Systems of Equations](#5-systems-of-equations)
6. [Exponents & Radicals](#6-exponents--radicals)
7. [Functions & Composition](#7-functions--composition)
8. [Logarithms](#8-logarithms)
9. [Sequences & Series](#9-sequences--series)
10. [Challenge Mixed Bag](#10-challenge-mixed-bag)

---

## 0. Algebraic Identities & Formulas (Reference)

> A comprehensive collection of valid algebraic statements used throughout high school algebra. Keep this section as a reference while solving the practice problems.

---

### 0.1 Expansions

$$(a + b)^2 = a^2 + 2ab + b^2$$

$$(a - b)^2 = a^2 - 2ab + b^2$$

$$(a + b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$$

$$(a - b)^3 = a^3 - 3a^2b + 3ab^2 - b^3$$

$$(a + b + c)^2 = a^2 + b^2 + c^2 + 2ab + 2bc + 2ac$$

$$(a + b + c)^3 = a^3 + b^3 + c^3 + 3(a+b)(b+c)(a+c)$$

---

### 0.2 Factoring Identities

$$a^2 - b^2 = (a - b)(a + b) \quad \text{(Difference of squares)}$$

$$a^2 + b^2 = (a + b)^2 - 2ab$$

$$a^3 - b^3 = (a - b)(a^2 + ab + b^2) \quad \text{(Difference of cubes)}$$

$$a^3 + b^3 = (a + b)(a^2 - ab + b^2) \quad \text{(Sum of cubes)}$$

$$a^3 + b^3 + c^3 - 3abc = (a + b + c)(a^2 + b^2 + c^2 - ab - bc - ac)$$

$$a^n - b^n = (a - b)(a^{n-1} + a^{n-2}b + a^{n-3}b^2 + \cdots + ab^{n-2} + b^{n-1})$$

$$a^n + b^n = (a + b)(a^{n-1} - a^{n-2}b + a^{n-3}b^2 - \cdots + ab^{n-2} - b^{n-1}) \quad \text{($n$ odd)}$$

---

### 0.3 Special Factoring Identities

$$a^4 + 4b^4 = (a^2 + 2ab + 2b^2)(a^2 - 2ab + 2b^2) \quad \text{(Sophie Germain identity)}$$

$$a^4 + a^2b^2 + b^4 = (a^2 + ab + b^2)(a^2 - ab + b^2)$$

$$a^4 - b^4 = (a - b)(a + b)(a^2 + b^2)$$

---

### 0.4 Binomial Theorem

$$(a + b)^n = \sum_{k=0}^{n} \binom{n}{k} a^{n-k} b^k$$

where $\displaystyle\binom{n}{k} = \frac{n!}{k!\,(n-k)!}$.

**First few cases:**

$$(a+b)^2 = a^2 + 2ab + b^2$$

$$(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$$

$$(a+b)^4 = a^4 + 4a^3b + 6a^2b^2 + 4ab^3 + b^4$$

$$(a+b)^5 = a^5 + 5a^4b + 10a^3b^2 + 10a^2b^3 + 5ab^4 + b^5$$

---

### 0.5 Exponent Rules

$$a^m \cdot a^n = a^{m+n}$$

$$(a^m)^n = a^{mn}$$

$$(ab)^n = a^n b^n$$

$$\frac{a^m}{a^n} = a^{m-n} \quad (a \neq 0)$$

$$a^0 = 1 \quad (a \neq 0)$$

$$a^{-n} = \frac{1}{a^n} \quad (a \neq 0)$$

$$a^{1/n} = \sqrt[n]{a}$$

$$a^{m/n} = \sqrt[n]{a^m} = \left(\sqrt[n]{a}\right)^m$$

---

### 0.6 Radical Rules

$$\sqrt[n]{a} \cdot \sqrt[n]{b} = \sqrt[n]{ab}$$

$$\frac{\sqrt[n]{a}}{\sqrt[n]{b}} = \sqrt[n]{\frac{a}{b}} \quad (b \neq 0)$$

$$\left(\sqrt[n]{a}\right)^m = \sqrt[n]{a^m}$$

$$\sqrt[m]{\sqrt[n]{a}} = \sqrt[mn]{a}$$

$$\sqrt{a^2} = |a|$$

---

### 0.7 Rationalizing Denominators

$$\frac{1}{\sqrt{a}} = \frac{\sqrt{a}}{a} \quad (a > 0)$$

$$\frac{1}{a + \sqrt{b}} = \frac{a - \sqrt{b}}{a^2 - b} \quad (a^2 \neq b)$$

$$\frac{1}{\sqrt{a} - \sqrt{b}} = \frac{\sqrt{a} + \sqrt{b}}{a - b} \quad (a \neq b)$$

$$\frac{1}{\sqrt{a} + \sqrt{b} + \sqrt{c}} = \frac{(\sqrt{a}+\sqrt{b})-\sqrt{c}}{(\sqrt{a}+\sqrt{b})^2 - c} \cdot \frac{(\sqrt{a}+\sqrt{b})+\sqrt{c}}{(\sqrt{a}+\sqrt{b})+\sqrt{c}} \quad \text{(two-step)}$$

---

### 0.8 Quadratic Formula & Discriminant

For $ax^2 + bx + c = 0$ with $a \neq 0$:

$$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$

$$\Delta = b^2 - 4ac \quad \text{(discriminant)}$$

| Discriminant | Roots |
|---|---|
| $\Delta > 0$ | Two distinct real roots |
| $\Delta = 0$ | One repeated real root |
| $\Delta < 0$ | Two complex conjugate roots |

---

### 0.9 Vieta's Formulas

For $ax^2 + bx + c = 0$ with roots $\alpha$ and $\beta$:

$$\alpha + \beta = -\frac{b}{a}$$

$$\alpha \cdot \beta = \frac{c}{a}$$

For $ax^3 + bx^2 + cx + d = 0$ with roots $\alpha$, $\beta$, $\gamma$:

$$\alpha + \beta + \gamma = -\frac{b}{a}$$

$$\alpha\beta + \beta\gamma + \alpha\gamma = \frac{c}{a}$$

$$\alpha\beta\gamma = -\frac{d}{a}$$

---

### 0.10 Polynomial Division Theorems

**Remainder Theorem:** When $P(x)$ is divided by $(x - a)$, the remainder is $P(a)$.

**Factor Theorem:** $(x - a)$ is a factor of $P(x)$ if and only if $P(a) = 0$.

---

### 0.11 Logarithm Rules

$$\log_b(M \cdot N) = \log_b M + \log_b N$$

$$\log_b\left(\frac{M}{N}\right) = \log_b M - \log_b N$$

$$\log_b(M^p) = p \cdot \log_b M$$

$$\log_b b = 1, \quad \log_b 1 = 0$$

$$b^{\log_b M} = M$$

$$\log_b b^p = p$$

$$\log_a b = \frac{\log_c b}{\log_c a} \quad \text{(change of base)}$$

$$\log_a b = \frac{1}{\log_b a}$$

$$a^x = b^x \ln a \cdot \frac{1}{\ln b} \quad \text{or equivalently} \quad \log_a b = \frac{\ln b}{\ln a}$$

---

### 0.12 Inequality Rules

If $a > b$:

$$a + c > b + c \quad \text{(add any } c\text{)}$$

$$ac > bc \quad \text{if } c > 0 \qquad \text{(multiply by positive)}$$

$$ac < bc \quad \text{if } c < 0 \qquad \text{(multiply by negative — reverse!)}$$

$$\frac{1}{a} < \frac{1}{b} \quad \text{if } a, b > 0 \qquad \text{(reciprocal reverses)}$$

$$\sqrt{a} > \sqrt{b} \quad \text{if } a, b \geq 0 \qquad \text{(square root preserves)}$$

---

### 0.13 Absolute Value

$$|a| = \begin{cases} a & \text{if } a \geq 0 \\ -a & \text{if } a < 0 \end{cases}$$

$$|a|^2 = a^2$$

$$\sqrt{a^2} = |a|$$

$$|a \cdot b| = |a| \cdot |b|$$

$$\left|\frac{a}{b}\right| = \frac{|a|}{|b|} \quad (b \neq 0)$$

$$|a + b| \leq |a| + |b| \quad \text{(Triangle inequality)}$$

$$|a - b| \geq \big||a| - |b|\big|$$

---

### 0.14 Sequences & Series Formulas

**Arithmetic sequence** (first term $a_1$, common difference $d$):

$$a_n = a_1 + (n-1)d$$

$$S_n = \frac{n}{2}(a_1 + a_n) = \frac{n}{2}\bigl(2a_1 + (n-1)d\bigr)$$

**Geometric sequence** (first term $a_1$, common ratio $r$):

$$a_n = a_1 \cdot r^{n-1}$$

$$S_n = \frac{a_1(1 - r^n)}{1 - r} \quad (r \neq 1)$$

**Infinite geometric series** ($|r| < 1$):

$$S = \frac{a_1}{1 - r}$$

**Sum of first $n$ natural numbers:**

$$\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$$

**Sum of squares:**

$$\sum_{k=1}^{n} k^2 = \frac{n(n+1)(2n+1)}{6}$$

**Sum of cubes:**

$$\sum_{k=1}^{n} k^3 = \left(\frac{n(n+1)}{2}\right)^2$$

---

### 0.15 Completing the Square

$$ax^2 + bx + c = a\left(x + \frac{b}{2a}\right)^2 + \left(c - \frac{b^2}{4a}\right)$$

**Vertex form** of $f(x) = ax^2 + bx + c$:

$$f(x) = a\left(x - h\right)^2 + k, \quad \text{where } h = -\frac{b}{2a}, \; k = f(h)$$

Vertex: $(h, k)$. Axis of symmetry: $x = h$.

---

### 0.16 Function Composition & Inverses

$$(f \circ g)(x) = f(g(x))$$

$$f \circ f = f^2 \quad \text{(iterate)}$$

If $f^{-1}$ exists: $\quad f(f^{-1}(x)) = x \quad \text{and} \quad f^{-1}(f(x)) = x$

**To find $f^{-1}$:** set $y = f(x)$, swap $x \leftrightarrow y$, solve for $y$.

---

### 0.17 Even and Odd Functions

$$\text{Even: } f(-x) = f(x) \quad \text{(symmetric about } y\text{-axis)}$$

$$\text{Odd: } f(-x) = -f(x) \quad \text{(symmetric about origin)}$$

---

### 0.18 Partial Fractions

$$\frac{1}{(x-a)(x-b)} = \frac{1}{a-b}\left(\frac{1}{x-a} - \frac{1}{x-b}\right) \quad (a \neq b)$$

$$\frac{1}{(x-a)(x-b)(x-c)} = \frac{A}{x-a} + \frac{B}{x-b} + \frac{C}{x-c}$$

where $A$, $B$, $C$ are found by equating coefficients or substituting strategic $x$-values.

---

### 0.19 Key Inequalities (AM-GM)

**Arithmetic Mean — Geometric Mean (AM-GM):**

For non-negative real numbers $a_1, a_2, \ldots, a_n$:

$$\frac{a_1 + a_2 + \cdots + a_n}{n} \geq \sqrt[n]{a_1 a_2 \cdots a_n}$$

**Two-variable case:**

$$\frac{a + b}{2} \geq \sqrt{ab} \quad (a, b \geq 0)$$

Equality holds if and only if $a = b$.

**Useful corollary:**

$$a + \frac{1}{a} \geq 2 \quad (a > 0)$$

---

### 0.20 Distance, Midpoint & Slope

**Distance** between $(x_1, y_1)$ and $(x_2, y_2)$:

$$d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$

**Midpoint:**

$$\left(\frac{x_1 + x_2}{2}, \; \frac{y_1 + y_2}{2}\right)$$

**Slope:**

$$m = \frac{y_2 - y_1}{x_2 - x_1}$$

**Parallel lines:** $m_1 = m_2$

**Perpendicular lines:** $m_1 \cdot m_2 = -1$

**Point-slope form:** $y - y_1 = m(x - x_1)$

**Slope-intercept form:** $y = mx + b$

---

### 0.21 Misc Useful Identities

$$a + b = (\sqrt{a} + \sqrt{b})^2 - 2\sqrt{ab} \quad (a, b \geq 0)$$

$$(a - b)^2 = (a + b)^2 - 4ab$$

$$a^2 + b^2 = (a + b)^2 - 2ab = (a - b)^2 + 2ab$$

$$ab = \frac{(a+b)^2 - (a-b)^2}{4}$$

$$a^2 + b^2 + c^2 = (a+b+c)^2 - 2(ab+bc+ac)$$

$$a^3 + b^3 = (a+b)^3 - 3ab(a+b)$$

$$a^3 - b^3 = (a-b)^3 + 3ab(a-b)$$

$$\frac{a}{b} + \frac{b}{a} = \frac{a^2 + b^2}{ab} = \frac{(a+b)^2 - 2ab}{ab} \quad (ab \neq 0)$$

$$(a+b)(a-b) = a^2 - b^2$$

$$(a+b)\left(a^2 - ab + b^2\right) = a^3 + b^3$$

$$(a-b)\left(a^2 + ab + b^2\right) = a^3 - b^3$$

---

## 1. Linear Equations & Inequalities

### Problem 1.1

Solve for $x$:

$$\frac{2x - 3}{4} - \frac{x + 1}{3} = \frac{x - 1}{6}$$

### Problem 1.2

Solve for $x$ and express your answer as an interval:

$$\frac{2x - 1}{3} - \frac{x + 2}{2} \leq \frac{x - 5}{6}$$

### Problem 1.3

Solve for $x$:

$$|2x - 5| + |x + 3| = 10$$

### Problem 1.4

Find all values of $a$ such that the equation

$$\frac{x + a}{x - 2} = \frac{3}{x - 2} + 1$$

has no solution.

### Problem 1.5

Solve the inequality:

$$\frac{x - 3}{x + 2} > 0$$

Then solve:

$$\frac{x - 3}{x + 2} \geq 0$$

Explain why the two answers differ.

### Problem 1.6

A line passes through the point $(2, -3)$ and is perpendicular to the line $4x - 3y = 12$. Find the equation of the line in slope-intercept form.

### Problem 1.7

Find the value of $k$ such that the system has infinitely many solutions:

$$\begin{cases} 3x + ky = 12 \\ 2x + 4y = 8 \end{cases}$$

### Problem 1.8

Solve for $x$:

$$\frac{3}{x - 1} + \frac{2}{x + 1} = \frac{5x + 1}{x^2 - 1}$$

---

---

## 2. Quadratics & Parabolas

### Problem 2.1

Solve for $x$:

$$x^2 - 5x + 6 = 0$$

### Problem 2.2

Solve for $x$:

$$2x^2 + 7x + 3 = 0$$

### Problem 2.3

Find the values of $m$ for which the equation $x^2 + (m+1)x + m = 0$ has:
1. Two distinct real roots
2. Exactly one real root (a repeated root)
3. No real roots

### Problem 2.4

Find the vertex, axis of symmetry, $x$-intercepts, and $y$-intercept of:

$$f(x) = -2x^2 + 8x - 5$$

### Problem 2.5

Find the range of values of $k$ such that the equation

$$x^2 - 2(k+1)x + k^2 = 0$$

has two real roots whose product is greater than 15.

### Problem 2.6

Solve for $x$:

$$x^4 - 5x^2 + 4 = 0$$

### Problem 2.7

Solve for $x$:

$$x^2 - 6|x| + 5 = 0$$

### Problem 2.8

The parabola $y = ax^2 + bx + c$ passes through the points $(1, 6)$, $(2, 11)$, and $(3, 18)$. Find $a$, $b$, and $c$.

### Problem 2.9

Find the minimum value of the expression $x^2 + 4x + 7$ without using calculus.

### Problem 2.10

Solve the inequality:

$$x^2 - 5x + 6 < 0$$

Then solve:

$$\frac{x^2 - 5x + 6}{x - 1} \leq 0$$

---

---

## 3. Polynomials

### Problem 3.1

Factor completely:

$$x^3 - 2x^2 - 5x + 6$$

### Problem 3.2

Factor completely:

$$2x^3 + 3x^2 - 11x - 6$$

### Problem 3.3

Given that $x = 2$ is a root of $x^3 - 4x^2 + x + 6 = 0$, find all roots.

### Problem 3.4

When the polynomial $P(x) = x^3 + ax^2 + bx - 6$ is divided by $(x - 1)$, the remainder is $-2$. When divided by $(x + 2)$, the remainder is $4$. Find $a$ and $b$.

### Problem 3.5

Find the remainder when $x^{2024} + x^{2023} + 1$ is divided by $x + 1$.

### Problem 3.6

Factor completely:

$$x^4 - 1$$

Then factor completely over the integers:

$$x^4 + 4$$

> **Hint for the second part:** Try adding and subtracting $4x^2$.

### Problem 3.7

If $P(x) = 2x^3 - 5x^2 + 3x + 1$, find $P(3)$ using synthetic division and interpret the result in terms of the Remainder Theorem.

### Problem 3.8

Prove that $x - 1$ is a factor of $x^n - 1$ for any positive integer $n$.

### Problem 3.9

Simplify:

$$\frac{x^3 - 8}{x^2 - 4} \cdot \frac{x^2 + 2x + 4}{x^2 + 4x + 4}$$

### Problem 3.10

Find all values of $p$ such that $x^3 + px^2 - 20x + 12$ has a factor of $(x + 6)$.

---

---

## 4. Rational Expressions & Equations

### Problem 4.1

Simplify:

$$\frac{x^2 - 9}{x^2 + 5x + 6} \div \frac{x^2 - 2x - 3}{x^2 + 2x}$$

### Problem 4.2

Simplify:

$$\frac{1}{x - 1} + \frac{1}{x + 1} - \frac{2}{x^2 - 1}$$

### Problem 4.3

Solve for $x$:

$$\frac{2}{x + 1} + \frac{3}{x - 2} = 1$$

### Problem 4.4

Simplify:

$$\frac{\frac{1}{x} + \frac{1}{y}}{\frac{1}{x} - \frac{1}{y}}$$

### Problem 4.5

Solve for $x$:

$$\frac{x - 1}{x + 1} + \frac{x + 1}{x - 1} = \frac{10}{3}$$

### Problem 4.6

Simplify:

$$\left(\frac{x^3 - 1}{x^2 + x + 1}\right)^2 \cdot \frac{1}{(x - 1)^2}$$

### Problem 4.7

Find all values of $x$ for which the expression is undefined:

$$\frac{x^2 - 4x + 3}{x^2 - 2x - 3}$$

### Problem 4.8

Solve for $x$:

$$\frac{6}{x} + \frac{x}{x - 1} = 5$$

---

---

## 5. Systems of Equations

### Problem 5.1

Solve the system:

$$\begin{cases} 2x + 3y = 1 \\ 3x - y = 7 \end{cases}$$

### Problem 5.2

Solve the system:

$$\begin{cases} x + 2y + z = 7 \\ 2x - y + 3z = 7 \\ 3x + y - z = 8 \end{cases}$$

### Problem 5.3

Solve the system:

$$\begin{cases} x^2 + y^2 = 25 \\ x + y = 7 \end{cases}$$

### Problem 5.4

Solve the system:

$$\begin{cases} x + y = 5 \\ xy = 6 \end{cases}$$

### Problem 5.5

For what value of $k$ does the following system have no solution?

$$\begin{cases} 3x - 2y = 5 \\ kx + 4y = -6 \end{cases}$$

### Problem 5.6

Solve the system:

$$\begin{cases} \dfrac{1}{x} + \dfrac{1}{y} = 5 \\ \dfrac{1}{x} - \dfrac{1}{y} = 1 \end{cases}$$

### Problem 5.7

A boat travels 30 km downstream in 2 hours and 30 km upstream in 3 hours. Find the speed of the boat in still water and the speed of the current.

### Problem 5.8

Find $a$, $b$, and $c$ such that the polynomial $ax^2 + bx + c$ passes through $(1, 2)$, $(-1, 8)$, and $(2, 2)$.

---

---

## 6. Exponents & Radicals

### Problem 6.1

Simplify (assume $x > 0$):

$$\frac{x^{1/2} \cdot x^{2/3}}{x^{1/6}}$$

### Problem 6.2

Simplify:

$$\sqrt[3]{x^2} \cdot \sqrt[6]{x^4}$$

### Problem 6.3

Rationalize the denominator:

$$\frac{3}{2 - \sqrt{5}}$$

### Problem 6.4

Simplify:

$$\frac{\sqrt{12} + \sqrt{27}}{\sqrt{3}}$$

### Problem 6.5

Rationalize the denominator:

$$\frac{1}{1 + \sqrt{2} - \sqrt{3}}$$

### Problem 6.6

Solve for $x$:

$$\sqrt{x + 3} + \sqrt{x - 2} = 5$$

### Problem 6.7

Solve for $x$:

$$x^{2/3} - 5x^{1/3} + 6 = 0$$

### Problem 6.8

Simplify:

$$\left(x^{a} \cdot x^{2a}\right)^3 \div \left(x^{a+1}\right)^2$$

### Problem 6.9

Solve for $x$:

$$2^{x+1} \cdot 4^{x-1} = 32$$

### Problem 6.10

Simplify:

$$\sqrt{(x - 3)^2}$$

Express your answer as a piecewise function and explain why $\sqrt{x^2} = |x|$.

---

---

## 7. Functions & Composition

### Problem 7.1

Let $f(x) = 2x + 1$ and $g(x) = x^2 - 3$. Find:
1. $(f \circ g)(x)$
2. $(g \circ f)(x)$
3. $(f \circ f)(x)$
4. $(g \circ g)(x)$

### Problem 7.2

Let $f(x) = \frac{x + 1}{x - 1}$. Find $f^{-1}(x)$ and verify that $f(f^{-1}(x)) = x$.

### Problem 7.3

Find the domain of:

$$f(x) = \frac{\sqrt{x - 2}}{x^2 - 9}$$

### Problem 7.4

Let $f(x) = \frac{2x + 3}{x - 1}$. Find $\left(\frac{f(x) - f(2)}{x - 2}\right)$ and simplify.

### Problem 7.5

If $f(x) = x^2 + 1$ and $g(x) = \sqrt{x - 2}$, find the domain of $(f \circ g)(x)$ and $(g \circ f)(x)$.

### Problem 7.6

Let $f(x) = \frac{x - 3}{x + 2}$. Find $f^{-1}(x)$ and state the domain of $f^{-1}$.

### Problem 7.7

If $f(x + 2) = x^2 + 4x + 7$, find $f(x)$.

> **Hint:** Let $u = x + 2$ and substitute.

### Problem 7.8

Let $f(x) = 2x - 5$. Find $\frac{f(x+h) - f(x)}{h}$ and simplify.

### Problem 7.9

Determine whether $f(x) = \frac{x}{x^2 + 1}$ is even, odd, or neither. Justify your answer.

### Problem 7.10

Let $f(x) = x^2 - 4x + 3$. Find the interval(s) on which $f(x) > 0$.

---

---

## 8. Logarithms

### Problem 8.1

Evaluate:

1. $\log_2 32$
2. $\log_3 \left(\frac{1}{27}\right)$
3. $\log_5 1$
4. $\log_{10} 0.001$

### Problem 8.2

Express in terms of $\log a$, $\log b$, and $\log c$:

$$\log\left(\frac{a^2 b^3}{\sqrt{c}}\right)$$

### Problem 8.3

Solve for $x$:

$$\log_2(x + 1) + \log_2(x - 1) = 3$$

### Problem 8.4

Solve for $x$:

$$2^{x+1} = 5^{x-1}$$

> Give your answer in terms of logarithms.

### Problem 8.5

Simplify:

$$\log_4 8 + \log_4 2$$

### Problem 8.6

Solve for $x$:

$$\log_2 x + \log_2(x - 2) = 3$$

### Problem 8.7

If $\log_2 3 = a$ and $\log_2 5 = b$, express $\log_2 360$ in terms of $a$ and $b$.

### Problem 8.8

Solve for $x$:

$$\log_3(x) = \log_3(x+1) - 1$$

### Problem 8.9

Use the change of base formula to evaluate $\log_7 50$ to three decimal places.

### Problem 8.10

Solve for $x$:

$$3^{2x} - 10 \cdot 3^x + 9 = 0$$

---

---

## 9. Sequences & Series

### Problem 9.1

Find the 15th term of the arithmetic sequence: $3, 7, 11, 15, \ldots$

### Problem 9.2

Find the sum of the first 20 terms of the arithmetic sequence where $a_1 = 5$ and $d = 3$.

### Problem 9.3

Find the 8th term of the geometric sequence: $2, 6, 18, 54, \ldots$

### Problem 9.4

Find the sum of the infinite geometric series:

$$1 + \frac{1}{3} + \frac{1}{9} + \frac{1}{27} + \cdots$$

### Problem 9.5

The 3rd term of an arithmetic sequence is 9 and the 7th term is 21. Find the first term and the common difference.

### Problem 9.6

Find the sum:

$$\sum_{k=1}^{100} (3k - 1)$$

### Problem 9.7

For what values of $r$ does the infinite geometric series $\sum_{n=0}^{\infty} 2r^n$ converge? Find the sum when it converges.

### Problem 9.8

The sum of the first $n$ terms of a sequence is $S_n = n^2 + 2n$. Find the 10th term $a_{10}$.

> **Hint:** $a_n = S_n - S_{n-1}$.

### Problem 9.9

Insert three arithmetic means between 4 and 24.

### Problem 9.10

In a geometric sequence, the 2nd term is 6 and the 5th term is 162. Find the first term and the common ratio.

---

---

## 10. Challenge Mixed Bag

### Problem 10.1

Find all real solutions:

$$x^2 - 7x + 12 = \frac{2}{x - 3}$$

### Problem 10.2

If $a + b = 6$ and $ab = 4$, find $a^2 + b^2$ without solving for $a$ and $b$.

### Problem 10.3

Solve for $x$:

$$\sqrt{x} + \sqrt[4]{x} = 2$$

### Problem 10.4

Find all values of $k$ such that $x^2 + (k-2)x + k + 1 = 0$ has two equal real roots.

### Problem 10.5

If $f(x) = \frac{x^2 - 4}{x - 2}$, find $\lim_{x \to 2} f(x)$.

### Problem 10.6

Find the sum of all two-digit numbers divisible by 7.

### Problem 10.7

Solve for $x$:

$$4^x - 5 \cdot 2^x + 4 = 0$$

### Problem 10.8

Simplify:

$$\left(\frac{a^{-1} + b^{-1}}{a^{-2} - b^{-2}}\right)$$

### Problem 10.9

Find the minimum value of $f(x) = \frac{x^2 + 2x + 5}{x + 1}$ for $x > -1$.

> **Hint:** Let $t = x + 1$.

### Problem 10.10

A ball is dropped from a height of 10 meters. Each time it bounces, it rises to $\frac{3}{4}$ of its previous height. Find the total distance the ball travels before coming to rest.

### Problem 10.11

Solve for $x$ and $y$:

$$\begin{cases} 2^x \cdot 3^y = 18 \\ 2^y \cdot 3^x = 12 \end{cases}$$

### Problem 10.12

If the roots of $2x^2 - 7x + 3 = 0$ are $\alpha$ and $\beta$, find a quadratic equation whose roots are $\frac{1}{\alpha}$ and $\frac{1}{\beta}$.

### Problem 10.13

Find all integer values of $n$ such that $n^2 - 19n + 99$ is a perfect square.

### Problem 10.14

Let $a$, $b$, $c$ be distinct real numbers. Show that there is no quadratic $ax^2 + bx + c$ that has two equal roots.

> **Hint:** Consider the discriminant and use the AM-GM inequality, or argue directly.

### Problem 10.15

Find all real $x$ satisfying:

$$x^4 - 13x^2 + 36 \leq 0$$

---

---
---

# Solutions

## Solutions: Section 1 — Linear Equations & Inequalities

### Solution 1.1

$$\frac{2x - 3}{4} - \frac{x + 1}{3} = \frac{x - 1}{6}$$

Multiply through by 12 (the LCM of 4, 3, 6):

$$3(2x - 3) - 4(x + 1) = 2(x - 1)$$
$$6x - 9 - 4x - 4 = 2x - 2$$
$$2x - 13 = 2x - 2$$
$$-13 = -2$$

This is a contradiction. **No solution.**

### Solution 1.2

$$\frac{2x - 1}{3} - \frac{x + 2}{2} \leq \frac{x - 5}{6}$$

Multiply by 6:

$$2(2x - 1) - 3(x + 2) \leq x - 5$$
$$4x - 2 - 3x - 6 \leq x - 5$$
$$x - 8 \leq x - 5$$
$$-8 \leq -5$$

This is always true. The solution is **all real numbers**, i.e., $x \in (-\infty, \infty)$.

### Solution 1.3

$$|2x - 5| + |x + 3| = 10$$

Critical points: $x = \frac{5}{2}$ and $x = -3$.

**Case 1: $x < -3$.** Then $|2x-5| = 5-2x$ and $|x+3| = -x-3$.
$$5 - 2x + (-x - 3) = 10 \implies -3x + 2 = 10 \implies x = -\frac{8}{3}$$

But $-\frac{8}{3} \approx -2.67 > -3$, so this is **not** in the range $x < -3$. No solution here.

**Case 2: $-3 \leq x \leq \frac{5}{2}$.** Then $|2x-5| = 5-2x$ and $|x+3| = x+3$.
$$5 - 2x + x + 3 = 10 \implies -x + 8 = 10 \implies x = -2$$

Check: $-3 \leq -2 \leq \frac{5}{2}$. ✅ **$x = -2$.**

**Case 3: $x > \frac{5}{2}$.** Then $|2x-5| = 2x-5$ and $|x+3| = x+3$.
$$2x - 5 + x + 3 = 10 \implies 3x - 2 = 10 \implies x = 4$$

Check: $4 > \frac{5}{2}$. ✅ **$x = 4$.**

**Solutions: $x = -2$ or $x = 4$.**

### Solution 1.4

Multiply both sides by $(x - 2)$ (noting $x \neq 2$):

$$x + a = 3 + x - 2$$
$$x + a = x + 1$$
$$a = 1$$

- If $a = 1$: the equation reduces to $x + 1 = x + 1$, which is true for all $x \neq 2$ (infinitely many solutions).
- If $a \neq 1$: we get $a = 1$, a contradiction, so no $x$ satisfies the equation.

**The equation has no solution for all $a \neq 1$, i.e., $a \in \mathbb{R} \setminus \{1\}$.**

### Solution 1.5

$$\frac{x - 3}{x + 2} > 0$$

The fraction is positive when numerator and denominator have the same sign. Critical points: $x = 3$, $x = -2$.

- $x < -2$: numerator $< 0$, denominator $< 0$ → positive ✅
- $-2 < x < 3$: numerator $< 0$, denominator $> 0$ → negative
- $x > 3$: numerator $> 0$, denominator $> 0$ → positive ✅

**Answer:** $x \in (-\infty, -2) \cup (3, \infty)$.

For $\frac{x-3}{x+2} \geq 0$: same regions, but $x = 3$ is now included (numerator = 0 makes the fraction 0, which satisfies $\geq 0$). $x = -2$ is still excluded (division by zero).

**Answer:** $x \in (-\infty, -2) \cup [3, \infty)$.

**Difference:** The $\geq$ version includes $x = 3$ because the fraction equals zero there.

### Solution 1.6

The given line: $4x - 3y = 12 \implies y = \frac{4}{3}x - 4$, so slope $= \frac{4}{3}$.

Perpendicular slope $= -\frac{3}{4}$.

Equation: $y - (-3) = -\frac{3}{4}(x - 2)$

$$y + 3 = -\frac{3}{4}x + \frac{3}{2}$$
$$y = -\frac{3}{4}x - \frac{3}{2}$$

### Solution 1.7

The system $\begin{cases} 3x + ky = 12 \\ 2x + 4y = 8 \end{cases}$ has infinitely many solutions when the equations are proportional:

$$\frac{3}{2} = \frac{k}{4} = \frac{12}{8} = \frac{3}{2}$$

So $\frac{k}{4} = \frac{3}{2} \implies k = 6$.

**$k = 6$.**

### Solution 1.8

$$\frac{3}{x-1} + \frac{2}{x+1} = \frac{5x+1}{(x-1)(x+1)}$$

Common denominator is $x^2 - 1$:

$$\frac{3(x+1) + 2(x-1)}{x^2-1} = \frac{5x+1}{x^2-1}$$
$$\frac{3x+3+2x-2}{x^2-1} = \frac{5x+1}{x^2-1}$$
$$\frac{5x+1}{x^2-1} = \frac{5x+1}{x^2-1}$$

This is always true (for $x \neq \pm 1$). **All real $x$ except $x = 1$ and $x = -1$.**

---

## Solutions: Section 2 — Quadratics & Parabolas

### Solution 2.1

$$x^2 - 5x + 6 = 0 \implies (x-2)(x-3) = 0 \implies \boxed{x = 2 \text{ or } x = 3}$$

### Solution 2.2

$$2x^2 + 7x + 3 = 0$$

By the quadratic formula: $x = \frac{-7 \pm \sqrt{49 - 24}}{4} = \frac{-7 \pm 5}{4}$

$$x = \frac{-7+5}{4} = -\frac{1}{2}, \quad x = \frac{-7-5}{4} = -3$$

**$x = -\frac{1}{2}$ or $x = -3$.**

### Solution 2.3

Discriminant: $\Delta = (m+1)^2 - 4m = m^2 + 2m + 1 - 4m = m^2 - 2m + 1 = (m-1)^2$.

1. Two distinct real roots: $(m-1)^2 > 0 \implies$ **$m \neq 1$**
2. One repeated root: $(m-1)^2 = 0 \implies$ **$m = 1$**
3. No real roots: $(m-1)^2 < 0$ → **never** (a square is always $\geq 0$)

### Solution 2.4

$$f(x) = -2x^2 + 8x - 5$$

**Vertex:** $x = -\frac{b}{2a} = -\frac{8}{2(-2)} = 2$. Then $f(2) = -8 + 16 - 5 = 3$. Vertex: $(2, 3)$.

**Axis of symmetry:** $x = 2$.

**$x$-intercepts:** $-2x^2 + 8x - 5 = 0 \implies x = \frac{-8 \pm \sqrt{64-40}}{-4} = \frac{-8 \pm \sqrt{24}}{-4} = \frac{-8 \pm 2\sqrt{6}}{-4} = \frac{4 \mp \sqrt{6}}{2} = 2 \mp \frac{\sqrt{6}}{2}$.

**$y$-intercept:** $f(0) = -5$.

### Solution 2.5

Product of roots $= k^2$ (by Vieta's: product $= \frac{c}{a} = k^2$).

Need: $k^2 > 15$ and discriminant $\geq 0$.

Discriminant: $4(k+1)^2 - 4k^2 = 4(k^2+2k+1) - 4k^2 = 8k + 4 \geq 0 \implies k \geq -\frac{1}{2}$.

$k^2 > 15 \implies k > \sqrt{15}$ or $k < -\sqrt{15}$.

Intersecting with $k \geq -\frac{1}{2}$: $\sqrt{15} \approx 3.87 > -\frac{1}{2}$, and $-\sqrt{15} \approx -3.87 < -\frac{1}{2}$.

**$k > \sqrt{15}$, i.e., $k \in (\sqrt{15}, \infty)$.**

### Solution 2.6

Let $u = x^2$:

$$u^2 - 5u + 4 = 0 \implies (u-1)(u-4) = 0 \implies u = 1 \text{ or } u = 4$$

$$x^2 = 1 \implies x = \pm 1, \quad x^2 = 4 \implies x = \pm 2$$

**$x \in \{-2, -1, 1, 2\}$.**

### Solution 2.7

Since $|x|^2 = x^2$, substitute $u = |x| \geq 0$:

$$u^2 - 6u + 5 = 0 \implies (u-1)(u-5) = 0 \implies u = 1 \text{ or } u = 5$$

$$|x| = 1 \implies x = \pm 1, \quad |x| = 5 \implies x = \pm 5$$

**$x \in \{-5, -1, 1, 5\}$.**

### Solution 2.8

$\begin{cases} a + b + c = 6 \\ 4a + 2b + c = 11 \\ 9a + 3b + c = 18 \end{cases}$

Subtract eq.1 from eq.2: $3a + b = 5$.
Subtract eq.2 from eq.3: $5a + b = 7$.

Subtract: $2a = 2 \implies a = 1$. Then $b = 2$. Then $c = 3$.

**$a = 1, b = 2, c = 3$.** (So $f(x) = x^2 + 2x + 3$.)

### Solution 2.9

$$x^2 + 4x + 7 = (x^2 + 4x + 4) + 3 = (x + 2)^2 + 3$$

Since $(x+2)^2 \geq 0$, the minimum value is **3**, achieved at $x = -2$.

### Solution 2.10

**Part 1:** $x^2 - 5x + 6 < 0 \implies (x-2)(x-3) < 0 \implies x \in (2, 3)$.

**Part 2:** $\frac{(x-2)(x-3)}{x-1} \leq 0$.

Critical points: $x = 1, 2, 3$. Sign chart:

| Interval | $x-1$ | $x-2$ | $x-3$ | Fraction | |
|---|---|---|---|---|---|
| $x < 1$ | $-$ | $-$ | $-$ | $-$ | ✅ |
| $1 < x < 2$ | $+$ | $-$ | $-$ | $+$ | |
| $2 \leq x \leq 3$ | $+$ | $+$/$0$ | $-$/$0$ | $-$/$0$ | ✅ |
| $x > 3$ | $+$ | $+$ | $+$ | $+$ | |

**Answer:** $x \in (-\infty, 1) \cup [2, 3]$.

---

## Solutions: Section 3 — Polynomials

### Solution 3.1

Try $x = 1$: $1 - 2 - 5 + 6 = 0$. ✅ So $(x-1)$ is a factor.

Divide: $x^3 - 2x^2 - 5x + 6 = (x-1)(x^2 - x - 6) = (x-1)(x-3)(x+2)$.

**$(x-1)(x-3)(x+2)$.**

### Solution 3.2

Try $x = -2$: $-16 + 12 + 22 - 6 = 12 \neq 0$.
Try $x = 3$: $54 + 27 - 33 - 6 = 42 \neq 0$.
Try $x = -3$: $-54 + 27 + 33 - 6 = 0$. ✅

Divide: $2x^3 + 3x^2 - 11x - 6 = (x+3)(2x^2 - 3x - 2) = (x+3)(2x+1)(x-2)$.

**$(x+3)(2x+1)(x-2)$.**

### Solution 3.3

$x = 2$ is a root, so $(x-2)$ is a factor. Divide:

$$x^3 - 4x^2 + x + 6 = (x-2)(x^2 - 2x - 3) = (x-2)(x-3)(x+1)$$

**Roots: $x = 2, 3, -1$.**

### Solution 3.4

By the Remainder Theorem:
- $P(1) = 1 + a + b - 6 = -2 \implies a + b = 3$
- $P(-2) = -8 + 4a - 2b - 6 = 4 \implies 4a - 2b = 18 \implies 2a - b = 9$

Add: $3a = 12 \implies a = 4$. Then $b = -1$.

**$a = 4, b = -1$.**

### Solution 3.5

By the Remainder Theorem, remainder $= P(-1) = (-1)^{2024} + (-1)^{2023} + 1 = 1 - 1 + 1 = 1$.

**Remainder = 1.**

### Solution 3.6

**First:** $x^4 - 1 = (x^2-1)(x^2+1) = (x-1)(x+1)(x^2+1)$.

**Second:** $x^4 + 4 = x^4 + 4x^2 + 4 - 4x^2 = (x^2+2)^2 - (2x)^2 = (x^2+2x+2)(x^2-2x+2)$.

**$(x^2+2x+2)(x^2-2x+2)$.** *(This is the Sophie Germain identity.)*

### Solution 3.7

Synthetic division of $2x^3 - 5x^2 + 3x + 1$ by $(x - 3)$:

$$\begin{array}{c|rrrr} 3 & 2 & -5 & 3 & 1 \\ & & 6 & 3 & 18 \\ \hline & 2 & 1 & 6 & \boxed{19} \end{array}$$

$P(3) = 19$. By the Remainder Theorem, dividing by $(x - 3)$ gives remainder $P(3) = 19$. ✅

### Solution 3.8

By the Factor Theorem, $(x - 1)$ is a factor of $P(x)$ iff $P(1) = 0$.

$P(1) = 1^n - 1 = 1 - 1 = 0$. ✅

### Solution 3.9

$$\frac{x^3 - 8}{x^2 - 4} \cdot \frac{x^2+2x+4}{x^2+4x+4} = \frac{(x-2)(x^2+2x+4)}{(x-2)(x+2)} \cdot \frac{x^2+2x+4}{(x+2)^2}$$

$$= \frac{(x^2+2x+4)^2}{(x+2)^3}$$

### Solution 3.10

By the Factor Theorem, $P(-6) = 0$:

$$(-6)^3 + p(-6)^2 - 20(-6) + 12 = 0$$
$$-216 + 36p + 120 + 12 = 0$$
$$36p - 84 = 0$$
$$p = \frac{84}{36} = \frac{7}{3}$$

**$p = \frac{7}{3}$.**

---

## Solutions: Section 4 — Rational Expressions & Equations

### Solution 4.1

$$\frac{(x-3)(x+3)}{(x+2)(x+3)} \cdot \frac{x(x+2)}{(x-3)(x+1)} = \frac{x}{x+1}$$

**$\frac{x}{x+1}$.**

### Solution 4.2

$$\frac{1}{x-1} + \frac{1}{x+1} - \frac{2}{(x-1)(x+1)}$$

$$= \frac{(x+1) + (x-1) - 2}{(x-1)(x+1)} = \frac{2x - 2}{(x-1)(x+1)} = \frac{2(x-1)}{(x-1)(x+1)} = \frac{2}{x+1}$$

### Solution 4.3

Common denominator $(x+1)(x-2)$:

$$2(x-2) + 3(x+1) = (x+1)(x-2)$$
$$2x - 4 + 3x + 3 = x^2 - x - 2$$
$$5x - 1 = x^2 - x - 2$$
$$x^2 - 6x + 1 = 0$$
$$x = \frac{6 \pm \sqrt{36-4}}{2} = \frac{6 \pm \sqrt{32}}{2} = 3 \pm 2\sqrt{2}$$

**$x = 3 \pm 2\sqrt{2}$.**

### Solution 4.4

$$\frac{\frac{y+x}{xy}}{\frac{y-x}{xy}} = \frac{x+y}{y-x}$$

**$\frac{x+y}{y-x}$.**

### Solution 4.5

Let $u = \frac{x-1}{x+1}$. Then the equation becomes:

$$u + \frac{1}{u} = \frac{10}{3}$$

$$3u^2 - 10u + 3 = 0 \implies (3u-1)(u-3) = 0 \implies u = \frac{1}{3} \text{ or } u = 3$$

$u = \frac{1}{3}$: $\frac{x-1}{x+1} = \frac{1}{3} \implies 3x - 3 = x + 1 \implies 2x = 4 \implies x = 2$.

$u = 3$: $\frac{x-1}{x+1} = 3 \implies x - 1 = 3x + 3 \implies -2x = 4 \implies x = -2$.

**$x = 2$ or $x = -2$.**

### Solution 4.6

$$\left(\frac{(x-1)(x^2+x+1)}{x^2+x+1}\right)^2 \cdot \frac{1}{(x-1)^2} = (x-1)^2 \cdot \frac{1}{(x-1)^2} = 1$$

### Solution 4.7

Denominator $= 0$: $x^2 - 2x - 3 = 0 \implies (x-3)(x+1) = 0 \implies x = 3$ or $x = -1$.

Numerator $= 0$: $x^2 - 4x + 3 = 0 \implies (x-1)(x-3) = 0 \implies x = 1$ or $x = 3$.

The expression is undefined when the denominator is zero: **$x = 3$ or $x = -1$**.

(Note: at $x = 3$, both numerator and denominator are zero — there's a "hole," but the expression is still undefined there.)

### Solution 4.8

$$\frac{6(x-1) + x^2}{x(x-1)} = 5$$

$$x^2 + 6x - 6 = 5x^2 - 5x$$
$$-4x^2 + 11x - 6 = 0$$
$$4x^2 - 11x + 6 = 0$$
$$x = \frac{11 \pm \sqrt{121-96}}{8} = \frac{11 \pm 5}{8}$$

$$x = 2 \quad \text{or} \quad x = \frac{3}{4}$$

**$x = 2$ or $x = \frac{3}{4}$.**

---

## Solutions: Section 5 — Systems of Equations

### Solution 5.1

From eq.2: $y = 3x - 7$.

Substitute: $2x + 3(3x - 7) = 1 \implies 2x + 9x - 21 = 1 \implies 11x = 22 \implies x = 2$.

$y = 3(2) - 7 = -1$.

**$x = 2, y = -1$.**

### Solution 5.2

From eq.3: $z = 3x + y - 8$.

Substitute into eq.1: $x + 2y + (3x + y - 8) = 7 \implies 4x + 3y = 15$.

Substitute into eq.2: $2x - y + 3(3x + y - 8) = 7 \implies 11x + 2y = 31$.

Solve the $2 \times 2$ system: multiply first by 2 ($8x + 6y = 30$), second by 3 ($33x + 6y = 93$), subtract:

$$25x = 63 \implies x = \frac{63}{25}$$

$$y = \frac{15 - 4 \cdot \frac{63}{25}}{3} = \frac{\frac{375 - 252}{25}}{3} = \frac{123}{75} = \frac{41}{25}$$

$$z = 3 \cdot \frac{63}{25} + \frac{41}{25} - 8 = \frac{189 + 41 - 200}{25} = \frac{30}{25} = \frac{6}{5}$$

**$x = \frac{63}{25}, \; y = \frac{41}{25}, \; z = \frac{6}{5}$.**

### Solution 5.3

From eq.2: $y = 7 - x$.

Substitute: $x^2 + (7-x)^2 = 25 \implies x^2 + 49 - 14x + x^2 = 25 \implies 2x^2 - 14x + 24 = 0 \implies x^2 - 7x + 12 = 0 \implies (x-3)(x-4) = 0$.

$x = 3 \implies y = 4$. $x = 4 \implies y = 3$.

**Solutions: $(3, 4)$ and $(4, 3)$.**

### Solution 5.4

$x$ and $y$ are roots of $t^2 - 5t + 6 = 0 \implies (t-2)(t-3) = 0$.

**Solutions: $(x, y) = (2, 3)$ or $(3, 2)$.**

### Solution 5.5

The system has no solution when the lines are parallel but not coincident:

$$\frac{3}{k} = \frac{-2}{4} \implies \frac{3}{k} = -\frac{1}{2} \implies k = -6$$

Check: $3(-6) \neq -2 \cdot 5$? $-18 \neq -10$. ✅ Not coincident.

**$k = -6$.**

### Solution 5.6

Add: $\frac{2}{x} = 6 \implies x = \frac{1}{3}$.

Subtract: $\frac{2}{y} = 4 \implies y = \frac{1}{2}$.

**$x = \frac{1}{3}, y = \frac{1}{2}$.**

### Solution 5.7

Let $b$ = boat speed, $c$ = current speed.

$$\begin{cases} b + c = 15 \\ b - c = 10 \end{cases}$$

Add: $2b = 25 \implies b = 12.5$. Subtract: $2c = 5 \implies c = 2.5$.

**Boat: 12.5 km/h, current: 2.5 km/h.**

### Solution 5.8

$\begin{cases} a + b + c = 2 \\ a - b + c = 8 \\ 4a + 2b + c = 2 \end{cases}$

Eq.1 $-$ Eq.2: $2b = -6 \implies b = -3$.

Eq.1: $a - 3 + c = 2 \implies a + c = 5$.

Eq.3: $4a - 6 + c = 2 \implies 4a + c = 8$.

Subtract: $3a = 3 \implies a = 1$. Then $c = 4$.

**$a = 1, b = -3, c = 4$.** (So $f(x) = x^2 - 3x + 4$.)

---

## Solutions: Section 6 — Exponents & Radicals

### Solution 6.1

$$\frac{x^{1/2 + 2/3}}{x^{1/6}} = \frac{x^{7/6}}{x^{1/6}} = x^{6/6} = x$$

### Solution 6.2

$$x^{2/3} \cdot x^{4/6} = x^{2/3} \cdot x^{2/3} = x^{4/3}$$

### Solution 6.3

$$\frac{3}{2 - \sqrt{5}} \cdot \frac{2 + \sqrt{5}}{2 + \sqrt{5}} = \frac{3(2 + \sqrt{5})}{4 - 5} = \frac{6 + 3\sqrt{5}}{-1} = -6 - 3\sqrt{5}$$

### Solution 6.4

$$\frac{2\sqrt{3} + 3\sqrt{3}}{\sqrt{3}} = \frac{5\sqrt{3}}{\sqrt{3}} = 5$$

### Solution 6.5

$$\frac{1}{1 + \sqrt{2} - \sqrt{3}}$$

Group as $\frac{1}{(1 + \sqrt{2}) - \sqrt{3}}$ and multiply by $(1+\sqrt{2}) + \sqrt{3}$:

$$= \frac{(1+\sqrt{2})+\sqrt{3}}{(1+\sqrt{2})^2 - 3} = \frac{(1+\sqrt{2})+\sqrt{3}}{1 + 2\sqrt{2} + 2 - 3} = \frac{(1+\sqrt{2})+\sqrt{3}}{2\sqrt{2}}$$

$$= \frac{1+\sqrt{2}+\sqrt{3}}{2\sqrt{2}} \cdot \frac{\sqrt{2}}{\sqrt{2}} = \frac{\sqrt{2} + 2 + \sqrt{6}}{4}$$

### Solution 6.6

$$\sqrt{x+3} = 5 - \sqrt{x-2}$$

Square: $x + 3 = 25 - 10\sqrt{x-2} + x - 2 \implies x + 3 = 23 + x - 10\sqrt{x-2}$

$$-20 = -10\sqrt{x-2} \implies \sqrt{x-2} = 2 \implies x - 2 = 4 \implies x = 6$$

Verify: $\sqrt{9} + \sqrt{4} = 3 + 2 = 5$. ✅ **$x = 6$.**

### Solution 6.7

Let $u = x^{1/3}$:

$$u^2 - 5u + 6 = 0 \implies (u-2)(u-3) = 0 \implies u = 2 \text{ or } u = 3$$

$$x = 8 \text{ or } x = 27$$

### Solution 6.8

$$\frac{x^{3a}}{x^{2a+2}} = x^{3a - 2a - 2} = x^{a - 2}$$

### Solution 6.9

$$2^{x+1} \cdot 2^{2(x-1)} = 2^5$$

$$2^{x+1+2x-2} = 2^5 \implies 2^{3x-1} = 2^5 \implies 3x - 1 = 5 \implies x = 2$$

### Solution 6.10

$$\sqrt{(x-3)^2} = |x - 3| = \begin{cases} x - 3 & \text{if } x \geq 3 \\ 3 - x & \text{if } x < 3 \end{cases}$$

In general, $\sqrt{x^2} = |x|$ because the square root function returns the **non-negative** root, and $|x|$ is the non-negative value whose square is $x^2$.

---

## Solutions: Section 7 — Functions & Composition

### Solution 7.1

1. $(f \circ g)(x) = f(x^2 - 3) = 2(x^2 - 3) + 1 = 2x^2 - 5$
2. $(g \circ f)(x) = g(2x+1) = (2x+1)^2 - 3 = 4x^2 + 4x - 2$
3. $(f \circ f)(x) = f(2x+1) = 2(2x+1)+1 = 4x+3$
4. $(g \circ g)(x) = g(x^2-3) = (x^2-3)^2 - 3 = x^4 - 6x^2 + 6$

### Solution 7.2

$$y = \frac{x+1}{x-1}$$

Swap $x$ and $y$: $x = \frac{y+1}{y-1} \implies x(y-1) = y+1 \implies xy - x = y + 1 \implies y(x-1) = x+1 \implies y = \frac{x+1}{x-1}$.

So $f^{-1}(x) = \frac{x+1}{x-1}$. (The function is its own inverse!)

**Verification:** $f\!\left(\frac{x+1}{x-1}\right) = \frac{\frac{x+1}{x-1}+1}{\frac{x+1}{x-1}-1} = \frac{\frac{x+1+x-1}{x-1}}{\frac{x+1-x+1}{x-1}} = \frac{\frac{2x}{x-1}}{\frac{2}{x-1}} = x$. ✅

### Solution 7.3

- **Numerator:** $\sqrt{x - 2}$ requires $x - 2 \geq 0 \implies x \geq 2$.
- **Denominator:** $x^2 - 9 \neq 0 \implies x \neq \pm 3$.

**Domain:** $[2, 3) \cup (3, \infty)$.

### Solution 7.4

$$f(x) - f(2) = \frac{2x+3}{x-1} - \frac{7}{1} = \frac{2x+3 - 7(x-1)}{x-1} = \frac{2x+3-7x+7}{x-1} = \frac{-5x+10}{x-1} = \frac{-5(x-2)}{x-1}$$

$$\frac{f(x) - f(2)}{x - 2} = \frac{-5(x-2)}{(x-1)(x-2)} = \frac{-5}{x-1}$$

### Solution 7.5

$(f \circ g)(x) = f(\sqrt{x-2}) = (\sqrt{x-2})^2 + 1 = x - 2 + 1 = x - 1$.

Domain: need $\sqrt{x-2}$ defined, so $x \geq 2$. **Domain: $[2, \infty)$.**

$(g \circ f)(x) = g(x^2 + 1) = \sqrt{(x^2+1) - 2} = \sqrt{x^2 - 1}$.

Need $x^2 - 1 \geq 0 \implies |x| \geq 1$. **Domain: $(-\infty, -1] \cup [1, \infty)$.**

### Solution 7.6

$y = \frac{x-3}{x+2}$. Swap: $x = \frac{y-3}{y+2} \implies x(y+2) = y-3 \implies xy + 2x = y - 3 \implies y(x-1) = -2x - 3 \implies y = \frac{-2x-3}{x-1} = \frac{2x+3}{1-x}$.

$f^{-1}(x) = \frac{2x+3}{1-x}$.

Domain of $f^{-1}$: $x \neq 1$ (since $f$ has range $\mathbb{R} \setminus \{1\}$ — $f(x) = 1$ has no solution).

### Solution 7.7

Let $u = x + 2$, so $x = u - 2$:

$$f(u) = (u-2)^2 + 4(u-2) + 7 = u^2 - 4u + 4 + 4u - 8 + 7 = u^2 + 3$$

**$f(x) = x^2 + 3$.**

### Solution 7.8

$$\frac{f(x+h) - f(x)}{h} = \frac{2(x+h) - 5 - (2x - 5)}{h} = \frac{2h}{h} = 2$$

### Solution 7.9

$$f(-x) = \frac{-x}{(-x)^2 + 1} = \frac{-x}{x^2 + 1} = -f(x)$$

Since $f(-x) = -f(x)$, the function is **odd**.

### Solution 7.10

$$x^2 - 4x + 3 = (x-1)(x-3) > 0$$

The parabola opens upward with roots at $x = 1$ and $x = 3$.

**$f(x) > 0$ on $(-\infty, 1) \cup (3, \infty)$.**

---

## Solutions: Section 8 — Logarithms

### Solution 8.1

1. $\log_2 32 = \log_2 2^5 = 5$
2. $\log_3 \frac{1}{27} = \log_3 3^{-3} = -3$
3. $\log_5 1 = 0$
4. $\log_{10} 0.001 = \log_{10} 10^{-3} = -3$

### Solution 8.2

$$\log\left(\frac{a^2 b^3}{\sqrt{c}}\right) = \log(a^2 b^3) - \log(c^{1/2}) = 2\log a + 3\log b - \frac{1}{2}\log c$$

### Solution 8.3

$$\log_2((x+1)(x-1)) = 3 \implies x^2 - 1 = 8 \implies x^2 = 9 \implies x = \pm 3$$

Check $x = -3$: $\log_2(-2)$ is undefined. ✗
Check $x = 3$: $\log_2 4 + \log_2 2 = 2 + 1 = 3$. ✅

**$x = 3$.**

### Solution 8.4

$$2^{x+1} = 5^{x-1}$$

$$(x+1)\ln 2 = (x-1)\ln 5$$

$$x \ln 2 + \ln 2 = x \ln 5 - \ln 5$$

$$x(\ln 2 - \ln 5) = -\ln 5 - \ln 2$$

$$x = \frac{\ln 5 + \ln 2}{\ln 5 - \ln 2} = \frac{\ln 10}{\ln\frac{5}{2}}$$

### Solution 8.5

$$\log_4 8 + \log_4 2 = \log_4(8 \cdot 2) = \log_4 16 = 2$$

### Solution 8.6

$$\log_2(x(x-2)) = 3 \implies x(x-2) = 8 \implies x^2 - 2x - 8 = 0 \implies (x-4)(x+2) = 0$$

$x = 4$ (valid: $x > 2$ ✅). $x = -2$ (invalid: $\log_2(-2)$ undefined ✗).

**$x = 4$.**

### Solution 8.7

$360 = 2^3 \cdot 3^2 \cdot 5$

$$\log_2 360 = 3\log_2 2 + 2\log_2 3 + \log_2 5 = 3 + 2a + b$$

### Solution 8.8

$$\log_3 x = \log_3(x+1) - 1 = \log_3(x+1) - \log_3 3$$

$$\log_3 x = \log_3\frac{x+1}{3}$$

$$x = \frac{x+1}{3} \implies 3x = x + 1 \implies 2x = 1 \implies x = \frac{1}{2}$$

Check: $\log_3 \frac{1}{2} = \log_3 \frac{3}{2} - 1$. $\log_3 \frac{1}{2} \approx -0.63$, $\log_3 1.5 - 1 \approx 0.37 - 1 = -0.63$. ✅

**$x = \frac{1}{2}$.**

### Solution 8.9

$$\log_7 50 = \frac{\ln 50}{\ln 7} \approx \frac{3.9120}{1.9459} \approx 2.010$$

### Solution 8.10

Let $u = 3^x > 0$:

$$u^2 - 10u + 9 = 0 \implies (u-1)(u-9) = 0 \implies u = 1 \text{ or } u = 9$$

$$3^x = 1 \implies x = 0, \quad 3^x = 9 \implies x = 2$$

**$x = 0$ or $x = 2$.**

---

## Solutions: Section 9 — Sequences & Series

### Solution 9.1

$a_1 = 3$, $d = 4$. $a_{15} = 3 + 14 \cdot 4 = 3 + 56 = 59$.

### Solution 9.2

$$S_{20} = \frac{20}{2}(2 \cdot 5 + 19 \cdot 3) = 10(10 + 57) = 670$$

### Solution 9.3

$a_1 = 2$, $r = 3$. $a_8 = 2 \cdot 3^7 = 2 \cdot 2187 = 4374$.

### Solution 9.4

$a_1 = 1$, $r = \frac{1}{3}$, $|r| < 1$.

$$S = \frac{a_1}{1 - r} = \frac{1}{1 - \frac{1}{3}} = \frac{1}{\frac{2}{3}} = \frac{3}{2}$$

### Solution 9.5

$a_3 = a_1 + 2d = 9$, $a_7 = a_1 + 6d = 21$.

Subtract: $4d = 12 \implies d = 3$. Then $a_1 = 9 - 6 = 3$.

**$a_1 = 3, d = 3$.**

### Solution 9.6

$$\sum_{k=1}^{100}(3k - 1) = 3 \cdot \frac{100 \cdot 101}{2} - 100 = 15150 - 100 = 15050$$

### Solution 9.7

Converges when $|r| < 1$, i.e., $-1 < r < 1$.

$$S = \frac{2}{1 - r}$$

### Solution 9.8

$$a_{10} = S_{10} - S_9 = (100 + 20) - (81 + 18) = 120 - 99 = 21$$

### Solution 9.9

Insert three arithmetic means between 4 and 24. This gives 5 terms: $4, a_2, a_3, a_4, 24$.

$a_5 = 4 + 4d = 24 \implies d = 5$.

**The means are 9, 14, 19.**

### Solution 9.10

$a_2 = a_1 r = 6$, $a_5 = a_1 r^4 = 162$.

$\frac{a_5}{a_2} = r^3 = \frac{162}{6} = 27 \implies r = 3$.

$a_1 = \frac{6}{3} = 2$.

**$a_1 = 2, r = 3$.**

---

## Solutions: Section 10 — Challenge Mixed Bag

### Solution 10.1

$$x^2 - 7x + 12 = \frac{2}{x-3}$$

Factor: $x^2 - 7x + 12 = (x-3)(x-4)$, so:

$$(x-3)(x-4) = \frac{2}{x-3}$$

Multiply by $(x-3)$ (noting $x \neq 3$):

$$(x-3)^2(x-4) = 2$$

Let $u = x - 3$:

$$u^2(u - 1) = 2 \implies u^3 - u^2 - 2 = 0$$

**Checking rational roots** ($\pm 1, \pm 2$): none satisfy the equation ($u=1: -2$, $u=-1: -4$, $u=2: 2$, $u=-2: -14$). The cubic has no rational roots.

Using numerical methods (e.g., Newton's method), the real root is $u \approx 1.696$, so $x \approx 4.696$.

**The equation has one real solution $x \approx 4.696$** (and two complex solutions). The exact form requires the cubic formula.

> **Note:** This problem is intentionally challenging — the resulting cubic does not factor nicely, demonstrating that not all algebraic equations have clean solutions.

### Solution 10.2

$$a^2 + b^2 = (a+b)^2 - 2ab = 36 - 8 = 28$$

### Solution 10.3

Let $u = \sqrt[4]{x} \geq 0$. Then $\sqrt{x} = u^2$.

$$u^2 + u - 2 = 0 \implies (u-1)(u+2) = 0 \implies u = 1 \text{ (since } u \geq 0\text{)}$$

$$x = 1^4 = 1$$

Verify: $\sqrt{1} + \sqrt[4]{1} = 1 + 1 = 2$. ✅ **$x = 1$.**

### Solution 10.4

Discriminant $= 0$:

$$(k-2)^2 - 4 \cdot 1 \cdot (k+1) = 0$$
$$k^2 - 4k + 4 - 4k - 4 = 0$$
$$k^2 - 8k = 0$$
$$k(k - 8) = 0$$

**$k = 0$ or $k = 8$.**

### Solution 10.5

$$f(x) = \frac{(x-2)(x+2)}{x-2} = x + 2 \quad \text{for } x \neq 2$$

$$\lim_{x \to 2} f(x) = 2 + 2 = 4$$

### Solution 10.6

Two-digit multiples of 7: 14, 21, 28, ..., 98.

This is an arithmetic sequence with $a_1 = 14$, $d = 7$, $a_n = 98$.

$n = \frac{98 - 14}{7} + 1 = 13$.

$$S_{13} = \frac{13}{2}(14 + 98) = \frac{13 \cdot 112}{2} = 13 \cdot 56 = 728$$

### Solution 10.7

Let $u = 2^x > 0$:

$$u^2 - 5u + 4 = 0 \implies (u-1)(u-4) = 0 \implies u = 1 \text{ or } u = 4$$

$$x = 0 \text{ or } x = 2$$

### Solution 10.8

$$\frac{\frac{a+b}{ab}}{\frac{b^2 - a^2}{a^2 b^2}} = \frac{a+b}{ab} \cdot \frac{a^2 b^2}{(b-a)(b+a)} = \frac{a^2 b^2}{ab(b-a)} = \frac{ab}{b-a}$$

### Solution 10.9

Let $t = x + 1 > 0$ (since $x > -1$). Then $x = t - 1$.

$$f = \frac{(t-1)^2 + 2(t-1) + 5}{t} = \frac{t^2 - 2t + 1 + 2t - 2 + 5}{t} = \frac{t^2 + 4}{t} = t + \frac{4}{t}$$

By AM-GM: $t + \frac{4}{t} \geq 2\sqrt{t \cdot \frac{4}{t}} = 2 \cdot 2 = 4$.

Equality when $t = \frac{4}{t} \implies t = 2 \implies x = 1$.

**Minimum value is 4, achieved at $x = 1$.**

### Solution 10.10

Total distance = initial drop + sum of up-and-down bounces.

$$D = 10 + 2\left(10 \cdot \frac{3}{4} + 10 \cdot \left(\frac{3}{4}\right)^2 + \cdots\right)$$

$$= 10 + 2 \cdot 10 \cdot \frac{3}{4} \cdot \frac{1}{1 - \frac{3}{4}} = 10 + 20 \cdot \frac{3}{4} \cdot 4 = 10 + 60 = 70 \text{ meters}$$

### Solution 10.11

$$\begin{cases} 2^x \cdot 3^y = 18 = 2 \cdot 3^2 \\ 2^y \cdot 3^x = 12 = 2^2 \cdot 3 \end{cases}$$

From the prime factorizations: $x = 1, y = 2$ satisfies both. Let's verify:

$2^1 \cdot 3^2 = 2 \cdot 9 = 18$. ✅
$2^2 \cdot 3^1 = 4 \cdot 3 = 12$. ✅

To prove uniqueness, take logarithms or divide:

Divide eq.1 by eq.2: $\frac{2^x \cdot 3^y}{2^y \cdot 3^x} = \frac{18}{12} = \frac{3}{2}$

$$2^{x-y} \cdot 3^{y-x} = \frac{3}{2} \implies \left(\frac{2}{3}\right)^{x-y} = \frac{3}{2} = \left(\frac{2}{3}\right)^{-1}$$

So $x - y = -1$, i.e., $y = x + 1$.

Substitute into eq.1: $2^x \cdot 3^{x+1} = 18 \implies 6^x \cdot 3 = 18 \implies 6^x = 6 \implies x = 1$.

Then $y = 2$.

**$x = 1, y = 2$.**

### Solution 10.12

Original roots: $\alpha + \beta = \frac{7}{2}$, $\alpha \beta = \frac{3}{2}$.

New roots: $\frac{1}{\alpha}$ and $\frac{1}{\beta}$.

Sum: $\frac{1}{\alpha} + \frac{1}{\beta} = \frac{\alpha + \beta}{\alpha \beta} = \frac{7/2}{3/2} = \frac{7}{3}$.

Product: $\frac{1}{\alpha \beta} = \frac{1}{3/2} = \frac{2}{3}$.

Equation: $x^2 - \frac{7}{3}x + \frac{2}{3} = 0$, or $3x^2 - 7x + 2 = 0$.

### Solution 10.13

Let $n^2 - 19n + 99 = k^2$ for some non-negative integer $k$.

$$n^2 - 19n + 99 - k^2 = 0$$

Treat as quadratic in $n$: discriminant must be a perfect square.

$$\Delta = 361 - 4(99 - k^2) = 361 - 396 + 4k^2 = 4k^2 - 35$$

Need $4k^2 - 35 = m^2$ for some non-negative integer $m$.

$$(2k)^2 - m^2 = 35 \implies (2k - m)(2k + m) = 35$$

Factor pairs of 35: $(1, 35)$, $(5, 7)$, $(-35, -1)$, $(-7, -5)$.

**Case 1:** $2k - m = 1$, $2k + m = 35 \implies 4k = 36 \implies k = 9$, $m = 17$.

$n = \frac{19 \pm 17}{2} \implies n = 18$ or $n = 1$.

**Case 2:** $2k - m = 5$, $2k + m = 7 \implies 4k = 12 \implies k = 3$, $m = 1$.

$n = \frac{19 \pm 1}{2} \implies n = 10$ or $n = 9$.

**Case 3:** $2k - m = -35$, $2k + m = -1 \implies 4k = -36 \implies k = -9$. Since $k \geq 0$, skip.

**Case 4:** $2k - m = -7$, $2k + m = -5 \implies 4k = -12 \implies k = -3$. Skip.

**Integer values: $n \in \{1, 9, 10, 18\}$.**

### Solution 10.14

The statement claims: if $a$, $b$, $c$ are distinct real numbers, then $ax^2 + bx + c$ cannot have two equal roots.

For equal roots, the discriminant must be zero: $b^2 - 4ac = 0$, i.e., $b^2 = 4ac$.

We check whether distinct $a, b, c$ can satisfy this. Take $a = 1$, $b = 6$, $c = 9$: all distinct, and $b^2 = 36 = 4 \cdot 1 \cdot 9 = 36$. ✅

The polynomial $x^2 + 6x + 9 = (x+3)^2$ has a repeated root $x = -3$, and $a = 1, b = 6, c = 9$ are distinct.

**The statement is false.** Counterexample: $a = 1, b = 6, c = 9$.

### Solution 10.15

Let $u = x^2 \geq 0$:

$$u^2 - 13u + 36 \leq 0 \implies (u - 4)(u - 9) \leq 0 \implies 4 \leq u \leq 9$$

So $4 \leq x^2 \leq 9 \implies 2 \leq |x| \leq 3$.

**$x \in [-3, -2] \cup [2, 3]$.**
