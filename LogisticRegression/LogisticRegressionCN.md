# 逻辑回归
## 思想

给定一个线性的判别函数:

![](http://latex.codecogs.com/gif.latex?z=w^{T} x)

在逻辑回归中，我们想要把 z 映射到区间 [0,1]. 这样，得到的数值就可以作为属于一个类的后验概率。

一个 sigmoid 函数 可以用来把 z 映射成概率:

![](http://latex.codecogs.com/gif.latex?s(z)=\\frac{1}{1+e^{z}}), 其中 ![](http://latex.codecogs.com/gif.latex?z\\in (- \\infty,+\\infty))

## 求解最优的 w

假设有一个二类的分类问题，类标签分别是0和1。

给定x，它属于1类的概率是

![](http://latex.codecogs.com/gif.latex?P(y=1|x)=\\frac{1}{1+e^{w^{T} x}}=s(w^{T} x))

则他属于0类的概率是

![](http://latex.codecogs.com/gif.latex?P(y=0|x)=1-P(y=1|x)=1-s(w^{T} x))

假设我们有m个训练点：

![](http://latex.codecogs.com/gif.latex?x_1, x_2,...,x_m)

我们想要找到一个w， 使他满足:

如果 ![](http://latex.codecogs.com/gif.latex?x_i) 属于1类，则![](http://latex.codecogs.com/gif.latex?P(y=1|x)) 越大越好(尽可能靠近1).

如果 ![](http://latex.codecogs.com/gif.latex?x_i) 属于0类，则![](http://latex.codecogs.com/gif.latex?P(y=0|x)) 越大越好 (尽可能靠近1).

假设

![](http://latex.codecogs.com/gif.latex?x_1, x_2,...,x_k) 属于1类

![](http://latex.codecogs.com/gif.latex?x_{k+1}, x_{k+2},...,x_m) 属于0类

构造以下似然函数:

![](http://latex.codecogs.com/gif.latex?L=\\prod_{l=1}^{k}P(y=1|x_{l})\\prod_{l=k+1}^{m}P(y=0|x_{l}))

为了方便, 对于训练集中的每个训练点 ![](http://latex.codecogs.com/gif.latex?x_i)， 我们可以构造： 

![](http://latex.codecogs.com/gif.latex?L_i =(S(z_i))^{y_{i}}(1-S(z_i))^{1-y_{i}})

这样，如果![](http://latex.codecogs.com/gif.latex?x_i) 属于1类，则![](http://latex.codecogs.com/gif.latex?y_i=1), 从而有

![](http://latex.codecogs.com/gif.latex?L_i=s(z_i)=P(y=1|x_i))

如果![](http://latex.codecogs.com/gif.latex?x_i) 属于0类，则 ![](http://latex.codecogs.com/gif.latex?y_i=0), 从而有

![](http://latex.codecogs.com/gif.latex?L_i=1-s(z_i)=P(y=0|x_i))

我们可以统一 y=1 和 y=0 两种情形，把似然函数改写成以下形式:

![](http://latex.codecogs.com/gif.latex?L=\\prod^{m}_{i=1}P(y=1|x_i)^{y_{i}}(1-P(y=1|x_{i}))^{1-y_{i}})
![](http://latex.codecogs.com/gif.latex?=\\prod^{m}_{i=1}s(z_i)^{y_{i}}(1-s(z_{i}))^{1-y_{i}})

两边取log，得到：

![](http://latex.codecogs.com/gif.latex?\\log L=\\sum^{m}_{i=1}y_{i} \\log s(z_i)+(1-y_{i}) \\log (1-s(z_i)))

代入 ![](http://latex.codecogs.com/gif.latex?z_i=w^{T} x_{i})

![](http://latex.codecogs.com/gif.latex?\\log L=\\sum^{m}_{i=1}y_{i} \\log s(w^{T} x_{i})+(1-y_{i}) \\log (1-s(w^{T} x_{i})))

我们可以用以下求导公式

![](http://latex.codecogs.com/gif.latex?s'(z)=\\frac{d(\\frac{1}{1+e^{-z}})}{dz}=s(z)(1-s(z)))       (1)

把这个log似然函数对w求偏导数:

![](http://latex.codecogs.com/gif.latex?\\frac{\\partial \\log L}{\\partial w})
![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i \\frac{s'(z_i)}{s(z_i)} \\frac{\\partial z_i}{\\partial w} +(1-y_i)\\frac{-s'(z_i)}{1-s(z_i)} \\frac{\\partial z_i}{\\partial w} ))

用 (1)

![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i (1-s(z_i)) \\frac{\\partial z_i}{\\partial w} +(1-y_i)(-s(z_i)) \\frac{\\partial z_i}{\\partial w} ))

得到 ![](http://latex.codecogs.com/gif.latex?z_i=w^{T} x_{i}) 和 ![](http://latex.codecogs.com/gif.latex?\\frac{\\partial z_i}{\\partial w}=x_i)

![](http://latex.codecogs.com/gif.latex?=\\sum^{m}_{i=1}(y_i(1-s(z_i))-(1-y_i)s(z_i))x_i)

如果 ![](http://latex.codecogs.com/gif.latex?x_{i}) 属于 1类:

![](http://latex.codecogs.com/gif.latex?y_i(1-s(z_i))-(1-y_i)s(z_i))
![](http://latex.codecogs.com/gif.latex?=1-s(z_i)=y_i-s(w^{T} x))

如果 ![](http://latex.codecogs.com/gif.latex?x_{i}) 属于0类:

![](http://latex.codecogs.com/gif.latex?y_i(1-s(z_i))-(1-y_i)s(z_i))
![](http://latex.codecogs.com/gif.latex?=-s(z_i)=y_i-s(w^{T} x))

所以得到

![](http://latex.codecogs.com/gif.latex?\\frac{\\partial \\log L}{\\partial w}=\\sum^{m}_{i=1}(y_i-s(w^{x_i}))x_i)


我们就可以用这个结果通过梯度上升求最大似然估计对应的w:

![](http://latex.codecogs.com/gif.latex?w:=w+\\alpha \\frac{\\partial \\log L}{\\partial w})

![](http://latex.codecogs.com/gif.latex?=w+\\alpha(\\sum^{m}_{i=1}(y_i-s(w^{T} x_i))x_i)) 


## 实现

下面给出我用ipython notebook演示的逻辑回归的实现的链接：

[用ipython notebook实现逻辑回归的链接](http://nbviewer.jupyter.org/github/HongHuangNeu/Machine-Learning-Notes/blob/try/LogisticRegression/LogisticRegressionCN.ipynb)
