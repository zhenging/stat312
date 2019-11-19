## Hypothesis Test on Population Proportion ($\pi$)

### Example A
Registered voter in Phoenix. `327` out of `500` support use of oxygenated fuel year-around to reduce air pollution. Do more than `60%` of registered voters in Phoenix support it?

#### Research Question
Do registered voters in Phoenix support use of oxygenated fuel year around to reduct air population?
  + **Population of Interest**: Registered voters in Phoenix
  + **Quantity of Interest**: Proportion who support oxygenated fules.

#### Perspective
We take the perspective of an environmentalist who want to shout to the world that more than `60%` of voters support oxygenated fules.
Let $\pi$ be the true population of voters who support the year-around use of oxygenated fuels to reduce air pollution.

#### Data Collection
Simple random sample of 500 registered voters
Record $X_j = \begin{cases} 1 \text{ if voters support}\\ 0 \text{ otherwise}\end{cases}$, where $j=1, 2, \dots, 500$
Sample size: $n=500$

#### State $H_0 \& H_A$
$H_0: \pi \le 0.60$
$H_A: \pi \gt 0.60$

#### Choose $\alpha$
Use standard value of $\alpha = 0.05$

#### Define test statistic & distribution
Let $C$ be the count of voters who says yes out of the 500 in the sample, and  assume $H_0$ is true.
$C \text{\textasciitilde} \text{Binomial(500, 0.6)}$
$E[C] = n * \pi = 500 \times 0.6 = 300$

#### Graph
![HT on population proportion](/assets/binomtest_right_tail.png)
> Observed `327` yeses. More yeses is surprising if $H_0$ is true.

#### Calculate `p-value`
> [Ti 83 tips](//todo)

$$
\begin{aligned}
\text{p-value} &= P\{\text{get our value or more extreme } \space | \space H_0 \text{ is true}\}\\
&= P(C \ge 327 \space | \space H_0 \text{ is true})\\
&= 1 - P(C < 326) \text{ one less than observed because of RV}\\
&= 1 - \text{binomcdf}(\color{magenta}\text{trail}, \color{magenta}\text{success probability}, \color{magenta}\text{success count})\\
&= 1 - \text{binomcdf}(500, 0.6, 326)\\
&= 1 - 0.99258\\
&= 0.00742
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Binomial Test Documentation](https://www.rdocumentation.org/packages/stats/versions/3.6.1/topics/binom.test)

##### Using Base R
```
binom.test(x = 327, n = 500, p = 0.60,
          alternative = "greater",
          conf.level = 0.95)

**********************************Output***************************************
Exact binomial test

data:  327 and 500
number of successes = 327, number of trials = 500, p-value = 0.00742
alternative hypothesis: true probability of success is greater than 0.6
95 percent confidence interval:
0.6173929 1.0000000
sample estimates:
probability of success
               0.654
```

##### Using ISCAM function
```
iscambinomtest(observed = 327, n = 500, hypothesized = 0.60,
              alternative = "greater",
              conf.level = 0.95)

**********************************Output***************************************
Exact Binomial Test

Data: observed successes = 327, sample size = 500, sample proportion = 0.654

Null hypothesis       : pi = 0.6
Alternative hypothesis: pi > 0.6
p-value: 0.0074202
95 % Confidence interval for pi: ( 0.61049 , 0.69568 )
```

#### Draw Conclusion
$\text{p-value} = 0.00742 < 0.05 = \alpha$
$\therefore$ **Reject** $H_0$ in favor of $H_A$.

#### State conclusion in context
This data (`327` out of `500`) **provides very strong evidence** that more than `60%` of registered voters in Phoenix support the use of oxygenated fuels year-around to reduce air pollution.

> **Note**
The size of the `p-value` determines the strength of the evidence.
![p-value](/assets/p_value_interpretation.png)

#### Questions
1. How to calculate Confidence Interval in the binominal test? Is is `1-PropZInterval`? Why the discrepancy between the results of `binom.test` and `iscambinomtest`?