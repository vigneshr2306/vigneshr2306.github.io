---
layout: page
title: Multi-Object Tracking using DeepSORT
description: Multi-Object Tracking using DeepSORT
img: assets/img/deepsort.gif
importance: 1
category: work
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/deepsort.gif" title="Multi-Object Tracking using DeepSORT" class=" img-fluid rounded z-depth-1" %}

    </div>

</div>

### <span style="color:#ff4703">Objective</span>

<!-- <div class="row" text-align="justify" text-justify= "inter-word"> -->

2D image recognition tasks like object detection and instance segmentation, have made significant strides lately but beyond obtaining 2D bounding boxes or pixel masks, 3D comprehension is avidly sought in many major applications including autonomous driving and augmented reality. A growing amount of 3D data is being gathered and processed as a result of the widespread use of 3D sensors on mobile devices and autonomous cars.
In light of this, there is an increasing demand for 3D object detection models that classify accurately and estimate the oriented 3D bounding boxes of actual objects using multi-sensor data. This work leverages a multi-stage sensor fusion concept that develops on top of Frustum PointPillar as a baseline by leveraging robust 2D object detectors as priors to build a 3D viewing frustum that predicts a 3D bounding box of the object from the points in the frustum.
We propose to modify the Frustum-PointPillar architecture to make it an end-to-end network by adding the 2D detection model, YOLOv7, as part of the learning pipeline. This work also replaces the object masking technique present in with a semantic segmented mask which improves the Average Precision by 3%.
All models are tested and evaluated with the baseline on the KITTI 3D detection benchmark involving the camera and Velodyne point clouds. <br /><br />

<!-- </div> -->

### <span style="color:#ff4703">Architecture</span>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/our_arch.png" title="Our Architecture" class="img-fluid rounded z-depth-1" %}

    </div>

</div>
<div class="row justify-content-sm-center">

The main contributions of our work over F-Pointpillars are as follows.

1. State-of-the-art 2D Object Detector <br />
   The major drawback of F-PointPillars is that the pipeline is not end-to-end, and the 2D bounding boxes are assumed to be given. This makes it impractical for real-time applications like autonomous driving. Therefore, we leveraged the robust state-of-the-art 2D object detector YOLOv7 for generating the 2D bounding boxes of objects which can be used as a prior for constructing the frustum proposal and detecting 3D objects from point clouds.<br /><br />

2. Segmentation Masking for Frustum Proposal
   Frustum PointPillars proposes a Gaussian masking technique to mask the point clouds for better localization of objects as shown in Fig.(a) below. However, this mask naively takes the euclidian distance of the projected point clouds from the center of the object, which makes the farther points from center less significant. Therefore, we propose a segmentation layer on top of the YOLOv7-detected bounding boxes using pre-trained PSPNet, which focuses on the entire object of interest, thus improving the localization of the object. Fig.(b) shows segmented mask of the same person. <br /><br />

Semantic segmentation associates a label or category with every pixel in an image. The pipeline involves PSPNet segmenting the entire image, giving us probability scores for every pixel. We iterate through every object present in the image given by YOLOv7, and extract the probability scores from the segmented image, and use these scores as mask for the 3D-to-2D projected lidar points.

</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/mask.png" title="Mask" class="img-fluid rounded z-depth-1" %}

    </div>

</div>

For more details, read our report [here](https://drive.google.com/file/d/1KLv457e_vkcNQ700JmX1KLAumDq6jrzX/view?usp=sharing)

### <span style="color:#ff4703">Code</span>

[Click here to view the code on Github](https://github.com/vigneshr2306/SegMask-Frustum-PointPillar)
