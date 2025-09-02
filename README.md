# options_risk_neutral_implied_PDF

Options are something beautiful. A non linear function that takes into account two values, the T and K. Is it thanks to this properties that its price has implicit the expected distribution of future prices.

$$
Call Payoff = \mathbb{E}^{\mathbb{Q}}[\max(S_T - K, 0)]
$$

The price of a European call option at time $t = 0$ under the risk-neutral measure $\mathbb{Q}$ is:

$$
C = e^{-rT} \mathbb{E}^{\mathbb{Q}}[\max(S_T - K, 0)]
$$

Where:  
- $C$: Call option price at time 0  
- $r$: Risk-free rate  
- $T$: Time to maturity  
- $S_T$: Underlying asset price at maturity  
- $K$: Strike price  
- $\mathbb{E}^{\mathbb{Q}}$: Expectation under the risk-neutral measure (risk-neutral measure = adding risk free rate)


This expectation can be written as an integral using the risk-neutral probability density function $f_{S_T}^{\mathbb{Q}}(s)$:

$$
C = e^{-rT} \int_K^{\infty} (s - K) f_{S_T}^{\mathbb{Q}}(s) \, ds
$$

The risk-neutral probability that the option expires in the money is:

$$
\mathbb{Q}(S_T > K) = \int_K^{\infty} f_{S_T}^{\mathbb{Q}}(s) \, ds = 1 - F_{S_T}^{\mathbb{Q}}(K)
$$

Without assuming a specific model (like lognormal under geometric Brownian motion), the call price remains in this general integral form. A closed-form expression using standard CDFs (e.g., Black-Scholes) requires specifying the distribution of $S_T$. But... what if instead we want to obtain this distribution from the real market option prices??

---

![Simulation Animation](option_analysis_animation.gif)
