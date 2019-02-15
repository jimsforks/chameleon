
<!-- README.md is generated from README.Rmd. Please edit that file -->
visualidentity
==============

The goal of visualidentity is to build package documentation using personnalized templates.

Installation
------------

``` r
# install.packages("remotes")
remotes::install_github("ThinkR-open/visualidentity")
```

Examples
--------

### Build a book from vignettes inside a package

You can use `create_book()` using your own template basis. By default, it uses {bookdown} site template. You can use it to build your own.

``` r
template <- system.file("rstudio/templates/project/resources", package = "bookdown")
create_book(path = "inst/report", clean = TRUE,
            template = template)
```

Help users find your book with function `open_guide_function()`. This adds function `open_guide()` inside your package that will open the userguide (in HTML or PDF) on demand.

``` r
open_guide_function(path = "inst/report")
```

### Build a pkgdown site inside a package

You can use `build_pkgdown()` using your own template basis. By default, it uses the {pkgdown} original template.
To use your own template, it is better to create a R package with all necessary files (See <https://github.com/tidyverse/tidytemplate> as an example).

\*You can then define your own "\_pkgdown.yml" file that will call your template when building the site: \*

``` yaml
template:
  package: mypackagetemplate
```

``` r
visualidentity::build_pkgdown(
  lazy = TRUE,
  yml = "/pah/to/your/yaml/_pkgdown.yml",
  favicon = "/path/to/your/favicon.ico",
  move = TRUE
)
```

Help users find your pkgdown website with function `open_pkgdown_function()`. This adds function `open_pkgdown()` inside your package that will open the site on demand.

``` r
visualidentity::open_pkgdown_function()
```
