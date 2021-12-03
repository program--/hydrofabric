
<!-- README.md is generated from README.Rmd. Please edit that file -->

# hydrofabric

<!-- badges: start -->

[![R-CMD-check](https://github.com/NOAA-OWP/hydrofabric/workflows/R-CMD-check/badge.svg)](https://github.com/NOAA-OWP/hydrofabric/actions)
<!-- badges: end -->

### Overview

There are three major types of network refactoring needed to meet a
broad set of needs:

1.  One based on a flowline length criteria (routing)
2.  One that aims for a uniform catchment size (rainfall-runoff)
3.  A POI version that forces things down to a set critical locations
    (PRMS).

`hydrofabric` is a set of packages that work in harmony to meet these
needs. The package is designed to make it easy to install and load core
packages across users and organizations in a single command.

## Installation

``` r
# Install the development version from GitHub
# install.packages("remotes")
remotes::install_github("NOAA-OWP/hydrofabric")
```

## Usage

``` r
library(hydrofabric)
#> ── Attaching packages ───────────────────────────────── hydrofabric1.3.1.9000 ──
#> ✓ nhdplusTools 0.4.3          ✓ hyAggregate  0.0.1     
#> ✓ hyRefactor   0.4.7          ✓ zonal        0.0.1     
#> ✓ hyRelease    0.0.0.9000
#> ── Conflicts ──────────────────────────────────────── hydrofabric_conflicts() ──
#> x hyAggregate::flowpaths_to_linestrings() masks hyRefactor::flowpaths_to_linestrings()
#> x hyAggregate::length_average_routlink()  masks hyRelease::length_average_routlink()
```

`library(hydrofabric)` will load the core packages:

-   [zonal](https://github.com/mikejohnson51/zonal) for catchment
    parameter estimation
-   [nhdplusTools](https://github.com/usgs-r/nhdplusTools/) for network
    manipulation
-   [hyRefactor](https://github.com/dblodgett-usgs/hyRefactor) for
    network factoring
-   [hyAggregate](https://github.com/mikejohnson51/hyAggregate) for
    network aggregation
-   [hyRelease](https://github.com/mikejohnson51/hyRelease) for data
    releases running elected subroutines

Soon these will be added:

-   [nhdarrow]() (In development)
-   [nwmdata]() (In development)

## Code of Conduct

Please note that the project is released with a [Contributor Code of
Conduct](). By contributing to this project, you agree to abide by its
terms.
