# Stavanger Marine Habitat Suitability and Biodiversity Hotspot Mapping

## Overview

This project demonstrates a fully automated Python-based GIS workflow for marine habitat suitability modelling, habitat richness analysis, and biodiversity hotspot mapping in Stavanger Municipality, Norway.

The workflow uses environmental raster datasets to identify potentially suitable areas for 21 marine habitat types and to map areas with high habitat richness and biodiversity value.

All analyses were performed using Python and open-source geospatial libraries, including GeoPandas, Rasterio, NumPy, Matplotlib, PySAL, and ESDA.

---

## Study Area

**Location:** Stavanger Municipality, Norway

The analysis was restricted to marine areas between **0 and 30 meters depth**, representing the primary study area for habitat suitability modelling.

---

## Project Objectives

- Automatically select a municipality from a national municipality dataset.
- Generate an Area of Interest (AOI) based on the 0–30 m marine depth zone.
- Clip environmental variables to the AOI.
- Align all raster datasets to a common CRS, extent, and resolution.
- Generate habitat suitability models for 21 marine habitat types.
- Create habitat richness maps.
- Generate a final biodiversity hotspot map.
- Demonstrate a fully automated Python GIS workflow.

---

# Environmental Variables

The following environmental variables were used as habitat predictors:

- Bathymetry
- Slope
- Wave Exposure
- Grain Size / Substrate
- Light Attenuation

---

## Bathymetry

Bathymetry represents seabed depth.

| Depth Range | Interpretation |
|-------------|---------------|
| 0 m | Sea surface |
| -1 to -10 m | Shallow marine zone |
| -10 to -30 m | Deeper marine zone |
| Less than -30 m | Excluded from analysis |

Only marine areas between 0 and 30 meters depth were included in habitat modelling.

---

## Slope

Slope was derived directly from the bathymetry raster and describes seabed steepness.

| Slope (Degrees) | Interpretation |
|----------------|---------------|
| 0–5 | Flat Seabed |
| 5–10 | Gently Sloping |
| 10–20 | Moderately Steep |
| >20 | Steep Seabed |

---

## Wave Exposure

Wave exposure represents the influence of wave action on the seabed.

| Value | Exposure Class |
|---------|--------------|
| 1 | Very Sheltered |
| 2 | Sheltered |
| 3 | Moderately Sheltered |
| 4 | Moderately Exposed |
| 5 | Exposed |
| 6 | Very Exposed |

Examples:

- Low wave exposure values (1–2) represent protected bays and sheltered coastal areas.
- High wave exposure values (5–6) represent exposed coastlines and wave-dominated environments.

---

## Grain Size / Substrate

The original sediment dataset was reclassified into four substrate classes.

| Class | Description |
|---------|-------------|
| 1 | Hard Bottom / Bedrock |
| 2 | Mud |
| 3 | Sand |
| 4 | Coarse Sediment (Gravel, Stones, Boulders) |

Examples:

- Kelp habitats typically occur on hard substrates (1 and 4).
- Seagrass habitats typically occur on soft substrates (2 and 3).

---

## Light Attenuation

Light attenuation describes how rapidly light decreases through the water column.

| Value | Interpretation |
|---------|--------------|
| Lower Values | Higher Light Availability |
| Higher Values | Lower Light Availability |

Light availability was used to constrain habitat suitability for vegetation-forming habitats such as kelp forests and seagrass communities.

---

# Habitat Groups

## Kelp Habitats

- NT03 Tangsamfunn
- NT14 Sukkertareskog
- NT16 Stortareskog
- NT18 Fingertareskog
- NT20 Butareskog
- NT21 Ruglbunn

---

## Seagrass and Coastal Vegetation Habitats

- NT09 Marin tidevannssump
- NT10 Ålegrasbunn
- NT11 Dvergålegrasbunn
- NT13 Brakkvanns-undervannseng
- NT32 Pusleplantebunn

---

## Shell Habitats

- NT02 Blåskjellbunn
- NT07 Flatøstersbunn
- NT08 O-skjellbunn

---

## Topography Habitats

- NT01 Litoralbassengbunn
- NT04 Litoral bergvegg
- NT05 Tidevannsmudderflate
- NT06 Sublitoral grunn sandbunn
- NT22 Litorale grotter og overheng
- NT29 Sublitoral bergvegg
- NT30 Sterke tidevannsstrømmer

---

# Habitat Suitability Modelling

Habitat suitability models were generated using logical combinations of environmental conditions.

Example:

```text
Bathymetry
+
Slope
+
Wave Exposure
+
Grain Size
+
Light Attenuation
=
Suitable Habitat
```

Output values:

| Value | Meaning |
|---------|---------|
| 0 | Unsuitable |
| 1 | Suitable |

Each habitat type was generated as an independent binary suitability raster.

---

# Habitat Richness Analysis

Habitat richness maps were produced by summing binary habitat suitability maps within each habitat group.

Richness maps created:

- Kelp Richness
- Seagrass Richness
- Shell Richness
- Topography Richness

Interpretation:

