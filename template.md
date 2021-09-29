Homework 1
================
Jinghan Liu
2021.9.29

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.4     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   2.0.1     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(palmerpenguins)
library(ggplot2)
```

**Problem 1**

``` r
weight_changes_df = 
  tibble( 
  vec_weightchanges = rnorm(10) , 
  vec_logical = vec_weightchanges > 0 ,
  vec_char = LETTERS [1:10] ,
  vec_factor = factor(c("A","B","C","C","B","A","A","B","C","C"))
)
```

``` r
mean(pull(weight_changes_df,vec_weightchanges))
```

    ## [1] -0.2878485

``` r
mean(pull(weight_changes_df,vec_logical))
```

    ## [1] 0.5

``` r
mean(pull(weight_changes_df,vec_char))
```

    ## Warning in mean.default(pull(weight_changes_df, vec_char)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

``` r
mean(pull(weight_changes_df,vec_factor))
```

    ## Warning in mean.default(pull(weight_changes_df, vec_factor)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

``` r
logic_to_numeric = as.numeric(pull(weight_changes_df,vec_logical))
factor_to_numeric = as.numeric(pull(weight_changes_df,vec_factor))
char_to_numeric = as.numeric(pull(weight_changes_df,vec_char))
```

    ## Warning: NAs introduced by coercion

\#fator vector and logic vector can numeric, but charactor vector cannot
be numeric.

**Problem 2**

``` r
data("penguins", package = "palmerpenguins")
name = colnames(penguins)
n_row = nrow(penguins)
n_col = ncol(penguins)
mean_flipper = mean(pull(penguins,var=flipper_length_mm),na.rm = TRUE)
```

the important variables are species, island, bill\_length\_mm,
bill\_depth\_mm, flipper\_length\_mm, body\_mass\_g, sex, year the
dataset test 344 rows and 8 columns the mean flipper length is
200.9152047

``` r
ggplot(penguins, aes(x = bill_length_mm, y = flipper_length_mm)) + geom_point(aes(color = species))
```

![](template_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
ggsave("penguins_plot.pdf",height = 6,width = 6)
```
