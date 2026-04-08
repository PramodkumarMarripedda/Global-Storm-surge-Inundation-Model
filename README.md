# Storm Surge Inundation Explorer

## Overview

Storm surge, triggered by intense low-pressure systems such as cyclones, causes sea levels to rise and pushes waves inland, leading to widespread coastal inundation.

To model this hazard more accurately, I developed an advanced in-house inundation model that integrates global high-resolution flood heights from GTSR (GTSM + ERA5) and the latest Delta DTM (2024) at 30 m resolution, along with LiDAR-derived DEM at 0.5 m resolution for Hong Kong.

The model incorporates projected sea level rise into probabilistic wave heights for RP100, assessed across SSP1-2.6, SSP2-4.5, and SSP5-8.5 scenarios for the years 2030, 2050, and 2100.

 algorithm improves accuracy by mapping only hydrologically connected inundation zones, eliminating isolated flood pockets. Validation against Climate Central and other open-source datasets confirms the model’s spatial reliability and precision.
 

---

## Key Features

- Integration of GTSR (GTSM + ERA5) global flood heights,RP100 extreme sea level data from Co-DEC ECMWF 
- Climate scenario assessment for SSP1-2.6, SSP2-4.5, and SSP5-8.5
- Future year mapping for 2030, 2050, and 2100
- Integration of GTSR (GTSM + ERA5) global flood heights
- Use of Delta DTM 2024 at 30 m resolution
- Local LiDAR DEM support at 0.5 m resolution for Hong Kong
- Hydrologically connected flood masking to remove isolated pockets
- Validation with Climate Central and open-source coastal flood datasets

---

## Storm Surge and Inundation Concept

Storm surge occurs when storm-driven winds and low pressure lift the sea surface above normal tidal levels. When this elevated water interacts with coastal terrain, it floods low-lying land, creating a fast-moving inundation hazard.

This project maps that process by combining:

- extreme total water levels from ECMWF
- projected sea level rise and wave height influences
- high-resolution coastal elevation data
- connectivity-based inundation filtering using simple bath-tub approach

---

## Methodology

### Data Sources

- **ECMWF total water level** for RP100 coastal flooding for all SSP senarios
- **Delta DTM 2024** at 30 m resolution
- **LiDAR-derived DEM** at 0.5 m resolution (Hong Kong)

### Model Workflow

1. RP 100 YR ECMWF Extreme sea levels (Storm Surge + Sea Level Rise Change + Heighst Astronomical Tide)
2. Map inundation zones where terrain elevation is below the Extreme sea level .
3. Enforce hydrologic connectivity to retain only flood areas linked to the coastline.
4. Generate final inundation maps for each scenario and year.

### Scenario Coverage

- **SSP1-2.6**: low-emission pathway
- **SSP2-4.5**: intermediate pathway
- **SSP5-8.5**: high-emission pathway

Years analyzed:
- 2030
- 2050
- 2100

---

## Model Improvements

The workflow is enhanced beyond a classical bathtub model by using connectivity filtering and multiple elevation sources:

- keeps only coastal flood areas that are hydrologically connected to the sea
- removes isolated inland water pockets unrelated to storm surge
- combines global flood height products with local high-resolution DEM data
- supports probabilistic sea level rise and wave-driven inundation mapping

---

## Validation and Reliability

This project uses open-source comparisons to verify spatial patterns and accuracy.

Validated against:
- Climate Central coastal flood datasets
- other public coastal inundation products




   


