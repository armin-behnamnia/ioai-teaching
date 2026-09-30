# Paper Reading Roadmap — Progressive Difficulty

## Philosophy

Students don't know how to read papers. This roadmap progresses from accessible blog posts and survey-style articles to full research papers. Each entry includes:

- **Paper**: Title and authors
- **Difficulty**: ★ (easy) to ★★★★★ (advanced)
- **Week**: Aligned with syllabus
- **Minimal reading**: What all students should read (abstract + intro + figures + conclusion)
- **Full reading**: For advanced students (full method, experiments, appendix)
- **Reading guide**: What to focus on, what to skip, key questions to answer

## Difficulty Progression

```
Weeks 1-8:   ★ to ★★    (blog posts, surveys, highly accessible)
Weeks 9-20:  ★★ to ★★★  (seminal papers with reading guides)
Weeks 21-24: ★★★        (exam prep — no new papers, re-read key ones)
Weeks 25-36: ★★★ to ★★★★ (modern research papers)
Weeks 37-44: ★★★★ to ★★★★★ (IOAI-level papers, competition problems)
```

---

## Phase 1: Foundations (Weeks 1–8)

### Week 1 — No paper (course orientation)

### Week 2 — Scalar Linear Regression
**Paper:** "A Few Useful Things to Know about Machine Learning" — Pedro Domingos (2012)
- **Difficulty:** ★
- **Type:** Communications of the ACM article (essay-style, no heavy math)
- **Minimal reading:** Sections 1–6 (learn, evaluate, features, overfitting)
- **Full reading:** Entire article
- **Reading guide:** Focus on the 12 lessons. This gives students a mental framework for the whole course. Don't worry about references to algorithms they haven't learned yet — focus on the concepts.
- **Key questions:** What does Domingos mean by "overfitting comes in many forms"? What is the "curse of dimensionality"? What does he say about feature engineering?

### Week 3 — Overfitting & Regularization
**Paper:** "A Few Useful Things to Know about Machine Learning" — Pedro Domingos (2012), re-read Section 5
- **Difficulty:** ★
- **Type:** Re-read of Week 2 paper, focusing on overfitting
- **Minimal reading:** Section 5 ("Overfitting Has Many Faces") and Section 3 ("Data Alone Is Not Enough")
- **Full reading:** Re-read with regularization context
- **Reading guide:** Section 5 directly connects to this week's deep dive on overfitting. Domingos describes multiple forms of overfitting — students should connect each form to the polynomial and ridge regression material. Section 3 motivates why regularization (inductive bias) is necessary.
- **Key questions:** What are the "many faces" of overfitting? How does ridge regression address overfitting? What does "data alone is not enough" mean for regularization?

### Week 4 — Model Evaluation
**Paper:** "The Relationship Between Precision-Recall and ROC Curves" — Davis & Goadrich (2006)
- **Difficulty:** ★★
- **Type:** Conference paper (ICML) — but accessible
- **Minimal reading:** Abstract, introduction, Section 2 (definitions), Figure 1
- **Full reading:** Sections 2–4
- **Reading guide:** This is the students' first "real" research paper. Read abstract → introduction → definitions → look at figures → read conclusion. Don't worry about all the proofs in Section 3. Focus on understanding what ROC and PR curves are and when each is preferred.
- **Key questions:** When should you use a PR curve instead of ROC? What is AUC? What does it mean for a curve to dominate another?

