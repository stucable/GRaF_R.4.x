# GRaF (R ≥ 4.x compatible fork)

This is an **unofficial fork** of [GRaF](https://github.com/goldingn/GRaF), the R package by **Nick Golding** that fits species distribution models with Gaussian processes (Gaussian random fields). It is not endorsed by the original author. The method, the model code and the copyright remain Nick Golding's. This fork changes only the code needed to run on current versions of R.

## Why this fork exists

Upstream GRaF 0.1-15 (2017) no longer runs on R ≥ 4.2. `cov.SE()` uses `if (class(x) == 'dist')`, and in R ≥ 4.0 a matrix has two classes, so R ≥ 4.2 stops with *"the condition has length > 1"*. This stops every `graf()` call with `opt.l = TRUE`. This fork replaces the class tests with `inherits()` and makes a related fix in `predict.graf()`. See [NEWS.md](NEWS.md) for the full list. Results are numerically identical to upstream: on a test data set they agree to 10 decimal places.

## Installation

```r
# install.packages("remotes")
remotes::install_github("stucable/GRaF_R.4.x")
library(GRaF)
```

The package name is still `GRaF`, so existing scripts work without change.

## Citation

If you use GRaF, please cite the method paper (`citation("GRaF")`):

> Golding, N. & Purse, B. V. (2016) Fast and flexible Bayesian species distribution modelling using Gaussian processes. *Methods in Ecology and Evolution*, 7(5), 598–608. https://doi.org/10.1111/2041-210X.12523

Please also state in your methods that you used this fork (GRaF 0.1-15.1, `stucable/GRaF_R.4.x`), so that others can identify the software version.

## Issues

Please report problems with this fork in [this repository's issues](https://github.com/stucable/GRaF_R.4.x/issues), not upstream. For new Gaussian process modelling work, see also Nick Golding's [greta](https://greta-stats.org) and greta.gp packages.

## Licence

GPL (≥ 2), as for the original package (see [LICENSE](LICENSE)). Original code © Nick Golding. The changed lines are marked in the source and listed in [NEWS.md](NEWS.md).
