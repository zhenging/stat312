## Hypothesis Test on Independence

> Credit: Dr. A

### Example G
In a study a hypertension and smoking habits, participants were categorized as non-smokers, moderate smokers, or heavy smokers and tests were run to decide if they have hypertension or not? The data is summmarized below. Are the variables independent?
|   | Non-smokers | Moderate Smokers | Heavy Smokers | Totals |
|---|-------------|------------------|---------------|--------|
| Hypertension    | 21 | 36 | 30 | 87 |
| No Hypertension | 48 | 26 | 19 | 93 |
| Totals          | 69 | 62 | 49 | 180 |

#### Research Question
Is hypertension independent of smoking status?
> Remember: $P(A \cap B) = P(A) * P(B)$

+ **Population of Interest**: We are not told any information about these participants so we can not justify a particular population.

> Like many textbook problems, there is very little context given for this data; however, we can still use it to learn the process.

#### Perspective
All tests on Independence are set up the same way. Only the data differs.
There are no population parameters to be defined.

#### Data Collection
We do assume a random sample for this HT. Data is collected for each observation unit for two categorical variables and create a contingency table as above.
Sample size: $n = 180$

#### State $H_0 \& H_A$
$H_0$: Smoking status and hypertension **are** independent.
$H_A$: Smoking status and hypertension **are Not** independent.

#### Choose $\alpha$
Use the standard value of $\alpha = 0.05$

#### Define test statistic & distribution
Interpret the contingency table:
Let $H$ denote person has hypertension. For a randomly selected person
$$
\begin{aligned}
P(H) = \frac{87}{180}, \space P(H^C) = \frac{93}{180}
\end{aligned}
$$
Let $S_0, S_1, S_2$ denote the three smoky statues.
$$
\begin{aligned}
P(S_0) = \frac{69}{180}, \space P(S_1) = \frac{62}{180}, \space P(S_2) = \frac{49}{180}
\end{aligned}
$$

Let $O_{ij}$ be the count of person with hypertension level of $i$ and smoking status of $j$.
Assuming $H_0$ is true, we calculate the number of cases we expect to see in each cell of the table.
$$
\begin{aligned}
E_{ij} &= n * (\frac{\text{total count in row i}}{n}) * (\frac{\text{total count in column j}}{n})\\
&= \frac{\text{(total count in row i)} * \text{(total count in column j)}}{n}
\end{aligned}
$$

Expected Counts:
|   | Non-smokers | Moderate Smokers | Heavy Smokers |
|---|-------------|------------------|---------------|
| Hypertension   | $\frac{87 * 69}{180}=33.350$ | $\frac{87 * 62}{180}=29.967$ |  $\frac{87 * 49}{180} = 23.683$ |
| No Hypertension | $\frac{93 * 69}{180}=35.650$ | $\frac{93 * 62}{180}=32.033$ | $\frac{93 * 49}{180}=25.317$ |

|   | Non-smokers | Moderate Smokers | Heavy Smokers |
|---|-------------|------------------|---------------|
| Hypertension    | 21 | 36 | 30 |
| No Hypertension | 48 | 26 | 19 |

Test Statistic is $\Chi^2$ (chi-squared)

$$
\begin{aligned}
\Chi_0^2 &\text{\textasciitilde} \Chi_v^2\\
v &= (\text{No. of rows} - 1)* (\text{No. of columns} - 1)\\
&= 1 * 2 = 2\\
\Chi_0^2  &= \Sigma_i \Sigma_j \frac{(O{ij-E_{ij}})^2}{E_{ij}}\\
&= \frac{(21 - 33.350)^2}{33.350} + \frac{(36 - 29.967)^2}{29.967} + \frac{(30 - 23.683)^2}{23.683}\\
&+ \frac{(48 - 35.650)^2}{35.650} + \frac{(26 - 32.033)^2}{32.033} + \frac{(19 - 25.316)^2}{25.316}\\
&\approx 14.4634
\end{aligned}
$$

#### Graph
![Chi-squared Test on Independence](/assets/chisq_test_independence_example.png)

#### Calculate `p-value`
$$
\begin{aligned}
\text{p-value} &= P\{\text{get our value or more extreme } \space | \space H_0 \text{ is true}\}\\
&= P(\Chi_0^2 > 14.4634 \space | \space H_0 \text{ is true})\\
&= \Chi^2\text{cdf}(14.4634, 999, 2)\\
&\approx 0.0007233
\end{aligned}
$$

#### Calculate `p-value` in `R`
> [Chi-squared Test Documentation](https://www.rdocumentation.org/packages/stats/versions/3.6.1/topics/chisq.test)

##### Using Base R
```
elementary = c(14, 37, 32)
secondary = c(19, 42, 17)
college = c(12, 17, 10)
M = as.table(rbind(elementary, secondary, college))
dimnames(M) = list("Education" = c("Elementary", "Secondary", "College"),
  "Number of Children" = c("0-1", "2-3", "Over 3"))

Xsq = chisq.test(M)
print("Observed Counts")
Xsq$observed
print("Expected Counts")
Xsq$expected
Xsq

**********************************Output***************************************
[1] "Observed Counts"
                   Smoker Status
Hypertension status Non Moderate Heavy
                Yes  21       36    30
                No   48       26    19
[1] "Expected Counts"
                   Smoker Status
Hypertension status   Non Moderate    Heavy
                Yes 33.35 29.96667 23.68333
                No  35.65 32.03333 25.31667

	Pearson's Chi-squared test

data:  M
X-squared = 14.464, df = 2, p-value = 0.0007232
```

##### Using ISCAM function
```
iscamchisqprob(xval = Xsq$statistic, df = 3)

**********************************Output***************************************
probability: 0.0007232
Graph
```

#### Draw Conclusion
$\text{p-value} = 0.0007233 < 0.05 = \alpha$
$\therefore$ **Reject** $H_0$ in favor of $H_A$.

#### State conclusion in context
This data **provides strong evidence** that smoking status (non-smoker, moderate, heavy) is **not** independent of having hypertension or not.

#### Questions
1. $\Chi_0^2$ and $\chi_0^2$