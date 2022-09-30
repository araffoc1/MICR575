Hmk_05
================
Beatrice

Please read the entire [R for Data
Science](https://r4ds.had.co.nz/transform.html) before you do this
homework.

This homework relies on the `nycflights13` package, which contains
several data frames, including `airlines`, `airports`, `flights`,
`planes`, and `weather`. Loading `nycflights13` puts all of these data
frames on the search path, so that they are available automatically,
just like `mpg` or `mtcars`.

## Installing data packages

Remember that any package needs to be installed only once (per version
of R), but needs to be loaded every time we start a new R session.

To install `nyclflights13`, we use `install.packages("nycflights13")`
(with quotation marks). To load it, we use `library(nycflights13)`.

- **I will first install the package and then load it. Then I will
  glimpse into it**

``` r
library(nycflights13)
```

``` r
library(tidyverse)
glimpse(flights)
```

    Rows: 336,776
    Columns: 19
    $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2…
    $ month          <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
    $ day            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
    $ dep_time       <int> 517, 533, 542, 544, 554, 554, 555, 557, 557, 558, 558, …
    $ sched_dep_time <int> 515, 529, 540, 545, 600, 558, 600, 600, 600, 600, 600, …
    $ dep_delay      <dbl> 2, 4, 2, -1, -6, -4, -5, -3, -3, -2, -2, -2, -2, -2, -1…
    $ arr_time       <int> 830, 850, 923, 1004, 812, 740, 913, 709, 838, 753, 849,…
    $ sched_arr_time <int> 819, 830, 850, 1022, 837, 728, 854, 723, 846, 745, 851,…
    $ arr_delay      <dbl> 11, 20, 33, -18, -25, 12, 19, -14, -8, 8, -2, -3, 7, -1…
    $ carrier        <chr> "UA", "UA", "AA", "B6", "DL", "UA", "B6", "EV", "B6", "…
    $ flight         <int> 1545, 1714, 1141, 725, 461, 1696, 507, 5708, 79, 301, 4…
    $ tailnum        <chr> "N14228", "N24211", "N619AA", "N804JB", "N668DN", "N394…
    $ origin         <chr> "EWR", "LGA", "JFK", "JFK", "LGA", "EWR", "EWR", "LGA",…
    $ dest           <chr> "IAH", "IAH", "MIA", "BQN", "ATL", "ORD", "FLL", "IAD",…
    $ air_time       <dbl> 227, 227, 160, 183, 116, 150, 158, 53, 140, 138, 149, 1…
    $ distance       <dbl> 1400, 1416, 1089, 1576, 762, 719, 1065, 229, 944, 733, …
    $ hour           <dbl> 5, 5, 5, 5, 6, 5, 6, 6, 6, 6, 6, 6, 6, 6, 6, 5, 6, 6, 6…
    $ minute         <dbl> 15, 29, 40, 45, 0, 58, 0, 0, 0, 0, 0, 0, 0, 0, 0, 59, 0…
    $ time_hour      <dttm> 2013-01-01 05:00:00, 2013-01-01 05:00:00, 2013-01-01 0…

# Question 1: filtering

Make a plot of air time as a function of distance for all flights that
meet the following criteria:

- originate from LaGuardia airport (“LGA”)

- departed on the 16th of the month

- have a flight distance of less than 2000

- **I am first going to assign all these filters to a specific object.
  They will all be combined into a single object.**

``` r
total <- filter(flights, origin == "LGA", day == 16, distance < 2000)
```

- **Now I will make the plot as with the criteria stated above**

``` r
ggplot(total, aes(x=distance, y=air_time)) +
  geom_point()
```

    Warning: Removed 75 rows containing missing values (geom_point).

![](hmk_05_files/figure-gfm/unnamed-chunk-4-1.png)

# Question 2: dealing with NAs

Make a data frame of all of the rows of `flights` that have values for
*both* `arr_time` and `dep_time` - that is, neither of those values are
`NA`.

``` r
ques_2 <- filter(flights, arr_time > 0, dep_time > 0)
```

## filtering NAs

`ggplot()` will automatically remove NA values from the plot, as you may
have seen in question 1, but it emits a warning message about that. Of
course you could silence the warning message using [chunk
options](https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html),
but how could you prevent them from appearing in the first place?

- **If you use drop_na(), it should get rid of all the NAs in your data
  frame.**

# Question 3: adding columns

Create a data frame of average flight speeds, based on `air_time` and
`distance`. Make either a histogram or a density plot of the data. If
you like, you may break the data out (e.g. by airline, or some other
variable) in a way that you think makes sense.

``` r
ques_3 <- mutate(flights, speed = distance/air_time)

ggplot(ques_3, aes(x=speed)) +
  geom_histogram(color="hotpink")
```

    Warning: Removed 9430 rows containing non-finite values (stat_bin).

![](hmk_05_files/figure-gfm/unnamed-chunk-6-1.png)
