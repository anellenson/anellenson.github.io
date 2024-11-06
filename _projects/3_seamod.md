---
layout: page
title: SEAMOD
description: Site Energy Assessment MOnitoring Dashboard - Providing wave metrics to wave energy developers.
img: assets/img/seamod/datadisplay.png
importance: 3
category: Integral
related_publications: true 
---


<h3>Where in my region is most ideal to place a wave device? </h3>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/seamod_video.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Demonstration of the wave metric dashboard, SEAMOD. Users can select a region of interest and get seasonal, annual, or monthly statistics of different wave metrics.
</div>

I helped to develop a dashboard for wave energy developers, where they could slect an area of interest and get information about the region's wave resource. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/datadisplay.png" title="Example of SEAMOD data display" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example of a user selecting a point and getting information about the wave variables. 
</div>


The data variables included both raw information usually available in wave hindcasts and also derived variables, which were calculated following <a href="https://www.sciencedirect.com/science/article/abs/pii/S0306261920304347"> Ahn, 2022 </a>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/variables.png" title="SEAMOD display variables" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Different wave variables provided in SEAMOD. The black are the original output from the wave hindcast, and the blue are calculated.
</div>

The wave information was sourced from <a href="https://polar.ncep.noaa.gov/waves/hindcasts/nopp-phase1.php"> a thirty year hindcast of wave data provided by NCEP. </a> It included 15 different grids to ranging from 55 to 8 km in resolution.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/glo_30m.png" title="Global grid" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/ecg_grid.png" title="East Coast Grid" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/med_bathy.png" title="Mediterrenean Grid" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Three examples of grids provided in the hindcast. 
</div>

The gridded data were post-processed to calculate additional variables for SEAMOD. I performed the post-processing on a Digital Ocean server, and used Dask and X-Array. The equations were reformatted into matrix calculations to allow for parallel processing (i.e., the arrays were flattened, and additional dimensions were added or removed as necessary).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/backend_data.png" title="SEAMOD Backend Processing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Processing routine to calculate the SEAMOD variables.
</div>

Ultimately, the processing routine was loaded into a backend database and served to the client via an API. The front-end was written in R-Shiny. I then presented on my methods at {% cite ellenson2024building %}

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/seamod/architecture.png" title="SEAMOD architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Backend architecture showing how data variables were moved from the database and into the front end display.
</div>