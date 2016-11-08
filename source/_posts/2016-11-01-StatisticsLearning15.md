---
title: Fundamental Statistics Learning Note (15)
date: 2016-11-01 00:03:16
tags:
 - Probability
categories: Statistics
---

>Hypothesis testing

**Definition:** A hypothesis is a statement about a parameter
Goal: Decide which of 2 complementatry hypothesis is true based on data. <!---more--->
- $H\_O$: null hypothesis
- $H\_A$: alternate hypothesis
This setting originates from the experimental design.

**Definition:** A hypothesis test is a rule that specifies, (often) based on the value of a test statistics $W(x\_1,x\_n)$.
 a. when to accept $H\_O$ as true
 b. when to reject $H\_O$ and accpect $H\_A$
 
Ex. $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu,\sigma^2)$ where $\mu$ is unknown
a. $H\_O:\mu = 0$ vs $H\_A:\mu \neq 0$ is an example of 2 complementary hypothesis.

Here $\bar x$ gives information whihc hypothesis is true, so $\bar x$ would be  agood test statistics. Our hypothesis test is to reject $H\_O$ if $\bar x > c$ or $\bar x < -c$, for some constant $c >0 $.

b. $H\_O: \mu \geq 0 vs\ H\_A: \mu <0$. 

If we use $\bar x $ as test statistics, we would reject $H\_O\ if\ \bar x<-c\ for\ some\ c>0$.
 
**Definition:** The likelihood ratio (LR) test statistics for testing
$H\_O: \theta \in \Omega\_0$ vs $ H\_A: \theta \in \Omega\_1$, where $\Omega=\Omega\_0 \cup \Omega\_1$ is the parameter space of $\theta$ and $\Omega\_0 \cap \Phi\_1 = \Phi$ $$\lambda(x\_1,\dots,x\_n)=\frac{\max \limits\_{\theta \in \Omega\_0}L(\theta|x\_1,\dots,x\_n)}{\max \limits\_{\theta \in \Omega}L(\theta|x\_1,\dots,x\_n)}$$ 
**Note**: $0\leq\lambda\leq  1$, $\lambda \approx 1$ if true value of $\theta \in \Omega\_0$(ie: $H\_0$ is true); $\lambda \approx 0$ if $H\_0$ is false (since values $\theta \in \Omega\_0$ don't fit the data well). So accept $H\_0$ if $\lambda$ is close to 1, accept $H\_A$ if $\lambda$ if $\lambda$ close to $0$.

**Definition:** Let $w$ be a test statitiscs, suppose the hypothesis test is the rule "reject $H\_o$ if $w\in \mathbb{R}$", then $\mathbb{R}$ is called the *rejection region*.

Ex. The rejection region for a LR test is $\lbrace \lambda \leq c \rbrace$ from some $0<c<1$.
Ex. $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu,\sigma^2)$ with $\sigma^2$ known, $\mu$ is unknown parameter.
$$H\_O: \mu=\mu\_0, H\_A: \mu\neq \mu\_0$$
Derive LR test statistics $\lambda$.
$$\begin{equation}\begin{split}
L(\mu|x\_1,\dots,x\_n)&=\prod \limits\_{i=1}^n \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x\_i-\mu)^2}{2\sigma^2}} \\\\
&=\frac{1}{(2\pi)^{n/2}\sigma^{n}}e^{-\frac{\sum(x\_i-\mu)^2}{2\sigma^2}}
\end{split}\end{equation}$$
$$\begin{equation}\begin{split}
\lambda(x\_1,\dots,x\_n)&=\frac{\max \limits\_{\theta \in \Omega\_0}L(\theta|x\_1,\dots,x\_n)}{\max \limits\_{\theta \in \Omega}L(\theta|x\_1,\dots,x\_n)}\\\\
&=\frac{\max \limits\_{\mu=\mu\_0}L(\theta|x\_1,\dots,x\_n)}{\max \limits\_{\mu\in \mathbb{R}}L(\theta|x\_1,\dots,x\_n)} \\\\
& = \frac{\frac{1}{(2\pi)^{n/2}\sigma^{n}}e^{-\frac{\sum(x\_i-\mu\_0)^2}{2\sigma^2}}}{\frac{1}{(2\pi)^{n/2}\sigma^{n}}e^{-\frac{\sum(x\_i-\bar x)^2}{2\sigma^2}}} \\\\
& = \exp(-\frac{\sum(x\_i-\mu\_i)^2-\sum(x\_i-\bar x)^2}{2\sigma^2}) \\\\
& = \exp(-\frac{n}{2\sigma^2}(\bar x-\mu\_0)^2)
\end{split}\end{equation}$$
It should notice that $$\begin{equation}\begin{split}\sum(x\_i - \mu\_0)^2 &= \sum(x\_i - \bar x+\bar x-\mu\_0)^2 \\\\
& = \sum(x\_i-\bar x)^2 + 2\sum (x\_i-\bar x)(\bar x - \mu\_0)+\sum(\bar x-\mu\_0)^2 \\\\
&= \sum(x\_i - \bar x)^2 + n(\bar x - \mu\_0)^2
\end{split}\end{equation}$$

