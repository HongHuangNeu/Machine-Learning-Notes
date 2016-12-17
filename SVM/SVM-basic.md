# Support Vector Machine : Basics

## VC-Dimension
Given a machine learning model, the VC-dimension of this model is the maximum number h in a p dimensional space such that this model can seperate h data points into two classes in all ![](http://latex.codecogs.com/gif.latex?2^h) possible ways.

## Complexity of Machine Learning Models

VC-dimension measures the complexity of a machine learning model. The higher the VC-demension is, the more complex the model is. More complex models are more capable to capture details in the data set.

## Generalization Performance of a Machine Learning Model

Given a machine learning model, with probability ![](http://latex.codecogs.com/gif.latex?1-\\eta) the following upper-bound holds:

![](http://latex.codecogs.com/gif.latex?\\varepsilon_{true}\\leq\\varepsilon_{A}+\\frac{\\varepsilon \(N\)}{2}\(1+\\sqrt{1+\\frac{\\varepsilon_{A}}{\\varepsilon \(N\)}} \))
