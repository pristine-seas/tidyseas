# Dependency policy

Add a package to DESCRIPTION only when the first function that needs it lands,
with `usethis::use_package()`. Keep Imports to what every user needs; anything
that serves one function goes in Suggests and is gated with
`rlang::check_installed()` inside that function.

## Prefer base R or an existing import over a new dependency

| Instead of | Use |
|---|---|
| glue | `cli::format_inline()` or `paste0()` |
| lubridate | `format(x, "%Y")` and friends |
| purrr | `lapply()`, `vapply()`, `dplyr::bind_rows()` |
| stringr | `sub()`, `regmatches()`, `tolower()`, `strsplit()`, `tools::toTitleCase()` |
| tibble | dplyr re-exports `tibble()`, `as_tibble()`, `tribble()` |
| viridisLite | `grDevices::hcl.colors()` |
| readr | `utils::read.csv()`, `utils::write.csv()` |
| furrr, future | sequential `lapply()` unless a job is measured to need it |

Base packages used by code, such as grDevices, graphics and utils, still have to
be declared in Imports.

## Logos

`man/figures/PS_shield.svg` and `man/figures/PS_wordmark.png` are the official
Pristine Seas marks. The shield carries the brand colours `#2074A4`, `#003764`
and `#AAE4D8`. They serve the README and pkgdown only; a function that needs a
logo should ship a copy under `inst/logos/`.
