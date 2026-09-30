# Assessment Strategy & Quiz Design

## Philosophy

Assessment serves three purposes in this course:

1. **Formative** — help students identify gaps before they become problems.
2. **Summative** — verify mastery of critical topics before the national exam.
3. **Calibration** — help the instructor pace the course and identify weak spots.

Quizzes are **low-stakes and frequent**. The goal is feedback, not ranking. Students should feel safe making mistakes on quizzes — that's how learning happens.

## Quiz Structure

### End-of-Day Quizzes (every class session)

| Property | Value |
|----------|-------|
| Duration | 5–10 minutes |
| Format | 2–4 questions on paper |
| Stakes | Low (not heavily graded, participation-focused) |
| Returned | Next session with brief discussion of common errors |
| Content | Same-day material + one spiral-back question from a previous week |

### Question Types

1. **Conceptual** — "Explain why..." / "What is the intuition behind..." / "True or False with justification"
2. **Calculation** — "Compute the gradient of..." / "Given this data, run one step of..."
3. **Multiple choice** — Fast to grade, forces careful reading. Always require justification to prevent guessing.
4. **Challenge (★)** — Optional, for advanced students. Does not count against others.

### Example Quiz (Week 3, Session 2 — Gradient Descent)

```
QUIZ: Gradient Descent (10 min)

1. [Conceptual] Explain in one sentence why gradient descent moves 
   in the direction of -∇L rather than +∇L.

2. [Calculation] Given L(w) = (w - 3)², compute one step of gradient 
   descent starting from w₀ = 0 with learning rate η = 0.5. 
   What is w₁?

3. [Multiple choice] Which of the following is TRUE about SGD 
   compared to batch gradient descent?
   (a) SGD always converges faster
   (b) SGD has lower variance in gradient estimates
   (c) SGD is cheaper per iteration  ← correct
   (d) SGD guarantees convergence to the global minimum
   Justify your answer in one sentence.

4. ★ [Challenge] For L(w) = w⁴ - 2w² + 1, find all critical points 
   and determine which are minima, maxima, and saddle points. 
   If η = 0.1 and w₀ = 0.1, will GD converge? To which point?
```

### Quiz Grading

- **0–3 scale per question** (not points-based):
  - 0 = no answer or completely wrong
  - 1 = partially correct, major gap
  - 2 = mostly correct, minor error
  - 3 = correct and well-explained
- Challenge questions: scored separately, reported as bonus.
- **No averages or letter grades on individual quizzes.** Instead, track a simple rubric per topic:

| Topic | Student's Level |
|-------|----------------|
| Linear regression | ✓ Solid |
| Gradient descent | ⚠ Partial — review step size intuition |
| Logistic regression | ✓ Solid |
| ... | ... |

This is recorded per student in a spreadsheet, updated weekly.

## Weekly Assessment Cycle

```
Monday (or first session of week):
  → Hand out weekly handout
  → Teach new material
  → End-of-day quiz

Tuesday/Wednesday (second session):
  → Continue material
  → End-of-day quiz (includes spiral-back from Monday)

Thursday/Friday (third session, Phase 2+):
  → Continue material
  → End-of-day quiz

Friday (fourth session, Phase 2+):
  → Problem-solving session
  → End-of-day quiz (includes one question from each topic that week)
  → Preview next week's topic
```

## Spiral-Back Design

Every quiz includes at least one question from a **previous week's** topic. This implements spaced retrieval practice, which is evidence-based for long-term retention.

### Spiral-Back Schedule (example)

| Week | New Topic | Spiral-Back Question Topic |
|------|-----------|---------------------------|
| W4 | Probability/MLE | Linear regression (W2) |
| W5 | Information theory | Gradient descent (W3) |
| W6 | Logistic regression | MLE/MAP (W4) |
| W7 | Evaluation | Cross-entropy / KL (W5) |
| W8 | Consolidation | Everything (comprehensive) |
| W9 | Feature engineering | Logistic regression (W6) |
| W10 | k-NN | Bias-variance (W7) |
| W11 | Decision trees | Curse of dimensionality (W9) |
| W12 | SVM Part 1 | Entropy / information gain (W11) |
| W13 | SVM Part 2 | Margins / duality (W12) |
| W14 | Neural networks | Kernel trick (W13) |
| W15 | Backpropagation | Forward propagation (W14) |
| W16 | Training NNs | Backprop (W15) |
| W17 | Generalization | Optimizers (W16) |
| W18 | Clustering | Regularization (W16) |
| W19 | PCA | EM algorithm (W18) |
| W20 | Consolidation | Everything (comprehensive) |

## Mock Exams

### Mock Exam 1 (Week 23)

- **Length:** 80 minutes
- **Format:** 4–6 multi-part problems
- **Coverage:** All Phase 1 + Phase 2 topics
- **Purpose:** Diagnostic — identify weak topics

**Sample Mock Exam Structure:**

