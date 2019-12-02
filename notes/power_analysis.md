## Power

$H_0: \mu = 4$
$H_A: \mu \ne 4$
$\mu_A = 4.3$
$n = 50$
$s = 0.8$

$\alpha = 0.05$

$$
\begin{aligned}
t* &= \text{invT}(1-\frac{\alpha}{2}, n-1)\\
&= \text{invT}(0.975, 49)\\
&\approx 2.01
\end{aligned}
$$

$$
\begin{aligned}
t_0 &= \frac{\bar{x} - \mu_0}{s/\sqrt{n}}\\
\to x* &= \mu_0 + t^* * \frac{s}{\sqrt{n}}\\
&= 4 + (2.01)(\frac{0.8}{\sqrt{50}})\\
&= 4.227
\end{aligned}
$$

The data set (size of 50) with $s=0.8$ has the power of `0.739` to detect $\mu$ of `4.3` versus `4.0`.
