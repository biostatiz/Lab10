Assignment Ten - Lab10
================
Taehoon Ha
11/22/2018

-   [Question 1](#question-1)
-   [Question 2](#question-2)

### Question 1

Write a function that calculates cumulative distribution function of a binomial random variable. Compare results from your function with `pbinom()` function.

``` r
q1 <- function(q, n, p) {
    prob_sum <- 0
    for (i in 0: q) {
        prob <- choose(n, i) * p^i * (1-p)^(n-i)
        prob_sum <- prob_sum + prob
    }
    prob_sum
}

# compare results from my function with pbinom()
q1(1, 10, 0.5) %>% round(4) == pbinom(1, 10, 0.5) %>% round(4)
```

    ## [1] TRUE

### Question 2

Write a function that runs simulations to obtain power from a one-sample t-test. Run your function (with number of simulations = 10,000 ) with *n*=30, delta=0.5, sd=1 and sig.level=0.05. Compare your results with `power.t.test(n = 30, delta = 0.5, sd = 1, sig.level = 0.05, type = 'one.sample')`.

``` r
q2 <- function(n, delta, sd, sig.level) {
    B <- 10000
    power <- replicate(B, {
        smpl <- rnorm(n, delta, sd)
        ttest <- as.numeric(t.test(smpl)$p.value < sig.level)
    })
    power_sum <- sum(power) / B
    list(n = n, delta = delta, sd = sd, sig.level = sig.level, 
        power = power_sum, method = "One-sample t test power calculation")
}

# Compare your results with power.t.test()
q2(n = 30, delta = 0.5, sd = 1, sig.level = 0.05)$power %>% round(4)
```

    ## [1] 0.7541

``` r
power.t.test(n = 30, delta = 0.5, sd = 1, sig.level = 0.05, type = 'one.sample')$power %>% round(4)
```

    ## [1] 0.754