So the LR test rejects $H\_O$ if $$\begin{equation}\begin{split} &e^{-\frac{n}{2\sigma^2}(\bar x-\mu\_0)^2}  \leq C \\\\
&\Rightarrow -\frac{n}{2\sigma^2}(\bar x-\mu\_0)^2 \leq logC \\\\
&\Rightarrow (\bar x - \mu\_0)^2 \geq -\frac{2\sigma^2}{n}logC \\\\
&\Rightarrow \bar x -\mu\_0 \geq \sqrt{-\frac{2\sigma^2}{n}logC} \\\\
& or \ \ \bar x -\mu\_0 \leq \sqrt{-\frac{2\sigma^2}{n}logC} \\\\
&\Rightarrow \bar x \geq \mu\_0+\sqrt{-\frac{2\sigma^2}{n}logC} \\\\
& or \ \ \bar x \leq \mu\_0-\sqrt{-\frac{2\sigma^2}{n}logC}
\end{split}\end{equation}$$

Based on LR test, we reject $H\_O: \mu=\mu\_0$ if $\bar x$ is quite different than $\mu\_0$ (either larger or smaller)

**Definition:** $w$ is test statistics, $H\_O: \theta \in \Omega\_0$. A hypothesis test has level $\alpha$ if $\max \limits\_{\theta\in\Omega\_0} p(w\in \mathbb{R}|\theta)=\alpha$, where $\mathbb{R} $ the rejection region.

i.e. $\alpha=probability$ of rejecting $H\_O$ when $H\_O$ is true. $\alpha$ is also called type-I error rate.

Continue our example above:
Let $\mathbf{C}=-\sqrt{-\frac{2\sigma^2}{n}logC}$. What value of $\mathbf{C}$ achieves a level $\alpha$ test?
Ans: reject $H\_O$ if $\bar x\leq \mu\_0+\mathbf{C}$ or $\bar x \leq \mu\_0-\mathbf{C}$
If $H\_O$ is true, the $\mu=\mu\_0$ and so $\bar x\sim N(\mu, \frac{\sigma^2}{n})\Rightarrow \frac{\bar x-\mu\_0}{\sigma/\sqrt{n}}\sim N(0,1)$ under $H\_O$
$$\begin{equation}\begin{split}
\alpha &=\max \limits\_{\mu = \mu\_0}p(\bar x\geq \mu\_0+\mathbf{C}\ or\ \bar x\leq \mu\_0-\mathbf{C}) \\\\
&=p(\frac{\bar x-\mu\_0}{\sigma/\sqrt{n}} \geq \frac{\mathbf{C}}{\sigma/\sqrt{n}})+p(\frac{\bar x-\mu\_0}{\sigma/\sqrt{n}} \leq \frac{-\mathbf{C}}{\sigma/\sqrt{n}})
\end{split}\end{equation}$$where $\bar x \sim N(\mu,\frac{\sigma^2}{n})$
$\Rightarrow \frac{\mathbf{C}}{\sigma/\sqrt{n}}$ is the $1-\frac{\alpha}{2}$ quantile pf $N(0,1)$.
So the final rule to achieve $\alpha$ level test is reject $H\_O$ if $\frac{\bar x-\mu\_0}{\sigma/\sqrt{n}}\geq Z\_{1-\frac{\alpha}{2}}$ or $\frac{\bar x-\mu\_0}{\sigma/\sqrt{n}}\leq -Z\_{1-\frac{\alpha}{2}}$
$\Rightarrow |\frac{\bar x-\mu\_0}{\sigma/\sqrt{n}}|\geq Z\_{1-\frac{\alpha}{2}}$£¬ this is the one-sample z-test for a mean.

If $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu,\sigma^2)$ with both $\mu, \sigma^2$ unknown, the LR test for $H\_O:\mu=\mu\_0$ vs $H\_A:\mu\neq \mu\_0$ yields one-sample test. *HINT: in numerator of LR, we need $\max \limits\_{\mu=\mu\_0,\sigma^2>0}L(\mu,\sigma^2|x\_1,\dots,x\_n)$*

i.e. substitute $\mu=\mu\_0$, maximize w.r.t $\sigma^2$ alone.

Often, we would not know the exact distribution of LR test statistics $\lambda\_0$. The, we can use the large sample approximation.

Theory: $H\_O: \theta \in \Omega\_0, H\_A:\theta \in \Omega\_1, \Omega = \Omega\_0 \cup \Omega\_1$. $\lambda=$ LR test statistics based on $x\_1,\dots,x\_n$. When n is large: if $H\_O$ is true, then $$-2log\lambda\overset{\text{approx}}\sim \chi\_p^2$$ for any $\theta \in \Omega\_0$.
$p = dim(\Omega)-dim(\Omega\_0)$, i.e. difference in # free parameters.

LR test rejects $H\_O$ if $\lambda \leq C$, then $-2log\lambda \geq \underbrace{-2logC}\_{\mathbf{C}}$
and $\alpha = p(-2log\lambda \geq \mathbf(C))$ gives and approx level $\alpha$ test.
So the approx level $\alpha$ of LR test is reject $H\_O$ if $-2log\lambda\geq (1-\alpha)$ quantile of $\chi\_p^2$.