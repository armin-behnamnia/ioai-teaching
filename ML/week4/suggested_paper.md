# Week 4 — Suggested Paper

## "The Relationship Between Precision-Recall and ROC Curves"

**Authors:** Jesse Davis and Mark Goadrich  
**Year:** 2006  
**Venue:** Proceedings of the 23rd International Conference on Machine Learning (ICML), pp. 233–240  
**Type:** Research paper (theory + experiments)  
**Difficulty:** ★★★ (this is the students' first "real" research paper — the reading guide below is designed to help you navigate it)

---

## Where to Find It

- **Official:** https://dl.acm.org/doi/10.1145/1143844.1143874
- **Author's version:** Search "Davis Goadrich Relationship Between Precision-Recall and ROC Curves" on Google Scholar — a free PDF is usually available from the authors' websites or researchgate.net.
- **DOI:** 10.1145/1143844.1143874

---

## Why This Paper?

This is the students' **first real research paper**. It was chosen because:

1. **It's directly relevant to this week's material.** We just learned about ROC curves, PR curves, and when to use each. This paper is *the* definitive analysis of the relationship between them. Reading it deepens your understanding of the very metrics you're learning.

2. **It's short and focused.** 8 pages, one main theorem, clear experiments. No heavy machinery — just the definitions of precision, recall, TPR, and FPR that you already know.

3. **It has the standard research paper structure** (abstract → introduction → method → experiments → conclusion). Learning to navigate this structure is a skill you'll use throughout the course and at IOAI.

4. **It makes a surprising claim.** Most people assume ROC curves are always the right tool. Davis and Goadrich show that for imbalanced datasets, PR curves are more informative — and prove a mathematical relationship between the two. This is a great example of how research challenges conventional wisdom.

5. **It connects to real-world impact.** Imbalanced datasets are the norm in practice: fraud detection, disease screening, defect detection. Understanding which metric to trust matters for real decisions.

---

## How to Read a Research Paper (First-Timer's Guide)

> **Read this section before diving into the paper.** Research papers are NOT textbooks. They're written for other researchers, not students. Here's how to approach your first one.

### The Structure of a Research Paper

Most ML research papers follow this structure:

| Section | What It Does | How to Read It |
|---------|-------------|----------------|
| **Abstract** | Summary of the whole paper in 150–250 words. | Read FIRST. It tells you if the paper is relevant. Read it 2–3 times. |
| **Introduction** | Motivation: what problem, why it matters, what's new. | Read carefully. This is the most important section for understanding WHY. |
| **Method / Definitions** | The algorithm or theory being proposed. | Read carefully for the core idea. Skip details that confuse you on first read. |
| **Theory / Analysis** | Proofs, theorems, convergence arguments. | **SKIM on first read.** Read the theorem statements, skip the proofs. Come back later if needed. |
| **Experiments / Results** | Empirical evaluation on datasets. | Look at the TABLES and FIGURES. These tell the story. Read the discussion of results. |
| **Conclusion** | Summary and future directions. | Read it. Often contains the authors' honest assessment. |

### General Tips for Your First Paper

1. **Don't read linearly.** Read abstract → introduction → skim method → look at figures → read conclusion. Then go back to sections that interested you.

2. **Don't understand everything.** A research paper is dense. On first read, aim for 50–70% understanding. That's normal and sufficient.

3. **Write down questions.** Things you don't understand are MORE valuable than things you do. Bring your questions to class.

4. **Look up terms you don't know.** But don't go down rabbit holes. If a term appears once and isn't central, note it and move on.

5. **Focus on the WHY and the WHAT, not the HOW.** Why did Davis and Goadrich write this paper? What do they claim? The detailed proofs can wait.

6. **Pay attention to figures.** Figure 1 is the heart of this paper. Spend time understanding it. The figures often tell the story more clearly than the text.

---

## Reading Guide

### Reading Time

**30–45 minutes** for the minimal reading. The paper is 8 pages, but you'll read about 5–6 pages closely.

### Minimal Reading (for all students)

Read these sections in this order:

1. **Abstract** (2 min) — Read 2–3 times. What is the main claim? What do they prove about ROC and PR curves?

2. **Section 1: Introduction** (5 min) — Motivation. Why ROC curves are popular, why they can be misleading with imbalanced data, and what the paper contributes.

3. **Section 2: ROC Space and PR Space** (10 min) — This is the core. The definitions of TPR, FPR, precision, and recall. The key theorem (Theorem 1): a curve dominates in ROC space if and only if it dominates in PR space. Look at **Figure 1** carefully — it shows the same classifiers in ROC space (left) and PR space (right). This is the key figure of the paper.

4. **Section 4: Interpolation in PR Space** (5 min) — Why interpolating between points in PR space is different from ROC space. This is a technical detail but important for understanding the curves.

5. **Section 6: Conclusions** (3 min) — Summary. When to use PR vs ROC.

**Total:** ~25–30 minutes of focused reading.

### Full Reading (for advanced students)

In addition to the above, read:

6. **Section 3: Constructing ROC and PR Curves** (5 min) — How the curves are built from data. This connects to our handout Section 5.2 (ROC construction).

7. **Section 5: An Optimistic Estimate of AUC in PR Space** (5 min) — A subtlety about how the area under the PR curve is computed. This is a technical detail but shows how careful you need to be with metrics.

**Skim (don't read in detail):**
- The mathematical proofs within Section 2 — read the theorem statement and the intuition, but don't worry about following every step of the proof.

---

## Key Sections and Their Connections to Our Course

### Section 1: Introduction

Davis and Goadrich point out that ROC curves are widely used but can be misleading when one class is much rarer than the other. They argue that PR curves are more informative in these cases.

**Connection:** Our handout Section 5.6 discusses when to use ROC vs. PR curves. The handout says "ROC can look misleadingly good when negatives dominate." This paper is the source of that claim.

**Question for students:** "Davis and Goadrich say ROC curves can be 'misleadingly optimistic' for imbalanced data. Can you explain why? Think about what happens to the FPR when there are many true negatives." → The FPR denominator (FP + TN) is dominated by TN. Even a large number of false positives gives a small FPR. The ROC curve looks good even when the model is making many errors relative to the positive class.

### Section 2: ROC Space and PR Space

This is the heart of the paper. The key definitions:

| Metric | Formula | In ROC Space? | In PR Space? |
|--------|---------|---------------|--------------|
| TPR (Recall) | $TP / (TP + FN)$ | Yes (y-axis) | Yes (x-axis) |
| FPR | $FP / (FP + TN)$ | Yes (x-axis) | No |
| Precision | $TP / (TP + FP)$ | No | Yes (y-axis) |

**Theorem 1 (the main result):** A classifier dominates another in ROC space if and only if it also dominates in PR space (assuming the same dataset).

**Connection:** This means the two curves are *consistent* — if Model A is better than Model B in ROC, it's also better in PR. BUT (and this is the key "but") the *visual impression* can be very different. A curve that looks great in ROC space might look much less impressive in PR space when the data is imbalanced.

**Question for students:** "If the theorem says dominance is the same in both spaces, why does it matter which one we use? Isn't the answer the same?" → Yes, the *ranking* of models is the same. But the *magnitude* of the difference can be hugely misleading in ROC space. A model can look "close to perfect" in ROC space but have terrible precision in PR space. The PR curve reveals the true performance gap.

### Figure 1: The Key Figure

Figure 1 shows the same five classifiers plotted in both ROC space (left) and PR space (right). Look at this figure carefully.

**What to notice:**
- In ROC space (left), all curves look reasonably good — they're all above the diagonal, and the best one (curve 5) is close to the top-left corner.
- In PR space (right), the differences are much more dramatic. The curves are spread out, and the "best" curve looks much less perfect.
- This is because the dataset is imbalanced (1:20 ratio of positive to negative). The ROC space hides the poor precision; PR space reveals it.

**Question for students:** "Look at Figure 1. In ROC space, which classifier looks best? Now look at PR space — does the ranking change?" → The ranking is the same (Theorem 1 guarantees this). But in PR space, the differences are much more visible. The ROC plot makes all classifiers look decent; the PR plot shows that some are actually quite poor.

### Section 4: Interpolation in PR Space

In ROC space, you can linearly interpolate between two points (any threshold between two values gives a point on the line segment). In PR space, linear interpolation is *not* correct — the true curve is concave, not linear.

**Connection:** This is a technical point, but it matters for computing AUC. If you linearly interpolate in PR space, you overestimate the area under the curve. The correct interpolation uses a different formula.

**Question for students:** "Why can't you linearly interpolate in PR space? What's different about the precision-recall relationship compared to TPR-FPR?" → In ROC space, both TPR and FPR are monotonically increasing as the threshold decreases. In PR space, as recall increases (threshold decreases), precision can go up or down. The relationship is non-linear.

### Section 6: Conclusions

Davis and Goadrich summarize: when datasets are imbalanced, PR curves are more informative than ROC curves. They recommend always checking PR curves for imbalanced problems.

**Connection:** Our handout Section 5.6 gives the practical rule: balanced → ROC, imbalanced → PR. This paper is the justification for that rule.

**Question for students:** "The paper recommends PR curves for imbalanced data. But many ML libraries show ROC curves by default. Why do you think that is? Should you change the default?" → ROC curves are traditional (from signal detection theory, WWII). They're easier to interpret when classes are balanced. But for imbalanced data — which is most real-world classification — PR curves are better. Always check both.

---

## Paper Reading Template (for students)

```
PAPER READING NOTES
===================
Title: The Relationship Between Precision-Recall and ROC Curves
Authors: Jesse Davis and Mark Goadrich
Year: 2006
Venue: Proceedings of the 23rd International Conference on Machine Learning (ICML)

1. Problem: What problem does this paper address?
   → ROC curves are widely used for evaluating classifiers, but they 
     can be misleading when the positive class is rare. The paper 
     asks: when should we use PR curves instead, and what is the 
     mathematical relationship between the two?

2. Prior work: What was known before? What was the gap?
   → ROC curves were well-established (from signal detection theory).
     PR curves were known but less widely used. The relationship 
     between them was not formally analyzed. The gap: no one had 
     proved whether dominance in one space implies dominance in the 
     other, or explained why PR curves are more informative for 
     imbalanced data.

3. Key idea: State the main contribution in 1-2 sentences.
   → Theorem 1: A classifier dominates in ROC space if and only if 
     it dominates in PR space (for the same dataset). However, PR 
     curves are more informative than ROC curves for imbalanced 
     datasets because they expose poor precision that ROC curves 
     hide.

4. Method: How does it work?
   → The paper defines ROC space (TPR vs FPR) and PR space 
     (Precision vs Recall). It proves that a curve that dominates 
     in ROC space also dominates in PR space by showing that 
     precision is a function of TPR, FPR, and the class ratio. 
     The key insight: when the negative class is much larger, 
     small changes in FPR correspond to large changes in precision.

5. Results: What are the key empirical or theoretical results?
   → Theorem 1: Dominance equivalence between ROC and PR space.
   → Figure 1: Visual demonstration that ROC curves look 
     deceptively good for imbalanced data (1:20 ratio), while PR 
     curves reveal the true performance differences.
   → Section 4: Correct (non-linear) interpolation in PR space.
   → Section 5: Warning about optimistic AUC estimates in PR space.

6. Connections: How does this relate to what we learned in class?
   → Confusion matrix (handout Section 4.1): the foundation for 
     both ROC and PR curves.
   → ROC curve construction (handout Section 5.2): the procedure 
     Davis and Goadrich use.
   → When to use ROC vs PR (handout Section 5.6): this paper is 
     the source of the recommendation.
   → Precision, recall, F1 (handout Section 4.3): the metrics 
     that define PR space.
   → Class imbalance (handout Section 4.7): the scenario where 
     PR curves are essential.

7. Limitations: What are the weaknesses or assumptions?
   → The analysis is for binary classification only. Multi-class 
     extensions are more complex.
   → The theorem assumes the same dataset is used for both curves.
   → The paper doesn't address the threshold-selection problem 
     (which point on the curve to choose).
   → Written in 2006 — deep learning wasn't dominant. But the 
     analysis is metric-level and applies to any classifier, 
     including modern ones.

8. Questions: What did you not understand? What would you ask?
   (Student fills in)
```

---

## In-Class Discussion (5 min — at the start of Session 2)

> **This is the students' FIRST paper discussion.** Spend 5 minutes on it. The goal is to show that paper reading is part of the course and to reward those who read. Keep it light — celebrate the effort, don't penalize those who didn't read.

Use these prompts:

1. **"What was the main idea of Davis and Goadrich's paper in one sentence?"** → ROC curves and PR curves are mathematically related (dominance is equivalent), but PR curves are more informative for imbalanced datasets because they reveal poor precision that ROC curves hide. (This is the elevator pitch of the paper.)

2. **"Look at Figure 1. In the ROC plot (left), all the curves look pretty good. In the PR plot (right), they look much worse. Why? What's different about the two spaces?"** → The dataset has a 1:20 class imbalance. In ROC space, the FPR is small because there are many true negatives. In PR space, precision directly shows how many of the predicted positives are correct — and with a rare positive class, even a small false positive rate means terrible precision.

3. **"Theorem 1 says dominance is the same in both spaces. So why does it matter which one we use?"** → The ranking is the same, but the *visual impression* is different. ROC can make a bad model look good. PR reveals the truth. When you're deciding whether to deploy a model, you need the honest picture.

4. **"Have you seen ROC curves in practice? Where?"** → Open-ended. Students might mention medical testing, Kaggle competitions, or ML tutorials. The point: ROC is the default in most software, but you should always check PR curves for imbalanced data.

**Don't spend more than 5 minutes.** The goal is to celebrate the paper-reading effort and connect it to the session's material. The full discussion of ROC vs PR happens during the session itself.

---

## Advanced Follow-Up for Sharp Students

If a student reads the paper and wants more:

1. **Construct your own example.** Create a dataset with 100 positives and 10,000 negatives. Build two classifiers:
   - Model A: TP = 80, FP = 200, FN = 20, TN = 9800
   - Model B: TP = 90, FP = 500, FN = 10, TN = 9500
   
   Plot both in ROC space and PR space. Which looks better in ROC? In PR? Does the dominance relationship hold? (This is handout exercise E12.)

2. **Read Fawcett (2006), "An Introduction to ROC Analysis."** This is a tutorial paper on ROC curves that complements Davis & Goadrich. It covers ROC construction, AUC interpretation, and the relationship to cost curves. More accessible than Davis & Goadrich but less focused on the imbalance issue.

3. **Explore the multi-class extension.** Davis and Goadrich only analyze binary classification. How would you extend PR curves to multi-class? (Hint: compute precision/recall per class, then average — either macro-average or micro-average. What are the tradeoffs?) This connects to Week 14 (neural networks for multi-class classification).

4. **Investigate the interpolation issue.** Section 4 of the paper discusses why linear interpolation is wrong in PR space. Can you construct an example where linear interpolation gives a significantly different AUC than the correct (concave) interpolation? How much does this matter in practice?

5. **Connect to cost-sensitive learning.** The paper is about *which curve to look at*, but not about *which point on the curve to choose*. The point you choose corresponds to a threshold, which corresponds to a tradeoff between false positives and false negatives. If you know the costs of each type of error, you can choose the optimal point. This connects to Challenge 4-2D (the cost-sensitive threshold) and to Week 7 (logistic regression).
