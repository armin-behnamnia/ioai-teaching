Introduction to machine learning

Fatemeh Seyyedsalehi

This lecture: the learning problem

 Example of machine learning problem
 Component of learning 
 A simple model
 Paradigms in machine learning

2

Example

 Predicting the risk of heart attack

 Is this a risky person for heart attack? (yes or no)

age

gender

diabetes

weight

…

59

Female

Yes

90

…

 The essence of machine learning

 A pattern exist
 We do not know it mathematically
 We have data on it

3

Components of learning 

Unknown target function
𝑡: 𝒳 → 𝒴

Training examples
𝒙(1), 𝑦(1) , 𝒙(2), 𝑦(2) , …

Learning 
Algorithm

Final Hypothesis
𝑔 ≈ 𝑡

Hypothesis set
𝑔 ∈ ℋ

4

Solution component

 The learning model:
 The hypothesis set

ℋ = ℎ

𝑔 ∈ ℋ

 The learning algorithm

 Search the hypothesis set to
find the best estimate of the 
target function

5

A simple hypothesis set

 Predicting the risk of heart attack

 Is this a risky person for heart attack? (yes (+1) or no (-1))
 For input vector 𝒙 = 𝑥1, … , 𝑥𝑑 , a person attributes

age

gender

𝑥1: 
𝑥2: 
𝑥3: diabetes
𝑥4: 
weight

…

59

Female

Yes

90

…

 A simple hypothesis set: The perceptron

6

A simple hypothesis set

 A case with a high risk of heart attack

𝑑

𝐴 𝑟𝑖𝑠𝑘𝑦 𝑝𝑒𝑟𝑠𝑜𝑛: 𝑖𝑓 ෍
𝑖=1

𝑤𝑖𝑥𝑖 > 𝑡ℎ𝑟𝑒𝑠ℎ𝑜𝑙𝑑

 Our hypothesis set:

𝑑

ℎ 𝒙 = 𝑠𝑖𝑔𝑛 (෍
𝑖=1

𝑤𝑖𝑥𝑖 − 𝑡ℎ𝑟𝑒𝑠ℎ𝑜𝑙𝑑)

7

A learning algorithm for perceptron

𝑑

ℎ 𝒙 = 𝑠𝑖𝑔𝑛 (෍
𝑖=1

𝑤𝑖𝑥𝑖 − 𝑤0)

 Considering 𝑥0 = 1,

ℎ 𝒙 = 𝑠𝑖𝑔𝑛 (𝒘𝑻𝒙)

 Given a training set:   𝒙(1), 𝑦(1) , 𝒙(2), 𝑦(2) , …

 Attributes of a set of normal or case of heart attack persons

8

A learning algorithm for perceptron

Repeat

Pick a misclassified point 𝒙 𝑖 , 𝑦 𝑖

from training data

𝑠𝑖𝑔𝑛 𝒘𝑇𝒙(𝑖) ≠ 𝑦(𝑖)

Update 𝒘:

𝒘 = 𝒘 + 𝑦(𝑖)𝒙(𝑖)
Until all training data points are correctly classified by 𝑔

9

[1]

Generalization

 We don’t intend to memorize data but want to distinguish 

the pattern.

 A core objective of learning is to generalize from the  

experience.
 Generalization: ability of a learning algorithm to perform 

accurately on new, unseen examples after having experienced?

10

Experience in ML

 Basic premise of learning:

 Using a set of observations to uncover an underlying process

 We have different types of (getting) observations in 

different types or paradigms of ML methods

11

A definition of ML

 Tom Mitchell (1998):

 A computer program is said to learn a task from experience if its 

performance improves with experience

 Using the observed data to make better decisions

 Generalizing from the observed data

12

Paradigms of machine learning

 Supervised learning
(input, correct output)
 Unsupervised learning

(input, ?)

 Reinforcement learning

(input, some output, grade for this output)

 Other paradigms: semi-supervised learning, online 

learning, active learning, etc

13

Supervised learning 

 Supervised learning
(input, correct output)
 Our risky heart attack identifier
 Predicting the function of protein sequences 

14

[https://medium.com]

Supervised learning

 Extract useful information as features

 Represent a protein sequence in a vectorized format

 Proteins with a length of 1000 amino-acids
 Each amino-acid is represented as a one hot vector

𝑥1
1

0

…

0

0

𝑥2
0

1

…

0

0

…

𝑥999
0

1

…

0

0

𝑥1000
0

0

…

0

1

15

Unsupervised learning

 Revealing structure in the observed data

(input, ?)
 Clustering: partitioning of data into groups of similar data points.

 Customer segmentation in marketing
 Community detection in social networks

 Users are represented with their links with others

16

[Literature review on data analytics
for social microblogging platforms]

Reinforcement learning

 Partial (indirect) feedback, no explicit guidance

(input, some output, grade for this output)
 AlphaZero

 DeeepMind chess player

 Autonomous driving

17

Some Learning Application Areas

 Computer Vision (Photo tagging, face recognition,…)
 Natural language processing (e.g., machine translation)
 Robotics
 Speech recognition
 Autonomous vehicles
 Social network analysis
 Web search engines
 Medical outcomes analysis
 Marketing (stock prediction)
 Computational biology
 Self-customizing programs (recommender systems)
18

