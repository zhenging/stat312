## Ti 83 Calculator Tips

#### Normal Distribution
```
normalcdf(lower bound, upper bound, mean, standard deviation)
```

#### Binomial Distribution
There are 9 people selected (n = number of trials = 9). The probability of success is 0.62 and we are finding $P(X \le 6)$. How you enter this looks different in each calculator.
> Key Sequence:  `2nd`, `VARS(DISTR)`, down arrow to select `A:binomcdf`
```
binomcdf(9, 0.62, 6)
```

#### Student T Distribution
```
tcdf(lower bound, upper bound, degree of freedom)
```

#### Inverse T
[Programming invT into a Ti 83 or Ti 83+ Calculator](https://www.youtube.com/watch?v=5Ft5eZVJtPk)

```
PROGRAMM: INVT
:INPUT "AREA LEFT:", A
:INPUT "DF:", D
:1->S
:If A<0.5
:Then
:-1->S
:End
:abs(2*A - 1)->A
:TInterval 0, sqrt(D+1), (D+1), A
:Disp upper*S
:
```

#### tcdf
```
PROGRAMM: TCDF
INPUT "LOWER", L
INPUT "UPPER", U
INPUT "DF", D
tcdf(L, U, D)
DISP ANS
```

#### T-score of Single Population
```
PROGRAMM: TSCORE1
INPUT "SAMPLE MEAN", X
INPUT "POPULATION MEAN", U
INPUT "SAMPLE SIZE", N
INPUT "SAMPLE SD", S
(X-U)/(S/sqrt(N))
DISP ANS
```
> Replace `sqrt` with squre root key on Ti 83 calculator

#### T-score of Two Populations
```
PROGRAMM: TSCORE2
INPUT "SAMPLE MEAN 1", X1
INPUT "SAMPLE MEAN 2", X2
INPUT "MEAN DIFF",
INPUT "SAMPLE SD 1", S1
INPUT "SAMPLE SD 2", S2

INPUT "SAMPLE SD", S
(X-U)/(S/sqrt(N))
DISP ANS
```
> Replace `sqrt` with squre root key on Ti 83 calculator

#### Chi-squared
E.g.
[21 36 30]
[48 26 19]

1. Put data into a matrix.
  + Press `2nd`, `x-1/MATRIX`, select `EDIT` on screen
  + Select `A`
  + Specify rows and columns for the matrix `2 x 3`
  + Input given numbers
2. Test with Chi-squared Test
  + Press `STAT`, select `TESTS`
  + Press `ALPHA`, then press `C` to select $\Chi^2$-Test
3. Select `Calculate` or `Draw` to see result
4. To check expected value
  + Press `2nd`, `x-1/MATRIX`, select `EDIT` on screen
  + Select `B` to see the result