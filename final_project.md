---
layout: default
---
# Air–Sea CO₂ Flux Over the Equatorial Pacific: Comparing Atmospheric Constraints

## 1. Project Motivation

Accurate estimates of air–sea CO₂ flux depend on knowing both the seawater partial pressure of CO₂ and the atmospheric CO₂ concentration just above the ocean surface. While surface ocean measurements have expanded significantly over the past two decades, atmospheric observations over the global ocean—especially across the Pacific—remain extremely sparse. As a result, many air–sea flux studies rely on atmospheric CO₂ products that are either zonally averaged or model-based, rather than built from direct, regionally representative measurements.

Traditionally, the atmospheric CO₂ concentration used in flux calculations is taken from products like the NOAA GML Marine Boundary Layer (MBL) reference surface, which provides a smooth, zonally homogeneous estimate of atmospheric CO₂. These products are stable and well-vetted, but they inevitably smooth out regional variability and may not reflect real atmospheric conditions in dynamic regions such as the equatorial Pacific. This region is strongly influenced by upwelling, large-scale circulation, and interannual climate variability. Without direct measurements, it is difficult to know whether zonally averaged atmospheric products adequately capture the gradients and anomalies that can significantly influence flux estimates.

Ship-based CO₂ systems offer an alternative source of atmospheric information, though they are traditionally optimized for measuring seawater CO₂. These instruments periodically switch to atmospheric sampling for short intervals, yielding limited but valuable snapshots of atmospheric CO₂ along ship tracks. Recent developments—particularly within the Surface Ocean CO₂ Reference Observing Network (SOCONET)—have improved the precision and consistency of shipboard atmospheric measurements through standardized drying procedures, humidity corrections, linearity checks, and the use of stable calibration gases. These high-quality measurements have revealed that discrepancies between different atmospheric CO₂ products can meaningfully alter flux estimates at regional scales.

Given the importance of the equatorial Pacific to the global carbon cycle, and the scarcity of direct atmospheric observations across this basin, it is critical to understand how different atmospheric CO₂ datasets influence calculated fluxes. This project focuses on comparing several atmospheric CO₂ sources for the equatorial Pacific in 2024: the NOAA GML MBL product, CarbonTracker 2024 model output, and in-situ atmospheric measurements from moorings and a 2025 ship track adjusted to a 2024 reference. By examining these differences, this project aims to assess whether commonly used atmospheric CO₂ products provide sufficiently accurate boundary conditions for estimating air–sea CO₂ flux in a region where variability is high and observations are limited.

---

## 2. Core Research Question

Estimating air–sea CO₂ flux requires knowing the difference between seawater \( pCO_{2w} \) and atmospheric \( pCO_{2a} \). This gradient is often expressed as:

\[
F_{\mathrm{CO_2}} = k \cdot s \cdot (pCO_{2w} - pCO_{2a}) = k \cdot s \cdot \Delta pCO_2
\]

where:

- \( F_{\mathrm{CO_2}} \) is the air–sea CO₂ flux,  
- \( k \) is the gas transfer velocity (controlled largely by wind speed),  
- \( s \) is the solubility of CO₂ in seawater,  
- \( \Delta pCO_2 \) is the air–sea CO₂ gradient.

Because the flux term depends directly on the atmospheric CO₂ value, even small biases in \( pCO_{2a} \) can propagate into large errors in calculated CO₂ flux. A difference of just **1–2 ppm** in atmospheric CO₂ corresponds to a **1–2 µatm** shift in \( pCO_2 \), and when this is multiplied by realistic values of \( k \) and \( s \) across a basin-scale area, it can change regional CO₂ flux estimates by **tens of teragrams of carbon (TgC)**. When integrated globally, persistent atmospheric biases of this size can lead to **gigaton-scale errors** in annual flux budgets.

This sensitivity means that the choice of atmospheric CO₂ product is critical—especially over regions like the equatorial Pacific, where strong upwelling and low in-situ atmospheric measurement density make the true atmospheric signal highly variable and difficult to represent with zonally averaged products.

### Research Question

**How do different atmospheric CO₂ datasets influence calculated air–sea CO₂ flux in the equatorial Pacific?**

Specifically:

1. How do 2024 atmospheric CO₂ values differ between  
   - the NOAA GML Marine Boundary Layer (MBL) product,  
   - CarbonTracker 2024 (CT2024), and  
   - direct atmospheric measurements from equatorial Pacific moorings?

2. How well do these products represent the atmospheric conditions encountered along a 2025 ship track (adjusted back to 2024 levels using the Mauna Loa CO₂ growth rate)?

3. Do these differences meaningfully alter calculated air–sea CO₂ flux, and if so, by how much?

Because the flux calculation is directly tied to \( pCO_{2a} \), answering this question is essential for determining whether commonly used atmospheric CO₂ products provide an accurate boundary condition for estimating CO₂ flux in one of the most dynamic and climatically important ocean regions on Earth.

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

