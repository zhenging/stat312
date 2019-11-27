### Interpreting Linear Regression Analysis Output

1\. What is/are the explanatory variable(s)?
> Height (in inches)

2\. What is the response variable?
> Weight (in pounds)

3\. Describe the association in the scatterplot.
> The weight and height of the children in this data data have a positive, moderate association. The association is linear for height below 40 inches. Between 40 and 60 inches, there is a set of higher weight children that gives the association a slight upward curve.

4\. State the linear model. (Response variable must have a “hat” to indicate that it is an estimate. Use informative variable names, not `y` and `x`. )
> $\widehat{\text{weight}} = -31.34191 + 1.90904 * (\text{height})$

5\. Check the assumptions of a linear regression model.
a. Linear association between the variables
> The scatterplot of the residuals versus height shows linear relationship when the height is between 0 and 60 inches because the points are randomly scattered and have equal distribution across the red (`residual = 0`) horizontal line. However, the relationship is not perfectly linear for heights between 60 and 140 inches because the residuals get larger as the heights increases. I will process with the analysis for now, but plan to complete a Phase II analysis where I develop seperate models for children under 60 inches and for children over 60 inches.

b. Residuals are approximately normally distributed with mean of zero.
> The QQ plot gives me a significant concern about this assumption because the points have a clear S-shaped curve and do not follow the identity line. In this histogram, we can see that there is a right skew and the residuals are not symmetrically distributed  around zero. Therefore, I will very cautiously proceed.

c. Residuals have constant variance, which is independent of the predictor variable.
> The residuals definitely do not have a constant variance, which is known in the scatterplot of residuls versus height. For heights smaller than 60 inches, the variance is constant, but as the heights increase from 60 to 140, the variance increase as well. I am not at all comfortable with assuming a constant variance in the residuals.

d. The observations are independent of each other.
> I do think that it is reasonable to assume that the observation are independent of each other because it is a random sample from the NHANES III survey.

e. State overall judgement on reasonableness
> Overall, I am not comfortable with the reasonableness of these assumption for this model using the whole data set. I think the data should be divided in some way, by age or heights of the children for example, and seperate models built for the two subsets of data. Because this is an academic exercise, I will continue anyway to demonstrate my understanding of linear regression analysis.

6\. Interpret the slope coefficient in the context of the problem.
> This slop coefficient of this model is `1.90904` which means that a child who is one inch taller than another is predicted to weight `1.90904` pounds more than the other child.

7\. Interpret the intercept coefficient in the context of the problem
>  The intercept coefficient of this model is ` -31.34191` and, in this context, has no useful interpretation. All children are born with a positive height, typically between 16 and 24 inches. It is impossible to have a child with a height of zero. Therefore the intercept has no usefule interpretation.

// TODO
8\. What is the estimate of the standard deviation of the residuals? Interpret this value. In the context of this problem, it is considered large?
> The estimate of the standard deviation of the residuals is the residual standard error and is `14.09` pounds; therefore, when the model is used to predict a child's weight, the typical error is `14` pounds. This is a large deviation because the average weight of the children in the sample is about `40` pounds, estimating from the scatterplot.

9\. Interpret the coefficient of determination.
> Approximately `68%` of the variation in children's weight is accounted for by the linear model using the children's height.

10\. Discuss the overall quality of the model, considering both the standard deviation of residuals and the coefficient of determination.
> Although the coefficient of determination is a good quality level, the standard deviation of the residuals is too high to make this model very useful for predicting a child's weight for most purposes.

11\. Is the slope of the LR model statistically significant?
> The slope of the model is statistically significant because the `p-value` testing whether zero is a reasonable value is practically zero (`2E-16`).

12\. Is the intercept of the LR model statistically significant?
> The intercept of the model is statistically significant because the `p-value` testing whether zero is a reasonable value is practically zero (`2E-16`).

13\. Construct a 90% Confidence Interval for the slope.
> `90%` CI formula: $(\hat \beta_1 \pm t^* (\text{St error of } \hat \beta_1 ))$, where $t^*$ satisfies $P{t_{n-2} \le t^*} = 1 - \frac{\alpha}{2}$
$$
\begin{aligned}
P\{t_{n-2} \le t^*\} &= 1 - \frac{\alpha}{2}\\
\Rightarrow t^* &= \text{invT}(\text{Area to left}, \text{Degree of freedom})\\
&= \text{invT}(0.95, 248)\\
&= 1.65102\\
\text{CI} &= (\hat \beta_1 - t^* (\text{St error of } \hat \beta_1), \hat \beta_1 + t^* (\text{St error of } \hat \beta_1))\\
&= (1.90904 - 1.65102 * 0.08343, 1.90904 + 1.65102 * 0.08343)\\
&= (1.771295322, 2.04678678)
\end{aligned}
$$

14\. Construct a 90% Confidence Interval for the intercept.
> `90%` CI formula: $(\hat \beta_0 \pm t^* (\text{St error of } \hat \beta_0 ))$, where $t^*$ satisfies $P{t_{n-2} \le t^*} = 1 - \frac{\alpha}{2}$
$$
\begin{aligned}
P\{t_{n-2} \le t^*\} &= 1 - \frac{\alpha}{2}\\
\Rightarrow t^* &= \text{invT}(\text{Area to left}, \text{Degree of freedom})\\
&= \text{invT}(0.95, 248)\\
&= 1.65102\\
\text{CI} &= (\hat \beta_0 - t^* (\text{St error of } \hat \beta_0), \hat \beta_0 + t^* (\text{St error of } \hat \beta_0))\\
&= (-31.34191 - 1.65102 * 3.17493, -31.34191 + 1.65102 * 3.17493)\\
&= (−36.58378, −26.100034)
\end{aligned}
$$

15\. Identify potential influential points.
> There are potential influential points at `(12, 18)` and `(33, 85)`. In addition, there are at least 5 points with weights above 120 that are potential influential points.

16\. Use the model to predict the response value for a given explanatory
variable value.
> Suppose that we have a child who is 40 inches tall. We predict that child's weight as follows:
$\widehat\text{weight} = -31.34191 + 1.90904 * (40) = 45.01969$ pounds

17\. Identify the range of explanatory variable values that the model can be used to predict the response value.
> If the assumptions held, we could use the model to comfortable predict the weights of children who were between 20 and 61 inches tall. Because we have only one observation lower than 20 and only one higher than 61, I am not willing to predict outside of this range.

18\. If you had more time and money to do a Phase II analysis, what would you do next?
> I would split the data set into children who were between 20 and 40 inches tall and those between 40 and 62 inches tall. Then I would develop separate linear regression models for these two subsets. Since age was also a significant predictor, I would also use both age and weight in a multiple-linear regression model.
