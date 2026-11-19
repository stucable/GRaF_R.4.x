# GRaF 0.1-15.1 (fork: stucable/GRaF_R.4.x)

Unofficial fork of [goldingn/GRaF](https://github.com/goldingn/GRaF) 0.1-15 (2017-02-27), maintained by Stuart Cable. The statistical method and the model code are unchanged; the changes below only restore compatibility with current R.

## Bug fixes

* `cov.SE()`: `if (class(sumdiffs) == 'dist')` replaced by `inherits(sumdiffs, 'dist')`. In R >= 4.0 a matrix has class `c("matrix", "array")`, so the condition had length 2; R 4.0–4.1 gave a warning and R >= 4.2 gives the error "the condition has length > 1", which stopped every `graf()` fit with `opt.l = TRUE` (2026-01).
* `predict.graf()`: the raster test now uses `inherits()`, and the column-class check compares only the first class of each column, so columns with more than one class (e.g. ordered factors) no longer break prediction (2026-01).

## Package metadata

* Package name restored to `GRaF` (an underscore is not valid in an R package name), so `library(GRaF)` works unchanged.
* `Authors@R` added: Nick Golding (author, copyright holder) and Stuart Cable (contributor, maintainer of this fork). `BugReports` now points to this fork.
* `LICENSE` (GPL-2 text) and `inst/CITATION` (Golding & Purse 2016) added.

## Verification

Installed and tested on R 4.3.3. On a test data set, fitted lengthscales, predictions to a data frame and to a `RasterStack`, and DIC agree with upstream 0.1-15 to 10 decimal places.
