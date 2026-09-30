# Week 1 — Instructional Teaching Notes

> **Purpose:** These notes are for the instructor. They contain timing, pedagogical advice, common student misconceptions, board work guidance, and discussion prompts. They are NOT shown to students.

---

## Session 1 (80 min): What is Machine Learning? The Problem Setup

### Learning Objectives

By the end of this session, students should be able to:
1. Define machine learning using Mitchell's formulation (task, experience, performance).
2. Distinguish supervised, unsupervised, and reinforcement learning.
3. Identify the components of a supervised learning problem: input space, output space, hypothesis space, loss function.
4. Explain what "learning" means mathematically: finding parameters that minimize empirical risk.

### Materials Needed

- Whiteboard / blackboard with multiple sections (or a document camera)
- Desmos open in browser (for the line-fitting demo — see `visual_demos.md`)
- Printed or projected handout Section 1–2

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:10 | **Hook: "Can a computer learn to recognize a cat?"** | See Hook section below. |
| 0:10–0:25 | **What is learning? Mitchell's definition.** | Interactive: ask students for examples of learning. Map to T, E, P. |
| 0:25–0:40 | **Why not just write rules? Three failure cases.** | Use the spam filter example. Ask: "How would YOU write rules for cat vs. dog?" |
| 0:40–0:55 | **The mathematical setup: notation, spaces, loss.** | This is the heaviest math section. Go slow. Write every symbol on the board. |
| 0:55–0:65 | **Three types of learning (overview, not deep).** | Keep this fast — it's a map, not a deep dive. We'll spend weeks on each. |
| 0:65–0:75 | **The supervised learning pipeline (walkthrough).** | Use the house price example. Draw the pipeline diagram. |
| 0:75–0:80 | **Wrap-up + preview of Session 2.** | "Next time: we'll fit a line to data and see overfitting in action." |

### Hook: "Can a Computer Learn to Recognize a Cat?" (10 min)

**Goal:** Get students thinking about what "learning" means before any math.

**Instructions:**

1. Show two photos: a cat and a dog (or project them).
2. Ask: "How do YOU know this is a cat? What rules are you using?" Let students call out answers. They'll say things like "pointy ears," "whiskers," "small nose," etc.
3. Then show a cat that violates their rules (e.g., a hairless cat, a cat with floppy ears, a big cat like a lion). Their rules break.
4. **The point:** Even humans can't perfectly articulate the rules. We learned from examples. If we can't write the rules, we can't program them. But we CAN show the computer many examples and let it find the patterns.
5. Transition: "This is machine learning. Let's make it precise."

