# Week 7 — Suggested Paper

## "Machine Learning that Matters"

**Author:** Kiri Wagstaff
**Year:** 2012
**Type:** Conference paper (ICML) — essay-style
**Difficulty:** ★★

---

## Where to Find It

- **arXiv:** 1206.4656
- Also widely mirrored (search "Wagstaff Machine Learning that Matters PDF")

---

## Why This Paper?

1. **Students now have enough ML knowledge to engage critically.** They have two complete models (linear + logistic regression), the loss-function story (MLE), the evaluation toolkit (Week 4), and the bias-variance theorem. Wagstaff's arguments about evaluation and impact can now be *checked against their own knowledge*.
2. **It is essay-style, not math-heavy.** After a derivation-dense week (MAP=Ridge, bias-variance, MSE gradient, cross-entropy), a readable argumentative paper is the right pace.
3. **It directly challenges Week 4 assumptions.** Wagstaff asks whether the metrics we diligently learned (accuracy, AUC, statistical significance) actually measure progress that matters. This is exactly the "critique an experiment" skill the IOAI theory round tests.
4. **Timing after the break.** A two-week gap plus a consolidation week — a big-picture paper re-motivates the technical grind.

---

## Reading Guide

### Reading Time

**25–35 minutes.**

### Minimal Reading

1. **Section 1 (Introduction)** (5 min) — the challenge: ML publications vs. real-world impact. Her "moon shots" for ML.
2. **Section 2 (Impact)** (5 min) — six categories of impact; why citation counts and benchmark improvements are weak proxies.
3. **Section 3 (Relevance)** (10 min) — the critique of evaluation practices: statistical significance vs. practical significance, overfitting to benchmarks, the "constraints" real problems impose.
4. **Section 6 (Conclusion)** (3 min) — the call to action.

### Full Reading

Add Sections 4 (Scale — the data-centric argument) and 5 (Openness — reproducibility). Strong students should read these and connect to Week 4's reproducibility discussion (data leakage, golden rule).

---

## Key Connections to Our Course

### Section 3: Evaluation — our Week 4 under the microscope

Wagstaff criticizes benchmark-chasing: small metric gains that don't transfer. Connect to:
- **Overfitting to the validation set** (W4): if you evaluate 100 models on the same benchmark, the winner is partly lucky — the same logic as why we never touch the test set twice.
- **Statistical vs. practical significance**: an AUC improvement of 0.001 on a huge benchmark can be "significant" and useless simultaneously.

**Question to answer while reading:** "Which of Wagstaff's criticisms of evaluation could have been stated using only concepts from our Week 4?"

### Section 2: Impact — and our bias-variance theorem

"Publishable" and "useful" are different targets — a model can minimize training-set surprise (low bias on what it was built for) and still fail on the deployment distribution. A loose but memorable mapping: **overfitting to the benchmark = variance with respect to the problem selection process.**

### Section 5: Openness — the golden rule's bigger sibling

Reproducibility failures are often data leakage and protocol errors — exactly Week 4's material, at the scale of a whole research field.

### Session 4 connection: probabilities, not just labels

Logistic regression outputs *calibrated probabilities*, which is what real decision-making (medicine, policy — Wagstaff's impact domains) requires. A bare 0/1 prediction throws away the uncertainty; Week 4's metrics and thresholds are built on the probabilities we derived this week.

---

## Paper Reading Template

```
PAPER READING NOTES
===================
Title: Machine Learning that Matters
Author: Kiri Wagstaff
Year: 2012

1. Key idea: ML research optimizes for publishable benchmark gains,
   not measurable real-world impact. Evaluation practices (metrics,
   significance, benchmarks) systematically overstate progress.

2. Key concepts:
   - Impact categories (personal, social, ... )
   - Statistical significance ≠ practical significance
   - Benchmark overfitting; relevance under constraints
   - Openness / reproducibility as impact enablers

3. Connections to class:
   - Week 4: validation-set overfitting, golden rule, data leakage
   - Week 5/7: MLE — what the benchmark "likelihood" actually is
   - Week 7 S4: probability outputs vs. bare labels for real decisions
   - Bias-variance: benchmark overfitting as variance over problems

4. One criticism I have of the paper: (Student fills in)

5. One "moon shot" I would add for ML in 2026: (Student fills in)
```

---

## In-Class Discussion (5 min — start of Week 8 Session 2)

1. **"Name one Wagstaff criticism expressible purely in Week-4 vocabulary."** → e.g., repeated evaluation on the same test data = overfitting to the evaluator.
2. **"She wrote in 2012. What has changed?"** → LLMs deliver visible personal/social impact (her category list is now partly realized); but benchmark saturation, contamination ("data leakage" at civilization scale), and reproducibility disputes remain.
3. **"Why does a 0.1% accuracy gain on a 10-million-example benchmark mean less than it sounds?"** → practical vs. statistical significance; measurement noise; distribution shift.
4. **"Connect to this week: why are calibrated probabilities (Session 4) an 'impact' feature?"** → Real decisions need uncertainty, cost-sensitive thresholds (Challenge 7-4C), not just argmax labels.

---

## Advanced Follow-Up

1. **Read Section 4 (Scale)** and write 5 sentences: which of Wagstaff's data-centric concerns did the deep-learning era solve, and which got worse?
2. **Benchmark contamination:** find one public case of test-set contamination in an LLM benchmark (2023–2025). Describe it in Week-4 vocabulary (leakage, golden rule).
3. **Cost-sensitive evaluation:** re-derive the optimal threshold $t^* = c_{FP}/(c_{FP}+c_{FN})$ (Challenge 7-4C) and use it to critique a benchmark that reports only accuracy.
4. **Read "The Statue in the Stone"** (Ghookasian et al.) or a survey of benchmark-methodology critiques — connect three of their findings to Week 4 concepts.
