#### b. Second scenario - unknown population standard deviation
In this second scenario, we are not willing to assume that we know the exact value of the population standard deviation. Therefore, we must use the `t critical value` instead of $z^*$. The critical value is dependent on the sample size through the degrees of freedom. Let’s now repeat the parts above under this different scenario.

**i)** Last year, the engineer had a data set with $n = 9$ and $\bar x = 4.06$, with $s = 0.08$. What was the `95%` confidence interval that they calculated? Show your derivation in detail, carrying as many significant figures as you can.
>Solution
**First** calculate t-score (`t critical value`) $t^*$. Given confidence interval of 95%, CL = Confidence Level = 0.95, degree of freedom = sample size - 1 = 8
$$
\begin{aligned}
\text{CL} &= 0.95\\
P\{T_0 < t^*\} &= 1-\frac{\alpha}{2} \\
&= 1- \frac{1-\text{CL}}{2} = 0.975\\
t^* &= \text{invT}(\text{area to the left, degree of freedom})\\
&= \text{invT}(0.975, 8)\\
&= 2.3060\\
\end{aligned}
$$
**Then** calculate confidence interval
Sample standard deviation $s = 0.08$
Sample mean $\bar{x} = 4.06$
Sample size $n = 9$
Confidence interval is
$$
\begin{aligned}
(\bar x - t^* (\frac{s}{\sqrt n}), \bar x + t^* (\frac{s}{\sqrt n})) &= (4.06 - 2.3060 \times \frac{0.08}{\sqrt 9}, 4.06 + 2.3060 \times \frac{0.08}{\sqrt 9})\\
&= (3.9985, 4.1215)
\end{aligned}
$$

**ii)** Use your calculator to compute the same CI (on a TI-84: `STAT -> TESTS -> TInterval`). Write down your calculator model, your buttons to get to the CI input screen, all of your input values and what they represent, and the final confidence interval.
>Solution
With a Ti 83+ calculator
1\. Press `STAT` button, then select `TESTS`,
2\. Then scroll down to `TInterval`, hit `ENTER`
3\. On the `TInterval` screen, highlight `Stats` and hit `ENTER`
4\. Enter values for $\bar{x}$, `Sx`, `n`, `C-Level`, where $\bar{x}$ `= 4.06` (Sample mean), `Sx = 0.08` (Sample standard deviation), `n = 9` (Sample Size) and `C-Level = 0.95`(Confidence Level)
5\. Select `Calculate` and hit `ENTER`
6\. We have the result of `(3.9985, 4.1215)`.

**iii)** What is the width of the CI that you calculated? (please show how you derive it and report your answer to the `4th` decimal place)
>Solution
We have the resulting CI from `part ii`, which is `(3.9985, 4.1215)`, the width of the CI is
$$
\begin{aligned}
\text{Width of CI} &= \text{Upper bound} - \text{Lower bound}\\
&= 4.1215 - 3.9985\\
&= 0.1230
\end{aligned}
$$

**iv)** Suppose that the engineer wants to have a smaller width this year when they compute the CI. Write down a formula to express the width of the CI and then explain how changing the sample size affects the width of the interval. Explain carefully – do not simply say something like “as the sample size increases the CI width increases”.
>Solution
$$
\begin{aligned}
\text{Upper bound} &= \bar{x} + t^* (\frac{s}{\sqrt{n}})\\
\text{Lower bound} &= \bar{x} - t^* (\frac{s}{\sqrt{n}})\\
\text{Width of CI} &= \text{Upper bound} - \text{Lower bound}\\
&= \bar{x} + t^* (\frac{\sigma}{\sqrt{n}}) - (\bar{x} - (t^* \frac{\sigma}{\sqrt{n}}))\\
&= 2 t^* (\frac{s}{\sqrt{n}})
\end{aligned}
$$
With $t*, s$ being constant, as sample size `n` increases, the width of CI decreases; as sample size `n` decreases, the width of CI increases.

**v)** Suppose that the target width for the `95%` CI this year is `0.06 mm`. What sample size is necessary to achieve that width, given the assumptions that the engineer is willing to make? List the assumptions explicitly. Use the **TEA** method: `T = try a value, E = evaluate the outcome, A = adjust the value` (repeat as necessary). Should your calculations along the way by constructing a table with columns:
1\. Value for $n$;
2\. $t^*$ critical value with n-1 degrees of freedom,
3\. achieved width,
4\. comparison to target,
5\. direction for adjustment; and with rows for each value that you try.
>Solution
Using excel to run simulation, we have

| n  | t-score | Achieved width | Comparison to target | Adjustment |
|:--:|-------|----------------|----------------------|------------|
| 18 | 2.10982 | 0.07957 | Greater | Larger n |
| 20 | 2.09302 | 0.07488 | Greater | Larger n |
| 24 | 2.06866 | 0.06756 | Greater | Larger n |
| 28 | 2.05183 | 0.06204 | Greater | Larger n |
| 32 | 2.03951 | 0.05769 | Less |   Smaller n|
| 31 | 2.04227 | 0.05869 | Less | Smaller n|
| **30** | 2.04523 | **0.05974** | Approximately Equal | $\approx$ 0.06 |
The sample size has to be `30` to achieve `95%` of CI with the width of `0.06` mm.
> **Note**
By rounding `n` up to the nearest integer, the width of the Confidence Interval would be **slightly smaller** than desired value (assume this is what we want).

**vi)** Calculate the necessary sample size for widths in the interval `0.04` to `0.08` (by `0.01` changes) and plot the sample size versus the width to see the trade-off between sample size and `95%` CI width.
>Solution
Confidence Interval of 95%. Using the similar procedure (**TEA**) from `part v`, we have (Using excel to run the simulation)

| Actual Width of CI | Approximate Value | Sample size  |
|:-----------:|-----------------|:---:|
| 0.04 | 0.03997 | 64 |
| 0.05 | 0.04986 | 42 |
| 0.06 | 0.05974 | 30 |
| 0.07 | 0.06919 | 23 |
| 0.08 | 0.07957 | 18 |
![Sample Size vs. Width Of CI](/assets/sample_size_width_of_ci_t_interval.png)

#### c. Comparing these two scenarios by discussing:
**i)** the effect on the required sample size, depending on whether you know the population standard deviation or whether you are estimating it
>Solution


**ii)** the desired width’s effect on the required sample size in both scenarios
>Solution
In both scenarios, to pursure a smaller width of a fixed Confidence Interval, we need to increase the sample size.

#### d. Solidify your understanding
Writing two or more statements that Dr. A could use as fill-in-the-blank questions on the final exam. Underline the part(s) that should be the blank(s).
>Solution
1\. To achieve a smaller width of a fixed Confidence Interval, we should ______ the sample size. (Answer: **increases**)
2\.