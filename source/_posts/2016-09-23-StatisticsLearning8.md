---
title: Foundamental Statistics Theory Notes (8)
date: 2016-09-23 15:27:19
tags:
 - Statistics
 - Probability
categories: 统计
---

> MLE continued


**Definition:**
The MLE is the value $\theta$ that maximized the <!---more---> likelihood function $L(\theta|x\_1,x\_2...x\_n)$.
Denote estimate of $\theta$ by $\hat \theta$.

**Definition:**
The parameter space is the set of allowable values of the parameter $\theta$, which can be discrete or continuous.

Ex. Bin(n,p)
 - if n is unknown, n's parameter space is discrete, n=1,2...
 - if p is unknown, p's parameter space is continuous, $0\leq p \leq 1$

**Strategies to find MLE**
1. discrete parameter: try different values
2. continuous parameter, $\theta$: use calculus
    - usually easier to work with log of L, denoted by    $l(\theta)$, "log-likelihood", maximizing $l(\theta)$ is     same as maximizing $L(\theta)$, since log is a monotonous function.
    - check $\frac{dl}{d\theta}=0$, solve $\theta$, check     is $l''(\theta)<0$, max by 2nd derivative order.
    - check boundry points

Ex. $x\_1,x\_2...x\_n\overset{\text{i.i.d}}\sim Bern(p)$, parameter space: $0 \leq p \leq 1$
$L(p|x\_1,x\_2...x\_n)=f(x\_1,x\_2...x\_n|p)\overset{\text{i.i.d}}=\prod\_{i=1}^n f(x\_i|p)$
$= \prod\_{i=1}^n \underbrace {p^{x\_i}(1-p)^{1-x\_i}}\_{Bin(1,p), PMF} = p^{\sum x\_i}(1-p)^{n-\sum x\_i}$
$\Rightarrow L(0)=L(1)=0$, wherever $\sum x\_i\neq0$, $\sum x\_i \neq n$
**Transform to log-likelihood function**
$l(p) = logL(p)$
$l(p) = \sum x\_i \cdot log(p) + (n-\sum x\_i)log(1-p)$
$l'(p) = \frac{\sum x\_i}{p}+\frac{n-\sum x\_i}{1-p}(-1)\overset{\text{set}}=0$
$\Rightarrow \sum x\_i(1-p)-(n-\sum x\_i)p=0$
$\Rightarrow \sum x\_i - np = 0 $
$\Rightarrow p = \frac{\sum x\_i}{n}=\bar x$
check $l''(\bar x)<0$, so MLE is $$\underbrace{\hat p}\_{estimate\ of\ probability\ of\ success} = \underbrace{\bar x}\_{observed fraction of success}$$.

**German Tank Problems**
During WW2, allies want to know how many tanks the Germans were prodcuing, based on serial numbers of caputured tanks, fortunately, some parts were numbered sequentially.

Data: n serial numbers randoms selected from the list ${1,2,\dots,N}$
$N = number\ of\ tanks$ (parameter of interest), find out the likelihood function of N.
Let $x\_1,x\_2...x\_n$ be the serial number we observe
$L(N|x\_1,x\_2...x\_n) = f(x\_1,x\_2...x\_n|N)$
what does knowing $x\_1$ tell us about N?
$N \geq x\_1$, actually $N \geq max\lbrace x\_i \rbrace$

They are $\left(N \atop n \right)$ differnet combinations of n serial number, each equally likely, so liklihood function is
$$\frac{1}{\left(N \atop n \right)}, N \geq max\lbrace x\_i \rbrace$$
Note $\left(N \atop n \right)$ is increasing function of N when n is fixed.
To maximize $\frac{1}{\left(N \atop n \right)}$, we want smallest denominator.

**Sufficient Statistics**

$L(N|x\_1,x\_2...x\_n) = \underbrace{\frac{1}{\left(N \atop n \right)}I(N\geq max\lbrace x\_i \rbrace)}\_{g(max\lbrace x\_i \rbrace|\theta)}\cdot \underbrace{1}\_{h(x\_1,x\_2...x\_n}$
So $max\lbrace x\_i \rbrace$ is sufficient for N.

>Invariance Property of MLEs

If $\hat \theta$ is the MLE of $\theta$,  then for any 1-1 function $g$, the MLE of $g(\theta)$ is $g(\hat \theta)$

Ex. $x\_1,x\_2...x\_n \overset{\text{i.i.d}}\sim Expo(\beta)$, find MLE of $\underbrace{\beta}\_{mean}$ and $\underbrace{\beta^2}\_{variance}$

Parameter space: $\beta > 0$
$L(\beta|x\_1,x\_2...x\_n)=f(x\_1,x\_2...x\_n|\beta)\overset{\text{i.i.d}}=\sum\_{i=1}^nf(x\_i|\beta)$
$=\prod\_{i=1}^n\frac{1}{\beta}e^{-\frac{x\_i}{\beta}}=\frac{1}{\beta^n}e^{-\frac{\sum x\_i}{\beta}}$
$\Rightarrow l'(\beta)=-\frac{n}{\beta}+\frac{\sum x\_i}{\beta^2}\overset{\text{set}}=0$
$\Rightarrow -n\beta + \sum x\_i = 0$
$\Rightarrow \beta = \frac{\sum x\_i}{n} = \bar x$
remember to verify that $l''(\bar x) < 0$, so we have a max MLE , $\hat \beta = \bar x$. By the **invariance property**, the MLE of $\beta ^2$ is $\bar x^2$.