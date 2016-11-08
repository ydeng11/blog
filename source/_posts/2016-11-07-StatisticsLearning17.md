---
title: Fundamental Statistics Learning Note(17)
date: 2016-11-07 15:11:54
tags:
---

> Power function

Outcomes of hypothesis testing: <!---more--->
$$H\_O: \theta \in \Omega\_0\text{ vs }H\_A: \theta \in \Omega\_1$$
$$\begin{matrix}
& &  Decision \\\\
& & \text{Accept H\_O} & \text{Reject H\_O/Accept H\_A} \\\\
Truth & H\_O & \checkmark & \text{type I error} \\\\
      & H\_A & \text{type II error} & \checkmark
\end{matrix}$$

Let $W$ be a test statistics, and $R$ be the rejection region.

$$\underbrace{p(W\in \mathbb{R}|\theta)}\_{\text{probability reject } H\_O \text{ as a function of }\theta} = \begin{equation}
  \left\lbrace
   \begin{aligned}
   \text{probability type I error, if }\theta \in \Omega\_O  \\\\
   \text{probability type II error, if }\theta \in \Omega\_A   \\\\
   \end{aligned}
  \right.
\end{equation}$$

**Definition:** Given test statistics $W$ and rejection region $R$, the **power function** is $pow(\theta)=p(W\in R|\theta)$, So $\begin{matrix}\text{if }\theta \in \Omega\_0, \text{then ideally } pow(\theta) \text{ is close to } 0 \\
\text{if }\theta \in \Omega\_1, \text{then ideally } pow(\theta) \text{ is close to } 1
\end{matrix}$

E.X. Let $X\sim Bin(5,p). H\_O:p\leq 0.5 \text{ vs } H\_A:p>0.5$. Test statistcs: $W = X$. Derive $pow(p)$ for 2 cases:
(a) $R = \lbrace W=5\rbrace$; (b) $R = \lbrace W\geq 4\rbrace$
Ans: 
(a) $$\begin{matrix}\begin{split}pow(p) &= P(W=5|p) \\\\
&= p^5 \end{split}\end{matrix}$$
(b) $$\begin{matrix}\begin{split}pow(p) &= P(w\geq 4|p) \\\\
& = P(W=4) + P(W=5) \\\\
& = {5 \choose 4}p^4(1-p)+p^5
\end{split}\end{matrix}$$

![](http://oc82vc8fw.bkt.clouddn.com/statlearn16.png)

Rule(a) has smaller probability type I error if $p\leq 0.5$.
Rule(b) has smaller probability type II error if $p>0.5$

What is the probability of type I error if $p=0.6$?
Rule(a): $1-0.6^5 = 0.922$
Rule(b): $1-[{5 \choose 4}0.6^40.4+0.6^5] = 0.663$

What is the level $\alpha$ of the two rules?
Recall $\alpha = \max \limits\_{\theta \in \Omega\_0}p(W\in R|\theta)= \max \limits\_{\theta \in \Omega\_0} pow(\theta)$
Ans:
(a) $0.5^5 = 0.03125$
(b) ${5 \choose 4}0.5^5+0.5^5 = 0.1875$