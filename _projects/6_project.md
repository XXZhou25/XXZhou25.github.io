---
layout: page
title: Measuring sperm cell length
description: Computational Geometry related, corperated with Yukun Li
img: 
importance: 2
category: Course Projects
redirect: https://github.com/XXZhou25/Measuring-sperm-cell-length/blob/main/report.pdf 
---

<h3 class="container-title"> Introduction </h3>

In the life science area, some scientists study the genetic basis of sperm length and need to look at the effect on sperm length while knocking out individual genes. So, it is essential to measure the length of sperm cells quickly and accurately. And it is unreliable to undertake such a task via manually selecting the location of cells. Therefore, there is a need to find a better method to measure the length of cells automatically. In this project, it built an interactive tool to measure the sperm cell length semi-automatically. The programming language is Python. It used PyQt5 to implement GUI, Numpy,OpenCV to implement algorithms.

<h3 class="container-title"> Reuired Features </h3>
<ol>
    <li>Calculate the length of sperm cells from images (shown in Fig.1) automatically </li>
    <li>Users can draw region-of-interest </li>
    <li>The threshold value can be selected by users as needed </li>
</ol>


<h3 class="container-title"> Methods </h3>

<ol>
    <li>Preprocess </li>
    	<ul> 
    		<li>For low-contrast images, histogram equalization was applied to enhace the image contrast. </li>
    		<li>Normalization[1] was performed to remove the gray-level deformation by subtracting an approxi- mate background from the original gray image. The approximate background is estimated using a 25*25 median filter on the original image. We use this to remove te big spot noises.</li>
    		<li>The adaptive local thresholds were applied to the normalized image.Fig.5 Adaptive thresholding was chosen because the image had different lighting conditions in different areas, and adaptive thresholding could calculate threshold values based on surrounding pixels.</li>
   		</ul>
    <li>Extract cells </li>
    <li>Apply user interaction to remove some spurious branches from the thinning results. For this step, we ask the user to choose several points on the part you want to remove, and then it can detect the closest point on the closest component and set the 3*3 neighbor of that point to 0. Then it refind the largest component and return that component. </li>
    <li>Calculate sperm cell length</li>
</ol>

<h3 class="container-title"> GUI </h3>

GUI was implemented using PyQt5. PyQt5 is a comprehensive set of Python bindings for Qt v5.[2] We used opencv to read and preprocess the images. The pipeline is shown in Fig14. It will automaticallystore the intermediate image generated during the process.

