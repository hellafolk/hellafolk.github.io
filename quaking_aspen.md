---
layout: default
---
#### Quaking Aspen

How will a tree’s home change from the time I grow up in to the time I grow old in?

Quaking aspen (Populus tremuloides) can feel stationary as I hike through the Sangre de Cristo Mountains near the Great Sand Dunes, but in reality, they are always moving. Slow, steady, and over the course of a lifetime, those shifts can become visible.

Aspen is one of the most widespread tree species in North America, but its future is becoming more uncertain as the climate warms. Found across subalpine and montane environments in the western United States, aspens depend on cool temperatures, reliable moisture, and well-drained soils. That makes them especially sensitive to changes in snowpack, drought, and heat.

In this project, I look at how suitable habitat for aspen may shift under future climate scenarios by combining soil, topographic, and climate data. I focus on where aspens are thriving now, and how, under different climate conditions, those preferred habitats may change, whether that means moving upslope, shifting northward, or disappearing from parts of the landscape altogether.

---
<div style="margin:1.5rem 0;">
  <img 
    src="https://hellafolk.github.io/img/2405CDBF-E94A-4942-9DDE-9C10917DDA84.jpeg"
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

To explore how habitat suitability might shift across different environments, I chose two study sites in Colorado that represent different conditions for aspen. Using the USGS Protected Areas Database (PAD-US v4.1), I focused on National Parks of similar size and picked locations where aspens are present, but where climate and elevation vary a lot. Rocky Mountain National Park (ROMO), my first site, represents a higher-elevation, cooler environment with more snowpack. Great Sand Dunes National Park (GSNP) has a much smaller aspen population, where conditions are warmer and drier. Looking at both together lets me compare an already comfortable habitat (ROMO) with one that’s pushing the limits (GSNP), and see how those might shift with climate change.

<div style="margin:1rem 0;">
  <iframe
    src="https://hellafolk.github.io/img/aspen_sites_map.html"
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

I selected two 30-year climate periods: 2011–2040 and 2041–2070. These windows follow standard climate normals and allow for a comparison between near-future and mid-century conditions. They also represent a span of my own lifetime. The first period reflecting the climate I am growing up in, while the second representing the climate I will grow old in.

To model habitat suitability across future scenarios, I used MACAv2 downscaled climate data in combination with the Climate Futures Toolbox to select representative projections for each site. To capture the range of possible climates within these time periods, I selected four models that span the extremes of projected temperature and precipitation: cool and wet (CNRM-CM5), cool and dry (MIROC5), hot and dry (IPSL-CM5A-LR), and hot and wet (HadGEM2-ES365). This allows me to explore not just a single future, but a range of plausible conditions that could influence where aspen can persist.

I focused on a high-emissions scenario (RCP 8.5) to capture a more extreme, but still plausible, trajectory of future climate change. In addition to temperature and precipitation, I incorporated environmental variables that directly influence aspen growth, including elevation, slope, and aspect to capture topographic controls on solar radiation and drainage, as well as soil properties such as saturated water content and soil organic matter, which reflect water availability, nutrient cycling, and overall soil health. Together, these variables provide a more complete representation of the physical conditions that determine where quaking aspen can persist under changing climate conditions.

<iframe
  src="https://hellafolk.github.io/img/sierra_valley_composite.html"
  width="800"
  height="500"
  style="border:none; border-radius:12px; display:block; margin:2rem auto;"
  loading="lazy">
</iframe>


To estimate habitat suitability, I used a Gaussian fuzzy logic approach to translate each environmental variable into a continuous suitability score. Instead of applying strict thresholds (e.g., suitable vs. not suitable), this method allows conditions to be partially suitable depending on how close they are to an optimal value for aspen growth. Temperature, precipitation, elevation, slope, aspect, soil moisture, and soil organic matter were assigned an optimal range and a tolerance, which controls how quickly suitability declines as conditions move away from that sweet spot. The final habitat suitability map is calculated by averaging across all variables, allowing multiple factors to contribute without any single one dominating the result.

<img 
  src="https://hellafolk.github.io/img/suitability_2011_2040.png"
  style="width:100%; max-width:900px; height:auto; display:block; margin:2rem auto; border-radius:12px;"
/>

<img 
  src="https://hellafolk.github.io/img/suitability_2041_2070.png"
  style="width:100%; max-width:900px; height:auto; display:block; margin:2rem auto; border-radius:12px;"
/>

Overall, my results suggest that habitat suitability for quaking aspen is shifting in both elevation and spatial distribution under future climate conditions. Initially, these changes were difficult to see clearly, so I compared time periods directly by subtracting one from the other to highlight differences in habitability. This made the patterns much more apparent.

In Rocky Mountain National Park, suitability generally increases at higher elevations, while lower elevations become less suitable, indicating an upward shift driven by warming temperatures. In contrast, Great Sand Dunes National Park shows an overall decline in suitability, suggesting that already marginal environments may become increasingly inhospitable as conditions become warmer and drier. Across the climate models, cooler and wetter scenarios tend to maintain or expand suitable habitat, while hotter and drier scenarios show widespread declines. 

<img 
  src="https://hellafolk.github.io/img/difference_map_2041_2070.png"
  style="width:100%; max-width:900px; height:auto; display:block; margin:2rem auto; border-radius:12px;"
/>
