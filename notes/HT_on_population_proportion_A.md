## Hypothesis Test on Population Proportion ($\pi$)

### Example A
Registered voter in Phoenix. 327 out of 500 support use of oxygenated fuel year-around to reduce air pollution. Do more than 60% of registered voters in Phoenix support it?

**Research Question**: Do registered voters in Phoenix support use of oxygenated fuel year around to reduct air population?
  + **Population of Interest**: Registered voters in Phoenix
  + **Quantity of Interest**: Proportion who support oxygenated fules.

**Perspective**: We take the perspective of an environmentalist who want to shout to the world that more than 60% of voters support oxygenated fules.
Let $\pi$ be the tru population of voters who support the year-around use of oxygenated fuels to reduce air pollution.

**Data Collection**:  Simple random sample of 500 registered voters
Record $X_j = \begin{cases} 1 \text{ if voters support}\\ 0 \text{ otherwise}\end{cases}$, where $j=1, 2, \dots, 500$
Sample size: $n=500$

**State $H_0 \& H_A$:**
$H_0: \pi \le 0.60$
$H_A: \pi \gt 0.60$

**Choose $\alpha$**: Use standard value of $\alpha = 0.05$

**Define test statistic & distribution**
Let $C$ be the count of voters who says yes out of the 500 in the sample, and  assume $H_0$ is true.
$C \text{\textasciitilde} \text{Binomial(500, 0.6)}$, $E[C] = n * \pi = 500 \times 0.6 = 300$

**Graph**
![HT on population proportion](/assets/ht_on_population_proportion.jpg)

**Calculate p-value**
$$
\begin{aligned}
\text{p-value} &= P(\text{get our value or more extreme } | H_0 \text{is true})\\
&= P(C \ge 327 | H_0 \text{is true})\\
&= 1 - P(C < 326) \text{ one less than observed because of RV}\\
&= 1 - \text{binomcdf}(500, 0.06, 326) \qquad \text{(Ti 83)}\\
&= 1 - 0.99258\\
&= 0.00742
\end{aligned}
$$

**Draw Conclusion**:
$\text{p-value} \approx 0.00742 < 0.05 = \alpha$
$\therefore$ Reject $H_0$ in favor of $H_A$.

**State conclusion in context**:
This data (327 out of 500) provides very strong evidence that more than 60% of registered voters in Phoenix support the use of oxygenated fuels year-around to reduce air pollution.

**Notes**
The size of the p-value determins the strength of the evidence.

![p-value](/assets/p-value.jpg)