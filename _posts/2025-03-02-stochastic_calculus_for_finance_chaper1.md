---
title: Binomial No-Arbitrage Pricing Model
date: 2025-03-02 11:33:00 +0800
categories: [Finance]
# tags: [graph_theory]     # TAG names should always be lowercase
math: true
---

Suppose at $t_0$, the stock price per share for some stock is $S_0$. The stock price per share at time $t_1$ for the same stock $S_1$ is determined by a coin toss, which is not necessarily fair, i.e. $p(H)$ can be different from $p(T)$. If it's a head, we arrive at $S_1(H)$ otherwise $S_1(T)$. 

We define the following variales:

upper factor $$u = \frac{S1(H)}{S_0}$$
down factor $$u = \frac{S1(T)}{S_0}$$
interests rate $r$: 1 dollar invested at $t_0$ will be worthy $(1+r)$ dollars at $t_1$. 1 dollar borrowed at $t_0$ will need to be returned by $(1+r)$ dollars at $t_1$. 

**Lemma 1.1**
> Abitrage does not exist in one-period binomial model iff $d < 1+r < u$. 

Prove that if abitrage does not exist, $d < 1+r < u$. 
If $d>1+r$
