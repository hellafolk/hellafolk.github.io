---
layout: default
---
# Air–Sea CO₂ Flux Over the Equatorial Pacific: Comparing Atmospheric Constraints

## 1. Project Motivation

Accurate estimates of air–sea CO₂ flux depend on knowing both the seawater partial pressure of CO₂ and the atmospheric CO₂ concentration directly above the ocean surface. While surface ocean CO₂ measurements have expanded over the past two decades, atmospheric observations over the global ocean—especially the Pacific—remain extremely sparse. Because of this, many flux calculations rely on atmospheric products that are zonally averaged or model-based rather than derived from direct, regionally representative measurements.

Flux studies often use the NOAA GML Marine Boundary Layer (MBL) product, which provides a smooth, zonally homogeneous reference surface for atmospheric CO₂. These fields are stable and well-vetted, but they inevitably smooth out regional variability and may not reflect real atmospheric conditions in dynamic environments like the equatorial Pacific—a region shaped by strong upwelling, large-scale circulation, and interannual anomalies. Without direct observations, it’s difficult to know whether these zonally averaged products capture the gradients that meaningfully influence flux estimates.

Because the equatorial Pacific plays an outsized role in the global carbon cycle—and because atmospheric observations across this basin are so limited—it is essential to understand how different atmospheric datasets shape flux estimates. This project compares three atmospheric CO₂ sources for the equatorial Pacific in 2024: the NOAA GML MBL product, CarbonTracker 2024 model output, and in-situ atmospheric measurements from a 2025 ship track adjusted to a 2024 reference. In this context, a high-quality, high-resolution atmospheric measurement system installed alongside an existing pCO₂ system can provide crucial boundary-layer information in regions where observations are sparse, helping resolve subtle gradients that significantly affect calculated flux. By examining these differences, the goal is to assess whether commonly used atmospheric CO₂ products provide sufficiently accurate boundary conditions for flux estimates in one of the most variable—and under-observed—regions of the global ocean.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/ship_track.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Shiptrack: Area of Interest</em>
  </p>
</div>
---

## 2. Core Research Question

Estimating air–sea CO₂ flux requires knowing the difference between seawater (pCO₂₍w₎) and atmospheric (pCO₂₍a₎) CO₂. This gradient is often written as:

$$
F_{CO_2} = k \, s \, (pCO_{2w} - pCO_{2a}) = k \, s \, \Delta pCO_2
$$

where:

- **F<sub>CO₂</sub>** is the air–sea CO₂ flux,  
- **k** is the gas transfer velocity (largely controlled by wind speed),  
- **s** is the solubility of CO₂ in seawater,  
- **ΔpCO₂** is the air–sea CO₂ gradient.

Because the flux depends directly on atmospheric CO₂, even small biases in pCO₂₍a₎ can produce large uncertainties in the resulting flux. A difference of just **1–2 ppm** in atmospheric CO₂ corresponds to a **1–2 µatm** shift in ΔpCO₂. When applied across realistic values of k and s over a basin-scale region such as the equatorial Pacific, this can change CO₂ flux estimates by **tens of teragrams of carbon (TgC)**. Over global scales and multiple years, persistent biases of this size can accumulate into **gigaton-scale errors** in annual CO₂ budgets.

This sensitivity makes the choice of atmospheric CO₂ dataset critical. In the equatorial Pacific—where upwelling, circulation, and climate variability create strong gradients—using zonally averaged products may obscure important structure in pCO₂₍a₎ and lead to inaccurate flux estimates.

---

<div style="
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 1.5rem 0;
">
  <img
    src="https://hellafolk.github.io/img/co2_2008_junjuly_turbo_24-9fps_final_norm375390.gif"
    alt="Animated CO₂ field, June–July 2008"
    style="
      max-width: 600px;
      width: 100%;
      height: auto;
      border-radius: 12px;
    "
  />
</div>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>CarbonTracker, Source:
    <a href="https://gml.noaa.gov/ccgg/carbontracker/" target="_blank">NOAA GML</a>.</em>
  </p>
</div>
---

**How do different atmospheric CO₂ datasets influence calculated air–sea CO₂ flux in the equatorial Pacific?**

Specifically:

1. How do 2024 atmospheric CO₂ values differ between  
   - the NOAA GML Marine Boundary Layer (MBL) product,  
   - CarbonTracker 2024 (CT2024)?  

2. How well do these products represent the atmospheric conditions encountered along a 2025 ship track, after adjusting those measurements back to 2024 levels using the Mauna Loa CO₂ growth rate?

