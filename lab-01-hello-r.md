Lab 01 - Hello R
================
Lindsey Wilson
1/17/23

## Load packages and data

``` r
library(tidyverse) 
library(datasauRus)
```

## Exercises

### Exercise 1

According to the help file, the dataset has 1846 rows and 3 variables
(“dataset”, “x”, and “y”)

    ?datasaurus_dozen

### Exercise 2

The correlation between “x” and “y” in the dino_data dataset is -0.0645.

And here’s what the data look like plotted:

``` r
dino_data <- datasaurus_dozen %>%
  filter(dataset == "dino")

ggplot(data = dino_data, mapping = aes(x = x, y = y)) +
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-dino-1.png)<!-- -->

And here’s the code I used (was given) to find the correlation!

``` r
dino_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0645

### Exercise 3

Add code and narrative as needed. Note that the R chunks are labeled
with `plot-star` and `cor-star` to provide spaces to place the code for
plotting and calculating the correlation coefficient. To finish, clean
up the narrative by removing these instructions.

I’m some filler text, you should replace me with more meaningful text…

### Exercise 4

Add code and narrative as needed. Note that two R chunks are given but
they are not labeled. Use the convention from above to name them
appropriately.

### Exercise 5

Add code and narrative as needed.

To add R chunks either type out the backticks, curly braces, and the
letter `r` or use the Insert chunk button above, green C+.
