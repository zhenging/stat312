## Hypothesis Test on Population Mean (Single Population)

> Credit: Dr. A

### Example C
Self-report data of height for a set of college students were analyzed. Summary statistics:
sample mean: $\bar{x} = 65.1622$
sample st dev: `s = 2.5442`
sample size: `n = 37`
`min = 59, Q1 = 64, Q3 = 67, max = 69`
Does the data support a claim that the population mean height is at least 65 inches?

#### Research Question
Is the population mean height at least 65 inches?
  + **Population of Interest**: College Students
  + **Quantity of Interest**: Population mean height

> **Note**
We have very little information about the sample therefore little about an appropriate population.

#### Perspective
We hope to find evidence that college students mean height is at least 65 inches.
Let $\mu$ be the true population mean height (inches) of college students

#### Data Collection
We are not given any information about how the data was collected. We must **assume** that a simple random sample was used.
> **Note**
Always state the assumption if you don't know how the data was collected.
Sample size: $n = 37$
Let $X_j$ be self reported height (inches) of the `jth` student $j=1, 2, \cdots, 12$

#### State $H_0 \& H_A$
$H_0: \mu \le 65$
$H_A: \mu > 65$

> **Note**
If you want to claim **at least** something, equal sign must be in $H_0$.

#### Choose $\alpha$
Use the standard value of $\alpha = 0.05$

#### Define test statistic & distribution
Since we only have summary data, we will assume that the following is true about our sample data
1. A simple random sample was used.
2. Data is from a normally distributed population. (**test is NOT very sensitive to this assumption, but check waht you can.** For this data, sample mean $\approx$ sample median, so it is not severely skewed.)
3. $\sigma^2 \approx s^2$. (**Large sample sizes support this**, `n=37`, so this is OK)

$$
\begin{aligned}
&\bar{x} = 65.1622, s = 2.5442, n = 37, \mu_0 = 65\\
&T_0 = \frac{\bar x - \mu_0}{s/\sqrt n} \text{ and }  T_0 \text{\textasciitilde} t_{n-1}\\
&t_{n-1} = t_{12-1} = t_{11}\\
&t_0 = \frac{65.1622- 65}{2.5442/\sqrt{37}} \approx 0.3878
\end{aligned}
$$

> **Note**
$t_0$ is a numerical value.

#### Graph
![One sample t test](/assets/one_sample_t_test_right_tail.png)

#### Calculate `p-value`
> [Ti 83 tips](//todo)

$$
\begin{aligned}
\text{(p-value)} &= P\{t_{36} > t_0 \space | \space T_0 \text{\textasciitilde} t_{36} \space \& \space H_0 \text{ is true}\}\\
&= P\{t_{36} > 0.3878 \space | \space T_0 \text{\textasciitilde} t_{36} \space \& \space H_0 \text{ is true}\}\\
&= 1- \text{tcdf}(-999, 0.3878, 36) \qquad \text{(Ti 83)}\\
&= 1 - 0.6498\\
&\approx 0.3502
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Summarized T-Test Documentation](https://www.rdocumentation.org/packages/BSDA/versions/1.2.0/topics/tsum.test)

##### Using Base R
```
tsum.test(mean.x = 65.1662, s.x = 2.5442, n.x = 37,
    alternative = "greater", mu = 65, conf.level = 0.95)

**********************************Output***************************************
One-sample t-Test

data:  Summarized x
t = 0.38779, df = 36, p-value = 0.3502
alternative hypothesis: true mean is greater than 65
95 percent confidence interval:
 64.45605       NA
sample estimates:
mean of x
  65.1622
```

##### Using ISCAM function
```
iscamonesamplet(xbar = 65.1662, sd =2.5442, n = 37,
    hypothesized = 65, alternative = "greater", conf.level = 0.95)

**********************************Output***************************************
One Sample t test

mean = 65.1622, sd = 2.5442,  sample size = 37
Null hypothesis       : mu = 65
Alternative hypothesis: mu > 65
t-statistic: 0.3878
95 % Confidence interval for mu: ( 64.31392 ,  66.01048 )
p-value: 0.3502262
```

#### Draw Conclusion
$\text{p-value} = 0.3502 > 0.05 = \alpha$
$\therefore$ **Fail** to Reject $H_0$

#### State conclusion in context
This data **does not** provide any evidence that the population mean height of college students is over 65 inches.