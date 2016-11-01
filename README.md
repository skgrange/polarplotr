
<!-- Edit the README.Rmd only!!! The README.md is generated automatically from README.Rmd. -->
polarplotr: bivariate polar plots for air pollution data analysis
=================================================================

For the main **openair** website, see <http://davidcarslaw.github.io/openair/>.

Functions to plot bivariate polar plots for air pollution data analysis. **polarplotr** uses [**openair**](https://github.com/davidcarslaw/openair) functions but they have been enhanced to consider pair-wise statistics to compare two pollutants through correlation and regression.

An accompanying publication outlining the package developments can be found [here](http://www.sciencedirect.com/science/article/pii/S1352231016307166). The package documentation is in development and can be found [here](http://davidcarslaw.github.io/polarplotr/docs/).

Installation
------------

**polarplotr** has not been released on CRAN yet, therefore the development version must be installed. The best way to do this is to install the **devtools** package and use the `install_github` function. However, if you are using a Windows system, [Rtools](https://cran.r-project.org/bin/windows/Rtools/) needs to be installed before installation of **devtools** is attempted. For macOS and Linux systems, this step is not needed and to install **polarplotr**, do this:

``` r
# If needed, install Rtools

# If needed, install devtools
install.packages("devtools")

# Install development version of polarplotr
devtools::install_github("davidcarslaw/polarplotr")
```

Usage
-----

At some point in the near future the existing `polarPlot` function in **openair** will be removed and the `polarplotr` version, which has more capabilities used instead. In the meantime it is best to load **polarplotr** *after* **openair** i.e.

``` r
library(openair)
library(polarplotr)
```

**polarplotr** main function is `polarPlot` and the usage is the same as for **openair**'s version. To use the enhancements of pair-wise statistics, a pair of pollutants is needed and the statistic argument differs. The function's help contains details on these options.

``` r
# Import air quality data for London Marylebone Road
data_mary <- importAURN(site = "my1", year = 2013, verbose = FALSE)

# Plot a "standard" polar plot
polarPlot(data_mary, pollutant = "no2", statistic = "mean")

# Plot correlation of particlate species
polarPlot(data_mary, pollutant = c("pm2.5", "pm10"), statistic = "r")

# How about the slope, with a newer colour map, will take a minute or two...
polarPlot(data_mary, pollutant = c("pm2.5", "pm10"), statistic = "robust_slope",
          cols = "inferno")
```