**Common student responses to watch for:**
- "Just use a neural network." → Acknowledge, but say "we'll get there. First, what problem are we solving?"
- "AI is the same as ML." → Briefly distinguish: AI is the broad goal, ML is a method to achieve it. (Don't spend more than 1 minute on this.)

### Board Work: The Mathematical Setup (15 min)

**This is the most important part of Session 1.** Students must leave with the notation clear.

**Draw on the board (keep it visible for the rest of the session):**

```
Input:    x ∈ X        (feature vector, e.g., [area, bedrooms, bathrooms])
Output:   y ∈ Y        (target, e.g., price)
Data:     D = {(x₁,y₁), ..., (xₙ,yₙ)}
Model:    f_θ(x)       (parameterized function)
Loss:     L(ŷ, y)      (how wrong is ŷ compared to y?)
Goal:     min_θ (1/n) Σ L(f_θ(xᵢ), yᵢ)
```

**Key teaching moves:**
1. Write each symbol and say what it is in words AND math. "This is x — it's a vector in R^d. Think of it as a column of numbers."
2. Use the house price example throughout. Every abstract symbol gets a concrete instance.
3. After writing the goal, circle it and say: "This is the entire machine learning problem in one line. Everything we do this course is about this equation."
4. Emphasize: "We minimize the AVERAGE loss. Not the loss on one example."

**Common misconceptions to address proactively:**
- **"The loss function is always MSE."** → No. We'll see many. MSE is for regression. Classification uses different losses.
- **"The hypothesis space is the dataset."** → No. The hypothesis space is the set of ALL possible models we could choose from. The dataset is what we use to choose.
- **"More parameters = better."** → No. More parameters = more flexibility = overfitting risk. We'll see this today.

### Discussion Prompts

Use these at the indicated times to keep students engaged:

1. **(After Mitchell's definition):** "Give me an example of something that IS learning and something that is NOT learning, using Mitchell's T, E, P framework." — This tests whether they can apply the definition, not just recite it.

2. **(After the three types):** "Is ChatGPT supervised, unsupervised, or reinforcement learning?" — **Answer: all three.** Pretraining is self-supervised (a variant of supervised). SFT is supervised. RLHF is reinforcement learning. This is a great teaser for the end of the course. Don't explain in detail — just say "we'll understand this by the end of the course."

3. **(After the pipeline):** "Where in this pipeline do you think the hardest part is?" — Most students will say "optimization" (finding the best parameters). The real answer is often "choosing the hypothesis space" and "collecting good data." This is a good seed for later discussions.

### Things NOT to Cover (Save for Later)

| Topic | When |
|-------|------|
| Specific loss functions (cross-entropy, hinge) | Week 7, Week 13–14 |
| How to solve the optimization | Week 2, Week 6 |
| Bias-variance decomposition (mathematical) | Week 5 |
| Training/test split details | Week 4 |
| Any specific algorithm | Week 2+ |

**Resist the urge to jump ahead.** The goal of Session 1 is the *framework*, not any specific model.

---

## Session 2 (80 min): The Supervised Learning Pipeline & Generalization

### Learning Objectives

By the end of this session, students should be able to:
1. Walk through the full supervised learning pipeline on a concrete example.
2. Define overfitting and underfitting with visual intuition.
3. Explain the concept of generalization and why training performance ≠ test performance.
4. Describe the overfitting-underfitting tradeoff qualitatively.
5. Preview the three perspectives (geometry, probability, optimization).

### Materials Needed

- Desmos with polynomial regression demo pre-loaded
- TensorFlow Playground open (optional — to show neural network overfitting visually)
- Printed or projected handout Sections 4–6

### Timing

| Time | Activity | Notes |
|------|----------|-------|
| 0:00–0:05 | **Recap of Session 1.** Quick: "What are the three components of an ML problem?" |
| 0:05–0:20 | **The pipeline walkthrough (house prices).** Step by step. |
| 0:20–0:35 | **Visual demo: fitting lines and curves to data.** Use Desmos. This is the centerpiece. |
| 0:35–0:50 | **Overfitting vs. underfitting.** Build on the visual demo. Define both. |
| 0:50–0:60 | **Generalization: training vs. true risk.** The fundamental challenge. |
| 0:60–0:70 | **The overfitting-underfitting tradeoff (qualitative).** No math yet — just intuition. |
| 0:70–0:75 | **The triality: geometry, probability, optimization.** Plant the seed. |
| 0:75–0:80 | **Quiz (end-of-day).** 10 min. See `quiz_S1.md` and `quiz_S2.md`. |

> **Note:** The quiz takes the last 5–10 minutes. Adjust the above timing — you may need to trim the triality section if running late. The triality is a "preview" and can be brief.

### Visual Demo: Fitting Lines and Curves (15 min)

**This is the most engaging part of Week 1.** Use it to make overfitting visceral.

**Setup in Desmos:**

1. Create a scatter plot of ~8 data points that roughly follow a linear trend with some noise. For example:
   - Points: (1, 2.1), (2, 3.9), (3, 5.8), (4, 8.2), (5, 10.1), (6, 11.7), (7, 14.3), (8, 15.8)
   - These follow $y \approx 2x$ with some noise.

2. **First fit: a constant** $f(x) = c$. Adjust $c$ to minimize the visual error. → This is **underfitting**. The model can't capture the trend.

3. **Second fit: a line** $f(x) = wx + b$. Adjust $w$ and $b$ to fit well. → This is a **good fit**. The model captures the trend without chasing noise.

4. **Third fit: a degree-7 polynomial.** $\sum_{k=0}^{7} a_k x^k$. This has 8 parameters for 8 data points. It can pass through EVERY point exactly. → This is **overfitting**. The training loss is 0, but the curve oscillates wildly between points. It would make terrible predictions for new data.

**Key teaching moves during the demo:**
- After fitting the constant: "What's wrong here?" → Students should say "the model is too simple."
- After fitting the line: "Is this perfect?" → "No, but it captures the pattern. The errors are small and random."
- After fitting the degree-7 polynomial: "What's the training error?" → "Zero!" "Would you trust this to predict $y$ at $x = 4.5$?" → Show that the polynomial gives a wild prediction between two points.
- **The punchline:** "Zero training error does NOT mean a good model. This is the most important lesson of Week 1."

**Alternative/extension:** Show TensorFlow Playground (playground.tensorflow.org) with a 2D classification problem:
- Set up a spiral dataset.
- Try a linear model (no hidden layers) → underfits.
- Try a small network → fits well.
- Try a huge network with no regularization → overfits (the decision boundary becomes too complex).
- This gives a visual feel for overfitting in classification, not just regression.

### Board Work: Overfitting vs. Underfitting (10 min)

**Draw this table on the board and fill it in WITH students (ask them to fill in each cell):**

```
                     Underfitting        Good Fit         Overfitting
                     ───────────         ────────         ───────────
Training error      HIGH                MEDIUM           LOW (≈0)
Test error          HIGH                MEDIUM           HIGH
Model complexity    TOO LOW             JUST RIGHT       TOO HIGH
Stability           HIGH (stable)       GOOD             LOW (unstable)
                    (but wrong)                          (fits noise)
Analogy             Studied nothing     Studied well     Memorized answers
```

> **Note on "bias" and "variance":** The formal terms are "bias" (how far off the model is on average) and "variance" (how much the model changes with different training data). We'll define these mathematically in Week 5 after learning probability. For now, use "stable/unstable" and "consistently wrong/fits noise" — the intuition is the same.

**The memorization analogy is powerful:** 
- Underfitting = student who didn't study at all. Fails both the practice test and the real test.
- Good fit = student who understood the concepts. Does well on both.
- Overfitting = student who memorized the practice test answers word-for-word. Perfect on practice test, fails the real test because the questions are different.

Use this analogy. Students remember it.

### The Triality (5 min — Brief Preview)

**Don't spend more than 5 minutes here.** The goal is to plant a seed, not to teach it fully.

**Say:**

"Every ML problem can be viewed from three angles:
1. **Geometry:** We're fitting a surface to data points. (Point to the Desmos demo — that's geometry.)
2. **Probability:** The data came from some random process. If we understand the process, we can make better predictions. (We'll study this in Week 5.)
3. **Optimization:** We're minimizing a function. The shape of that function determines how hard it is to find the minimum. (We'll study this in Week 6.)

Throughout this course, we'll see the same problem from all three angles. By the end, you'll be able to switch between them fluently."

**Do NOT go into any mathematical detail.** Just name the three perspectives and connect them to what they've seen.

### Wrapping Up Session 2

End with:

"Today we've seen the *framework* of machine learning. We know what the problem is, what the components are, and the central challenge (generalization). Starting next week, we'll solve our first real problem: linear regression. We'll see all three perspectives — geometry, probability, and optimization — in action on one concrete model.

Before you leave: take the quiz. It's 5 minutes. Don't worry about getting everything right — it's for feedback, not grades."

### Anticipated Questions from Students

| Question | How to Answer |
|----------|--------------|
| "What's the difference between AI, ML, and deep learning?" | AI = broad field of making machines intelligent. ML = a subset that learns from data. Deep learning = a subset of ML using neural networks. Draw three nested circles. (30 seconds.) |
| "Is ChatGPT machine learning?" | Yes. It's a neural network trained on text data. We'll understand exactly how by Week 35. (Don't elaborate now.) |
| "How many parameters does ChatGPT have?" | GPT-4 has ~1 trillion parameters. But the number of parameters doesn't tell you everything — the architecture and training matter. (15 seconds.) |
| "Will AI take our jobs?" | Acknowledge it's a valid question. ML automates pattern recognition tasks. It creates and destroys jobs. Understanding ML gives you agency. (30 seconds. Don't get drawn into a long debate.) |
| "What programming language do we use?" | None in this course. This is a math and theory course. You're learning Python in the parallel course. Here, we focus on understanding. |
| "How is this relevant to the IOAI?" | The IOAI tests exactly this: deep understanding of ML theory and methods. You can't solve competition problems without understanding the fundamentals we're building now. |
| A sharp student asks about a specific advanced topic (e.g., "How does backprop work with batch norm?") | "Great question. We'll cover that in Week 16. Hold onto that question." Write it down. Acknowledge it. Don't derail the class. (Note: backprop is Week 16, batch norm is Week 17.) |

### Differentiation Notes

**For struggling students:**
- The notation in Section 2 is the biggest barrier. After class, offer to go over the symbols one more time. Give them a "notation cheat sheet" (the table from the handout).
- Focus them on the *concepts* (overfitting, learning types) rather than the *formulas*. The formulas will come with practice.
- Reassure them: "If this feels overwhelming, that's normal. We'll see every concept again in concrete contexts. You don't need to understand everything today."

**For advanced students:**
- They may find Session 1 too easy. Redirect them to the ★ exercises (E7, E8) in the handout.
- Mention: "If you already know gradient descent or neural networks, great. But I want you to focus on the *why*, not the *what*. Can you derive everything from first principles? Can you explain why a particular loss function is chosen? That's what IOAI tests."
- In class, when asking questions, direct conceptual questions to struggling students and the probing follow-ups to advanced students. Example: "What is overfitting?" (anyone) → "Why does a degree-7 polynomial through 8 points generalize poorly?" (advanced).

---

## Challenge Questions for Advanced Students

> **How to use these:** Give these to sharp students *during* class when they finish an activity early, or as "think about this while I explain the basics to others" prompts. They are NOT extra homework — they are conversation starters. Follow up with these students individually or in a small group during breaks or after class. The goal is to keep them intellectually hungry without derailing the class pace.
>
> **Delivery:** Write the question on a sticky note, slip it to the student, or display it on a side board. Say: "While we review [topic], think about this. Let's discuss after class or during the break."
>
> **Principle:** Every challenge is tied to a Week 1 concept but pushes *deeper* — either toward a topic we'll cover later (creating anticipation) or toward a subtlety that most students won't notice (building analytical thinking).

---

### Session 1 Challenges

**Challenge 1-A: The 0-1 Loss Problem**
*(Give after introducing the loss function — around minute 50)*

> We defined the empirical risk as $R_{\text{emp}}(\theta) = \frac{1}{n}\sum_{i=1}^n L(f_\theta(\mathbf{x}_i), y_i)$. For classification, the most natural loss is the 0-1 loss: $L(\hat{y}, y) = \mathbb{1}[\hat{y} \neq y]$ (0 if correct, 1 if wrong).
>
> **Question:** Why might this "obvious" loss function be problematic when we try to *optimize* it? Think about what "optimizing" means — we need to adjust $\theta$ to reduce $R_{\text{emp}}$. What makes this hard for 0-1 loss compared to squared error?

**Instructor notes (don't share with student yet):**
- The 0-1 loss is non-differentiable (it's a step function). You can't compute a gradient, so gradient descent doesn't work directly.
- It's also non-convex for most models, so finding the global minimum is NP-hard in general.
- This is WHY we use surrogate losses like cross-entropy or hinge loss — they are differentiable approximations of the 0-1 loss. (Weeks 7, 13.)
- **Follow-up if the student figures it out:** "So if we can't optimize 0-1 loss directly, what could we use instead? What properties would a good replacement need?" → Leads to: differentiable, convex, an upper bound on 0-1 loss. This seeds logistic regression (Week 7) and SVMs (Week 13).

---

**Challenge 1-B: The No-Free Lunch Teaser**
*(Give after the hypothesis space discussion — around minute 55)*

> We said that choosing the hypothesis space $\mathcal{H}$ is a modeling assumption. Suppose $\mathcal{H}$ is the set of ALL possible functions from $\mathcal{X}$ to $\mathcal{Y}$ — no restrictions at all.
>
> **Question:** With this all-encompassing $\mathcal{H}$, can you always find a function with zero training error? Now here's the deeper question: if a function has zero training error, does that tell you ANYTHING about its performance on new data? Can you argue that, without ANY restriction on $\mathcal{H}$, learning is impossible?

**Instructor notes:**
- Yes, with unrestricted $\mathcal{H}$, you can always find a function that fits the training data perfectly (just memorize it).
- But with no restrictions, for any new input $\mathbf{x}_{\text{new}}$, the function could output anything. There's no reason the output should be correct.
- This is the intuition behind the No Free Lunch theorem (Week 9): without inductive bias (= restriction on $\mathcal{H}$), you cannot generalize.
- **Follow-up:** "So restricting $\mathcal{H}$ is not a limitation — it's necessary for learning. What kind of restriction would make sense for house prices?" → Linearity, smoothness, monotonicity in certain features, etc. This connects to inductive bias.

---

**Challenge 1-C: The Data Distribution Question**
*(Give after introducing empirical vs. true risk — around minute 55)*

> We defined true risk as $R(\theta) = \mathbb{E}_{(\mathbf{x}, y) \sim \mathcal{P}}[L(f_\theta(\mathbf{x}), y)]$, where $\mathcal{P}$ is the true data distribution. The empirical risk uses the training data as an approximation.
>
> **Question:** The law of large numbers says that the empirical average converges to the expected value as $n \to \infty$. So does this mean that with enough data, $R_{\text{emp}}(\theta) \approx R(\theta)$ for ALL $\theta$ simultaneously? Or just for a fixed $\theta$? Why does this distinction matter?

**Instructor notes:**
- LLN gives convergence for a *fixed* $\theta$. But in learning, we *choose* $\theta^* = \arg\min R_{\text{emp}}(\theta)$ — the $\theta$ depends on the data itself.
- For the convergence to hold uniformly over all $\theta \in \Theta$, we need additional conditions (finite hypothesis space, or bounded complexity measured by VC dimension, Rademacher complexity, etc.).
- This is the crux of generalization theory: we need uniform convergence, not just pointwise.
- **Follow-up:** "If $\mathcal{H}$ is infinite (like all linear functions in $\mathbb{R}^d$), does having more data guarantee generalization?" → Not necessarily without controlling the complexity of $\mathcal{H}$. This seeds Week 18 (generalization theory).

---

**Challenge 1-D: What If the Data Distribution Changes?**
*(Give during the three types of learning — around minute 60)*

> Everything we've set up assumes that the training data and the test data come from the same distribution $\mathcal{P}$. This is called the "i.i.d. assumption."
>
> **Question:** What happens if the distribution changes between training and testing? Can you think of a real-world scenario where this happens? Is there any way to detect or handle this?

**Instructor notes:**
- This is the problem of distribution shift / domain adaptation. Examples: training a medical model on data from Hospital A, deploying at Hospital B. Training a spam filter on 2023 emails, deploying in 2025 (spammers evolve).
- This is an active research area. Simple approaches: retrain periodically, use domain adaptation techniques, monitor for drift.
- **Follow-up:** "Does this break our entire framework?" → Not the framework, but it violates an assumption. Good ML practitioners check this assumption. Seeds discussion of robustness and fairness later in the course.

---

### Session 2 Challenges

**Challenge 2-A: The Irreducible Error**
*(Give during the overfitting-underfitting discussion — around minute 65)*

> In our overfitting demo, the "good fit" (linear model) still has nonzero training error. The data was generated by $y \approx 2x$ with noise, so even the true model doesn't fit perfectly.
>
> **Question:** Is there a floor to how low the test error can go, no matter how much data you have or how good your model is? What causes this floor? Can you express it mathematically?

**Instructor notes:**
- Yes — this is the irreducible error. It comes from the noise in the data-generating process.
- If $y = f^*(\mathbf{x}) + \epsilon$ where $\epsilon$ is zero-mean noise, then even with the true function $f^*$, there's error we can't remove — we can't predict the noise.
- No model can predict the random noise. This is a fundamental limit.
- **Follow-up:** "Can the irreducible error ever be zero?" → Only if the relationship is deterministic (no noise). In practice, almost all real data has noise. This connects to the probabilistic perspective (Week 4).

---

**Challenge 2-B: Double Descent Teaser**
*(Give after the overfitting/underfitting table — around minute 70)*

> We just drew the classic picture: as model complexity increases, training error goes down, but test error is U-shaped (decreases, then increases due to overfitting).
>
> **Question:** What if I told you that in deep learning, the test error sometimes goes down AGAIN if you make the model even MORE complex — past the point of overfitting? The U-shape becomes a W-shape (or "double descent"). Why might this happen? What does this imply about the overfitting-underfitting tradeoff?

**Instructor notes:**
- This is the double descent phenomenon (Belkin et al., 2019). It occurs in over-parameterized regimes where the model has so many parameters that there are many zero-training-error solutions, and the optimizer finds a "good" one (implicit regularization).
- The classical overfitting-underfitting tradeoff applies in the under-parameterized regime. In the over-parameterized regime, more parameters can actually help.
- This doesn't invalidate the tradeoff — it extends it. The U-curve is part of a larger picture.
- **Follow-up:** "Does this mean we should always use the biggest model possible?" → Not necessarily. The over-parameterized regime requires lots of data and careful optimization. And the double descent curve can have a region of very bad performance (the "interpolation threshold"). Seeds Week 18.

---

**Challenge 2-C: The Optimization-Generalization Puzzle**
*(Give during the triality discussion — around minute 72)*

> We said the goal is $\theta^* = \arg\min_\theta R_{\text{emp}}(\theta)$. The better we optimize, the lower the training loss.
>
> **Question:** If we find the ABSOLUTE global minimum of $R_{\text{emp}}$ — the best possible training loss — is that always the best model? Can you think of a scenario where a model that DOESN'T perfectly minimize training loss actually generalizes better?

**Instructor notes:**
- Yes! This happens all the time in deep learning. The global minimum of training loss often corresponds to overfitting (memorization).
- SGD doesn't find the global minimum — it finds a local minimum (or saddle point) that happens to generalize well. This is "implicit regularization" — the optimizer itself has a preference for simpler solutions.
- Early stopping (stopping before convergence) is an explicit version of this.
- **Follow-up:** "If the global minimum isn't always best, what should we optimize instead?" → This is an open research question! Some answers: minimize a regularized objective, use early stopping, use SGD (which implicitly regularizes). Seeds Weeks 16–17.

---

**Challenge 2-D: Designing a Loss Function**
*(Give during the pipeline walkthrough — around minute 18)*

> We've seen squared error $L(\hat{y}, y) = (\hat{y} - y)^2$ and 0-1 loss. Now think about this scenario:
>
> You're building a model to predict whether a patient has cancer (1) or not (0). If the model says "cancer" but the patient is healthy, that's a false alarm (costs extra tests, anxiety). If the model says "healthy" but the patient has cancer, that's a missed diagnosis (potentially fatal).
>
> **Question:** Design a loss function that captures this asymmetry. The two types of errors should have different costs. Write it mathematically. Then think: what happens to the decision boundary if you make one error much more costly than the other?

**Instructor notes:**
- A weighted 0-1 loss: $L(\hat{y}, y) = c_{FP} \cdot \mathbb{1}[\hat{y}=1, y=0] + c_{FN} \cdot \mathbb{1}[\hat{y}=0, y=1]$
  where $c_{FN} \gg c_{FP}$ (false negatives are much worse).
- With asymmetric costs, the optimal decision boundary shifts: the model predicts "cancer" more easily (lower threshold), accepting more false positives to avoid false negatives.
- This connects to: precision/recall tradeoff (Week 4), ROC curves (Week 4), and cost-sensitive learning.
- **Follow-up:** "Can you express this as a change in the threshold on a probabilistic prediction?" → Yes. If $P(y=1|\mathbf{x}) > t$, predict 1. Normally $t = 0.5$. With asymmetric costs, $t$ changes. If false negatives cost $c_{FN}$ and false positives cost $c_{FP}$, the optimal threshold is $t = \frac{c_{FP}}{c_{FP} + c_{FN}}$. (We'll derive this in Week 7.)

---

**Challenge 2-E: The Representation Question**
*(Give during the "what does a NN see" demo or at the end of Session 2 — around minute 73)*

> We talked about choosing features for the house price model: area, bedrooms, bathrooms. But what if the most important feature is "distance to the nearest school" — and we didn't include it?
>
> **Question:** In general, how do you know if you've chosen the RIGHT features? Is there a way to quantify the "information content" of a feature? And a deeper question: what if the important features are not directly measurable — like "how beautiful is the house" — can a model still use them?

**Instructor notes:**
- Feature selection is a major topic. Approaches: correlation analysis, mutual information (Week 5 — information theory), ablation studies (remove a feature and see if performance drops).
- Unmeasurable features: this is where representation learning (Week 34) comes in. Neural networks can learn features that humans can't name. A CNN "discovers" edges, textures, and object parts from raw pixels.
- **Follow-up:** "If a neural network learns its own features, does that mean feature engineering is obsolete?" → No. For tabular data (like house prices), feature engineering is still crucial. For images and text, learned features dominate. The choice depends on the data type. Seeds Weeks 9 and 34.

---

### Ongoing Challenges (Cross-Week)

These are longer-form questions that advanced students can think about throughout the week. Mention them at the end of Session 2 and discuss during office hours or the start of Week 2.

**Ongoing 1: The "True Model" Question**

> Throughout Week 1, we assumed there's a "true" relationship between $\mathbf{x}$ and $y$. But what if there isn't? What if $y$ is generated by a process that depends on variables we don't observe? Is the "true model" a meaningful concept? What does this mean for the idea of irreducible error?

**Instructor notes:** This leads to the concept of "aleatoric uncertainty" (noise in the data) vs. "epistemic uncertainty" (uncertainty due to limited knowledge). If unobserved variables exist, what looks like noise might actually be structure we're missing. This is a deep philosophical question that connects to causal inference and Bayesian ML.

---

**Ongoing 2: The "Learning to Learn" Question**

> We defined learning as improving performance with experience. But some humans are better at learning than others — they learn faster, generalize better, adapt to new tasks quickly. Could a machine "learn to learn"? What would that look like in our framework? Is meta-learning still just ERM, or is it something fundamentally different?

**Instructor notes:** This is meta-learning / learning-to-learn. In our framework, the "experience" is not just data from one task, but data from MULTIPLE tasks. The model learns a prior or a learning algorithm that works well across tasks. This is an active research area (MAML, few-shot learning). It connects to the IOAI spirit — the competition tests whether students can quickly adapt to new problem types.

---

**Ongoing 3: The "Meaning of Intelligence" Question**

> We've been talking about learning as optimization. But is intelligence just optimization? A chess engine optimizes its moves. ChatGPT optimizes next-token prediction. Are these systems "intelligent"? What would a machine need to do beyond optimization to be considered intelligent?

**Instructor notes:** This connects to François Chollet's "On the Measure of Intelligence" (the final paper in the course, Week 44). Chollet argues that intelligence is not skill at a specific task, but the ability to acquire new skills efficiently. This is a great question to revisit at the end of the course. For now, let students grapple with it — there's no right answer, but the discussion sharpens their thinking.

---

### Managing Advanced Students: Practical Tips

| Situation | Strategy |
|-----------|----------|
| Student finishes an activity 5 min early | Hand them a challenge question on a sticky note. Say: "Think about this while others finish. We'll discuss at the break." |
| Student answers everything correctly in class | Instead of moving on, ask a challenge follow-up: "You're right. Now, why?" or "What if we changed this assumption?" |
| Student seems bored / disengaged | Give them Ongoing Challenge 1 or 3 — these are open-ended philosophical questions that don't have a "right answer." Sharp students often find these more engaging than calculation problems. |
| Student asks an advanced question in class | Acknowledge it: "Excellent question. I'll put it on the 'parking lot' board and we'll address it in Week [N]." Then give them a challenge question that explores the same idea at a level they can handle now. |
| Multiple advanced students | Form a "study cluster." Give them the same challenge and ask them to discuss it together during the break. Come back and ask them to present their thinking to you (not the whole class — unless they want to). |
| Student already knows the answer to a challenge | Push deeper. If they solved the 0-1 loss challenge, ask: "Now, can you design a loss function that is both differentiable AND an upper bound on the 0-1 loss?" → This is the hinge loss (SVM) and cross-entropy (logistic regression). |
| Student is frustrated by a challenge | Remind them: "These questions are HARD. They're research-level questions that the ML community is still working on. The point is to think, not to solve. If you're confused, that means you're thinking deeply." |

---

## Post-Session Checklist

After each session, the instructor should:

- [ ] Review quiz results and note common mistakes
- [ ] Update the student progress tracker (see `03_Assessment_Strategy.md`)
- [ ] Prepare spiral-back questions for the next quiz
- [ ] Check if any student needs intervention (⚠ or ✗ on the tracker)
- [ ] Preview next session's material and adjust if needed

---

## Preparation Checklist for Week 1

### Before Session 1

- [ ] Read handout Sections 1–3
- [ ] Prepare the cat/dog photos for the hook
- [ ] Prepare board layout for the mathematical setup
- [ ] Open Desmos (not needed until Session 2, but good to have ready)
- [ ] Print quiz S1 (or have it ready to project)
- [ ] Print handout for students (or distribute digitally)

### Before Session 2

- [ ] Read handout Sections 4–6
- [ ] Set up Desmos with the data points and three models (constant, linear, degree-7 polynomial)
- [ ] Optionally set up TensorFlow Playground with spiral dataset
- [ ] Print quiz S2
- [ ] Review Session 1 quiz results — prepare to address common mistakes at the start of Session 2
