# Resource List — Textbooks, References, and Visualization Tools

## Primary Textbooks (Reference, Not Required Purchase)

These are for the instructor to prepare handouts and for advanced students to go deeper. No textbook is required for the course — all necessary material is in the handouts. However, these references are invaluable for preparation.

### Core ML Textbooks

| Book | Author | Best For | Level |
|------|--------|----------|-------|
| Pattern Recognition and Machine Learning (PRML) | Christopher Bishop | Everything in Phase 1–2. The gold standard for ML theory. | Intermediate–Advanced |
| The Elements of Statistical Learning (ESL) | Hastie, Tibshirani, Friedman | Statistical perspective. Excellent for linear models, SVMs, trees. | Advanced |
| Understanding Machine Learning | Shalev-Shwartz & Ben-David | Rigorous theoretical ML. PAC learning, VC dimension. Good for generalization theory. | Intermediate–Advanced |
| A Course in Machine Learning | Hal Daumé III | Very accessible. Good for beginners. Free online. | Beginner–Intermediate |
| Machine Learning | Tom Mitchell | Classic. Good for decision trees, concept learning. Slightly dated. | Beginner–Intermediate |
| Mathematics for Machine Learning | Deisenroth, Faisal, Ong | Fills math gaps. Excellent for linear algebra + calculus + probability in ML context. | Beginner–Intermediate |

### Deep Learning Textbooks

| Book | Author | Best For | Level |
|------|--------|----------|-------|
| Deep Learning | Goodfellow, Courville, Bengio | The standard DL textbook. Strong on theory and history. Phase 4 reference. | Intermediate–Advanced |
| Dive into Deep Learning (D2L) | Zhang, Lipton, Li, Smola | Practical + mathematical. Good code examples (for instructor reference, not for students). | Intermediate |
| Neural Networks and Deep Learning | Michael Nielsen | Beautifully written, very intuitive. Free online. Great for NN intuition. | Beginner–Intermediate |

### Reinforcement Learning

| Book | Author | Best For | Level |
|------|--------|----------|-------|
| Reinforcement Learning: An Introduction | Sutton & Barto | The RL bible. Covers everything from first principles. Free online (2nd edition). | Intermediate |
| Algorithms for Reinforcement Learning | Csaba Szepesvári | More concise, mathematical. Good for theory. | Advanced |

### Probability & Information Theory

| Book | Author | Best For | Level |
|------|--------|----------|-------|
| Information Theory, Inference, and Learning Algorithms | David MacKay | Masterpiece. Combines information theory, coding theory, and ML. Free online. | Intermediate–Advanced |
| Probability Theory: The Logic of Science | E.T. Jaynes | Deep philosophical treatment of Bayesian probability. For the instructor. | Advanced |

## Lecture Notes & Online Courses (Instructor Reference)

These are high-quality free resources for lecture preparation:

| Resource | Author | Link/Source | Notes |
|----------|--------|-------------|-------|
| CS229: Machine Learning | Andrew Ng (Stanford) | stanford.edu | Classic ML course. Good lecture notes. |
| CS231n: CNNs for Visual Recognition | Stanford | stanford.edu | Excellent CNN and vision material. |
| CS224n: NLP with Deep Learning | Stanford | stanford.edu | Excellent sequence model and transformer material. |
| 6.S191: Introduction to Deep Learning | MIT | mit.edu | Good modern DL coverage. |
| Introduction to Statistical Learning (ISLR) | James, Witten, Hastie, Tibshirani | statlearning.com | Accessible version of ESL. Free PDF. |
| Andrej Karpathy's blog / YouTube | Andrej Karpathy | karpathy.github.io / YouTube | Exceptional intuition for neural networks. |
| 3Blue1Brown neural network series | Grant Sanderson | YouTube | Best visual intuition for neural networks and backprop. |

## Visualization Tools (For In-Class Demos)

Since this course is math/visual/no-code, these tools are essential for creating visual demonstrations:

### Interactive Tools

