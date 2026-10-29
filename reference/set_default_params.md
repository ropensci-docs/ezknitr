# Set default parameters

Create variables with the given values only if these variables do not
currently exist.

## Usage

``` r
set_default_params(params)
```

## Arguments

- params:

  List of parameters.

## Details

Sometimes it may be useful to define a variable only it hasn't been
defined yet. One example where this can be useful is when you have an
Rmd script that uses some variables and you want to be able to use
custom values for these variables, but also give them a default value in
the script in case they are not set beforehand.

## Examples

``` r
exists("foo")
#> [1] FALSE
exists("bar")
#> [1] FALSE
foo <- 5
set_default_params(list(foo = 10, bar = 20))
print(foo)
#> [1] 5
print(bar)
#> [1] 20
```
