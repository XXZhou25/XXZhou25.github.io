---
layout: page
title: Spline-based Image Registration
description: Implemented from scratch in Python by myself, advised by Dr. Geoffrey Hugo
img: assets/img/registrationexample.png
importance: 3
category: Research Projects
github: https://github.com/XXZhou25/Bspline-registration.git
---

<h3 class="container-title"> Introduction </h3>
Image registration is a task aiming at finding a spatial transformation between two images to align them. In plain words, it aims to deform one image to reasonably resemble another image as closely as possible. The first image is referred to as the fixed image, serving as the target image. The second image is known as the moving image, which is intended to be registered or aligned with the fixed image. 

A registration is called rigid if the motion or change is limited to global rotations and translations, and is called deformable when the registration includes complex local variations. In clinics, rigid matching is appropriate for serial imaging of the skull, brain, or other rigidly immobilized sites. Deformable registration is appropriate for almost all other scenarios and is useful for many applications within medical research, medical diagnosis, and interventional treatments.

Image registration can be modeled as an optimization problem. In general, it has three components: a geometric transformation, a similarity metric and an optimization method. The goal of the optimization process is to find an optimal deformation field, which accurately describes how the voxels in the moving image have been displaced with respect to their original positions in the fixed image. 

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/registrationprocess.png" title="registration process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. Basic process of image registration algorithm[2]
</div>

<h3 class="container-title"> Methods </h3>

In this project, the B-spline registration was implemented, which uses B-spline curves to define a continuous deformation field that maps each voxel in a moving image to a corresponding voxel within a fixed or reference image. In the case of B-spline registration, the dense deformation field can be parameterized by a sparse set of control points which are uniformly distributed throughout the moving image’s voxel grid. The control points are free to move, the displacment vectors of other points are obtained by B-spline interpolation of these control point coefficients using piecewise continuous B-spline basis functions. 

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Bsplinegrid.jpg" title="Bspline grids" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 2.  A graphical example of computing the deformation field from B-spline coefficients in two-dimensions. (a) The 16 control points needed to compute the deformation field within the highlighted tile are shown in gray. The smaller arrows represent the deformation vectors associated with each voxel within the tile. (b) Uniform cubic B-spline basis function plotted (top) and written as a piecewise algebraic equation (bottom).[3]
</div>

The employed loss function consists of a combination of a similarity metric and a regularization term. Given that the image pairs being registered belong to the same modality, the Sum of Squared Error (SSE) was utilized as the similarity metric. Additionally, the Total Variation method was employed as the regularization term to enhance smoothness in the obtained results. The Gradient Descent was used as the optimization algorithm. 

<h3 class="container-title"> Experiments </h3>
The algorithem was tested on two pairs of images.
The first pair of images are as Fig. 3, and the corresponding registered moving image and loss curve are as Fig. 4. 

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair1_moving.png" title="A: image to be registered" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair1_fixed.png" title="B: target image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 3. left: moving image    right: fixed image
</div>

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair1_registeredmov.png" title="registered A" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair1_loss.png" title="Loss curve for registration process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 4. left: registered moving image     right: loss curve
</div>

The second pair of images are as Fig. 5, and the corresponding registered moving image and loss curve are as Fig. 6. 

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair2_moving.png" title="A: image to be registered" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair2_fixed.png" title="B: target image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 5. left: moving image    right: fixed image
</div>


<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair2_registeredmov.png" title="registered A" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Pair2_loss.png" title="Loss curve for registration process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 6. left: registered moving image     right: loss curve
</div>


<h3 class="container-title"> Results and conclusion </h3>

It is evident from the observations that the moving image underwent deformation to a certain extent, leading to a decrease in the loss. Overall, the Bspline registration process operated normally, although its deformation capability proved to be relatively limited. To enhance this ability, optimization can be achieved by modifying the transformation model, altering the loss function or optimization method, and fine-tuning the parameters such as the number of control points and learning rate.




<h4 class="container-title"> Reference </h4>
[1]. Shackleford J, Kandasamy N, Sharp G. Unimodal b-spline registration[J]. High Performance Deformable Image Registration Algorithms for Manycore Processors, 2013: 13-43.
[2]. Brock K K, Mutic S, McNutt T R, et al. Use of image registration and fusion algorithms and techniques in radiotherapy: Report of the AAPM Radiation Therapy Committee Task Group No. 132[J]. Medical physics, 2017, 44(7): e43-e76.
[3]. Shackelford J, Kandasamy N, Sharp G. Deformable Volumetric Registration Using B-Splines[M]//GPU Computing Gems Emerald Edition. Morgan Kaufmann, 2011: 751-770.
