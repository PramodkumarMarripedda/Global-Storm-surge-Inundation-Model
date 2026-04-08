# Storm Surge Inundation Explorer

## 🌊 What is Storm Surge?

Storm surge is the abnormal rise in sea level caused by strong wind and low atmospheric pressure from intense storms such as cyclones and tropical depressions. When these systems move near the coast, they push ocean water inland, producing coastal flooding and potentially devastating inundation.

> Storm surge = elevated sea level + waves + wind-driven water pushed onshore.

```text
      Offshore storm
          ↓
  Low pressure center
      ↙   ↘
  Wind-driven water surge
       → coastal inundation
```

---

## 🧠 Project Summary

This repository demonstrates a simplified storm surge inundation workflow using ECMWF total water level data and a bathtub-style mapping approach across climate scenarios.

Key features:
- Uses a simple bathtub inundation model for coastal mapping
- Applies ECMWF total water level data for 100-year return period (RP100)
- Evaluates climate projections for SSP1-2.6, SSP2-4.5, and SSP5-8.5
- Includes future years: 2030, 2050, and 2100
- Combines global and local elevation products for better accuracy

---

## 🧭 Methodology

### 1. Data Inputs
- **ECMWF Total Water Level** for extreme event mapping
- **GTSR / GTSM + ERA5** high-resolution global flood height dataset
- **Delta DTM 2024** at 30 m resolution
- **LiDAR DEM (Hong Kong)** at 0.5 m resolution

### 2. Modeling Approach

The workflow is based on a bathtub inundation concept, enhanced with hydrologic connectivity to avoid isolated ponds.

```text
  [Extreme sea level] + [SLR adjustment] + [wave height] = inundation threshold

  Inundation mapping process:
   1) apply total water level to coastal DEM
   2) flood from coast inland where elevation < threshold
   3) retain only connected cells linked to the shoreline
```

### 3. Climate Scenario Mapping
- **RP100**: 100-year return period extreme water level
- **SSP1-2.6**: low-emissions pathway
- **SSP2-4.5**: moderate pathway
- **SSP5-8.5**: high-emissions pathway

```text
         Year      SSP1-2.6    SSP2-4.5    SSP5-8.5
         2030        ✓           ✓           ✓
         2050        ✓           ✓           ✓
         2100        ✓           ✓           ✓
```

---

## 📈 Notebook-style Graphics

### Storm Surge Concept

```text
   Storm center
       ⬇
    _________         Coastal floodplain
   /         \         ____________
  |  cyclone  |------>   inundation
   \_________/
        ↑
    low pressure
```

### Methodology Diagram

```text
  [ECMWF total water levels]   [Sea level rise scenarios]
                 \                 /
                  \               /
                   [Combined water threshold]
                            |
                            v
                  [DEM elevation grid layers]
                            |
                            v
               [Hydrologically connected flood mask]
                            |
                            v
                 [Mapped inundation for RP100]
```

---

## 🔧 Model Improvements

Our enhanced in-house inundation workflow improves accuracy by:
- mapping only **hydrologically connected inundation zones**
- removing isolated flood pockets not connected to the sea
- integrating both **global flood products** and **high-resolution local DEMs**
- using projected sea level rise together with extreme wave conditions

---

## ✅ Validation

Model outputs are validated with open-source references such as Climate Central and other publicly available coastal flood datasets to confirm spatial reliability and precision.

---

## 📁 Repository Structure

- `Download_data/` — raw input data references and notes
- `Sample_Results/` — example output maps and summaries
- `Scripts/` — analysis notebooks and processing code

---

## 💡 Notes

This README is designed in an LLM-notebook style with simplified diagrams and conceptual graphics. Replace the ASCII illustrations with real figures in future versions if desired.
