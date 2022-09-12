Homework 2
================
Beatrice Caiado

## Homework 2

``` r
library(tidyverse)
a <- 2 
b <- 4 
a > b 
```

    [1] FALSE

``` r
ls() 
```

    [1] "a" "b"

``` r
rm(list=ls()) 
ls()
```

    character(0)

## Question 4: Why does rm(list=ls()) work?

- **(rm)** will remove the objects from the specified environment
- **list** is the argument in the rm function that provides the specific
  location where the objects are that are to be removed
- **ls()** is a function that will list the objects that are in the
  environment that we want to be removed
- in the end, our global environment will be empty.

## Search Function

We can use this to search a number of different options and packages
that are in base R.

``` r
search()
```

     [1] ".GlobalEnv"        "package:forcats"   "package:stringr"  
     [4] "package:dplyr"     "package:purrr"     "package:readr"    
     [7] "package:tidyr"     "package:tibble"    "package:ggplot2"  
    [10] "package:tidyverse" "tools:quarto"      "package:stats"    
    [13] "package:graphics"  "package:grDevices" "package:utils"    
    [16] "package:datasets"  "package:methods"   "Autoloads"        
    [19] "package:base"     
