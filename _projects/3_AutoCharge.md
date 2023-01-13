---
layout: page
title: AutoCharge
description: Autonomous docking of charger with an Autonomous Forklift
img: assets/img/vecna.png
importance: 1
category: work
---

<!-- ### <span style="color:#ff4703">a</span> -->

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/vecna.png" title="autocharge" class="img-fluid rounded z-depth-1" %}

    </div>

</div>
### <span style="color:#ff4703">Acknowledgements</span>
The project was part of my summer internship at [Vecna Robotics](https://www.vecnarobotics.com/) where I worked as a Research & Advanced Development intern.
### <span style="color:#ff4703">Objective</span>
A robot that can charge an Autonomous Mobile Robot (AMR) automatically if it is within the vicinity. The robot consists of a Stewart Platform with the electrical plug connected to its plate that connects to the socket of the AMR. Increases AMR productivity and decreases manual labour which are key to warehouse management.
### <span style="color:#ff4703">Short Pipeline</span>


1. Stereo camera in the robot detects at the ArUco markers on the AMR and provides the desired charger's plug pose as a topic in ROS2.<br />
2. Kinematics and velocity controllers were implemented in the microcontroller running Zephyr RTOS and messages are passed using micro-ROS at 1000Hz. <br />
3. Various filter algorithms like Kalman Filter and Moving-Average filters were used to denoise the sensor inputs and the resulting PWM signals were sent to the motor. <br />

### <span style="color:#ff4703">Video</span>

[Click here to watch the video on YouTube](https://youtu.be/MfdbfeNWv3E)
