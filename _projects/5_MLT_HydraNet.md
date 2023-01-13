---
layout: page
title: Multi-Task Learning HydraNets for Autonomous Driving
description: Multi-Task Learning HydraNets for Autonomous Driving
img: assets/img/mtl.gif
importance: 1
category: work
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/mtl.gif" title="Multi-Task Learning HydraNets for Autonomous Driving " class=" img-fluid rounded z-depth-1" %}

    </div>

</div>

### <span style="color:#ff4703">Objective</span>

This project refers to the paper [Real-Time Joint Semantic Segmentation and Depth Estimation Using Asymmetric Annotations](https://arxiv.org/pdf/1809.04766.pdf) to implement a model that can perform multiple tasks such as semantic segmentation and depth estimation at once.

### <span style="color:#ff4703">Architecture</span>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/mtl_arch.jpeg" title="Our Architecture" class="img-fluid rounded z-depth-1" %}

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

### <span style="color:#ff4703">Code</span>

[Click here to view the code on Github](https://github.com/vigneshr2306/Multi-Task-Learning)
