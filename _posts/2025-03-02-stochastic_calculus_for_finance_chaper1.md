---
title: One-time period binomial model 
date: 2025-03-02 11:33:00 +0800
categories: [Finance]
tags: [stochastic_calculus,reading_notes]     # TAG names should always be lowercase
math: true
---
Suppose at $t_0$, the stock price per share for some stock is $S_0$. The stock price per share at time $t_1$ for the same stock $S_1$ is determined by a coin toss, which is not necessarily fair, i.e. $p(H)$ can be different from $p(T)$. If it's a head, we arrive at $S_1(H)$ otherwise $S_1(T)$. 

We define the following variales:

upper factor $$u = \frac{S1(H)}{S_0}$$
down factor $$u = \frac{S1(T)}{S_0}$$
interests rate $r$: 1 dollar invested at $t_0$ will be worthy $(1+r)$ dollars at $t_1$. 1 dollar borrowed at $t_0$ will need to be returned by $(1+r)$ dollars at $t_1$. 

The value of portfolio at each time period i is $X_i$.

### Rule out abitrage 

**Lemma 1.1**
> Abitrage does not exist in one-period binomial model iff $0 < d < 1+r < u$. 

**Prove that if abitrage does not exist, $d < 1+r < u$.** 

$d>0$ is followed by the fact that the stock price per share cannot be negative or zero. 

If $ d > 1+r$, one can start with 0 money and just borrow at $t_0$. At $t_1$, they will earn enough t pay debt and still have positive profits even the stock ends up at the lower price at $t_1$. 

If $u\leq 1+r$, one can sell the stock short at $t_0$ and buy them back at $t_1$ with positive profits even the stock ends up at the higher price at $t_1$. 


**Prove that if $d < 1+r < u$, abitrage does not exist.** 

Suppose we start with zeor money i.e. $X_0 = 0$ and borrow some money to buy $\Delta _0$ shares of stock. 

$X_1 = \Delta _0 S_1 + (1+r)(X_0 - \Delta _0 S_0)$
$X_1 = \Delta _0 (S_1 - (1+r)S_0)$

$S_1 = uS_0$ if the coin toss turns out to be head and  $S_1 = dS_0$ if the coin toss turns out to be tail. If $d < 1+r < u$, $S_1(H) >0 \text{ and } S_1(T) < 0$. Therefore, the possibility of making money $P(S_1(H))$ is positive and the possibility of losing money is also positive. 

**This conclusion is not influenced by the choice of $\Delta _0$**

### Arbitrage pricing theory approach

> The fundamental question of option pricing is *how much the option is worth at time zeor before knowing the coin toss results*

Consider the European call option, suppose at $t_1$, owner of the option can buy the stock at the strike price $K$. Assume $S_1(T) < K < S_1(H)$, if we arrive at $S_1(T)$, the owner of the option would not want to exercise the option as they will simply lose money. On the contrary, if we arrive at $S_1(H)$, the owner of the option will want to exercise the option and yield profit of $[S_1(H)-K]^+$($max(0,S_1(H)-K)$). We also need to ensure that if the coin toss turns out to be tail, the buyer of the call option won't want to exercise the option. Therefore, we get the following equations:
$$X_1(T) = \Delta _0S_1(T) + (1+r)(X_0-\Delta _0 S_0) = 0 $$
$$X_1(H) = \Delta _0S_1(H) + (1+r)(X_0-\Delta _0 S_0) = S_1(H) - K $$. 

Subtract two equations, we get the so called **delta hedging formula**: 
$$\Delta _0(S_1(H) - S_1(T)) = S_1(H) - K $$
Therefore, $\Delta _0 $ must be:
$$\Delta _0 = \frac{S_1(H) - K}{S_1(H)-S_1(T)}$$
Subsitude $\Delta _0$ back into any one of two equations, we get the value of $X_0$.

<!-- ** 1.2** -->
> Arbitrage does not exist iff the price of the option at $t_0$ is equal to $X_0$, i.e arbitrage exists when the option price is underpriced or overpriced. 

Suppose the option price at $X_0^{'}$ which is larger than the derived $X_0$, i.e. the option is overpriced at $t_1$. One should sell the exact same option and replicate the portfolio by borrowing $X_0 - \Delta _0 S_0$ and owning $\Delta _0$ shares of stock at $t_0$. No matter what the coin toss result is at $t_1$, the seller will be able to pay off the option and gain profit by the investment of rest of the money. 

Suppose the option price at $X_0^{'} < X_0$, i.e. the option is underpriced. One should buy the option and reverse the portfolio. More specifically, one should sell the $\Delta _0$ shares of stock which generates $\Delta _0 S_0$ profit and invest the rest $\Delta _0 S_0 - X{'}$ to the market. If at $t_1$, the coin flip turns out to be $H$, there are profits from both the option and the investment from the rest of the money. If at $t_1$, the coin flip turns out to be $T$, the option is worthless. But the investment will be worth $(1+r)(\Delta _0 S_0 - X_0)+(1+r)(X_0 - X_0^{'})$. The first part would be enough to buy the the same share of stock back at $t_1$ since $d<1+r$ and the second part will just be profit.

Either case, when the option price is underpriced and overpriced, one can find a corresponding strategy such that there will no risk of losing but positive possibility of gaining.

### General one-period model and risk-neutral pricing formula
Define **derivative security** $V_1(H), V_1(T),V_0$ for more general model. The value of $V_1(H), V_1(T),V_0$ might be different from different derivatives. In the previous Eureopean call option case, we have $V_1(H) = [S_1(H) - K]^{+} $ and $V_1(T) = 0$. Similarly, for the general model, we get: 
$$X_1(T) = \Delta _0S_1(T) + (1+r)(X_0-\Delta _0 S_0) = V_1(T)$$
$$X_1(H) = \Delta _0S_1(H) + (1+r)(X_0-\Delta _0 S_0) = V_1(H)$$. 
Divide both equations by $(1+r)$:
$$X_0 + \Delta _0(\frac{1}{1+r}S_1(T)- S_0) = \frac{1}{1+r}V_1(T)$$
$$X_0 + \Delta _0(\frac{1}{1+r}S_1(H)- S_0) = \frac{1}{1+r}V_1(H)$$. 

Again, we could get the exact delta value by subtracting two equations. Subsitude the delta hedging formula to the first equation, we get:
$$X_0 = - \frac{S_1(H) - K}{S_1(H)-S_1(T)}(\frac{1}{1+r}S_1(T)- S_0) + \frac{1}{1+r} V_1(T)$$ 
Subsitude $S_1(T)$ with $dS_0$ and $S_1(H)$ with $uS_0$, we get the **risk-neutral pricing formula**:
$$X_0 = \frac{1}{1+r} (\frac{1+r-d}{u-d}V_1(H) + \frac{u-(1+r)}{u-d}V_1(T))$$
> Any $V_0 \neq X_0$ will introduce arbitrage. 

Let $p^{'}$ be $\frac{1+r-d}{u-d}$ and $q^{'}$ be $\frac{u-(1+r)}{u-d}$. These are called the **risk-neutral factors**. 