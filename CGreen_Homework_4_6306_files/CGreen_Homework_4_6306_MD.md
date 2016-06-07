Illustrating the Central Limit Theorem
======================================

-   The purpose of this assignment is to illustrate the central limit
    theorem in R Markdown by looking at the distribution of two
    different sample sizes for both a normal distribution and an
    exponential distribution.

### Part 1

In the first portion we are using normal distribution of means to depict
the CLT. We use both a small sample size and a larger sample size.
According to the CLT, as the sample size increases the distrubtion will
approach normality.

Define initial variables

    R1 <- 1000 #sample size
    R1_mean <- numeric(R1) #empty vector of sample size
    Firstnormal <- rnorm(1000, 500, 250) #normal distribution sample
    sample1 <- numeric() #empty vector
    R1m <- mean(Firstnormal) #mean of normal sample

    for(i in 1:1000 ){ #bootstrapping for loop to sample means 100 times
    sample1 <- sample(Firstnormal, 1:100, replace = FALSE)
    R1_mean[i] <- mean(sample1)}# appending them to the empty vector

    hist(R1_mean, main = "Smaller Sample Size normal dist")#histogram of data
    summary(R1_mean)#summary of data to compare 

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  -253.2   347.7   492.3   502.5   682.9  1339.0

    abline(v=R1m, col= "red",lwd=2)#mean of normal sample to histogram mean
    abline(v=mean(R1_mean), col= "blue",lwd=2)#mean of sample means compared to normal sample mean
    abline(v=500, col= "green",lwd=2, lty=3)#calculated mean from oroginal sample

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-3-1.png)<!-- -->

#### Figure 1:

-   The histogram for the sampler sample size. The histogram is very
    close to bieng a normal distribution but it is not quite there yet.
    This can be seen by comparing the means of the known normal
    distribution and the mean of the sample.

#### Larger sample size

This next portion uses basically the sample code but increases the
sample size. In thoery the output should look a lot more like a normal
distribution.

    R2 <- 10000#creating another sample size
    R2_mean <- numeric(R1)#empty vector
    Secondnormal <- rnorm(100000, 1000, 250)#again created a normal selection of random variables with sample size, mean, and std
    sample1 <- numeric()#another empty vector
    R2m <- mean(Secondnormal)#taking the mean of the random sample

Bootstap a data set with a larger sample size:

    for(i in 1:10000 ){
    sample1 <- sample(Secondnormal, 1:1000, replace = FALSE)
    R2_mean[i] <- mean(sample1)}#for loop that bootstraps the data so we can apply the sample mean function multiple times

    hist(R2_mean, main = "Larger Sample Size Normal Distribution")
    summary(R2_mean)#shows summary of the data set

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   100.3   833.9   994.9   999.2  1171.0  2033.0

    abline(v=R2m, col= "red",lwd=2)#mean of normal sample to histogram mean
    abline(v=mean(R2_mean), col= "blue",lwd=2)#shows mean of the sample dataset 
    abline(v=1000, col= "green",lwd=2, lty=3)#shows estimated mean

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-6-1.png)<!-- -->

#### Figure 2:

-   This second histogram as you can see follows the rules of normality
    much closer. The mean of the orginal distribution is much closer to
    the mean of the final sample. It is also closer to the assigned
    distribution of 500

##### Boxplot for mean data

    boxplot(R2_mean)#made a boxplot for the sample data

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-7-1.png)<!-- -->

#### Figure 3:

-   Another way to observe the data is by using a boxplot. A boxplot for
    a normal distribution is supposed to be evenly distrubuted over
    the mean.

Part 2
------

Using an exponential distribution we again chose a small sample size and
observe the sample distribution.

    R3<-20
    R4<-1000#assigning basic variables
    R3_mean <- numeric(R3)#empty vectors
    R4_mean <- numeric(R4)
    First_Exp <- rexp(100,1)
    Second_Exp <-rexp(10000,.1)

Here again we run almost the same bootstrapping code but instead of
rnorm we are using rexp, which creates a sample from an exponential
distribution

    for(i in 1:20 ){
    sample1 <- sample(First_Exp,1:20, replace = FALSE)
    R3_mean[i] <- mean(sample1)}

    summary(R3_mean)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ## 0.01038 0.18570 0.52690 0.66920 0.77450 2.15700

    hist(R3_mean, main = "Smaller Sample Size Exponential Distribution")

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-10-1.png)<!-- -->

#### Figure 4:

-   This is the distribution of the samples selected in a smaller
    data set. The distribution does not appear to be
    completely exponential.

<!-- -->

    for(i in 1:1000 ){
    sample1 <- sample(Second_Exp,1:1000, replace = FALSE)
    R4_mean[i] <- mean(sample1)}

    summary(R4_mean)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  0.0059  2.8880  7.3360 10.3200 13.7500 74.3900

    hist(R4_mean, main = "Larger Sample Size Exponential Distribution")

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-12-1.png)<!-- -->

#### Figure 5:

-   This distribution looks a lot more closer to the what an exponential
    distribution should look like. Normally they contain a lot of data
    points closer to zero.

##### Boxplot for mean data

    boxplot(R4_mean)#made a boxplot for the sample data

![](https://github.com/cliffordgreen/CGreen_Homework_4_6306/blob/master/CGreen_Homework_4_6306_files/figure-markdown_strict/unnamed-chunk-13-1.png)<!-- -->

#### Figure 6:

-   Again we will check the distribution by looking at the same sample
    using a boxplot. For an exponential distribution you will expect the
    boxplot to be heavily distributed to one side. Just like the box
    plot that we see below.
