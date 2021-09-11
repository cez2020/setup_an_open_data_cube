# Install and set up an Open Data Cube
* Earth Observation tool that facilitates access and analysis of satellite images.
* Several installation methods and countless datasets can be indexed for analysis.
* This project worked with Sentinel-2 Level-2A images hosted in an AWS Cloud bucket.
* No satellite data was manually downloaded or locally saved.

## Materials
* Data set: Sentinel-2 Level-2A in cloud-optimized GeoTIFF format ([link](https://registry.opendata.aws/sentinel-2-l2a-cogs/)
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
Connect ODC environment to database

## Product definition and Image indexation
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