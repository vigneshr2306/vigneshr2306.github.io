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

Multi-object tracking (MOT) is a challenging task in computer vision that involves identifying and tracking multiple objects in a video sequence. One popular method for MOT is DeepSORT, which combines the Hungarian algorithm, Kalman filter, and Siamese networks. <br /><br />

<!-- </div> -->

### <span style="color:#ff4703">Architecture</span>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/mot.jpeg" title="Our Architecture" class="img-fluid rounded z-depth-1" %}

    </div>

</div>
    [Source](https://medium.com/augmented-startups/deepsort-deep-learning-applied-to-object-tracking-924f59f99104)

<div class="row justify-content-sm-center">

The Hungarian algorithm is used to solve the data association problem in MOT, which involves matching detections in consecutive frames to the same object. The Kalman filter is then used to estimate the state of each object, including its position and velocity, based on the matched detections.<br /><br />

The Siamese network component of DeepSORT is used for re-identification, which is the task of matching detections of the same object across different frames. The network is trained to learn a feature representation of the object that is invariant to appearance changes caused by factors such as lighting and viewpoint.<br /><br />

The combination of these three components allows DeepSORT to accurately track multiple objects in a video sequence, even in challenging scenarios with heavy occlusion and clutter. The use of siamese networks also allows for online learning, updating the model as new observations come in.<br /><br />

</div>

### <span style="color:#ff4703">Code</span>

[Click here to view the code on Github](https://github.com/vigneshr2306/SegMask-Frustum-PointPillar)
