---
title: Foundamental Statistics Theory Notes (4)
date: 2016-09-07 15:05:20
tags:
 - Statistics
 - Probability
categories: 统计
---

> 忘了带鼠标，悲伤脸

Continue:
Let $x\_1,x\_2...,x\_n$ have $E(x\_i)=\mu, Var(x\_i)=\sigma^2$ and are independent with each other. <!---more--->
 1. $E(\bar {x}) = \mu$
 
 2. $Var(\bar x) = Var(\frac {x\_1+x\_2+...x\_n}{n})\overset{\text{indep}}{=} \frac {1}{n^2}\sum\_{i=1}^{n}Var(x\_i)=\frac{1}{n^2}\cdot n\sigma^2=\frac{\sigma^2}{n}$
 
 3. $S^2 = \frac{1}{n-1}\sum\_{i=1}^n(x\_i - \bar x)^2 = \frac{1}{n-1}\sum\_{i=1}^n(x\_{i}^2-2x\_i\bar x+\bar x^2)$
    $= \frac{1}{n-1}[\sum\_{i=1}^nx\_i^2-\sum\_{i=1}^{n}2x\_i\bar x+\sum\_{i=1}^n\bar x^2]$
    $=\frac{1}{n-1}[\sum\_{i=1}^n x\_i^2-2\bar x\sum\_{i=1}^nx\_i + n\bar x^2]$
    $=\frac{1}{n-1}[\sum\_{i=1}^n x\_i^2 - n\bar x^2]$, where $\sum\_{i=1}^{n}x\_i = n\bar x$

 4. $E(S^2) = \frac{1}{n-1}[\sum\_{i=1}^{n}E(x\_i^2)-nE(\bar x)^2]$
 $= \frac{1}{n-1}[n(\sigma^2+\mu^2)-n(\frac{\sigma^2}{n}+\mu^2)]$ 
where $E(x\_i^2) = Var(x\_i)+E(x\_i)^2,\ E(\bar x^2) = Var(\bar x) + E(\bar x)^2$

Random samples from a Normal Population
Let $x\_1, x\_2...x\_n \overset {\text{i.i.d}}{\sim} N(\mu,\sigma^2)$, then:
a. $\frac{x\_i-\mu}{\sigma}\sim N(0,1)$
b. $\bar x \sim N(\mu,\frac{\sigma^2}{n})$
c. $\frac{n-1}{\sigma^2}S^2 \sim \chi\_{n-1}^2$
d. $\bar x \ and\ S^2\ are\ independent $

Proof of a and b:

Proof of c:
$\sum\_{i=1}^{n}(x\_i - \mu)^2 = \sum\_{i=1}^{n}(x\_i - \bar x +\bar x - \mu)^2$
$= \sum\_{i=1}^{n}(x\_i - \bar x)^2 + 2\sum\_{i=1}^{n}(x\_i-\bar x)(\bar x - \mu) + \sum\_{i=1}^{n}(\bar x - \mu)^2$
$= \sum\_{i=1}^{n}(x\_i - \bar x)^2 + n(\bar x - \mu)^2$ 
where $\sum\_{i=1}^{n}(x\_i-\bar x)(\bar x - \mu) \Rightarrow (\bar x - \mu)\sum\_{i=1}^{n}(x\_i-\bar x) \Rightarrow (\bar x - \mu)\cdot 0$ 
beacsue $\sum\_{i=1}^{n}(x\_i-\bar x)\ is\ equal\ to\ \sum\_{i=1}^{n}x\_i-n\bar x\ which\ is\ zero. $
And we know $\sum\_{i=1}^{n}(x\_i - \bar x)^2 = (n-1) S^2$, so we just divide them by $\sigma^2$ to get:
$\sum\_{i=1}^{n}(\frac{(x\_i - \mu)}{\sigma})^2 = \frac{(n-1)S^2}{\sigma^2}+(\frac{\bar x -\mu}{\sigma \sqrt{n}})^2$ and we should notice $U\_i = \frac{x\_i - \mu}{\sigma} \sim N(0,1)$ and $\frac{\bar x - \mu}{\sigma/\sqrt{n}}\sim N(0,1)$
$\Rightarrow U\_i^2 \sim \chi\_1^2,\ \frac{\bar x - \mu}{\sigma/\sqrt{n}} \sim \chi\_1^2\ and\ \sum\_{i=1}^{n}U\_i^2 \sim \chi\_n^2$.
So, $S^2$ and $\bar x$ are independent, $\frac{(n-1)S^2}{\sigma^2}$ and $(\frac{\bar x -\mu}{\sigma/\sqrt{n}})^2$ are independent.

Note: $A = B + C,\ where A\sim \chi\_n^2, C\sim \chi\_1^2 \Rightarrow B \sim \chi\_{n-1}^2$ 