```
MOCK EXAM 1 (80 min)

Problem 1: Linear Regression & MLE (15 min)
  (a) Derive the normal equation for OLS. [5 min]
  (b) Show that OLS = MLE under Gaussian noise. [5 min]
  (c) Explain why ridge regression helps and derive the solution. [5 min]

Problem 2: Gradient Descent & Logistic Regression (15 min)
  (a) Derive the gradient of binary cross-entropy loss. [7 min]
  (b) Explain why we don't use MSE for classification. [3 min]
  (c) Write the SGD update rule for logistic regression. [5 min]

Problem 3: Neural Networks & Backpropagation (20 min)
  (a) Compute the forward pass for this 2-layer network. [5 min]
  (b) Derive the backpropagation gradients. [10 min]
  (c) How would dropout affect training? [5 min]

Problem 4: SVM & Kernels (10 min)
  (a) Write the soft-margin SVM optimization. [4 min]
  (b) What is the kernel trick? Give an example. [3 min]
  (c) Compare hinge loss and cross-entropy. [3 min]

Problem 5: Evaluation & Generalization (10 min)
  (a) Explain bias-variance tradeoff with a diagram. [5 min]
  (b) When is F1 better than accuracy? Give an example. [3 min]
  (c) What is k-fold cross-validation? [2 min]

Problem 6: Unsupervised Learning (10 min)
  (a) Write the k-means objective and algorithm. [4 min]
  (b) Derive the E-step for GMM. [3 min]
  (c) What is PCA optimizing? [3 min]
```

### Mock Exam 2 (Week 24)

- Same structure, different problems.
- **Purpose:** Measure improvement and build confidence.

### IOAI Mock Exams (Weeks 41–43)

- Based on past IOAI problem formats.
- May include both theory and practical reasoning (without coding).
- Longer multi-part problems requiring synthesis across topics.

## Grading Philosophy

### For the Course

The course grade (if applicable) should be based on:

| Component | Weight |
|-----------|--------|
| Quiz participation (not score) | 15% |
| Weekly handout engagement (reading + marked questions) | 10% |
| Mock exams | 30% |
| Paper reading summaries (1 per month, using the template) | 15% |
| Final comprehensive exam | 30% |

### Emphasis on Participation Over Performance

- Quizzes are about feedback, not ranking. Participating matters more than scoring perfectly.
- Students who consistently attempt challenge questions should be recognized, even if not always correct.
- Paper reading summaries should be graded on engagement, not correctness.

## Tracking Student Progress

### Per-Student Topic Mastery Tracker

Maintain a spreadsheet with:

| Student | W1: ML Setup | W2: Lin Reg | W3: GD | W4: MLE/MAP | W5: Info Theory | W6: Log Reg | W7: Eval | W8: Consolidation | ... |
|---------|-------------|-------------|--------|-------------|-----------------|-------------|----------|-------------------|-----|
| Alice | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ⚠ | ✓ | |
| Bob | ✓ | ⚠ | ⚠ | ⚠ | ✓ | ⚠ | ⚠ | ⚠ | |
| Carol | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | |

Levels: ✓ Solid | ⚠ Partial — needs review | ✗ Gap — intervention needed

### Intervention Strategy

- **⚠ on 1–2 topics:** Provide targeted practice problems from the handout.
- **⚠ on 3+ topics:** Schedule a 15-min one-on-one review.
- **✗ on any topic:** Immediate intervention — re-teach core concept in office hours or break-out session.
- **Strong students (all ✓):** Give them the challenge problems and encourage them to help peers (teaching reinforces learning).

## Quiz Archive

Keep all quizzes in a shared folder organized by week:

```
quizzes/
  W01_S1_quiz.pdf
  W01_S2_quiz.pdf
  W02_S1_quiz.pdf
  ...
  W23_mock_exam_1.pdf
  W24_mock_exam_2.pdf
  W41_mock_ioai_1.pdf
  ...
```

Also maintain an answer key for each, with common-mistake annotations.

## Common Mistakes to Watch For

### By Topic

| Topic | Common Mistake | How to Address |
|-------|---------------|----------------|
| Linear regression | Forgetting to add bias term | Always include b explicitly in derivations |
| Gradient descent | Confusing ∇L with ∇L evaluated at a point | Emphasize: gradient is a function, we evaluate it at current w |
| Logistic regression | Forgetting the sigmoid derivative cancellation | Show the full derivation; the cancellation is beautiful and memorable |
| Backpropagation | Transposing matrices incorrectly | Use consistent notation; draw computational graphs |
| SVM | Confusing primal and dual | Always state which formulation you're working in |
| PCA | Using rows instead of columns for data matrix | Fix a convention early and stick to it |
| EM | Confusing E-step (responsibilities) and M-step (parameters) | Use the GMM example consistently |
| Attention | Forgetting the √d_k scaling | Derive why it's needed (dot products grow with dimension) |
| RLHF | Confusing reward model training with policy optimization | Emphasize: reward model is supervised; policy optimization is RL |
