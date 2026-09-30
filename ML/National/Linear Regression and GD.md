Linear regression and Gradient descent 
algorithm
Fatemeh Seyyedsalehi

A supervised problem

 Predict the residential electrical usage as a function of

living area and house members.

 Input feature 𝒙 𝑖 ∈ X
 Output or target 𝑦 𝑖 ∈ Y
 Training set 𝐷 = 𝒙 𝑖 , 𝑦 𝑖

𝑛

𝑖=1

Living area (𝑚2)

#House members

Residential Electrical 
usage(𝑘𝑤ℎ)

40
70
70
200
150
.
.

2
2
4
3
4
.
.

4
5
7
8
7
.
.

2

A supervised problem

 Our goal is to learn a function ℎ ∶ X → Y
 ℎ(𝑥) should be a good predictor for the corresponding 𝑦
 ℎ is called a hypothesis

Ref. [2]

3

Linear Regression

 Regression problem: The target is continuous

 We begin by the class of linear functions as a hypothesis

 Easy to extend to generalized linear and so cover more

complex regression functions

4

Linear Regression

 Coming back to our problem
 𝒙 is a two dimensional vector in ℝ2
 We first decide how to represent the hypothesis ℎ

 A function family

Living area (𝑚2)

#House members

Residential Electrical 
usage(𝑘𝑤ℎ)

40
70
70
200
150
.
.

2
2
4
3
4
.
.

4
5
7
8
7
.
.

5

Linear Regression: the hypothesis space

 ℎ𝑤 𝒙 as a linear function of 𝒙

ℎ𝑤 𝒙 = 𝑤0 + 𝑤1 𝑥1 + 𝑤2𝑥2

 Where 𝑤𝑖s are called parameters or weights of the model
which parameterize the space of linear functions mapping
from X to Y.

6

Linear Regression: the hypothesis space

 To have a better notation we consider 𝑥0 = 1 (the

intercept term),

ℎ𝑤 𝒙 = σ𝑖=0

𝑑 𝑤𝑖𝑥𝑖

 How to learn parameters 𝑤𝑖s, given a training set,

 Make ℎ 𝒙 close to 𝑦

7

Linear Regression: the hypothesis space

 Univariate

 Multivariate

ℎ: ℝ → ℝ

ℎ𝑤 𝒙 = 𝑤0 + 𝑤1𝑥

𝑥

Ref. [1]

ℎ: ℝ𝑑 → ℝ

ℎ𝑤 𝒙 = 𝑤0 + 𝑤1𝑥1 + . . . 𝑤𝑑𝑥𝑑

 𝒘 = 𝑤0, 𝑤1, . . . , 𝑤𝑑

𝑇 are parameters we need to set.

8

How to measure the error

500
500

400
400

300
300

200
200

100
100

0
0

𝑦(𝑖) − ℎ𝑤(𝑥(𝑖))

0
0

500
500

1000
1000

1500
1500

2000
2000

2500
2500

Ref. [1]

3000
3000
𝑥

 A loss function between the ground truth and the

estimated output

Loss = (𝑦 − ℎ𝑤(𝑥))2

9

How to measure the error

500
500

400
400

300
300

200
200

100
100

0
0

𝑦(𝑖) − ℎ𝑤(𝑥(𝑖))

0
0

500
500

1000
1000

1500
1500

2000
2000

2500
2500

Ref. [1]

3000
3000
𝑥

Cost function (sum of squared error(SSE)):

𝐽 𝒘 = ෍

𝑛

𝑖=1
𝑛

= ෍

𝑖=1

𝑦 𝑖 − ℎ𝑤(𝑥(𝑖))

2

𝑦 𝑖 − 𝑤0 − 𝑤1𝑥 𝑖 2

10

Linear Regression: the learning algorithm

 Choose 𝑤 so as to minimize the 𝐽(𝑤)

𝐽 𝒘 = σ𝑖=1

𝑛

𝑦 𝑖 − ℎ𝑤(𝒙 𝑖 )

2

 The learning algorithm: optimization of the cost function

 Explicitly taking the cost function derivative with respect to the 

𝑤𝑖s, and setting them to zero.

 Parameters of the best hypothesis for the training set:
𝒘∗ = argmin

𝐽(𝒘)

𝒘

11

Cost function optimization: univariate

𝑛
𝐽 𝒘 = ෍

𝑖=1

𝑦 𝑖 − 𝑤0 − 𝑤1𝑥 𝑖 2

 Necessary conditions for the “optimal” parameter values:

𝜕𝐽 𝒘
𝜕𝑤0

𝜕𝐽 𝒘
𝜕𝑤1

= 0

= 0

12

Optimality conditions: univariate

𝑛
𝐽 𝒘 = ෍

𝑖=1

𝑦 𝑖 − 𝑤0 − 𝑤1𝑥 𝑖 2

𝜕𝐽 𝒘
𝜕𝑤1

𝜕𝐽 𝒘
𝜕𝑤0

𝑛
= ෍

𝑖=1

2 𝑦 𝑖 − 𝑤0 − 𝑤1𝑥 𝑖 −𝑥 𝑖 = 0

𝑛
= ෍

𝑖=1

2 𝑦 𝑖 − 𝑤0 − 𝑤1𝑥 𝑖 −1 = 0

 A systems of 2 linear equations

13

Cost function optimization: multivariate

𝐽 𝒘 = σ𝑖=1

𝑛

