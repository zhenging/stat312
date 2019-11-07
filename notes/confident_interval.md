### Confident Interval

To construct a confident interval for a single unknown population mean $\mu$, where **the population standard deviation is known**, we need $\bar{x}$ as an estimate for $\mu$ and we need the margin of error. Here the margin of error (EBM) is called the error bound for a population mean. The sample mean $\bar{x}$ is the point estimate of the unknown population mean $\mu$.
The confidence interval estimate will have the form:
(point estimate - error bound, point estimate + error bound) or, in symbols, $(\bar{x} - EBM, \bar{x} + EBM)$

#### Example
Suppose we have collected data from a sample. We know the sample mean but we do not know the mean for the entire population. The sample mean is seven, and the error bound for the mean is 2.5.
>Solution
Let the sample mean be $\bar {x}$ and error of bound be $EBM$
$\bar{x} = 7$
$EBM = 2.5$
The confidence interval is $(7-2.5, 7+2.5)$, namely $(4.5, 9.5)$
If the confidence level (CL) is 95%, then we say that "We estimate with 95% confidence that the tru value of the population mean is between 4.5 and 9.5".

##### Calculating the Confidence Interval
To construct a confidence interval estimate for an unknown population mean, we need data from a random sample. The steps to construct and interpret the confidence interval are:
+ Calculate the sample mean $\bar{x}$ from the sample data. Remeber, in this section we already know the population standard deviation $\alpha$.
+ Find z-score that correponds to the confidence level.
+ Calcuate the error bound EBM,.
+ Construct the confidentce interval.
+ Write a sentence that interpret the estimate in the context of the stituation in the problem.

##### Find the z-score for the Stated Confidence Level
//todo

##### Calculating the Error Bound (EBM)
The error bound formula for an unknown population mean $\mu$ when the population standard deviation $\alpha$ is know is
$$
\begin{aligned}
EBM = (z_{\frac{\alpha}{2}}) (\frac{\sigma}{\sqrt{n}})
\end{aligned}
$$

##### Constructing the Confidence Interval
The confidence interval estimate has the format $(\bar{x} - EBM, \bar{x} + EBM)$.
$CL + \frac{\alpha}{2} + \frac{\alpha}{2} = 1$

![confidence interval](/assets/d41c5a290f2f6753460b1119861889bfa18caf65.jpeg)

##### Writing the Interpretation
We estimate with __% confidence that the tru population mean (include the context of the problem) is between __ and __ (include appropriate units).

##### Example
Suppose scores on exams in statistics are normally distributed with an unknown population mean and a population standard deviation of three points. A random sample of 36 scores is taken and gives a sample mean (sample mean score) of 68. Find a confidence interval estimate for the population mean exam score (the mean score on all exams).
>Solution
To find the confidence interval, you need the sample mean, $\bar{x}$, and the EBM
+ Sample size: $n = 30$
+ Sample mean: $\bar{x} = 68$
+ Population standard deviation: $\sigma = 3$
+ $EBM = (z_{\frac{\alpha}{2}}) (\frac{\sigma}{\sqrt{n}})$
+ The confidence level is 90% ($CL=0.90$)
$CL = 0.90$ so $\alpha = 1-CL = 0.10$
$\frac{\alpha}{2} = 0.05$ and $z_{\frac{\alpha}{2}}$

The are to the right of $z_{0.05}$

