# Logistic Regression
## Idea

Given a linear combination of features:

![](http://latex.codecogs.com/gif.latex?z=w^{T} x)

We want to map the output z to the interval [0,1]. In this way, the mapped value can be used as the posterior probability of belonging to a class.

A sigmoid function will be used to map z to a probability:

![](http://latex.codecogs.com/gif.latex?s(z)=\\frac{1}{1+e^{z}}), where ![](http://latex.codecogs.com/gif.latex?z\\in (- \\infty,+\\infty))
