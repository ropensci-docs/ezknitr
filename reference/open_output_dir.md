# Open the directory containing the output from the last ezknitr command

Call this function after running
[ezspin](https://docs.ropensci.org/ezknitr/reference/ezknitr_core.md) or
[ezknit](https://docs.ropensci.org/ezknitr/reference/ezknitr_core.md) to
open the resulting output directory in your file browser. This is simply
a convenience function so that if you want to see the results you don't
need to navigate to the appropriate folder manually.

## Usage

``` r
open_output_dir()
```

## Examples

``` r
if (FALSE) { # \dontrun{
library(ezknitr)
setup_ezspin_test()
ezspin("R/ezspin_test.R", wd = "ezknitr_test")
open_output_dir()
} # }
```
