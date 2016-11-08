---
title: Fundamental Statistics Theory Notes (1)
date: 2016-08-25 11:20:14
tags:
 - Probability
categories: Statistics
---

> 无根之木犹若浮萍

虽然不是统计学出身，但作为一只科研狗，还是从各处学习了很多。但以前过于偏重应用方面，对理论上的知识没有深刻理解。现在觉得还是学得过于肤浅了，因此准备重新补一下统计基础。先从概率论开始吧。<!---more--->

## 概率分布公式
Suppose y is a continuous random variable, which has a PDF (Probability distribution function) $f(y)$ and a CDF (Cumulative distribution function) $F(y)$ shown as below

$$P(a<=y<=b)=\int\_a^bf(y)dy$$

Generally 

$$\int\_{-\infty}^{+\infty}{f(y)dy}=1$$

For CDF, $F(y)$ is equal to $P(Y<=y) = \int\_{-\infty}^{y}f(t)dt$. If we differtiate the $F(y)$, we will get $f(y)$, the PDF, like $f(y) = \frac{d}{dy}F(y)$.

Example:
Suppose $z\sim N(0,1)$, $f(z) = \frac{1}{\sqrt{2\pi}}e^{\frac{-z^2}{2}}$, $z \epsilon R$.
Define $Y = |z|$, find PDF/CDF of Y.
**First Step: Identify the range**
$Y\geq0$
For any y greater than 0, $P(Y\leq y) = P(|z|\leq y) = P(-y\leq z\leq y) = \int\_{-y}^{y}\frac{1}{\sqrt{2\pi}}e^{\frac{-z^2}{2}}dz$
Define $\Phi(z) = $ CDF of $N(0,1) = \int\_{-\infty}^z\frac{1}{\sqrt{2\pi}}e^{\frac{-z^2}{2}}dz \Rightarrow \Phi(y) - \Phi(-y)$, which is the CDF of y for any y $\geq0$. 

**Second Step: Get derivative of CDF**
PDF of Y is $ f(y) = \frac{d}{dy} \left( \Phi(y) - \Phi(-y) \right) $
= $ \Phi'(y) + \Phi'(-y) $ 
= $\frac{1}{\sqrt{2\pi}} e^{\frac{(-y)^2}{2}}$ + $\frac{1}{\sqrt{2\pi}} e^{-{\frac{(-y)^2}{2}}} $
= $\frac{2}{\sqrt{2\pi}} e^{-\frac{y^2}{2}} $ for any y $\geq 0$


## 期望公式
For Y contains with PDF $f(y)$
$E(Y) = \int\_{-\infty}^{+\infty}yf(y)dy$ which is "expected value" or "mean".
$E(g(y)) = \int\_{-\infty}^{+\infty}g(y)f(y)dy$ 
Varince: $Var(Y) = E(Y^2) - E(Y]^2$

 - Expectations are linear: $E(a + bx + cy) = a + bE(x) + cE(y)$
 - When x, y are independent: $E[g(x)h(y)] = E[g(x)]E[h(y)]$
 -  $M\_y(t) = E[e^{ty}]$ is the MGF of Y. The MGF uniquely determines the destribution, i.e. if $M\_x(t) = M\_y(t)$ then $x$~$y$.

Example:
$x\sim Expo(\beta)$, which has MGF $M\_x(t) = \frac{1}{1-\beta t}$. Whta is the distribution of $Y=2x$?

The MGF of Y is $M\_y(t) = E[e^{ty}] = E[e^{t\cdot2x}] = E[e^{(2t)x}] = M\_x(2t) = \frac{1}{1-2\beta t}$, which is the MGF of $Expo(2\beta)$.

Since MGF determines the distribution, $Y\sim Expo[2\beta]$.

