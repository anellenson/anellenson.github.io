---
layout: page
title: Surf Resource Assessment
description: Using wave models and algorithms to assess surf quality
img: assets/img/surf_project/peelangle.png
importance: 1
category: Integral
related_publications: true
---


<h2>How will a surf break be impacted by construction on the beach? By a seawall? By a wetland restoration?</h2>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/peelangle.png" title="Wave Breaking" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualization of peel angle. The peel angle is defined as the angle between the wave front and the wave path. The wave path is the direction the wave travels, and can be seen as the edge of the whitewater in the image (red line), and the wave fronts are the wave faces (orange lines) as the wave bends around the bottom.
</div>
 
In surf assessments, surfing resources (waves) are assessed pre- and post- construction quantitatively using wave models and wave metric calculation. This requires calculating a wave quality metric called "peel angle." 

For this project, I ran a wave model (non-hydrostatic <a href="https://oss.deltares.nl/web/xbeach/"> X-Beach </a>) for different scenarios, and then developed an algorithm to extract peel angle from the wave model.

I pulled wave fronts and wave path from the model to calculate peel angle. The wave model provides wave breaking, a binary mask, as an output. 

Wave path was determined by simulating white water: summing all of the wave breaking points simulates the white water, and a path is drawn along the white water. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/surf_project/whitewater_sum.png" title="Wave Breaking" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Deriving wave path from model simulations. The individual frames (top) are summed to visualize where the waves break most often (bottom).
</div>

The wave simulation is then run again, this time with the wave path overlaid, and individual wave fronts are extracted. The angle between the wave fronts and wave path is the peel angle. 
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/peelangle.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Extracting peel angle from a wave model. The wave path is the dashed white line. The wave fronts are colored in cyan. The angle between the wave front and wave path is colored magenta and is calculated using the geopandas library in python.
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
    <b> Center: </b> Five point moving average to visualize peel angle trend along the shoreline and for easy project comparison. 
    <br>
    <b> Bottom: </b> Comparison of three conditions: baseline (gray); no project (solid gold); with project (dashed gold). 
</div>

We validated the baseline conditions with surfers, and they confirmed that the peel angle we modelled corresponded with the wave itself. Despite the surfer fears that the porject would have a large impact, we found that the wetland construction would result in only slight variations in peel angle to the surfing wave. We presented at a meeting between the Resources Conservation District (RCD) and the surfing stakeholders which you can see in  {% cite ellenson_csbpa %} and in {% cite revell_asbpa %}. 