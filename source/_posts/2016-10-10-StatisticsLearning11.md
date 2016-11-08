---

title: Fundamental Statistics Learning Note (11)

date: 2016-10-10 18:33:03

tags:
 - Probability
categories: Statistics

---
> Rao-Blackwell theorem



Rao-Blackwell Theorem:  <!---more--->Let $\hat \theta$  be an unbiased estimator for $\theta$, and $T$ is the minimal sufficient statistics for $\theta$.
Then define $$\hat \theta^\* = E(\theta|T)$$
result is $E(\hat \theta^\*) = \theta$ and $Var(\hat \theta^\*)=Var(\hat \theta)$

Recall: 
$E(y|x)$ is a r.v, $E(E(y|x))=E(y)$, $Var(y)=E[Var(y|x)]+Var[E(y|x)]$
$E(\hat \theta^\*)=E[E(\hat\theta|T)]=E(\hat \theta)=\theta$, so $\hat \theta^\*$ is unbiased.
$Var(\hat \theta)=E[Var(\hat \theta|T)]+Var[E(\hat \theta|T)]=\underbrace{E[Var(\hat \theta|T)]}\_{\geq 0}+Var(\hat \theta^\*) \geq Var(\hat \theta^\*)$

when is $E(\hat \theta|T)=\hat \theta$? When $\hat \theta$ is a function of $T$.
Conclude: lowest variance is obtained when $\hat \theta$ is a function of minimal sufficient statistics.
Theorem: The minimal variance unbiased estimator (MVUE) must be a function of the minimal sufficient statistics.

Ex $x\_1,x\_2,\dots,x\_n \overset{\text{i.i.d}}\sim N(\mu, \sigma^2)$, minimal sufficient statistics is $\bar x$ and $S^2$.
The MVUE of $\mu$ is $\bar x$ since $E(\bar x) = \mu$.
The MVUE of $\sigma^2$ is $S^2$ since $E(S^2) = \sigma^2$.
MLE of $\sigma^2$ is $\frac{n-1}{n}S^2$.

**How to find MVUE?**
- Find MLE
 1. If MLE is unbiased, it is MVUE.
 2. If MLE is biased, adjust it to make an unbiased estimator.
    
**Properties of the MLE**
 1. it is a function of the minimal sufficient statistics
 2. it is consistent
 3. it is the most efficient estimator as $n \to \infty$
 4. variance of the MLE, when n is large the $\hat \theta\_{MLE}\overset{\text{approx}}\sim N(\theta, \frac{1}{I\_n(\theta)})$, where $\theta$ is the true value of the parameter and $I\_n(\theta)$ is the fisher information.
   - $I\_n(\theta) = -E[\underbrace{l''(\theta)}\_{2^{nd}\text{derivative of log-like}}] \overset{\text{approx since $\theta$ unknown}} \approx -l''(\hat \theta\_{MLE})$ 
   - Hence $Var(\hat \theta\_{MLE})\approx \frac{1}{I\_n(\theta)}$
   - $\hat Var(\hat \theta\_{MLE}) = \frac{-1}{\underbrace{l''(\hat \theta\_{MLE})}\_{<0}}$