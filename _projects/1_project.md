---
layout: page
title: Surf Resource Assessment
description: Using wave models and algorithms to assess surf quality
img: assets/img/surf_project/wave.jpg
importance: 1
category: Integral
related_publications: true
---

Surfing resources are increasingly becoming more valued for both their recreational and economic benefits. Coastal infrastructure projects - like building seawalls, or even developing wetlands - can negatively impact surfing resources. Surfers, who care deeply about protecting their waves, have started to demand that surfing resources are considered in environmental impact assessments whenever a new project is proposed at the coast. 

In surf assessments, surfing resources are assessed pre- and post- construction using wave models. A quantitative assessment of the surfing resource requires calculating a wave quality metric called "peel angle." 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/peelangle.png" title="Wave Breaking" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualization of peel angle. The peel angle is defined as the angle between the wave front and the wave path. The wave path can be seen as tracing the edge of the whitewater in the image (red line), and the wave front are the wave faces (orange lines) as the wave bends around the whitewater.
</div>

For this project, I ran a wave model (non-hydrostatic <a href="https://oss.deltares.nl/web/xbeach/"> X-Beach </a>) for different scenarios, and then developed an algorithm to extract peel angle from the wave model.

The wave model provides wave breaking, a binary mask, as an output. To extract peel angle, first we have to extract wave path. Wave path was determined by simulating white water: summing all of the wave breaking points simulates the white water, and a path is drawn along the white water. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/whitewater_sum.png" title="Wave Breaking" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Deriving wave path from model simulations. The individual frames (top) are summed to visualize where the waves break most often (bottom).
</div>

The wave simulation is then run again, this time with the wave path overlaid, and individual wave fronts can be extracted. The angle between the wave fronts and wave path is the peel angle. 
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/peelangle.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Extracting peel angle from a wave model. The wave front is the points of wave breaking for each individual wave. The angle between the wave front and wave path is extracted using the geopandas library in python.
</div>

We can compare peel angles from different scenarios by plotting peel angle as a function of shoreline distance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/obs_pts.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/obs_pts_avg.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/compare_project.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    <b> Top: </b> Peel angle points as a function of distance along the shoreline. 
    <br>
    <b> Center: </b> Five point moving average to visualize peel angle behavior and to use to compare projects. 
    <br>
    <b> Bottom: </b> Comparison of three conditions: baseline; no project; with project (with Restoration). The peel angle curves allow us to visualize how the peel angle will be affected with the project. 
</div>

We found that the project would result in minimal impacts to the surfing wave, despite the surfer fears that it would. We presented at a meeting between the Resources Conservation District (RCD) and the surfing stakeholders. The result was a success! The surfers validated the peel angle baseline conditions, and signed off on the project's completion.
