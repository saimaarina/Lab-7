Lab 07 - Conveying the right message through visualisation
================
Saima Arina
02/24/2026

### Load packages and data

``` r
library(tidyverse) 
```

Looking at the visualization, I can see how misleading it is. First of
all, the y-axes for both sides are on a different scale (the mask side
goes from 15-25 while the no mask side goes from 14-4, and this is
extremely confusing). Because of that, it is easy to think before
actually diving deeper that mask-mandate counties may have shown a
decrease in cases, but no mask-mandate counties did not seem to change
(which can insinuate that not wearing a mask does not have
consequences). If you actually look closer, you can see that there
actually is a decrease in cases for the no mask-mandate counties. Also,
this could all be avoided if the visualization was made with standards
kept in mind, like the scale to be the same for both variables and a
proper color legend to better discriminate between the two.

### Exercise 1

``` r
library(readr)
kansas_grouped_rolling_avg <- read_csv("kansas_grouped_rolling_avg.csv")
```

    ## Rows: 46 Columns: 3
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (1): mask_mandate
    ## dbl  (1): rolling_avg
    ## date (1): date
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(kansas_grouped_rolling_avg)
```

### Exercise 2

…

Add exercise headings as needed.
