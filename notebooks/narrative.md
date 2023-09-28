# Updates for Introdcution Geospatial python 

**Context** 
The original course exists of the following components:

|episode|summary|
|----|----|
|0. Summary and Setup | setup for the software |
|1. Introduction to Raster Data | theory about Raster data format |
|2. Introduction to Vector Data | theory about Vector data format |
|3. Coordinate Reference Systems | theory about project coordinate systems|
|4. The Geospatial Landscape | explanation about various tools and why python would be a good idea to use. |
|5. Access satellite imagery using Python | STAC catalogue and data retrieval using python. Based on a xy coordinate an overview is generated on the available satellite images  |
|6. Read and visualize raster data | A series of processing and calculations are provided on the satellite image that is accessed in step 5 |
|7. Vector data in Python | Data about water wells and crop plots are provided on which a couple of vector analyses are performed. Basically, a point in polygon analysis is performed to see which wells are in a crop plot [7.1]. Furthermore, a flipped dataset is corrected but nothing is done with it.|
|8. Crop raster data with rioxarray and geopandas | the vector dataset from 7.1 is cropped and clipped with the dataset from step 5. |
|9. Raster Calculations in Python | NDVI on raster file that was obtained in step 5, resulting in a classification on vegetation density. |
|10. Calculating Zonal Statistics on Rasters | Zonal statistics performed to relate the crop type from brp to the classified NDVI dataset. Before that a vector to raster conversion is performed. |
|11. Parallel raster computations using Dask | parallel raster computation is performed to remove noise from the original image |

After a thorough evaluation of the existing material the following observations were made:

- The various components in the course are good, however not very much related to each other. It lacks coherence.
- The various steps in the workshop can also be done in a GUI (i.e. QGIS, ArcGIS pro etc.), thus GIS experts that would join it would probably assess that 99% of the steps in the workshop could already be done in a GUI (which also has the advantage of being able to explore the data much easier by zooming in and out and being able to very intuitively rearrange the layers in the table of content). The workshop material should thus be updated in such a wy that it shows that strength of coding; rerunning the script with a different configuration (a different region, different time period etc.)
- The used vector data in the workshop it too specific, since it is a subset from a specific Dutch dataportal (i.e. [BRP](https://www.pdok.nl/introductie/-/article/basisregistratie-gewaspercelen-brp-).
 
Based on these observations the following starting points for the update have been formulated:

1.	Show the strength of python in terms of reproducibility of an analysis / process. The learners should develop a script / jupyter notebook which they in the end need to rerun with different configuration steps (different settings/ different location). This will allow them to open their eyes that that is much more effective compared to the click and go tools in a GUI. Also, since we are using libraries outside the ecosystem of the GIS software this goes beyond the model builder tools
2.	Develop a strong narrative and explain why certain steps are taken. This will allow the learners to better understand what they are doing and also why they are doing so. Introducing a tool or an analysis without a purpose is less effective when teaching something.

This led to the following restructuring. 

# Updates

For the narrative we chose to focus on wild fires. Results of large fires, like forest fires or fires on savannah landscapes can be identified on sattelite images. Scorched land leaves a particular signature on satellite images that can automatically be identified. By combining that with data about where people live we can estimate the impact of these large fires on our world, which in theory could also lead to insights on where to take certain mitigation matters. Based on the study of 
[Zhai et al., 2023](https://doi.org/10.3390/f14040807) we also decided to include a calculation of slope classes in our workshop, since they identified a correlation slope and forest fires. As for the study area, we decided to focus a the island of Rhodos around July 2023, when large wild fires occured and around 19.000 people needed to be [evacuated](https://en.wikipedia.org/wiki/2023_Greece_wildfires).  

## Restructering

**Episode 0** (keep)
Setup

**Episode 1-4** (keep) 
For the moment we decided to keep chapters 0 to 4 the way they are (although some updates on the theory would actually be needed, since it contains a couple of false statements).

**Episode 5** Access satellite imagery using Python (keep)
After the setup and theory we start with the access to the satellite images and DEM episode, which is the same as episode 5 from the orginal setup. Here we focus at the island of Rhodos and in particular to July 2023. The satellite image we can get does not cover the whole island. As a nice to have we can lateron update the material to do some merging / mosaicing. The participants will see that the area scorched and will directly see the impact of the wildfire on the island.

**Episode 6**  Vector data in Python *(refactoring of episode 7)*
Once the participants have explored the area we are going to introduce them to vector data in python. We will let them obtain the geometry from Rhodos and use that as a mask to clip the satellite image with. We can either get the data from the build in datasets in geopandas or get them from [GADM](https://gadm.org/download_country.html) the [geopackage](https://geodata.ucdavis.edu/gadm/gadm4.1/gpkg/gadm41_GRC.gpkg) or the [shapefile](https://geodata.ucdavis.edu/gadm/gadm4.1/shp/gadm41_GRC_shp.zip) (level-3). They will first learn how to select a polygon by it's attribute. 

Next, we will download data from OpenStreetMaps, for this various options are available see [https://wiki.openstreetmap.org/wiki/Downloading_data](https://wiki.openstreetmap.org/wiki/Downloading_data) of which [Geofabrik](https://download.geofabrik.de/) is the easiest one. We might lateron consider to include an episode here where we dive into the API in which we configure the download exactly to our area of interest. In the narrative we explain that we want to do this in order to see which infrastructure and build environment were harmed during the wildfire. We will either ask them to download the whole of [Greece](https://download.geofabrik.de/europe/greece.html) or prepare a selection of that dataset. 












