---
layout: page
title: Visual Odometry using Stereo Images
description: Visual Odometry using Stereo Images (Classical Computer Vision)
img: assets/img/vizodom.png
importance: 1
category: work
---

    {% include figure.html path="aassets/img/vizodom.png" title="Visual Odometry using Stereo Images" class=" Visual Odometry using Stereo Images (Classical Computer Vision)" %}

<!-- ### <span style="color:#ff4703">Acknowledgements</span>

The project was part of my summer internship at [Vecna Robotics](https://www.vecnarobotics.com/) where I worked as a Research & Advanced Development intern. -->

### <span style="color:#ff4703">Objective</span>

Visual Odometry is a method of finding a robot/camera pose i.e translation and orientation of the robot/camera with respect to the the world frame using camera data. The study of sequential images and its corresponding points helps in calculating the displacement of the robot/camera. The consecutive pairs of the images were used to estimate the camera pose attached to the car in the data set.<br />
The set of images with the camera calibration matrix are the given parameters for this project and the output is the trajectory plot of the car/camera in the x and z axis. The output is also compared with output using pre-defined OpenCV functions. The basic concepts used for Visual Odometry can be compared to the results of SLAM which is an important topic in Image Processing and Perception.

### <span style="color:#ff4703">Short Pipeline</span>

<div class="row justify-content-sm-center">

1. The images from the Oxford RobotCar dataset folder were first loaded and then converted from Bayer format to BGR format. The Camera calibration matrix was computed followed by undistorting of the images.<br />
2. The feature points are extracted from consecutive frames to compute the Fundamental matrix, using OpenCV functions of SIFT Detector for detection and FLANN based Matcher for matching the detected feature points.<br />
3. Then after extracting these feature point correspondences, the Fundamental matrix was computed by randomly selecting 8 feature points.<br />
4. Also, after computing the Fundamental matrix from those points, a RANSAC check is used for getting the count of the inliers(corresponding feature points).The Fundamental matrix with the most numberof inliers is our optimal fundamental matrix.<br />
5. The above check was done for 50 iterations to get the optimal Fundamental matrix. The solution be can improve by increasing the number of iterations at an expense of more computation time.<br />
6. With the final Fundamental matrix, we further computed the Essential matrix using the Camera calibration matrix.<br />
7. Then the possible Camera poses were determined forming four sets of camera centres and rotation matrices.<br />
8. We assumed that the + x axis points towards right, + y axis is coming out of the page and + z axis points downwards initially. The camera poses with extreme rotation in z-axis are then neglected manually as rotation about z-axis does not have any physical relevance. These gave us the possible values of the camera poses and were further singled out based on cheirality check criteria.<br />
9. We then computed the position of the camera of the current frame with respect to the previous frame by calculating Homogeneous transformation and multiplying it with previously calculated Homogeneous matrix.<br />
10. From the calculated homogeneous transformation matrix the center of the camera frame for every frame is found plotted.<br />
11. Our output is finally matched with the output using Opencv pre-defined function such as cv2.ndEssentialMat and cv2.recoverPose.<br />
<!-- </div>
<div class="caption">
    <strong>Master-Slave Pipeline for Deployment.</strong> A video stream from the Pi Camera is chopped into images at regular intervals by a Slave Raspberry Pi 3B+. These images are sent to a Master Computer that publishes the image feed as a ROS topic. This is read by ORB-SLAM2's system which performs the necessary mapping and localization.
</div> -->

### <span style="color:#ff4703">Sample Results</span>

        {% include figure.html path="assets/img/comparison.png" title="example image" class="comparison" %}

We can see the difference in the output in the Opencv function and the code we made. We can
reduce the error by the following ways.\

1. Increasing the number of iteration of RANSAC to compute Fundamental matrix.\
2. We can use Zhang's 8-point algorithm, instead of randomly selecting correspondences between two images.\
3. The image could be normalized to get everything with respect to optical center thus having better results.

<!-- <div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project-1_orbslam/feats_new.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Results on sample indoor setting.</strong> Displayed from left to right: RViz windows of ORB-SLAM2 running on 1000, 1500, and 2000 sampled features respectively. Red dots represent detected ORB features, green lines show odometry of the ego-camera, blue envelopes show the pose of the ego-camera at equal time intervals.
</div> -->
