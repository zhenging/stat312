### 06 Summarizing Data

#### Sample Size: $n$
+ The number of cases (AKA observational units, participants, people/places/things that you collected data about) is the sample size.

#### Measures of Central Tendency (typical values)
+ **Sample Mean** (the average): $\bar{X} = \displaystyle \frac{\sum_{j=1}^n x_j}{n}$
+ **Sample Median** (the middle number): the median is the middle number in a sorted list of data. If there are even number of data points, average the two middle numbers.
+ **Sample Mode** (most frequent): the data point repeated the most often. For continuous data, we often have no repeated data, so we might use the center of the histogram bin with the highest frenquency.

#### Measures of Dispersion ("how spread out the data is")
+ **Sample Variance** (the average squared deviation from the mean)
$$
\begin{aligned}
\sigma^2 = \frac{\sum_{j=1}^n (x_j - \bar{x})^2}{n-1}
\end{aligned}
$$
+ Sample Standard Deviation (the square root of the variance)
+ Sample IQR (width of the middle 50%) : **IRD = Q3 - Q1**
+ Sample Range (max - min): **Range = Max{x_j} - Min{x_j}**

#### Quantiles and Quartiles
$Q_p$ is the "100*p" quantile. For example, $Q_{0.1}$ is the $10^{\text{th}}$. THe quantile is the number that has the given probability to its left. More specifically, $Q_p$ and $p$ statisfy:
$$
\begin{aligned}
P\{ X \le Q_p\} = p
\end{aligned}
$$

#### Mean, Standard Deviation
For quantiative data that are roughtly symmetric and "mound-shaped", the most common way to summarize the data is by giving the mean and the standard deviation. However, if the data is skewed or has Outliers, it is more common to use the 5 number summary, discussed below.

#### 5 Number Summary
+ Minimum value
+ First Quartile
+ Median
+ Third Quartile
+ Maximum value

#### Outliers
Outliers are data points which are far away from the rest of the data. There are several methods for computing outlia
