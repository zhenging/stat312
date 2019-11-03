### 07  Sampling Distributions

#### Standardizing Random Variables
The idea of standardizing a random variable can be applied to other families as well, by substracting the _expected value_ (mean) and dividing by the standard deviation.
$$
\begin{aligned}
\frac{Y -E[Y]}{\sqrt{\textrm{VAR}[Y]}} = \text{standardized version of } Y
\end{aligned}
$$

> Example
Suppose $X \text{\textasciitilde} N(47, 16)$. Then $\mu = 47$ and $\sigma = 4$
$$
\begin{aligned}
P\{X < 50\} &= P\bigg\{\frac{X-\mu}{\sigma} < \frac{50-\mu}{\sigma}\bigg\}\\
&= P\bigg\{\frac{X-47}{4} < \frac{50-47}{4}\bigg\}\\
&= P\big\{Z_{0, 1}\ < \frac{3}{4} \big\}\\
&= 0.773
\end{aligned}
$$

#### Notation
`n` = sample size
`j` is the subscript that denotes the particular one

**Probability VS. Statistics**
$X_j$ - Random Variable (For _probability perspective_)
+ Capital Letter
+ With "Feet"

$x_j$ - Data Value (For _statistics perspective_)

For Example:
Let $X_j$ = height of _jth_ patient in inches, j=1,...,n
$x_j = 64.5$ inches - measuared value subject to measurement error, recording errod, etc.
$X_j$ = height of _4th_ patient (**true value**)

**Population VS. Sample**

| Concept | Population Parameter | Sample Statistic |
|---------|----------------------|------------------|
| mean | $\mu$ | $\bar{x}$ |
| standard deviation | $\sigma$ | $s$ |
| variance | $\sigma^2$ | $s^2$ |
| proportion | $\pi$ | $p$ |

+ The **True value** fo the population parameter is unknown (unless we do a census - collect data from every memeber of the population - in which case, we don't really need to estimate anything).
+ We estimate the value of the population parameter by the sample statistic.
+ Estimate are denoted with "hats", eg. $\hat \mu = \bar{x}$.
+ Seeing $\pi$ as a parameter instead of a number.