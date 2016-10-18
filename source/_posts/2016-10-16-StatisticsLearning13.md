---
title: Foundamental Statistics Learning Note (13)
date: 2016-10-16 16:58:12
tags:
 - Probability
 - Statistics
categories: 统计
---

> Confidential Interval

<!---more--->

 - $theta$ parameter, $x\_1,x\_2,\dots,x\_n$ are data 
 - An interval $(a,b)$ is a $1-\alpha$ confidence interval (CI) for $\theta$ 
   * if $p(a\leq \theta \leq b)\geq 1-\alpha$, $a$ and $b$ are function of data.

Two ways to construct CI:
 1. Approximate CIs based on MLE (large $n$)
   - Suppose $\hat \theta$ is the MLE, then
      * $\hat \theta \overset{\text{approx}}\sim N(\theta, \frac{1}{I\_n(\theta)})$
      * g(\hat \theta) \overset{\text{approx}}\sim N(g(\theta), \frac{[g'(\theta)]^2}{I\_n(\theta)})

Hence, $\frac{\hat \theta - \theta}{\sqrt{1/I\_n(\theta)}} \overset{\text{approx}}\sim N(0,1)$, $P(-1.96 \leq \frac{\hat \theta - \theta}{\sqrt{1/I\_n(\theta)}} \leq 1.96) = 0.95$
Equivalently, $\frac{\hat \theta - \theta}{\sqrt{1/I\_n(\theta)}} \geq -1.96 \Rightarrow \hat \theta - \theta \geq -1.96\sqrt{1/I\_n (\theta)} \Rightarrow \theta \leq \hat \theta + 1.96\sqrt{1/I\_n(\theta)}$
$\Rightarrow p(\hat \theta - 1.96\sqrt{1/I\_n(\theta)} \leq \theta \leq \hat \theta + 1.96\sqrt{1/I\_n(\theta)})$ is an approximate $95\%$ CI for $\hat \theta(MLE)$ when $n$ is large, this can also be written as $\hat \theta \stackrel{+}-1.96\sqrt{-\frac{[g(\hat \theta)]^2}{l''(\hat \theta)}}$.

For binomial odds, $\frac{p}{1-p}$, $\hat Var(\frac{\hat p}{1-\hat p})=\frac{\hat p}{n(1-\hat p)^3}$, so approximate $95\%$ CI of the odds is $\frac{\hat p}{1-\hat p}\stackrel{+}-1.96\sqrt{\frac{\hat p}{n(1-\hat p)^3}}$.

2. Exact CIs based on pivots
Definition: A pivot is a function, $Q(\theta, x\_1,x\_2,\dots,x\_n)$ whose distribution does not depend on $\theta$.

Ex. $x\sim N(\mu, \sigma^)$ with unknown $\mu$ and $\sigma^2$, given $\frac{x-\mu}{\sigma}\sim N(0,1))$, then $Q(\mu, x\_1,x\_2,\dots,x\_n)=\frac{x-\mu}{\sigma}$ is a pivot.

Ex. $x\_1,x\_2,\dots,x\_n \overset{\text{iid}}\sim N(\mu,1)$ with unknown $\mu$, given $\bar x \sim N(\mu, \frac{1}{N})$, then $Q(\mu, x\_1,x\_2,\dots,x\_n)=\frac{\bar x-\mu}{\sqrt{1/N}}$ is a pivot.

Ex. $x\_1,x\_2,\dots,x\_n \overset{\text{iid}}\sim N(0,\sigma^2)$, then $Q(\mu, x\_1,x\_2,\dots,x\_n)=\frac{(n-1)S^2}{\sigma^2}\sim \chi\_{n-1}^2$ is a pivot.

*How to make CIs from pivots?*
1. Find/show $Q(\mu, x\_1,x\_2,\dots,x\_n)$ is a pivot
2. Find $a\_1$, $a\_2$ to satisfy $p(a\_1\leq Q(\mu, x\_1,x\_2,\dots,x\_n) \leq a\_2) = 1-\alpha \leftarrow$ Confidence level
3. Rearrange to form $a\leq \theta \leq b$

Ex $x\_1 \sim Expo(\beta)$, a) shown that $Q = \frac{x}{\beta}$ is a pivot, b) use the 0.025 and 0.975 quantiles of $Q$ to construct an exact $95\%$ CI for $\beta$.

a) $p(Q\leq q)=p(\frac{x\_1}{\beta}\leq q)=p(x\_1\leq q\beta)=\int\_0^{q\beta}\frac{1}{\beta}e^{-x/\beta}dx = 1-e^{-\frac{q\beta}{\beta}}=1-e^{-q}$
so $Q$ is a pivot as the CDF doesn't depend on $\beta$.
$Q$ has PDF, $f(q)=\frac{d}{dq}(1-e^{-q})=e^{-q}$ for $q$, so $ Q\sim Expo(1)$.

b) p(a\_1\leq Q \leq a\_2)=0.95
Here, the 0.025 quantiles satisfies $0.025 = \int\_0^{a\_1}e^{-q}dq = 1-e^{-a\_1}\Rightarrow a\_1 = -log(0.975) = 0.0253$
he 0.975 quantiles satisfies $0.975 = \int\_0^{a\_1}e^{-q}dq = 1-e^{-a\_2}\Rightarrow a\_2 = -log(0.025) = 3.69$
so $p(0.0253\leq \frac{x\_1}{\beta} \leq 3.69)=0.95$
$\Rightarrow p(\frac{x\_1}{3.69}\leq \beta \frac{x\_1}{0.0253})=0.95$
$\Rightarrow CI = (\frac{x\_1}{3.69}, \frac{x\_1}{0.0253})$