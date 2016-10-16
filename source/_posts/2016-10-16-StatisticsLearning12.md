---
title: Foundamental Statistics Learning Note (12)
date: 2016-10-12 15:38:00
tags:
 - Probability
 - Statistics
categories: 统计
---

> Working...

Recall: 
$$\begin{equation}\begin{split} 
& \hat\theta\_{MLE}\overset{\text{approx}}\sim N(\theta, \frac{1}{I\_n(\theta)}) \\\\
& i.e. Var(\hat \theta\_{MLE})\approx \frac{1}{I\_n(\theta)} \\\\
& \hat Var(\hat \theta\_{MLE}) = \frac{-1}{l''(\hat \theta\_{MLE})}
\end{split}\end{equation}$$ <!---more--->

Suppose $g(\theta)$ is a function of the parameter, by MLE invaiance property, $g(\theta)$ has MLE, $g(\hat \theta\_{MLE})$.
$$\begin{equation}\begin{split} 
& g(\hat\theta\_{MLE})\overset{\text{approx}}\sim N(g(\theta), \frac{[g'(\theta)]^2}{I\_n(\theta)}) \\\\
& Var(g(\hat\theta\_{MLE}))\approx \frac{[g'(\theta)]^2}{I\_n(\theta)} \\\\
& \hat Var(g(\hat\theta\_{MLE}))= -\frac{[g'(\hat \theta\_{MLE})]^2}{l''(\hat \theta\_{MLE})}
\end{split}\end{equation}$$

Ex. $x\_1,x\_2,\dots,x\_n \overset{\text{iid}}\sim Bern(p)$, recall MLE is $\hat p = \bar x$, what is MVUE of $p$?
Ans: It is $\bar x$ since $E(\bar x)=p$ and minimum sufficient statistics $\sum\_{i=1}^n x\_i$.
In this case, we know exactly $$Var(\hat p)= Var(\bar x)=\frac{p(1-p)}{n}$$
estimate by $$\hat Var(\hat p)= \frac{\hat p(1-\hat p)}{n}$$
Odds is $\frac{p}{1-p}$, the MLE of the odds is $\frac{\hat p}{1-\hat p} (invariance, g(p)=\frac{p}{1-p})$, however, $$ Var(\frac{\hat p}{1-\hat p}) = Var(\frac{\bar x}{1-\bar x})$$
is not known.

When n is large, $$\hat {Var}(\frac{\hat p}{1-\hat p})=-\frac{[g'(\hat p)]^2}{l''(\hat p)} $$
$$g'(p)=\frac{(1-p)+p}{(1-p)^2}=\frac{1}{(1-p)^2}$$
$$\begin{equation}\begin{split}
L(p|x\_1,x\_2,\dots,x\_n)&=\prod\_{i=1}^n p^{x\_i}(1-p)^{1-x\_i} \\\\
&=p^{\sum x\_i}(1-p)^{n-\sum x\_i}
\end{split}\end{equation}$$
$$l(p) = \sum x\_i logp+(n-\sum x\_i)log(1-p) $$
$$l'(p) = \frac{\sum x\_i}{p}-\frac{n-\sum x\_i}{1-p} $$
$$l''(p)=-\frac{\sum x\_i}{p^2} - \frac{n-\sum x\_i}{(1-p)^2} = -\frac{n\hat p}{p^2}-\frac{n-n\hat p}{(1-p)^2} $$

$$\begin{equation}\begin{split}
l''(\hat p) &= -\frac{n\hat p}{\hat p^2}-\frac{n(1-\hat p)}{(1- \hat p)^2} \\\\
&= -\frac{n}{\hat p}-\frac{n}{1-\hat p} \\\\
&= -\frac{-n}{\hat p(1-\hat p)}
\end{split}\end{equation}$$

$$\Rightarrow \hat {Var}(\frac{\hat p}{1-\hat p})=\frac{[\frac{1}{(1-\hat p)^2}]^2}{\frac{n}{\hat p(1-\hat p)}}=\frac{\hat p}{n(1-\hat p)^3}$$
This is approximate Var of the odds MLE when n is large.
