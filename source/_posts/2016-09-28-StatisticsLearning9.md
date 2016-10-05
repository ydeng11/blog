---
title: Foundatmental Statistics Theory Notes (9)
date: 2016-09-28 17:36:12
tags:
 - Probability
 - Statistics
categories: 统计
---


> Sufficient Statistics

Def $x\_1,x\_2,\dots,x\_n$ are r.v's, and $\theta$ is unknown parameter. The function $T(x\_1,x\_2,\dots,x\_n)$ is a sufficient statistics for $\theta$. If the conditonal distribution of $x\_1,x\_2,\dots,x\_n$ given<!---more---> $T(x\_1,x\_2,\dots,x\_n)$ does not depend on $\theta$.

To estimate $\theta$, $T(x\_1,x\_2,\dots,x\_n)$ captures all the information about $\theta$ in the sample. Estimation of $\theta$ only depends on $x\_1,x\_2,\dots,x\_n$ through $T(x\_1,x\_2,\dots,x\_n)$.

**How to check that a statistic is sufficient**
> Factorization theorem

Let $f(x\_1,x\_2,\dots,x\_n|\theta)$ be the joint PDF/PMF.
$T(x\_1,x\_2,\dots,x\_n)$ is sufficient for $\theta \Leftrightarrow f(x\_1,x\_2,\dots,x\_n|\theta)$ can be factored into $g(T(x\_1,x\_2,\dots,x\_n)|\theta)h(x\_1,x\_2,\dots,x\_n)$

Definition:
Let I denote the **indicator function.**
$  f(n) =
\begin{cases}
1,  & \text{if $A$ true} \\\\
0,  & \text{otherwise}
\end{cases}$

Ex1. $x\_1,x\_2,\dots,x\_n \overset{\text{i.i.d}}\sim Expo(\beta)$ 
$L(\beta|x\_1,x\_2,\dots,x\_n)= \frac{1}{\beta^n}e^{-\frac{\sum x\_i}{\beta}} \cdot I(\beta > 0)$ 
*$I(\beta > 0)$ capture bounds on parameter space*
$ =\underbrace {\frac{1}{\beta^n}e^{-\frac{\sum x\_i}{\beta}}I(\beta > 0)}\_{g(\sum x\_i|\beta)} \cdot \underbrace{1}\_{h(x\_1,x\_2,\dots,x\_n)}$
As $g$ takes care of everything, $\sum x\_i$ is sufficient for $\beta$ by factorization theorem.

Ex2. Suppose $x\_1,x\_2,\dots,x\_n$ are iid with PDF, $f(x|\theta) = e^{-(x-\theta)},\ \theta \in \mathbb{R}, x > \theta$, find sufficient statistics for $\theta$.
Joint density $f(x\_1,x\_2,\dots,x\_n|\theta) = \prod\_{i=1}^nf(x\_i|\theta)=\prod\_{i=1}^ne^{-(x\_i - \theta)}$
$=e^{-\sum x\_i}e^{n\theta}\cdot I(x<min\lbrace x\_i \rbrace) \Leftarrow \theta < min\lbrace x\_i \rbrace$
$=\underbrace{e^{n\theta}I(x<min\lbrace x\_i\rbrace)}\_{g(min\lbrace x\_i\rbrace |\theta)}\cdot \underbrace{e^{-\sum x\_i}}\_{h(x\_1,x\_2,\dots,x\_n)}$
So $min\lbrace x\_i\rbrace$ is sufficient for $\theta$.

Ex3. $x\_1,x\_2,\dots,x\_n \overset{\text{i.i.d}}\sim Gamma(\alpha, \beta)$, where $\alpha$, $\beta$ are unknown, find sufficient statistics for $\alpha$, $\beta$.

$\begin{equation}\begin{split}
 f(x\_1,x\_2,\dots,x\_n|\alpha, \beta) & = \prod\_{i=1}^{n}\frac{1}{\beta^{\alpha}\Gamma (\alpha)}x\_i^{\alpha-1}e^{-x\_i/\beta} \\\\ 
& =\underbrace{\frac{1}{\beta^{nx}(\Gamma(\alpha))^n}(\prod\_{i=1}{n}x\_i)^{\alpha-1}e^{-\sum x\_i /\beta}I(\alpha>0)I(\beta>0)}\_{g(\prod x\_i, \sum x\_i, \alpha, \beta)}\cdot \underbrace{1}\_{h(x\_1,x\_2,\dots,x\_n)}
\end{split}\end{equation}$