𝑦 𝑖 − ℎ𝑤(𝒙 𝑖 )

2

𝑛
= σ𝑖=1

𝑦 𝑖 − 𝒘𝑇𝒙 𝑖 2

𝑿 =

(1)

(1) ⋯ 𝑥𝑑
1 𝑥1
(2)
(2)
⋯
1
𝑥𝑑
𝑥1
⋱
⋮
⋮
⋮
(𝑛)
(𝑛) ⋯ 𝑥𝑑
1 𝑥1

𝒘 =

𝑤0
𝑤1
⋮
𝑤𝑑

𝒚 =

𝑦(1)
⋮
𝑦(𝑛)

14

Cost function optimization: multivariate

 Explicitly taking the cost function derivative with respect 

to the 𝒘s, and setting them to zero.

2
𝐽 𝒘 = 𝒚 − 𝑿𝒘 𝟐

𝛻𝒘𝐽 𝒘 = −2𝑿𝑇 𝒚 − 𝑿𝒘

𝛻𝒘𝐽 𝒘 = 𝟎 ⇒ 𝑿𝑇𝑿𝒘 = 𝑿𝑇𝒚
𝒘 = 𝑿𝑇𝑿 −𝟏 𝑿𝑇𝒚

 Is  𝑿𝑇𝑿 invertible? 

15

Cost function optimization

 Another approach,

 Start from an initial guess and iteratively change 𝒘 to minimize 𝐽 𝒘 .

 The gradient descent algorithm

 Steps:

 Start from 𝒘0
 Repeat

 Update 𝒘𝑡 to 𝒘𝑡+1 in order to reduce 𝐽
 𝑡 ← 𝑡 + 1

 until we hopefully end up at a minimum



16

Review:
Gradient descent

 In each step, takes steps proportional to the negative of the

gradient vector of the function at the current point 𝒘𝑡:

𝒘𝑡+1 = 𝒘𝑡 − 𝜂 𝛻 𝐽 𝒘𝑡

 𝐽(𝒘) decreases fastest if one goes from 𝒘𝑡 in the direction of −𝛻𝐽 𝒘𝑡

 Assumption: 𝐽(𝒘) is defined and differentiable in a neighborhood of a

point 𝒘𝑡

Gradient ascent takes steps proportional to (the positive of) 
the gradient to find a local maximum of the function

 Continue to find

17

𝒘∗ = argmin

𝐽(𝒘)

𝒘

Review:
Gradient descent

 Minimize 𝐽(𝒘)

𝒘𝑡+1 = 𝒘𝑡 − 𝜂𝛻𝒘𝐽(𝒘𝑡)

Step size
(Learning rate parameter)

𝛻𝒘𝐽 𝒘 =

𝜕𝐽 𝒘
𝜕𝑤1
⋮
𝜕𝐽 𝒘
𝜕𝑤𝑑

 If 𝜂 is small enough, then 𝐽 𝒘𝑡+1 ≤ 𝐽 𝒘𝑡 .
 𝜂 can be allowed to change at every iteration as 𝜂𝑡.

18

Review:
Gradient descent disadvantages

 Local minima problem

 However, when 𝐽 is convex, all

local minima are also global
minima ⇒ gradient descent can converge to the global
solution.

19

Review: Problem of gradient descent with 
non-convex cost functions

J()



20

Ref. [2]



Review: Problem of gradient descent with 
non-convex cost functions

J()



21

Ref. [2]



Cost function optimization

 Minimize 𝐽(𝒘)

𝒘𝑡+1 = 𝒘𝑡 − 𝜂𝛻𝒘𝐽(𝒘𝑡)

 𝐽(𝒘): Sum of squares error

𝐽 𝒘 = ෍

𝑖=1

𝑛

𝑦 𝑖 − ℎ𝒘 𝒙 𝑖

2

 Weight update rule for ℎ𝒘 𝒙 = 𝒘𝑇𝒙:

𝑛
𝒘𝑡+1 = 𝒘𝑡 + 𝜂 ෍
𝑖=1

𝑦 𝑖 − 𝒘𝑡𝑇

𝒙 𝑖 𝒙(𝑖)

22

Cost function optimization

 Weight update rule: ℎ𝒘(𝒙) = 𝒘𝑇𝒙

𝑛
𝒘𝑡+1 = 𝒘𝑡 + 𝜂 ෍
𝑖=1

𝑦 𝑖 − 𝒘𝑇𝒙 𝑖 𝒙(𝑖)

Batch mode: each step 
considers all training data

 𝜂: too small → gradient descent can be slow.
 𝜂 : too large → gradient descent can overshoot the

minimum. It may fail to converge, or even diverge.

23

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

(function of the parameters 𝑤0,𝑤1)

𝐽(𝑤0, 𝑤1)

1
𝑤

Ref. [2]

𝑤0

24

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

(function of the parameters 𝑤0,𝑤1)

𝐽(𝑤0, 𝑤1)

1
𝑤

Ref. [2]

𝑤0

25

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

26

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

(function of the parameters 𝑤0,𝑤1)

𝐽(𝑤0, 𝑤1)

1
𝑤

Ref. [2]

𝑤0

27

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

28

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

29

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

30

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

31

ℎ𝑤 𝑥 = 𝑤0 + 𝑤1𝑥

𝐽(𝑤0, 𝑤1)

(function of the parameters 𝑤0,𝑤1)

1
𝑤

Ref. [2]

𝑤0

32

