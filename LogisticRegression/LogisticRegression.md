# Logistic Regression
## Idea

Given a linear combination of features:

![](http://latex.codecogs.com/gif.latex?z=w^{T} x)

We want to map the output z to the interval [0,1]. In this way, the mapped value can be used as the posterior probability of belonging to a class.

A sigmoid function will be used to map z to a probability:

![](http://latex.codecogs.com/gif.latex?s(z)=\\frac{1}{1+e^{z}}), where ![](http://latex.codecogs.com/gif.latex?z\\in (- \\infty,+\\infty))

## Determine w

Suppose we have a two class classification problem, with label 1 and 0 respectively.

Given x, the probability that it belongs to 1-class:

![](http://latex.codecogs.com/gif.latex?P(y=1|x)=\\frac{1}{1+e^{w^{T} x}}=s(w^{T} x))

Then the probability for x to belong to 0-class:

![](http://latex.codecogs.com/gif.latex?P(y=0|x)=1-P(y=1|x)=1-s(w^{T} x))

Given m training data points:

![](http://latex.codecogs.com/gif.latex?x_1, x_2,...,x_m)

We want to find a w such that:

if ![](http://latex.codecogs.com/gif.latex?x_i) belongs to 1-class, then ![](http://latex.codecogs.com/gif.latex?P(y=1|x)) is as large as possible (as close as possible to 1).

if ![](http://latex.codecogs.com/gif.latex?x_i) belongs to 0-class, then ![](http://latex.codecogs.com/gif.latex?P(y=0|x)) is as large as possible (as close as possible to 1).

Suppose 

![](http://latex.codecogs.com/gif.latex?x_1, x_2,...,x_k) belongs to 1-class

![](http://latex.codecogs.com/gif.latex?x_{k+1}, x_{k+2},...,x_m) belongs to 0-class

We can construct the following likelihood function:

![](http://latex.codecogs.com/gif.latex?L=\prod_{l=1}^{k})
