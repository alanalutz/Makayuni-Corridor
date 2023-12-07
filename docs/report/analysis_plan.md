# Makuyuni Wildlife Corridor: Analysis of the Effects of Socioecological Interactions and Changing Land Use on Movement Patterns of Large Mammal Species

## Authors

- Emmanuel H. Lyimo<sup>1</sup>\*, email address, [ORCID link](https://orcid.org/0000-0002-5750-8636)
- Gabriel M. Mayengo<sup>1</sup>, mayengogabriel@gmail.com
- David J. Castico<sup>2</sup>, davidcastico@gmail.com
- Damian Nguma<sup>3</sup>, damiannguma@gmail.com
- Kwaslema M. Hariohay<sup>1</sup>, kwaslema2000@gmail.com
- Alex W. Kisingo<sup>1</sup>, alexkisingo@gmail.com
- Justin Lucas<sup>4</sup>
- Niwaeli Kimambo<sup>4</sup>
- Joseph Holler<sup>4</sup>
- Alana Lutz<sup>4</sup>
- Andy Atallah<sup>4</sup>

<sup>1</sup> College of African Wildlife Management, Mweka. P.O Box 3031, Moshi, Tanzania 

<sup>2</sup>Tanzania People and Wildlife, P.O Box 11306, Arusha, Tanzania

<sup>3</sup> Tanzania Wildlife Research Institute, P.O Box 661, Arusha, Tanzania

<sup>4</sup> Middlebury College, Middlebury, Vermont 05753, USA

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

Hardware: Lenovo ThinkStation
OS: Windows 11 Pro

R Version 2023.06.2+561 (2023.06.2+561)

R Packages:
- groundhog
- raster
- stars
- sf

include citations and versions of these packages

### Data and variables

Secondary data sources for the study are to include land cover, buffer region, merged buildings, initial clip, adjusted study site, bouding box, secondary roads, bomas, and major roads.

Each of the next subsections describes one data source.

#### Land Cover

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
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. 
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.

#### Merged Buildings

- `Abstract`: Microsoft and OSM buildings combined
- `Label`: merged_buildings.shp
- `Spatial Coverage`: 4007553.8440031828358769,-414102.9735587749746628 : 4033053.2097658971324563,-387288.0955167215433903
- `Spatial Reference System`: EPSG 3857
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. 
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.

#### Initial Clip

- `Abstract`: Shapefile used to initially clip landcover map, larger than study area and bounding box
- `Label`: initial clip.shp
- `Spatial Coverage`: 830767.7591739012859762,9581072.9865449033677578 : 862007.9419027733383700,9619914.2523989714682102
- `Spatial Reference System`: EPSG 32736
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. 
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.

#### Adjusted Study Site

- `Abstract`: This is a shapefile for the study site (i.e. the Makuyuni Wildlife Corridor)
- `Label`: adjusted_studysite.shp
- `Spatial Coverage`: The data source pertains to Makuyuni Wildlife Corridor.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 833295.2141958434367552,9588552.1709635984152555 : 858831.0715981726534665,9615078.0293724834918976
- `Spatial Reference System`: EPSG:32736 - WGS 84 / UTM zone 36S - Projected
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas.
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The shapefile is filled with a Simple Fill and has no land cover data.

#### Bounding Box

- `Abstract`: This is a shapefile which was "used to create [a] buffer to prevent edge effects", per Justin Lucas. It extends past the boundaries of adjusted_studysite when the shapefiles are visualized together.
- `Label`: bounding_box.shp
- `Spatial Coverage`: The data source pertains to land surrounding Makuyuni Wildlife Corridor and the corridor itself.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 833295.2141958434367552,9585634.2357019279152155 : 860913.8547548535279930,9617039.8727052193135023
- `Spatial Reference System`: EPSG:32736 - WGS 84 / UTM zone 36S
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas.
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The shapefile is filled with a Simple Fill and has no land cover data.

#### Secondary Roads

- `Abstract`: This is a shapefile which is described as containing "all tracks and roads that were within the study area aside from the two major highways" by Justin Lucas. The shapefile contains line geometries and has 176 total features.
- `Label`: secondary_roads.shp
- `Spatial Coverage`: The data source pertains to land surrounding Makuyuni Wildlife Corridor and the corridor itself.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 4002985.2809690786525607,-417528.5057486270670779 : 4055363.5504161105491221,-386600.4248493338818662
- `Spatial Reference System`: EPSG:3857 - WGS 84 / Pseudo-Mercator
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. Lucas states that this shapefile was sourced from OpenStreetMap.
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: Roads are filled with a Simple Fill and there are no associated land cover data.

#### Bomas

- `Abstract`: This is a shapefile which ostensibly contains locations of bomas, or livestock enclosures, within the wildlife corridor.
- `Label`: bomas.shp
- `Spatial Coverage`: The data source pertains to land within the wildlife corridor.
- `Spatial Extent`: 4007605.1797135984525084,-412580.2386067652842030 : 4032954.7106412472203374,-387445.8448925596894696
- `Spatial Reference System`: EPSG:3857 - WGS 84 / Pseudo-Mercator
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. 
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: Bomas are filled with a Simple Fill and there are no associated land cover data.

#### Major Roads

- `Abstract`: This is a shapefile which contains "two highways that run through the study area", per Justin Lucas.
- `Label`: major_roads_vector.shp
- `Spatial Coverage`: The data source pertains to the entirety of the extent of the highways, which extend far past the study site and outside of Tanzania to the north and south.
- `Spatial Extent`: 24.9389406999999999,-33.9686420999999967 : 36.7868238000000005,-1.4968789000000000
- `Spatial Reference System`: EPSG:4326 - WGS 84
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. Lucas states that this shapefile is sourced from OpenStreetMap. 
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The highways are filled with a Simple Fill and there are no associated land cover data.

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

The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.

## Acknowledgements

- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References
