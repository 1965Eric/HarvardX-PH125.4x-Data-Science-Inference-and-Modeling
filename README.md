# Data_Science_Inference_and_Modeling
# HarvardX: PH125.4x | Data Science: Inference and Modeling

## Abstract

This is the fourth in a series of courses in a Professional Certificate in Data Science program, a series of courses that prepare you to do data analysis in R, from simple computations to machine learning. Statistical inference and modeling are indispensable for analyzing data affected by chance, and thus essential for data scientists. In this course, you will learn these key concepts through a motivating case study on election forecasting.

This course will show you how inference and modeling can be applied to develop the statistical approaches that make polls an effective tool and we’ll show you how to do this using R. You will learn concepts necessary to define estimates and margins of errors and learn how you can use these to make predictions relatively well and also provide an estimate of the precision of your forecast.

Once you learn this you will be able to understand two concepts that are ubiquitous in data science: confidence intervals and p-values.

Finally, to understand statements about the probability of a candidate winning, you will learn about Bayesian modeling. At the end of the course, we will put it all together to recreate a simplified version of an election forecast model and apply it to the 2016 US presidential election.

The textbook for the Data Science course series is [freely available online](https://rafalab.github.io/dsbook/).

## Learning Objectives
- The concepts necessary to define estimates and margins of errors of populations, parameters, estimates, and standard errors in order to make predictions about data
- How to use models to aggregate data from different sources
- The very basics of Bayesian statistics and predictive modeling

## Course Overview

## Section 1: Parameters and Estimates
You will learn how to estimate population parameters.

## Section 2: The Central Limit Theorem in Practice
You will apply the central limit theorem to assess how close a sample estimate is to the population parameter of interest.

## Section 3: Confidence Intervals and p-Values
You will learn how to calculate confidence intervals and learn about the relationship between confidence intervals and p-values.

## Section 4: Statistical Models
You will learn about statistical models in the context of election forecasting.

## Section 5: Bayesian Statistics
You will learn about Bayesian statistics through looking at examples from rare disease diagnosis and baseball.

## Section 6: Election Forecasting
You will learn about election forecasting, building on what you’ve learned in the previous sections about statistical modeling and Bayesian statistics.

## Section 7: Association Tests
You will learn how to use association and chi-squared tests to perform inference for binary, categorical, and ordinal data through an example looking at research funding rates.

## Section 1 Overview

Section 1 introduces you to parameters and estimates.

After completing Section 1, you will be able to:
- Understand how to use a sampling model to perform a poll.
- Explain the terms population, parameter, and sample as they relate to statistical inference.
- Use a sample to estimate the population proportion from the sample average.
- Calculate the expected value and standard error of the sample average.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/inference.html)

## Assessment 1.1: Parameters and Estimates

1. Polling - expected value of S

Suppose you poll a population in which a proportion **p** of voters are Democrats and **1−p** are Republicans. Your sample size is **N=25**. Consider the random variable **S**, which is the total number of Democrats in your sample.

What is the expected value of this random variable **S**?

Possible Answers
- [ ] A.  E(S)=25(1−p)
- [X] B.  E(S)=25p
- [ ] C.  E(S)=√(25p(1−p))
- [ ] D.  E(S)=p

2. Polling - standard error of S

Again, consider the random variable S, which is the total number of Democrats in your sample of 25 voters. The variable p describes the proportion of Democrats in the sample, whereas 1−p describes the proportion of Republicans.

What is the standard error of S?

Possible Answers
- [ ] A.  SE(S)=25p(1−p)
- [ ] B.  SE(S)=√25p
- [ ] C.  SE(S)=25(1−p)
- [X] D.  SE(S)=√(25p(1−p))

3. Polling - expected value of X-bar

Consider the random variable **S/N**, which is equivalent to the sample average that we have been denoting as **X̄**. The variable **N** represents the sample size and **p** is the proportion of Democrats in the population.

What is the expected value of **X̄**?

Possible Answers
- [X] A.  E(X̄)=p
- [ ] B.  E(X̄)=Np
- [ ] C.  E(X̄)=N(1−p)
- [ ] D.  E(X̄)=1−p

4. Polling - standard error of X-bar

What is the standard error of the sample average, **X̄**?

The variable **N** represents the sample size and **p** is the proportion of Democrats in the population.

Possible Answers
- [ ] A.  SE(X̄)=√(Np(1−p))
- [X] B.  SE(X̄)=√(p(1−p)/N)
- [ ] C.  SE(X̄)=√(p(1−p))
- [ ] D.  SE(X̄)=√N

5. se versus p

Write a line of code that calculates the standard error se of a sample average when you poll 25 people in the population. Generate a sequence of 100 proportions of Democrats p that vary from 0 (no Democrats) to 1 (all Democrats).

Plot se versus p for the 100 different proportions.

