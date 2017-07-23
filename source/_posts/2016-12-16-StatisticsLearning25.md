---
title: Fundatmental Statistics Learning Note(End)
date: 2016-12-16 22:54:52
tags:
 - Probability
categories: Statistics
---
> Some Exercises

Let $x\_1,\dots,x\_n \overset{\text{iid}}\sim N(\mu\_x,1)$, $y\_1,\dots,y\_n \overset{\text{iid}}\sim N(\mu\_y,1)$, and both are independent.
Derive LR test for $H\_O:\mu\_x=\mu\_y \text{ vs } H\_A:\mu\_x\neq\mu\_y$. <
<!---more--->
$$\begin{equation}\begin{split}
L(\mu\_x,\mu\_y|x\_1,\dots,x\_n,y\_1,\dots,y\_n) & = f(x\_1,\dots,x\_n,y\_1,\dots,y\_n|\mu\_x,\mu\_y) \\
& \overset{\text{indep}}=\prod\_{i=1}^nf(x\_i|\mu)\prod\_{j=1}^m f(y\_j|\mu\_y) \\
& = \prod\_{i=1}^{n}\frac{1}{\sqrt{2\pi}}e^{-\frac{(x\_i-\mu\_x)^2}{2}}\cdot  \prod\_{i=1}^{n}\frac{1}{\sqrt{2\pi}}e^{-\frac{(y\_i-\mu\_y)^2}{2}}
\end{split}\end{equation}$$
$\Rightarrow (\frac{1}{2\pi})^{\frac{m+n}{2}}e^{-\frac{\sum(x\_i-\mu\_x)^2}{2}}e^{-\frac{\sum(y\_i - \mu\_y)^2}{2}}$

$x\_1,\dots,x\_n,y\_1,\dots,y\_n \overset{\text{iid}}\sim N(\bar \mu, 1)$. all $x,y$ are iid with same unknown mean, so maximized by $\hat \mu = \frac{\sum x\_i + \sum y\_i}{n+m}$ (Overall average)

$$\begin{equation}\begin{split}
LR & = \frac{\max\limits\_{\mu\_x=\mu\_y}L(\mu\_x,\mu\_y|\mathbf{x},\mathbf{y})}{\max\limits\_{\mu\_x,\mu\_y}L(\mu\_x,\mu\_y|\mathbf{x},\mathbf{y})} \\
& = \frac{(\frac{1}{2\pi})^{\frac{m+n}{2}}e^{-\frac{\sum(x\_i-\hat x)^2}{2}}e^{-\frac{\sum(y\_i - \hat y)^2}{2}}}{(\frac{1}{2\pi})^{\frac{m+n}{2}}e^{-\frac{\sum(x\_i-\bar x)^2}{2}}e^{-\frac{\sum(y\_i - \bar y)^2}{2}}}
\end{split}\end{equation}$$
where $\hat \mu\_x = \bar x, \hat \mu\_y = \bar y$.

To get approx LR test, $-2logLR \overset{\text{approx}}\sim \chi\_{2-1}^2$, reject $H\_O$ if $-2logLR > (1-\alpha)$ quantile of $\chi\_1^2$

Let $x$ has PDF $f(x|\theta)=\frac{2x}{\theta^2}, 1<x<\theta$. $\theta$ is unknown parameter, $\theta>0$
Set prior $\pi(\theta) \propto \frac{1}{\theta^2}$, derive posterior PDF pf $\theta|x$
$\pi(\theta|x)\propto \underbrace{\frac{2x}{\theta^2}I(\theta>x)}\_{\text{likelihood}}\cdot \underbrace{\frac{1}{\theta^2}}\_{\text{prior}} = \frac{2x}{\theta^2}I(\theta>x)$

$\Rightarrow \int\_x^{\infty}\frac{2x}{\theta^2}d\theta = -\frac{2x}{\theta^2}|\_x^\infty = \frac{2}{3x^2}$
Hence, the valid PDF is $\pi(\theta|x) = \frac{3x^2}{2}\cdot \frac{2x}{\theta^2}I(\theta>x)\overset{\text{set}}=1$