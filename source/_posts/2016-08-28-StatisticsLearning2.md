---
title: Fundamental Statistics Theory Notes (2)
date: 2016-08-26 17:54:48
tags:
 - Probability
categories: Statistics
---

> ¼ÌÐø´ò×®

### MGF(Moment Generating Function)

<!---more--->
Example 1:
Let $y\_1 ... y\_2$ be independent $Expo(\beta)\ r.v\ 's$. What is the dirstribution of $x = ay\_1+ay\_2+...ay\_n$?
Answer: 
MGF of x is $M\_x(t) = E[e^ {(tx)}] = E[e^{t(ay\_1+ay\_2+...ay\_n)}]$ 
$= E[e^{tay\_1}e^{tay\_2}...e^{tay\_n}] \overset{ {\text{indep}}}{=} E[e^{tay\_1}]E[e^{tay\_2}]...E[e^{tay\_n}]$
$= M\_{y\_{1}}(at)M\_{y\_{2}}(at)...M\_{y\_{n}}(at)$
$= (\frac{1}{1-\beta at})^n$
This is the MGF of $Gamma(n, \beta a)$
$\Rightarrow x \sim Gamma(n, \beta a)$ since MGF determines the distribution.

Example 2:
Let $f(x,y) $be the joint PDF for r.v.s X and Y, then the marginal PDF of x is $F\_x(x) = \int\_{-\infty}^{+\infty}f(x,y)dy$;  the marginal PDF of y is $F\_y(y) = \int\_{-\infty}^{+\infty}f(x,y)dx$.

 - If x and y are independent, then $f(x,y) = f\_x(x)\cdot f\_y(y)$
 - If a joint density F(x,y) can be factored so that $f(x,y) = g(x)h(y)$, then x, y are independet and $g(x)\ and\ h(y)$are only function of x and y respectively.

### Bivariate transformation
Suppose x, y are joint continuous with joint PDF $f\_{x,y}(x,y)$, consider a 1-1, onto transformation, $U = g\_1(x,y),\ V = g\_2(x,y)$, with the **inverse** transformation, we can find:
$$X = h\_1(U,V)$$
$$Y = h\_2(U,V)$$
Then we need to get the jacobian of the transformation:
$$
J = det\begin{bmatrix}
\frac{\alpha x}{\alpha U} & \frac{\alpha x}{\alpha V} \\\\
\frac{\alpha y}{\alpha U} & \frac{\alpha y}{\alpha V}
\end{bmatrix}
= \frac{\alpha x}{\alpha U} \frac{\alpha y}{\alpha V} - \frac{\alpha x}{\alpha V} \frac{\alpha y}{\alpha U}$$ 
Therefore, $f\_{U,V}(U,V) = f\_{x,y}(h\_1(U,V), h\_2(U,V))|J|$ for all (U,V) where $f\_{x,y}(x,y) > 0$.

Example 1: 
Let X, Y be independent $N\sim (0,1)$. Define $U = x+y,\ V=x-y$. Find joint PDF of U and V.
Joint PDF: $f\_{x,y}(x,y)\overset {\text{indep}}{=} \frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}} \frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}$, where $x \in \mathbb{R},\ y\in \mathbb{R}$.
The inverse transformation are:
$$U+V=2x\Rightarrow x=\frac{U+V}{2}=h\_1(U,V)$$
$$U-V=2y\Rightarrow y=\frac{U-V}{2}=h\_2(U,V)$$
$$
\Rightarrow J = def \begin{bmatrix}
\frac{1}{2} & \frac{1}{2} \\\\
\frac{1}{2} & -\frac{1}{2}
\end{bmatrix}
$$
Then $f\_{U,V}(U,V) = f\_{x,y}{(\frac{U+V}{2},\frac{U-V}{2})}\cdot {\frac{1}{2}}$
$=\frac{1}{\sqrt {2\pi }}e^{-({\frac {U+V}{2}})^2/2}\cdot \frac{1}{\sqrt{2\pi}}e^{-({\frac{U-V}{2}})^2/2}\cdot\frac{1}{2}$
$= \frac{1}{4\pi}e^{-\frac{(U+V)^2}{8}-\frac{(U-V)^2}{8}} = \frac{1}{4\pi}exp(-\frac{1}{8}(U^2+2UV+V^2+U^2-2UV+V^2))$
$=\frac{1}{4\pi}e^{-\frac{1}{4}(U^2+V^2)} = \frac{1}{4\pi}e^{-\frac{U^2}{4}}e^{-\frac{V^2}{4}}$
$= \frac{1}{\sqrt{2\pi}\sqrt{2}}e^{-\frac{U^2}{4}}\cdot \frac{1}{\sqrt{2\pi}\sqrt{2}}e^{-\frac{V^2}{4}}$
$\Rightarrow $ then the joint PDF of U, V factors into g(U)h(V), so U,V are independent and are N(0,2).

Example 2: 
Let $x \sim N(0,1)$, and $y\sim |Z|$ where $Z\sim N(0,1) $ and x, y are independent. Define $U = \frac{x}{y}, V = y, f\_x(x) = \frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}, x \in \mathbb{R}; f\_y(y) = \frac{2}{\sqrt{2\pi}}e^{\frac{-y^2}{2}} for\ y > 0$.
So x, y have joint PDF $f\_{x,y}(x,y)\overset{\text{indep}}{=}\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}\frac{2}{\sqrt{2\pi}}e^{\frac{-y^2}{2}}, x\in \mathbb{R}, y > 0.$
Range of transformation $U\in \mathbb{R}, V > 0$.
Get the inverse transformation: $Y = V,\ X = U\cdot V$, and jacobian is $$ 
J = det\begin{bmatrix}
V & U \\\\
0 & 1
\end{bmatrix}
$$
$\Rightarrow J= V\cdot 1 - U\cdot 0 = V$
So$ f\_{U,V}(U,V) = f\_{x,y}(UV, V)|V|$
$=\frac{1}{\sqrt{2\pi}}e^{-\frac{(UV)^2}{2}}\frac{2}{\sqrt{2\pi}}e^{\frac{-V^2}{2}}$
$=\frac{V}{\pi}e^{\frac{-V^2(U^2+1)}{2}}\ for\ U\in \mathbb{R},\ V>0$
Therefore U and V are not independent because they can't factor into $g(U)h(V)$.
The marginal PDF of U is $f\_U(U) = \int\_0^{\infty}f\_{U,V}(U,V)dV$
$=\int\_{0}^{\infty}\frac{V}{\pi}e^{\frac{-V^2(U^2+1)}{2}}dV = \int\_{0}^{\infty}\frac{1}{\pi}e^{\frac{-w(U^2+1)}{2}}\frac{dw}{2}$
$=\frac{1}{2\pi}\frac{1}{\frac{-(U^2+1)}{2}}e^{\frac{-w(U^2+1)}{2}}|\_0^{\infty} = \frac{1}{\pi(U^2+1)}, U\in \mathbb{R}$, where $w = V^2$, $dw = 2VdV$ and $\int e^{cw}dw = \frac{1}{c}e^{cw}$
This distribution looks like N(0,1) but has fatter tail, which go to 0 slower than N(0,1) does.
In fact E(U), Var(U) are undefined given integral doesn't converge.
$f\_U(U) = \frac{1}{\pi(U^2+1)}, U \in \mathbb{R}$ is called the cauchy distribution. Due to the symmetry around 0, we can express $\frac{Z\_1}{Z\_2} \sim\ Cauchy$ where $Z\_1, Z\_2$ are independent N(0,1).