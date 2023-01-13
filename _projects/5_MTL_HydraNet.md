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
        {% include figure.html path="assets/img/mtl_arch.jpeg" title="Architecture" class="img-fluid rounded z-depth-1" %}

    </div>

</div>
<div class="row justify-content-sm-center">

Multi-task learning (MTL) is a technique in deep learning where a single neural network is trained to perform multiple tasks simultaneously. This approach can improve the performance of the network on all tasks, as the network learns to share information and representations among the tasks.<br /><br />

One common way to implement MTL is to use a shared base network, with task-specific layers attached on top. The shared base network learns a general representation of the input data, while the task-specific layers learn the task-specific features. This allows the network to reuse the learned features across different tasks, reducing the amount of data and computation required for each task.<br /><br />

Another way to implement MTL is to use a network with multiple heads, where each head is responsible for a different task. The multiple heads can be trained together, allowing the network to learn shared representations across the tasks. This approach can be useful when the tasks are highly related and the data for each task is limited.<br /><br />

</div>
### <span style="color:#ff4703">Code</span>

[Click here to view the code on Github](https://github.com/vigneshr2306/Multi-Task-Learning)