### Week 5 — Probability for ML
**Paper:** "Visual Information Theory" — Christopher Olah (blog post, colah.github.io)
- **Difficulty:** ★★
- **Type:** Visual blog post
- **Minimal reading:** Entire post (it's designed to be accessible)
- **Full reading:** Work through all visual examples
- **Reading guide:** Olah's visualizations of entropy, joint distributions, and KL divergence are among the best ever made. Students should spend time with the diagrams. The key insight: entropy = expected surprise, KL divergence = extra surprise from wrong distribution. This also serves as a preview of information theory (Week 11).
- **Key questions:** What is self-information? Why is KL divergence non-negative? How does cross-entropy relate to entropy and KL?

### Week 6 — Gradient Descent
**Paper:** "An Overview of Gradient Descent Optimization Algorithms" — Sebastian Ruder (2016)
- **Difficulty:** ★★
- **Type:** Blog post / technical review
- **Minimal reading:** Sections on batch GD, SGD, mini-batch, and challenges
- **Full reading:** Entire post including momentum, Adam (preview of Week 17)
- **Reading guide:** Focus on the parts that connect to this week's material (batch GD, SGD, mini-batch). The advanced optimizers (momentum, Adam) are previews of Week 17.
- **Key questions:** Why is the gradient the direction of steepest ascent? What happens when the learning rate is too large? What is the difference between batch GD and SGD?

### Week 7 — Logistic Regression
**Paper:** "Machine Learning that Matters" — Kiri Wagstaff (2012)
- **Difficulty:** ★★
- **Type:** Conference paper (ICML) — essay-style
- **Minimal reading:** Sections 1–3
- **Full reading:** Entire paper
- **Reading guide:** Students now have enough ML knowledge (two complete models) to engage critically with Wagstaff's arguments about ML evaluation and impact.
- **Key questions:** What does Wagstaff mean by "machine learning that matters"? What are the pitfalls she identifies in ML evaluation?

### Week 8 — Matrix Linear Regression & Phase 1 Consolidation
**Paper:** "A High-Bias, Low-Variance Introduction to Machine Learning for Physicists" — Mehta et al. (2019)
- **Difficulty:** ★★
- **Type:** Physics Reports (long pedagogical review)
- **Minimal reading:** Sections 1–3 (overview + linear models + neural networks)
- **Full reading:** Sections relevant to topics covered so far
- **Reading guide:** This is a comprehensive review that ties together many concepts. Use it as a "big picture" reference. The physics analogies are a bonus. Focus on confirming that students understand the connections between topics, especially the triality of linear regression (geometry, probability, optimization).
- **Key questions:** How do the authors frame the bias-variance tradeoff? What connections do they draw between linear models and neural networks?

---

## Phase 2: Core ML (Weeks 9–20)

### Week 9 — k-Nearest Neighbors
**Paper:** "The Lack of A Priori Distinctions Between Learning Algorithms" — David Wolpert (1996)
- **Difficulty:** ★★★
- **Type:** Neural Computation journal paper
- **Minimal reading:** Abstract, introduction, Section 1 (the theorem statement)
- **Full reading:** Sections 1–3
- **Reading guide:** This is a hard paper. Focus on the *statement* and *implications* of the No Free Lunch theorem, not the full proof. The key insight: averaged over all possible problems, no algorithm is better than any other. This means inductive bias is necessary. Connect to k-NN's inductive bias ("locality").
- **Key questions:** What does the No Free Lunch theorem actually say? What are its practical implications? What is k-NN's inductive bias?

### Week 10 — Decision Trees
**Paper:** "Random Forests" — Leo Breiman (2001)
- **Difficulty:** ★★★
- **Type:** Machine Learning journal paper
- **Minimal reading:** Abstract, Sections 1–2 (introduction + random forest definition), Section 5 (empirical results — look at the figures)
- **Full reading:** Sections 1–5, Section 10 (conclusions)
- **Reading guide:** Breiman's writing is clear and practical. Focus on the definition of random forests and why randomness helps. The out-of-bag error estimate is a key concept. Don't get bogged down in the theoretical sections (Sections 4, 6–9). Connect bagging to the bias-variance decomposition from Week 5.
- **Key questions:** What is the difference between bagging and random forests? What is out-of-bag error? Why does random feature selection help? How does bagging reduce variance?

### Week 11 — Information Theory
**Paper:** "Visual Information Theory" — Christopher Olah (blog post, colah.github.io) *(re-read with information theory context)*
- **Difficulty:** ★★
- **Minimal reading:** Re-read the entropy and KL divergence sections
- **Full reading:** Full re-read with Week 11 context
- **Reading guide:** Now that students are studying information theory formally, Olah's visualizations should click at a deeper level. The connection between entropy, cross-entropy, and KL divergence is the key insight. Also connect to Gini impurity from Week 10.
- **Key questions:** What is self-information? Why is KL divergence non-negative? How does cross-entropy relate to entropy and KL? How does entropy relate to Gini impurity?

### Week 12 — Feature Engineering
**Paper:** "A Few Useful Things to Know about Machine Learning" — Pedro Domingos (2012) *(re-read Section 6 on feature engineering)*
- **Difficulty:** ★★
- **Minimal reading:** Section 6 + Section 5 (overfitting)
- **Full reading:** Full re-read with Phase 2 context
- **Reading guide:** Now that students know more ML, they'll get more out of the feature engineering and overfitting discussion. Compare Domingos' advice to what they've learned.
- **Key questions:** What makes a good feature? How does feature engineering interact with the bias-variance tradeoff?

### Week 13 — SVM Part 1
**Paper:** "Support-Vector Networks" — Cortes & Vapnik (1995)
- **Difficulty:** ★★★
- **Type:** Machine Learning journal paper
- **Minimal reading:** Abstract, Sections 1–2 (introduction + the soft margin formulation), Figure 1–3
- **Full reading:** Sections 1–5
- **Reading guide:** This is the foundational SVM paper. Focus on the geometric margin concept and the optimization formulation. The soft margin extension (slack variables) is in Section 3. Skip the detailed generalization theory (Section 4) on first read.
- **Key questions:** What is the margin? How is the soft-margin SVM formulated? What are support vectors?

### Week 14 — SVM Part 2
**Paper:** "Nonlinear Component Analysis as a Kernel Eigenvalue Problem" — Schölkopf, Smola, Müller (1998)
- **Difficulty:** ★★★
- **Type:** Neural Computation paper
- **Minimal reading:** Abstract, Section 1 (introduction), Section 2 (kernel PCA concept)
- **Full reading:** Sections 1–3
- **Reading guide:** This paper extends the kernel idea. Focus on understanding the kernel trick conceptually: why can we replace inner products with kernel functions? The key insight is that many algorithms only use inner products, so the kernel trick applies broadly.
- **Key questions:** What is the kernel trick? What makes a function a valid kernel? Give examples of common kernels.

### Week 15 — Neural Networks
**Paper:** "Approximation by Superpositions of a Sigmoidal Function" — Cybenko (1989)
- **Difficulty:** ★★★
- **Type:** Mathematics of Control, Signals, and Systems
- **Minimal reading:** Abstract, introduction, statement of Theorem 1
- **Full reading:** Sections 1–2 (skip the full proof on first read)
- **Reading guide:** This is the universal approximation theorem paper. The proof is dense — focus on the *statement* and *meaning*. A single hidden layer with enough neurons can approximate any continuous function. Discuss: why doesn't this mean "one layer is enough" in practice?
- **Key questions:** What does the universal approximation theorem state? Why is "width" not sufficient in practice (why do we need "depth")?

### Week 16 — Backpropagation
**Paper:** "Learning representations by back-propagating errors" — Rumelhart, Hinton, Williams (1986)
- **Difficulty:** ★★
- **Type:** Nature paper (short, influential)
- **Minimal reading:** Entire paper (it's short — ~4 pages)
- **Full reading:** Entire paper
- **Reading guide:** This is one of the most influential papers in ML history and is surprisingly readable. Focus on the description of the algorithm and the key idea: errors flow backward through the network via the chain rule. The XOR example in the paper is a great teaching moment.
- **Key questions:** What problem did backpropagation solve? How does error flow backward? Why was the XOR problem important historically?

### Week 17 — Training Neural Networks
**Paper:** "Adam: A Method for Stochastic Optimization" — Kingma & Ba (2014)
- **Difficulty:** ★★★
- **Type:** ICLR paper
- **Minimal reading:** Abstract, Section 1 (introduction), Section 2 (algorithm), Algorithm 1
- **Full reading:** Sections 1–3, Section 6 (conclusion)
- **Reading guide:** Focus on the algorithm itself (Algorithm 1) and the intuition: adaptive learning rates + momentum. The bias correction (Section 2) is important to understand. Skip the convergence proof (Section 4) on first read.
- **Key questions:** What are the two key ideas in Adam? Why is bias correction needed? What are the default hyperparameters?

**Optional additional paper:** "Dropout: A Simple Way to Prevent Neural Networks from Overfitting" — Srivastava et al. (2014)
- **Difficulty:** ★★
- **Minimal reading:** Abstract, Sections 1–2, Figures 1–2
- **Reading guide:** Very intuitive paper. Dropout randomly zeroes neurons during training. Focus on the interpretation as an ensemble.

### Week 18 — Generalization
**Paper:** "Understanding Deep Learning Requires Rethinking Generalization" — Zhang, Bengio, Hardt, Recht, Vinyals (2017)
- **Difficulty:** ★★★
- **Type:** ICLR paper
- **Minimal reading:** Abstract, Sections 1–3 (experiments on random labels)
- **Full reading:** Sections 1–5
- **Reading guide:** This paper shook the ML community by showing neural networks can memorize random data perfectly. The key experiments (Sections 2–3) are easy to understand and deeply thought-provoking. Focus on the tension between classical generalization theory and the empirical success of deep learning.
- **Key questions:** What happens when you train a neural network on randomly labeled data? Why is this surprising? What does this tell us about classical generalization bounds?

### Week 19 — Clustering / EM
**Paper:** "Maximum Likelihood from Incomplete Data via the EM Algorithm" — Dempster, Laird, Rubin (1977)
- **Difficulty:** ★★★
- **Type:** Journal of the Royal Statistical Society
- **Minimal reading:** Abstract, Section 1 (introduction), Section 2 (the algorithm)
- **Full reading:** Sections 1–4
- **Reading guide:** The EM algorithm is one of the most important tools in ML. Focus on the general framework: E-step computes expected complete-data log-likelihood, M-step maximizes it. The GMM application is the most intuitive example. Skip the historical examples in later sections.
- **Key questions:** What is the E-step? What is the M-step? Why does EM monotonically increase the likelihood? How does k-means relate to EM for GMM?

### Week 20 — PCA + Phase 2 Consolidation
**Paper:** "PCA" — Section 12.1 of Pattern Recognition and Machine Learning (Bishop)
- **Difficulty:** ★★★
- **Type:** Textbook section
- **Minimal reading:** Pages 561–568 (PCA derivation and interpretation)
- **Full reading:** Full PCA section including probabilistic PCA
- **Reading guide:** Bishop's treatment is thorough. Focus on two derivations: (1) maximum variance formulation, (2) minimum reconstruction error. Understanding both gives a deeper appreciation. The connection to SVD is in Section 12.1.2.
- **Key questions:** Derive PCA from the maximum variance perspective. Derive PCA from the minimum reconstruction error perspective. How are they related? What is the connection to SVD?

---

## Phase 3: Exam Prep (Weeks 21–24)

### Week 21–22 — Re-read key papers
**Re-read:** Domingos (2012), Rumelhart et al. (1986), Kingma & Ba (2014)
- Focus on being able to summarize each paper's key contribution in 2–3 sentences.

### Week 23–24 — No new papers
Focus entirely on exam preparation.

---

## Phase 4: Advanced ML (Weeks 25–36)

### Week 22–23 (Syllabus Week 26–27) — CNNs
**Paper 1:** "ImageNet Classification with Deep Convolutional Neural Networks" — Krizhevsky, Sutskever, Hinton (2012)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 3 (the architecture), Figure 2
- **Full reading:** Sections 1–5
- **Reading guide:** The AlexNet paper. Focus on the architecture description (Section 3): conv layers, ReLU, pooling, dropout. This paper launched the deep learning era.
- **Key questions:** What architectural innovations did AlexNet introduce? Why was ReLU important? How did they prevent overfitting?

**Paper 2:** "Deep Residual Learning for Image Recognition" — He, Zhang, Ren, Sun (2015)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (residual learning), Figure 2
- **Full reading:** Sections 1–4
- **Reading guide:** The ResNet paper. The key idea is simple but powerful: add identity shortcuts to learn residual functions. Focus on Figure 2 (the residual block) and the depth comparison in Section 4.
- **Key questions:** What problem does the residual connection solve? What is a residual block? How deep can ResNet go?

### Week 24–25 (Syllabus Week 28–29) — Sequence Models & Transformers
**Paper:** "Attention Is All You Need" — Vaswani et al. (2017)
- **Difficulty:** ★★★★
- **Type:** NeurIPS paper
- **Minimal reading:** Abstract, Section 1 (intro), Section 3 (model architecture), Figures 1–2
- **Full reading:** Sections 1–5
- **Reading guide:** THE Transformer paper. This is a must-read. Focus on: (1) scaled dot-product attention (Section 3.2.1), (2) multi-head attention (Section 3.2.2), (3) the overall encoder-decoder architecture (Figure 1). The positional encoding (Section 3.5) is worth understanding. Skip the training details (Section 5) on first read.
- **Key questions:** Why is it called "Attention Is All You Need"? What is scaled dot-product attention? Why the √d_k scaling? What is multi-head attention and why use it? How does positional encoding work?

### Week 26–27 (Syllabus Week 30–31) — Generative Models
**Paper 1:** "Auto-Encoding Variational Bayes" — Kingma & Welling (2014)
- **Difficulty:** ★★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (method), Algorithm 1
- **Full reading:** Sections 1–3
- **Reading guide:** The VAE paper. Focus on the ELBO derivation (Section 2) and the reparameterization trick (Section 2.3). The key insight: we can train a generative model by maximizing a lower bound on the log-likelihood. The reparameterization trick makes the estimator differentiable.
- **Key questions:** What is the reparameterization trick and why is it needed? What is the ELBO? What are the two terms in the ELBO and what do they represent?

**Paper 2:** "Generative Adversarial Nets" — Goodfellow et al. (2014)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 3 (the GAN framework), Figure 1
- **Full reading:** Sections 1–4
- **Reading guide:** The GAN paper. The minimax game is the key concept (Section 3). The theoretical analysis (Section 3.1) shows that the global optimum is achieved when the generator matches the data distribution. Focus on the game-theoretic formulation.
- **Key questions:** What is the minimax objective? What are the generator and discriminator roles? What is the theoretical optimum?

**Paper 3 (optional):** "Denoising Diffusion Probabilistic Models" — Ho, Jain, Abbeel (2020)
- **Difficulty:** ★★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (background), Section 3 (method), Figures 1–3
- **Full reading:** Sections 1–4
- **Reading guide:** The DDPM paper. Focus on the forward process (adding noise) and reverse process (learning to denoise). The key training objective (Algorithm 1) is surprisingly simple: predict the noise. Don't get lost in the math of the variational bound on first read.
- **Key questions:** What is the forward process? What is the reverse process? What does the model predict? Why is the training objective simple despite the complex theory?

### Week 28–29 (Syllabus Week 32–33) — Reinforcement Learning
**Paper 1:** "Playing Atari with Deep Reinforcement Learning" — Mnih et al. (2013)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (DQN), Figure 1
- **Full reading:** Sections 1–4
- **Reading guide:** The DQN paper. Focus on the key innovations: experience replay and the target network (Section 2). The input is raw pixels, output is Q-values — a deep neural network approximates the Q-function.
- **Key questions:** What are the two key techniques that stabilize DQN training? Why is experience replay useful? Why use a separate target network?

**Paper 2:** "Proximal Policy Optimization Algorithms" — Schulman et al. (2017)
- **Difficulty:** ★★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (clipped objective), Section 3 (algorithm)
- **Full reading:** Entire paper (it's short)
- **Reading guide:** PPO is the algorithm behind RLHF. Focus on the clipped surrogate objective (Section 2). The key idea: limit how much the policy can change in one update to ensure stable training.
- **Key questions:** What problem does PPO solve compared to vanilla policy gradients? What is the clipped objective? Why clip?

### Week 30 (Syllabus Week 34) — Representation Learning
**Paper:** "A Simple Framework for Contrastive Learning of Visual Representations" — Chen et al. (2020)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (method), Figure 2
- **Full reading:** Sections 1–4
- **Reading guide:** The SimCLR paper. Contrastive learning learns representations by pulling positive pairs together and pushing negative pairs apart. Focus on the NT-Xent loss (normalized temperature-scaled cross-entropy). The key components: data augmentation, encoder, projection head, contrastive loss.
- **Key questions:** What is contrastive learning? What are positive and negative pairs? What is the InfoNCE/NT-Xent loss?

### Week 31 (Syllabus Week 35) — LLMs
**Paper 1:** "Language Models are Few-Shot Learners" — Brown et al. (2020)
- **Difficulty:** ★★★★
- **Type:** NeurIPS paper (GPT-3 paper, 75 pages)
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (approach), Figures 1–3
- **Full reading:** Sections 1–6 (skip detailed benchmark results)
- **Reading guide:** The GPT-3 paper. It's long — don't try to read everything. Focus on the key claims: (1) scaling up models improves few-shot performance, (2) few-shot learning emerges at scale. The scaling behavior is the key insight. Look at Figures 1–3 for the scaling trends.
- **Key questions:** What is few-shot learning? How does GPT-3 perform few-shot learning without fine-tuning? What is the relationship between model size and performance?

**Paper 2:** "Training language models to follow instructions with human feedback" (InstructGPT) — Ouyang et al. (2022)
- **Difficulty:** ★★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 3 (method), Figure 2
- **Full reading:** Sections 1–5
- **Reading guide:** The InstructGPT paper — this is the RLHF paper. Focus on the three-step pipeline (Section 3): SFT, reward model training, PPO. The key figure is Figure 2 (the RLHF pipeline). This connects RL (Week 32–33) to LLMs.
- **Key questions:** What are the three steps of RLHF? How is the reward model trained? How is PPO used to optimize the policy? Why not just use SFT?

### Week 32 (Syllabus Week 36) — Phase 4 Consolidation
**Paper:** "The Bitter Lesson" — Rich Sutton (2019)
- **Difficulty:** ★
- **Type:** Blog post (very short, ~1 page)
- **Minimal reading:** Entire post
- **Full reading:** Entire post
- **Reading guide:** Sutton argues that the biggest AI advances have come from scaling computation, not from clever human-designed features or methods. This is a provocative and important perspective. Use it as a discussion starter about the future of ML.
- **Key questions:** What is Sutton's "bitter lesson"? Do you agree with it? What are counterarguments?

---

## Phase 5: IOAI Prep (Weeks 37–44)

### Week 33–34 (Syllabus Week 37–38) — IOAI Preparation
**Paper:** IOAI official problem sets and solutions (released competition materials)
- **Difficulty:** ★★★–★★★★★
- **Reading guide:** Treat these as exam problems, not papers. Solve them under timed conditions.

### Week 35–36 (Syllabus Week 39–40) — Advanced Topics
**Paper 1:** "Neural Message Passing for Quantum Chemistry" — Gilmer et al. (2017)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (message passing framework)
- **Reading guide:** An accessible introduction to graph neural networks via the message passing framework. The key equation: h_v^{k+1} = UPDATE(h_v^k, AGGREGATE({h_u^k : u ∈ N(v)})).

**Paper 2:** "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks" — Lewis et al. (2020)
- **Difficulty:** ★★★
- **Minimal reading:** Abstract, Section 1 (intro), Section 2 (method), Figure 1
- **Reading guide:** The RAG paper. Combines retrieval with generation. Focus on the architecture: retriever + generator, and how they're trained jointly.

### Week 37 (Syllabus Week 44) — Final Reading
**Paper:** "On the Measure of Intelligence" — François Chollet (2019)
- **Difficulty:** ★★
- **Type:** arXiv preprint (essay-style)
- **Minimal reading:** Sections 1–3
- **Full reading:** Entire paper
- **Reading guide:** A thought-provoking essay on what "intelligence" means and how to measure it. A fitting capstone: it asks students to think critically about what ML systems are actually doing and whether they're truly "intelligent." Connects to the IOAI spirit.
- **Key questions:** What is Chollet's definition of intelligence? Why does he argue that skill at a specific task is not intelligence? How does this relate to the No Free Lunch theorem?

---

## Reading Skills Progression

### By Week 8, students should be able to:
- Read a blog post and summarize key points
- Identify the main claim of a paper from abstract + introduction
- Understand figures and their captions

### By Week 20, students should be able to:
- Read a full paper section and understand the method
- Identify the loss function, model, and optimizer in any ML paper
- Critically assess experimental methodology
- Connect a paper's contribution to course material

### By Week 36, students should be able to:
- Read a modern ML paper independently
- Identify the key mathematical contributions
- Spot connections between papers (e.g., attention → transformers → scaling laws → LLMs)
- Formulate critiques of a paper's approach

### By Week 44, students should be able to:
- Read IOAI-level papers and competition problems
- Synthesize knowledge across the entire ML landscape
- Present a paper to peers in 5–10 minutes

## How to Teach Paper Reading

### In-Class Paper Reading Sessions (start Week 4)

1. **Week 4:** Walk through the structure of a paper (abstract → intro → method → experiments → conclusion). Do this live with the Davis & Goadrich paper.
2. **Week 8:** Have a student summarize the Mehta et al. (2019) paper in 5 minutes. Provide feedback.
3. **Week 10:** Have a student summarize the Breiman (2001) paper in 5 minutes. Discuss bagging and random forests.
4. **Week 16:** Discuss how to read math-heavy papers: focus on the setup and results, skip proofs on first read.
5. **Week 12:** Discuss how to read papers critically: what are the assumptions? What are the limitations?
6. **Week 29:** Full paper discussion session on "Attention Is All You Need" — structured as a 40-min seminar.
7. **Week 35:** Full paper discussion on InstructGPT (RLHF) — connecting RL to LLMs.

### Paper Reading Template (give to students)

```
PAPER READING NOTES
===================
Title:
Authors:
Year:
Venue:

1. Problem: What problem does this paper address?

2. Prior work: What was known before? What was the gap?

3. Key idea: State the main contribution in 1-2 sentences.

4. Method: How does it work? (1-2 paragraphs)
   - Model:
   - Loss function:
   - Optimizer:

5. Results: What are the key empirical or theoretical results?

6. Connections: How does this relate to what we learned in class?

7. Limitations: What are the weaknesses or assumptions?

8. Questions: What did you not understand? What would you ask the authors?
```
