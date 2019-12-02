## Mileage By Brands of Tyres

### Setup
Source for data: https://datascienceplus.com/oneway-anova-explanation-and-example-in-r-part-1/
+ 4 different brands of tires were tested to determine if they had different population mean miles
of use.
+ 15 tires of each brand were randomly selected.
+ Variables:
  - Brands = factor with 4 levels: Apollo, Bridgestone, CEAT, Falken
  - Mileage = thousands of miles


### Key R code for ANOVA
```r
tyre = read.csv("tyre.csv") # if you have it on your local hard drive
summary(tyre)

tyres.aov = aov(Mileage ~ Brands, tyre)
tyres.aov

summary(tyres.aov)
```

### Summary Output
```
Brand        N	Mean        SD     Median      Min      Max
Apollo	     15	34.79913  2.21889  34.83600  30.62300  38.328
Bridgestone  15	31.78013  2.19977  31.99500  27.87900  35.006
CEAT         15	34.76121  2.53184  34.78336  30.42748  41.050
Falken	     15	37.62467  1.69520  37.38200  34.31000  40.663
```

### ANOVA Output
```
Call:
   aov(formula = Mileage ~ Brands, data = tyre)

Terms:
                  Brands Residuals
Sum of Squares  256.2908  266.6495
Deg. of Freedom        3        56

Residual standard error: 2.182108
Estimated effects may be unbalanced
            Df Sum Sq Mean Sq F value   Pr(>F)
Brands       3  256.3   85.43   17.94 2.78e-08 ***
Residuals   56  266.6    4.76
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

1\. Using the boxplots only, what can you conclude about the mileage of the different brands of tires?
> **I\.** The Bridgestone tires have a lower median then other three and is slightly left-skewed. Nearly all of the middle 50% of thoes tires have lower mileage than the middle 50% of the other tires. In other words, the box of Bridgestone is almost completely to the left of the other boxes.
**II**. The Apollo and CEAT tires have roughly the same boxplot, with very similar left whisker ends, first quartiles, second quartiles, and third quartiles. The right whisker ends are slightly different with Apollo tires having a somewhat larger value.
**III**. Overall, the Falken tires have the best performance with a first, second, and third quartiles, being larger than all three of the other third quartiles.
**IV**. Both Apollo and Falken tires are very symmetric. Bridgestone tires have a slightly left-skewed distribution. The CEAT distribution is also slightly left-skewed and it has a large upper outlier.

2\. This **ANOVA** analysis is assuming that all 4 populations have a common population variance.
a) Using the boxplots only, how reasonable is this assumption?
> The dispersion of the four types of tires is similar, but the not the same. The CEAT tires have a larger dispersion, with both a large left whisker and an upper outlier. The dispersion of the Falken tires is propably the smallest because the box is the smallest and the whisker are not much larger than the other types of tires. The Appollo is wider than Falken and Bridgestone.

b) Using the output, what is the estimate of the common standard deviation?
> The estimate of the common standard deviation is the Residual standard error, which is `2.1821` thousand miles.

3\. What is the mean sum of squares error value?
> The mean sum of squares error value is in the row labeled “Residuals” in the summary table and has the value of `4.76`.

4\. What are the $H_0$ and $H_A$ statements that correspond to the listed `p-value`?
> The p-value of `2.78e-08` corresponds to the following HT
$H_0: \tau_{\tiny\text{Falken}} = \tau_{\tiny\text{CEAT}} = \tau_{\tiny\text{Bridgestone}} = \tau_{\tiny\text{Apollo}} = 0$
$H_A$: There is at least one j in `{Falken, CEAT, Bridgestone, Apollo}` such that $\tau_j \ne 0$

5\. Using the standard value for $\alpha$, what is your conclusion for this hypothesis test?
> The p-value of `2.78e-08` is far less then $\alpha = 0.05$, therefore, we have strong evidence to reject the null hypothesis in favor of the alternative hypothesis.
This data set provides very strong evidence that the four types of tires do not have the same population mileage values.

6\. Construct a `95%` CI on the population mean mileage for `Bridgestone` tires.
> Formula: $\text{CI} = (\overline{y_{\tiny {J.}}} \pm t^* (\sqrt{\frac{MS_E}{n}}))$
$$
\begin{aligned}
\overline{y_{\tiny {J.}}} &= 31.78013 \quad MS_E = 4.76 \quad n = 15\\
t^* &= \text{invT}(1-\frac{\alpha}{2}, \text{degree of freedom of error})\\
&= \text{invT}(0.975, 56)\\
&= 2.00324\\
\text{CI} &= (31.78013 - 2.00324 * \sqrt{ \frac{4.76}{15}}, 31.78013 + 2.00324 * \sqrt{ \frac{4.76}{15}})\\
&= (30.65165752, 32.90860249)
\end{aligned}
$$

7\. Construct a `95%` CI on the population mean mileage for `Falken` tires.
> Formula: $\text{CI} = (\overline{y_{\tiny {J.}}} \pm t^* (\sqrt{\frac{MS_E}{n}}))$
$$
\begin{aligned}
\overline{y_{\tiny {J.}}} &= 37.62467 \quad MS_E = 4.76 \quad n = 15\\
t^* &= \text{invT}(1-\frac{\alpha}{2}, \text{degree of freedom of error})\\
&= \text{invT}(0.975, 56)\\
&= 2.00324\\
\text{CI} &= (37.62467 - 2.00324 * \sqrt{ \frac{4.76}{15}}, 37.62467 + 2.00324 * \sqrt{ \frac{4.76}{15}})\\
&= (36.49619752, 38.75314249)
\end{aligned}
$$

8\. Add your `95%` CIs on the individual means just underneath the boxplots in the graph. How do these compare. Explain why this is true.
>  The CIs are near the boxes in the boxplots because they are centered on the sample and because the distribution are approximately symmetrix, these means are close to the sample medians. The widths of the CIs are not directly related to the widths of the boxes however, because the CIs are built using the standard deviattion while the box width are the IQRs.
![Graph](/assets/anova_tires_ci.png)

9\. Construct a `95%` CI on the difference in population mean mileages for (Falken – Bridgestone)
> Formula: $\text{CI} = \bigg((\overline{y_{\tiny {J.}}} - \overline{y_{\tiny {k.}}}) \pm t^* (\sqrt{\frac{2*MS_E}{n}})\bigg)$
$$
\begin{aligned}
\overline{y_{\tiny {J.}}} &= 37.62467 \quad \overline{y_{\tiny {K.}}} = 31.78013)\\
MS_E &= 4.76 \quad n = 15\\
t^* &= \text{invT}(1-\frac{\alpha}{2}, \text{degree of freedom of error})\\
&= \text{invT}(0.975, 56)\\
&= 2.00324\\
\text{CI} &= (37.62467- 31.78013 - 2.00324 * \sqrt{ \frac{2 * 4.76}{15}}, 37.62467 - 31.78013 + 2.00324 * \sqrt{ \frac{2 * 4.76}{15}})\\
&= (4.248638907, 7.440441093)
\end{aligned}
$$

10\. Can you get the CI on the difference in means (from question 9) by subtracting the individual CIs (from questions 6 and 7)?
> No. Substraction is a mathematical operation on two numbers, not on intervals.