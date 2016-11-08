---

title: Fundamental Statistics Learning Note (14)

date: 2016-10-20 11:42:14

tags:

 - Probability

categories: Statistics

---



> Wald's memos



Analyzed data of planes returning from combat missions

 1. rate of survival when hit by enemy gunfire

 2. how to imporve survival rate by reinforcing certain plane parts

 

Intuition: section A has lots of hits among survivors, section B has few hits among survivors.



<!---more--->



1. Analysis of rate of survival when hit by enemy fire

$$\begin{matrix}

x\_{10} && x\_{11} && x\_{12} && x\_{13} \\\\

      && x\_{21} && x\_{22} && x\_{23}

\end{matrix}$$

$N = \sum x\_{ij} \equiv$ total planes sent on mission

$x\_{1j} \equiv $ # planes returning with $j$ hits

$x\_{2j} \equiv $ # planes not returned with $j$ hits



Let $p{ij} \equiv$ probability of being in category $x\_{ij}$

we knoe the total lost is $x\_{21}+x\_{22}+x\_{23}$ but don't know $x\_{21}, x\_{22}, x\_{23}$ counts individually



$$L(p\_{10},p\_{11},p\_{12},p\_{13}|x\_{10},x\_{11}, x\_{12}, x\_{13}, x\_{21}+x\_{22}+x\_{23}) \overset{\text{planes are independent}}= C\cdot p\_{10}^{x\_{10}}p\_{11}^{x\_{11}} p\_{12}^{x\_{12}} p\_{13}^{x\_{13}}(1-\sum\_{j=0}^3 p\_{ij}^{x\_{21}+x\_{22}+x\_{23}})$$

where $C$ is the count orderings which doesn't depend on $p\_{ij}$



Note that $$x\_{21}+x\_{22}+x\_{23} = N - \sum\_{j=0}^3 x\_{1j}$$

$$l(p\_{10},p\_{11},p\_{12},p\_{13}) = logC + \sum\_{j=0}^3 x\_{ij}logp\_{ij}+(N - \sum\_{j=0}^3 x\_{1j})log(1-\sum\_{j=0}^3 p\_{ij})$$



$$\Rightarrow \frac{\alpha l}{\alpha p\_{10}}=\frac{x\_{10}}{p\_{10}}+(N-1-\sum\_{j=0}^3 x\_{ij})\frac{-1}{1-1-\sum\_{j=0}^3 p\_{ij}} \overset{\text{set}}=0$$

Similarly, we need the partial derivative for other parameter, $\frac{\alpha l}{\alpha p\_{ij}}$, sovling the 4 equations gives MLE: $\hat p\_{ij} = \frac{x\_{ij}}{n}$

Defein $r\_j = \frac{p\_{1j}}{p\_{1j}+p\_{2j}}$, wald define this to represent probability of surviving hit $j$ given survival $j-1$.



Wald assumed $r\_j = q^j, j=1,2,3,$ i.e. hits are iid with survival probability $q$ for each.



Note $1-\sum\_{j=1}^3(p\_{1j}+p\_{2j})=1-p\_{10}=\sum\_{j=1}^3 \frac{p\_{1j}}{r\_j}=\sum\_{j=1}^3\frac{p\_{1j}}{q^j}$



MLE of $q$ by invariance is solution of $1-\hat p\_{10} = \sum\_{j=1}^3\frac{\hat p\_{1j}}{q^j}$