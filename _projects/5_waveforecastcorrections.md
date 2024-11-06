---
layout: page
title: Wave Forecast Time Series Correction 
description: Increasing wave model accuracy and determining wave model error regimes using Machine Learning
img: assets/img/decisiontree/scatterplot.jpg
importance: 6
category: PhD
related_)publications: true
---

<br>
<br>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/decisiontree/timeseries.jpg" title="Time Series of Wave Height and Corrected Wave Height" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/decisiontree/scatterplot.jpg" title="Scatter Plot of Wave Height and Corrected Wave Height" class="img-fluid rounded z-depth-1" %}
</div>
</div>
<div class="caption">
    <b> Left </b> Time series of observed wave height (black), wave watch 3 wave height (blue), and with corrections (green). Top panel is summer, bottom panel is winter. 
    <br> 
    <b> Right </b> Scatter plot of original wave height versus observations (left), and corrected wave height versus observations (right). 
</div>

In this paper, I correct wave height time series using a machine learning technique called bagged regression tree. The wave height output time series was taken from <a href="gabe'spaper"> Wave Watch 3 </a>. The output was divided between winter and summer, and the bagged regression tree was trained on the error between wave model output (wave height time series) and observed time series (at various <a href="www.ndbc.com"> National Data Buoy Center </a> buoys) with wave model input as features (wave height, wave direction, mean wave period). Several experiments were made with wind (wind magnitude, wind direction) as well. A final experiment was also performed where a decision tree was trained on several buoys and applied on the original buoy that was not included in the dataset in a geospatial experiment.

The cool thing about decision tree is that it can be used to diagnose model operating conditions - which features were most important to determine wave height error? This can tell us how the model performs for different regimes defined by its own output.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/decisiontree/featureimportances.jpg" title="Feature Importances" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Feature importances for summer and winter. Three experiments are shown here: 1. Summer; 2. Winter; 3. Geospatial.
</div>

For all three experiments, mean period was either the most or the second most important feature. This suggests that the accuracy of the wave model depended on how "developed" the sea state was; consistent over- and under- estimations might exist for different frequencies. 

For winter, wind magnitude becomes important, which is directly tied to the existence of local windseas. The ML technique differentiated corrections for different types of large wave heights. The wave heights associated with high winds from the south and required over a meter correction, while those that were not required a half meter negative correction. If you're interested in learning more, check out the paper {% cite ellenson2020application %}.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/decisiontree/partitions31_44.jpg" title="Scatterplot for large wave heights, colored by decision tree correction value" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Wave height scatterplots for original model output (left) and corrected model output (right). Different leaves (correction values) are colored. The orange instances were associated with high wind height coming from the south.
</div>

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% include repository/repo.liquid repository='anellenson/DecisionTree_WaveForecasts' %}
</div>