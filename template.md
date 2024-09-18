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
