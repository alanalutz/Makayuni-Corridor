# Makuyuni Wildlife Corridor: Analysis of the Effects of Socioecological Interactions and Changing Land Use on Movement Patterns of Large Mammal Species

## Authors

- Emmanuel H. Lyimo\*, lyimo.emanuel@gmail.com, @githubname, ORCID: 0000-0002-5750-8636, College of African Wildlife Management, Mweka. P.O Box 3031, Moshi, Tanzania
- Gabriel M. Mayengo, mayengogabriel@gmail.com, College of African Wildlife Management, Mweka. P.O Box 3031, Moshi, Tanzania
- David J. Castico, 

\* Corresponding author and creator

## Abstract

This study is a reproduction of unpublished research by Emmanual H Lyimo et al (2023), titled: Makuyuni Wildlife Corridor: Analysis of the Effects of Socioecological Interactions and Changing Land Use on Movement Patterns of Large Mammal Species.
The original study evaluated the connectivity of Makuyuni Wildlife Corridor, a stretch of unprotected land between Tarangire National Park and Essmingor National Forest Reserve in Tanzania.
We reproduce the first part of the study, a multifactor analysis model that approximates cost of movement through the corridor based on least cost pathway analysis.
The study was originally conducted using the QGIS Model Builder, and we reproduce the workflow in R.
The goal of the study is to reproduce the authors' map displaying the minimum cost of movement through each point in the study area, compare the reproduced map to the original map, and evaluate why the reproduction may differ from the original.

## Study Metadata

- `Key words`: multifactor analysis, least cost pathway, wildlife corridor, movement cost, Makayuni, Tarangire, Essmingor, Tanzania
- `Subject`: Social and Behavioral Sciences: Geography: Nature and Society Relations
- `Date created`: 11-30-2023
- `Date modified`: 11-30-2023
- `Spatial Coverage`: Makayuni Wildlife Corridor, Tanzania
- `Spatial Resolution`: 10m
- `Spatial Reference System`: EPSG 32736
- `Temporal Coverage`: 2023
- `Temporal Resolution`: N/A
- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant

#### Original study spatio-temporal metadata

Because this is a reproduction study, the original study spatio-temporal metadata is identical to the study metadata.

## Study design

This study is a reproduction of an original observational study that created a cost surface of wildlife movement in Makayuni Wildlife Corridor.
We aim to reproduce the original study's Figure 5, a map of the cost surface, in the R computational environment rather than the QGIS Model Builder environment used by the original authors.
The null hypothesis is that there are no differences between the reproduced cost surface map and the original cost surface map.
The alternative hypothesis is that there are differences between the reproduced cost surface map and the original cost surface map.
We will test this hypothesis by visually comparing the two maps after standardizing to the same color range.

## Materials and procedure

We are using the original study data, metadata, workflow, and QGIS Model shared by the original authors.
We will reproduce the author's original methodology as closely as possible using an R script, using the same data.

### Computational environment

R
RStudio
groundhog
raster
stars
sf

Define the hardware, operating system, and software requirements for the research.
Include citations to important software projects, plugins or packages and their versions.

### Data and variables

Secondary data sources for the study are to include land cover, buffer region, merged buildings, initial clip, major roads, secondary roads, bomas, bounding box, and adjusted study site.

Each of the next subsections describes one data source.

#### Land Cover

**Standard Metadata**

