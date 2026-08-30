# Changelog

## ezknitr 0.6.3 2023-08-19

CRAN release: 2023-08-20

- More maintenance work for CRAN

## ezknitr 0.6.2 2023-04-01

CRAN release: 2023-04-01

- Small maintenance work to keep the package on CRAN

## ezknitr 0.6.1 2016-12-19

- GitHub repository ownership transferred from ropenscilabs to ropensci

## ezknitr 0.6 2016-09-15

CRAN release: 2016-09-16

- GitHub repository ownership transferred from daattali to rOpenSciLabs

## ezknitr 0.5 2016-08-21

CRAN release: 2016-09-14

- added JOSS paper
- revisions based on rOpenSci feedback, mostly modifications to README
  and other documentation

## ezknitr 0.4 2016-06-12

CRAN release: 2016-06-13

- added `...` argument to `ezspin` that passes any additional arguments
  to [`knitr::spin`](https://rdrr.io/pkg/knitr/man/spin.html)
  ([\#6](https://github.com/ropensci/ezknitr/issues/6))
- add param `move_intermediate_file` to `ezspin` that controls whether
  the intermediate Rmd file stays with the source R script or moves to
  the output folder (thanks [@klmr](https://github.com/klmr))

## ezknitr 0.3.0

CRAN release: 2015-12-08

2015-12-07

- add section about
  [`rmarkdown::render`](https://pkgs.rstudio.com/rmarkdown/reference/render.html)
  in vignette/readme

## ezknitr 0.2.0

2015-12-07

- add unit tests
- documentation additions, getting ready for CRAN release

## ezknitr 0.1.0

2015-12-05

- add `setup_ezknit_test` function
- add `open_output_dir` function

## ezknitr 0.0.0.9002

2015-11-06

- rename `ezrender` to `ezknitr`
- many internal changes and code improvements
- no longer need to delete an empty wrong figures folder because knitr
  fixed its bug [\#942](https://github.com/ropensci/ezknitr/issues/942)

## ezknitr 0.0.0.9001

2015-10-23

- [`ezspin()`](https://docs.ropensci.org/ezknitr/reference/ezknitr_core.md)
  gains new arguments `keepRmd` (default: `FALSE`) and `keepMd`
  (default: `TRUE`)
  ([\#1](https://github.com/ropensci/ezknitr/issues/1))

## ezknitr 0.0.0.9000

- Import from `rsalad` package
