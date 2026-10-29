# Knit Rmd or spin R files without the typical pain of working directories

`ezknitr` is an extension of `knitr` that adds flexibility in several
ways. One common source of frustration with `knitr` is that it assumes
the directory where the source file lives should be the working
directory, which is often not true. `ezknitr` addresses this problem by
giving you complete control over where all the inputs and outputs are,
and adds several other convenient features. The two main functions are
`ezknit` and `ezspin`, which are wrappers around `knitr`'s `knit` and
`spin`, used to make rendering markdown/HTML documents easier.

## Usage

``` r
ezspin(
  file,
  wd,
  out_dir,
  fig_dir,
  out_suffix,
  params = list(),
  verbose = FALSE,
  chunk_opts = list(tidy = FALSE),
  keep_rmd = FALSE,
  keep_md = TRUE,
  keep_html = TRUE,
  move_intermediate_file = TRUE,
  ...
)

ezknit(
  file,
  wd,
  out_dir,
  fig_dir,
  out_suffix,
  params = list(),
  verbose = FALSE,
  chunk_opts = list(tidy = FALSE),
  keep_md = TRUE,
  keep_html = TRUE
)
```

## Arguments

- file:

  The path to the input file (.Rmd file if using `ezknit` or .R script
  if using `ezspin`). If `wd` is provided, then this path is relative to
  `wd`.

- wd:

  The working directory to be used in the Rmd/R script. Defaults to the
  current working directory (note that this is not the same behaviour as
  `knitr`). See the 'Detailed Arguments' section for more details.

- out_dir:

  The output directory for the rendered markdown or HTML files (if `wd`
  is provided, then this path is relative to `wd`). Defaults to the
  directory containing the input file.

- fig_dir:

  The name (or path) of the directory where figures should be generated.
  See the 'Detailed Arguments' section for more details.

- out_suffix:

  A suffix to add to the output files. Can be used to differentiate
  outputs from runs with different parameters. The name of the output
  files is the name of the input file appended by `out_suffix`,
  separated by a dash.

- params:

  A named list of parameters to be passed to use in the input Rmd/R
  file. For example, if the script to execute assumes that there is a
  variable named `DATASET_NAME`, then you can use
  `params = list('DATASET_NAME' = 'oct10dat')`.

- verbose:

  If TRUE, then show the progress of knitting the document.

- chunk_opts:

  List of knitr chunk options to use. See
  [`?knitr::opts_chunk`](https://rdrr.io/pkg/knitr/man/opts_chunk.html)
  for a list of available chunk options.

- keep_rmd, keep_md:

  Should intermediate `Rmd` or `md` files be kept (`TRUE`) or deleted
  (`FALSE`)?

- keep_html:

  Should the final `html` file be kept (`TRUE`) or deleted (`FALSE`)?

- move_intermediate_file:

  Should the intermediate `Rmd` file be moved to the output folder
  (`TRUE`) or stay in the same folder as the source `R` file (`FALSE`)?

- ...:

  Any extra parameters that should be passed to
  [`knitr::spin`](https://rdrr.io/pkg/knitr/man/spin.html).

## Value

The path to the output directory (invisibly).

## Details

If you have a very simple project with a flat directory structure, then
`knitr` works great. But even something as simple as trying to knit a
document that reads a file from a different directory or placing the
output rendered files in a different folder cannot be easily done with
`knitr`.

`ezknitr` improves basic `knitr` functionality in a few ways. You get to
decide:

- What the working directory of the source file is

- Where the output files will go

- Where the figures used in the markdown will go

- Any parameters to pass to the source file

## Detailed Arguments

All paths given in the arguments can be either absolute or relative.

The `wd` argument is very important and is set to the current working
directory by default. The path of the input file and the path of the
output directory are both relative to `wd` (unless they are absolute
paths). Moreover, any code in the R script that reads or writes files
will use `wd` as the working directory.

The `fig_dir` argument is relative to the output directory, since the
figures accompanying a markdown file should be placed in the same
directory. It is recommended to either leave `fig_dir` as default or set
it to a different name but not to a different directory. Because of the
way `knitr` works, there are a few known minor issues if `fig_dir` is
set to a different directory.

## Difference between ezknit and ezspin

`ezknit` is a wrapper around
[`knitr::knit`](https://rdrr.io/pkg/knitr/man/knit.html) while `ezspin`
is a wrapper around `ezspin`. The two functions are very similar. `knit`
is the more popular and well-known function. It is used to render a
markdown/HTML document from an Rmarkdown source. `spin` takes an R
script as its input, produces an Rmarkdown document from the R script,
and then calls `knit` on it.

## See also

[`open_output_dir`](https://docs.ropensci.org/ezknitr/reference/open_output_dir.md)
[`setup_ezknit_test`](https://docs.ropensci.org/ezknitr/reference/setup_test.md)
[`setup_ezspin_test`](https://docs.ropensci.org/ezknitr/reference/setup_test.md)
[`set_default_params`](https://docs.ropensci.org/ezknitr/reference/set_default_params.md)
[`knit`](https://rdrr.io/pkg/knitr/man/knit.html)
[`spin`](https://rdrr.io/pkg/knitr/man/spin.html)

## Examples

``` r
if (FALSE) { # \dontrun{
   tmp <- setup_ezknit_test()
   ezknit("R/ezknit_test.Rmd", wd = "ezknitr_test")
   ezknit("R/ezknit_test.Rmd", wd = "ezknitr_test",
          out_dir = "output", fig_dir = "coolplots",
          params = list(numPoints = 50))
   open_output_dir()
   unlink(tmp, recursive = TRUE, force = TRUE)
 
   tmp <- setup_ezspin_test()
   ezspin("R/ezspin_test.R", wd = "ezknitr_test")
   ezspin("R/ezspin_test.R", wd = "ezknitr_test",
          out_dir = "output", fig_dir = "coolplots",
          params = list(numPoints = 50), keep_rmd = TRUE)
   open_output_dir()
   unlink(tmp, recursive = TRUE, force = TRUE)
} # }
```