So, $\sum x\_i$, $\prod x\_i$ are sufficient for $\alpha$, $\beta$.



**Note:**
**1. Sufficient statistics cannot contain unknown parameters.**
**2. $x\_1,x\_2,\dots,x\_n$ is always a (trivial) sufficient statistics.**

> Minimal Sufficiency : Use the fewest statistics if possible (apply factorization theorem to identify them)

We can also find MLEs for multiple unknown parameters by maximizing L over their entire parameter space (however, harder to verify it's a maximul MLE)

Ex4. $x\_1,x\_2,\dots,x\_n \overset{\text{i.i.d}}\sim N(\mu, \sigma^2)$, where $\mu$, $\sigma$ are unknown.
$\begin{equation}\begin{split}
L(\mu, \sigma^2|x\_1,x\_2,\dots,x\_n) &=f(x\_1,x\_2,\dots,x\_n|\mu, \sigma^2) \\\\
& = \prod\_{i=1}^n \frac{1}{\sigma \sqrt{2\pi}}e^{-\frac{(x\_i-\mu)^2}{2\sigma^2}} \\\\
&=\frac{1}{(\sigma^2 2\pi)^{n/2}}e^{-\frac{\sum (x\_i-\mu)^2}{2\sigma^2}},\mu \in \mathbb{R}, \sigma^2 >0
\end{split}\end{equation}$
$l(\mu, \sigma^2)=-\frac{n}{2}log(\sigma^2)-\frac{n}{2}log(2\pi)-\frac{\sum(x\_i-\mu)^2}{2\sigma^2}$
For more than one parameter, we would set $\frac{\alpha l}{\alpha \theta}=0$ for each parameter.

$\begin{equation}\begin{split}
\frac{\alpha l}{\alpha \mu} &=-\frac{1}{2\sigma^2}\sum 2(x\_i-\mu)(-1) \\\\
&=\frac{1}{2\sigma^2}\sum(x\_i-\mu)\overset{\text{set}}=0
\end{split}\end{equation}$
$\Rightarrow \sum(x\_i - \mu)=\sum x\_i-n\mu=0$
$\Rightarrow \mu=\frac{\sum x\_i}{n} = \bar x$

$\begin{equation}\begin{split}
\frac{\alpha l}{\alpha \sigma^2} &=-\frac{1}{2}\frac{1}{\sigma^2}-(\frac{\sum(x\_i-\mu)^2}{2})(-\frac{1}{\sigma^4})\\\\
&=-\frac{n}{2\sigma^2}+\frac{1}{2\sigma^4}\sum(x\_i-\mu)^2\overset{\text{set}}=0
\end{split}\end{equation}$
$\Rightarrow -n\sigma^2 + \sum(x\_i-\mu)^2=0$
$\Rightarrow \sigma^2 = \frac{\sum (x\_i-\mu)^2}{n}$

To satisfy both equations, the MLE are: 
$\hat \mu = \bar x$ 
$\hat \sigma^2 = \frac{1}{n}(x\_i-\mu)^2=\frac{n-1}{n}S^2$

**Verification:**
Recall: 

$\begin{equation}\begin{split}
\sum(x\_i-\mu)^2& = \sum(x\_i - \bar x +\bar x-\mu)^2\\\\
&=\sum(x\_i-\bar x)^2 + \sum (\bar x - \mu)^2 +\underbrace{2\sum(x\_i-\bar x)(\bar x -\mu)}\_0 \\\\
&=(n-1)S^2 + n(\bar x-\mu)^2
\end{split}\end{equation}$

So the joint PDF is equal to:
$f(x\_1,x\_2,\dots,x\_n|\mu, \sigma^2)=\underbrace{\frac{1}{(\sigma^2 2\pi)^{n/2}}e^{-\frac{1}{2\sigma^2}[(n-1)S^2+n(\bar x-\mu)^2]I(\sigma^2>0)}}\_{g(\bar x, S^2|\mu, \sigma^2)}\cdot \underbrace{1}\_{h(x\_1,x\_2,\dots,x\_n)}$