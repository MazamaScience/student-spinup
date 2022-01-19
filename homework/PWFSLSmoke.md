# PWFSLSmoke

Introduction to Air Quality with the **PWFSLSmoke** package.

-----

## Background

The PWFSLSmoke R package was developed for PWFSL to help modelers, scientists and air quality professionals more easily work with PM2.5 data from monitoring locations across North America.

The package makes it easier to obtain data, perform analyses and generate reports. It includes functionality to:

* download and easily work with regulatory PM2.5 data from the EPA and AirNow
* download and quality control raw monitoring data from AIRSIS and WRCC
* convert between UTC and local timezones
* apply various algorithms to the data (nowcast, rolling means, aggregation, etc.)
* provide interactive timeseries and maps through RStudio’s Viewer pane
* create a variety of publication ready maps and timeseries plots

## Documentation

The **PWFSLSmoke** package has extensive documentation available at:

http://mazamascience.github.io/PWFSLSmoke/index.html

The [Get Started](http://mazamascience.github.io/PWFSLSmoke/articles/PWFSLSmoke.html)
tab is the best place to begin.

## Lifecycle

The **PWFSLSmoke** package is being maintained only. New development is happening
on a replacement package called [AirMonitor](https://github.com/MazamaScience/AirMonitor)
which is faster, more robust and whose functions are more compatible with 
**tidyverse** style. The **AirMonitor** package will eventually replace **PWFSLSmoke**
in operational systems, hopefully before the end of 2022.

As of Jan 19, 2022, the **AirMonitor** package has functionality for
working with "latest" data covering the most recent 10 days. But archival 
datasets have not yet been created.

