p8105\_hw1\_cx2227
================
Chuyue Xiang
2019-09-17

# Problem 1

``` r
p1_df = tibble(
  norm_samp = rnorm(8),
  norm_samp_pos = norm_samp > 0,
  vec_char = c ("1", "2", "3", "4", "5", "6", "7", "8"),
  vec_factor = factor(c("A", "A", "A", "B", "B", "B", "C", "C"))
)

mean(pull(p1_df, norm_samp))
```

    ## [1] 0.6882971

``` r
mean(pull(p1_df, norm_samp_pos))
```

    ## [1] 0.625

``` r
mean(pull(p1_df, vec_char))
```

    ## Warning in mean.default(pull(p1_df, vec_char)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(p1_df, vec_factor))
```

    ## Warning in mean.default(pull(p1_df, vec_factor)): argument is not numeric
    ## or logical: returning NA

    ## [1] NA

It only worked when taking the mean of “norm\_samp” and
“norm\_samp\_pos” and did not work when taking the mean of
“vec\_char” and
“vec\_factor”.

## Converting variables from one type to another

``` r
### convert the logical vector to numeric, and multiply the random sample by the result
as.numeric(pull(p1_df, norm_samp_pos)) * pull(p1_df, norm_samp)
```

    ## [1] 2.9134452 0.0000000 0.8361247 0.0000000 0.9774486 0.0000000 0.1667729
    ## [8] 2.0311971

``` r
### convert the logical vector to a factor, and multiply the random sample by the result
as.factor(pull(p1_df, norm_samp_pos)) * pull(p1_df, norm_samp)
```

    ## [1] NA NA NA NA NA NA NA NA

``` r
### convert the logical vector to a factor and then convert the result to numeric, and multiply the random sample by the result
as.numeric(as.factor(pull(p1_df, norm_samp_pos))) * pull(p1_df, norm_samp)
```

    ## [1]  5.8268904 -0.0930207  1.6722493 -0.4622822  1.9548973 -0.8633091
    ## [7]  0.3335458  4.0623942

# Problem 2

``` r
p2_df = tibble(
  x = rnorm(500),
  y = rnorm(500),
  norm_samp_pos1 = x + y > 1,
  num_vec = as.numeric (norm_samp_pos1),
  fac_vec = as.factor (norm_samp_pos1)
)
```
