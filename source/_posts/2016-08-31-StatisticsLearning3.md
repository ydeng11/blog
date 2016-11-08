---
title: Fundamental Statistics Theory Notes (3)
date: 2016-08-31 15:44:17
tags:
 - Probability
categories: Statistics
---

> Statistics is the function of everything.



### Variance & Covariance
<!---more--->
 1. $E(a+by+cz)=a+bE(y)+cE(z)$
 2. $Var(a+by+cz)=b^2Var(y)+c^2Var(z)+2bc\cdot Cov(y,z)$
 3. $Var(\sum\_{i=1}^{n}a\_i y\_i) = \sum\_{i=1}^{n}a\_i^2Var(y\_i)+2\sum\_{i<j} a\_i a\_jCov(y\_i,y\_j)$
 4. $Cov(aU+bV,cX+dY)=acCov(U,X)+adCov(U,Y)+bcCov(V,X)+bdCov(V,Y)$
 5. $Cov(\sum\_{i=1}^{n}a\_ix\_i,\sum\_{i=1}^{n}b\_iy\_i)=\sum\_{i=1}^{m}\sum\_{j=1}^{n}a\_ib\_jCov(x\_i,y\_i)$
### Random Sample
Define the r.v's $y\_1,y\_2...y\_n$ are a random sample of size n, if they are all independent and have the same distribution (PMF/PDF), i.e. they are "independent and identically distributed" (iid).

Example 1: 
Suppose $y\_1, y\_2...y\_n\overset{\text{iid}}{\sim}Expo(\beta)$, the joint density $f(y\_1,y\_2...y\_n)\overset{\text{indep}}{=}f\_{y\_1}(y\_1)f\_{y\_2}(y\_2)...f\_{y\_n}(y\_n)$
$=\frac{1}{\beta}e^{-\frac{y\_1}{\beta}}\frac{1}{\beta}e^{-\frac{y\_2}{\beta}}...\frac{1}{\beta}e^{-\frac{y\_n}{\beta}}$
$=\frac{1}{\beta ^n}e^{-\frac{\sum\_{i=1}^{n}y\_i}{\beta}}, y\_i>0\ for\ i=1,2...n$

Define a statistic is a function of the random sample $y\_1...y\_n$, so a statistic is also a r.v with a distribution, means, variances, etc.

Distribution of statistics are called "sampling distributions."

Example 2: 
Sample mean $\bar Y = \frac{y\_1+y\_2+...y\_n}{n}$, sample variances $S^2 = \frac{1}{n-1}\sum\_{i=1}^{n}(y\_i-\bar y)^2$, sample standard deviation (SD) is $S = \sqrt{S^2}$.

Properties: let $x\_1,x\_2...x\_n$ be r.v's with $E(x\_i) = \mu, Var(x\_i)=\sigma ^2$

 1. $E(\bar X)=E(\frac{x\_1+x\_2+...x\_n}{n})=\frac{1}{n}[E(x\_1)+...+E(x\_n)]=\frac{1}{n}\cdot n\mu = \mu$
