Activity Ten - Lab10
================
Taehoon Ha
11/13/2018

-   [Question 1](#question-1)
-   [Question 2](#question-2)
-   [Question 3](#question-3)
-   [Question 4](#question-4)

### Question 1

Generate Generate 1000 uniform pseudorandom variates using the `runif()` function. + compute average and variance + compare your results with true mean and variance

``` r
set.seed(1)
dat <- runif(1000)
mean(dat)
```

    ## [1] 0.4996917

``` r
var(dat)
```

    ## [1] 0.08316708

### Question 2

Use the `round()` function together with `runif()` to generate 1000 pseudo-random integers which take values from 1 through 10. Use the `table()` function to check whether the observed frequencies for each value are close to what you expect.

``` r
set.seed(1)
dat2 <- runif(1000, min = 0.5, max = 10.5) %>% round
table(dat2)
```

    ## dat2
    ##   1   2   3   4   5   6   7   8   9  10 
    ##  96 104  93 112 115  86  90 106  88 110

<br>

### Question 3

Use sample() function to generate 1000 pseudo-random integers which take values from 1 through 10. Use the `table()` function to check whether the observed frequencies for each value are close to what you expect.

``` r
set.seed(1)
dat3 <- sample(1:10, 1000, replace = T)
table(dat3)
```

    ## dat3
    ##   1   2   3   4   5   6   7   8   9  10 
    ##  96 104  93 112 115  86  90 106  88 110

<br>

### Question 4

Simulate 10000 binomial pseudo-random numbers with parameters 10 and 0.4. Let X be a Binomial(10, 0.4) random variable. Use the simulated numbers to estimate the following quantities:

-   Pr(*X* ≤ 3)
-   Pr(*X* = 3)

``` r
x <- rbinom(1000000, 10, 0.4)
table(x)
```

    ## x
    ##      0      1      2      3      4      5      6      7      8      9 
    ##   5989  40645 120754 214801 250862 200758 111838  42152  10596   1502 
    ##     10 
    ##    103

``` r
length(x[x<=3]) / length(x)
```

    ## [1] 0.382189

``` r
length(x[x==3]) / length(x) 
```

    ## [1] 0.214801

``` r
pbinom(3, 10, 0.4) %>% round(3)
```

    ## [1] 0.382

``` r
dbinom(3, 10, 0.4) %>% round(3)
```

    ## [1] 0.215

``` r
table(x)
```

    ## x
    ##      0      1      2      3      4      5      6      7      8      9 
    ##   5989  40645 120754 214801 250862 200758 111838  42152  10596   1502 
    ##     10 
    ##    103
