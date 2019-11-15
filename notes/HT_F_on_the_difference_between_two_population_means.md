## Hypothesis Test on the Difference between Twp Population Means

### Example F
A paper in Quality Engineering [2013, v25(1)] presented data on cycles to failure of solder joints at different temperatures for printed circuit boards. Failure data for two temperatures for a copper-nickel-gold printed circuit board is summarized.
$20^{\degree} C: \bar{x_1} = 422.2; \space s_1 = 172.23; \space n_1 = 10$
$60^{\degree} C: \bar{x_2} = 375.7; \space s_1 = 161.92; \space n_2 = 10$
Test whether or not the mean number of cycles to failure is the same at both temperatures?

#### Research Question
Are the mean number of cycles to failure is the same at both temperatures?
**Population of Interest**
+ Population 1: Solder joints made at $20^{\degree} C$.
+ Population 2: Solder joints made at $60^{\degree} C$.

#### Perspective
We are testing for a difference without choosing which is larger. Our claim to shout is "there is no difference".
Let $\mu_1$ population mean number of cycles to failure for solder joints made at $20^{\degree} C$.
Let $\mu_2$ population mean number of cycles to failure for solder joints made at $60^{\degree} C$.

#### Data Collection
The data is already collected.
+ We assume that a simple random sample was used.
+ We assume that the data sets are independent.
Sample size: $n_1 = 10, \space n_2 = 10$

> **Note**
Balanced sample size are preferred. Very large difference (e.g. 10 vs 100) are problematic!

#### State $H_0 \& H_A$
$H_0: \mu_1 = \mu_2$
$H_A: \mu_1 \ne \mu_2$
**Or**
$H_0: \mu_1 - \mu_2 = 0$
$H_A: \mu_1 - \mu_2 \ne 0$


> **Note**
This is a two-sided HT, so both tails are part of the p-value.

#### Choose $\alpha$
Use the standard value of $\alpha = 0.05$

#### Define test statistic & distribution
Assumptions:
1. Simple random sample for each population
2. The two samples are independent.
3. Each data set is normally distributed.
4. $\sigma_1^2 \ne \sigma_2^2$,  $\sigma_1^2 \approx s_1^2$ and $\sigma_2^2 \approx s_2^2$

$$
\begin{aligned}
&\bar{x_1} = 422.2; \space s_1 = 172.23; \space n_1 = 10\\
&\bar{x_2} = 375.7; \space s_1 = 161.92; \space n_2 = 10\\
&\Delta_0 = 0\\
T_0 &= \frac{(\bar{X_1} - \bar{X_2}) - \Delta_0}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}\\
&= 0.62204\\
T_0 &\text{\textasciitilde} t_v\\
v &= \lfloor \frac{(r_1^2 + r_2^2)}{\frac{r_1^2}{n_1 - 1} + \frac{r_2^2}{n_2 - 1}} \rfloor, \space r_j = \frac{s_j^2}{n_j}, \space j\in \{1, 2\}\\
\implies &v = \lfloor 17.93 \rfloor = 17\\
T_0 &\text{\textasciitilde} t_{17}
\end{aligned}
$$

> **Note**
Be careful calculating $v$. It should be close to $n_1 + n_2$.

#### Graph
![Two sample t test](/assets/two_sample_t_test_two_sides.png)

#### Calculate `p-value`
$$
\begin{aligned}
\text{p-value} &= P\{\text{get what we got or somthing more extreme} \space | \space H_0 \text{ is true}\}\\
&= 2 * P\{t_{17} < -46.5\ | \mu_1 - \mu_2 = 0\} \quad \text{b/c t17 is symmetric}\\
&= 2 * \text{tcdf}(\underbrace{-99}_{\text{lower boundary}}, \overbrace{-0.622}^{\text{upper boundary}}, \underbrace{17}_{\text{degree of freedom}}) \qquad \text{(Ti 83)}\\
&= 2 * 0.2710973\\
&= 0.54219
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Summarized T-Test Documentation](https://www.rdocumentation.org/packages/BSDA/versions/1.2.0/topics/tsum.test)

##### Using Base R
```
tsum.test(mean.x = 422.2, s.x = 172.23, n.x = 10,
          mean.y = 375.7, s.y = 161.92, n.y = 10,
          alternative = "two.sided",
          mu = 0,
          conf.level = 0.95)

**********************************Output***************************************

	Welch Modified Two-Sample t-Test

data:  Summarized x and y
t = 0.62204, df = 17.932, p-value = 0.5417
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -110.5946  203.5946
sample estimates:
mean of x mean of y
    422.2     375.7
```

##### Using ISCAM function
```
iscamtwosamplet(x1 = 422.2, sd1 = 172.23, n1 = 10,
                x2 = 375.7, sd2 = 161.92, n2 = 10,
                hypothesized = 0,
                alternative = "two.sided",
                conf.level = 0.95)

**********************************Output***************************************
Two Sample t test

Group1: mean = 422.2, sd = 172.23,  sample size = 10
Group2: mean = 375.7, sd = 161.92,  sample size = 10
diff:46.5

Null hypothesis       : mu1-mu2 = 0
Alternative hypothesis: mu1-mu2 <> 0
t-statistic: 0.622
df: 17.93
95 % Confidence interval for mu1-mu2: ( -110.5958 ,  203.5958 )
p-value: 0.5417
```

#### Draw Conclusion
$\text{p-value} = 0.54 > 0.05 = \alpha$
$\therefore$ **Fail** to reject $H_0$.

#### State conclusion in context
This data **does not** provide evidence that the mean number of cycles until failures is different for solder joints made at $20^{\degree}$ C versus $60^{\degree}$ C.