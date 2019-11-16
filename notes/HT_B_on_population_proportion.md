## Hypothesis Test on Population Proportion ($\pi$)

> Credit: Dr. A

### Example B
Semiconductor manufacturer produces controllers used in automobile engine applications. A customer requires that the fraction of defective controllers not exceed `0.03` and that the manufacturer demonstrates process capability at this level of quality using $\alpha = 0.05$. The semiconductor manufacturer takes a random sample of `200` devices and finds via testing that `4` of them are defective. Can the manufacturer demonstrate process capability for the customer?

#### Research Question
Does the proportion of defective controllers meet the customer's requirement?
  + **Population of Interest**: All controllers of this type made by the manufacturer
  + **Quantity of Interest**: Proportion of defective controllers

#### Perspective
We take the manufacturer's perspective and hope to shout to the world that the proportion of defective controllers is less than `0.03`.
Let $\pi$ be the true population proportion of defective controllers

#### Data Collection
Simple random sample of `200` controllers
Record $X_j = \begin{cases} 1 \text{ if controllers is defective }\\ 0 \text{ otherwise}\end{cases}$, where $j=1, 2, \dots, 500$
Sample size: $n = 200$
Sample proportion: $\hat p = \frac{4}{200} = 0.02$

#### State $H_0 \& H_A$
$H_0: \pi \ge 0.03$
$H_A: \pi \lt 0.03$

#### Choose $\alpha$
Use the standard value of $\alpha = 0.05$

#### Define test statistic & distribution
Let $C$ be the count of defective controllers, and assume $H_0$ is true.
$C \text{\textasciitilde} \text{Binomial(200, 0.03)}$
$E[C] = n * \pi = 200 \times 0.03 = 6$
$C \in [0, 1, 2 \cdots, 200]$

#### Graph
![HT on population proportion](/assets/binomtest_left_tail.png)
> **Note**
Small values of $C$ are surprising if $H_0$ is true
$\therefore$ p-value is left tail.

#### Calculate `p-value`
> [Ti 83 tips](//todo)

$$
\begin{aligned}
\text{p-value} &= P\{\text{get our value or more extreme } | \space H_0 \text{ is true}\}\\
&= P(C \le 4 \space | \space H_0 \text{ is true})\\
&= \text{binomcdf}(n, \pi, \text{observed})\\
&= \text{binomcdf}(200, 0.03, 4) \qquad \text{(Ti 83)}\\
&\approx 0.2810
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Binomial Test Documentation](https://www.rdocumentation.org/packages/stats/versions/3.6.1/topics/binom.test)

##### Using Base R
```
binom.test(x = 327, n = 500, p = 0.03,
    alternative = "less", conf.level = 0.95)

**********************************Output***************************************
Exact binomial test

data:  4 and 200
number of successes = 4, number of trials = 200, p-value = 0.281
alternative hypothesis: true probability of success is less than 0.03
95 percent confidence interval:
0.00000000 0.04518041
sample estimates:
probability of success
                0.02
```

##### Using ISCAM function
```
iscambinomtest(observed = 4, n = 200, hypothesized = 0.03,
    alternative = "less", conf.level = 0.95)

**********************************Output***************************************
Exact Binomial Test

Data: observed successes = 4, sample size = 200, sample proportion = 0.02

Null hypothesis       : pi = 0.03
Alternative hypothesis: pi < 0.03
p-value: 0.28098
95 % Confidence interval for pi: ( 0.0054756 , 0.050414 )
```

#### Draw Conclusion
$\text{p-value} \approx 0.2810 > 0.05 = \alpha$
$\therefore$ **Fail** to Reject $H_0$.

#### State conclusion in context
The sample data (`4` defective out of `200`) **does not provide** strong evidence that the manufacturer has the process quality that the custome requires.

> **Note**
1\. The sample proportion of defective controllers is `0.02` which is less than the desired `0.03` quality level. However, if the true population proportion is `0.03`, it would not be too surprising to see `4` or fewer defectives in `200`.
2\. If we flipped `200` coins, each `w/P(heads) =3`, we would see 4 or fewer 4 heads in about `28%` of the replications.

| x | 0 | 1 | 2 |
|----|---|---|---|---|
$P(C\le x)$ | 0.002266 | 0.0165 | 0.05929

If we observed `0` or `1` defective controller, we would have strong evidence to reject $H_0$.