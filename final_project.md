---
layout: default
---
# Air–Sea CO₂ Flux Over the Equatorial Pacific: Comparing Atmospheric Constraints

## 1. Project Motivation

Accurate estimates of air–sea CO₂ flux depend on knowing both the seawater partial pressure of CO₂ and the atmospheric CO₂ concentration directly above the ocean surface. While surface ocean CO₂ measurements have expanded over the past two decades, atmospheric observations over the global ocean—especially the Pacific—remain extremely sparse. Because of this, many flux calculations rely on atmospheric products that are zonally averaged or model-based rather than derived from direct, regionally representative measurements.

Flux studies often use the NOAA GML Marine Boundary Layer (MBL) product, which provides a smooth, zonally homogeneous reference surface for atmospheric CO₂. These fields are stable and well-vetted, but they inevitably smooth out regional variability and may not reflect real atmospheric conditions in dynamic environments like the equatorial Pacific—a region shaped by strong upwelling, large-scale circulation, and interannual anomalies. Without direct observations, it’s difficult to know whether these zonally averaged products capture the gradients that meaningfully influence flux estimates.

Because the equatorial Pacific plays an outsized role in the global carbon cycle—and because atmospheric observations across this basin are so limited—it is essential to understand how different atmospheric datasets shape flux estimates. This project compares three atmospheric CO₂ sources for the equatorial Pacific in 2024: the NOAA GML MBL product, CarbonTracker 2024 model output, and in-situ atmospheric measurements from a 2025 ship track adjusted to a 2024 reference. In this context, a high-quality, high-resolution atmospheric measurement system installed alongside an existing pCO₂ system can provide crucial boundary-layer information in regions where observations are sparse, helping resolve subtle gradients that significantly affect calculated flux. By examining these differences, the goal is to assess whether commonly used atmospheric CO₂ products provide sufficiently accurate boundary conditions for flux estimates in one of the most variable—and under-observed—regions of the global ocean.

---

## 2. Core Research Question

Estimating air–sea CO₂ flux requires knowing the difference between seawater (pCO₂₍w₎) and atmospheric (pCO₂₍a₎) CO₂. This gradient is often written as:

$$
F_{\mathrm{CO_2}} = k \cdot s \cdot (pCO_{2w} - pCO_{2a}) = k \cdot s \cdot \Delta pCO_2
$$

where:

- **F<sub>CO₂</sub>** is the air–sea CO₂ flux,  
- **k** is the gas transfer velocity (largely controlled by wind speed),  
- **s** is the solubility of CO₂ in seawater,  
- **ΔpCO₂** is the air–sea CO₂ gradient.

Because the flux depends directly on atmospheric CO₂, even small biases in pCO₂₍a₎ can produce large uncertainties in the resulting flux. A difference of just **1–2 ppm** in atmospheric CO₂ corresponds to a **1–2 µatm** shift in ΔpCO₂. When applied across realistic values of k and s over a basin-scale region such as the equatorial Pacific, this can change CO₂ flux estimates by **tens of teragrams of carbon (TgC)**. Over global scales and multiple years, persistent biases of this size can accumulate into **gigaton-scale errors** in annual CO₂ budgets.

This sensitivity makes the choice of atmospheric CO₂ dataset critical. In the equatorial Pacific—where upwelling, circulation, and climate variability create strong gradients—using zonally averaged products may obscure important structure in pCO₂₍a₎ and lead to inaccurate flux estimates.

**Research question:**  

How do different atmospheric CO₂ datasets influence calculated air–sea CO₂ flux in the equatorial Pacific?

Specifically:

1. How do 2024 atmospheric CO₂ values differ between  
   - the NOAA GML Marine Boundary Layer (MBL) product,  
   - CarbonTracker 2024 (CT2024) 

2. How well do these products represent the atmospheric conditions encountered along a 2025 ship track, after adjusting those measurements back to 2024 levels using the Mauna Loa CO₂ growth rate?

3. To what extent do the resulting differences in \( pCO_{2a} \) change calculated air–sea CO₂ flux, and are those differences large enough to matter for regional or global carbon budgets?

---
### **Preliminary Data**

- In early 2025, I measured high-frequency atmospheric CO₂ with a Picarro analyzer onboard the ro-ro ship **M/V *Tysla*** during its transit across the equatorial Pacific.

- To compare these 2025 observations with **2024 atmospheric CO₂ products** (NOAA MBL and CarbonTracker PBL CO₂), I estimated what the shipboard CO₂ values *would have been* in 2024.

- I used the **Mauna Loa 2024 annual growth rate**:  
  `ΔCO2_MLO,2024 = 3.33 ± 0.11 ppm`

- For each ship measurement, I created a *“2024-equivalent”* atmospheric CO₂ value by subtracting this growth rate:  
  `CO2_ship,2024_equiv = CO2_ship,2025 − 3.33 ppm`

- I also shifted the 2025 day-of-year by **–1** to align with the 2024 seasonal cycle (since 2024 was a leap year).










## 3. Atmospheric CO₂ Data Sources

### 3.1 NOAA GML MBL Product
- A zonally averaged, smoothed reference surface CO₂ product.
- Derived from a global network of marine flask and in-situ sites.
- Traditonally used for large-scale climatological work.

### 3.2 CarbonTracker 2024 (CT2024)
- A 3D global atmospheric inversion model that simulates CO₂ concentration fields.
- Provides 3-hourly xCO₂ at relatively high spatial resolution.

### 3.3 TAO/TRITON Mooring Atmospheric CO₂
- Direct, in-situ atmospheric CO₂ measurements from equatorial moorings.
- Typically collected using non-dispersive infrared (NDIR) or related low-frequency sensors.
- Measurement resolution is lower than shipboard Picarro systems.
- Provides long-term, stable boundary-layer measurements.


### 3.4 Shipboard Atmospheric CO₂ (Picarro; 2025 → adjusted to 2024)
- Atmospheric xCO₂ measured using a high-precision Picarro cavity ring-down spectrometer (CRDS) G2301.
- Picarro provides:
  - High sampling frequency 
  - High precision
  - Continuous measurements along a ship track.

To compare the 2025 shipboard measurements with 2024 products (MBL and CT2024), the values are adjusted using the Mauna Loa annual CO₂ growth rate:

$$
xCO_2^{2024\,(est)} = xCO_2^{2025\,(meas)} - \Delta CO_2^{ML}
$$

This provides a first-order 2024-equivalent ship dataset suitable for comparison with CT2024, MBL, and mooring observations.

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

