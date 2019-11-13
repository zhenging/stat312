---
title: 'HW # 6: Movies Data Analysis'
author: "Zhongyuan Zheng"
date: "2019/11/12"
output:
  word_document: default
  html_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
# read in data
movies = dget("movies.dataframe.2")
# load data into local memory to directly access variables
attach(movies)
# load for ggplot option
library(ggplot2)
# load ISCAM functions
load("ISCAM.RData")
# load for doing HTs with summary data
library(BSDA)
```

## Introduction

The goal of this assignment is to analyze data about movies released in 2016 in the United States. The data was originally downloaded from TMDB and stored on Kaggle.com. The variables include:

* budget - measured in millions of U.S. dollars
* revenue - measured in millions of U.S. dollars
* genre - major category that movie is filed under
* runtime - measured in minutes

## 1. Analysis of Budget

Analyze the budget variable, using both numerical and graphical summaries.

### a) Numerical summary

```{r P1_budget_Num, echo=TRUE}
# Edit the code below. You may erase any code you do not use.
my.var = budget
# Numerical Summaries
summary(my.var) # 5 num sum + mean
# additional useful sample statistics include:
sd(my.var, na.rm = TRUE)  # standard deviation
IQR(my.var)  # IQR
range(my.var)  # range giving min and max
# there are no functions for LOB and UOB, so you have to create those yourself
Q1 = quantile(x = my.var, 0.25, na.rm = TRUE)
cat("[Q1]", Q1, "\n")
Q3 = quantile(x = my.var, 0.75, na.rm = TRUE)
cat("[Q3]", Q3, "\n")
LOB = Q1 - (1.5*(Q3-Q1))
cat("[LOB]", LOB, "\n")
UOB = Q3 + (1.5*(Q3-Q1))
cat("[UOB]", UOB, "\n")
if (min(my.var) < LOB) {paste("The height data has lower outliers.")} else {paste("The height data does not have any lower outliers.")}
if (max(my.var) > UOB) {paste("The height data has upper outliers.")} else {paste("The height data does not have any upper outliers.")}
```

***
Write your numerical summary paragraph here. Be sure to include everything you should according to the guidelines you were given.
***

### b) Graphical summary

```{r P1_budget_Graphs, echo=TRUE, fig.height=3, fig.width=7}
# In the line above, fig.height and fig.width control the size of the plots. Change them to get the size plots you want. You may also change their size after you knit to Word.
# Edit the code below to create meaningful graphics. You may erase any code you do not use.

my.var = budget

# Histograms
# Set intentional bin boundaries
my.bins = seq(from = min(my.var) -1, to = max(my.var) + 1, by = 1)

# ggplot approach
ggplot(data = movies, aes(x=my.var)) +
  geom_histogram(breaks = my.bins,
                 color = "magenta",
                 fill = "magenta") +
  labs(x = "Budget (millions of dollars)",
       y = "Frequency",
       title = "Budget of 2016 Movies (n=72)")

# ggplot approach
ggplot(data = movies, aes(y=my.var)) +
  geom_boxplot(color = "blue",
             fill = "lightblue") +
 labs(x = "Budget (millions of dollars)",
      y = "Frequency",
      title = "Budget of 2016 Movies (n=72)") +
  coord_flip()
```

***

Write your graphical discussion paragraph here. This paragraph should include all of the important information that is revealved in the graphic. Remember that document readers can not "read" a graph for a person who is blind. Therefore, we always need to include the information in paragraph form as well.
***

## 2. HT on Population Mean Budget
In 2015, the mean budget of movies released in the U.S. was 43 million dollars. Does the data provide evidence that the mean movie budget in 2016 was higher than 43 million dollars?

***
Replace this text with explanations necessary to set up your audience to understand your HT. It is not sufficient to simply show the code and state the p-value with conclusion. Instead, make sure that you define the population parameters and such. You may either use Latex code to insert equations or you can write "T_0 equation here" and the edit the knitted Word document to insert the equation.
***

***
**Research Question**: Is the mean movie budget in 2016 higher than 43 million dollars?
**Population of Interest**: Budgets of movises released in 2016 in US
**Quantity of Interest**: Mean movie budget
**Perspective**: We want to shout it to the world the mean budget of movies released in 2016 in US is higher than 43 million dollars.
Let $\mu$ = population mean of movie budget, $\mu = 43$ million dollars.
**Data Collection**: The data is already collected from TMDB. Because the total movies produced in 2016 is more than 72 (sample size), we assume that a simple random sample was used.
Let $n$ = the sample size, $n=12$.
Let $\bar{X}$ = the mean movie budget of the sample. $\bar{X} = 63.80$ million dollars.
Record $X_j$ = budget of `jth` movie, whereas $j=1, 2, \cdots , 72$
**State $H_0 \& H_A$**:
$H_0: \mu \le 43$
$H_A: \mu > 43$
**Note**: This is one sided HT (right sided), which means that only larger sample means provide support for rejecting $H_0$ in favor of $H_A$.
**Choose $\alpha$**: Use $\alpha = 0.05$ which is the standard value.
**Define Test Statistics & Distribution**: We will make the assumptions that
1. A simple random sample was used.
2. Data is from a normally distributed population. (Reasonable assumption since these types of measurements are frequently normally distributed).
3. $\sigma^2 \approx s^2$. Using `t` distrubtion helps compensate for making this assumption.
***

```{r HT_mean_budget, echo=TRUE, fig.height=3, fig.width=7}
# Choose which functions you want to use and erase the rest.
# Edit the code so that it computes the numbers you need.

