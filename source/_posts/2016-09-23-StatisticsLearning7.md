---
title: Fundamental Statistics Theory Notes (7)
date: 2016-09-23 10:25:39
tags:
 - Probability
categories: Statistics
---

> Estimating parameters from a random sample

<!---more--->
Recall for a random sample $x\_1, x\_2...x\_n i.i.d$ from a PMF/PDF, $f(x)$, the joint PMF/PDF can be written:
$f(x\_1,x\_2...x\_n)=\prod\_{i=1}^nf(x\_i)$
Usually, $f(x)$ will depend on some unknown parameter,$s$, like $\theta$.
Notation: $f(x|\theta)$, $\theta$ can be unkown mean or variance.

**Goal: Construct estimators for** $\theta$ **based on** $x\_1, x\_2...x\_n$.

Definition:
Let $f(x\_1,x\_2...x\_n)$ denote the joint PMF/PDF of $x\_1,x\_2...x\_n$. The given observed data $X\_1 =x\_1, X\_2 = x\_2...X\_n=x\_n$, the likelihood function (as a function of $\theta$) is $L(\theta|x\_1,x\_2...x\_n)=f(x\_1,x\_2...x\_n|\theta)$, if they are i.i.d, the function is also equal to $\prod\_{i=1}^nf(x\_i|\theta).$

Ex. Gators won 3 games of 3. Let x denote # wins. Assume $x\sim Bin(3,p)$. p is the unknown parameter to be estimated from the data.
$$f(x|p)=\left(3\atop p \right)p^x (1-p)^{3-x},\ for\ x=0,1,2,3$$
Data:
$x=3 \Rightarrow L(p|x=3)=\left(3\atop 3\right)p^3(1-p)^{3-3}=p^3$, as a function of p, $0\leq p\leq 1$.

This tell us the probability of data (3 wins) for different value of p.
e.g. $\underbrace {L(\frac{1}{2}|x=3)}\_{1/8}<\underbrace{L(\frac{3}{4}|x=3)}\_{27/64}$, then $p=\frac{3}{4}$seems more plausible than $p=\frac{1}{2}$.
In this case, $p=1$ maximized the likelihood function.

**Definition:**
The maximum likelihood estimate (MLE) is the value of $\theta$ that maximized $L(\theta|x\_1,x\_2...x\_n)$.
**Interpretation:**
The MLE of $\theta$ is the value $\theta$ that make the observed data the most likely to occur.