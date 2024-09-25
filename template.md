Data_import
================

This documnet will show how to import data.

## Import the FAS Litters CSV

- Get rid of characters, lower case, replace space with underscore
- clean_name is the only one function in the janitor so I don’t need
  library actually. It works when there are multiple packages use the
  same function name

``` r
litters_df = read_csv("data_import_examples/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

## Look at the dataset

head(litters_df) tail(litters_df,10)

``` r
view(litters_df)
```

## Learning Assessment

``` r
pups_df = read.csv("data_import_examples/FAS_pups.csv")
#read.csv("~/Desktop/data_wranging_i/data/FAS_litters.csv")
pups_df = janitor::clean_names(pups_df)
```

## Look at read_csv options

col_names and skip

``` r
litters_df = read_csv(
  file = "data_import_examples/FAS_litters.csv",
  col_names = FALSE,
  skip = 1
)
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

what about missing values

``` r
litters_df = 
  read_csv(
    file = "data_import_examples/FAS_litters.csv",
    na = c("NA","",".")
  )
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
pull(litters_df, gd0_weight)
```

    ##  [1] 19.7 27.0 26.0 28.5   NA   NA   NA   NA   NA 28.5 28.0   NA   NA   NA   NA
    ## [16] 17.0 21.4   NA   NA   NA 28.0 23.5 22.6   NA 21.7 24.4 19.5 24.3 22.6 22.2
    ## [31] 23.8 22.6 23.8 25.5 23.9 24.5   NA   NA 26.9 27.5 28.5 33.4 21.8 25.4 20.0
    ## [46] 21.8 25.6 23.5 25.5

what if we code `group` as a factor variable?

``` r
litters_df = 
  read_csv(
    file = "data_import_examples/FAS_litters.csv",
    na = c("NA","","."),
    col_types = cols(
      Group = col_factor()
    )
  )
```

## Import an excel file

import MLB 2011 summary data

``` r
mlb_df = read_excel("data_import_examples/mlb11.xlsx", sheet = "mlb11")
```

## Import SAS data

``` r
pulse_df = read_sas("data_import_examples/public_pulse_data.sas7bdat")
```
