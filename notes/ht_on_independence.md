## HT on Independence

+ We have two variable and we want to test whether they are independent or not.
+ $H_0$: Variable A **is** independent of variable B.
+ $H_A$: Variable A **is NOT **independent of variable B.
+ Independence is commutative, os it does not matter which one is listed first.

#### HT on Independence for 2 Categorical Vars
1. Construct a contingency table of observed values
2. Calculate $O{ij}$ and $E{ij}$ for all cells
  - $O{ij}$ = observed count in cell `(i, j)`
  - $E{ij}$ = expected count in cell `(i, j)`
  - Assuming $H_0$ is true, the variables are inpdependent
  - $E{ij} = \hat p_i * \hat p_j * n = \frac{\text{(count in row i) * \text{(count in column j)}}}{n}$
  - Large difference between $O{ij}$ and $E{ij}$ given evidence to reject $H_0$.

#### $\chi_k^2$ Chi-squared Random Variable

![Chi-squared Distribution](/assets/chi_squared_distribution.png)
1. Bounded on left by 0. Unbounded on right.
2. As $k$ increases, it becomes more symmetric.

#### HT on Independence: Test statics
$$
\begin{aligned}
\Chi_0^2 &\text{\textasciitilde} \Chi_v^2\\
v &= (\text{No. of rows} - 1)* (\text{No. of columns} - 1)\\
\Chi_0^2  &= \Sigma_i \Sigma_j \frac{(O{ij-E_{ij}})^2}{E_{ij}}
\end{aligned}
$$

#### HT on Independence R Code
See example G for R Code