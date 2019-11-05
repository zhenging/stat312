### 07  Sampling Distributions

#### Data Distribution
**1\. Numerical Summaries**
+ Point summaries: mean, median, st dev, IQR, etc.
+ Summary intervals: The middle k% of the data is is (left -> right). (**Open Interval**)
  + 50% summary interval = $Q1 \to Q3$
  + 80% summary interval = $Q_{0.1} \to Q_{0.9}$
  + 95% summary interval = $Q_{0.025} \to Q_{0.975}$

**2\. Graphical Summaries**
+ Categorical: bar plots, dot plots
+ Numerical: histogram, box plots, stem-and-leaf-plots

**3\. Symmetric versus Skewed**
+ Strong left skewed
+ Symmetric
+ Strong right skewed

**4\. Outliers verse Skewed**
a. Both can affect the value fo the mean a lot
b. Outliers have very little effect on median
c. Oulliers = Data point characteristic; which skew = distribution characteristic

**5\. Model Data with probability model (=family + parameter values)**
+ Choose family: features like continuous vs discrete, bounded or unbounded on the left and right; experience in that field of engineering; compare histogram shape to pdf shape.
+ Choose parameter values: several methods are available (method of moment, MLE, standard practice). Most commone practice: $\hat \mu = \bar{x}$ and $\hat \sigma = s$
+ Check the quality of the fit:
  - Plot pdf on the top of histogram -  not very reliable judgement
  - QQ plot - qualitative judgement
  - Goodness of fit Hypothesis text - quantitative, but very sensitive to slight mismatch.

> QQ plot looks at the fitness of data points on a theoretical distribution familiy, compares the data set and the theoretical distribution, and does a qualitative judgement.

#### Sampling Distributions
1. A sample statistic is a function of the data, e.g. mean, st dev, minimum
2. A sampling distribution is the probability distribution of a sample statistic.

##### Examples A: Count of "successes"
+ Data collected is binary => success or failures for each observational unit.
+ Observational units are independent.
+ Every observational unit has the same probability of success.
+ Notation: $C$ = count of successes.
+ $C \text{\textasciitilde} \text{Binomial}(n, \pi)$ where $n$ is the sample size, and  $\pi$ = population propotion.
+ $f_C(x) = \dbinom{n}{x} \pi^x (1-\pi)^{n-x}$, where $x$ = count of successes

![count_of_successes](/assets/count_of_successes.png)

##### Examples B: Sample Mean
+ Data collected is quantitative, measurement data.
+ Observational units are independent.
+ Observational unit's meansurements are from the same distribution.
$P\{X_j < t\} = P\{X < t\}$ for all real values of $t$ and $j=1, 2, \cdots, n$
+ Notation: $\bar{X} = \displaystyle\frac{1}{n}\sum^n_{j=1} X_j$
+ Three cases for distribution of $\bar{X}$:

Case I: Data is normally distrbuted and population variance is known with certainty: $X \text{\textasciitilde} N(\mu, \sigma^2)$.
$$
\begin{aligned}
\bar{X} \text{\textasciitilde} N(\mu, \frac{\sigma^2}{n})
\end{aligned}
$$

Case II: Data has any distribution family and population variance is known with certainty: (**Central Limit Theorem**)
$$
\begin{aligned}
\bar{X} \text{\textasciitilde \space approximately } N(\mu, \frac{\sigma^2}{n})
\end{aligned}
$$

Case III: Data has any distribution family, population variance is estimated with sample variance, and sample size is large enough. (We do not know the variance of $t$ or how to estimate it)
$$
\begin{aligned}
\bar{X} \text{\textasciitilde \space approximately } t_{n-1}
\end{aligned}
$$