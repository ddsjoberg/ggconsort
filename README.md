
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ggconsort

<!-- badges: start -->
<!-- badges: end -->

The goal of ggconsort is to provide convenience functions for creating
CONSORT diagrams with `ggplot2`.

## Installation

You can install the released version of ggconsort from
[GitHub](https://github.com/tgerke/ggconsort) with:

``` r
devtools::install_github("tgerke/ggconsort")
```

## Example

In the following, we filter the `penguins` data to only those from
Biscoe island. In the same `dplyr` chain, we collect the number of
distinct species overall (i.e. before the filter to Biscoe) and the
number of distinct species on Biscoe into a list called `counts`. In the
next step, we will use `counts` to construct a basic data flow diagram.

``` r
library(ggconsort)

biscoe_penguins <- palmerpenguins::penguins %>%
  return_distinct(species, counts, "species_overall") %>%
  dplyr::filter(island == "Biscoe") %>%
  return_distinct(species, counts, "species_biscoe")

# the number of penguins in our data before the filter
nrow(palmerpenguins::penguins)
#> [1] 344
# the number of penguins in our data after the filter
nrow(biscoe_penguins)
#> [1] 168
# the numbers of unique penguin species before and after the filter
counts
#> $species_overall
#> [1] 3
#> 
#> $species_biscoe
#> [1] 2
```
