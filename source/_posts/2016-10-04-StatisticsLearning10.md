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

Ex 2. $x\_1, x\_2, \dots, x\_n \overset{\text{i.i,d}}\sim f(x|\theta)=\frac{1}{\theta},\ 0<x<\theta$
Recall MLE: $\hat \theta = max\lbrace x\_i \rbrace$
a) Derive CDF/PDF of $U = max\lbrace x\_i \rbrace$
Bounds: $0<\mu<\theta$

$$\begin{equation}\begin{split}
p(U\leq \mu)&=p(max\lbrace x\_i \rbrace \leq \mu) \\\\
&=p(x\_1 \leq \mu, x\_2 \leq \mu,\dots, x\_n \leq \mu) \\\\
&=p(x\_1\leq \mu)p(x\_2 \leq \mu)\dots p(x\_n\leq \mu) \\\\
&=[p(x\_i \leq \mu)]^n \\\\
&=[\int\_0^\mu\frac{1}{\theta}dx]^n \\\\
&=(\frac{\mu}{\theta})^n
\end{split}\end{equation}$$
So $U$ has PDF, $f(U)=\frac{d}{d\mu}[(\frac{\mu}{\theta})^n]= \frac{n}{\theta^n}\mu^{n-1}$, where $0 < \mu< 0$

b) Bias, Variance, Consistency of $\hat \theta$
$$\begin{equation}\begin{split}
E(\hat \theta) = E(U) & = \int\_0^\theta \mu \frac{n}{\theta^n}\mu^{n-1}d\mu \\\\
&=\frac{n}{\theta^n}\cdot \frac{\mu^{n+1}}{n+1}|\_0^\theta \\\\
&=\frac{n}{n+1}\theta
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
Bias(\hat \theta)&=\frac{n}{n+1}\theta-\theta \\\\
&= -\frac{\theta}{n+1}
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
E(\mu^2)& = \int\_0^\theta \mu^2 \frac{n}{\theta^n}\mu^{n-1}d\mu\\\\
&=\frac{n}{\theta^n}\frac{\mu^{n+1}}{n+2}|\_0^\theta \\\\
&=\frac{n}{n+2}\theta^2
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
Var(\hat \theta)& = E(U^2)-E(U)^2 \\\\
&=\frac{n}{n+2}\theta^2 - (\frac{n}{n+2}\theta)^2 \\\\
&=\theta^2\frac{[n(n+1)^2-n^2(n+2)]}{(n+2)(n+1)^2} \\\\
&=\frac{n}{(n+2)(n+1)^2}\theta^2
\end{split}\end{equation}$$, where $n(n+1)^2-n^2(n+2) = n^3+2n^2+n-(n^3+2n^2)$.

$$MSE(\hat \theta) = Var(\hat \theta)+[Bias(\hat \theta)]^2$$
$\hat \theta$ is consistent since $\lim\_{n \to \infty}-\frac{\theta}{n+1}=0$, $\lim\_{n \to \infty}-\frac{n}{(n+1)^2(n+2)}\theta^2=0$

 - We can construct function to eliminate bias, $\hat \theta\_1=\frac{n+1}{n}max\lbrace x\_i \rbrace$ is unbiased
 - For two unbiased estimators, it makes sense to compare their variances for the sample size $n$ (which estimator goves more precise results for the same amount of data?)
 
 **Definition:** The relative efficiency of two unbiased estimators $\hat \theta\_1$, and $\hat \theta\_2$, is $\frac{\text{variance}(\hat \theta\_2)}{\text{variance}(\hat \theta\_1)}$.
  - $\hat \theta\_1$ is more efficient than $\hat \theta\_2$ if $Var(\hat \theta\_1)< Var(\hat \theta\_2)$
  - $\hat \theta\_2$ is more efficient than $\hat \theta\_1$ if $Var(\hat \theta\_2)< Var(\hat \theta\_1)$
  
Ex. $x\_1, x\_2, \dots, x\_n \overset{\text{i.i.d}}\sim \text{uniform}(0, \theta)$, i.e. $f(x|\theta)=\frac{1}{\theta}$ for $0<x<\theta$
$\hat \theta\_1 = \frac{n+1}{n}max \lbrace x\_i \rbrace$ is unbiased estimator of $\theta$.
$\hat \theta\_2 = 2 \bar x $ is also unbiased since $E(x\_i)=\frac{\theta}{2}$, $Var(x\_i)=\frac{\theta^2}{12}$.
probability pf uniform distribution:
$E(\bar x)=\frac{\theta}{2}, Var(\bar x)=\frac{\theta^2}{12}$
And so $E(\hat \theta\_2)=E(2\bar x)=2E(\bar x)=2\cdot \frac{\theta}{2}=\theta$, which is unbiased.
if $\hat \theta\_1$ or $\hat \theta\_2$ more efficient?

$$\begin{equation}\begin{split}
Var(\hat \theta\_1) &= (\frac{n+1}{n})^2 Var(max \lbrace x\_i \rbrace) \\\\
&=(\frac{n+1}{n})^2\frac{n}{(n+1)^2(n+2)}\theta^2 \\\\
&=\frac{1}{n(n+2)}\theta^2
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
Var(\hat \theta\_2) &= 2^2 Var(\bar x) \\\\
&=4 \frac{\theta^2}{12n} \\\\
&=\frac{\theta^2}{3n}
\end{split}\end{equation}$$

$$\begin{equation}\begin{split}
\frac{Var(\hat \theta\_2)}{Var(\hat \theta\_1)} &= \frac{\frac{\theta^2}{3n}}{\frac{\theta^2}{n(n+2)}} \\\\
& = \frac{n+2}{3}
\end{split}\end{equation}$$

 - if $n>1$, then $\hat \theta\_1$ is more efficient than $\hat \theta\_2$
 - if $n=1$, then equal efficiency