---
layout: page
title: AutoCharge
description: Autonomous docking of charger with an Autonomous Forklift
img: assets/img/vecna.jpeg
importance: 1
category: work
---

### <span style="color:#ff4703">Acknowledgements</span>

The project was part of my summer internship at [Vecna Robotics](https://www.vecnarobotics.com/) whee I worked as a Research & Advanced Development intern.

### <span style="color:#ff4703">Objective</span>

To simulate, test, and deploy monocular ORB-SLAM2 on a mobile robot using Raspberry Pi and Pi Camera V2.

### <span style="color:#ff4703">Short Pipeline</span>

<div class="row justify-content-sm-center">
    {% include figure.html path="assets/img/project-1_orbslam/pipeline.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    <strong>Master-Slave Pipeline for Deployment.</strong> A video stream from the Pi Camera is chopped into images at regular intervals by a Slave Raspberry Pi 3B+. These images are sent to a Master Computer that publishes the image feed as a ROS topic. This is read by ORB-SLAM2's system which performs the necessary mapping and localization.
</div>

### <span style="color:#ff4703">Sample Results</span>

We tested some of the results by free hand moving the Pi Camera in an indoor setting i.e., a study desk. By increasing the number of sampled features, we obtained denser reconstructions of the desk with reduced localization error.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project-1_orbslam/feats_new.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Results on sample indoor setting.</strong> Displayed from left to right: RViz windows of ORB-SLAM2 running on 1000, 1500, and 2000 sampled features respectively. Red dots represent detected ORB features, green lines show odometry of the ego-camera, blue envelopes show the pose of the ego-camera at equal time intervals. 
</div>
