---
layout: page
title: Unsupervised Deformable Registration DNN for 3D Medical Images
description: Implemented by myself in Keras/Tensorflow/PyTorch, advised by Dr. Geoffrey Hugo
img:
importance: 4
category: Research Projects
---

<h3 class="container-title"> Introduction </h3>

Deformable registration is a widely used technique in various image-related tasks. Within clinical settings, medical images provide crucial information about the pathology and associated anatomy of the human body. Physicians often seek to compare two images of the same anatomical area captured under different conditions or integrate all available image data to gain a more comprehensive understanding of the regions of interest.

Conventional registration methods (non-lerning-based) involve optimizing an objective function for each image pair, which can be time-consuming when dealing with large datasets or complex deformation models. To address this challenge, neural network-based registration models are becoming an active research area, with numerous proposed approaches. Among these models, Voxelmorph is trained through unsupervised learning and has had a notable impact. Given a pair of images, Voxelmorph can rapidly compute a deformation field directly. 

The purpose of this project is to build a reliable DNN-based registration model for 3D lung CT images. This project entails exploring various DNN-based registration methods and implemented some of them, with specific emphasis on studying Voxelmorph, and variations on Voxelmorph are proposed. 

<h3 class="container-title"> Methods </h3>

Given the inherent complexity nature of lung structures and the challenges of registering image pairs with significant anatomical variations, a multi-level registration strategy is proposed to apply to the Voxelmorph model. The strategy computes deformation fields on different scales, a coarse-level alignment is obtained
first, which is subsequently improved on finer levels. 

The multi-level registration strategy I proposed: 
<ol>
    <li>1st level DNN has two downsampling layer in its first two layers, two upsampling layers at the end. 1st level DNN will be trained until its loss satisfy our criteria. </li>
    <li>2nd level DNN has one downsampling layer in its first layer, one upsampling layer at the end. 
    Fix the 1st level DNN, the output of it will be the input of the 2nd level DNN. 2nd level DNN will be trained until its loss satisfy our criteria. </li>
    <li>Once the 1st and 2nd level DNNs have been trained independently, they will be combined and retrained using the same dataset. This iterative process aims to refine the performance and accuracy of the combined model. </li>
</ol>
This strategy offers adaptability as the number of levels can be increased or decreased based on specific requirements and the available memory of the machine.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Voxelmorph.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1. Overview of Voxelmorph model framework[1]
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/multilevelstrategy.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 2. The proposed multi-level registration strategy
</div>





<h3 class="container-title"> Datasets </h3>


<h5 class="container-title"> Training dataset: Dirlab </h5>
Deformable Image Registration Laboratory (Dirlab) 4DCT, https://med.emory.edu/departments/radiation-oncology/research-laboratories/deformable-image-registration/index.html

The Dirlab dataset is obtained from a group of 10 patients diagnosed with thoracic malignancies, and for each patient, a series of 10 consecutive CT scans capturing the complete breath cycle, ranging from inhalation to exhalation, is included in the dataset. For each patient, the breath-in and breath-out images are all manually annotated with 300 landmarks by an expert distributed in the lung parenchyma. The point sets serve as a reference for evaluating DIR spatial accuracy within the lung for each case. The mean distance between corresponding landmark pairs on two images is defined as Landmark Distance Error(LDE). 


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/DirlabExample.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 2. Example: one pair of 3D CT images from a patient in Dirlab dataset. 
</div>

<h5 class="container-title"> Testing dataset: 4D lung CT dataset </h5>
This dataset is collected by Virginia Commonwealth University(VCU), which includes 17 patients who have atelectasis (partially collapsed lung). Each patient has one pair of CT scans before and after some treatment. 
On average, there were 169 landmarks per patient, with a standard deviation of 31 landmarks. Testing data differed from training data as they had large anatomical deformations compared to training data, and contained landmarks that were annotated by different experts. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/VCUexample.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 3. Example: one pair of 3D CT images from a patient in 4D lung CT dataset. 
</div>


<h3 class="container-title"> Experiments </h3>

The multi-level Voxelmorph is trained on Dirlab, test on an in-house 4DCT dataset. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Dirlabtraining.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Dirlabtraining.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<h4 class="container-title"> Reference </h4>
[1]. Balakrishnan G, Zhao A, Sabuncu M R, et al. Voxelmorph: a learning framework for deformable medical image registration[J]. IEEE transactions on medical imaging, 2019, 38(8): 1788-1800.
[2]. Galib, Shaikat M., et al. "A fast and scalable method for quality assurance of deformable image registration on lung CT scans using convolutional neural networks." Medical physics 47.1 (2020): 99-109.

