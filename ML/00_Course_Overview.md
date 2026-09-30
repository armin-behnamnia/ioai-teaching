# ML Course Overview & Philosophy

## Course Identity

- **Target audience:** High school students preparing for IOAI (International Olympiad in AI) and national qualification exams.
- **Duration:** 10–12 months.
  - Weeks 1–6: 2× 80-min sessions/week.
  - Week 7 onward: 4× 70-min sessions/week (schedule change after the mid-course break; gives ~75% more weekly contact time, used for review, completing pending derivations, and problem-solving sessions).
- **National qualification exam:** Approximately mid-course (around month 5–6). Critical topics must be covered before this point.

## Parallel Courses (students take these concurrently)

| Course | Relevance to ML |
|--------|-----------------|
| Combinatorics, Probability & Statistics | Foundational for Bayesian thinking, distributions, loss functions, evaluation metrics |
| Linear Algebra | Core to vectors, matrices, projections, eigendecomposition, PCA, neural network parameters |
| Python & ML Programming | Students handle coding elsewhere; this course is math/theory/intuition only |
| Basic Math & Calculus | Derivatives, chain rule, optimization, Taylor expansion intuition |

## Teaching Philosophy

1. **No assumptions about prior ML knowledge.** Start every topic from first principles. Even if some students know RLHF, we teach gradient descent from scratch.
2. **Math-first, code-free.** All concepts taught through mathematics, algorithms (pseudocode), visual demos, and intuition. No Python coding in this course.
3. **Deep intuition over memorization.** Every formula is motivated by a problem, a geometric picture, or an information-theoretic argument.
4. **Front-load critical topics.** The most important and frequently-tested topics must appear before the national qualification exam.
5. **Differentiated depth, not differentiated topics.** All students learn the same core topics. Sharp students go deeper via optional advanced sections, challenge problems, and paper reading.
6. **Life-long value.** Even students who don't qualify for IOAI should leave with a rigorous, useful ML foundation.

## Weekly Deliverables

| Deliverable | Purpose | Distribution |
|-------------|---------|--------------|
| **Weekly handout** | Structured notes covering the week's theory, derivations, and worked examples. Includes core section + advanced section. | Before each week |
| **Suggested paper(s)** | Progressive reading list. Early papers are accessible (blog-style or survey-level); later papers are full research papers. | Each week |
| **End-of-day quiz** | Short (5–10 min) check for understanding. 2–4 questions, mix of conceptual and calculation. | Each class day |

## Differentiation Strategy for Heterogeneous Class

- **Core content** is mandatory for all.
- **Advanced sections** in handouts (marked with ★) extend core topics — expected of strong students, bonus for others.
- **Challenge problems** on quizzes (marked, low stakes) let sharp students demonstrate deeper understanding.
- **Paper reading** scales naturally: the suggested paper each week has a "minimal reading" guide (abstract + intro + figures) and a "full reading" path for advanced students.
- **Peer explanation** opportunities: invite strong students to present derivations or paper summaries occasionally.

## Exam Readiness Timeline

```
Weeks 1–6  | Foundations: ML setup, linear models, optimization basics (2 sessions/wk,
           |   80 min each; Weeks 5–6 partially covered — completions carried into Week 7)
Break      | Two-week break
Week 7–8   | Foundations consolidated (4 sessions/wk, 70 min each): Week 7 = review of
           |   Weeks 1–6 + completion of pending W5–W6 derivations + logistic regression I;
           |   Week 8 = logistic regression II (training + softmax), matrix regression, Phase 1 consolidation
Weeks 9–20 | Core ML: classification, neural networks, training, generalization
Weeks 21–24| Exam-critical review + practice exams + commonly tested topics
Weeks 24–25| >>> NATIONAL QUALIFICATION EXAM <<<
Weeks 25–36| Advanced topics: deep learning architectures, generative models,
           |   reinforcement learning, representation learning, IOAI prep
Weeks 37–44| IOAI preparation: past problems, mock exams, competition strategy
```

## What "Proficiency" Means at Course End

A student who completes this course should be able to:

1. Formulate a real-world problem as a learning problem (choose hypothesis space, loss function, data assumptions).
2. Derive and explain gradient descent, backpropagation, and the key training algorithms from scratch.
3. Understand and explain the math behind: linear/logistic regression, neural networks, CNNs, RNNs/Transformers, decision trees, SVMs, clustering, PCA, and basic RL.
4. Read a modern ML research paper and identify the key contribution, method, and limitations.
5. Reason about bias-varariance, overfitting/underfitting, regularization, and generalization.
6. Understand evaluation metrics and experimental methodology well enough to critique an experiment.
7. Discuss the societal impact and ethical considerations of ML systems.

## File Structure of This Course Plan

```
00_Course_Overview.md          ← you are here
01_Syllabus.md                 ← week-by-week topic breakdown
02_Paper_Reading_Roadmap.md    ← progressive paper list with reading guides
03_Assessment_Strategy.md      ← quiz design, grading philosophy, exam prep
04_Topic_Dependencies.md       ← dependency graph and ordering rationale
05_Resource_List.md            ← textbooks, references, visualization tools
INDEX.md                       ← master index
```
