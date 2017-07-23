---
title: Fundamental Statistics Learning Note(23)
date: 2016-11-22 23:48:32
tags:
 - Probability
categories: Statistics
---
> Linear Regression

This chapter will talk about using MLE to estimate the parameters in linear regression. Though the most common way nowdays is to use least square. I think it can bridge the gap between probability and regression theoretically.
<!---more--->
Suppose we want to construct a regression model to simulate the relationship between the weight of moose and the size of its anteler.
Model: $y\_i\sim N(\beta\_0+\beta\_1x\_i,\sigma^2)$, where $y\_i$ is the weight of moose and $x\_i$ is the size of the anteler. Because $y\_i$ is dependent on $x\_i$, so $y\_i$ is indepedent.
First we get likelihood function:
$$\begin{equation}\begin{split}
L(\beta\_0,\beta\_1,\sigma^2|y\_1,\dots,y\_n) & = \prod\limits\_{i=1}^n \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{y\_i-(\beta\_0+\beta\_1x\_i)^2}{2\sigma^2}} \\\\
& = \frac{1}{\sigma^n (2\pi)^{\frac{n}{2}}}e^{-\frac{\sum(y\_i-\beta\_0-\beta\_1x\_i)^2}{2\sigma^2}}
\end{split}\end{equation}$$
Then get log-likelihood function
$$\begin{equation}\begin{split}
l(\beta\_0,\beta\_1,\sigma^2) & = -\frac{n}{2}log(\sigma^2)-\frac{n}{2}log(2\pi)-\frac{\sum(y\_i-\beta\_0-\beta\_1x\_i)^2}{2\sigma^2}
\end{split}\end{equation}$$
Take partial derivative and set partitals to 0
$$\begin{equation}\begin{split}
\frac{\partial l}{\partial \beta\_0} & = \sum 2(y\_i-\beta\_0-\beta\_1x\_i)(-1)\overset{\text{set}}=0 \\\\
& \Rightarrow \sum(y\_i-\beta\_0-\beta\_1x\_i)=0 \\\\
& \Rightarrow \sum y\_i-n\beta\_0-\beta\_1\sum x\_i = 0 \\\\
& \Rightarrow n\beta\_0 = \sum y\_i - \beta\_1\sum x\_i \\\\
& \Rightarrow \beta\_0 = \bar y - \beta\_1 \bar x
\end{split}\end{equation}$$
which is intercept.
$$\begin{equation}\begin{split}
\frac{\partial l}{\partial \beta\_1} & = \sum 2(y\_i-\bar y + \beta\_1\bar x+\beta\_1x\_i)(-1) \\\\
& = -\frac{1}{2\sigma^2}[\sum2\lbrace (y\_1-\bar y)-\beta\_1(x\_i-\bar x)\rbrace(x\_i-\bar x)(-1)] \overset{\text{set}}=0 \\\\
& \Rightarrow \sum[(y\_i-\bar y)(x\_i-\bar x)-\beta\_1\sum(x\_i-\bar x)^2=0 \\\\
& \Rightarrow \hat \beta\_1 = \frac{\sum(y\_i-\bar y)(x\_i-\bar x)}{\sum(x\_i-\bar x)^2}
\end{split}\end{equation}$$
which is slope.