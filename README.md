# World rainfall exercise

Here I present a basic workflow on handling rainfall data provided by NASA' Global Precipitation Climatology Project([GPCP](https://precip.gsfc.nasa.gov)).

_GPCP 1-Degree Daily_([1DD, version 1.2](https://rda.ucar.edu/datasets/ds728.3/)) is the dataset in use.
1DD contains world-wide precipitation estimates binned in 1 square degree (longitude,latitude) for each day since October,1996, until October,2015.
The whole dataset is splited in 19x12+1=229 files, for each month of the period.
Each data file is a 3-dimensional array of shape (lines,columns,fields): 180,360; *lines* represent latitude, *columns* represent longitude and *fields* are the days of the respective month.

From the [dataset description page](https://rda.ucar.edu/datasets/ds728.3/):
```
The data set archive consists of unformatted REAL*4 binary files with ASCII headers. Each file holds 28-31 daily fields. Each file occupies about 8 MB. The grid on which each field of values is presented is a 1°x1° latitude--longitude (Cylindrical Equal Distance) global array of points. It is size 360x180, with X (longitude) incrementing most rapidly West to East from the Prime Meridian, and then Y (latitude) incrementing North to South. Whole- and half-degree values are at grid edges:
 
First point center = (89.5°N,0.5°E)
Second point center = (89.5°N,1.5°E)
Last point center = (89.5°S,0.5°W)
Missing values are denoted by the value -99999., and the units are mm/day.
The standard reference is:
 
Huffman, G.J., R.F. Adler, M. Morrissey, D.T. Bolvin, S. Curtis, R. Joyce, B McGavock, J. Susskind, 2001: Global Precipitation at One-Degree Daily Resolution from Multi-Satellite Observations. J. Hydrometeor., 2, 36-50.
```

## Goals

First of all, we have to read the GPCP-1DD dataset -- distributed in binary files (numpy arrays).
Then, to visualize the data, we want to have world-map plot with data shown per country according to the epoch (month/year) or during a period.

The fundamental -- or *main* -- product here is a table of precipitations, per country per month.

The data model:
* _Regions_: table defining the regions of interest; for instance, countries and their (longitude,latitude) polygon definition as seen at: https://github.com/chdoig/scipy2015-blaze-bokeh/blob/master/data/World_Country_Boundaries.csv.gz

name | lons | lats | ...
-----|-----------|----------|-----
Brazil | [0,1,0] | [0,0,1]  | ...

* _World-Rainfall_: monthly table with values for precipitation at each position of interest (for instance, the whole world)

longitude | latitude | precipitation
:--------:|:--------:|:-------------:
0.5 | 0.5 | 13

* _Countries-Rainfall_: table with values for precipitation for each country on each month

period | Country-A | Country-B | ...
:-----:|:---------:|:---------:|-----
Month-1/Year-1 | value-A | value-B | ...
