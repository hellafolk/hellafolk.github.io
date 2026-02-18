---
layout: default
---
#### Sierra Valley

The Sierra Valley, nestled on the border of Northern California and Western Nevada, has never just been a place on a map to me. It is where I spent my summers growing up... working on a farm in the summer heat, watching migratory birds pass overhead, and climbing on monzonite cliffs with my uncle. It was there that I first began to understand the rhythm of a landscape that feels both wild and deeply worked.

Eventually, I convinced my parents to let me move there full time to finish high school. Living with the valley year-round made its contrasts impossible to ignore. One of the largest alpine valleys in North America (The Nature Conservancy, n.d.), Sierra Valley is ecologically rich, seasonally flooded, and a critical stop along the Pacific Flyway for migratory birds (California Department of Fish and Wildlife, n.d.). Yet it is also a working landscape shaped by generations of ranching. Irrigated fields border wetlands. Historic barns sit beneath snow-covered peaks. Wilderness and agriculture coexist.

---
<p align="center">
  <img 
    src="https://hellafolk.github.io/img/Denver_Downtown_Aerial,_December_2025.jpg"
    style="width: 90%; max-width: 500px; border-radius: 12px;"
  >
</p>
<div style="text-align: center; max-width: 600px; margin: 0 auto;">
  <p style="font-size: 0.8rem; color: #444; background: #f5f5f5; padding: 6px 10px; border-radius: 6px;">
    <em>Downtown Denver Source: 
    <a By Spicypepper999 - Own work, CC0, https://commons.wikimedia.org/w/index.php?curid=180627168</a>.</em>
  </p>
</div>
---

In this assignment, I worked with satellite imagery of Sierra Valley that measures surface reflectance across several spectral bands. After adjusting the data to reflect true surface values and trimming it to the watershed boundary, I removed pixels affected by clouds. I then combined multiple images taken on different dates throughout the summer into a single median composite image to create a cleaner view of the area. Finally, I organized the data so that each pixel had reflectance values for each band, which allowed me to compare pixels across the valley.

I then used k-means clustering (k = 5) to group pixels based on how similar their reflectance values were. The resulting clusters reveal how different surface types, such as wetlands and irrigated fields or prarie and rocky outcroppings, are distributed across the valley.

<div style="
  width: 100%;
  overflow-x: visible;
  overflow-y: visible;
  display: flex;
  justify-content: center;
  margin: 2rem 0;
">
  <div style="
    position: relative;
    width: 100%;
    max-width: 800px;        /* match theme body width */
    height: 500px;           /* MUST be big enough to show the scaled iframe */
  ">
    <iframe
      src="https://hellafolk.github.io/img/sleep_vs_vegetation.html"
      style="
        position: absolute;
        top: 0;
        left: 0;
        transform-origin: top left;
        transform: scale(.8);   /* <--- shrink it */
        width: 1300px;           /* pretend size of real map content */
        height: 820px;           /* pretend size of real map content */
        border: none;
        border-radius: 12px;
      "
      loading="lazy"
      scrolling="no"
    ></iframe>
  </div>
</div>


Overall, the clustering results make intuitive sense when compared to the landscape I know. Large wetland areas and open water separate clearly from drier uplands, and many of the irrigated fields group together as their own distinct class. In some places, especially where pasture transitions into marsh or where soil moisture changes across a field, the clusters blend together. That feels accurate too — the valley isn’t made up of hard boundaries, but gradual shifts. While k-means doesn’t “know” what water or vegetation is, it does a surprisingly good job of organizing the landscape based purely on reflectance. Seeing those familiar patterns emerge from data reinforces how remote sensing can capture the structure of a place that once felt defined only by experience.


<div style="
  width: 100%;
  overflow-x: visible;
  overflow-y: visible;
  display: flex;
  justify-content: center;
  margin: 2rem 0;
">
  <div style="
    position: relative;
    width: 100%;
    max-width: 800px;        /* match theme body width */
    height: 500px;           /* MUST be big enough to show the scaled iframe */
  ">
    <iframe
      src="https://hellafolk.github.io/img/scatter_matrix_transformed.html"
      style="
        position: absolute;
        top: 0;
        left: 0;
        transform-origin: top left;
        transform: scale(.8);   /* <--- shrink it */
        width: 1300px;           /* pretend size of real map content */
        height: 820px;           /* pretend size of real map content */
        border: none;
        border-radius: 12px;
      "
      loading="lazy"
      scrolling="no"
    ></iframe>
  </div>
</div>




<div style="
  width: 100%;
  overflow-x: visible;
  overflow-y: visible;
  display: flex;
  justify-content: center;
  margin: 2rem 0;
">
  <div style="
    position: relative;
    width: 100%;
    max-width: 800px;        /* match theme body width */
    height: 500px;           /* MUST be big enough to show the scaled iframe */
  ">
    <iframe
      src="https://hellafolk.github.io/img/short_sleep_model_error_map.html"
      style="
        position: absolute;
        top: 0;
        left: 0;
        transform-origin: top left;
        transform: scale(.8);   /* <--- shrink it */
        width: 1300px;           /* pretend size of real map content */
        height: 820px;           /* pretend size of real map content */
        border: none;
        border-radius: 12px;
      "
      loading="lazy"
      scrolling="no"
    ></iframe>
  </div>
</div>
---
<small>
Data credit to: MODIS/Terra Vegetation Indices (MOD13Q1 v6.1), NASA LP DAAC (Didan, 2021).
<a href="https://doi.org/10.5067/MODIS/MOD13Q1.061" target="_blank">
https://doi.org/10.5067/MODIS/MOD13Q1.061
</a>
</small>

<small>
Satellite data accessed via the Microsoft Planetary Computer STAC Catalog.
<a href="https://planetarycomputer.microsoft.com" target="_blank">
https://planetarycomputer.microsoft.com
</a>
</small>

<small>
Sleep duration data from the Centers for Disease Control and Prevention (CDC),
PLACES: Local Data for Better Health.
<a href="https://www.cdc.gov/places" target="_blank">
https://www.cdc.gov/places
</a>
</small>

<small>
Census tract boundaries from the U.S. Census Bureau TIGER/Line Shapefiles.
<a href="https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html" target="_blank">
https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html
</a>
</small>

<small>
Colorado sleep context from the Colorado Health Institute,
“Let’s Sleep on It, Colorado.”
<a href="https://www.coloradohealthinstitute.org/blog/lets-sleep-it-colorado" target="_blank">
https://www.coloradohealthinstitute.org/blog/lets-sleep-it-colorado
</a>
</small>



