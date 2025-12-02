---
layout: default
---
# Air–Sea CO₂ Flux Over the Equatorial Pacific: Comparing Atmospheric Constraints

## 1. Project Motivation

Air–sea CO₂ fluxes in the tropics are tightly connected to large-scale circulation, equatorial upwelling, and the strength of the Pacific carbon pump. When trying to quantify surface fluxes, the accuracy of the *airside* CO₂ boundary condition matters just as much as the surface ocean \( pCO_2 \).

Traditionally, many air–sea flux studies use the **NOAA GML Marine Boundary Layer (MBL) CO₂ product**. While the MBL record is extremely stable and well-vetted, it is also *coarse*—heavily smoothed and zonally averaged. This makes it unclear whether the MBL product is appropriate for regions like the equatorial Pacific, where spatial gradients and interannual anomalies are strong.

In this project, I compare atmospheric CO₂ data from **CarbonTracker 2024 (CT2024)**, **MBL**, and **direct in-situ measurements** (mooring and shipboard). My goal is to evaluate whether these different atmospheric constraints meaningfully change the estimated air–sea CO₂ flux.

---

## 2. Core Research Question

**How different are airside CO₂ constraints in the equatorial Pacific when using:**

1. **NOAA GML MBL CO₂ product**
2. **CarbonTracker 2024 xCO₂ fields**
3. **Direct atmospheric measurements** from:
   - TAO/TRITON equatorial moorings  
   - A 2025 research ship transect (adjusted back to a 2024 reference year using Mauna Loa growth rates)

**And do those differences meaningfully change the resulting air–sea CO₂ flux estimates?**

---

## 3. Atmospheric CO₂ Data Sources

### 3.1 NOAA GML MBL Product
- Zonal, smoothed, globally representative surface CO₂.
- Ideal for large-scale climatological work.
- May not capture:
  - regional gradients
  - ENSO-related anomalies
  - upwelling-driven variability in the tropical Pacific

### 3.2 CarbonTracker 2024 (CT2024)
- 3D global atmospheric inversion model.
- Provides 3-hourly xCO₂ fields at relatively high spatial resolution.
- Advantages:
  - Better representation of synoptic variability.
  - Captures transport and surface flux-driven anomalies.
- Limitations:
  - Still a model; transport and flux errors influence results.

### 3.3 TAO/TRITON Mooring CO₂ (Air)
- Direct in-situ atmospheric CO₂ measurements.
- Provides “ground truth” in a region with few atmospheric observations.
- High-frequency, relatively clean boundary-layer signal.

### 3.4 Shipboard Atmospheric CO₂ (2025 → adjusted to 2024)
- Atmospheric xCO₂ measured along a ship transect in early 2025.
- To compare with 2024 datasets, I convert it using the Mauna Loa annual growth rate:

\[
xCO_2^{2024 \; \text{est}} = xCO_2^{2025 \; \text{meas}} - \Delta CO_2^{ML}
\]

- This gives a first-order 2024-equivalent dataset for comparison with CT2024 and MBL.

---

## 4. Methods Overview

### 4.1 Region of Interest
The analysis focuses on the **equatorial Pacific**, approximately:
- **Latitudes:** \(10^\circ S\) to \(10^\circ N\)
- **Longitudes:** \(160^\circ E\) to \(120^\circ W\)

Chosen because:
- Persistent upwelling and degassing  
- Strong atmospheric and oceanic CO₂ gradients  
- Sparse atmospheric measurement availability  

### 4.2 Extracting Atmospheric CO₂

#### CarbonTracker 2024
- Use ERDDAP/NetCDF files.
- Extract surface (or lowest-model-layer) xCO₂.
- Compute weekly or monthly means.

#### NOAA MBL CO₂
- Interpolate MBL zonal values to the region of interest.
- Extract 2024 values only.

#### Moorings
- Clean for flags and humidity corrections.
- Compute daily or weekly averages.

#### Shipboard CO₂
- Clean, QC, and interpolate to ship track coordinates.
- Subtract Mauna Loa annual growth rate to approximate 2024 values.

---

## 5. Analysis Plan

### 5.1 Time Series Comparison
Compare:
- CT2024  
- MBL  
- Moorings  
- Adjusted ship track  

Look for:
- Offsets  
- Anomalies  
- Synoptic variability  
- Interannual differences between 2024 and the 2025-measured track

### 5.2 Spatial Structure
- Map CT2024 fields over the equatorial Pacific.
- Overlay ship track CO₂.
- Compare to smooth MBL zonal means.
- Quantify how much MBL misses east–west gradients.

### 5.3 Flux Sensitivity Analysis

Air–sea CO₂ flux (bulk formula):

\[
F = k \cdot s \cdot \left( pCO_{2}^{ocean} - pCO_{2}^{air} \right)
\]

Where:
- **k** = gas transfer velocity  
- **s** = solubility  
- **pCO₂_air** = depends directly on atmospheric dataset used  

Small differences in air CO₂ (\(1–2\) ppm) can lead to significant changes in the flux, especially in dynamic regions like the equatorial Pacific.

---

## 6. Expected Outcomes

I expect that:

- **MBL will smooth out important gradients** in CO₂.  
- **CT2024 will reflect finer-scale structure** and better match moorings/ship data.  
- **Shipboard CO₂**, even after converting to 2024, will show synoptic variability that MBL cannot capture.  
- The resulting flux differences may be **non-negligible**, especially in upwelling zones.

This should highlight the importance of using higher-resolution atmospheric fields for regional flux studies.

---

## 7. Broader Context

A persistent challenge in air–sea CO₂ work is that:
> *We have excellent ocean carbon measurements, but relatively sparse atmospheric CO₂ observations over the open ocean.*

If CT2024 or in-situ CO₂ significantly outperform MBL in representing the equatorial Pacific atmosphere, it supports:

- Increasing atmospheric measurement density over the ocean  
- Incorporating model-based atmospheric fields into flux programs  
- Revisiting the use of zonally averaged products for regional carbon budgets  

This comparison helps determine which atmospheric datasets provide the most realistic boundary conditions for estimating air–sea fluxes in one of the most important CO₂ outgassing regions on Earth.

---

