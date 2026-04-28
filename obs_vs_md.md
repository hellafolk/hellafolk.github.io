---
layout: default
---

# Model vs. Observations of CO₂ in the Tropical Pacific Marine Boundary Layer

## 1. Project Motivation

This project is a direct extension of work I began last semester, when I installed a Picarro CO₂ analyzer aboard a research vessel transiting the tropical Pacific. That deployment gave me my first look at high-resolution atmospheric CO₂ measurements from a part of the ocean that is both critically important to the global carbon cycle and severely under-observed. When I compared those shipboard measurements to model reference products — specifically the NOAA Marine Boundary Layer (MBL) reference — I found systematic offsets that I couldn't immediately explain. Were they an artifact of my instrument? A problem with the model? Or something more fundamental about how we represent atmospheric CO₂ over the tropical Pacific?

That question became the seed of this project.

The tropical Pacific plays an outsized role in the global carbon cycle. The region is shaped by strong upwelling, large-scale atmospheric circulation, and dramatic interannual variability driven by the El Niño–Southern Oscillation. It is also one of the most sparsely observed ocean regions on Earth — most of what we know about atmospheric CO₂ there comes from zonally averaged model products rather than direct measurements. This matters because air-sea CO₂ flux is calculated as:

<p align="center"><strong>F<sub>CO₂</sub> = k · s · (pCO₂<sub>w</sub> − pCO₂<sub>a</sub>) = k · s · ΔpCO₂</strong></p>

where **k** is the gas transfer velocity (driven by wind speed), **s** is CO₂ solubility (driven by temperature), **pCO₂<sub>w</sub>** is the partial pressure of CO₂ in the surface ocean, and **pCO₂<sub>a</sub>** is the atmospheric CO₂ concentration. Even a 1–2 ppm bias in the atmospheric term propagates directly into flux estimates — and over a basin the size of the Pacific, accumulated across years, that can amount to gigaton-scale errors in annual carbon budgets.

Rather than treat my original observation as an anomaly, I decided to ask whether the offset I saw was unique to my platform or common across multiple independent observing systems. If it is widespread and systematic, it has implications for every study that uses these reference products to calculate air-sea flux.

---

## 2. What Other Work Has Been Done

The NOAA GML Marine Boundary Layer reference product has been widely used in air-sea flux studies as a stable, well-vetted atmospheric boundary condition. It is constructed from a global network of flask and in-situ measurements and provides a smooth, zonally averaged representation of atmospheric CO₂ as a function of latitude and time. While it is excellent for capturing large-scale gradients and the seasonal cycle, it is by design unable to resolve regional variability — and the tropical Pacific is a region where that variability matters.

CarbonTracker, also produced by NOAA, takes a different approach — it is a three-dimensional atmospheric transport model constrained by observations, and provides CO₂ fields at higher spatial resolution. Several studies have used CarbonTracker output to provide atmospheric boundary conditions for flux calculations, with the expectation that its spatial structure better represents real atmospheric conditions than a zonally averaged product.

