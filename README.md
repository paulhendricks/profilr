<!-- README.md is generated from README.Rmd. Please edit that file -->
profilr
=======

[![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/profilr)](http://cran.r-project.org/package=profilr) [![Downloads from the RStudio CRAN mirror](http://cranlogs.r-pkg.org/badges/profilr)](http://cran.rstudio.com/package=profilr) [![Build Status](https://travis-ci.org/paulhendricks/profilr.png?branch=master)](https://travis-ci.org/paulhendricks/profilr) [![Build status](https://ci.appveyor.com/api/projects/status/pcsh36eeajvevjbg/branch/master?svg=true)](https://ci.appveyor.com/project/paulhendricks/profilr/branch/master) [![codecov.io](http://codecov.io/github/paulhendricks/profilr/coverage.svg?branch=master)](http://codecov.io/github/paulhendricks/profilr?branch=master) [![Project Status: Active - The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/0.1.0/active.svg)](http://www.repostatus.org/#active)

`profilr` quickly and easily profiles data using common descriptive statistics.

Installation
------------

You can install:

-   the latest released version from CRAN with

    [![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/profilr)](http://cran.r-project.org/package=profilr)

    ``` r
    install.packages("profilr")
    ```

-   the latest development version from github with

    [![GitHub version](https://badge.fury.io/gh/paulhendricks%2Fprofilr.svg)](http://badge.fury.io/gh/paulhendricks%2Fprofilr)

    ``` r
    if (packageVersion("devtools") < 1.6) {
      install.packages("devtools")
    }
    devtools::install_github("paulhendricks/profilr")
    ```

If you encounter a clear bug, please file a minimal reproducible example on [github](https://github.com/paulhendricks/profilr/issues).

API
---

``` r
library(dplyr, warn.conflicts = FALSE)
library(profilr)
#> 
#> Attaching package: 'profilr'
#> 
#> The following object is masked from 'package:stats':
#> 
#>     profile

mtcars %>% 
  profile
#>    .column_name .column_class .column_type .count_elements .count_uniques
#> 1           mpg       numeric       double              32             25
#> 2           cyl       numeric       double              32              3
#> 3          disp       numeric       double              32             27
#> 4            hp       numeric       double              32             22
#> 5          drat       numeric       double              32             22
#> 6            wt       numeric       double              32             29
#> 7          qsec       numeric       double              32             30
#> 8            vs       numeric       double              32              2
#> 9            am       numeric       double              32              2
#> 10         gear       numeric       double              32              3
#> 11         carb       numeric       double              32              6
#>    .percent_uniques .count_NULLs .percent_NULLs .count_NAs .percent_NAs
#> 1           0.78125            0              0          0            0
#> 2           0.09375            0              0          0            0
#> 3           0.84375            0              0          0            0
#> 4           0.68750            0              0          0            0
#> 5           0.68750            0              0          0            0
#> 6           0.90625            0              0          0            0
#> 7           0.93750            0              0          0            0
#> 8           0.06250            0              0          0            0
#> 9           0.06250            0              0          0            0
#> 10          0.09375            0              0          0            0
#> 11          0.18750            0              0          0            0
#>    .count_zeroes .percent_zeros .mean_value   .sd_value .q0_value
#> 1              0        0.00000   20.090625   6.0269481    10.400
#> 2              0        0.00000    6.187500   1.7859216     4.000
#> 3              0        0.00000  230.721875 123.9386938    71.100
#> 4              0        0.00000  146.687500  68.5628685    52.000
#> 5              0        0.00000    3.596563   0.5346787     2.760
#> 6              0        0.00000    3.217250   0.9784574     1.513
#> 7              0        0.00000   17.848750   1.7869432    14.500
#> 8             18        0.56250    0.437500   0.5040161     0.000
#> 9             19        0.59375    0.406250   0.4989909     0.000
#> 10             0        0.00000    3.687500   0.7378041     3.000
#> 11             0        0.00000    2.812500   1.6152000     1.000
#>    .q25_value .q50_value .q75_value .q100_value
#> 1    15.42500     19.200      22.80      33.900
#> 2     4.00000      6.000       8.00       8.000
#> 3   120.82500    196.300     326.00     472.000
#> 4    96.50000    123.000     180.00     335.000
#> 5     3.08000      3.695       3.92       4.930
#> 6     2.58125      3.325       3.61       5.424
#> 7    16.89250     17.710      18.90      22.900
#> 8     0.00000      0.000       1.00       1.000
#> 9     0.00000      0.000       1.00       1.000
#> 10    3.00000      4.000       4.00       5.000
#> 11    2.00000      2.000       4.00       8.000
#>                                                                    .top_5_values
#> 1       (1) 10.4 [2]\n (1) 15.2 [2]\n (1) 19.2 [2]\n (1) 21 [2]\n (1) 21.4 [2]\n
#> 2                                          (1) 8 [14]\n (2) 4 [11]\n (3) 6 [7]\n
#> 3     (1) 275.8 [3]\n (2) 160 [2]\n (2) 167.6 [2]\n (2) 360 [2]\n (5) 71.1 [1]\n
#> 4           (1) 110 [3]\n (1) 175 [3]\n (1) 180 [3]\n (4) 66 [2]\n (4) 123 [2]\n
#> 5     (1) 3.07 [3]\n (1) 3.92 [3]\n (3) 2.76 [2]\n (3) 3.08 [2]\n (3) 3.15 [2]\n
#> 6  (1) 3.44 [3]\n (2) 3.57 [2]\n (3) 1.513 [1]\n (3) 1.615 [1]\n (3) 1.835 [1]\n
#> 7   (1) 17.02 [2]\n (1) 18.9 [2]\n (3) 14.5 [1]\n (3) 14.6 [1]\n (3) 15.41 [1]\n
#> 8                                                      (1) 0 [18]\n (2) 1 [14]\n
#> 9                                                      (1) 0 [19]\n (2) 1 [13]\n
#> 10                                         (1) 3 [15]\n (2) 4 [12]\n (3) 5 [5]\n
#> 11                 (1) 2 [10]\n (1) 4 [10]\n (3) 1 [7]\n (4) 3 [3]\n (5) 6 [1]\n
#>                                                                 .bottom_5_values
#> 1       (8) 33.9 [1]\n (8) 32.4 [1]\n (8) 27.3 [1]\n (8) 26 [1]\n (8) 24.4 [1]\n
#> 2                                          (3) 6 [7]\n (2) 4 [11]\n (1) 8 [14]\n
#> 3          (5) 472 [1]\n (5) 460 [1]\n (5) 440 [1]\n (5) 400 [1]\n (5) 351 [1]\n
#> 4          (8) 335 [1]\n (8) 264 [1]\n (8) 230 [1]\n (8) 215 [1]\n (8) 205 [1]\n
#> 5     (9) 4.93 [1]\n (9) 4.43 [1]\n (9) 4.11 [1]\n (9) 3.85 [1]\n (9) 3.77 [1]\n
#> 6  (3) 5.424 [1]\n (3) 5.345 [1]\n (3) 5.25 [1]\n (3) 4.07 [1]\n (3) 3.845 [1]\n
#> 7     (3) 22.9 [1]\n (3) 20.22 [1]\n (3) 20.01 [1]\n (3) 20 [1]\n (3) 19.9 [1]\n
#> 8                                                      (2) 1 [14]\n (1) 0 [18]\n
#> 9                                                      (2) 1 [13]\n (1) 0 [19]\n
#> 10                                         (3) 5 [5]\n (2) 4 [12]\n (1) 3 [15]\n
#> 11                  (5) 8 [1]\n (5) 6 [1]\n (4) 3 [3]\n (3) 1 [7]\n (1) 4 [10]\n

mtcars %>% 
  group_by(cyl) %>% 
  do(profile(.))
#> Source: local data frame [33 x 22]
#> Groups: cyl [3]
#> 
#>      cyl .column_name .column_class .column_type .count_elements
#>    (dbl)        (chr)         (chr)        (chr)           (int)
#> 1      4          mpg       numeric       double              11
#> 2      4          cyl       numeric       double              11
#> 3      4         disp       numeric       double              11
#> 4      4           hp       numeric       double              11
#> 5      4         drat       numeric       double              11
#> 6      4           wt       numeric       double              11
#> 7      4         qsec       numeric       double              11
#> 8      4           vs       numeric       double              11
#> 9      4           am       numeric       double              11
#> 10     4         gear       numeric       double              11
#> ..   ...          ...           ...          ...             ...
#> Variables not shown: .count_uniques (int), .percent_uniques (dbl),
#>   .count_NULLs (int), .percent_NULLs (dbl), .count_NAs (int), .percent_NAs
#>   (dbl), .count_zeroes (int), .percent_zeros (dbl), .mean_value (dbl),
#>   .sd_value (dbl), .q0_value (dbl), .q25_value (dbl), .q50_value (dbl),
#>   .q75_value (dbl), .q100_value (dbl), .top_5_values (chr),
#>   .bottom_5_values (chr)
```

People
------

-   The original author of `describer` is [Paul Hendricks](https://github.com/paulhendricks). [![Gratipay](https://img.shields.io/gratipay/JSFiddle.svg)](https://gratipay.com/~paulhendricks/)

-   The lead maintainer of `describer` is [Paul Hendricks](https://github.com/paulhendricks). [![Gratipay](https://img.shields.io/gratipay/JSFiddle.svg)](https://gratipay.com/~paulhendricks/)

License
-------

[![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/paulhendricks/profilr/blob/master/LICENSE)
