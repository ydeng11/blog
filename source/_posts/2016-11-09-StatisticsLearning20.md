---
title: Fundamental Statistics Learning Note(20)
date: 2016-11-09 21:47:47
tags:
 - Probability
categories: Statistics
---

>Bayes' rule revisited

How is $p(H\_O\text{ is true})$ related to $p(\text{reject } H\_O|H\_O\text{ is true})?$
Ans: According to Bayes' rule $$p(\text{reject } H\_O|H\_O\text{ is true}) = \frac{p(\text{reject } H\_O\cap H\_O\text{ is true})}{p(H\_O\text{ is true})} = \frac{p(H\_O\text{ is true}|\text{reject } H\_O)p(\text{reject } H\_O)}{p(H\_O\text{ is true})}$$
<!---more--->
**Limitations of classical (frequentist) statistics**
For illstration suppose we have the hypothesis is $H\_O: \theta \leq 1$. Then $p(H\_O\text{ is true})=p(\theta\leq 1)$. But it doesn't make sense as $\theta$ is not an random variable, it is an unknown constants. It is why we don't directly use classical $p(H\_O\text{ is true})$ and use **p-value** instead.

> Bayesian statistics

The Bayesian approach to statistical inference is to treat all unknown as random variable. This includes both the usual random variables $X\_1,X\_2,\dots,X\_n$ representing the data and the parameter(s) $\theta$. 
The probability like $p(\theta\leq 1)$ make sense and $p(H\_O\text{ is true})$ can be calculated in Bayesian statistical inference, which makes hypotehis testing more interpretable.

> Batesian inference

All unknows $X\_1,X\_2,\dots,X\_n$ (data) and $\theta$ (parameter) are random vairable, so they have a joint distribution.
$p(\theta, X\_1,X\_2,\dots,X\_n)$ is joint distribution of data and parameter.
$$p(\theta, X\_1,X\_2,\dots,X\_n) = \underbrace{f(X\_1,X\_2,\dots,X\_n|\theta)}\_{\text{likelihood function }}\underbrace{\pi(\theta)}\_{\underbrace{\text{prior}}\_{\text{before data}}}=\underbrace{\pi(\theta|X\_1,X\_2,\dots,X\_n)}\_{\underbrace{\text{posteiror}}\_{\text{after data}}}\underbrace{m(X\_1,X\_2,\dots,X\_n)}\_{\underbrace{\text{marginal distribution of data}}\_{\text{does not depend on }\theta\text{, ignore for estimating }\theta}}$$
Here $\pi$ is a classical statistical inference notation, $f$ and $m$ are just assumptive probability function.
$$\Rightarrow \pi(\theta|X\_1,X\_2,\dots,X\_n) = \frac{f(X\_1,X\_2,\dots,X\_n|\theta)\pi(\theta)}{m(X\_1,X\_2,\dots,X\_n)} \propto f(X\_1,X\_2,\dots,X\_n|\theta)\pi(\theta)$$