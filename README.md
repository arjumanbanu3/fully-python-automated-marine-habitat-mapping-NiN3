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
-