# Using ISCAM function
#iscambinomtest(observed = 10, n = 500, hypothesized = 0.03, alternative = #"less", conf.level = 0.95)

# Using Base R
#binom.test(x = 10, n = 500, p = 0.03, alternative = "less", conf.level = 0.05)

# Using ISCAM function
iscamonesamplet(xbar = mean(budget),sd = sd(budget),
                n = length(budget), hypothesized = 43,
                alternative = "greater", conf.level = 0.95 )

# Using Base R
#t.test(x = weight.data, alternative = "two.sided", mu = 300,
#       conf.level = 0.95)

# Using tsum.test()
#tsum.test(mean.x = 60139.7, s.x = 3645.94, n.x = 16,
#          alternative = "greater", mu = 60000,
#          conf.level = 0.95)


# Using ISCAM function
#iscamtwosamplet(x1 = 12.5, sd1 = 7.63, n1 = 10,
#                x2 = 27.5, sd2 = 15.3, n2 = 10,
#                hypothesized = 0, alternative = "two.sided",
#                conf.level = 0.95 )

# Using tsum.test()
#tsum.test(mean.x = 12.5, s.x = 7.63, n.x = 10, mean.y = 27.5, s.y = 15.3,
#          n.y = 10, alternative = "two.sided", mu = 0, var.equal = FALSE,
#          conf.level = 0.95)

```

***
**Draw Conclusion:**
$\text{p-value} = 0.003803294 < 0.05 = \alpha$
Reject $H_0$ in favor of $H_A$.
**State Conclusion in Context:**
This is data set provide strong evident that the mean budget of movies released in 2016 in US is higher than $43 millions.
**Note**: If the true population mean of movie buget is truly $43 millions, and we sampled 72 movies released in 2016 in US to test repeatedly, only about 3.8% of those samples would have a sample mean that is less or eqaul to $43 millions.
***

## 3. Comparing the budgets of two movie genres
This data set includes movies that are classified as one of the following: Action, Comedy, Drama, Fantasy, Horror, and Romance.

### a) Choose two of these genres to examine in this problem. Which one do you think has a larger budget? Support your position.

***

Replace this text with your choice of genres and a short discussion of which you think has a larger budget, giving reasons to support your position. These reasons can be solely based on your experience in watching movies.

***

### b) Now, analyze your data to see if it supports your position.

```{r boxplot_budget_by_genre, fig.height=5, fig.width=7}
# The code below constructs boxplots for each genre. Improve the graphical display by choosing different titles, etc.

boxplot(budget ~ genre, horizontal = TRUE, las=2,
        main = "My good title",
        xlab = "my good x label",
        ylab = " ")
# Add the mean values as red triangles on the plot to make the plots more informative.
points(mean(budget[genre=="Romance"]),6, pch = 17, col ="red")
points(mean(budget[genre=="Horror"]),5, pch = 17, col ="red")
points(mean(budget[genre=="Fantasy"]),4, pch = 17, col ="red")
points(mean(budget[genre=="Drama"]),3, pch = 17, col ="red")
points(mean(budget[genre=="Comedy"]),2, pch = 17, col ="red")
points(mean(budget[genre=="Action"]),1, pch = 17, col ="red")

# Knowing the sample size is always good. Create table of counts for each genre.
my.genre.table = table(genre)
my.genre.table    # get table to print out
```

***

Replace this text with a short discussion of what the comparative boxplot reveals. Be sure to include whether it supports your position above.

****

### c) HT comparing the mean budget of two genres
Now, construct a HT to quantitatively test the position you supported in part a). That is, use the two genres that you chose and test if the one you thought was higher does have a statistically significant higher mean budget.

***

Replace this text with discussion to set up the HT

***

```{r  HT_mean_budget_2_genres, echo=TRUE, fig.height=3, fig.width=7}
# Choose which functions you want to use and erase the rest.
# Edit the code so that it computes the numbers you need.

# Using ISCAM function
#iscambinomtest(observed = 10, n = 500, hypothesized = 0.03, alternative = #"less", conf.level = 0.95)

