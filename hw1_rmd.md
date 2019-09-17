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

    ## [1] -0.4827447

``` r
mean(pull(p1_df, norm_samp_pos))
```

    ## [1] 0.125

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

    ## [1] 0.0000000 0.0000000 0.0000000 0.0000000 0.0000000 0.0000000 0.0000000
    ## [8] 0.7076808

``` r
### convert the logical vector to a factor, and multiply the random sample by the result
as.factor(pull(p1_df, norm_samp_pos)) * pull(p1_df, norm_samp)
```

    ## [1] NA NA NA NA NA NA NA NA

``` r
### convert the logical vector to a factor and then convert the result to numeric, and multiply the random sample by the result
as.numeric(as.factor(pull(p1_df, norm_samp_pos))) * pull(p1_df, norm_samp)
```

    ## [1] -0.88296677 -1.29096260 -0.03667512 -0.22762818 -0.68163273 -0.48549384
    ## [7] -0.96427944  1.41536156

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

## Short Description

  - the number of row in `p2_df` is 500 ;
  - the number of column in `p2_df` is 5 ;
  - the mean of x is -0.0067019 ;
  - the median of x is -0.0916441 ;
  - the standard deviation of x is 1.0583745 ;
  - the proportion of cases for which x + y \> 1 is 0.256

## Scatterplot

``` r
# Scatterplot for logical vector
ggplot(p2_df, aes( x = x, y = y, color = norm_samp_pos1)) + geom_point()
```

![](hw1_rmd_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
# Scatterplot for numeric vector
ggplot(p2_df, aes( x = x, y = y, color = num_vec)) + geom_point()
```

![](hw1_rmd_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->

``` r
# Scatterplot for factor vector
ggplot(p2_df, aes( x = x, y = y, color = fac_vec)) + geom_point()
```

![](hw1_rmd_files/figure-gfm/unnamed-chunk-2-3.png)<!-- -->

### Comments

  - The first and third scatterplot have two colors: the red represents
    False and the blue represents True.
  - The second scatterplot has a numbered blue bar representing from
    0.00 to 1.00, with darker blue dots gathered in the lower left
    corner and lighter blue gathered in the upper right
corner.

<!-- end list -->

``` r
ggsave("Problem2_1stplot.pdf", plot = ggplot(p2_df, aes( x = x, y = y, color = norm_samp_pos1)) + geom_point())
```

    ## Saving 7 x 5 in image
