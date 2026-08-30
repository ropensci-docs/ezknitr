# Set up a test directory to experiment with `ezspin` or `ezknit`

Create a few directories that try to mimic a real data-analysis project
structure, and add a data file and a simple R script (for `ezspin`) or
Rmarkdown file (for `ezknit`).  
  
After setting up these files and directories, you can run `ezknitr`
commands and their equivalent `knitr` commands to compare and see the
benefits of using `ezknitr`.  
  
More specific instructions on how to interact with this test directory
will be printed to the console.

## Usage

``` r
setup_ezspin_test()

setup_ezknit_test()
```

## Value

The path to the test directory.

## See also

[`ezspin`](https://docs.ropensci.org/ezknitr/reference/ezknitr_core.md)
[`spin`](https://rdrr.io/pkg/knitr/man/spin.html)
[`ezknit`](https://docs.ropensci.org/ezknitr/reference/ezknitr_core.md)
[`knit`](https://rdrr.io/pkg/knitr/man/knit.html)
[`open_output_dir`](https://docs.ropensci.org/ezknitr/reference/open_output_dir.md)

## Examples

``` r
if (FALSE) { # \dontrun{
library(ezknitr)

# setup the test directory structures and run naive spin
setup_ezspin_test()
knitr::spin("ezknitr_test/R/ezspin_test.R")
file.remove(c("ezspin_test.md", "ezspin_test.html"))

# setup the test directory structures and run simple ezspin
setup_ezspin_test()
ezspin("R/ezspin_test.R", wd = "ezknitr_test")

# setup the test directory structures and run ezspin with more parameters
tmp <- setup_ezspin_test()
ezspin("R/ezspin_test.R", wd = "ezknitr_test",
        out_dir = "output", fig_dir = "coolplots")
unlink(tmp, recursive = TRUE, force = TRUE)
} # }
```
