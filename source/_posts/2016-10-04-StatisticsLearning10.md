---
title: Foundamental Statistics Learning Note (10)
date: 2016-10-04 21:47:06
tags:
 - Probability
 - Statistics
categories: 统计
---

> Properties of Estimators

Let $\hat \theta$ be an estimator of $\theta$ :<!---more--->
 1. $Bias(\hat \theta) = E(\hat \theta)-\theta$
    - We say $\hat \theta$ is unbiased for estimation $\theta$ if the bias is 0 
 2. $Var(\hat \theta) = E[(\hat \theta-E(\hat \theta))^2]$
 3. Mean-Squared Error
    - $MSE(\hat \theta) = E[(\hat \theta - \theta)^2]$
    - **Note:** $MSE(\hat \theta) = Var(\hat \theta)\Leftrightarrow Bias(\hat \theta)=0$
$$\begin{equation}\begin{split}
MSE(\hat \theta)&=E[(\hat \theta - \theta)^2] \\\\
&=E[(\hat \theta - E(\hat \theta)+E(\hat \theta)-\theta)^2]\\\\
&=E[(\hat \theta-E(\hat \theta))^2]+E[2(\hat \theta-E(\hat \theta))\underbrace{(E(\hat \theta)-\hat \theta)}\_{\text{constant}}]+E[(E(\hat \theta)-\hat \theta)^2] \\\\
& = E[(\hat \theta-E(\hat \theta))^2]+2(E(\hat \theta)-\hat \theta))\underbrace{E(\hat \theta-E(\hat \theta))}\_{\underbrace{E(\hat \theta)-E(E(\hat \theta))}\_{\text{zero}}}]+\underbrace{E[(E(\hat \theta)-\hat \theta)^2]}\_{Bias(\hat \theta)}\\\\
&=Var(\hat \theta) + Bias(\hat \theta)^2
\end{split}\end{equation}$$
 4. Consistency
    - Let $\hat \theta\_n$ be estimator based on sample size $n$, we say that estimator is consistent if $\lim\_{n \to \infty}Bias(\hat \theta\_n)=0$ and $\lim\_{n \to \infty}Var(\hat \theta\_n)=0$.

---
Ex 1. $x\_1, x\_2, \dots, x\_n \overset{\text{i.i.d}}\sim N(\mu, \sigma^2)$. 
recall $MLE$ :  $\hat \mu = \bar x$, $\hat {\sigma^2} = \frac{n-1}{n}S^2$

To get $\hat \mu$: 
$$E(\mu)=E(\bar x)=\mu$$
so $\hat \mu$ is an unbiased estimator of $\mu$.
$$Var(\hat \mu)= Var(\bar x)=\frac{\sigma^2}{n}$$
so $$MSE(\hat \mu)=Var(\hat \theta)=\frac{\sigma^2}{n}$$
and it is consistent since $Bias=0$, $\lim\_{n \to \infty}\frac{\sigma^2}{n}=0$

To get $\hat \sigma^2$:
$$\begin{equation}\begin{split}
E(\hat \sigma^2)&=E(\frac{n-1}{n}S^2) \\\\
&=\frac{n-1}{n}E(S^2)\\\\
&=\frac{n-1}{n}\sigma^2
\end{split}\end{equation}$$

where $E(S^2) = \sigma^2$ in general.

$$\begin{equation}\begin{split}
Bias(\hat \sigma^2)&=E(\hat \sigma^2)-\sigma^2\\\\
&=-\frac{\sigma^2}{n}
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
Var(\hat \sigma^2)&=Var(\frac{n-1}{n}S^2) \\\\
&=Var(\frac{\sigma^2}{n}\cdot \frac{n-1}{\sigma^2}S^2) \\\\
&=\frac{\sigma^4}{n^2}\cdot 2(n-1)
\end{split}\end{equation}$$

where $\frac{(n-1)S^2}{\sigma^2}\sim \chi\_{n-1}^2$ and $Var(\chi\_{n-1}^2)=2(n-1)$

$$MSE(\hat \sigma^2)=\frac{\sigma^4}{n^2}\cdot 2(n-1) + \underbrace{\frac{\sigma^4}{n^2}}\_{Bias^2} $$

$\Rightarrow \hat \sigma^2$ is a constant estimator of $\sigma^2$ since $\lim\_{n \to \infty}-\frac{\sigma^2}{n}=0$ and $\lim\_{n \to \infty}\frac{2\sigma^4(n-1)}{n^2}=0$.

We can construct a function to eliminate the Bias of MLE, e.g. the estimator $\hat \sigma\_{\text{unbiased}}^2=S^2$ would be unbiased for estimating $\sigma^2$, **however, if we reduce the bias, the variance will increase and vice versa.**