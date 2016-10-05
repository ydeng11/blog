---
title: Foundamental Statistics Theory Notes (5)
date: 2016-09-12 10:51:22
tags:
 - Statistics
 - Probability
categories: 统计
---

> t-distribution & F-distribution


### t-distrubition

Let $x\_1,x\_2...x\_3 \overset{\text{i.i.d}}{\sim} N(\mu, \sigma^2)$, $\frac{n-1}{\sigma^2}S^2 \sim \chi\_{n-1}^2,\ \frac{\bar x - \mu}{\sigma/\sqrt{n}} \sim N(0,1)$.
To construct CI for $\mu$, we usually don't now $\mu,\ \sigma$, so we substitute S for $\sigma$(intuitively make sense since $E(S^2) = \sigma^2$)<!---more--->
To get $\frac{\bar x - \mu}{S/\sqrt{n}}$, what is the distribution?
We can express $\frac{\bar x - \mu}{S/\sqrt{n}}$ as $\frac{({\bar x - \mu})/({\sigma/\sqrt{n}})}{({S/ \sqrt{n}})/({\sigma/\sqrt{n}})}$
$\Rightarrow \frac{({\bar x - \mu})/({\sigma/\sqrt{n}})}{\sqrt{S^2/ \sigma^2}} \sim N(0,1)$, it's very like $\chi^2$.
Given $\frac{\bar x - \mu}{\sigma/\sqrt{n}} \sim N(0,1)$,
$\Rightarrow \frac{\bar x - \mu}{S/\sqrt{n}} \sim \frac{U}{\sqrt{V/{n-1}}}$,
$where\ U\sim N(0,1),\ V\sim \chi\_{n-1}^2\ and\ they\ are\ independent\ since\ \bar x, S^2\ are\ independent.$

Definition: A r.v. T has students t-distribution with p d.f. denoted as $T \sim t\_p$, if $T \sim \frac{U}{\sqrt{V/P}}$ where $U \sim N(0,1),\ V \sim \chi\_p^2$ are independent.

PDF of $t\_p$:
Let $x \sim N(0,1),\ y\sim \chi\_p^2,$ define $U = \frac{x}{\sqrt{y/P}}, V = y$, inverses are $\ x = U\sqrt{\frac{V}{P}}, y=V$, where $x \in \mathbb{R}, y > 0$.
$\Rightarrow U\in \mathbb{R}, V > 0$,
$J = det\begin{bmatrix}
\sqrt{\frac{v}{P}} & ... \\\\
0 & 1
\end{bmatrix} = \sqrt{\frac{V}{P}}$

$f\_{U,V}(U,V) = f\_{x,y}(U\sqrt{\frac{V}{P}}, V)|\sqrt{\frac{V}{P}}|$
$= \frac{1}{\sqrt{2\pi}}e^{-(\mu\sqrt{\frac{V}{P}})^2/2}\cdot\frac{1}{\Gamma(\frac{P}{2})2^{P/2}}V^{\frac{P}{2}-1}e^{-\frac{V}{2}}\cdot \sqrt{\frac{V}{P}}$
since $x,\ y$ are independent, the marginal PDF of V is:
$f\_V(V) = \frac{1}{\sqrt{2\pi}}\frac{1}{\Gamma(\frac{P}{2})2^{P/2}}\frac{1}{\sqrt{P}}\int\_0^{\infty}e^{-\frac{U^2V}{2P}-\frac{V}{2}}V^{\frac{P}{2}-1}\cdot V^{\frac{1}{2}}dV$
$= \frac{1}{\sqrt{2\pi}}\frac{1}{\Gamma(\frac{P}{2})2^{P/2}}\frac{1}{\sqrt{P}}\int\_0^{\infty}e^{-V(\frac{1}{2}+\frac{\mu^2}{2P})}V^{\frac{P+1}{2}-1}$, the $e^{-V(\frac{1}{2}+\frac{U^2}{2P})}V^{\frac{P+1}{2}-1}$ is exactly Gamma density.

Gamma PDF with $\alpha,\ \beta$:
$\int\_0^{\infty}\frac{1}{\Gamma(\alpha)\beta^\alpha}x^{\alpha-1}e^{-x/\beta} = 1$
$\Rightarrow \int\_0^{\infty}x^{\alpha-1}e^{-x/\beta} = {\Gamma(\alpha)\beta^\alpha}$
so $f\_V(V) =  \frac{1}{\sqrt{2\pi}}\frac{1}{\Gamma(\frac{P}{2})2^{P/2}}\frac{1}{\sqrt{P}}\cdot {\Gamma(\frac{P+1}{2})(\frac{1}{\frac{1}{2}+\frac{U^2}{2p}})^{\frac{P+1}{2}}}$, where $\alpha = \frac{P+1}{2},\ \beta = (\frac{1}{\frac{1}{2}+\frac{U^2}{2p}})$.

### F-distribution
Let $x\_1,x\_2...x\_n \overset{\text{i.i.d}}{\sim} N(\mu\_{x}, \sigma\_{x}^2)$, and $y\_1,y\_2...y\_n \overset{\text{i.i.d}}{\sim} N(\mu\_{y}, \sigma\_{y}^2)$ and they are independent. Now we want to compute the variances $\frac{\sigma\_{x}^2}{\sigma\_{y}^2}$, using data the approximation is $\frac{S\_{x}^2}{S\_{y}^2}$.

Define A r.v. has an F distribution with p and q d.f. if it ca be represented by $\frac{U/p}{V/q}$, where $U \sim \chi\_p^2,\ V \sim \chi\_q^2$, and they are independent(Notation: $F\_{p,q}$).

What is the distribution of $\frac{S\_x^2/\sigma\_x^2}{S\_y^2/\sigma\_y^2}$, recall $\frac{(n-1)S^2}{\sigma^2}\sim \chi\_{n-1}^2$
$\Rightarrow \frac{S\_x^2/\sigma\_x^2}{S\_y^2/\sigma\_y^2} = (\frac{(n-1)S\_x^2}{\sigma\_x^2}\cdot \frac{1}{n-1})/(\frac{(m-1)S\_y^2}{\sigma\_y^2}\cdot \frac{1}{m-1}) = \frac{U/(n-1)}{V/(m-1)} \sim F\_{n-1,m-1}$, where $U \sim \chi\_{n-1}^2, V \sim \chi\_{m-1}^2$, they are independent as they originates from independent distribution.

Ex1. $x\_1,x\_2...x\_4 \overset{\text{i.i.d}}{\sim} N(0,1)$, what is the distribution of $\frac{3x\_1^2}{x\_2^2+x\_3^2+x\_4^2}$?
Suppose $U = x\_1^2 = \chi\_1^2,\ V = x\_2^2+x\_3^2+x\_4^2 = \chi\_3^2$, they are independent.
$\Rightarrow \frac{3U}{V} = \frac{U/1}{V/3} = \frac{\chi\_1^2/1}{\chi\_3^2/3} = F\_{1,3}$

Ex2. $x\_1, x\_2 \overset{\text{i.i.d}}{\sim} N(0,2)$, what is the distribution of $\frac{1}{2}(x\_1^2+x\_2^2)$?
As $\frac{x\_1}{\sqrt{2}}\sim N(0,1),\ \frac{x\_2}{\sqrt{2}}\sim N(0,1),\ \frac{1}{2}(2U^2+2V^2)=U^2+V^2 = \chi\_1^2+\chi\_1^2 = \chi\_2^2$, 
where $U = \frac{x\_1}{\sqrt{2}},\ V = \frac{x\_2}{\sqrt{2}}$.
