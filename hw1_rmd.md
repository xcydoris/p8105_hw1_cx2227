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
```
