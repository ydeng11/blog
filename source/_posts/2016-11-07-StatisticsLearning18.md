---
title: Fundamental Statistics Learning Note(18)
date: 2016-11-08 01:07:19
tags:
 - Probability
categories: Statistics
---

> Classical hypothesis testing workflow

I am going to summarize the workflow of hypothesis testing including LR test, $\alpha$ level and p-value.
<!---more--->
1. Scientific context determines $H\_O, H\_A$
2. Determine test statistics $W$ (LR test is commonly used)
3. Scientist set an acceptable type I error rate ($\alpha$-level)
4. We use that to set rejection region $R$ to achieve $\alpha=\max\limits\_{\theta\in\Omega\_0}p(W\in R|\theta)$
5. power analysis: does the test have a high probability to reject $H\_O$ when $H\_A$ is true? i.e. Calculate $pow(\theta)$ for $\theta\in\Omega\_O$
6. Calculate p-value once we have data (smallest level $\alpha$ at which $H\_O$ would be rejected)

E.X. $X\sim Expo(\beta), H\_O:\beta\leq 1\text{ vs }H\_A:\beta >1$, test statistics $W=X$.
(a). Determine rejection region $R$ for a level $\alpha=0.05$ test. Since $E(W)=\beta$, reject $H\_O$.

$$\begin{equation}\begin{split}
\alpha = 0.05 & = \max \limits\_{\beta\leq 1} p(W\geq C) \\\\
& = \max\limits\_{\beta\leq 1}\int\_c^\infty \frac{1}{\beta}e^{-X/\beta}dx \\\\
& =\max \limits\_{\beta\leq 1}e^{-C/\beta}=e^{-C}
\end{split}\end{equation}$$

Note: $C$ denotes how large is $W$ for rejecting $H\_O$?

So $C=-log(0.05)=2.995 \Rightarrow R=\lbrace W\geq 2.995\rbrace$, i.e. to achieve 0.05 level test, reject $H\_O$ if $W\geq 2.995$

(b). For MLE in (a), plot power function.
![](http://oc82vc8fw.bkt.clouddn.com/statlearn16-2.png)
$pow(\beta)=p(W\geq 2.995 |\beta)=e^{\frac{-2.995}{\beta}} $

e.g. if $\beta=10$, we will correctly reject $H\_O$ with probability $e^{\frac{-2.995}{10}}\approx0.74$

(c). We observe the value $X=5$. Calculate p-value.
$\text{p-value}=\max\limits\_{\beta\leq 1}p(W\geq 5)=\max \limits\_{\beta \leq 1}e^{-5/\beta}=e^{-5}\approx 0.0067$
We would reject $H\_O$ at 0.05 level, and also at any level $\alpha\geq 0.0067$