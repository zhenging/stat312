### Student t's Distribution (aka the `t` distribution)
+ 1 parameter (v): degree of freedom
+ Shape like Normal, but fatter tail
+ Centered at 0
+ $ \text{VAR} = \begin{cases} \displaystyle\frac{v}{v-2} &\text{ if } v > 2\\  \infty &\text{ if } 1 < v \le 2 \\ \text{undefined} &\text{otherwise}\end{cases}$
+ As $v \to \infty$, $t_v \to \text{Normal}(0, 1)$