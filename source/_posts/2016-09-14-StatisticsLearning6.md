---
title: Fundamental Statistics Theory Notes (6)
date: 2016-09-14 14:53:59
tags:
 - Probability
categories: Statistics
---

> Central Limit Theorem (CLT)

CLT workd for i.i.d sample from "most" distribution.
<!---more--->
Let $x\_1,x\_2...x\_n$ be i.i.d from any distribution, where $M\_x(t)$ exists. Denote $E(x\_i) = \mu\ and\ Var(x\_i) = \sigma^2$. Let $\bar x\_n = \frac{1}{n}\sum\_{i=1}^{n}x\_i\ and\ U = \frac{\bar x\_n - \mu}{\sigma/\sqrt{n}}$.
Then $U \Rightarrow N(0,1)\ as\ n\rightarrow \infty$. This means the PDF of U will approximate standard normal distribution when n is efficiently large.

Proof:
Let $y\_i = \frac{x\_i-\mu}{\sigma},\ then\ E(y\_i) = 0,\ Var(y\_i) = E(y\_i^2) = 1,\ and\ U = \frac{1}{\sqrt{n}}\sum\_{i=1}{n}y\_i$
$\Rightarrow$ MGF of U is then $M\_u(t) = E(e^{tU}) = E[e^{ty\_1/\sqrt{n}+ty\_2/\sqrt{n}...+ty\_n/\sqrt{n}}]$
$=E[e^{ty\_1/\sqrt{n}}]E[e^{ty\_2/\sqrt{n}}]...E[e^{ty\_n/\sqrt{n}}]$
$=M\_{y\_1}(t/\sqrt{n})M\_{y\_2}(t/\sqrt{n})...M\_{y\_n}(t/\sqrt{n})$
$=[M\_y(t/\sqrt{n})]^n$



**(from Taylor expand around t=0)**
$= 1  +E(y\_i)\frac{t}{\sqrt{n}}+E(y\_i^2)\frac{t^2}{2n}+R$
$= 1 + 0 + \frac{t^2}{2n}+R$
$= M\_u(t) = [1+\frac{t^2}{2}\cdot \frac{1}{n}+R]^n$
$\Rightarrow M\_y(t/ {\sqrt{n}}) = M\_y(0)\frac {(t/ \sqrt{n})^0}{0!}+M\_y'(0)\frac{(t/ \sqrt{n})^1}{1!}+M\_y''(0)\frac{(t/ \sqrt{n})^2}{2!}+R$

**Recall** 
$$\lim \limits\_{n \rightarrow \infty}(1+\frac{x}{n})^2 = e^x$$

$\Rightarrow \lim \limits\_{n \rightarrow \infty}M\_u(t) = \lim \limits\_{n \rightarrow \infty}[1+\frac{t^2}{2}\frac{1}{n}+R]^n = e^{t^2/2}$
$\Rightarrow$ this is the MGF of $N(0,1)$.

$\Rightarrow$ MGF of U $\rightarrow MGF\ of\ N(0,1)$, since MGF uniquely determines the distribution, $U \rightarrow N(0,1)$.

Ex. Let $x\_1,x\_2...x\_n \overset {\text{i.i.d}}{\sim} Bernouli(p)$, whihc is equal $Binomial(1,p)$.
$E(x\_i) = p,\ Var(x\_i)=p(1-p)$
By CLT, when n is large
$\Rightarrow \frac{\bar x - p}{\sqrt{p(1-p)}/ \sqrt{n}} \overset{\text{arrpox}}{\sim}N(0,1)$
or $\bar x \overset{\text{arrpox}}{\sim} N(p, \frac{p(1-p)}{n})$
or $\sum\_{i=1}^{n}x\_i\overset{\text{arrpox}}{\sim}N(np, np(1-p))$
and $\sum\_{i=1}^{n}x\_i \sim Binomial(n,p)$ which is the **exact** distribution.