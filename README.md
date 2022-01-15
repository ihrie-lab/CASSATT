# CASSATT - Cyclic Analysis of Single-Cell Subsets and Tissue Territories

This repository contains the Python implementation of CASSATT, a workflow designed to streamline cyclic immunohistochemistry data analysis. This is described in the following paper: 

PAPER LINK.

## Overview

Cyclic immunohistochemistry utilizes sequential rounds of colorimetric immunostaining and imaging to quantitatively map cells of interest. This technique can be used to uncover spatial relationships between different cellular subpopulations found within a given tissue specimen. CASSATT automates immunohistochemistry data analysis by 1) achieving tissue-level and cell-level registration across imaging rounds and 2) providing modular options for downstream neighborhood analysis. The following figure provides a graphical summary of the pipeline.

![pipeline_overview](images/pipeline_overview.png)

## Directory Structure

Under `notebooks`, one can find interactive jupyter notebooks containing the original source code. Specifically, `mxihc_pipeline_FULL.ipynb` registers and tiles tissue specimens to ultimately generate single-cell readout measurements. `neighborhood_and_odds_ratios_FULL.ipynb` serves to analyze the previously generated single-cell expression data, including detection of cell subsets and calculation of log odds ratios of interactions between gated populations. 

In order to run CASSATT, the input directory should be structured as seen down below. Consistent naming should be utilized across biomarkers for each individual tissue specimen and sample names should only contain alphanumeric characters:

```
input_directory
├── marker1
│   ├── Sample1.scn
│   ├── Sample2.scn
├── marker2
│   ├── Sample1.scn
│   ├── Sample2.scn
└── marker3
    ├── Sample1.scn
    ├── Sample2.scn
```

The resulting output directory structure after running `mxihc_pipeline_FULL.ipynb` is depicted below. Development mode allows the user to confirm the pipeline is working as expected. Batch mode allows the user to run the workflow on multiple slides simultaneously.

```
├── output_directory
│   ├── BaseAligned
│   ├── BaseImages
│   ├── CroppedStacks
│   ├── Labels
│   ├── Plots
│   ├── StitchedSlides
│   └── Tiled
├── OutputSample1_export.csv
├── OutputSample2_export.csv
└── OutputSample3_export.csv
```

The resulting output directory structure after running `neighborhood_and_odds_ratios_FULL.ipynb` is as follows:

```
figures
└── Neighborhood
    ├── Gated_Input
    ├── Gated_Perslide
    ├── LogOdds
    │   └── Interactions
    │       ├── Slide
    │       └── Tile
    ├── Neighbor_CSVs
    ├── Neighborhood_Plots
    │   └── Per_Slide
    └── Neighborhood_Umap_CSVs
```


## Installation & Usage (TODO)

Currently, the code is being refactored to be installable via pip. More details will follow as to how to properly install the package; additional code files will be posted.
