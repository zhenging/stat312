## Hypothesis Test on Population Proportion ($\pi$)

### Example B
Semiconductor manufacturer produces controllers used in automobile engine applications. A customer requires that the fraction of defective controllers not exceed $0.03$ and that the manufacturer demonstrates process capability at this level of quality using $\alpha = 0.5$. The semiconductor manufacturer takes a random sample of 200 devices and finds via testing that 4 of them are defective. Can the manufacturer demonstrate process capability for the customer?

**Research Question**: Does the proportion of defective controllers meet the customer's requirement?
  + **Population of Interest**: All controllers of this type made by the manufacturer
  + **Quantity of Interest**: Proportion of defective controllers

**Perspective**: We take the manufacturer's perspective and hope to shout to the world that the proportion of defective controllers is less than $0.03$.
Let $\pi$ be the true population proportion of defective controllers

**Data Collection**:  Simple random sample of 200 controllers
Record $X_j = \begin{cases} 1 \text{ if controllers is defective }\\ 0 \text{ otherwise}\end{cases}$, where $j=1, 2, \dots, 500$
Sample size: $n=200$

**State $H_0 \& H_A$:**
$H_0: \pi \ge 0.03$
$H_A: \pi \lt 0.03$

**Choose $\alpha$**: Use standard value of $\alpha = 0.05$

**Define test statistic & distribution**
Let $C$ be the count of defective controllers, and assume $H_0$ is true.
$C \text{\textasciitilde} \text{Binomial(200, 0.03)}$
$E[C] = n * \pi = 200 \times 0.03 = 6$
$C \in [0, 1, 2 \cdots, 200]$

**Graph**
![HT on population proportion](/assets/ht_on_proportion_b.png)

**Calculate p-value**
$$
\begin{aligned}
\text{p-value} &= P(\text{get our value or more extreme } | H_0 \text{is true})\\
&= P(C \le 4 | H_0 \text{ is true})\\
&= \text{binomcdf}(200, 0.03, 4) \qquad \text{(Ti 83)}\\
&= 0.280979
\end{aligned}
$$

**Draw Conclusion**:
$\text{p-value} \approx 0.280979 > 0.05 = \alpha$
$\therefore$ **Fail** to Reject $H_0$.

**State conclusion in context**:
The sample data (4 defective out of 200) does not provide strong evidence that the manufacturer has the process quality that the custome requires.

**Notes**
//todo

![p-value](/assets/p-value.jpg)