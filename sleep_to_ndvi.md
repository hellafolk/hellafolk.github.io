---
layout: default
---
#### Goodnight Denver: Sleep and Green Space

As a poor undergraduate, I found many creative ways to make money. One semester, when funds were especially tight, I signed up for a sleep study. I tracked my food, wore sensors, and spent long hours in dark laboratories, all to be told something I already suspected: I was not sleeping enough.

Colorado is known for many things... sunshine, access to nature, and a generally outdoorsy lifestyle. And yet, more often than not, adults in Colorado report sleeping fewer than seven hours per night. Previous analyses have shown that short sleep duration is common across the state and is associated with increased mental distress, with notable differences across demographic groups (Colorado Health Institute, Let’s Sleep on It, Colorado).

In this assignment, I explore whether urban greenspace might play a role in this pattern. Specifically, I examine whether neighborhoods with more vegetation are associated with lower rates of short sleep (defined as under seven hours per night), focusing on Denver as a case study.

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

I first pulled census tract data and Colorado CDC sleep estimates and plotted short sleep duration alongside neighborhood green space across Denver. One of the most noticeable patterns is that neighborhoods closest to downtown show some of the highest rates of short sleep, with up to ~44% of the population reporting fewer than seven hours of sleep per night. These same areas also tend to have relatively low levels of green space. In contrast, neighborhoods on the northeast side of Denver show higher amounts of vegetation and, more generally, lower rates of short sleep.

To quantify green space, I used satellite-derived Normalized Difference Vegetation Index (NDVI) data aggregated to the census tract level. NDVI provides a simple measure of vegetation presence by comparing reflected near-infrared and red light, with higher values indicating denser or healthier vegetation. I summarized NDVI within each tract to represent neighborhood-scale green space and examined this metric alongside CDC short sleep estimates to explore spatial patterns across the city.

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
        transform: scale(1);   /* <--- shrink it */
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

Comparing the two maps side by side wasn’t enough for me to draw any real conclusions about sleep and green space. While there were some visible spatial patterns, it was hard to tell whether those patterns actually reflected a relationship in the data. To get a clearer picture, I plotted the variables against each other using pairwise comparisons.

The figure shows scatter plots and distributions for short sleep duration and several vegetation metrics, including edge density, fractional vegetation cover, and patch size. Plotting the variables this way makes it easier to see whether any relationships exist beyond what can be inferred visually from maps alone. Some variables were log-transformed to reduce skew and make the data easier to interpret, especially where values span a wide range.

Overall, while the vegetation metrics are strongly related to each other, their relationship with short sleep duration appears weak and scattered, suggesting that green space alone may not be a strong predictor of short sleep at the census-tract level in Denver. 

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
        transform: scale(1);   /* <--- shrink it */
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

I decided to give the relationship between sleep and green space one last shot by building a simple linear regression model to predict short sleep duration using vegetation edge density. I trained the model on 70% of the data and tested it on the remaining 30%. When I mapped the model error, it became clear that the model did not do a good job predicting sleep based on urban green space alone.

In some areas, particularly near downtown, the model consistently underestimated how much short sleep people experience, while in other neighborhoods it predicted more sleep than was actually observed. Overall, the model tended to overestimate sleep duration across much of the city. This suggests that vegetation edge density on its own is a weak predictor of short sleep at the census-tract scale.

Overall, this assignment was a good reminder not to chase outcomes. While it is tempting to expect green space to explain patterns in sleep, the results suggest that these variables are largely unrelated in Denver, at least when considered in isolation.

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
        transform: scale(1);   /* <--- shrink it */
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

<small>
Data credit to: MODIS/Terra Vegetation Indices (MOD13Q1 v6.1), NASA LP DAAC (Didan, 2021). <a href="https://doi.org/10.5067/MODIS/MOD13Q1.061" target="_blank">https://doi.org/10.5067/MODIS/MOD13Q1.061</a>
</small>

