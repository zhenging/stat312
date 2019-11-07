### Student t's Distribution (aka the `t` distribution)
+ 1 parameter (v): degree of freedom
+ Shape like Normal, but fatter tail
+ Centered at 0
+ $ \text{VAR} = \begin{cases} \displaystyle\frac{v}{v-2} &\text{ if } v > 2\\  \infty &\text{ if } 1 < v \le 2 \\ \text{undefined} &\text{otherwise}\end{cases}$
+ As $v \to \infty$, $t_v \to \text{Normal}(0, 1)$

If you draw a sample random sample of size n from a population that has an approximately normal distribution with mean $\mu$ and unknown popoluation standardf deviation $\sigma$ and calculate the t-score $t = \displaystyle \frac{\bar{x} - \mu}{(\frac{s}{\sqrt{n}})}$, then the t-scores follow a Student's t-distribution with $n-1$ degree of freedom. The t-scire has the same interpretation as the z-score, It measures how far $\bar{x}$ is from its mean $\mu$. For each sample size, there is a different Student's t-distribution.

The notation for the Student's t-distribution (using T as the random variable) is:
+ $T\text{\textasciitilde} t_{df}$ where $df = n -1$
For example , if we have a sample size $n=20$ items, then we calculate the degree of freedom as $df = n-1 = 19$ and we wrte the distribution as $T\text{\textasciitilde} t_{19}$

If the population standard deviation is unkown, the error bound for a population mean is
+ $EBM = (t_{\frac{\alpha}{2}})(\frac{s}{\sqrt{n}})$
+ $t_{\frac{\alpha}{2}$ is the t-score with area to the right equal to $\frac{\alpha}{2}$,
+ use $df = n-1$ degree of freedom, and
+ $s$ = sample standard deviation.

The format for the confidence interval is
$(\bar{x} - EBM, \bar{x} + EBM)$

#### Example
Suppose you do a study of acupuncture to determine how effective it is in relieving pain. You measure sensory rates for 15 subjects with the results given. Use the sample data to construct a 95% confidence interval for the mean sensory rate for the population (assumed normal) from which you took the data.
The solution is shown step-by-step and by using the TI-83, 83+, or 84+ calculators.
`8.6; 9.4; 7.9; 6.8; 8.3; 7.3; 9.2; 9.6; 8.7; 11.4; 10.3; 5.4; 8.1; 5.5; 6.9`
>Solution

