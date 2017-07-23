---
title: Fundamental Statistics Learning Note(24)
date: 2016-12-16 22:21:05
tags:
 - Probability
categories: Statistics
---
> R Square

To test $H\_O: \beta\_1 = 0\text{ vs } H\_A:\beta\neq 0$, $W = \frac{\hat\beta}{S\_{reg}/\sqrt{\sum(x-\bar x)^2}}\sim t\_{n-2}$ if $H\_O$ is true.
reject $H\_O$ if $|W|>(1-\alpha/2)$ quantile of $t\_{n-2}$
<!---more--->
Recall $t\_p^2 \sim F\_{1,p} $
Define F-statistic for the regression as $F=\frac{\hat \beta^2}{S\_{reg}^2/\sum(x\_i-\bar x)^2}$, then $F\sim F\_{1,n-2}$ if $H\_O$ is true.

Def $\hat y\_1 = \hat \beta\_0 + \hat \beta\_1 x\_i$ are the fitted values. $r\_i = y\_i - \hat y\_i$ are the residuals (the difference between the true value and fitted value).
$\Rightarrow \sum(y\_i - \bar y)^2$ represents total variability in $y\_i's$ (sum of squares).

$$\begin{equation}\begin{split}
\underbrace{\sum(y\_i - \bar y)^2}\_{\text{SS(Total)}} & = \sum(y\_i - \hat y\_i + \hat y\_i - \bar y) \\
& = \underbrace{\sum(y\_i - \hat y\_i)^2}\_{\text{SS(residual)}} + \underbrace{\sum(\hat y\_i - \hat y)^2}\_{\text{SS(reg)}}
\end{split}\end{equation}
which is called ANOVA decomposition.

**Definition**
$R^2 = \frac{\sum(\hat y\_i - \bar y)^2}{\sum(y\_i - \bar y)^2}$, fraction of variability in $y\_i$ explained by the line.


