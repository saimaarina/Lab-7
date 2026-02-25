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
df <- read_csv("kansas_grouped_rolling_avg.csv")
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
View(df)
```

### Exercise 2

``` r
df %>% 
  mutate(mask_group = if_else(mask_mandate == "Mask",
                              "Mask mandate counties",
                              "No mask mandate counties")) %>% 
  ggplot(aes(x = date,
             y = rolling_avg,
             color = mask_group,
             group = mask_group)) +
  geom_line(size = 1.1) +
  scale_color_manual(values = c("Mask mandate counties" = "red",
                                "No mask mandate counties" = "blue"),
                     name = "County type") +
  labs(
    x = "Date",
    y = "7-day rolling average of new cases\n(per 100,000 residents)",
    title = "COVID-19 case trends in Kansas counties\nwith vs. without mask mandates",
  ) +
  theme_minimal(base_size = 12) +
  theme(
    legend.position = "top",
    panel.grid.minor = element_blank()
  )
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once per session.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

![](lab-07_files/figure-gfm/-%20enhanced%20and%20corrected%20visual-1.png)<!-- -->

Looking at the data now that it is visually represented better, I can
see how even my initial assumptions were wrong after I thought I looked
closer, but it wasn’t close enough! It just makes no sense why the plot
would be made the way it did when it could be made so much simpler, that
is so frustrating!

### Exercise 3

In my visualization, it is way more clear that there were not really any
differences in the number of cases that were notable in the no
mask-mandate counties, while the decrease in cases for the mask-mandate
counties are much clearer, showcasing their effect more strongly than in
the original visual representation.

### Exercise 4

My new plot can honestly say that mask-mandate counties start and they
stay at a slightly higher rolling average than the no-mandate counties,
with no obvious patterns between them. WIth the new plot that has a
shared y-axis, the main thing we can infer is difference in level (mask
counties had more cases at baseline) and modest changes in trends. In
relation to mask-wearing, this data doesn’t act as a clear demonstrator
in support of mask mandates or not, but rather as information that can
help support making these decisions (like how a mask mandate can help
decrease virus spread, even if not strong). Something I know of mask
mandates is that bigger areas and cities had them in effect because they
started with a greater baseline of cases, unlike smaller counties with
no mask-mandate in place, who started with a smaller amount of cases
(due to confounding factors like smaller populations).

### Exercise 5

My accurate visualization suggests that mask‑mandate counties
consistently had higher COVID‑19 case rates than no‑mandate counties
over this time period, and that both groups show only modest decreases
rather than dramatic divergence. In terms of the variables I used, I
plotted date on the x‑axis and rolling_avg on the y‑axis, encoding
mask_mandate as a color grouping (mask vs. no mask counties). For my
scale, both county types share the same y‑axis range, so viewers can
directly compare the height and slope of the two lines without being
misled by different scales. Choosing to do a line chart helps emphasize
how the case rates change over time and how the two groups change in
relation to each other.
