### Central Limit Theorem For Sample Means
Suppose $X$ is a random variable with a distribution that may be known or unknow (it can be any distribution). Using a subscript that matches the random variable, suppose:
a. $\mu_X = $ the mean of $X$
b. $\sigma_X = $ the standard deviation of $X$.

If you draw random sample of sizes $n$, then as $n$ increase, the random variable $\bar {X}$ which consist of sample means, tends to be **normally distributed** and
$\bar{X} \text{\textasciitilde} N(\mu_x, \displaystyle\frac{\sigma_X}{\sqrt{n}})$

+ **Sampling distribution of the mean** - the distribution of the random variable $\bar{X}$, which consist of sample means
+ As the sample size $n$ increases, the **sampling distribution of the mean** approaches a normal distribution.

#### Example
In a recent study reported Oct. 29, 2012 on the Flurry Blog, the mean age of tablet users is 34 years. Suppose the standard deviation is 15 years. Take a sample of size n = 100.
a. What are the mean and standard deviation for the sample mean ages of tablet users?
b. What does the distribution look like?
c. Find the probability that the sample mean age is more than 30 years (the reported mean age of tablet users in this particular study).
d. Find the 95th percentile for the sample mean age (to one decimal place).
>Solution
a. Since the sample mean tends to target the population mean, we have $\mu_X = \mu = 34$. The sample standard deviation is given by $\sigma_X = \frac{\sigma}{\sqrt{n}} = \frac{15}{\sqrt{100}} = 1.5$
b. The central limit theorem stats that for large sample sizes(n), the sampling distribution will be approximately normal.
c. The possibility that the sample mean age is more than 30 is given by
`P(X>30) = normalcdf(30, 999999, 34, 1.5) = 0.9962`
d. Let k = the 95th percentile
`k = invNorm(0.95, 34, 1.5) = 36.5`