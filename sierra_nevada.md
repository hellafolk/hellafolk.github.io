---
layout: default
---
#### Sierra Valley

The Sierra Valley, nestled on the border of Northern California and Western Nevada, has never just been a place on a map to me. It is where I spent my summers growing up... working on a farm in the summer heat, watching migratory birds pass overhead, and climbing on monzonite cliffs with my uncle. It was there that I first began to understand the rhythm of a landscape that feels both wild and deeply worked.

Eventually, I convinced my parents to let me move there full time to finish high school. Living with the valley year-round made its contrasts impossible to ignore. One of the largest alpine valleys in North America (The Nature Conservancy, n.d.), Sierra Valley is ecologically rich, seasonally flooded, and a critical stop along the Pacific Flyway for migratory birds (California Department of Fish and Wildlife, n.d.). Yet it is also a working landscape shaped by generations of ranching. Irrigated fields border wetlands. Historic barns sit beneath snow-covered peaks. Wilderness and agriculture coexist.

---
<div style="margin:1.5rem 0;">
  <img 
    src="https://hellafolk.github.io/img/4DC8C30A-0BB1-4EEE-AD8C-A803BD115110.jpeg"
    style="
      width:100%;
      max-width:500px;
      border-radius:12px;
      display:block;
      margin:0 auto;
    "
  >
</div>
---

In this assignment, I worked with satellite imagery of Sierra Valley that measures surface reflectance across several spectral bands. After adjusting the data to reflect true surface values and trimming it to the watershed boundary, I removed pixels affected by clouds. I then combined multiple images taken on different dates throughout the summer into a single median composite image to create a cleaner view of the area. Finally, I organized the data so that each pixel had reflectance values for each band, which allowed me to compare pixels across the valley.

<div style="margin:1rem 0;">
  <iframe
    src="https://hellafolk.github.io/img/sierra_valley_study_site.html"
    style="
      width:100%;
      height:500px;
      border:none;
      border-radius:12px;
      display:block;
    "
    loading="lazy">
  </iframe>
</div>

I then used k-means clustering (k = 5) to group pixels based on how similar their reflectance values were. The resulting clusters reveal how different surface types, such as wetlands and irrigated fields or prarie and rocky outcroppings, are distributed across the valley.

<iframe
  src="https://hellafolk.github.io/img/sierra_valley_composite.html"
  width="800"
  height="500"
  style="border:none; border-radius:12px; display:block; margin:2rem auto;"
  loading="lazy">
</iframe>


Overall, the clustering results make intuitive sense when compared to the landscape I know. Large wetland areas and open water separate clearly from drier uplands, and many of the irrigated fields group together as their own distinct class. In some places, especially where pasture transitions into marsh or where soil moisture changes across a field, the clusters blend together. That feels accurate too — the valley isn’t made up of hard boundaries, but gradual shifts. While k-means doesn’t “know” what water or vegetation is, it does a surprisingly good job of organizing the landscape based purely on reflectance. Seeing those familiar patterns emerge from data reinforces how remote sensing can capture the structure of a place that once felt defined only by experience.

<iframe
  src="https://hellafolk.github.io/img/sierra_valley_spectral_clustering_k5.html"
  width="800"
  height="500"
  style="display:block; margin:2rem auto; border:none; border-radius:12px;"
  loading="lazy">
</iframe>

---

<small>
Surface reflectance data from Harmonized Landsat and Sentinel-2 (HLS), NASA LP DAAC.
<a href="https://lpdaac.usgs.gov/products/hlsl30v002/" target="_blank">
https://lpdaac.usgs.gov/products/hlsl30v002/
</a>
</small>

<small>
Satellite imagery accessed via the Microsoft Planetary Computer STAC Catalog.
<a href="https://planetarycomputer.microsoft.com" target="_blank">
https://planetarycomputer.microsoft.com
</a>
</small>

<small>
Watershed boundary data from the U.S. Geological Survey (USGS) Watershed Boundary Dataset (WBD).
<a href="https://www.usgs.gov/national-hydrography/watershed-boundary-dataset" target="_blank">
https://www.usgs.gov/national-hydrography/watershed-boundary-dataset
</a>
</small>

<small>
Background basemap imagery © Esri, Earthstar Geographics.
</small>
