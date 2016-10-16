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
$\Rightarrow p(\hat \theta - 1.96\sqrt{1/I\_n(\theta)} \leq \theta \leq \hat \theta + 1.96\sqrt{1/I\_n(\theta)})$