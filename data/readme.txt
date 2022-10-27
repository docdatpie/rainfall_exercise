# World rainfall dataset

This dataset provides historical data of rainfall measurements worldwide. 
The 229 numpy files report average measurements for every month since 1996 (October) until 2015 (October).
The arrays in each file have shape "180,360", representing a 1 deg^2 resolution grid covering "latitude, longitude" axes (-90:90, -180:180 deg).
The coordinates of the top-left "pixel" is at "89.5N,0.5E", the next on its side is "89.5N,1.5E"; and finish at "89.5S,0.5W".

The original page of the dataset is at https://rda.ucar.edu/datasets/ds728.3/.
The original dataset is at https://www1.ncdc.noaa.gov/pub/data/gpcp/daily-v1.2/.

Related links:
- https://www.ncei.noaa.gov/access/metadata/landing-page/bin/iso?id=gov.noaa.ncdc:C00931
- https://climatedataguide.ucar.edu/climate-data/gpcp-daily-global-precipitation-climatology-project
- https://rda.ucar.edu/datasets/ds728.7/
