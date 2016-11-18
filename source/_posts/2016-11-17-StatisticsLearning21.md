---
title: Fundamental Statistics Learning Note(21)
date: 2016-11-17 00:41:27
tags:
 - Probability
categories: Statistics
---

> Maximum A Posterior

**Definition**: The maximum a posterior (MAP) estimate is the value $\theta$ that maximize $\pi(\theta | x\_1,\dots,x\_n)d\theta$.
<!---more--->
$Beta$ distribution has PDF, $f(x) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}x^{\alpha-1}(1-x)^{\beta-1}$, for $0\leq x\leq 1$, parameters $\alpha>0,\ \beta>0$. $Beta(\alpha,\beta)$ is commonly used prior for binomial probability.

e.g. Suppose the prior $Beta(3,6)$ can represent the fraction of canandians who can speak French as shown below.

And you meed 10 randomly selected canandians, and only the first person you met can speak french (so there is no ordering).
Given $x\_1,\dots,x\_n \overset{\text{iid}}\sim Bern(p)$, the likelihood function is $f(x\_1,\dots,x\_n|p)=p(1-p)^9$, $p\equiv$ probability a randomly selected canadian speaks French.

Using the prior $p\sim Beta(2,6)$, 
![](http://oc82vc8fw.bkt.clouddn.com/beta\_2\_6.png)
$$\begin{equation}\begin{split}
\pi(p|x\_1,\dots,x\_n) & \propto f(x\_1,\dots,x\_n)\pi(p) \\\\
& = p(1-p)^9\frac{\Gamma(2)\Gamma(6)}{\Gamma(8)}p^{2-1}(1-p)^{6-1} \\\\
& \propto p^2(1-p)^{14} 
\end{split}\end{equation}$$
Which has the form of $Beta(3,15)$.
**Note**: the posterior probability is proportional to the product of likelihood and prior probaility, then the constant can be placed outside.

Ex1 Beta-Binomial
prior probability: $p\sim Beta(\alpha,\beta)$; likelihood function: $x\sim Bin(n,p)$, suppose we observe $X=x$. Then posterior probability: 
$$\begin{equation}\begin{split}
\pi(p|x) & \propto \underbrace{f(x|p)}\_{\text{ likelihood }}\underbrace{\pi(p)}\_{\text{ prior }} \\\\
& = {n \choose x}p^x(1-p)^{n-x} \cdot \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}p^{\alpha-1}(1-p)^{\beta-1}\\\\
& \propto p^{\alpha+x-1}(1-p)^{n-x+\beta-1}
\end{split}\end{equation}$$

which has form of $Beta$ PDF.
Hence posterior probability: $\pi(p|x)=Beta(\alpha+\beta,\beta+n-x)$

Ex2 $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu,1)$. Suppose prior probability is $\mu \sim N(0,1)$.
a) Whatis the prior probability of $-1\leq \mu \leq 1$?
$$p(-1\leq \mu \leq 1)=\int\_{-1}^1\underbrace{\frac{1}{\sqrt{2\pi}}e^{-\mu^2/2}}\_{\text{prior probability of }\mu}d\mu\approx 0.68$$

b) Derive posterior $\mu|x\_1,\dots,x\_n$ (up to probable constant)
$$\begin{equation}\begin{split}
\pi(\mu|x\_1,\dots,x\_n) & \propto f(x\_1,\dots,x\_n|\mu)\pi(\mu) \\\\
& = \sum\_{i=1}^n\frac{1}{\sqrt{2\pi}}e^{-\frac{(x\_i-\mu)^2}{2}}\frac{1}{\sqrt{2\pi}}e^{-\frac{\mu^2}{2}} \\\\
& \propto = e^{-\frac{\sum (x\_i-\mu)^2}{2}}e^{-\frac{\mu^2}{2}}
\end{split}\end{equation}$$

c) Find MAP estimate of $\mu$
Let $g(\mu)=-\frac{\sum(x\_i-\mu)^2}{2}-\frac{\mu^2}{2}$ (log-posterior)
$g'(\mu)=\sum(x\_i-\mu)-\mu \overset{\text{set}}=0$
$\Rightarrow \sum x\_i -n\mu -\mu=0$
$\Rightarrow \sum x\_i=\mu(n+1)$
$\Rightarrow \text{MAP estimate is }\hat \mu = \frac{\sum x\_i}{n+1}$

d) Identify distribution of $\mu | x\_1,\dots, x\_n$
$$\begin{equation}\begin{split}
\pi(\mu|x\_1,\dots,x\_n) & \propto exp[-\frac{1}{2}(\sum x\_i^2-2\mu\sum x\_i+n\mu^2+\mu^2)] \\\\
& \propto exp[-\frac{1}{2}((n+1)\mu^2-2\mu\sum x\_i)] \\\\
& = e^{-\frac{1}{2/(n+1)}(\mu^2-\frac{2\mu\sum x\_i}{n+1})} \\\\
& \propto e^{-\frac{1}{2/(n+1)}[\mu-\frac{\sum x\_i}{n+1}]^2}
\end{split}\end{equation}$$
**Note**: $e^{(\frac{\sum x\_i}{n+1})^2}$ is a constant so we can leave it out here.
So we see that $\mu|x\_1,\dots,x\_n \sim N(\frac{\sum x\_i}{n+1},\frac{1}{n+1})$

e) posterior probability of $-1\leq \mu \leq 1$?
$p(-1\leq \mu \leq 1|x\_1,\dots,x\_n)=\int\_{-1}^1\frac{1}{\sqrt{2\pi}\sqrt{\frac{1}{n+1}}}e^{-\frac{1}{2/(n+1)}(\mu-\frac{\sum x\_i}{n+1})^2}d\mu$

**Note:**
 1. Need correct constant to calculate posterior probability (either identify distribution, or integrate the form of posterior to find constant to make a valid PDF)
 2. Posterior probability is a compromise between prior and likelihood.
    In nomal example, prior mean of $\mu$ is 0, (prior $\mu \sim N(0,1)$), MLE of $\mu$ is $\bar x$, posteriro mean of $\mu$ is $\frac{\sum x\_i}{n+1}$. **If we have more data, the posterior probability will more likely be towards MLE.**

