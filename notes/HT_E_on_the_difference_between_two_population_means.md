## Hypothesis Test on the Difference between Twp Population Means

### Example E
Two suppliers maufacture a plastic gear used in a laser printer, the impact strength of those gears measured in foot-pounds is an important characteristic. A random sample of 10 gears from suppliers 1 result in $\bar{x_1} = 290$ and $s_1 = 12$; which another random sample of 16 gears from the second supplier result in $\bar{x_2} = 321$ and $s_2 = 22$. Does the data support the claim that the mean impact strength of gears from supplier 2 is at least 20 foot-pounds higher than that of supplier 1? Use $\alpha = 0.01$

#### Research Question
Is supplier 2 gears mean strength at least 20 ft-lbs higher than that of supplier 1?

##### Population of Interest
+ Population 1: Plastic gears made by supplier 1
+ Population 2: Plastic gears made by supplier 2

##### Quantituy of Interest
Population mean impact strength

#### Perspective
Population mean impact strength from supplier 2 is at least 20 ft-lbs higher than that of supplier 1.
We are looking for strong evidence that supplier 2 gears are 20 ft-lbs better. Perhaps our current supplier is 1 and we decided that an improvement of 20 ft-lbs would be worth the cost of chaing suppliers.
Let $\mu_j$ be true population mean impact strength of gears from supplier `j`, and  `j = 1, 2`.

#### Data Collection
**Assumptions**
+ A simple random sample was used.
+ The data sets are independent, because they are different manufacturers.

Sample size: $n_1 = 10, \space n_2 = 16$

#### State $H_0 \& H_A$
$H_0: \mu_2 - \mu_1 \le 20$
$H_A: \mu_2 - \mu_1 > 20$
**Or** (keep input to software or calculator straight)
$H_0: \mu_1 - \mu_2 \ge -20$
$H_A: \mu_1 - \mu_2 < -20$

> **Note**
We denote `-20` with $\Delta_0$.

#### Choose $\alpha$
Use the **given** value of $\alpha = 0.01$

#### Define test statistic & distribution
**Assumptions:**
1. Simple random sample for each population
2. The two samples are independent.
3. Each data set is normally distributed.
4. $\sigma_1^2 \ne \sigma_2^2$, since  $s_1^2 \ne s_2^2$, we can **not** assume that $\sigma_1^2 = \sigma_2^2$

> **Note**
In the rare case, that we **can** assume $\sigma_1^2 = \sigma_2^2$, the degree of freedom and the denominator of $T_0$ are different. This equal variance situation uses a pooled standard deviation.

$$
\begin{aligned}
&\bar{x_1} = 290; \space s_1 = 12; \space n_1 = 10\\
&\bar{x_2} = 321; \space s_1 = 22; \space n_2 = 16\\
&\Delta_0 = -20\\
T_0 &= \frac{(\bar{X_1} - \bar{X_2}) - \Delta_0}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}} \text{ and } T_0 \text{\textasciitilde} t_v\\
t_0 &= \frac{(290 - 321) - (-20)}{\sqrt{\frac{12^2}{10} + \frac{22^2}{16}}}\\
&= -1.6462\\
v &= \bigg\lfloor \frac{(r_1^2 + r_2^2)}{\frac{r_1^2}{n_1 - 1} + \frac{r_2^2}{n_2 - 1}} \bigg\rfloor, \space r_j = \frac{s_j^2}{n_j}, \space j\in \{1, 2\} \qquad \color{magenta}{\text{(The ugly formula)}}\\
\implies &v = \lfloor 23.721 \rfloor = 23 \qquad \text{Floor function: round to integer}\\
T_0 &\text{\textasciitilde} t_{23}
\end{aligned}
$$

> **Note**
Be careful calculating $v$. It should be close to $n_1 + n_2$.

#### Graph
![Two sample t test](/assets/two_sample_t_test_left_tail.png)

#### Calculate `p-value`
$$
\begin{aligned}
\text{p-value} &= P\{\text{get what we got or somthing more extreme} \space | \space H_0 \text{ is true}\}\\
&= P\{T_{0} < t_0\ \space | \space T_{0} \text{\textasciitilde} t_{23} \text{ and } \mu_1 - \mu_2 = -20\} \\
&= \text{tcdf}(\color{magenta}\text{Lower bound}, \color{magenta}\text{ Upper bound}, \color{magenta}\text{ Degree of freedom})\\
&= \text{tcdf}(-99, -1.6462, 23)\\
&= 0.05666
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Summarized T-Test Documentation](https://www.rdocumentation.org/packages/BSDA/versions/1.2.0/topics/tsum.test)

##### Using Base R
```
tsum.test(mean.x = 290, s.x = 12, n.x = 10,
          mean.y = 321, s.y = 22, n.y = 16,
          alternative = "less",
          mu = -20,
          conf.level = 0.99)

**********************************Output***************************************
Welch Modified Two-Sample t-Test

data:  Summarized x and y
t = -1.6462, df = 23.721, p-value = 0.05645
alternative hypothesis: true difference in means is less than -20
99 percent confidence interval:
      NA -14.33333
sample estimates:
mean of x mean of y
    290       321
```

##### Using ISCAM function
```
iscamtwosamplet(x1 = 290, sd1 = 12, n1 = 10,
                x2 = 321, sd2 = 22, n2 = 16,
                hypothesized = -20,
                alternative = "less",
                conf.level = 0.99)

**********************************Output***************************************
Two Sample t test

Group1: mean = 290, sd = 12,  sample size = 10
Group2: mean = 321, sd = 22,  sample size = 16
diff:-31

Null hypothesis       : mu1-mu2 = -20
Alternative hypothesis: mu1-mu2 < -20
t-statistic: -1.646
df: 23.72-1.6462
99 % Confidence interval for mu1-mu2: ( -49.70815 ,  -12.29185 )
p-value: 0.05646
```

#### Draw Conclusion
$\text{p-value} = 0.05666 > 0.01 = \alpha$
$\therefore$ **Fail** to reject $H_0$.

#### State conclusion in context
This data **does not** support the claim that the mean impact strength of gear from supplier 2 is at least 20 ft-lbs high than that of supplier 1. We do not recommand changing from supplier 1 to supplier 2.

#### Questions
1. Why $\sigma_1^2 \ne \sigma_2^2$, since  $s_1^2 \ne s_2^2$, we can **not** assume that $\sigma_1^2 = \sigma_2^2$