Work by [Takahashi et al. (2009)](https://doi.org/10.1016/j.dsr2.2008.12.009) established the climatological picture of air-sea CO₂ exchange and highlighted the tropical Pacific as a dominant source region. More recently, [Landschützer et al. (2024)](https://doi.org/10.5194/essd-16-2123-2024) emphasized the importance of high-quality atmospheric observations alongside surface ocean measurements for constraining flux estimates. My previous semester's project built on this foundation by deploying a Picarro analyzer — a cavity ring-down spectrometer known for its high precision and reliability in shipboard environments ([Rella et al., 2015](https://doi.org/10.5194/amt-8-411-2015)) — directly in this under-observed region.

This project extends that work by bringing in two additional observing platforms and comparing all three against multiple reference products over a three-year period.

---

## 3. Study Area and Data

The study focuses on the tropical Pacific marine boundary layer, defined here as the region between 23.5°S and 23.5°N. For aircraft data, the marine boundary layer is further constrained to altitudes below 500 meters, consistent with typical MBL depths in this region.

<p align="center">
  <img src="" style="width: 90%; max-width: 600px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Pacific-centred globe showing the tropical study region (23.5°S–23.5°N, gold dashed lines)</em>
  </p>
</div>

The time period 2016–2018 was chosen because it coincides with the NASA Atmospheric Tomography (ATom) campaign, which provided repeated aircraft transects across the tropical Pacific at high vertical resolution. This gave us a rare opportunity to compare surface ship observations with aircraft measurements sampling the same atmospheric layer, over the same region, within the same multi-year window.

### Observation Platforms

Three independent observation platforms were used:

**TransFuture 5 (TF5) Shipboard Picarro** — a Japanese cargo vessel operated by Toyofuji Shipping on a regular route between Japan and New Zealand, equipped with a Picarro cavity ring-down spectrometer measuring atmospheric CO₂ continuously at 1 Hz.

**POC Shipboard Flask** — a NOAA GML vessel collecting discrete atmospheric CO₂ samples via glass flask. Flask sampling provides lower temporal resolution than the Picarro but uses a well-established calibration standard maintained by NOAA GML, making it a useful cross-check.

**ATom DC-8 Aircraft** — the NASA DC-8 aircraft flew four campaigns (ATom-1 through ATom-4) across the tropical Pacific between August 2016 and May 2018, measuring atmospheric CO₂ with a NOAA Picarro instrument at 1 Hz. Only data collected below 500 meters altitude within the tropical band were used.

All ship and aircraft CO₂ data were filtered to the tropical band and the 2016–2018 period, and converted from mole fraction (mol/mol) to parts per million. The three platforms were combined into a single dataset with a source label.

### Reference and Model Products

Three atmospheric CO₂ reference products were used for comparison:

| Dataset | Source | Type |
|---|---|---|
| TF5 Shipboard CO₂ | Japanese cargo ship | Picarro (in-situ) |
| POC Shipboard CO₂ | NOAA GML | Flask sampling |
| ATom DC-8 CO₂ | NASA ATom campaign | Picarro (in-situ) |
| NOAA Global MBL | NOAA GML | Zonal mean model |
| NOAA Pacific MBL | NOAA GML | Zonal mean model |
| CarbonTracker CT2022 | NOAA | 3D transport model |
| OISST Sea Surface Temperature | NOAA ERDDAP | Satellite (blended) |
| MODIS-Aqua Chlorophyll-a | NASA CoastWatch | Satellite (ocean color) |
| ERA5 Pressure + Wind | Copernicus CDS | Reanalysis model |

Each observation was matched to the nearest grid cell and time step in each reference product using a nearest-neighbor approach.

---

## 4. Methods

The full analysis was conducted in Python using a single Jupyter notebook that handles data loading, downloading, matching, plotting, and machine learning in sequence. All output directories are created automatically when the notebook is run.

Ship data were read from NetCDF files and filtered to the tropical band and study period. ATom data were read from NASA ICARTT format files — a text-based format where the first line encodes the number of header lines to skip. Flight dates were parsed from filenames and UTC start times were converted to proper datetimes. Both ship and aircraft CO₂ data were converted from mole fraction to ppm by multiplying by 1×10⁶.

Each observation was matched to each reference product by snapping to the nearest sine-latitude band and decimal year time step — what we call nearest-box matching. The offset was computed as model minus observation. Remote sensing fields were downloaded using ERDDAP and the Copernicus CDS API and matched to observations using nearest-neighbor interpolation. Chlorophyll-a was log-transformed before analysis given its lognormal distribution.

A random forest regression model was trained to predict CO₂ from seven input features: SST, log(chlorophyll), wind speed, MSL pressure, latitude, longitude, and day of year. The forest used 200 trees with a maximum depth of 6 and a minimum leaf size of 20 to prevent overfitting. An 80/20 train-test split was used to evaluate generalization on held-out data.

---

## 5. Results

### 5.1 Observations Across Platforms

All three platforms show a consistent seasonal CO₂ cycle across the tropical Pacific, ranging from approximately 398–418 ppm over the study period. The rising trend from 2016 to 2018 is clearly visible in the time series. ATom campaigns appear as discrete clusters in time — each campaign lasted only a few weeks — while the ship data provide more continuous coverage.

<p align="center">
  <img src="" style="width: 90%; max-width: 700px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 700px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Time series of CO₂ (ppm) for all three platforms, 2016–2018. ATom campaigns appear as discrete clusters. The rising trend reflects the global increase in atmospheric CO₂.</em>
  </p>
</div>

<p align="center">
  <img src="" style="width: 90%; max-width: 600px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Pacific-centred globe map of all observations coloured by CO₂ value (ppm). Ship tracks are concentrated in the western Pacific; ATom flask measurements span the central Pacific.</em>
  </p>
</div>

### 5.2 Offsets from Reference Products

When observations are compared to the three reference products, all platforms show small but systematic positive offsets — meaning the observations are consistently slightly higher than what the reference products predict. Mean offsets range from approximately +0.07 ppm (ATom-1) to +0.87 ppm (ATom-4) relative to the Global MBL reference. The CarbonTracker product reduces these offsets relative to the MBL products, suggesting it captures some of the regional variability that the zonally averaged MBL products smooth over.

<p align="center">
  <img src="" style="width: 90%; max-width: 700px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 700px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Per-platform CO₂ offset from the NOAA GHG MBL reference. Dashed line at zero. Mean offset annotated for each platform. All platforms show a small positive bias.</em>
  </p>
</div>

<p align="center">
  <img src="" style="width: 90%; max-width: 800px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Globe maps of CO₂ offset (model minus observations) for three reference products. Red = model higher than obs, blue = model lower. Diverging colorbar, ±3 ppm.</em>
  </p>
</div>

### 5.3 Spatial and Temporal Structure of Offsets

The most striking result is the coherent spatial and temporal structure of the offsets revealed by the Hovmöller diagram. All three reference products show the same north-south asymmetry — models tend to be higher than observations in the southern tropics and lower in the northern tropics. This pattern is not random noise — it is consistent across all three independent reference products and persists through the full three-year study period. The seasonal banding visible in the Hovmöller suggests the bias has a seasonal component, likely related to the migration of the Inter-Tropical Convergence Zone and the north-south hemispheric asymmetry in the CO₂ seasonal cycle.

<p align="center">
  <img src="" style="width: 90%; max-width: 900px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 900px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Hovmöller diagrams of CO₂ offset (model minus obs) vs latitude and time for three reference products. Red = model high, blue = model low. The north-south asymmetry is consistent across all three products, indicating a real atmospheric signal rather than a product artifact.</em>
  </p>
</div>

### 5.4 Remote Sensing Drivers

None of the four remote sensing variables — SST, chlorophyll, wind speed, or surface pressure — show a strong linear relationship with the CO₂ offset on their own. SST shows a slightly negative relationship with CO₂, likely because the seasonal CO₂ cycle driven by the Northern Hemisphere land biosphere dominates over the local ocean temperature signal at monthly resolution. Chlorophyll shows a weak positive slope, consistent with upwelling regions bringing CO₂-rich subsurface water to the surface. Wind speed is essentially flat. Pressure shows a weak positive slope associated with stable high-pressure systems.

<p align="center">
  <img src="" style="width: 90%; max-width: 800px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Scatter plots of CO₂ (ppm) vs SST, chlorophyll-a, wind speed, and MSL pressure. Red lines show linear fits. Weak slopes across all four variables indicate no single oceanographic driver dominates the CO₂ variance.</em>
  </p>
</div>

### 5.5 Random Forest

A random forest regression model trained on seven features achieved R² = 0.84 and MAE = 0.69 ppm when predicting raw CO₂ across all 23,312 matched observations. While this appears to be a strong result, much of the explained variance is likely driven by the strong seasonal cycle captured by day of year and the latitudinal CO₂ gradient captured by latitude and longitude. The contribution of the ocean state variables alone remains to be isolated. This analysis is ongoing and represents a work in progress as I continue to develop my machine learning skills.

<p align="center">
  <img src="" style="width: 90%; max-width: 700px; border-radius: 12px;">
</p>
<div style="text-align: center; max-width: 700px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Random forest predicted vs actual CO₂ (ppm) on the held-out test set. R² = 0.84, MAE = 0.69 ppm. Points cluster along the 1:1 line in the 400–410 ppm range. The model struggles at the high end (>412 ppm) where observations are sparse.</em>
  </p>
</div>

---

## 6. Conclusions and Future Work

This project started with a simple question: was the offset I saw last semester between my shipboard CO₂ measurements and a model reference product something unique to my instrument, or a broader phenomenon? The answer is clearly the latter. All three observing platforms — two ships and a research aircraft — show systematic offsets from all three reference products, with a coherent north-south spatial structure and seasonal variability that none of the products fully capture.

The key findings are:

- All platforms show small but systematic positive offsets from reference products, ranging from +0.07 to +0.87 ppm depending on campaign and product
- CarbonTracker performs better than the zonally averaged MBL products, reducing offset magnitudes across all platforms
- The Hovmöller diagrams reveal a coherent north-south asymmetry and seasonal structure consistent across three independent reference products — this is a real atmospheric signal, not a product artifact
- No single remote sensing variable explains the offset variance on its own, consistent with the random forest result
- The random forest explains 84% of raw CO₂ variance, with location and seasonality as dominant features

Looking ahead, the most important next step is isolating the contribution of ocean state variables by deseasonalizing the data before applying the random forest. I also want to compare the error of my random forest predictions against the published uncertainty of the NOAA reference products. Finally, while this project focused on constraining the atmospheric pCO₂ term in the air-sea flux equation, the remote sensing variables I used are actually better suited for constraining the ocean-side pCO₂ term — a natural direction for future work.

---

## References

Lan, X., Tans, P., Thoning, K., & NOAA Global Monitoring Laboratory. (2024). NOAA Greenhouse Gas Marine Boundary Layer Reference - CO2. NOAA GML. [https://doi.org/10.15138/DVNP-F961](https://doi.org/10.15138/DVNP-F961)

CarbonTracker Team. (2022). CarbonTracker CT2022 atmospheric CO₂ mole fraction product. NOAA Global Monitoring Laboratory. [https://doi.org/10.25925/Z1GJ-3254](https://doi.org/10.25925/Z1GJ-3254)

Huang, B., et al. (2021). Improvements of the Daily Optimum Interpolation Sea Surface Temperature (DOISST) Version 2.1. Journal of Climate, 34(8), 2923–2049. [https://doi.org/10.1175/JCLI-D-20-0166.1](https://doi.org/10.1175/JCLI-D-20-0166.1)

Hersbach, H., et al. (2020). The ERA5 global reanalysis. Quarterly Journal of the Royal Meteorological Society, 146(730), 1999–2049. [https://doi.org/10.1002/qj.3803](https://doi.org/10.1002/qj.3803)

Rella, C. W., Chen, H., Andrews, A. E., et al. (2015). High accuracy CO₂ and CH₄ measurements in humid air with the Picarro G2301 analyzer. Atmospheric Measurement Techniques, 8, 411–425. [https://doi.org/10.5194/amt-8-411-2015](https://doi.org/10.5194/amt-8-411-2015)

Takahashi, T., Sutherland, S. C., Wanninkhof, R., et al. (2009). Climatological mean and decadal changes in surface ocean pCO₂, and net sea–air CO₂ flux over the global oceans. Deep-Sea Research II, 56, 554–577. [https://doi.org/10.1016/j.dsr2.2008.12.009](https://doi.org/10.1016/j.dsr2.2008.12.009)

Landschützer, P., Lauvset, S. K., Becker, M., & the SOCONET Team. (2024). Surface Ocean CO₂ Reference Observing Network (SOCONET). Earth System Science Data, 16, 2123–2160. [https://doi.org/10.5194/essd-16-2123-2024](https://doi.org/10.5194/essd-16-2123-2024)

## Full Analysis Notebook
[Available here](https://github.com/hellafolk/final_project/tree/main/notebook)