# Using Base R
#binom.test(x = 10, n = 500, p = 0.03, alternative = "less", conf.level = 0.05)

# Using ISCAM function
#iscamonesamplet(xbar = mean(weight.data),sd = sd(weight.data),
#                n = length(weight.data), hypothesized = 300,
#                alternative = "two.sided", conf.level = 0.95 )

# Using Base R
#t.test(x = weight.data, alternative = "two.sided", mu = 300,
#       conf.level = 0.95)

# Using tsum.test()
#tsum.test(mean.x = 60139.7, s.x = 3645.94, n.x = 16,
#          alternative = "greater", mu = 60000,
#          conf.level = 0.95)


# Using ISCAM function
#iscamtwosamplet(x1 = 12.5, sd1 = 7.63, n1 = 10,
#                x2 = 27.5, sd2 = 15.3, n2 = 10,
#                hypothesized = 0, alternative = "two.sided",
#                conf.level = 0.95 )

# Using tsum.test()
#tsum.test(mean.x = 12.5, s.x = 7.63, n.x = 10, mean.y = 27.5, s.y = 15.3,
#          n.y = 10, alternative = "two.sided", mu = 0, var.equal = FALSE,
#          conf.level = 0.95)

```

***

Replace this code with discussion drawing a conclusion and stating it in context. Are you surprised by your conclusion? Discuss why you are or are not surprised.

***

### d) Analyzing assumptions

Every hypothesis test has assumptions that underlie the mathematics. As an analyst, you must make a judgement call as to whether it is reasonable to make the assumptions in the context of your problem. In this part, you will analyze each assumption and make a judgement call as to whether it is reasonable for this context of comparing budgets of movie genres.

1) Independent samples

Given what you know about the context and the data, how reasonable is it to assume that the two samples are independent?

***

Replace this text with your answer

***

2) Random samples from the populations

Given what you know about the context and the data, how reasonable is it to assume that the two samples are random samples from the respective populations?

***

Replace this text with your answer

***

3) Each data set is from a Normal distribution

This assumption can be analyzed with a QQ plot.

```{r  QQ_plot_1, echo=TRUE, fig.height=3, fig.width=7}
# Start with your first genre. Change the code below to match your choice.
my.genre = "Horror"
# The model family is Normal.
# What estimate of the population mean do you want to use? Change the value below.
my.model.mean = 0
# What estimate of the population standard deviation do you want to use? Change the value below.
my.model.stdev = 1
# What is the sample size ?
n = length(budget[genre==my.genre])
# Put the correct data into x
x = budget[genre==my.genre]
# set limits for QQ plot axis
limits = c(my.model.mean-3*my.model.stdev, my.model.mean+3*my.model.stdev)

## construct the QQ plot
probs = (1:n)/(n+1)
norm.quants = qnorm(probs,my.model.mean,my.model.stdev)
par(pty="s")
plot(sort(x),sort(norm.quants),ylab="Theoretical Quantiles",
     xlab="Empirical Quantiles", main="Q-Q Plot of what???",
     xlim=limits, ylim=limits, pch=16)
abline(0,1)
par(pty="m")

```

***

Replace this text with a discussion of your first QQ plot

***


```{r  QQ_plot_2, echo=TRUE, fig.height=3, fig.width=7}
# Start with your first genre. Change the code below to match your choice.
my.genre = "Horror"
# The model family is Normal.
# What estimate of the population mean do you want to use? Change the value below.
my.model.mean = 0
# What estimate of the population standard deviation do you want to use? Change the value below.
my.model.stdev = 1
# What is the sample size ?
n = length(budget[genre==my.genre])
# Put the correct data into x
x = budget[genre==my.genre]
# set limits for QQ plot axis
limits = c(my.model.mean-3*my.model.stdev, my.model.mean+3*my.model.stdev)

## construct the QQ plot
probs = (1:n)/(n+1)
norm.quants = qnorm(probs,my.model.mean,my.model.stdev)
par(pty="s")
plot(sort(x),sort(norm.quants),ylab="Theoretical Quantiles",
     xlab="Empirical Quantiles", main="Q-Q Plot of what???",
     xlim=limits, ylim=limits, pch=16)
abline(0,1)
par(pty="m")

```

***

Replace this text with a discussion of your 2nd QQ plot

***

4) The population variances can be estimated by the sample variances.


***

Replace this text with a discussion of whether this is a reasonable assumption

***

To make a final decision as to whether the HT is a valid analysis approach for a given problem and context, we must combine our levels of comfort for the different assumptions into an overall judgement call.


***

Replace this text with a discussion of your overall judgement call. Would you be comfortable using this HT to guide your decision about budgeting for different film genres? Or perhaps you feel the opposite, that this is purely an exercise to demonstrate to your instructor that you know how to do a HT.

***

***

Congratulations! This is the end of the assignment.

***

