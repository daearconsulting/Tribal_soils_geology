# Tribal Soils and Geology

**Author:** Lilly Jones, PhD, Daear Consulting, LLC/CIRES Earth Lab                          
**Primary Focus:** Pine Ridge (Oglala Lakota) and Rosebud (Sicangu Lakota), Oceti Sakowin                    
**License:** Apache 2.0                        

## Overview

This repository provides a modular, reproducible geoscience analysis series
for Pine Ridge and Rosebud Reservations, grounded in Tribal data sovereignty
frameworks. It acquires and visualizes publicly available soils and geology
data, and provides intake frameworks for Tribal-collected field data.

The series is designed for use by PhD geologists, geological engineers, soil
scientists, and Tribal resource managers. Visualizations are accessible to
community members and Tribal decision makers.

## Notebook Series

| Notebook | Topic |
|---|---|
| 01 | Territorial and Geologic Context |
| 02 | Surficial Geology |
| 03 | Bedrock Geology |
| 04 | 3D Geologic Model (Spangler 2024) |
| 05 | Soil Survey — SSURGO |
| 06 | Soil Profiles and Horizons |
| 07 | Geologic Hazards |
| 08 | Aquifer Geology |
| 09 | Data Gaps and Sovereignty |

## 3D Model

**USGS 3D Geological Model of Western South Dakota**
Spangler, L.R., 2024. DOI: [10.5066/P9LK4QHJ](https://doi.org/10.5066/P9LK4QHJ)

A regional-scale volumetric 3D geologic model covering all of western South
Dakota — including Pine Ridge and Rosebud entirely. Contains 25 subsurface
horizon rasters and 35 fault surfaces. Licensed CC0 (public domain).
The stratigraphic column includes the Ogallala Group (Arikaree aquifer),
Pierre Shale, Hell Creek Formation, Madison Group, and 20 additional units.

This dataset has never been visualized in a Tribal land sovereignty context.
Notebook 04 provides cross-sections, depth-to-formation maps, fault
visualization, and isopach maps over Tribal boundaries.

## Data Sources

### Public data (downloaded manually: see below)

| Source | What | Notebooks |
|---|---|---|
| USGS ScienceBase | 3D Geologic Model (Spangler 2024) | 04 |
| USGS mrdata.usgs.gov | South Dakota state geologic map | 02, 03 |
| USDA SSURGO | Soil map units, components, horizons | 05, 06 |
| USGS NWIS | Well logs, groundwater sites | 08 |
| USGS National Map | Elevation (3DEP) | 01 |
| Census TIGER AIANNH | Tribal boundaries | All |
| USGS NHD | Stream network | 01 |

### Tribal-collected data (sensitive data: gitignored)

Field data collected by or in partnership with Tribal natural resource
departments. Lives in `data/raw/` and is never committed to version control.

| Template | What |
|---|---|
| `soil_profile_template.xlsx` | Horizon-by-horizon field soil profiles |
| `well_log_template.xlsx` | Lithologic well logs |
| `field_observation_template.xlsx` | Geologic field notes and measurements |

## Setup

### 1. Download required datasets

**3D Geologic Model** (242 MB GDB — required for notebook 04):
1. Go to https://doi.org/10.5066/P9LK4QHJ
2. Download `WSouthDakota3D.gdb.zip` and `WSD_NonspatialTables.zip`
3. Extract to `data/raw/geology/`

**SSURGO soil data** (required for notebooks 05–06):
1. Go to https://websoilsurvey.nrcs.usda.gov/
2. Use the ESRI Soil Data Downloader https://esri.maps.arcgis.com/apps/instant/basic/index.html?appid=806c857d504c476ba6477ac475c45bf5
3. Download by AREASYMBOL: SD113, SD007, SD063 (Pine Ridge) and SD121, SD095, SD123, SD055 (Rosebud)
4. Extract to `data/raw/ssurgo/`

**South Dakota state geology** (required for notebooks 02–03):
1. Go to https://mrdata.usgs.gov/geology/state/
2. Download South Dakota state geologic map GDB
3. Place in `data/raw/geology/`

### 2. Create and activate the conda environment

```bash
conda env create -f environment.yml
conda activate tribal-soils-geology

python -m ipykernel install --user --name tribal-soils-geology \
    --display-name "Python (tribal-soils-geology)"

jupyter lab notebooks/
```

## Data Sovereignty

This repository implements the following frameworks:

- **OCAP®**: Ownership, Control, Access, Possession
  https://fnigc.ca/ocap-training/
- **CARE Principles**: Collective Benefit, Authority to Control, Responsibility, Ethics
  https://www.gida-global.org/care
- **FAIR Principles**: Findable, Accessible, Interoperable, Reusable
  https://www.go-fair.org/fair-principles/
- **IEEE 2890-2025**: Recommended Practice for Provenance of Indigenous Peoples' Data
  https://standards.ieee.org/ieee/2890/10318/

Federal geological surveys and soil surveys conducted on Pine Ridge and Rosebud
describe the subsurface resources of sovereign Tribal territories. Public data
covering these lands does not transfer authority to federal agencies or
researchers. Tribal-collected field data is governed by OCAP® and is never
committed to version control.

## Adapting for Another Nation

1. Update `config/config.yaml`:  bounding boxes, SSURGO AREASYMBOL codes
2. Update `src/constants.py`: Tribal boundary names, centroids
3. Download SSURGO for your counties
4. Run the notebooks, everything else updates automatically

## Connections to Related Repositories

- **tribal_water_monitoring** Notebook 08 (Aquifer Geology) provides the
  subsurface context for the Arikaree aquifer analysis in that series
- **he_sapa_mining_twin** The Black Hills uplift that structures He Sapa
  also controls the regional dip of formations across Pine Ridge
- **tribal_agricultural_science** Soils data from this series feeds
  land capability and erosion analysis in the agriculture series

