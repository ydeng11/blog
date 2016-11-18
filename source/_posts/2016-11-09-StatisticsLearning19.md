---
title: Fundamental Statistics Learning  Note(19)
date: 2016-11-09 17:25:34
tags:
 - Probability
categories: Statistics
---

> Intepretation of p-value

p-vale represent $p(reject\ H\_O|H\_O\ is\ true)$, calculated on your data. It is **Not** $p(H\_O\ is\ true)$.
<!---more--->
E.X. There are 1000 new cancer drugs developed. To test the effectiveness of each, suppose we have a hypothesis test that rejects $H\_O$: there is no treatment effect at level $\alpha=0.5$. Suppose we can achieve $90%$ power for their test if $H\_O$ is false.
Case I: none of drugs actually work
1. For how many drugs do we expect $H\_O$ to be rejected?
Ans: according to $\alpha = 0.5$, though none of drugs acutually work, there is $5\%$ probability we could incorrectly reject $H\_O$. Thus $50$ drugs are expected to be rejected.
2. What is $p(H\_O\ is\ true)$ among drugs where $H\_O$ is rejected?
Ans: It is $\frac{50}{50}=1$ because the rejected drugs are incorrectly rejected, they don't have effects.

Case II: 100 of them actually work
1. For how many drugs do we expect $H\_O$ to be rejected?
Ans: Here we use the fact that we can achive $90\%$ power for the test if $H\_O$ is false, which means we could correctly reject $H\_O$ by $90\%$ when $H\_O$ is false. 
$$\begin{matrix}
  & \text{reject } H\_O & \text{accept } H\_O & \text{Total} \\
\text{work} & 90 & 10 & 100 \\
\text{doesn't wrok} & 45 & 855 & 900 \\
 & 135 & 865
\end{matrix}$$
2. What is $p(H\_O\ is\ true)$ among drugs where $H\_O$ is rejected?
Ans: It is $\frac{45}{135}=\frac{1}{3}$

