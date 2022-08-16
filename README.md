# burn-index-analysis

The Los Angeles Times conducted a geospatial analysis of the burn severity in the Sierra Nevada region with data provided by the Rapid Assessment of Vegetation Condition after Wildfire (RAVG) of the USDA Forest Service. 

Findings
The total area burned in Sierra Nevada in 2021 was 10.6 times that of 2012. In addition, the total area burned at high severity was 22 times greater than in 2012.

3.36 billion square meters of wildfire land lost more than 75% of its canopy coverage last year, while 2.95 billion lost more than 90% of its basal area.

We reprodcued the data cleaning and wrangling process using QGIS and the GRASS plugin (https://grass.osgeo.org/grass78/manuals/r.report.html). The final results, which are saved in the "qgis-grass" folder, are the same as those produced by our scripts.

We also validated our findings by comparing the sizes of two wildfires—the North Complex Fire and the Creek Fire—calculated by our scripts to data provided by the United States Forest Service. The differences between our scripts' results and the numbers from the US Forest Service were less than 5%.

Limitations
The RAVG program evaluates burn severity using regression equations that relate derivatives of Landsat or other similar imagery. Open water, as well as areas obscured by clouds, shadows, active fire, smoke, or snow, were masked and labeled as "unmappable." Furthermore, factors such as delayed mortality, resprouting, the presence of non-tree vegetation, and the occurrence of non-fire disturbances can all contribute to errors in the estimates. The database only contains records for wildland fires reported within the conterminous United States (CONUS) that include at least 1000 acres of forested National Forest System (NFS) land (500 acres for Regions 8 and 9 as of 2016).

Methodology
We began by gathering TIFF data sets from 2012 to 2021 for the standardized composite burn index (CBI), percent change in basal area (BA) and percent change in canopy cover (CC).

The CBI product includes four categories: unchanged, low severity, medium severity and high severity. 

The BA product includes seven categories: 0% loss, loss less than 10%, loss between 10% and 25%, loss between 25% and 50%, loss between 50% and 75%, loss between 75% and 90%, loss more than 90%.

The CC product includes five categories: 0% loss, loss less than 25%, loss between 25% and 50%, loss between 50% and 75%, loss more than 75%. 

The process follows three main paths:
- Clip the burn severity TIFF file with Sierra Nevada's  shapefile using the rasterio package
- Use GDAL to extract and calculate the area size of each category in the TIFF file
- Save the results as dataframes