3. To what extent do the resulting differences in \( pCO_{2a} \) change calculated air–sea CO₂ flux, and are those differences large enough to matter for regional or global carbon budgets?

---

<div style="
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 1.5rem 0;
">
  <img
    src="https://hellafolk.github.io/img/co2_surface_movie_time_cropped.gif"
    alt="Animated CO₂ field, June–July 2008"
    style="
      max-width: 600px;
      width: 100%;
      height: auto;
      border-radius: 12px;
    "
  />
</div>

---

### **Preliminary Data**

- In early 2025, I measured high-frequency atmospheric CO₂ with a Picarro analyzer onboard the ro-ro ship **M/V *Tysla*** during its transit across the equatorial Pacific.

- To compare these 2025 observations with **2024 atmospheric CO₂ products** (NOAA MBL and CarbonTracker PBL CO₂), I estimated what the shipboard CO₂ values *would have been* in 2024.

- I used the **Mauna Loa 2024 annual growth rate**:  
  `ΔCO2_MLO,2024 = 3.33 ± 0.11 ppm`

- For each ship measurement, I created a *“2024-equivalent”* atmospheric CO₂ value by subtracting this growth rate:  
  `CO2_ship,2024_equiv = CO2_ship,2025 − 3.33 ppm`

- I also shifted the 2025 day-of-year by **–1** to align with the 2024 seasonal cycle (since 2024 was a leap year).

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/tysla_stack.jpg"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Photo taken during installation of Atmopsheric System, Carribean Sea, Anna McAuliffe</em>
  </p>
</div>
---

### **MBL and CarbonTracker**

- I organized the shipboard measurements into a GeoDataFrame containing  
  time, latitude, longitude, and high-frequency atmospheric CO₂ from the Picarro analyzer.

- This spatial–temporal structure allowed each CO₂ measurement to be treated as a  
  georeferenced point along the ship track.

- Using the ship’s time and location, I interpolated:  
  1. NOAA’s Marine Boundary Layer (MBL) CO₂ product, and  
  2. CarbonTracker’s Planetary Boundary Layer CO₂ (PBL CO₂)

  to the exact times and positions of the ship.

- This produced a direct, point-by-point comparison between  
  **ship CO₂**, **MBL CO₂**, and **CarbonTracker PBL CO₂**,  
  enabling residual analysis and evaluation of model performance along the track.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/tysla_side.jpg"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Photo of M/V Tysla via VesselFinder</em>
  </p>
</div>
---

## **Preliminary Results**

I initially expected **CarbonTracker PBL CO₂** to match the shipboard atmospheric measurements most closely, since it resolves more spatial structure than the NOAA MBL product. However, the comparison showed a more nuanced result.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/ortho_ship_map.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/ct_final.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/mbl_final.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>

---

### **1. CarbonTracker captured gradients but showed a positive bias**

- CarbonTracker reproduced the **interhemispheric CO₂ gradient**, including the transition from northern-hemisphere winter air to southern-hemisphere summer air.  
- Despite capturing this large-scale structure, **CarbonTracker’s CO₂ values were consistently higher** than the shipboard observations along most of the track.  
- This suggests that while CarbonTracker preserves realistic spatial variability, it may introduce a **systematic bias** that inflates ΔpCO₂ and affects air–sea flux estimates.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/residuals_map.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
---


### **2. The NOAA MBL product was smoother but closer in mean value**

- The MBL product is intentionally smooth and does not resolve the regional features seen in CarbonTracker or the ship data.  
- Even so, the **overall mean value of MBL CO₂ aligned more closely with the shipboard measurements**.  
- This implies that MBL may be **bias-reduced on average**, but less representative of real atmospheric variability in the equatorial Pacific.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/three_comparisions.png"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
---

### **3. Trade-offs between the two atmospheric datasets**

The comparison indicates that **neither dataset is uniformly superior**:

- **CarbonTracker** preserves spatial structure but may carry a positive bias relative to real atmospheric conditions.  
- **MBL** is smoother and lacks variability, but its average value matches the observations more closely.

### **4. Importance of direct atmospheric measurements**

For air–sea CO₂ flux calculations, **having only seawater pCO₂ is not enough**.  
A high-resolution atmospheric CO₂ measurement system—such as the Picarro analyzer used on the ship—can capture subtle gradients and variability that neither MBL nor CarbonTracker fully resolves. These differences can meaningfully alter ΔpCO₂ and therefore the resulting flux estimates.


