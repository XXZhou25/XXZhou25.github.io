---
layout: page
title: Traffic Sign Recognition
description: 
img: assets/img/GTSRBExamples.jpg
importance: 1
category: Research Projects
---

<h3 class="container-title"> Abstract </h3>

Extremely high accuracy and efficiency of Traffic Sign Recognition(TSR) are crucial for driving autonomous vehicles(AVs). A new Extreme Learning Machine(ELM) based TSR framework with spatial and time-frequency feature fusion technology, named as STF-ELM, is proposed in this project. Histogram equalization is employed to enhance the traffic sign images preprocessing, which contributes to balancing distribution of intensity and sharpness. In addition to the existing histogram of oriented gradients(HOG) for extracting spatial features, the feature based on the time-frequency domain, Gabor filter, is also used. The compressively fused feature vector is mapped to the predicated traffic signs via ELM network. The experimental results showed that the proposed STF-ELM achieved almost perfect performance for NO FAULT on most of categories, and outperformed the state-of-the-art TSR methods on the German Traffic Sign Recognition Benchmark(GTSRB).

<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.html path="assets/img/ExamplesofGTSRB.jpg" title="43 types of  traffic signs in the GTSRB dataset" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-7 mt-3 mt-md-0">
        {% include figure.html path="assets/img/GTSRBCategories.jpg" title="Traffic sign categories in GTSRB dataset" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. 43 types of  traffic signs in the GTSRB dataset    Fig 2. Traffic sign categories in GTSRB dataset
</div>

<h3 class="container-title"> Introduction </h3>

Traffic sign recognition (TSR) is a crucial task in vehicular systems, enabling vehicles to identify upcoming traffic signs while driving on the road. This real-time process necessitates a high degree of accuracy and efficiency. Conventional approaches for TSR primarily rely on visual information such as the shape and color of the traffic signs. Nonetheless, this task is inherently challenging due to the poor quality of images captured during the dynamic driving process. Factors such as bad weather conditions, occlusions, motion blur, viewpoint variations, and too dark or too bright illumination introduce disturbances that impede the recognition process, even for human observers.

To develop a high-performance TSR system, a fundamental approach involves preprocessing the images to enhance clarity and contrast, thereby facilitating the recognition of sign shapes. Additionally, it is crucial to design representative and robust features extracted from the images and employ a classifier that has a good balance between recognition accuracy and efficiency.

<h3 class="container-title"> Methods </h3>

In light of these considerations, we propose a fast and accurate model called based Extreme Learning Machine Spatial and Time-Frequency Feature Fusion(STF-ELM), combining with an efficient imge preprocessing pipeline. This model leverages the fusion of spatial Histogram of Oriented Gradients (HOG) and time-frequency Gabor features as a hybrid feature representation. This fusion approach ensures robustness to various variations in the image data and sensitivity to edges. Furthermore, our model incorporates the use of the Extreme Learning Machine (ELM), which excels in achieving high prediction accuracy while maintaining rapid learning speeds.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/FlowchartofSTF-ELM.jpg" title="our method" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 3. Pipeline of our proposed STF-ELM method.
</div>

<h3 class="container-title"> Experiments </h3>

As a whole, models should be tested for accuracy and efficiency, and compared with other published results for overall performance estimation. There are other six proposed TSR models performed on GTSRB from published papers. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Results.png" title="our method" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Table 1. Overall accuracy(%) and performance comparison with different proposed models.
</div>

<h3 class="container-title"> Results </h3>

From Table 1, we can find that our proposed model STF-ELM based on ELM performs best with the highest testing accuracy of 99.83% and achieves 100% on five categories of six. Also, our model based on KELM gets the second place with accuracy of 99.705%. Compared with other listed ELM-based methods such as HOGv+r(KELM) and DP-KELM, we could suppose that our methods outperform them in TSR whole process. In contrast with other state-of-the-art methods based on CNNs, despite the quite small margins of 0.18% between our methods and Ensemble CNNs, the computational costs of CNNs could be as much as dozens or even hundreds of times higher than our ELM based models.

<h3 class="container-title"> Conclusion </h3>

In conclusion, our Traffic Sign Recognition (TSR) model demonstrates exceptional accuracy and efficiency. These remarkable outcomes render our model highly valuable for integration into the driver assistance systems of autonomous vehicles, offering significant practical benefits.








