
<!-- README.md is generated from README.Rmd. Please edit that file -->

# autodepFailExample

This demonstrates that **devtools::document()** does not record imports
included in files which contain no code.

This means that a file which only contains imports, such as:

``` r
#' @importFrom data.table as.data.table
```

will **NOT** have the **as.data.table** function added to the package
NAMESPACE, but the following:

``` r
#' @importFrom data.table as.data.table 
whatever <- NULL
```

**will**, regardless of whether the accompanying code makes any sense or
not.

To replicate within the package, simply rerun the command for this
package. **passing\_import.R** only contains a single bogus definition -
but unlike **failing\_import.R**, **devtools::document()** recognizes
the imports listed there (regardless of whether they are used).

I have no idea if this behavior is intended, but I nonetheless wanted to
replicate it here.
