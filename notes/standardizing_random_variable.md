### Standardizing Random Variables
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
