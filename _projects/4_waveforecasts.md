---
layout: page
title: Wave Modeling Extreme Events
description: Determining wave model error mechanisms for extreme events
img: assets/img/extrememodeling/spectra_peaks.jpg
importance: 5
category: PhD
related_publications: true
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/extrememodeling/timeseries_permutations.jpg" title="Wave Height Time Series" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Wave height time series from buoy observations (solid black line) and modelling permutations.
</div>

In this research, a wave model was run for three different extreme events, and the mechanisms for wave model erorr were determined. The three different extreme events all featured a strong southern wind during their peak. Models differed in terms of their wind input and physics package selected. 

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/extrememodeling/synopticscale_forcing.jpg" title="Synoptic Scale Conditions for Extreme Events" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Synoptic scale conditions for different time steps for a chosen event. The strong southern wind is visible throughout the event, but especially in the bottom right panel (November 17, 2009).
</div>

The spectral shape (variance density) of the model output and the buoy were inspected. The models that performed better had higher energy in the southern partition of the spectrum. 

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/extrememodeling/spectra_peaks.jpg" title="Energy Spectra at Peak Time Step" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Energy spectra for the worst performing (ST2-GFS) model, the best performing (ST4-CFSR) model, and the observed spectra. The spectra were taken from the peak of the wave height time series for the three events. 
</div>

This suggested that wave models that better represent local wind seas (ST4) and wind input with higher resolution (CFSR) performed best. For full details, see {% cite ellenson2018predicting %}.
