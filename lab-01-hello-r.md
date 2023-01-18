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

And here’s the code I used (was given) to find the correlation

``` r
dino_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0645

### Exercise 3

Below we have the code that allows us to plot the star data

First, we create a dataset with just the star data

Then, we plot that data using the same code we used for the dino data

``` r
star_data <- datasaurus_dozen %>%
  filter(dataset == "star")

ggplot(star_data, aes(x = x, y = y)) + 
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-star-1.png)<!-- -->

The same code from Ex. 2 also lets us find the correlation between “x”
and “y”

``` r
star_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0630

So we can see that the correlation comes out to -0.0630. That’s almost
exactly the same as in the dino data!

### Exercise 4

Following the example of the last few sections, we can find the
correlation between “x” and “y” in the circle data

``` r
circle_data <- datasaurus_dozen %>%
  filter(dataset == "circle")

circle_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0683

And plot it

``` r
ggplot(circle_data, aes(x = x, y = y)) +
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-circle-1.png)<!-- --> So one
again, even though the shape of the data is very different from Ex. 2 &
3, the correlation is almost exactly the same.

### Exercise 5

The code below lets us visualize all of the datasets at once

``` r
ggplot(datasaurus_dozen, aes(x = x, y = y, color = dataset))+
  geom_point()+
  facet_wrap(~ dataset, ncol = 3) +
  theme(legend.position = "none")
```

![](lab-01-hello-r_files/figure-gfm/all-plots-1.png)<!-- -->

They look really different! However, we can see below that, in spite of
that, the correlation between “x” and “y” across the datasets doesn’t
vary much

``` r
all_correlations <- datasaurus_dozen %>%
  group_by(dataset) %>%
  summarize(r = cor(x, y))
all_correlations
```

    ## # A tibble: 13 × 2
    ##    dataset          r
    ##    <chr>        <dbl>
    ##  1 away       -0.0641
    ##  2 bullseye   -0.0686
    ##  3 circle     -0.0683
    ##  4 dino       -0.0645
    ##  5 dots       -0.0603
    ##  6 h_lines    -0.0617
    ##  7 high_lines -0.0685
    ##  8 slant_down -0.0690
    ##  9 slant_up   -0.0686
    ## 10 star       -0.0630
    ## 11 v_lines    -0.0694
    ## 12 wide_lines -0.0666
    ## 13 x_shape    -0.0656
