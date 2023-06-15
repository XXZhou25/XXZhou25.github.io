---
layout: page
title: Out of Sample Performance of a Deep Learning Based Registration Quality Assurance Method
description: Implemented by myself, advised by Dr. Geoffrey Hugo
img: assets/img/2D_views_60.jpg
# redirect: https://unsplash.com
importance: 1
category: Research Projects
---

<a href="https://drive.google.com/file/d/1DgEF6JotMDPDQCMnSUlkhKKLenGvvo_O/view?usp=drive_link"> Paper link </a>

<h3 class="container-title"> Introduction </h3>

Deformable image registration(DIR) is widely used in radiation oncology despite lacking a ground truth for validating individual results. Quality assurance of DIR in the clinic relies on either visual inspection, or performance in phantom (benchmarking). However, benchmarking cannot be used to Quality Assurance (QA) individual image registrations. It is essential to have a reliable quality assessment system to provide clinically meaningful evaluation. Here we develop a 3D neural network to automatically learn highly-representative features to quantify DIR errors as a first pass QA procedure. To deal with various DIR algorithms and differing anatomy, it is expected to have good robustness as well. 

Motivated by the above intentions, a 3D neural network, based on registered images labelled by expert identified point landmarks, has been demonstrated to have reliable quality inference. In this study, we evaluate and improve the deep learning based registration QA algorithm robustness by 1) Improving preprocessing and network design; 2) evaluating generalizability of the model with new registration algorithm DRAMMS.

<h3 class="container-title"> Methods </h3>

We previously developed a three-dimensional neural network to infer registration accuracy based on registered images labelled by expert identified point landmarks and evaluated performance across two different datasets, the publicly available Dirlab dataset (Dirlab) and an in-house database of longitudinal 4DCT scans (Long4DCT) and two DIR algorithms, elastix b-spline (B-spline) and DRAMMS. 

In this study, we evaluated and improved algorithm robustness for different dataset and DIR combinations. Different combinations of training data were evaluated on held-out testing datasets: 1) Dirlab registered by B-spline (Dirlab / B-spline); 2) Dirlab registered by B-spline and DRAMMS (Dirlab / B-spline / DRAMMS; 3) Dirlab and Long4DCT registered by B-spline (Dirlab / Long4DCT / B-spline).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Patch.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1. Image preparation procedure of one patch, as input of Quality Assurance(QA) neural network
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/output.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 2. The label created process, as the ground truth of Quality Assurance(QA) neural network
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Networkstructure.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 3. Structure of our neural network, input: resampled patches, labeled by its landmark distance error
</div>


<h3 class="container-title"> Results </h3>

<ol>
    <li>The Area Under Curve (AUC) for training Dirlab / B-spline tested on held out Dirlab / B-spline was 0.99, on Long4DCT / B-spline was 0.94, on Dirlab / DRAMMS was 0.96, and on Long4DCT / DRAMMS was 0.94. </li>
    <li>Training on multiple registration algorithms Dirlab / B-spline / DRAMMS gave AUC 0.99 for Dirlab / B-spline, 0.94 for Long4DCT / B-spline, 0.99 for Dirlab / DRAMMS, and 0.93 for Long4DCT / DRAMMS. </li>
    <li>By training on Dirlab / Long4DCT / B-spline, the AUC for testing on Dirlab / B-spline was 0.99, for Long4DCT / B-spline was 0.97, for Dirlab / DRAMMS was 0.97, and for Long4DCT / DRAMMS was 0.96. </li>
</ol>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2D_views_60.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 4. Visualized Quality Assurance results of our model, mapped with original image:(a), overlapping of fixed and registered moving image; (b)-(d), predicted label map overlay; (e)-(g), true label map overlay. The highlighted areas have worse registration quality.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/QArobustness.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Table 1: Overall Accuracy and Area under Curve(AUC) of our model.
</div>



<h3 class="container-title"> Conclusion </h3>

Our registration QA algorithm showed reliable inference ability across various datasets and DIR, however, training with diverse datasets provided slightly better performance than by adding DIR algorithms. Enriching training data by different dataset combinations obtained some improvement, demonstrating that our model’s robustness has the potential for improvement.

