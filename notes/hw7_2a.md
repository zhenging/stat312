### 2. Sample Size Calculations
In designing a study, we need to decide what sample size will be sufficient for our needs. This problem will step you through the logic to make that decision for two scenario, using the “confidence interval width” approach. This is only one of several ways that people make this decision.

#### a. First scenario - known population standard deviation
A quality control engineer needs to certify the wall thickness of a particular type of glass bottle. The engineer plans to randomly choose n bottles manufactured over the past month from the set of all bottles manufactured during that time. They will measure the wall thickness in millimeters for each bottle, then use this data to construct a `95%` confidence interval on the mean wall thickness. Suppose that the engineer is very sure that the population standard deviation of wall thickness is `0.08` mm.

**i)** When we know the population standard deviation, **we can use a $Z_{0,1}$ distribution** instead of a `t distribution` for finding a confidence interval on the population mean. The $(1-\alpha)\%$ CI on $\mu$ formula is then: $(\bar x - z^* \frac{\sigma}{\sqrt n}, \bar x + z^* \frac{\sigma}{\sqrt n})$ where $z^*$ statisfies $P\{Z_{0,1} < z^*\} = 1-\frac{\alpha}{2}$.
Last year, the engineer computed the `95%` CI on the population mean wall thickness from a data set with $n = 9$ and $\bar x = 4.06$, with $\sigma = 0.08$. What was the interval that they calculated? Show your derivation in detail, carrying as many significant figures as you can.
>Solution
**First** calculate z-score $z^*$. Given confidence interval of 95%, CL = Confidence Level = 0.95
$$
\begin{aligned}
\text{CL} &= 0.95\\
P\{Z_{0,1} < z^*\} &= 1-\frac{\alpha}{2} \\
&= 1- \frac{1-\text{CL}}{2} = 0.975\\
z^* &= \text{invNorm}(\text{probability, mean, standard deviation})\\
&= \text{invNorm}(0.975, 0, 1)\\
&= 1.95996\\
\end{aligned}
$$
**Then** calculate confidence interval
Population standard deviation $\sigma = 0.08$
Sample mean $\bar{x} = 4.06$
Sample size $n = 9$
Confidence interval is
$$
\begin{aligned}
(\bar x - z^* \frac{\sigma}{\sqrt n}, \bar x + z^* \frac{\sigma}{\sqrt n}) &= (4.06 - 1.95996 \times \frac{0.08}{\sqrt 9}, 4.06 + 1.95996 \times  \frac{0.08}{\sqrt 9})\\
&= (4.0077344, 4.1122656)
\end{aligned}
$$

**ii)** Use your calculator to compute the same CI (on a TI-84: `STAT` -> `TESTS`  -> `ZInterval`). Write down your calculator model, your buttons to get to the CI input screen, all of your input values and what they represent, and the final confidence interval.
>Solution
With a Ti 83+ calculator
1\. Press `STAT` button, then select `TESTS`,
2\. Then scroll down to `ZInterval`, hit `ENTER`
3\. On the `ZInterval` screen, highlight `Stats` and hit `ENTER`
4\. Enter values for $\sigma$, $\bar{x}$, `n`, `C-Level`, where $\sigma = 0.08$ (Population standard deviation. **Given**), $\bar{x} = 4.06$ (Sample mean), $n = 9$ (Sample Size) and `C-Level = 0.95`(Confidence Level)
5\. Select `Calculate` and hit `ENTER`
6\. We have the result of `(4.0077, 4.1123)`.

**iii)** What is the width of the CI that you calculated? (please show how you derive it and report your answer to the `4th` decimal place)
>Solution
We have the resulting CI from `part ii`, which is `(4.0077, 4.1123)`, the width of the CI is
$$
\begin{aligned}
\text{Width of CI} &= \text{Upper bound} - \text{Lower bound}\\
&= 4.1123 - 4.0077\\
&= 0.1046
\end{aligned}
$$

**iv)** Suppose that the engineer wants to have a smaller width this year when they compute the CI. Write down a formula to express the width of the CI and then explain how changing the sample size affects the width of the interval.
>Solution
$$
\begin{aligned}
\text{Upper bound} &= \bar{x} + z^* \frac{\sigma}{\sqrt{n}}\\
\text{Lower bound} &= \bar{x} - z^* \frac{\sigma}{\sqrt{n}}\\
\text{Width of CI} &= \text{Upper bound} - \text{Lower bound}\\
&= \bar{x} + z^* \frac{\sigma}{\sqrt{n}} - (\bar{x} - z^* \frac{\sigma}{\sqrt{n}})\\
&= 2 z^* \frac{\sigma}{\sqrt{n}}
\end{aligned}
$$
With $z*, \sigma$ being constant, as sample size `n` increases, the width of CI decreases; as sample size `n` decreases, the width of CI increases.

**v)** Suppose that the target width for the `95%` CI this year is `0.06` mm. What sample size is necessary to achieve that width, given the assumptions that the engineer is willing to make? List the assumptions explicitly.
>Solution
**Assumptions**
1\. A simple random sample is used.
2\. Data is from normally distributed population.
$$
\begin{aligned}
z^* &= 1.95996\text{(From part i)}, \sigma = 0.08 \text{(Given)}\\
\text{Width of CI} & = 0.06\\
&= 2 z^* \frac{\sigma}{\sqrt{n}} &\text{(From part iv)}\\
\Rightarrow n &= \bigg( 2 z^* \frac{\sigma}{\text{Width of CI}}\bigg)^2\\
&= \bigg( 2 \times 1.95996 \times \frac{0.08}{0.06}\bigg)^2\\
&= 27.316929 \approx 28
\end{aligned}
$$
The sample size has to be `28` to achieve `95%` of CI with the width of `0.06` mm.
> Note
By rounding `n` up to the nearest integer, the width of the Confidence Interval would be **slightly smaller** than desired value (assume this is what we want).

**vi)** Calculate the necessary sample size for widths in the interval `0.04` to `0.08` (by `0.01` changes) and plot the sample size versus the width to see the trade-off between sample size and `95%` CI width.
>Solution
Confidence Interval of 95%. Using the similar procedure from `part v`, we have

| Width of CI | Sample size (n) | Rounded (n)  |
|:-----------:|-----------------|:---:|
| 0.04 | 61.4630912256 | 62 |
| 0.05 | 39.3363783844 | 40 |
| 0.06 | 27.3169294336 | 28 |
| 0.07 | 20.0695808084 | 21 |
| 0.08 | 15.3657728064 | 16 |
![Sample Size vs. Width Of CI](/assets/sample_size_width_of_ci_z_interval.png)
