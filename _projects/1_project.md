---
layout: page
title: Traffic Sign Classification
description: 
img: assets/img/GTSRBExamples.jpg
importance: 1
category: Machine Learning/Computer Vision
---

Extremely high accuracy and efficiency of Traffic Sign Recognition(TSR) are crucial for driving autonomous vehicles(AVs). A new extreme learning machine(ELM) based TSR framework with spatial and time-frequency feature fusion technology, named as STF-ELM, is proposed in this thesis. Histogram equalization is employed to enhance the traffic sign images preprocessing, which contributes to balancing distribution of intensity and sharpness. In addition to the existing histogram of oriented gradients(HOG) for extracting spatial features, the feature based on the time-frequency domain, Gabor filter, is also used. The compressively fused feature vector is mapped to the predicated traffic signs via ELM network. The experimental results showed that the proposed STF-ELM achieved almost perfect performance for NO FAULT on most of categories, and outperformed the state-of-the-art TSR methods on the German Traffic Sign Recognition Benchmark(GTSRB).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/GTSRBCategories.jpg" title="Traffic sign categories" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Traffic sign categories. 
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/FlowchartofSTF-ELM.jpg" title="our method" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Pipeline of our proposed method.
</div>


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/GTSRBCategories.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/FlowchartofSTF-ELM.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

