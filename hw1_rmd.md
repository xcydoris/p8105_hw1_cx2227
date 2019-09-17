p8105\_hw1\_cx2227
================
9/17/2019

``` r
p1_df = tibble(
  norm_samp = rnorm(8),
  norm_samp_pos = norm_samp > 0,
  vec_char = c ("1", "2", "3", "4", "5", "6", "7", "8"),
  vec_factor = factor(c("A", "A", "A", "B", "B", "B", "C", "C"))
)

mean(pull(p1_df, norm_samp))
```

    ## [1] 0.1587036

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
“vec\_char” and “vec\_factor”.