| Richness Value | Meaning |
|---------|--------|
| 0 | No Suitable Habitat |
| 1 | One Suitable Habitat |
| 2 | Two Overlapping Habitats |
| 3+ | Multiple Overlapping Habitats |

Areas with higher richness values indicate locations where multiple habitat types may coexist.

---

# Biodiversity Hotspot Mapping

A final biodiversity hotspot map was created by combining:

- Kelp Richness
- Seagrass Richness
- Shell Richness
- Topography Richness

The resulting hotspot map highlights areas with high potential habitat diversity and ecological importance.

Higher hotspot values indicate:

- Greater habitat diversity
- More overlapping habitat types
- Higher ecological value

---

# Workflow

```text
Municipality Selection
            ↓
Create AOI (0–30 m)
            ↓
Clip Environmental Variables
            ↓
Align Raster Datasets
            ↓
Generate Slope Layer
            ↓
Create 21 Habitat Suitability Models
            ↓
Generate Richness Maps
            ↓
Create Biodiversity Hotspot Map
```

---
# Results
## Habitat Richness Maps


<img width="3581" height="3569" alt="Richness_Maps" src="https://github.com/user-attachments/assets/0c26e625-8c25-4d86-8112-1363b3754e97" />

**Figure 1.** Habitat richness maps for kelp, seagrass, shell, and topography habitat groups.

---

## Final Habitat Hotspot Map


 <img width="2656" height="2970" alt="Final_Habitat_Hotspot" src="https://github.com/user-attachments/assets/dbcc7079-9061-4628-a9e3-6096d569c817" />

**Figure 2.** Final biodiversity hotspot map showing areas with high potential habitat diversity.


# Python Libraries Used

- GeoPandas
- Rasterio
- NumPy
- Matplotlib
- Pandas
- Shapely
- PySAL (LibPySAL)
- ESDA

---

# Automation Components

The workflow was designed as a fully automated Python GIS process.

Automated tasks include:

- Municipality Selection
- AOI Generation
- Raster Clipping
- Raster Alignment
- Slope Derivation
- Habitat Suitability Modelling
- Richness Mapping
- Hotspot Mapping
- Raster Export

---

# Skills Demonstrated

## GIS Skills

- Raster Analysis
- Habitat Suitability Modelling
- Marine Spatial Analysis
- Biodiversity Mapping
- Habitat Richness Assessment
- Environmental Modelling
- Spatial Data Processing
- Marine GIS

---

## Python Skills

- GeoPandas
- Rasterio
- NumPy
- Matplotlib
- Spatial Data Automation
- Raster Processing
- File Management Automation
- Scientific Computing

---

## GIS Automation Skills

- Fully Automated GIS Workflow
- Reproducible Spatial Analysis
- Raster Workflow Automation
- AOI Generation Automation
- Environmental Data Processing
- Habitat Modelling Automation
- Biodiversity Assessment Automation

---

# Data Sources

## Municipality Boundaries

**Source:**  
https://kartkatalog.geonorge.no/metadata/administrative-enheter-kommuner/041f1e6e-bdbc-4091-b48f-8a5990f3cc5b 

---

## Bathymetry

**Source:**  
https://kartkatalog.geonorge.no/metadata/dybdedata-terrengmodeller-50-meters-grid/67a3a191-49cc-45bc-baf0-eaaf7c513549 


---

## Wave Exposure

**Source:**  
https://dataleveranser.miljodirektoratet.no/nedlasting/44121089-26b2-4a64-bec6-15926a77d14d/ 

---

## Marine Sediment / Grain Size Data

**Source:**  
https://kartkatalog.geonorge.no/metadata/seabed-sediments-grain-size-detailed/79f0f17d-9f62-456d-b1a9-2a8c754c51c4 
---

## Light Attenuation

**Source:**  
https://emodnet.ec.europa.eu/geoviewer/ 

---

# Repository Structure

```text
fully-python-marine-habitat-automation/
│
├── README.md
│
├── notebook/
│   └── Stavanger_Habitat_Automation.ipynb
│
├── images/
│   ├── Richness_Maps.png
│   ├── Final_Habitat_Hotspot.png
│
├── suitability_analysis/
│   ├── Kelp/
│   ├── Seagrass/
│   ├── Shell/
│   └── Topography/
│
├── richness/
│   ├── Kelp_Richness.tif
│   ├── Seagrass_Richness.tif
│   ├── Shell_Richness.tif
│   ├── Topography_Richness.tif
│   └── Final_Habitat_Hotspot.tif
│
└── outputs/
```

---

# Key Achievements

- Developed a fully automated Python GIS workflow.
- Generated 21 marine habitat suitability models.
- Created habitat group richness maps.
- Produced a biodiversity hotspot map for Stavanger Municipality.
- Automated raster processing and habitat modelling workflows.
- Demonstrated reproducible marine spatial analysis using open-source GIS tools.

---

# Author

**Arjuman Banu**

GIS | Python | Spatial Analysis | Environmental Modelling | Marine Habitat Mapping
