# Implementation of an Open Data Cube for Processing Sentinel-2 Data
* A data cube is a multidimensional data structure
* Open Data Cube facilitates access and broadens the use of satellite imagery
* Free and open-source software built upon a series of Python libraries and a database connection
* Sentinel-2 Level-2A (bottom of atmosphere reflectance) cloud-hosted images: atmospheric corrections, free access, and global coverage
* Thousands of cloud-optimized Sentinel-2 images were indexed into ODC database
* Sentinel-2 data was retrieved from the cloud and into local environment
* Popular EO products such as water and vegetation indexes were generated within ODC environment writing Python code in Jupyter Notebook

## Materials
* Data set: Sentinel-2 Level-2A in cloud-optimized GeoTIFF format ([link](https://registry.opendata.aws/sentinel-2-l2a-cogs/))
* System: Windows
* Python 3.7
* Installation method: Anaconda
* Software: ([Open Data Cube](https://www.opendatacube.org/)) (free and open-source software)
* ODC Documentation: ([link](https://datacube-core.readthedocs.io/en/latest/))
* Database: PostgreSQL (in PGAdmin 4)
* Sentinel-2 GeoTIFF indexing ([tool](https://github.com/opendatacube/datacube-dataset-config/blob/main/sentinel-2-l2a-cogs.md))

## Installation & setup
```bash
> conda create name cubeenv python=3.7 datacube
> activate cubeenv
> conda install jupyter matplotlib scipy
```
Connect ODC environment to database (See [configuration_file](https://datacube-core.readthedocs.io/en/latest/ops/db_setup.html))

## Product definition and Image indexation
Sentinel-2 Level-2A Cloud-optimized GeoTIFF product definition file ([link](https://github.com/opendatacube/datacube-dataset-config/blob/main/products/s2_l2a.odc-product.yaml))  

Sentinel-2 GeoTIFF indexing ([tool](https://github.com/opendatacube/datacube-dataset-config/blob/main/sentinel-2-l2a-cogs.md))

Product definition
```bash
> datacube product add s2_l2a.odc-product.yaml
```

Sample indexation command
```bash
> stac-to-dc
--bbox 72.428, 13.341, 68.652, 9.906
--collections=sentinel s2 l2a cogs
--datetime=2020 01 01/2020 12 31
```
Spatial extent of indexed images

![img1](/img/odc_extent_mad_dios.png)

## Product generation and visualization
See Jupyter Notebook file for code
Visualizations may be displayed within ODC environment  
OR  
After exporting Tiff files for analysis elsewhere.  
The following images were generated in QGIS:  

RGB
![img2](/img/maldonado_rgb_2.png)

False color
![img3](/img/maldonado_false_color_2.png)

NDVI
![img4](/img/maldonado_ndvi_2.png)

NDWI
![img5](/img/maldonado_ndwi_2.png)

MNDWI
![img6](/img/maldonado_mndwi_2.png)

MDCI
![img7](/img/maldonado_ndci_2.png)