| Tool | Purpose | How to Use |
|------|---------|------------|
| [TensorFlow Playground](https://playground.tensorflow.org) | Visualize neural network training in real time | In-class demo: show how layers, neurons, learning rate affect training. Solve XOR live. |
| [Distill.pub](https://distill.pub) | Interactive visual explanations of ML concepts | Assign as reading. The attention/entropy articles are exceptional. |
| [Seeing Theory](https://seeing-theory.brown.edu) | Visual probability and statistics | Use for probability refresher (Week 4). Interactive distributions, CLT, regression. |
| [Polynomial regression visualizer](https://www.desmos.com) | Show overfitting/underfitting | Desmos graphing calculator: plot data points and fit polynomials of varying degree. |
| [MLU Explain](https://mlu-explain.github.io) | Visual explanations of ML concepts | Excellent interactive guides for gradient descent, decision trees, etc. |
| [Attention visualization](https://github.com/jessevig/bertviz) | Visualize attention weights | Show how attention works in transformers (conceptual, not code). |

### Static Visualization Creation

| Tool | Purpose |
|------|---------|
| Desmos | 2D function plotting, regression visualization, loss landscapes |
| GeoGebra | Geometry (SVM margins, PCA projections, decision boundaries) |
| Manim (3Blue1Brown's animation tool) | Animated mathematical concepts (if instructor has time) |
| Excalidraw | Hand-drawn-style diagrams for handouts (very approachable look) |
| TikZ/LaTeX | Publication-quality diagrams for handouts |
| draw.io / diagrams.net | Flowcharts (model selection, ML pipeline) |

### Key Visual Demos to Prepare (by week)

| Week | Visual Demo | Tool |
|------|------------|------|
| W1 | Fitting a line to 2D data (drag-and-fit) | Desmos |
| W2 | OLS as projection onto column space | GeoGebra (3D) |
| W3 | Gradient descent on a 1D quadratic (ball rolling downhill) | Desmos / TF Playground |
| W5 | Entropy of a Bernoulli as function of p | Desmos |
| W6 | Sigmoid function + decision boundary in 2D | Desmos / TF Playground |
| W7 | ROC curve construction | Desmos |
| W9 | XOR problem + polynomial features | TF Playground / Desmos |
| W10 | k-NN decision boundary in 2D | Custom or TF Playground |
| W11 | Decision tree splitting on 2D data | MLU Explain |
| W12 | SVM maximum margin | GeoGebra |
| W13 | Kernel trick: data → feature space → linear boundary | Custom diagram |
| W14 | Neural network forward pass (node activations lighting up) | TF Playground |
| W15 | Computational graph + backprop flow | Excalidraw / custom |
| W16 | Dropout (neurons randomly disappearing) | TF Playground |
| W17 | Double descent curve | Desmos |
| W18 | k-means clustering iterations | Custom / MLU Explain |
| W19 | PCA projection and variance explained | GeoGebra (3D) |
| W26 | Convolution operation (sliding window) | Custom animation |
| W28 | RNN unrolling through time | Excalidraw |
| W29 | Attention weights as heatmaps | Distill.pub attention article |
| W30 | VAE latent space interpolation | Distill.pub or custom |
| W31 | GAN: generator vs. discriminator | Custom diagram |
| W32 | Gridworld MDP + value iteration | Custom / GeoGebra |
| W33 | RLHF pipeline (3-step diagram) | Excalidraw |

## Problem Sets & Practice Resources

### Exam Preparation

| Resource | Source | Topics |
|----------|--------|--------|
| Past IOAI problems | IOAI official website | Competition-format problems |
| CS229 problem sets | Stanford CS229 | Classic ML (linear models, SVMs, neural networks) |
| ESL exercises | Hastie et al. | Statistical learning theory |
| PRML exercises | Bishop | All ML topics, with solutions available |
| "100 Page Machine Learning Book" | Andriy Burkov | Concise reference + problems |

### Math Practice

| Resource | Topics |
|----------|--------|
| Mathematics for Machine Learning (Deisenroth et al.) | Linear algebra, calculus, probability refresher |
| MIT 18.06 Linear Algebra (Strang) | If students need LA support (should be covered by parallel course) |
| Matrix Cookbook | Matrix calculus reference for backprop derivations |

## Handout Template

Each weekly handout should follow this structure:

```
WEEK [N] HANDOUT: [Topic]
========================

1. MOTIVATION
   - What problem are we trying to solve?
   - Why did the previous methods fall short?
   - Real-world example.

2. MATHEMATICAL SETUP
   - Notation (define every symbol)
   - Model definition
   - Loss function

3. DERIVATION
   - Step-by-step mathematical derivation
   - Every step justified (no "it can be shown")
   - Geometric interpretation alongside algebra

4. ALGORITHM
   - Pseudocode (not Python)
   - Computational complexity analysis

5. INTUITION
   - Geometric picture
   - What is the algorithm "doing"?
   - Common analogies

6. PRACTICAL CONSIDERATIONS
   - Hyperparameters and their effects
   - Common pitfalls
   - When to use / not use this method

7. CONNECTIONS
   - How does this relate to previous topics?
   - What does this enable for future topics?

8. WORKED EXAMPLES
   - 2–3 fully worked numerical examples

9. EXERCISES
   - 5–10 problems of varying difficulty
   - Marked: [Basic] / [Intermediate] / [★ Advanced]

10. SUMMARY
    - Key equations (box these)
    - Key intuition (one sentence per concept)
    - "If you remember nothing else, remember..."
```

## Curated FAQ for Students

Anticipate common student questions and prepare answers:

| Question | Answer Reference |
|----------|-----------------|
| "Do I need to know Python for this class?" | No. This course is math and theory. Python is taught in the parallel programming course. |
| "I already know [topic]. Can I skip?" | No. But you can help your peers and work on the ★ challenge problems and advanced readings. |
| "Will this be on the exam?" | If it's in the handout or was covered in class, it's fair game. ★ sections are bonus. |
| "How do I read a research paper?" | See the paper reading template in 02_Paper_Reading_Roadmap.md. We'll practice in class. |
| "I'm struggling. What should I do?" | Ask questions in class. Review the handout exercises. Come to office hours. Don't fall behind — topics build on each other. |
| "I'm ahead of the class. What should I do?" | Read the suggested papers in full. Attempt all ★ problems. Help peers (teaching deepens understanding). Explore the advanced references in this resource list. |
