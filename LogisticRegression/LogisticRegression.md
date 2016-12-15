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

![](http://latex.codecogs.com/gif.latex?P(y=1|x)=\\frac{1}{1+e^{w^{T} x}})
