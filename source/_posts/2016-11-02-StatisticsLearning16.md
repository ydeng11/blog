---
title: Fundamental Statistics Learning Note(16)
date: 2016-11-02 18:41:14
tags:
 - Probability
categories: Statistics
---

> LR-test continued

Continued:
If LR test statistics $\lambda$ has an unknown distribution, we use large-sample approximate LR test.
Reject $H\_O$ if $-2log\lambda \geq (1-\alpha)$ quantile of $\chi\_p^2$, where $p$ is difference in # free parameters(between $\Omega\_0\ and\ \Omega\_0 \cup \Omega\_1$)
<!---more--->
Ex. $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu\_x,\sigma\_x^2), y\_1,\dots,y\_n \overset{\text{iid}}\sim N(\mu\_y,\sigma\_y^2)$, what is the value of p for the approximate LR test?
$$\begin{matrix}
H\_O:\mu\_x=\mu\_y=0, \sigma\_x^2=\sigma\_y^2=1\text{ vs } H\_A:otherwise && p = 4-0 \\\\
H\_O:\mu\_x=\mu\_y=0 \text{ vs } H\_A:otherwise && p = 4-2 \\\\
H\_O:\mu\_x=\mu\_y \text{ vs } H\_A:\mu\_x\neq\mu\_y && p = 4-3
\end{matrix}$$

Ex. $x\_1,\dots,x\_n \overset{\text{iid}}\sim Pois(\theta)$. Derive approximate LR test for $H\_O:\theta=\theta\_0$ vs $H\_A:\theta \neq \theta\_0$(when n is large)

$$\begin{equation}\begin{split}
L(\theta|x\_1,\dots,x\_n)& = \prod \limits\_{i=1}^n e^{-\theta}\frac{\theta^{x\_i}}{x\_i!} \\\\
& = e^{-n\theta}\frac{\theta^{\sum x\_i}}{\prod x\_i!}
\end{split}\end{equation}$$
Then LR test $\lambda$ is:
$$\begin{equation}\begin{split}
\lambda&= \frac{\max\limits\_{\theta=\theta\_0}L(\theta|x\_1,\dots,x\_n)}{\underbrace{\max\limits\_{\theta>0}L(\theta|x\_1,\dots,x\_n)}\_{\text{MLE is }\hat \theta = \bar x}} \\\\
&=\frac{e^{-n\theta\_0}\theta\_0^{\sum x\_i}/\prod x\_i!}{e^{-n\bar x}\bar x^{\sum x\_i}/\prod x\_i!} \\\\
& = \underbrace{e^{-n\theta\_0+n\bar x}(\frac{\theta\_0}{\bar x})^{n\bar x}}\_{\text{is actually a value given data}}
\end{split}\end{equation}$$
Though we can't easily tell the distribution of $\lambda$, so approximate $-2log\lambda \overset{\text{approximate}}\sim \chi\_1^2$.
Then approximate LR test: reject $H\_O$ if $-2log\lambda \geq (1-\alpha)\text{ quantile of }\chi\_1^2$

>p-values

**Defnition:** Let $W$ be a test statistics for $H\_O: \theta \in \Omega\_0$.
Data: $ \widetilde{X} = X\_1,\dots,X\_n$ and observed value $\tilde{x} = x\_1,\dots,x\_n$. 
If $W$ is larger when $H\_O$ is false: p-value=$\max\limits\_{\theta\in\Omega\_0}P(W(\widetilde{X})\geq W(\tilde{x})|\theta)$
If $W$ is smaller when $H\_O$ is false: p-value=$\max\limits\_{\theta\in\Omega\_0}P(W(\widetilde{X})\leq W(\tilde{x})|\theta)$
*Note*: $\widetilde{X}$ is random variable and $\tilde{x}$ is observed value.

E.X. $x\_1,\dots,x\_n \overset{\text{iid}}\sim Bern(p). H\_O: p\leq0.4\text{ vs }H\_A: p\geq 0.4$.
$W=\sum \limits\_{i=1}^4 X\_i$ is test statistics. 
Suppose data: $x\_1=x\_2=x\_3=1, x\_4=0$, what is the p-value?
$E(W)=4p$, $W$ is larger when $H\_O$ is false. 
$$\Rightarrow W\sim Bin(4,p)$$
$$\begin{equation}\begin{split}
\text{p-value}&=\max\limits\_{p\leq 0.4}[p(W=3)+P(W=4)] \\\\
&=\max\limits\_{p\leq 0.4}[{4 \choose 3}p^3(1-p)^1+{4\choose4}p^4(1-p)^0] \\\\
&=4(0.4)^3(0.6)+0.4^4=0.1792
\end{split}\end{equation}$$
**Note**: when $p=0.4$, this makes data most likely in the parameter space ($p\leq 0.4$).