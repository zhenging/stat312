## Hypothesis Test on Population Mean (Single Population)

> Credit: Dr. A

### Example D
A company which makes vacuum cleaners has designed a new model. There is some concern that the new model has some issues in the energy it needs. Historically, vacuum cleaners expend `46` kw hours. The company tests `12` vacuum cleaners to calculate the annual kilowatt usage. The sample average was `42` kw and a sample standard deviation of `5.7` kw.

#### Research Question
Is the population mean energy level different from 46?
  + **Population of Interest**: All vacuum cleaners of this new model type
  + **Quantity of Interest**: Population mean annual energy usage

#### Perspective
We want to know if the population mean is different, which would be the "shout it to the world" conclusion.
Let $\mu$ be the population mean energy usage (annual) by this vacuum cleaner of new model.

#### Data Collection
The data is already collected. We assume that a simple random sample was used.
Sample size: `n = 12`
Sample mean: $\bar x = 42$ kw
Sample standard deviation: `s = 5.7` kw
Let $X_j$ be annual energy usage of `jth` vacuum cleaner, where `j=1, 2,... 12

#### State $H_0 \& H_A$
$H_0: \mu = 46$
$H_A: \mu \ne 46$
> **Note**
This is a two-sided HT, which means that sample means that are very large and ones that are very small both provide support for rejecting $H_0$ in favor of $H_A$.

#### Choose $\alpha$
Use the standard value of $\alpha = 0.05$

#### Define test statistic & distribution
**Assumptions**
1. A simple random sample was used.
2. Data is from a normally distributed population.
  a. Since `n` is small, this is important.
  b.  Reasonable assumption since these types of measuremetns are frequently normally distributed.
  c. $\sigma^2 \approx s^2$. Using a `t-distribution` helps compensate for making this assumption.

> **Assume $H_0$ is true**

$$
\begin{aligned}
&\bar{x} = 42, s = 5.7, n = 12, \mu_0 = 46\\
&T_0 = \frac{\bar x - \mu_0}{s/\sqrt n} \\
&T_0 \text{\textasciitilde} t_{n-1}\\
&t_{n-1} = t_{12-1} = t_{11}\\
&t_0 = \frac{42- 46}{5.7/\sqrt{12}} = -2.4309
\end{aligned}
$$

#### Graph
![One sample t test](/assets/one_sample_t_test_two_sides.png)

#### Calculate `p-value`
> [Ti 83 tips](//todo)

$$
\begin{aligned}
\frac{1}{2}\text{(p-value)} &= P\{T_{11} < t_0 \space | \space H_0 \text{ is true}\}\\
&= \text{tcdf}(\underbrace{-99}_{\text{lower bound}}, \overbrace{-2.4309}^{\text{upper bound}}, \underbrace{11}_{\text{degree of freedom}}) \qquad \text{(Ti 83)}\\
&= 0.016678\\
\text{p-value} &= 2 * 0.016678 = 0.03336
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Summarized T-Test Documentation](https://www.rdocumentation.org/packages/BSDA/versions/1.2.0/topics/tsum.test)

##### Using Base R
```
tsum.test(mean.x = 42, s.x = 5.7, n.x = 12,
    alternative = "two.sided", mu = 46, conf.level = 0.95)

**********************************Output***************************************
One-sample t-Test

data:  Summarized x
t = -2.4309, df = 11, p-value = 0.03335
alternative hypothesis: true mean is not equal to 46
95 percent confidence interval:  38.37839 45.62161
sample estimates:
mean of x: 42
```

##### Using ISCAM function
```
iscamonesamplet(xbar = 42, sd = 5.7, n = 12,
    hypothesized = 46, alternative = "two.sided", conf.level = 0.95)

**********************************Output***************************************
One Sample t test

mean = 42, sd = 5.7,  sample size = 12
Null hypothesis       : mu = 46
Alternative hypothesis: mu <> 46
t-statistic: -2.431
95 % Confidence interval for mu: ( 38.37839 ,  45.62161 )
p-value: 0.03335358
```

#### Draw Conclusion
$\text{p-value} = 0.03336 > 0.05 = \alpha$
$\therefore$ **Reject** $H_0$ in favor of $H_A$

#### State conclusion in context
This data set provides strong evidence that the energy usage of these new model vacuum cleaners is different from the historical value of `46` kw.

> **Note**
If `the population mean energy usage` of the new model type is truly `46` kw annually and we sampled `12` vacuum cleaners to test repeatedly, only about `3%` of those samples would have a sample mean as far from 46 as our sample mean is.