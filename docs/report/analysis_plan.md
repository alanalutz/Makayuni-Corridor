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

Describe the **data sources** and **variables** to be used.
Data sources may include plans for observing and recording **primary data** or descriptions of **secondary data**.
For secondary data sources with numerous variables, the analysis plan authors may focus on documenting only the variables intended for use in the study.

Primary data sources for the study are to include ... .
Secondary data sources for the study are to include ... .

Each of the next subsections describes one data source.

#### Land Cover

**Standard Metadata**

- `Abstract`: A raster of classified landcover for the entire country of Tanzania.
- `Spatial Coverage`: Tanzania
- `Spatial Resolution`: 4.78m
- `Spatial Reference System`: EPSG 3857
- `Temporal Coverage`: 2023
- `Temporal Resolution`: N/A
- `Lineage`: (Song et al 2023)[https://doi.org/10.1016/j.jag.2022.103152]
- `Distribution`: Shared by original authors
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment
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



#### Secondary data source1 name

**Standard Metadata**

- `Abstract`: Buffer region used to avoid edge effects
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Lineage`: Describe and/or cite data sources and/or methodological steps used to create this data source
- `Distribution`: Describe how the data is distributed, including any persistent identifier (e.g. DOI) or URL for data access
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State result of quality assessment or state "Quality unknown"
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Range (Maximum and Minimum) of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |

### Prior observations  

Prior experience with the study area, prior data collection, or prior observation of the data can compromise the validity of a study, e.g. through p-hacking.
Therefore, disclose any prior experience or observations at the time of study pre-registration here, with example text below:

At the time of this study pre-registration, the authors had _____ prior knowledge of the geography of the study region with regards to the ____ phenomena to be studied.
This study is related to ____ prior studies by the authors

For each primary data source, declare the extent to which authors had already engaged with the data:

- [ ] no data collection has started
- [ ] pilot test data has been collected
- [ ] data collection is in progress and data has not been observed
- [ ] data collection is in progress and __% of data has been observed
- [ ] data collection is complete and data has been observed. Explain how authors have already manipulated / explored the data.

For each secondary source, declare the extent to which authors had already engaged with the data:

- [ ] data is not available yet
- [ ] data is available, but only metadata has been observed
- [ ] metadata and descriptive statistics have been observed
- [ ] metadata and a pilot test subset or sample of the full dataset have been observed
- [ ] the full dataset has been observed. Explain how authors have already manipulated / explored the data.

If pilot test data has been collected or acquired, describe how the researchers observed and analyzed the pilot test, and the extent to which the pilot test influenced the research design.

### Bias and threats to validity

Given the research design and primary data to be collected and/or secondary data to be used, discuss common threats to validity and the approach to mitigating those threats, with an emphasis on geographic threats to validity.

These include:
  - uneven primary data collection due to geographic inaccessibility or other constraints
  - multiple hypothesis testing
  - edge or boundary effects
  - the modifiable areal unit problem
  - nonstationarity
  - spatial dependence or autocorrelation
  - temporal dependence or autocorrelation
  - spatial scale dependency
  - spatial anisotropies
  - confusion of spatial and a-spatial causation
  - ecological fallacy
  - uncertainty e.g. from spatial disaggregation, anonymization, differential privacy

### Data transformations

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
