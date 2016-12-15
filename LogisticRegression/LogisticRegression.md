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

![](http://latex.codecogs.com/gif.latex?L=\\prod_{l=1}^{k}P(y=1|x_{l})\\prod_{l=k+1}^{m}P(y=0|x_{l}))

For convenience, for each data point ![](http://latex.codecogs.com/gif.latex?x_i) in the training set, we can make:

![](http://latex.codecogs.com/gif.latex?L_i =(S(z_i))^{y_{i}}(1-S(z_i))^{1-y_{i}})

In this way, if ![](http://latex.codecogs.com/gif.latex?x_i) belongs to 1-class, then ![](http://latex.codecogs.com/gif.latex?y_i=1), we have

![](http://latex.codecogs.com/gif.latex?L_i=s(z_i)=P(y=1|x_i))

if ![](http://latex.codecogs.com/gif.latex?x_i) belongs to 0-class, then ![](http://latex.codecogs.com/gif.latex?y_i=0), we have

![](http://latex.codecogs.com/gif.latex?L_i=1-s(z_i)=P(y=0|x_i))

We can unify y=1 and y=0 and rewrite the likelihood function as follows:

![](http://latex.codecogs.com/gif.latex?L=\\prod^{m}_{i=1}P(y=1|x_i)^{y_{i}}(1-P(y=1|x_{i}))^{1-y_{i}})
![](http://latex.codecogs.com/gif.latex?=\\prod^{m}_{i=1}s(z_i)^{y_{i}}(1-s(z_{i}))^{1-y_{i}})

Take the log for this likelihood function, we have

![](http://latex.codecogs.com/gif.latex?\\log L=\\sum^{m}_{i=1}y_{i} \\log s(z_i)+(1-y_{i}) \\log (1-s(z_i)))

Substitue with ![](http://latex.codecogs.com/gif.latex?z_i=w^{T} x_{i})

![](http://latex.codecogs.com/gif.latex?\\log L=\\sum^{m}_{i=1}y_{i} \\log s(w^{T} x_{i})+(1-y_{i}) \\log (1-s(w^{T} x_{i})))

A formula we can use: 

![](http://latex.codecogs.com/gif.latex?s'(z)=\\frac{d(\\frac{1}{1+e^{-z}})}{dz}=s(z)(1-s(z)))       (1)

For the log likelihhod function, take the derivative with respect to w:

![](http://latex.codecogs.com/gif.latex?\\frac{\\partial \\log L}{\\partial w})
![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i \\frac{s'(z_i)}{s(z_i)} \\frac{\\partial z_i}{\\partial w} +(1-y_i)\\frac{-s'(z_i)}{1-s(z_i)} \\frac{\\partial z_i}{\\partial w} ))

Use formula (1)

![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i (1-s(z_i)) \\frac{\\partial z_i}{\\partial w} +(1-y_i)(-s(z_i)) \\frac{\\partial z_i}{\\partial w} ))

We have ![](http://latex.codecogs.com/gif.latex?z_i=w^{T} x_{i}) and ![](http://latex.codecogs.com/gif.latex?\\frac{\\partial z_i}{\\partial w}=x_i)

![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i(1-s(z_i))-(1-y_i)s(z_i))x_i)


