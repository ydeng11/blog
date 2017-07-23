---
title: Fundamental Statistics Learning Note(22)
date: 2016-11-22 23:48:28
tags:
 - Probability
categories: Statistics
---

Rcall posterior is a compromise between prior and likelihood
i.e. Bayesian analysis provides framework to update posterior based on data/evidence (e.x. college football rankings)
<!---more--->
> Bayesian Hypothesis Testing

Consider $H\_O: \theta \in \Omega\_0 \text{ vs } \theta \in \Omega\_1$
Since $\theta$ is a r.v under Bayesian inference:
 - the prior probability that $H\_O$ is true is $P(\theta\in \Omega\_O)$, calculated using $\pi(\theta)$.
 - the posteriro probability that $H\_O$ is true is $P(\theta\in \Omega\_O|x\_1,\dots,x\_n)$, calculated using $\pi(\theta|x\_1,\dots,x\_n)$.

**Definition**: The **Bayes factor** in favour of $H\_O$ is determined by $$\underbrace{\frac{P(\theta\in\Omega\_0|x\_1,\dots,x\_n)}{P(\theta\in\Omega\_1|x\_1,\dots,x\_n)}}\_{\text{posterior odds that }H\_O\text{ is true}}=\underbrace{\frac{P(\theta\in \Omega\_0)}{P(\theta\in\Omega\_1)}}\_{\text{prior odds that }H\_O\text{ is true}}\times \text{Bayes Factor}$$

**Intepretation**:
$$\begin{matrix}
\text{B.F }\geq 1 & \text{data support }H\_O \\\\
\text{B.F }< 1   & \text{data support }H\_A
\end{matrix}$$
Ex. $x\_1,\dots,x\_n \overset{\text{iid}}\sim Bern(p)$. $H\_O: p\leq 0.5\text{ vs }H\_A: p>0.5$. Suppose prior on $p$ is $p\sim Beta(1,2)$.
(a) prior probability $H\_O$ is true?
$$\begin{equation}\begin{split}
P(p\leq 0.5)=\int\_0^{0.5}\pi(p)dp &=\int\_0^{0.5}\frac{\Gamma(3)}{\Gamma(1)\Gamma(2)}p^{1-1}(1-p)^{2-1}dp \\\\
&=\int\_0^{0.5}2(1-p)dp \\\\
&=2p-p^2|\_0^{0.5} \\\\
&=1-0.5^2 \\\\
&=0.75
\end{split}\end{equation}$$

(b) Observe 5 successes out of 5, what is the posterior probability $H\_O$ is true?
Given $\pi(\theta|x\_1,\dots,x\_n) \sim Beta(1+5,2+0)$ from last chapter.
$$\begin{equation}\begin{split}
P(p\leq 0.5) &= \int\_0^{0.5}\frac{\Gamma(8)}{\Gamma(6)\Gamma(2)}p^{6-1}(1-p)^{2-1}dp \\\\
&=\int\_0^{0.5}42p^5(1-p)^1dp \\\\
&=42[\frac{p^6}{6}-\frac{p^7}{7}]|\_0^{0.5} \\\\
&=0.0625
\end{split}\end{equation}$$

(c) prior odds $H\_O$ is true?
$\frac{0.75}{1-0.75}=3$

(d) posterior odds $H\_O$ is true?
$\frac{0.0625}{1-0.0625}=0.0667$

(e) Bayes factor
$0.0667=3\times B.F$
$\Rightarrow B.F = 0.0222 \ll 1$
Data strongly supports $H\_A: p>0.5$