Instructions
- Use the seq function to generate a vector of 100 values of p that range from 0 to 1.
- Use the sqrt function to generate a vector of standard errors for all values of p.
- Use the plot function to generate a plot with p on the x-axis and se on the y-axis.
```
# `N` represents the number of people polled
N <- 25

# Create a variable `p` that contains 100 proportions ranging from 0 to 1 using the `seq` function
p <- seq(0,1, length = 100)

# Create a variable `se` that contains the standard error of each sample average
se <- sqrt(p * (1 - p)/N)

# Plot `p` on the x-axis and `se` on the y-axis
plot(p,se)
```
![index](https://user-images.githubusercontent.com/17474099/76228027-7931be00-6220-11ea-8096-8f017f7ed223.png)

6. Multiple plots of se versus p

Using the same code as in the previous exercise, create a for-loop that generates three plots of p versus se when the sample sizes equal N=25, N=100, and N=1000.

Instructions
- Your for-loop should contain two lines of code to be repeated for three different values of N.
- The first line within the for-loop should use the sqrt function to generate a vector of standard errors se for all values of p.
- The second line within the for-loop should use the plot function to generate a plot with p on the x-axis and se on the y-axis.
- Use the ylim argument to keep the y-axis limits constant across all three plots. The lower limit should be equal to 0 and the upper limit should equal the highest calculated standard error across all values of p and N.
```
# The vector `p` contains 100 proportions of Democrats ranging from 0 to 1 using the `seq` function
p <- seq(0, 1, length = 100)

# The vector `sample_sizes` contains the three sample sizes
sample_sizes <- c(25, 100, 1000)

# Write a for-loop that calculates the standard error `se` for every value of `p` for each of the three samples sizes `N` in the vector `sample_sizes`. Plot the three graphs, using the `ylim` argument to standardize the y-axis across all three plots.
for(N in sample_sizes){
  se <- sqrt(p*(1-p)/N)
  plot(p, se, ylim = c(0,0.5/sqrt(25)))
}
```

![index](https://user-images.githubusercontent.com/17474099/76228027-7931be00-6220-11ea-8096-8f017f7ed223.png)

![index](https://user-images.githubusercontent.com/17474099/76228450-0a089980-6221-11ea-80e4-13ac6233f1a1.png)

![index](https://user-images.githubusercontent.com/17474099/76228545-2a385880-6221-11ea-8bb5-2cba961954c3.png)

7. Expected value of d

Our estimate for the difference in proportions of Democrats and Republicans is **d=X̄−(1−X̄)**.

Which derivation correctly uses the rules we learned about sums of random variables and scaled random variables to derive the expected value of d?

Possible Answers
- [ ] A.  E[X̄−(1−X̄)]=E[2X̄−1]=2E[X̄]−1=N(2p−1)=Np−N(1−p)
- [ ] B.  E[X̄−(1−X̄)]=E[X̄−1]=E[X̄]−1=p−1
- [ ] C.  E[X̄−(1−X̄)]=E[2X̄−1]=2E[X̄]−1=2√(p(1−p))−1=p−(1−p)
- [X] D.  E[X̄−(1−X̄)]=E[2X̄−1]=2E[X̄]−1=2p−1=p−(1−p)

8. Standard error of d

Our estimate for the difference in proportions of Democrats and Republicans is **d=X̄−(1−X̄)**.

Which derivation correctly uses the rules we learned about sums of random variables and scaled random variables to derive the standard error of **d**?

Possible Answers
- [ ] A.  SE[X̄−(1−X̄)]=SE[2X̄−1]=2SE[X̄]=2√(p/N)
- [ ] B.  SE[X̄−(1−X̄)]=SE[2X̄−1]=2SE[X̄−1]=2√(p(1−p)/N−1)
- [X] C.  SE[X̄−(1−X̄)]=SE[2X̄−1]=2SE[X̄]=2√(p(1−p)/N)
- [ ] D.  SE[X̄−(1−X̄)]=SE[2X̄−1]=2SE[X̄]=√(p(1−p)/N)

9. Standard error of the spread

Say the actual proportion of Democratic voters is p=0.45. In this case, the Republican party is winning by a relatively large margin of d=−0.1, or a 10% margin of victory. What is the standard error of the spread 2X̄−1 in this case?

Use the sqrt function to calculate the standard error of the spread 2X̄−1.
```
# `N` represents the number of people polled
N <- 25

# `p` represents the proportion of Democratic voters
p <- 0.45

# Calculate the standard error of the spread. Print this value to the console.
2*sqrt(p*(1-p)/N)
```
```
## [1] 0.1989975
```
10. Sample size

So far we have said that the difference between the proportion of Democratic voters and Republican voters is about 10% and that the standard error of this spread is about 0.2 when N=25. Select the statement that explains why this sample size is sufficient or not.

- [ ] A. This sample size is sufficient because the expected value of our estimate 2X̄−1 is d so our prediction will be right on.
- [X] B. This sample size is too small because the standard error is larger than the spread.
- [ ] C. This sample size is sufficient because the standard error of about 0.2 is much smaller than the spread of 10%.
- [ ] D. Without knowing p, we have no way of knowing that increasing our sample size would actually improve our standard error.

## Section 2 Overview

In Section 2, you will look at the Central Limit Theorem in practice.

After completing Section 2, you will be able to:
- Use the Central Limit Theorem to calculate the probability that a sample estimate X̄ is close to the population proportion p.
- Run a Monte Carlo simulation to corroborate theoretical results built using probability theory.
- Estimate the spread based on estimates of X̄ and ŜE(X̄).
- Understand why bias can mean that larger sample sizes aren’t necessarily better.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/random-variables.html#central-limit-theorem)

## Assessment 2.1: Introduction to Inference

1. Sample average

Write a function called take_sample that takes the proportion of Democrats p and the sample size N as arguments and returns the sample average of Democrats (1) and Republicans (0).

Calculate the sample average if the proportion of Democrats equals 0.45 and the sample size is 100.

Instructions
- Define a function called take_sample that takes p and N as arguments.
- Use the sample function as the first statement in your function to sample N elements from a vector of options where Democrats are assigned the value ‘1’ and Republicans are assigned the value ‘0’.
- Use the mean function as the second statement in your function to find the average value of the random sample.
```
# Write a function called `take_sample` that takes `p` and `N` as arguements and returns the average value of a randomly sampled population.
take_sample <- function(p, N){
    X <- sample(c(0,1), size = N, replace = TRUE, prob = c(1 - p, p))
    mean(X)
}

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# Call the `take_sample` function to determine the sample average of `N` randomly selected people from a population containing a proportion of Democrats equal to `p`. Print this value to the console.
take_sample(p,N)
```
```
## [1] 0.46
```
2. Distribution of errors - 1

Assume the proportion of Democrats in the population p equals 0.45 and that your sample size N is 100 polled voters. The take_sample function you defined previously generates our estimate, X̄.

Replicate the random sampling 10,000 times and calculate  p−X̄ for each random sample. Save these differences as a vector called errors. Find the average of errors and plot a histogram of the distribution.

Instructions
- The function take_sample that you defined in the previous exercise has already been run for you.
- Use the replicate function to replicate subtracting the result of take_sample from the value of p 10,000 times.
- Use the mean function to calculate the average of the differences between the sample average and actual value of p. 
```
# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# The variable `B` specifies the number of times we want the sample to be replicated
B <- 10000

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Create an objected called `errors` that replicates subtracting the result of the `take_sample` function from `p` for `B` replications
errors <- replicate(B, p - take_sample(p, N))

# Calculate the mean of the errors. Print this value to the console.
mean(errors)
```
```
## [1] -4.9e-05
```
3. Distribution of errors - 2

In the last exercise, you made a vector of differences between the actual value for p and an estimate, X̄. We called these differences between the actual and estimated values errors.

The errors object has already been loaded for you. Use the hist function to plot a histogram of the values contained in the vector errors. Which statement best describes the distribution of the errors?

Possible Answers
- [ ] A. The errors are all about 0.05.
- [ ] B. The error are all about -0.05.
- [X] C. The errors are symmetrically distributed around 0.
- [ ] D. The errors range from -1 to 1.

4. Average size of error

The error p−X̄ is a random variable. In practice, the error is not observed because we do not know the actual proportion of Democratic voters, p. However, we can describe the size of the error by constructing a simulation.

What is the average size of the error if we define the size by taking the absolute value ∣p−X̄∣?

Instructions
- Use the sample code to generate errors, a vector of ∣p−X̄∣.
- Calculate the absolute value of errors using the abs function.
- Calculate the average of these values using the mean function.
```
# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# The variable `B` specifies the number of times we want the sample to be replicated
B <- 10000

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# We generated `errors` by subtracting the estimate from the actual proportion of Democratic voters
errors <- replicate(B, p - take_sample(p, N))

# Calculate the mean of the absolute value of each simulated error. Print this value to the console.
mean(abs(errors))
```
```
## [1] 0.039267
```
5. Standard deviation of the spread

The standard error is related to the typical size of the error we make when predicting. We say size because, as we just saw, the errors are centered around 0. In that sense, the typical error is 0. For mathematical reasons related to the central limit theorem, we actually use the standard deviation of errors rather than the average of the absolute values.

As we have discussed, the standard error is the square root of the average squared distance (X̄−p)2. The standard deviation is defined as the square root of the distance squared.

Calculate the standard deviation of the spread.

Instructions
- Use the sample code to generate errors, a vector of ∣p−X̄∣.
- Use ^2 to square the distances.
- Calculate the average squared distance using the mean function.
- Calculate the square root of these values using the sqrt function.
```
# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# The variable `B` specifies the number of times we want the sample to be replicated
B <- 10000

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# We generated `errors` by subtracting the estimate from the actual proportion of Democratic voters
errors <- replicate(B, p - take_sample(p, N))

# Calculate the standard deviation of `errors`
sqrt(mean(errors^2))
```
```
## [1] 0.04949939
```
6. Estimating the standard error

The theory we just learned tells us what this standard deviation is going to be because it is the standard error of X̄.

Estimate the standard error given an expected value of 0.45 and a sample size of 100.

Instructions
- Calculate the standard error using the sqrt function
```
# Define `p` as the expected value equal to 0.45
p <- 0.45

# Define `N` as the sample size
N <- 100

# Calculate the standard error
sqrt(p*(1-p)/N)
```
```
## [1] 0.04974937
```
7. Standard error of the estimate

In practice, we don’t know p, so we construct an estimate of the theoretical prediction based by plugging in X̄ for p.

Calculate the standard error of the estimate:

**ŜE(X̄)**

Instructions
- Simulate a poll X using the sample function.
- When using the sample function, create a vector using c() that contains all possible polling options where ‘1’ indicates a Democratic voter and ‘0’ indicates a Republican voter.
- When using the sample function, use replace = TRUE within the sample function to indicate that sampling from the vector should occur with replacement.
- When using the sample function, use prob = within the sample function to indicate the probabilities of selecting either element (0 or 1) within the vector of possibilities.
- Use the mean function to calculate the average of the simulated poll, X_bar.
- Calculate the standard error of the X_bar using the sqrt function and print the result.
```
# Define `p` as a proportion of Democratic voters to simulate
p <- 0.45

# Define `N` as the sample size
N <- 100

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Define `X` as a random sample of `N` voters with a probability of picking a Democrat ('1') equal to `p`
X <- sample(0:1, N, replace=T, p=c(1-p,p))

# Define `X_bar` as the average sampled proportion
X_bar <- mean(X)

# Calculate the standard error of the estimate. Print the result to the console.
sqrt(X_bar*(1-X_bar)/N)
```
```
## [1] 0.04983974
```
8. Plotting the standard error

The standard error estimates obtained from the Monte Carlo simulation, the theoretical prediction, and the estimate of the theoretical prediction are all very close, which tells us that the theory is working. This gives us a practical approach to knowing the typical error we will make if we predict p with X̂. The theoretical result gives us an idea of how large a sample size is required to obtain the precision we need. Earlier we learned that the largest standard errors occur for p=0.5.

Create a plot of the largest standard error for N ranging from 100 to 5,000. Based on this plot, how large does the sample size have to be to have a standard error of about 1%?
```
N <- seq(100, 5000, len = 100)
p <- 0.5
se <- sqrt(p*(1-p)/N)
```
Possible Answers
- [ ] A. 100
- [ ] B. 500
- [X] C. 2,500
- [ ] D. 4,000

9. Distribution of X-hat

For N=100, the central limit theorem tells us that the distribution of X̂ is…

Possible Answers
- [ ] A. practically equal to $ p $.
- [X] B. approximately normal with expected value p and standard error √(p(1−p)/N).
- [ ] C. approximately normal with expected value X̄ and standard error √(X̄(1−X̄)/N).
- [ ] D. not a random variable.

10. Distribution of the errors

We calculated a vector errors that contained, for each simulated sample, the difference between the actual value p and our estimate X̂.

The errors X̄−p are:

Possible Answers
- [ ] A. practically equal to 0.
- [X] B. approximately normal with expected value 0 and standard error √(p(1−p)/N).
- [ ] C. approximately normal with expected value p and standard error √(p(1−p)/N).
- [ ] D. not a random variable.

11. Plotting the errors

Make a qq-plot of the errors you generated previously to see if they follow a normal distribution.

Instructions
- Run the supplied code
- Use the qqnorm function to produce a qq-plot of the errors.
- Use the qqline function to plot a line showing a normal distribution.
```
# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# The variable `B` specifies the number of times we want the sample to be replicated
B <- 10000

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Generate `errors` by subtracting the estimate from the actual proportion of Democratic voters
errors <- replicate(B, p - take_sample(p, N))

# Generate a qq-plot of `errors` with a qq-line showing a normal distribution
qqnorm(errors)
qqline(errors)
```

![index](https://user-images.githubusercontent.com/17474099/76305614-c156ec00-62c5-11ea-9a5e-0a9c83f21ae5.png)

12. Estimating the probability of a specific value of X-bar

If p=0.45 and N=100, use the central limit theorem to estimate the probability that X̄>0.5.

Instructions
- Use pnorm to define the probability that a value will be greater than 0.5.
```
# Define `p` as the proportion of Democrats in the population being polled
p <- 0.45

# Define `N` as the number of people polled
N <- 100

# Calculate the probability that the estimated proportion of Democrats in the population is greater than 0.5. Print this value to the console.
1-pnorm(0.5, mean = p, sd=(sqrt(p*(1-p)/N)))
```
```
## [1] 0.1574393
```
13. Estimating the probability of a specific error size

Assume you are in a practical situation and you don’t know p. Take a sample of size N=100 and obtain a sample average of X̄=0.51.

What is the CLT approximation for the probability that your error is equal or larger than 0.01?

Instructions
- Calculate the standard error of the sample average using the sqrt function.
- Use pnorm twice to define the probabilities that a value will be less than 0.01 or -0.01.
- Calculate the probability that the error will be 0.01 or larger.
```
# Define `N` as the number of people polled
N <-100

# Define `X_hat` as the sample average
X_hat <- 0.51

# Define `se_hat` as the standard error of the sample average
se_hat <- sqrt(X_hat*(1-X_hat)/N)

# Calculate the probability that the error is 0.01 or larger
1 - pnorm(.01, 0, se_hat) + pnorm(-0.01, 0, se_hat)
```
```
## [1] 0.8414493
```
## Section 3 Overview

In Section 3, you will look at confidence intervals and p-values.

After completing Section 3, you will be able to:
- Calculate confidence intervals of difference sizes around an estimate.
- Understand that a confidence interval is a random interval with the given probability of falling on top of the parameter.
- Explain the concept of “power” as it relates to inference.
- Understand the relationship between p-values and confidence intervals and explain why reporting confidence intervals is often preferable.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/inference.html#confidence-intervals)

## Assessment 3.1: Confidence Intervals and p-Values

1. Confidence interval for p

For the following exercises, we will use actual poll data from the 2016 election. The exercises will contain pre-loaded data from the dslabs package.
```
library(dslabs)
library(dplyr)
library(ggplot2)
data(polls_us_election_2016)
```
We will use all the national polls that ended within a few weeks before the election.

Assume there are only two candidates and construct a 95% confidence interval for the election night proportion p.

Instructions
- Use filter to subset the data set for the poll data you want. Include polls that ended on or after October 31, 2016 (enddate). Only include polls that took place in the United States. Call this filtered object polls.
- Use nrow to make sure you created a filtered object polls that contains the correct number of rows.
- Extract the sample size N from the first poll in your subset object polls.
- Convert the percentage of Clinton voters (rawpoll_clinton) from the first poll in polls to a proportion, X_hat. Print this value to the console.
- Find the standard error of X_hat given N. Print this result to the console.
- Calculate the 95% confidence interval of this estimate using the qnorm function.
- Save the lower and upper confidence intervals as an object called ci. Save the lower confidence interval first.
```
# Load the data

data(polls_us_election_2016)

# Generate an object `polls` that contains data filtered for polls that ended on or after October 31, 2016 in the United States
polls <- filter(polls_us_election_2016, enddate >= "2016-10-31" & state == "U.S.")

# How many rows does `polls` contain? Print this value to the console.
nrow(polls)
```
```
## [1] 70
```
```
# Assign the sample size of the first poll in `polls` to a variable called `N`. Print this value to the console.
N <- head(polls$samplesize,1)
N
```
```
## [1] 2220
```
```
# For the first poll in `polls`, assign the estimated percentage of Clinton voters to a variable called `X_hat`. Print this value to the console.
X_hat <- (head(polls$rawpoll_clinton,1)/100)
X_hat
```
```
## [1] 0.47
```
```
# Calculate the standard error of `X_hat` and save it to a variable called `se_hat`. Print this value to the console.
se_hat <- sqrt(X_hat*(1-X_hat)/N)
se_hat
```
```
## [1] 0.01059279
```
```
# Use `qnorm` to calculate the 95% confidence interval for the proportion of Clinton voters. Save the lower and then the upper confidence interval to a variable called `ci`.
qnorm(0.975)
```
```
## [1] 1.959964
```
```
ci <- c(X_hat - qnorm(0.975)*se_hat, X_hat + qnorm(0.975)*se_hat)
```
2. Pollster results for p

Create a new object called pollster_results that contains the pollster’s name, the end date of the poll, the proportion of voters who declared a vote for Clinton, the standard error of this estimate, and the lower and upper bounds of the confidence interval for the estimate.

Instructions
- Use the mutate function to define four new columns: X_hat, se_hat, lower, and upper. Temporarily add these columns to the polls object that has already been loaded for you.
- In the X_hat column, convert the raw poll results for Clinton to a proportion.
- In the se_hat column, calculate the standard error of X_hat for each poll using the sqrt function.
- In the lower column, calculate the lower bound of the 95% confidence interval using the qnorm function.
- In the upper column, calculate the upper bound of the 95% confidence interval using the qnorm function.
- Use the select function to select the columns from polls to save to the new object pollster_results.
```
# The `polls` object that filtered all the data by date and nation has already been loaded. Examine it using the `head` function.
head(polls)
```
```
        state   startdate       enddate
        <fctr>  <date>          <date>
1	U.S.	2016-11-03	2016-11-06	
2	U.S.	2016-11-01	2016-11-07	
3	U.S.	2016-11-02	2016-11-06	
4	U.S.	2016-11-04	2016-11-07	
5	U.S.	2016-11-03	2016-11-06	
6	U.S.	2016-11-03	2016-11-06	
6 rows | 1-4 of 16 columns
```
```
# Create a new object called `pollster_results` that contains columns for pollster name, end date, X_hat, lower confidence interval, and upper confidence interval for each poll.
polls <- mutate(polls, X_hat = polls$rawpoll_clinton/100, se_hat = sqrt(X_hat*(1-X_hat)/polls$samplesize), lower = X_hat - qnorm(0.975)*se_hat, upper = X_hat + qnorm(0.975)*se_hat)
pollster_results <- select(polls, pollster, enddate, X_hat, se_hat, lower, upper)
```
3. Comparing to actual results - p

The final tally for the popular vote was Clinton 48.2% and Trump 46.1%. Add a column called hit to pollster_results that states if the confidence interval included the true proportion p=0.482 or not. What proportion of confidence intervals included p?

Instructions
- Use the mutate function to define a new variable called ‘hit’.
- Use logical expressions to determine if each values in lower and upper span the actual proportion.
- Use the mean function to determine the average value in hit and summarize the results using summarize.
- Save the result as an object called avg_hit.
```
# The `pollster_results` object has already been loaded. Examine it using the `head` function.
head(pollster_results)
```
```	
   pollster                                                     enddate         X_hat
   <fctr>                                                       <date>          <dbl>
1  ABC News/Washington Post	                                2016-11-06	0.4700	
2  Google Consumer Surveys	                                2016-11-07	0.3803	
3  Ipsos	                                                2016-11-06	0.4200	
4  YouGov	                                                2016-11-07	0.4500	
5  Gravis Marketing	                                        2016-11-06	0.4700	
6  Fox News/Anderson Robbins Research/Shaw & Company Research	2016-11-06	0.4800	
6 rows | 1-4 of 7 columns
```
```
# Add a logical variable called `hit` that indicates whether the actual value exists within the confidence interval of each poll. Summarize the average `hit` result to determine the proportion of polls with confidence intervals include the actual value. Save the result as an object called `avg_hit`.
avg_hit <- pollster_results %>% mutate(hit=(lower<0.482 & upper>0.482)) %>% summarize(mean(hit))
avg_hit
```
```
                                                                        mean(hit)
                                                                        <dbl>
                                                                        0.3142857
1 row
```
4. Theory of confidence intervals

If these confidence intervals are constructed correctly, and the theory holds up, what proportion of confidence intervals should include p?

Possible Answers
- [ ] A. 0.05
- [ ] B. 0.31
- [ ] C. 0.50
- [X] D. 0.95

5. Confidence interval for d

A much smaller proportion of the polls than expected produce confidence intervals containing p. Notice that most polls that fail to include p are underestimating. The rationale for this is that undecided voters historically divide evenly between the two main candidates on election day.

In this case, it is more informative to estimate the spread or the difference between the proportion of two candidates d, or 0.482−0.461=0.021 for this election.

Assume that there are only two parties and that d=2p−1. Construct a 95% confidence interval for difference in proportions on election night.

Instructions

    Use the mutate function to define a new variable called ‘d_hat’ in polls. The new variable subtract the proportion of Trump voters from the proportion of Clinton voters.
    Extract the sample size N from the first poll in your subset object polls.
    Extract the difference in proportions of voters d_hat from the first poll in your subset object polls.
    Use the formula above to calculate p from d_hat. Assign p to the variable X_hat.
    Find the standard error of the spread given N.
    Calculate the 95% confidence interval of this estimate of the difference in proportions, d_hat, using the qnorm function.
    Save the lower and upper confidence intervals as an object called ci. Save the lower confidence interval first.

# Add a statement to this line of code that will add a new column named `d_hat` to `polls`. The new column should contain the difference in the proportion of voters.
polls <- polls_us_election_2016 %>% filter(enddate >= "2016-10-31" & state == "U.S.")  %>%
  mutate(d_hat = rawpoll_clinton/100 - rawpoll_trump/100)

# Assign the sample size of the first poll in `polls` to a variable called `N`. Print this value to the console.
N <- polls$samplesize[1]

# For the difference `d_hat` of the first poll in `polls` to a variable called `d_hat`. Print this value to the console.
d_hat <- polls$d_hat[1]
d_hat

## [1] 0.04

# Assign proportion of votes for Clinton to the variable `X_hat`.
X_hat <- (d_hat+1)/2

# Calculate the standard error of the spread and save it to a variable called `se_hat`. Print this value to the console.
se_hat <- 2*sqrt(X_hat*(1-X_hat)/N)
se_hat

## [1] 0.02120683

# Use `qnorm` to calculate the 95% confidence interval for the difference in the proportions of voters. Save the lower and then the upper confidence interval to a variable called `ci`.
ci <- c(d_hat - qnorm(0.975)*se_hat, d_hat + qnorm(0.975)*se_hat)

    Pollster results for d
    Create a new object called pollster_results that contains the pollster’s name, the end date of the poll, the difference in the proportion of voters who declared a vote either, the standard error of this estimate, and the lower and upper bounds of the confidence interval for the estimate.

Instructions

    Use the mutate function to define four new columns: ‘X_hat’, ‘se_hat’, ‘lower’, and ‘upper’. Temporarily add these columns to the polls object that has already been loaded for you.
    In the X_hat column, calculate the proportion of voters for Clinton using d_hat.
    In the se_hat column, calculate the standard error of the spread for each poll using the sqrtfunction.
    In the lower column, calculate the lower bound of the 95% confidence interval using the qnorm function.
    In the upper column, calculate the upper bound of the 95% confidence interval using the qnorm function.
    Use the select function to select the columns from polls to save to the new object pollster_results.

# The subset `polls` data with 'd_hat' already calculated has been loaded. Examine it using the `head` function.
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
1	U.S.	2016-11-03	2016-11-06	
2	U.S.	2016-11-01	2016-11-07	
3	U.S.	2016-11-02	2016-11-06	
4	U.S.	2016-11-04	2016-11-07	
5	U.S.	2016-11-03	2016-11-06	
6	U.S.	2016-11-03	2016-11-06	
6 rows | 1-4 of 17 columns

# Create a new object called `pollster_results` that contains columns for pollster name, end date, d_hat, lower confidence interval of d_hat, and upper confidence interval of d_hat for each poll.
pollster_results <- polls %>% mutate(X_hat = (d_hat + 1) / 2) %>% mutate(se_hat = 2 * sqrt(X_hat * (1 - X_hat) / samplesize)) %>% mutate(lower = d_hat - qnorm(0.975) * se_hat) %>% mutate(upper = d_hat + qnorm(0.975) * se_hat) %>% select(pollster, enddate, d_hat, lower, upper)
pollster_results

pollster
<fctr>
	
enddate
<date>
	
d_hat
<dbl>
	
ABC News/Washington Post	2016-11-06	0.0400	
Google Consumer Surveys	2016-11-07	0.0234	
Ipsos	2016-11-06	0.0300	
YouGov	2016-11-07	0.0400	
Gravis Marketing	2016-11-06	0.0400	
Fox News/Anderson Robbins Research/Shaw & Company Research	2016-11-06	0.0400	
CBS News/New York Times	2016-11-06	0.0400	
NBC News/Wall Street Journal	2016-11-05	0.0400	
IBD/TIPP	2016-11-07	-0.0150	
Selzer & Company	2016-11-06	0.0300	
1-10 of 70 rows | 1-3 of 5 columns

    Comparing to actual results - d
    What proportion of confidence intervals for the difference between the proportion of voters included d, the actual difference in election day?

Instructions

    Use the mutate function to define a new variable withinpollster_results called hit.
    Use logical expressions to determine if each values in lower and upper span the actual difference in proportions of voters.
    Use the mean function to determine the average value in hit and summarize the results using summarize.
    Save the result as an object called avg_hit.

# The `pollster_results` object has already been loaded. Examine it using the `head` function.
head(pollster_results)

 
 
	
pollster
<fctr>
	
enddate
<date>
	
d_hat
<dbl>
	
1	ABC News/Washington Post	2016-11-06	0.0400	
2	Google Consumer Surveys	2016-11-07	0.0234	
3	Ipsos	2016-11-06	0.0300	
4	YouGov	2016-11-07	0.0400	
5	Gravis Marketing	2016-11-06	0.0400	
6	Fox News/Anderson Robbins Research/Shaw & Company Research	2016-11-06	0.0400	
6 rows | 1-4 of 6 columns

# Add a logical variable called `hit` that indicates whether the actual value (0.021) exists within the confidence interval of each poll. Summarize the average `hit` result to determine the proportion of polls with confidence intervals include the actual value. Save the result as an object called `avg_hit`.
avg_hit <- pollster_results %>% mutate(hit=lower <= 0.021 & upper >= 0.021) %>% summarize(mean(hit))

    Comparing to actual results by pollster
    Although the proportion of confidence intervals that include the actual difference between the proportion of voters increases substantially, it is still lower that 0.95. In the next chapter, we learn the reason for this.

To motivate our next exercises, calculate the difference between each poll’s estimate d¯ and the actual d=0.021. Stratify this difference, or error, by pollster in a plot.

Instructions

    Define a new variable errors that contains the difference between the estimated difference between the proportion of voters and the actual difference on election day, 0.021.
    To create the plot of errors by pollster, add a layer with the function geom_point. The aesthetic mappings require a definition of the x-axis and y-axis variables. So the code looks like the example below, but you fill in the variables for x and y.
    The last line of the example code adjusts the x-axis labels so that they are easier to read.

data %>% ggplot(aes(x = , y = )) +
  geom_point() +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))

# The `polls` object has already been loaded. Examine it using the `head` function.
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
1	U.S.	2016-11-03	2016-11-06	
2	U.S.	2016-11-01	2016-11-07	
3	U.S.	2016-11-02	2016-11-06	
4	U.S.	2016-11-04	2016-11-07	
5	U.S.	2016-11-03	2016-11-06	
6	U.S.	2016-11-03	2016-11-06	
6 rows | 1-4 of 17 columns

# Add variable called `error` to the object `polls` that contains the difference between d_hat and the actual difference on election day. Then make a plot of the error stratified by pollster.
polls %>% mutate(error = d_hat - 0.021) %>% ggplot(aes(x = pollster, y = error)) + geom_point() + theme(axis.text.x = element_text(angle = 90, hjust = 1))

    Comparing to actual results by pollster - multiple polls
    Remake the plot you made for the previous exercise, but only for pollsters that took five or more polls.

You can use dplyr tools group_by and n to group data by a variable of interest and then count the number of observations in the groups. The function filter filters data piped into it by your specified condition.

For example:

data %>% group_by(variable_for_grouping) 
    %>% filter(n() >= 5)

Instructions

    Define a new variable errors that contains the difference between the estimated difference between the proportion of voters and the actual difference on election day, 0.021.
    Group the data by pollster using the group_by function.
    Filter the data by pollsters with 5 or more polls.
    Use ggplot to create the plot of errors by pollster.
    Add a layer with the function geom_point.

# The `polls` object has already been loaded. Examine it using the `head` function.
# The `polls` object has already been loaded. Examine it using the `head` function.
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
1	U.S.	2016-11-03	2016-11-06	
2	U.S.	2016-11-01	2016-11-07	
3	U.S.	2016-11-02	2016-11-06	
4	U.S.	2016-11-04	2016-11-07	
5	U.S.	2016-11-03	2016-11-06	
6	U.S.	2016-11-03	2016-11-06	
6 rows | 1-4 of 17 columns

# Add variable called `error` to the object `polls` that contains the difference between d_hat and the actual difference on election day. Then make a plot of the error stratified by pollster, but only for pollsters who took 5 or more polls.
polls %>% mutate(error = d_hat - 0.021) %>%
  group_by(pollster) %>%
  filter(n() >= 5) %>%
  ggplot(aes(pollster, error)) +
  geom_point() +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))

Section 4 Overview

In Section 4, you will look at statistical models in the context of election polling and forecasting.

After completing Section 4, you will be able to:

    Understand how aggregating data from different sources, as poll aggregators do for poll data, can improve the precision of a prediction.
    Understand how to fit a multilevel model to the data to forecast, for example, election results.
    Explain why a simple aggregation of data is insufficient to combine results because of factors such as pollster bias.
    Use a data-driven model to account for additional types of sampling variability such as pollster-to-pollster variability.

The textbook for this section is available here
Assessment 4.1: Statistical Models

    Heights Revisited
    We have been using urn models to motivate the use of probability models. However, most data science applications are not related to data obtained from urns. More common are data that come from individuals. Probability plays a role because the data come from a random sample. The random sample is taken from a population and the urn serves as an analogy for the population.

Let’s revisit the heights dataset. For now, consider x to be the heights of all males in the data set. Mathematically speaking, x is our population. Using the urn analogy, we have an urn with the values of x in it.

What are the population average and standard deviation of our population?

Instructions

    Execute the lines of code that create a vector x that contains heights for all males in the population.
    Calculate the average of x.
    Calculate the standard deviation of x.

# Load the 'dslabs' package and data contained in 'heights'
library(dslabs)
library(dplyr)
data(heights)

# Make a vector of heights from all males in the population
x <- heights %>% filter(sex == "Male") %>%
  .$height

# Calculate the population average. Print this value to the console.
mean(x)

## [1] 69.31475

# Calculate the population standard deviation. Print this value to the console.
sd(x)

## [1] 3.611024

    Sample the population of heights
    Call the population average computed above μ and the standard deviation σ. Now take a sample of size 50, with replacement, and construct an estimate for μ and σ.

Instructions

    Use the sample function to sample N values from x.
    Calculate the mean of the sampled heights.
    Calculate the standard deviation of the sampled heights.

# The vector of all male heights in our population `x` has already been loaded for you. You can examine the first six elements using `head`.
head(x)

## [1] 75 70 68 74 61 67

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Define `N` as the number of people measured
N <- 50

# Define `X` as a random sample from our population `x`
X <- sample(x, N, replace = TRUE)

# Calculate the sample average. Print this value to the console.
mean(X)

## [1] 70.47293

# Calculate the sample standard deviation. Print this value to the console.
sd(X)

## [1] 3.426742

    Sample and Population Averages
    What does the central limit theory tell us about the sample average and how it is related to μ, the population average?

Possible Answers

A. It is identical to μ.
B. It is a random variable with expected value μ and standard error  σ/N−−√

.
C. It is a random variable with expected value μ and standard error σ.
D. It underestimates μ.

    Confidence Interval Calculation
    We will use  X¯

as our estimate of the heights in the population from our sample size N. We know from previous exercises that the standard estimate of our error  X¯−μ is  σ/N−−√

    .

Construct a 95% confidence interval for μ.

Instructions

    Use the sd and sqrt functions to define the standard error se
    Calculate the 95% confidence intervals using the qnorm function. Save the lower then the upper confidence interval to a variable called ci.

# The vector of all male heights in our population `x` has already been loaded for you. You can examine the first six elements using `head`.
head(x)

## [1] 75 70 68 74 61 67

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Define `N` as the number of people measured
N <- 50

# Define `X` as a random sample from our population `x`
X <- sample(x, N, replace = TRUE)

# Define `se` as the standard error of the estimate. Print this value to the console.
X_hat <- mean(X)
se_hat <- sd(X)
se <- se_hat / sqrt(N)
se

## [1] 0.4846145

# Construct a 95% confidence interval for the population average based on our sample. Save the lower and then the upper confidence interval to a variable called `ci`.
ci <- c(qnorm(0.025, mean(X), se), qnorm(0.975, mean(X), se))

    Monte Carlo Simulation for Heights
    Now run a Monte Carlo simulation in which you compute 10,000 confidence intervals as you have just done. What proportion of these intervals include μ?

Instructions

    Use the replicate function to replicate the sample code for B <- 10000 simulations. Save the results of the replicated code to a variable called res. The replicated code should complete the following steps: -1. Use the sample function to sample N values from x. Save the sampled heights as a vector called X. -2. Create an object called interval that contains the 95% confidence interval for each of the samples. Use the same formula you used in the previous exercise to calculate this interval. -3. Use the between function to determine if μ is contained within the confidence interval of that simulation.
    Finally, use the mean function to determine the proportion of results in res that contain mu.

# Define `mu` as the population average
mu <- mean(x)

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Define `N` as the number of people measured
N <- 50

# Define `B` as the number of times to run the model
B <- 10000

# Define an object `res` that contains a logical vector for simulated intervals that contain mu
res <- replicate(B, {
  X <- sample(x, N, replace = TRUE)
  X_hat <- mean(X)
  se_hat <- sd(X)
  se <- se_hat / sqrt(N)
  interval <- c(qnorm(0.025, mean(X), se) , qnorm(0.975, mean(X), se))
  between(mu, interval[1], interval[2])
})

# Calculate the proportion of results in `res` that include mu. Print this value to the console.
mean(res)

## [1] 0.9479

    Visualizing Polling Bias
    In this section, we used visualization to motivate the presence of pollster bias in election polls. Here we will examine that bias more rigorously. Lets consider two pollsters that conducted daily polls and look at national polls for the month before the election.

Is there a poll bias? Make a plot of the spreads for each poll.

Instructions

    Use ggplot to plot the spread for each of the two pollsters.
    Define the x- and y-axes usingusing aes() within the ggplot function.
    Use geom_boxplot to make a boxplot of the data.
    Use geom_point to add data points to the plot.

# Load the libraries and data you need for the following exercises
library(dslabs)
library(dplyr)
library(ggplot2)
data("polls_us_election_2016")

# These lines of code filter for the polls we want and calculate the spreads
polls <- polls_us_election_2016 %>% 
  filter(pollster %in% c("Rasmussen Reports/Pulse Opinion Research","The Times-Picayune/Lucid") &
           enddate >= "2016-10-15" &
           state == "U.S.") %>% 
  mutate(spread = rawpoll_clinton/100 - rawpoll_trump/100) 

# Make a boxplot with points of the spread for each pollster
polls %>% ggplot(aes(pollster, spread)) + geom_boxplot() + geom_point()

    Defining Pollster Bias
    The data do seem to suggest there is a difference between the pollsters. However, these data are subject to variability. Perhaps the differences we observe are due to chance. Under the urn model, both pollsters should have the same expected value: the election day difference,  d

    .

We will model the observed data Yij in the following way:

 Yij=d+bi+εij

with  i=1,2
indexing the two pollsters, bi the bias for pollster  i, and  εij poll to poll chance variability. We assume the ε are independent from each other, have expected value 0 and standard deviation  σi regardless of  j

.

Which of the following statements best reflects what we need to know to determine if our data fit the urn model?

Possible Answers

A. Is  εij=0
?
B. How close are  Yij to  d?
C. Is  b1≠b2?
D. Are  b1=0 and  b2=0

?

    Derive Expected Value
    We modelled the observed data  Yij

    as:

 Yij=d+bi+εij

On the right side of this model, only  εij

is a random variable. The other two values are constants.

What is the expected value of  Yij

?

Possible Answers

A.  d+b1

B.  b1+εij C.  d
D.  d+b1+εij

    Expected Value and Standard Error of Poll 1
    Suppose we define  Y¯1

    as the average of poll results from the first poll and σ1 as the standard deviation of the first poll.

What is the expected value and standard error of  Y¯1

?

Possible Answers

A. The expected value is  d+b1
and the standard error is  σ1
B. The expected value is  d and the standard error is  σ1/N1−−−√
C. The expected value is  d+b1 and the standard error is  σ1/N1−−−√
D. The expected value is  d and the standard error is  σ1+N1−−−√

    Expected Value and Standard Error of Poll 2
    Now we define  Y¯2

    as the average of poll results from the second poll.

What is the expected value and standard error of  Y¯2

?

Possible Answers

A. The expected value is  d+b2
and the standard error is  σ2 B. The expected value is  d and the standard error is  σ2/N2−−−√ C. The expected value is  d+b2 and the standard error is  σ2/N2−−−√ D. The expected value is  d and the standard error is  σ2+N2−−−√

    Difference in Expected Values Between Polls
    Using what we learned by answering the previous questions, what is the expected value of  Y¯2−Y¯1

    ?

Possible Answers

A.  (b2−b1)2
B.  b2−b1/(√N) C.  b2+b1 D.  b2−b1

    Standard Error of the Difference Between Polls
    Using what we learned by answering the questions above, what is the standard error of  Y¯2−Y¯1

    ?

Possible Answers

A.  σ22/N2+σ21/N1−−−−−−−−−−−−−√
B.  σ2/N2+σ1/N1−−−−−−−−−−−−√ C.  (σ22/N2+σ21/N1)2 D.  σ22/N2+σ21/N1

    Compute the Estimates
    The answer to the previous question depends on  σ1

and  σ2

    , which we don’t know. We learned that we can estimate these values using the sample standard deviation.

Compute the estimates of  σ1
and  σ2

.

Instructions

    Group the data by pollster.
    Summarize the standard deviation of the spreads for each of the two pollsters.
    Store the pollster names and standard deviations of the spreads (σ) in an object called sigma

# The `polls` data have already been loaded for you. Use the `head` function to examine them.
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
1	U.S.	2016-11-05	2016-11-07	The Times-Picayune/Lucid	NA	
2	U.S.	2016-11-02	2016-11-06	Rasmussen Reports/Pulse Opinion Research	C+	
3	U.S.	2016-11-01	2016-11-03	Rasmussen Reports/Pulse Opinion Research	C+	
4	U.S.	2016-11-04	2016-11-06	The Times-Picayune/Lucid	NA	
5	U.S.	2016-10-31	2016-11-02	Rasmussen Reports/Pulse Opinion Research	C+	
6	U.S.	2016-11-03	2016-11-05	The Times-Picayune/Lucid	NA	
6 rows | 1-6 of 17 columns

# Create an object called `sigma` that contains a column for `pollster` and a column for `s`, the standard deviation of the spread
polls %>% group_by(pollster)

state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
samplesize
<int>
	
U.S.	2016-11-05	2016-11-07	The Times-Picayune/Lucid	NA	2521	
U.S.	2016-11-02	2016-11-06	Rasmussen Reports/Pulse Opinion Research	C+	1500	
U.S.	2016-11-01	2016-11-03	Rasmussen Reports/Pulse Opinion Research	C+	1500	
U.S.	2016-11-04	2016-11-06	The Times-Picayune/Lucid	NA	2584	
U.S.	2016-10-31	2016-11-02	Rasmussen Reports/Pulse Opinion Research	C+	1500	
U.S.	2016-11-03	2016-11-05	The Times-Picayune/Lucid	NA	2526	
U.S.	2016-10-27	2016-10-31	Rasmussen Reports/Pulse Opinion Research	C+	1500	
U.S.	2016-10-30	2016-11-01	Rasmussen Reports/Pulse Opinion Research	C+	1500	
U.S.	2016-11-02	2016-11-04	The Times-Picayune/Lucid	NA	2561	
U.S.	2016-11-01	2016-11-03	The Times-Picayune/Lucid	NA	2627	
1-10 of 40 rows | 1-6 of 16 columns

sigma <- polls %>% group_by(pollster) %>% summarize(s = sd(spread))

# Print the contents of sigma to the console
sigma

pollster
<fctr>
	
s
<dbl>
Rasmussen Reports/Pulse Opinion Research	0.01768945
The Times-Picayune/Lucid	0.02678078
2 rows

    Probability Distribution of the Spread
    What does the central limit theorem tell us about the distribution of the differences between the pollster averages,  Y¯2−Y¯1

    ?

Possible Answers

A. The central limit theorem cannot tell us anything because this difference is not the average of a sample.
B. Because  Yij
are approximately normal, the averages are normal too.
C. If we assume N2 and N1 are large enough,  Y¯2 and  Y¯1

, and their difference, are approximately normal.
D. These data do not contain vectors of 0 and 1, so the central limit theorem does not apply.

    Calculate the 95% Confidence Interval of the Spreads
    We have constructed a random variable that has expected value  b2−b1

, the pollster bias difference. If our model holds, then this random variable has an approximately normal distribution. The standard error of this random variable depends on  σ1 and  σ2, but we can use the sample standard deviations we computed earlier. We have everything we need to answer our initial question: is  b2−b1

    different from 0?

Construct a 95% confidence interval for the difference  b2
and  b1

. Does this interval contain zero?

Instructions

    Use pipes %>% to pass the data polls on to functions that will group by pollster and summarize the average spread, standard deviation, and number of polls per pollster.
    Calculate the estimate by subtracting the average spreads.
    Calculate the standard error using the standard deviations of the spreads and the sample size.
    Calculate the 95% confidence intervals using the qnorm function. Save the lower and then the upper confidence interval to a variable called ci.

# The `polls` data have already been loaded for you. Use the `head` function to examine them.
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
1	U.S.	2016-11-05	2016-11-07	The Times-Picayune/Lucid	NA	
2	U.S.	2016-11-02	2016-11-06	Rasmussen Reports/Pulse Opinion Research	C+	
3	U.S.	2016-11-01	2016-11-03	Rasmussen Reports/Pulse Opinion Research	C+	
4	U.S.	2016-11-04	2016-11-06	The Times-Picayune/Lucid	NA	
5	U.S.	2016-10-31	2016-11-02	Rasmussen Reports/Pulse Opinion Research	C+	
6	U.S.	2016-11-03	2016-11-05	The Times-Picayune/Lucid	NA	
6 rows | 1-6 of 17 columns

names(polls)

##  [1] "state"            "startdate"        "enddate"         
##  [4] "pollster"         "grade"            "samplesize"      
##  [7] "population"       "rawpoll_clinton"  "rawpoll_trump"   
## [10] "rawpoll_johnson"  "rawpoll_mcmullin" "adjpoll_clinton" 
## [13] "adjpoll_trump"    "adjpoll_johnson"  "adjpoll_mcmullin"
## [16] "spread"

# Create an object called `res` that summarizes the average, standard deviation, and number of polls for the two pollsters.
res <- polls %>% group_by(pollster) %>% summarize(avg=mean(spread), s = sd(spread), N=n())
res

pollster
<fctr>
	
avg
<dbl>
	
s
<dbl>
	
N
<int>
Rasmussen Reports/Pulse Opinion Research	0.00062500	0.01768945	16
The Times-Picayune/Lucid	0.05291667	0.02678078	24
2 rows

# Store the difference between the larger average and the smaller in a variable called `estimate`. Print this value to the console.
estimate <- max(res$avg) - min(res$avg)
estimate

## [1] 0.05229167

# Store the standard error of the estimates as a variable called `se_hat`. Print this value to the console.
se_hat <- sqrt(res$s[2]^2/res$N[2] + res$s[1]^2/res$N[1])
se_hat

## [1] 0.007031433

# Calculate the 95% confidence interval of the spreads. Save the lower and then the upper confidence interval to a variable called `ci`.
ci <- c(estimate - qnorm(0.975)*se_hat, estimate + qnorm(0.975)*se_hat)

    Calculate the P-value
    The confidence interval tells us there is relatively strong pollster effect resulting in a difference of about 5%. Random variability does not seem to explain it.

Compute a p-value to relay the fact that chance does not explain the observed pollster effect.

Instructions

    Use the pnorm function to calculate the probability that a random value is larger than the observed ratio of the estimate to the standard error.
    Multiply the probability by 2, because this is the two-tailed test.

# We made an object `res` to summarize the average, standard deviation, and number of polls for the two pollsters.
res <- polls %>% group_by(pollster) %>% 
  summarize(avg = mean(spread), s = sd(spread), N = n()) 

# The variables `estimate` and `se_hat` contain the spread estimates and standard error, respectively.
estimate <- res$avg[2] - res$avg[1]
se_hat <- sqrt(res$s[2]^2/res$N[2] + res$s[1]^2/res$N[1])

# Calculate the p-value
2 * (1 - pnorm(estimate / se_hat, 0, 1))

## [1] 1.030287e-13

    Comparing Within-Poll and Between-Poll Variability
    We compute statistic called the t-statistic by dividing our estimate of  b2−b1

    by its estimated standard error:

 Y¯2−Y¯1s22/N2+s21/N1√

Later we learn will learn of another approximation for the distribution of this statistic for values of N2 and N1 that aren’t large enough for the CLT.

Note that our data has more than two pollsters. We can also test for pollster effect using all pollsters, not just two. The idea is to compare the variability across polls to variability within polls. We can construct statistics to test for effects and approximate their distribution. The area of statistics that does this is called Analysis of Variance or ANOVA. We do not cover it here, but ANOVA provides a very useful set of tools to answer questions such as: is there a pollster effect?

Compute the average and standard deviation for each pollster and examine the variability across the averages and how it compares to the variability within the pollsters, summarized by the standard deviation.

Instructions

    Group the polls data by pollster.
    Summarize the average and standard deviation of the spreads for each pollster.
    Create an object called var that contains three columns: pollster, mean spread, and standard deviation.
    Be sure to name the column for mean avg and the column for standard deviation s.

# Execute the following lines of code to filter the polling data and calculate the spread
polls <- polls_us_election_2016 %>% 
  filter(enddate >= "2016-10-15" &
           state == "U.S.") %>%
  group_by(pollster) %>%
  filter(n() >= 5) %>% 
  mutate(spread = rawpoll_clinton/100 - rawpoll_trump/100) %>%
  ungroup()

# Create an object called `var` that contains columns for the pollster, mean spread, and standard deviation. Print the contents of this object to the console.
var <- polls %>% group_by(pollster) %>% summarize(avg = mean(spread), s = sd(spread))
var

pollster
<fctr>
	
avg
<dbl>
	
s
<dbl>
ABC News/Washington Post	0.037333333	0.033904628
CVOTER International	0.027895455	0.017975499
Google Consumer Surveys	0.030280000	0.018476390
Gravis Marketing	0.016000000	0.015165751
IBD/TIPP	0.001047619	0.016832933
Ipsos	0.055272727	0.019464698
Morning Consult	0.041428571	0.014638501
Rasmussen Reports/Pulse Opinion Research	0.000625000	0.017689451
The Times-Picayune/Lucid	0.052916667	0.026780779
USC Dornsife/LA Times	-0.021320833	0.020661474
1-10 of 11 rows
Section 5 Overview

In Section 5, you will learn about Bayesian statistics through looking at examples from rare disease diagnosis and baseball.

After completing Section 5, you will be able to:

    Apply Bayes’ theorem to calculate the probability of A given B.
    Understand how to use hierarchical models to make better predictions by considering multiple levels of variability.
    Compute a posterior probability using an empirical Bayesian approach.
    Calculate a 95% credible interval from a posterior probability.

The textbook for this section is available here
Assessment 5.1: Bayesian Statistics

    Statistics in the Courtroom
    In 1999 in England Sally Clark was found guilty of the murder of two of her sons. Both infants were found dead in the morning, one in 1996 and another in 1998, and she claimed the cause of death was sudden infant death syndrome (SIDS). No evidence of physical harm was found on the two infants so the main piece of evidence against her was the testimony of Professor Sir Roy Meadow, who testified that the chances of two infants dying of SIDS was 1 in 73 million. He arrived at this figure by finding that the rate of SIDS was 1 in 8,500 and then calculating that the chance of two SIDS cases was 8,500 × 8,500 ≈ 73 million.

Based on what we’ve learned throughout this course, which statement best describes a potential flaw in Sir Meadow’s reasoning?

Possible Answers

A. Sir Meadow assumed the second death was independent of the first son being affected, thereby ignoring possible genetic causes.
B. There is no flaw. The multiplicative rule always applies in this way: Pr(A and B)=Pr(A)Pr(B)
C. Sir Meadow should have added the probabilities: Pr(A and B)=Pr(A)+Pr(B)
D. The rate of SIDS is too low to perform these types of statistics.

    Recalculating the SIDS Statistics
    Let’s assume that there is in fact a genetic component to SIDS and the the probability of Pr(second case of SIDS∣first case of SIDS)=1/100, is much higher than 1 in 8,500.

What is the probability of both of Sally Clark’s sons dying of SIDS?

Instructions

    Calculate the probability of both sons dying to SIDS.

# Define `Pr_1` as the probability of the first son dying of SIDS
Pr_1 <- 1/8500

# Define `Pr_2` as the probability of the second son dying of SIDS
Pr_2 <- 1/100

# Calculate the probability of both sons dying of SIDS. Print this value to the console.
Pr_1*Pr_2

## [1] 1.176471e-06

    NBayes’ Rule in the Courtroom
    Many press reports stated that the expert claimed the probability of Sally Clark being innocent as 1 in 73 million. Perhaps the jury and judge also interpreted the testimony this way. This probability can be written like this:

 Pr(mother is a murderer∣two children found dead with no evidence of harm)

Possible Answers

A.  Pr(two children found dead with no evidence of harm)Pr(mother is a murderer)Pr(two children found dead with no evidence of harm)

B.  Pr(two children found dead with no evidence of harm)Pr(mother is a murderer)

C.  Pr(two children found dead with no evidence of harm∣mother is a murderer)Pr(mother is a murderer)Pr(two children found dead with no evidence of harm)

D. 1/8500

    Calculate the Probability
    Assume that the probability of a murderer finding a way to kill her two children without leaving evidence of physical harm is:

 Pr(two children found dead with no evidence of harm∣mother is a murderer)=0.50

Assume that the murder rate among mothers is 1 in 1,000,000.

 Pr(mother is a murderer)=1/1,000,000

According to Bayes’ rule, what is the probability of:

 Pr(mother is a murderer∣two children found dead with no evidence of harm)

Instructions

Use Bayes’ rule to calculate the probability that the mother is a murderer, considering the rates of murdering mothers in the population, the probability that two siblings die of SIDS, and the probability that a murderer kills children without leaving evidence of physical harm.

# Define `Pr_1` as the probability of the first son dying of SIDS
Pr_1 <- 1/8500

# Define `Pr_2` as the probability of the second son dying of SIDS
Pr_2 <- 1/100

# Define `Pr_B` as the probability of both sons dying of SIDS
Pr_B <- Pr_1*Pr_2

# Define Pr_A as the rate of mothers that are murderers
Pr_A <- 1/1000000

# Define Pr_BA as the probability that two children die without evidence of harm, given that their mother is a murderer
Pr_BA <- 0.50

# Define Pr_AB as the probability that a mother is a murderer, given that her two children died with no evidence of physical harm. Print this value to the console.
Pr_AB <- Pr_BA*Pr_A/Pr_B
Pr_AB

## [1] 0.425

    Misuse of Statistics in the Courts
    After Sally Clark was found guilty, the Royal Statistical Society issued a statement saying that there was “no statistical basis” for the expert’s claim. They expressed concern at the “misuse of statistics in the courts”. Eventually, Sally Clark was acquitted in June 2003.

In addition to misusing the multiplicative rule as we saw earlier, what else did Sir Meadow miss?

Possible Answers

A. He made an arithmetic error in forgetting to divide by the rate of SIDS in siblings.
B. He did not take into account how rare it is for a mother to murder her children.
C. He mixed up the numerator and denominator of Bayes’ rule.
D. He did not take into account murder rates in the population.

    Back to Election Polls
    Florida is one of the most closely watched states in the U.S. election because it has many electoral votes and the election is generally close. Create a table with the poll spread results from Florida taken during the last days before the election using the sample code.

The CLT tells us that the average of these spreads is approximately normal. Calculate a spread average and provide an estimate of the standard error.

Instructions

    Calculate the average of the spreads. Call this average avg in the final table.
    Calculate an estimate of the standard error of the spreads. Call this standard error se in the final table.
    Use the mean and sd functions nested within summarize to find the average and standard deviation of the grouped spread data.
    Save your results in an object called results.

# Load the libraries and poll data
library(dplyr)
library(dslabs)
data(polls_us_election_2016)

# Create an object `polls` that contains the spread of predictions for each candidate in Florida during the last polling days
polls <- polls_us_election_2016 %>% 
  filter(state == "Florida" & enddate >= "2016-11-04" ) %>% 
  mutate(spread = rawpoll_clinton/100 - rawpoll_trump/100)

# Examine the `polls` object using the `head` function
head(polls)

 
 
	
state
<fctr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
1	Florida	2016-11-03	2016-11-06	Quinnipiac University	A-	
2	Florida	2016-11-02	2016-11-04	YouGov	B	
3	Florida	2016-11-01	2016-11-07	SurveyMonkey	C-	
4	Florida	2016-11-06	2016-11-06	Trafalgar Group	C	
5	Florida	2016-11-05	2016-11-06	Opinion Savvy/InsiderAdvantage	C-	
6	Florida	2016-11-02	2016-11-06	Rasmussen Reports/Pulse Opinion Research	C+	
6 rows | 1-6 of 17 columns

# Create an object called `results` that has two columns containing the average spread (`avg`) and the standard error (`se`). Print the results to the console.
results <- polls %>% summarize(avg = mean(spread),  se = sd(spread)/sqrt(n()))
results

avg
<dbl>
	
se
<dbl>
0.004154545	0.007218692
1 row

    The Prior Distribution
    Assume a Bayesian model sets the prior distribution for Florida’s election night spread d to be normal with expected value μ and standard deviation τ.

What are the interpretations of μ and τ?

Possible Answers

A. μ and τ are arbitrary numbers that let us make probability statements about d.
B. μ and τ summarize what we would predict for Florida before seeing any polls.
C. μ and τ summarize what we want to be true. We therefore set μ at 0.10 and τ at 0.01.
D. The choice of prior has no effect on the Bayesian analysis.

    Estimate the Posterior Distribution
    The CLT tells us that our estimate of the spread  d^

    has a normal distribution with expected value d and standard deviation σ, which we calculated in a previous exercise.

Use the formulas for the posterior distribution to calculate the expected value of the posterior distribution if we set μ=0 and τ=0.01.

Instructions

    Define μ and τ Identify which elements stored in the object results represent σ and Y
    Estimate B using σ and τ
    Estimate the posterior distribution using B, μ, and Y

# The results` object has already been loaded. Examine the values stored: `avg` and `se` of the spread
results

avg
<dbl>
	
se
<dbl>
0.004154545	0.007218692
1 row

# Define `mu` and `tau`
mu <- 0
tau <- 0.01

# Define a variable called `sigma` that contains the standard error in the object `results
sigma <- results$se

# Define a variable called `Y` that contains the average in the object `results`
Y <- results$avg

# Define a variable `B` using `sigma` and `tau`. Print this value to the console.
tau <- 0.01
miu <- 0
B <- sigma^2 / (sigma^2 + tau^2)
B

## [1] 0.342579

# Calculate the expected value of the posterior distribution
miu + (1 - B) * (Y - miu)

## [1] 0.002731286

    Standard Error of the Posterior Distribution
    Compute the standard error of the posterior distribution.

Instructions

    Using the variables we have defined so far, calculate the standard error of the posterior distribution.
    Print this value to the console.

# Here are the variables we have defined
mu <- 0
tau <- 0.01
sigma <- results$se
Y <- results$avg
B <- sigma^2 / (sigma^2 + tau^2)

# Compute the standard error of the posterior distribution. Print this value to the console.
sqrt(1 / (1 / sigma ^2 + 1 / tau ^2))

## [1] 0.005853024

    Constructing a Credible Interval
    Using the fact that the posterior distribution is normal, create an interval that has a 95% of occurring centered at the posterior expected value. Note that we call these credible intervals.

Instructions

    Calculate the 95% credible intervals using the qnorm function.
    Save the lower and upper confidence intervals as an object called ci. Save the lower - confidence interval first.

# Here are the variables we have defined in previous exercises
mu <- 0
tau <- 0.01
sigma <- results$se
Y <- results$avg
B <- sigma^2 / (sigma^2 + tau^2)
se <- sqrt( 1/ (1/sigma^2 + 1/tau^2))

# Construct the 95% credible interval. Save the lower and then the upper confidence interval to a variable called `ci`.
est <- B * mu + (1 - B) * Y
est

## [1] 0.002731286

ci <- c(est - qnorm(0.975) * se, est + qnorm(0.975) * se)
ci

## [1] -0.008740432  0.014203003

    Odds of Winning Florida
    According to this analysis, what was the probability that Trump wins Florida?

Instructions

    Using the pnorm function, calculate the probability that the spread in Florida was less than 0.

# Assign the expected value of the posterior distribution to the variable `exp_value`
exp_value <- B*mu + (1-B)*Y 

# Assign the standard error of the posterior distribution to the variable `se`
se <- sqrt( 1/ (1/sigma^2 + 1/tau^2))

# Using the `pnorm` function, calculate the probability that the actual spread was less than 0 (in Trump's favor). Print this value to the console.
pnorm(0, exp_value, se)

## [1] 0.3203769

    Change the Priors
    We had set the prior variance τ to 0.01, reflecting that these races are often close.

Change the prior variance to include values ranging from 0.005 to 0.05 and observe how the probability of Trump winning Florida changes by making a plot.

Instructions

    Create a vector of values of taus by executing the sample code.
    Create a function using function(){} called p_calc that first calculates B given tau and sigma and then calculates the probability of Trump winning, as we did in the previous exercise.
    Apply your p_calc function across all the new values of taus.
    Use the plot function to plot τ on the x-axis and the new probabilities on the y-axis.

# Define the variables from previous exercises
mu <- 0
sigma <- results$se
Y <- results$avg

# Define a variable `taus` as different values of tau
taus <- seq(0.005, 0.05, len = 100)

# Create a function called `p_calc` that generates `B` and calculates the probability of the spread being less than 0
p_calc <- function(tau) {
  B <- sigma ^ 2 / (sigma^2 + tau^2)
  se <- sqrt(1 / (1/sigma^2 + 1/tau^2))
  exp_value <- B * mu + (1 - B) * Y
  pnorm(0, exp_value, se)
}

# Create a vector called `ps` by applying the function `p_calc` across values in `taus`
ps <- p_calc(taus)

# Plot `taus` on the x-axis and `ps` on the y-axis
plot(taus, ps)

Section 6 Overview

In Section 6, you will learn about election forecasting, building on what you’ve learned in the previous sections about statistical modeling and Bayesian statistics.

After completing Section 6, you will be able to:

Understand how pollsters use hierarchical models to forecast the results of elections.
Incorporate multiple sources of variability into a mathematical model to make predictions.
Construct confidence intervals that better model deviations such as those seen in election data using the t-distribution. There are 2 assignments that use the DataCamp platform for you to practice your coding skills.

The textbook for this section is available here
Assessment 6.1: Election Forecasting

    Confidence Intervals of Polling Data
    For each poll in the polling data set, use the CLT to create a 95% confidence interval for the spread. Create a new table called cis that contains columns for the lower and upper limits of the confidence intervals.

Instructions

    Use pipes %>% to pass the poll object on to the mutate function, which creates new variables.
    Create a variable called X_hatthat contains the estimate of the proportion of Clinton voters for each poll.
    Create a variable called se that contains the standard error of the spread.
    Calculate the confidence intervals using the qnorm function and your calculated se.
    Use the select function to keep the following columns: state, startdate, enddate, pollster, grade, spread, lower, upper.

## Load the libraries and data
library(dplyr)
library(dslabs)
data("polls_us_election_2016")

# Create a table called `polls` that filters by  state, date, and reports the spread
polls <- polls_us_election_2016 %>% 
  filter(state != "U.S." & enddate >= "2016-10-31") %>% 
  mutate(spread = rawpoll_clinton/100 - rawpoll_trump/100)

# Create an object called `cis` that has the columns indicated in the instructions
cis <- polls %>% mutate(X_hat = (spread+1)/2, se = 2*sqrt(X_hat*(1-X_hat)/samplesize), 
                 lower = spread - qnorm(0.975)*se, upper = spread + qnorm(0.975)*se) %>%
  select(state, startdate, enddate, pollster, grade, spread, lower, upper)

    Compare to Actual Results
    You can add the final result to the cis table you just created using the left_join function as shown in the sample code.

Now determine how often the 95% confidence interval includes the actual result.

Instructions

    Create an object called p_hits that contains the proportion of intervals that contain the actual spread using the following steps.
    Use the mutate function to create a new variable called hit that contains a logical vector for whether the actual_spread falls between the lower and upper confidence intervals.
    Summarize the proportion of values in hit that are true as a variable called proportion_hits.

# Add the actual results to the `cis` data set
add <- results_us_election_2016 %>% mutate(actual_spread = clinton/100 - trump/100) %>% select(state, actual_spread)
ci_data <- cis %>% mutate(state = as.character(state)) %>% left_join(add, by = "state")

# Create an object called `p_hits` that summarizes the proportion of confidence intervals that contain the actual value. Print this object to the console.
p_hits <- ci_data %>% mutate(hit = lower <= actual_spread & upper >= actual_spread) %>% summarize(proportion_hits = mean(hit))
p_hits

proportion_hits
<dbl>
0.66133
1 row

    Stratify by Pollster and Grade
    Now find the proportion of hits for each pollster. Show only pollsters with more than 5 polls and order them from best to worst. Show the number of polls conducted by each pollster and the FiveThirtyEight grade of each pollster.

Instructions

    Create an object called p_hits that contains the proportion of intervals that contain the actual spread using the following steps.
    Use the mutate function to create a new variable called hit that contains a logical vector for whether the actual_spread falls between the lower and upper confidence intervals.
    Use the group_by function to group the data by pollster.
    Use the filter function to filter for pollsters that have more than 5 polls.
    Summarize the proportion of values in hit that are true as a variable called proportion_hits. Also create new variables for the number of polls by each pollster using the n() function and the grade of each poll.
    Use the arrange function to arrange the proportion_hits in descending order.

# The `cis` data have already been loaded for you
add <- results_us_election_2016 %>% mutate(actual_spread = clinton/100 - trump/100) %>% select(state, actual_spread)
ci_data <- cis %>% mutate(state = as.character(state)) %>% left_join(add, by = "state")

# Create an object called `p_hits` that summarizes the proportion of hits for each pollster that has at least 5 polls. 
p_hits <- ci_data %>% mutate(hit = lower <= actual_spread & upper >= actual_spread) %>% 
  group_by(pollster) %>%
  filter(n() >=  5) %>%
  summarize(proportion_hits = mean(hit), n = n(), grade = grade[1]) %>%
  arrange(desc(proportion_hits))
p_hits

pollster
<fctr>
	
proportion_hits
<dbl>
	
n
<int>
	
grade
<fctr>
Quinnipiac University	1.0000000	6	A-
Emerson College	0.9090909	11	B
Public Policy Polling	0.8888889	9	B+
University of New Hampshire	0.8571429	7	B+
Ipsos	0.8067227	119	A-
Mitchell Research & Communications	0.8000000	5	D
Gravis Marketing	0.7826087	23	B-
Trafalgar Group	0.7777778	9	C
Rasmussen Reports/Pulse Opinion Research	0.7741935	31	C+
Remington	0.6666667	9	NA
1-10 of 13 rows

    Stratify by State
    Repeat the previous exercise, but instead of pollster, stratify by state. Here we can’t show grades.

Instructions

    Create an object called p_hits that contains the proportion of intervals that contain the actual spread using the following steps.
    Use the mutate function to create a new variable called hit that contains a logical vector for whether the actual_spread falls between the lower and upper confidence intervals.
    Use the group_by function to group the data by state.
    Use the filter function to filter for states that have more than 5 polls.
    Summarize the proportion of values in hit that are true as a variable called proportion_hits. Also create new variables for the number of polls in each state using the n() function.
    Use the arrange function to arrange the proportion_hits in descending order.

# The `cis` data have already been loaded for you
add <- results_us_election_2016 %>% mutate(actual_spread = clinton/100 - trump/100) %>% select(state, actual_spread)
ci_data <- cis %>% mutate(state = as.character(state)) %>% left_join(add, by = "state")

# Create an object called `p_hits` that summarizes the proportion of hits for each state that has more than 5 polls. 
p_hits <- ci_data %>% mutate(hit = lower <= actual_spread & upper >= actual_spread) %>% 
  group_by(state) %>%
  filter(n() >=  5) %>%
  summarize(proportion_hits = mean(hit), n = n()) %>%
  arrange(desc(proportion_hits)) 
p_hits

state
<chr>
	
proportion_hits
<dbl>
	
n
<int>
Connecticut	1.0000000	13
Delaware	1.0000000	12
Rhode Island	1.0000000	10
New Mexico	0.9411765	17
Washington	0.9333333	15
Oregon	0.9285714	14
Illinois	0.9230769	13
Nevada	0.9230769	26
Maine	0.9166667	12
Montana	0.9166667	12
1-10 of 51 rows

    Plotting Prediction Results
    Make a barplot based on the result from the previous exercise.

Instructions

    Reorder the states in order of the proportion of hits.
    Using ggplot, set the aesthetic with state as the x-variable and proportion of hits as the y-variable.
    Use geom_bar to indicate that we want to plot a barplot. Specifcy stat = "identity" to indicate that the height of the bar should match the value.
    Use coord_flip to flip the axes so the states are displayed from top to bottom and proportions are displayed from left to right.

# The `p_hits` data have already been loaded for you. Use the `head` function to examine it.
head(p_hits)

state
<chr>
	
proportion_hits
<dbl>
	
n
<int>
Connecticut	1.0000000	13
Delaware	1.0000000	12
Rhode Island	1.0000000	10
New Mexico	0.9411765	17
Washington	0.9333333	15
Oregon	0.9285714	14
6 rows

# Make a barplot of the proportion of hits for each state
p_hits %>% mutate(state = reorder(state, proportion_hits)) %>%
  ggplot(aes(state, proportion_hits)) + 
  geom_bar(stat = "identity") +
  coord_flip()

    Predicting the Winner
    Even if a forecaster’s confidence interval is incorrect, the overall predictions will do better if they correctly called the right winner.

Add two columns to the cis table by computing, for each poll, the difference between the predicted spread and the actual spread, and define a column hit that is true if the signs are the same.

Instructions

    Use the mutate function to add two new variables to the cis object: error and hit.
    For the error variable, subtract the actual spread from the spread.
    For the hit variable, return “TRUE” if the poll predicted the actual winner.
    Save the new table as an object called errors.
    Use the tail function to examine the last 6 rows of errors```.

# The `cis` data have already been loaded. Examine it using the `head` function.

cis <- cis %>% mutate(state = as.character(state)) %>% left_join(add, by = "state")

head(cis)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
1	New Mexico	2016-11-06	2016-11-06	Zia Poll	NA	0.02	
2	Virginia	2016-11-03	2016-11-04	Public Policy Polling	B+	0.05	
3	Iowa	2016-11-01	2016-11-04	Selzer & Company	A+	-0.07	
4	Wisconsin	2016-10-26	2016-10-31	Marquette University	A	0.06	
5	North Carolina	2016-11-04	2016-11-06	Siena College	A	0.00	
6	Georgia	2016-11-06	2016-11-06	Landmark Communications	B	-0.03	
6 rows | 1-7 of 10 columns

# Create an object called `errors` that calculates the difference between the predicted and actual spread and indicates if the correct winner was predicted
errors <- cis %>% mutate(error = spread - actual_spread, hit = sign(spread) == sign(actual_spread))

# Examine the last 6 rows of `errors`
tail(errors)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
807	Utah	2016-10-04	2016-11-06	YouGov	B	-0.0910	
808	Utah	2016-10-25	2016-10-31	Google Consumer Surveys	B	-0.0121	
809	South Dakota	2016-10-28	2016-11-02	Ipsos	A-	-0.1875	
810	Washington	2016-10-21	2016-11-02	Ipsos	A-	0.0838	
811	Utah	2016-11-01	2016-11-07	Google Consumer Surveys	B	-0.1372	
812	Oregon	2016-10-21	2016-11-02	Ipsos	A-	0.0905	
6 rows | 1-7 of 12 columns

    Plotting Prediction Results
    Create an object called p_hits that contains the proportion of instances when the sign of the actual spread matches the predicted spread for states with more than 5 polls.

Make a barplot based on the result from the previous exercise that shows the proportion of times the sign of the spread matched the actual result for the data in p_hits.

Instructions

    Use the group_by function to group the data by state.
    Use the filter function to filter for states that have more than 5 polls.
    Summarize the proportion of values in hit that are true as a variable called proportion_hits. Also create new variables for the number of polls in each state using the n() function.
    To make the plot, follow these steps:
    Reorder the states in order of the proportion of hits.
    Using ggplot, set the aesthetic with state as the x-variable and proportion of hits as the y-variable.
    Use geom_bar to indicate that we want to plot a barplot.
    Use coord_flip to flip the axes so the states are displayed from top to bottom and proportions are displayed from left to right.

# Create an object called `errors` that calculates the difference between the predicted and actual spread and indicates if the correct winner was predicted
errors <- cis %>% mutate(error = spread - actual_spread, hit = sign(spread) == sign(actual_spread))

# Create an object called `p_hits` that summarizes the proportion of hits for each state that has more than 5 polls
p_hits <- errors %>%  group_by(state) %>%
  filter(n() >=  5) %>%
  summarize(proportion_hits = mean(hit), n = n())

# Make a barplot of the proportion of hits for each state
p_hits %>% mutate(state = reorder(state, proportion_hits)) %>%
  ggplot(aes(state, proportion_hits)) + 
  geom_bar(stat = "identity") +
 coord_flip()

    Plotting the Errors
    In the previous graph, we see that most states’ polls predicted the correct winner 100% of the time. Only a few states polls’ were incorrect more than 25% of the time. Wisconsin got every single poll wrong. In Pennsylvania and Michigan, more than 90% of the polls had the signs wrong.

Make a histogram of the errors. What is the median of these errors?

Instructions

    Use the hist function to generate a histogram of the errors
    Use the median function to compute the median error

# The `errors` data have already been loaded. Examine them using the `head` function.
head(errors)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
1	New Mexico	2016-11-06	2016-11-06	Zia Poll	NA	0.02	
2	Virginia	2016-11-03	2016-11-04	Public Policy Polling	B+	0.05	
3	Iowa	2016-11-01	2016-11-04	Selzer & Company	A+	-0.07	
4	Wisconsin	2016-10-26	2016-10-31	Marquette University	A	0.06	
5	North Carolina	2016-11-04	2016-11-06	Siena College	A	0.00	
6	Georgia	2016-11-06	2016-11-06	Landmark Communications	B	-0.03	
6 rows | 1-7 of 12 columns

# Generate a histogram of the error
hist(errors$error)

# Calculate the median of the errors. Print this value to the console.
median(errors$error)

## [1] 0.037

    Plot Bias by State
    We see that, at the state level, the median error was slightly in favor of Clinton. The distribution is not centered at 0, but at 0.037. This value represents the general bias we described in an earlier section.

Create a boxplot to examine if the bias was general to all states or if it affected some states differently. Filter the data to include only pollsters with grades B+ or higher.

Instructions

    Use the filter function to filter the data for polls with grades equal to A+, A, A-, or B+.
    Use the reorder function to order the state data by error.
    Using ggplot, set the aesthetic with state as the x-variable and error as the y-variable.
    Use geom_boxplot to indicate that we want to plot a boxplot.
    Use geom_point to add data points as a layer.

# The `errors` data have already been loaded. Examine them using the `head` function.
head(errors)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
1	New Mexico	2016-11-06	2016-11-06	Zia Poll	NA	0.02	
2	Virginia	2016-11-03	2016-11-04	Public Policy Polling	B+	0.05	
3	Iowa	2016-11-01	2016-11-04	Selzer & Company	A+	-0.07	
4	Wisconsin	2016-10-26	2016-10-31	Marquette University	A	0.06	
5	North Carolina	2016-11-04	2016-11-06	Siena College	A	0.00	
6	Georgia	2016-11-06	2016-11-06	Landmark Communications	B	-0.03	
6 rows | 1-7 of 12 columns

# Create a boxplot showing the errors by state for polls with grades B+ or higher
errors %>% filter(grade %in% c("A+","A","A-","B+") | is.na(grade)) %>%
  mutate(state = reorder(state, error)) %>%
  ggplot(aes(state, error)) + 
  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  geom_boxplot() + 
  geom_point()

    Filter Error Plot
    Some of these states only have a few polls. Repeat the previous exercise to plot the errors for each state, but only include states with five good polls or more.

Instructions

    Use the filter function to filter the data for polls with grades equal to A+, A, A-, or B+.
    Group the filtered data by state using group_by.
    Use the filter function to filter the data for states with at least 5 polls.
    Use the reorder function to order the state data by error.
    Using ggplot, set the aesthetic with state as the x-variable and error as the y-variable.
    Use geom_box to indicate that we want to plot a boxplot.
    Use geom_point to add data points as a layer.

# The `errors` data have already been loaded. Examine them using the `head` function.
head(errors)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
1	New Mexico	2016-11-06	2016-11-06	Zia Poll	NA	0.02	
2	Virginia	2016-11-03	2016-11-04	Public Policy Polling	B+	0.05	
3	Iowa	2016-11-01	2016-11-04	Selzer & Company	A+	-0.07	
4	Wisconsin	2016-10-26	2016-10-31	Marquette University	A	0.06	
5	North Carolina	2016-11-04	2016-11-06	Siena College	A	0.00	
6	Georgia	2016-11-06	2016-11-06	Landmark Communications	B	-0.03	
6 rows | 1-7 of 12 columns

# Create a boxplot showing the errors by state for states with at least 5 polls with grades B+ or higher
errors %>% filter(grade %in% c("A+","A","A-","B+") | is.na(grade)) %>%
  group_by(state) %>%
  filter(n() >= 5) %>%
  ungroup() %>%
  mutate(state = reorder(state, error)) %>%
  ggplot(aes(state, error)) + 
  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  geom_boxplot() + 
  geom_point()

Assessment 6.2: The t-Distribution

    Using the t-Distribution
    We know that, with a normal distribution, only 5% of values are more than 2 standard deviations away from the mean.

Calculate the probability of seeing t-distributed random variables being more than 2 in absolute value when the degrees of freedom are 3.

Instructions

Use the pt function to calculate the probability of seeing a value less than or equal to the argument.

# Calculate the probability of seeing t-distributed random variables being more than 2 in absolute value when 'df = 3'.
1 - pt(2, 3) + pt(-2, 3)

## [1] 0.139326

    Plotting the t-distribution
    Now use sapply to compute the same probability for degrees of freedom from 3 to 50.

Make a plot and notice when this probability converges to the normal distribution’s 5%.

Instructions

    Make a vector called df that contains a sequence of numbers from 3 to 50.
    Using function, make a function called pt_func that recreates the calculation for the probability that a value is greater than 2 as an absolute value for any given degrees of freedom.
    Use sapply to apply the pt_func function across all values contained in df. Call these probabilities probs.
    Use the plot function to plot df on the x-axis and probs on the y-axis.

# Generate a vector 'df' that contains a sequence of numbers from 3 to 50
df <- seq(3,50)

# Make a function called 'pt_func' that calculates the probability that a value is more than |2| for any degrees of freedom 
pt_func <- function(n) {
  1 - pt(2, n) + pt(-2, n)
}

# Generate a vector 'probs' that uses the `pt_func` function to calculate the probabilities
probs <- sapply(df, pt_func)

# Plot 'df' on the x-axis and 'probs' on the y-axis
plot(df, probs)

    Sampling From the Normal Distribution
    In a previous section, we repeatedly took random samples of 50 heights from a distribution of heights. We noticed that about 95% of the samples had confidence intervals spanning the true population mean.

Re-do this Monte Carlo simulation, but now instead of N=50, use N=15. Notice what happens to the proportion of hits.

Instructions

    Use the replicate function to carry out the simulation. Specify the number of times you want the code to run and, within brackets, the three lines of code that should run.
    First use the sample function to randomly sample N values from x.
    Second, create a vector called interval that calculates the 95% confidence interval for the sample. You will use the qnorm function.
    Third, use the between function to determine if the population mean mu is contained between the confidence intervals.
    Save the results of the Monte Carlo function to a vector called res.
    Use the mean function to determine the proportion of hits in res.

# Load the neccessary libraries and data
library(dslabs)
library(dplyr)
data(heights)

# Use the sample code to generate 'x', a vector of male heights
x <- heights %>% filter(sex == "Male") %>%
  .$height

# Create variables for the mean height 'mu', the sample size 'N', and the number of times the simulation should run 'B'
mu <- mean(x)
N <- 15
B <- 10000

# Use the `set.seed` function to make sure your answer matches the expected result after random sampling
set.seed(1)

# Generate a logical vector 'res' that contains the results of the simulations
res <- replicate(B, {
  X <- sample(x, N, replace=TRUE)
  interval <- mean(X) + c(-1,1)*qnorm(0.975)*sd(X)/sqrt(N)
  between(mu, interval[1], interval[2])
})

# Calculate the proportion of times the simulation produced values within the 95% confidence interval. Print this value to the console.
mean(res)

## [1] 0.9331

    Sampling from the t-Distribution
    N=15 is not that big. We know that heights are normally distributed, so the t-distribution should apply. Repeat the previous Monte Carlo simulation using the t-distribution instead of using the normal distribution to construct the confidence intervals.

What are the proportion of 95% confidence intervals that span the actual mean height now?

Instructions

    Use the replicate function to carry out the simulation. Specify the number of times you want the code to run and, within brackets, the three lines of code that should run.
    First use the sample function to randomly sample N values from x.
    Second, create a vector called interval that calculates the 95% confidence interval for the sample. Remember to use the qt function this time to generate the confidence interval.
    Third, use the between function to determine if the population mean mu is contained between the confidence intervals.
    Save the results of the Monte Carlo function to a vector called res.
    Use the mean function to determine the proportion of hits in res.

# The vector of filtered heights 'x' has already been loaded for you. Calculate the mean.
mu <- mean(x)

# Use the same sampling parameters as in the previous exercise.
set.seed(1)
N <- 15
B <- 10000

# Generate a logical vector 'res' that contains the results of the simulations using the t-distribution
res <- replicate(B, {
  s <- sample(x, N, replace = TRUE)
  interval <- c(mean(s) - qt(0.975, N - 1) * sd(s) / sqrt(N), mean(s) + qt(0.975, N - 1) * sd(s) / sqrt(N))
  between(mu, interval[1], interval[2])
})

# Calculate the proportion of times the simulation produced values within the 95% confidence interval. Print this value to the console.
mean(res)

## [1] 0.9512

    Why the t-Distribution?
    Why did the t-distribution confidence intervals work so much better?

Possible Answers

A. The t-distribution takes the variability into account and generates larger confidence intervals. B. Because the t-distribution shifts the intervals in the direction towards the actual mean. C. This was just a chance occurrence. If we run it again, the CLT will work better. D. The t-distribution is always a better approximation than the normal distribution.
Section 7 Overview

In Section 7, you will learn how to use association and chi-squared tests to perform inference for binary, categorical, and ordinal data through an example looking at research funding rates.

After completing Section 7, you will be able to:

    Use association and chi-squared tests to perform inference on binary, categorical, and ordinal data.
    Calculate an odds ratio to get an idea of the magnitude of an observed effect.

The textbook for this section is available here
Assessment 7.1: Association and Chi-Squared Tests

    Comparing Proportions of Hits
    In a previous exercise, we determined whether or not each poll predicted the correct winner for their state in the 2016 U.S. presidential election. Each poll was also assigned a grade by the poll aggregator. Now we’re going to determine if polls rated A- made better predictions than polls rated C-.

In this exercise, filter the errors data for just polls with grades A- and C-. Calculate the proportion of times each grade of poll predicted the correct winner.

Instructions

    Filter errors for grades A- and C-.
    Group the data by grade and hit.
    Summarize the number of hits for each grade.
    Generate a two-by-two table containing the number of hits and misses for each grade.
    Calculate the proportion of times each grade was correct.

library(tidyr)
# The 'errors' data have already been loaded. Examine them using the `head` function.
head(errors)

 
 
	
state
<chr>
	
startdate
<date>
	
enddate
<date>
	
pollster
<fctr>
	
grade
<fctr>
	
spread
<dbl>
	
1	New Mexico	2016-11-06	2016-11-06	Zia Poll	NA	0.02	
2	Virginia	2016-11-03	2016-11-04	Public Policy Polling	B+	0.05	
3	Iowa	2016-11-01	2016-11-04	Selzer & Company	A+	-0.07	
4	Wisconsin	2016-10-26	2016-10-31	Marquette University	A	0.06	
5	North Carolina	2016-11-04	2016-11-06	Siena College	A	0.00	
6	Georgia	2016-11-06	2016-11-06	Landmark Communications	B	-0.03	
6 rows | 1-7 of 12 columns

# Generate an object called 'totals' that contains the numbers of good and bad predictions for polls rated A- and C-
totals <- errors %>%
  filter(grade %in% c("A-", "C-")) %>%
  group_by(grade,hit) %>%
  summarize(num = n()) %>%
  spread(grade, num)

# Print the proportion of hits for grade A- polls to the console
totals[[2,3]]/sum(totals[[3]])

## [1] 0.8030303

# Print the proportion of hits for grade C- polls to the console
totals[[2,2]]/sum(totals[[2]])

## [1] 0.8614958

    Chi-squared Test
    We found that the A- polls predicted the correct winner about 86% of the time in their states and C- polls predicted the correct winner about 80% of the time.

Use a chi-squared test to determine if these proportions are different.

Instructions

    Use the chisq.test function to perform the chi-squared test. Save the results to an object called chisq_test.
    Print the p-value of the test to the console.

# The 'totals' data have already been loaded. Examine them using the `head` function.
head(totals)

hit
<lgl>
	
C-
<int>
	
A-
<int>
FALSE	50	26
TRUE	311	106
2 rows

# Perform a chi-squared test on the hit data. Save the results as an object called 'chisq_test'.
chisq_test <- totals %>% 
  select(-hit) %>%
  chisq.test()
chisq_test

## 
##  Pearson's Chi-squared test with Yates' continuity correction
## 
## data:  .
## X-squared = 2.1053, df = 1, p-value = 0.1468

# Print the p-value of the chi-squared test to the console
chisq_test$p.value

## [1] 0.1467902

    Odds Ratio Calculation
    It doesn’t look like the grade A- polls performed significantly differently than the grade C- polls in their states.

Calculate the odds ratio to determine the magnitude of the difference in performance between these two grades of polls.

Instructions

    Calculate the odds that a grade C- poll predicts the correct winner. Save this result to a variable called odds_C.
    Calculate the odds that a grade A- poll predicts the correct winner. Save this result to a variable called odds_A. -Calculate the odds ratio that tells us how many times larger the odds of a grade A- poll is at predicting the winner than a grade C- poll.

# The 'totals' data have already been loaded. Examine them using the `head` function.
head(totals)

hit
<lgl>
	
C-
<int>
	
A-
<int>
FALSE	50	26
TRUE	311	106
2 rows

# Generate a variable called `odds_C` that contains the odds of getting the prediction right for grade C- polls
odds_C <- (totals[[2,2]] / sum(totals[[2]])) / 
  (totals[[1,2]] / sum(totals[[2]]))

# Generate a variable called `odds_A` that contains the odds of getting the prediction right for grade A- polls
odds_A <- (totals[[2,3]] / sum(totals[[3]])) / 
  (totals[[1,3]] / sum(totals[[3]]))

# Calculate the odds ratio to determine how many times larger the odds ratio is for grade A- polls than grade C- polls
odds_A/odds_C

## [1] 0.6554539

    Significance
    We did not find meaningful differences between the poll results from grade A- and grade C- polls in this subset of the data, which only contains polls for about a week before the election. Imagine we expanded our analysis to include all election polls and we repeat our analysis. In this hypothetical scenario, we get that the p-value for the difference in prediction success if 0.0015 and the odds ratio describing the effect size of the performance of grade A- over grade B- polls is 1.07.

Based on what we learned in the last section, which statement reflects the best interpretation of this result?

Possible Answers

A. The p-value is below 0.05, so there is a significant difference. Grade A- polls are significantly better at predicting winners.
B. The p-value is too close to 0.05 to call this a significant difference. We do not observe a difference in performance.
C. The p-value is below 0.05, but the odds ratio is very close to 1. There is not a scientifically significant difference in performance.
D. The p-value is below 0.05 and the odds ratio indicates that grade A- polls perform significantly better than grade C- polls.
