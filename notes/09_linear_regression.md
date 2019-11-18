## 09 Linear Regression

> Explanatory Variables and Response Variables

### Association
+ In data analysis, we say that two variables are **associated** when there is a relationship between them.
+ Association in the statistical perspective is parallel to two random variables being NOT independent in the probability in the probability perspective.
+ Association includes: **linear**, **exponential**, **log**, and **polynomial**

### Correlation
+ **Correlation** is a **quantitative** measure of the linear association between two **quantitative** variables. It is only meaningful for linearly associated variables.
+ **Sample correlation coefficient** - or sample correlation ( lower case $r$)
+ **Population correlation** - denotes $\rho$
+ Two independent random variables have a correlation value of $0$. The reverse is **not true.**
+ $r > 0.7$ - strong correlation.
+ $0.3 < r < 0.7$ - moderate correlation.
+ $r < 0.3$ - weak correlation.

> Correlation **does not** imply Association!

#### Calculate $r$
$$
\begin{aligned}
S_{xx} = \sum_{i=1}^n(x_i - \bar{x})^2; \space S_{yy} &= \sum_{i=1}^n(y_i - \bar{y})^2; \space S_{xy} = \sum_{i=1}^n(x_i - \bar{x}) * (y_i - \bar{y})\\
r &= \frac{S_{xy}}{\sqrt{S_{xx}*S_{yy}}}\\
-1 &\le r \le 1
\end{aligned}
$$

### Analyze a scatterplot
1. Randomly scattered -> No Association
2. Linear or Non-linear
3. Direction of association, positive or negative
4. Strength of the association: weak, moderate, strong
5. Combine observations, e.g. "The speed and stopping distance of cars have a strong positive, linear association"

### Residual
A residual is the difference between the predicted value and the observed value. If we let $y_i$ represent the `ith` observed value and $\hat y_i$ represent the predicted or "fitted" value, then
$$
\begin{aligned}
\text{residual}_i = y_i - \hat y_i
\end{aligned}
$$

+ Positve residual - **Underestimate**
+ Negative residual - **Overestimate**