- `Abstract`: A raster of classified landcover for the entire country of Tanzania.
- `Label`: landcover.tif
- `Spatial Coverage`: Tanzania
- `Spatial Resolution`: 4.78m
- `Spatial Reference System`: EPSG 3857
- `Temporal Coverage`: 2023
- `Lineage`: (Song et al 2023)[https://doi.org/10.1016/j.jag.2022.103152]
- `Distribution`: Shared by original authors
- `Bands`: 1
  - `Label`: Landcover
  - `Definition`: Classified landcover type using satellite imagery
  - `Type`: integer
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: 0-8
  - `Values`:
      - 1 (orange): cropland
      - 2 (dark green): forest/dense tree
      - 3 (light green): grassland
      - 4 (green): shrubland
      - 5 (blue): water
      - 6 (gray): built-up
      - 7 (yellow): bareland
      - 8 (teal): wetlands

#### Buffer Region

- `Abstract`: Buffer region used to avoid edge effects
- `Label`: buffer_region.shp
- `Spatial Coverage`: 833295.2141958434367552,9585634.2357019279152155 : 860913.8547548535279930,9617039.8727052193135023
- `Spatial Reference System`: EPSG 32736
- `Distribution`: Shared by original authors

#### Merged Buildings

- `Abstract`: Microsoft and OSM buildings combined
- `Label`: merged_buildings.shp
- `Spatial Coverage`: 4007553.8440031828358769,-414102.9735587749746628 : 4033053.2097658971324563,-387288.0955167215433903
- `Spatial Reference System`: EPSG 3857
- `Distribution`: Shared by original authors

#### Initial Clip

- `Abstract`: Shapefile used to initially clip landcover map, larger than study area and bounding box
- `Label`: initial clip.shp
- `Spatial Coverage`: 830767.7591739012859762,9581072.9865449033677578 : 862007.9419027733383700,9619914.2523989714682102
- `Spatial Reference System`: EPSG 32736
- `Distribution`: Shared by original authors

### Prior observations

At the time of this study pre-registration, the authors had no prior knowledge of the geography of the study region with regards to the phenomena to be studied.
This study is related to not prior studies by the authors

For each data source, the authors have observed the layers and their metadata in QGIS.

### Bias and threats to validity

There are several possible geographic threats to validity in a wildlife corridor analysis.
The primary threat is boundary distortion, also known as edge effects.
This issue may be addressed by using a buffer region around the study area, and assigning this buffer a high cost.
This method will prevent unrealistic low-cost pathways from forming around the edge of the study area.

A second threat is space-time interactions.
Wildlife movement patterns and landscape characteristics can change over time, especially over the course of a year, due to seasonal variations.
Corridor analyses that do not take into account temporal considerations may not accurately capture these dynamics.
This threat to validity will be difficult to address without additional temporal data that accounts for changing movement behaviors or landscape characteristics.

### Data transformations

- Reproject all layers to a common CRS (EPSG 32736)
- Rasterize all shapefiles
- Clip all layers to 
Describe all data transformations planned to prepare data sources for analysis.
This section should explain with the fullest detail possible how to transform data from the **raw** state at the time of acquisition or observation, to the pre-processed **derived** state ready for the main analysis.
Including steps to check and mitigate sources of **bias** and **threats to validity**.
The method may anticipate **contingencies**, e.g. tests for normality and alternative decisions to make based on the results of the test.
More specifically, all the **geographic** and **variable** transformations required to prepare input data as described in the data and variables section above to match the study's spatio-temporal characteristics as described in the study metadata and study design sections.
Visual workflow diagrams may help communicate the methodology in this section.

Examples of **geographic** transformations include coordinate system transformations, aggregation, disaggregation, spatial interpolation, distance calculations, zonal statistics, etc.

Examples of **variable** transformations include standardization, normalization, constructed variables, imputation, classification, etc.

Be sure to include any steps planned to **exclude** observations with *missing* or *outlier* data, to **group** observations by *attribute* or *geographic* criteria, or to **impute** missing data or apply spatial or temporal **interpolation**.

### Analysis

Describe the methods of analysis that will directly test the hypotheses or provide results to answer the research questions.
This section should explicitly define any spatial / statistical *models* and their *parameters*, including *grouping* criteria, *weighting* criteria, and *significance thresholds*.
Also explain any follow-up analyses or validations.

## Results

Describe how results are to be presented.

## Discussion

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

Include an integrity statement - The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.
If a prior registration *does* exist, explain the rationale for revising the registration here.

## Acknowledgements

- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References
