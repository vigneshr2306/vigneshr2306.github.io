---
layout: post
title: Group Normalization
date: 2022-10-07 23:13:27
description: Group Normalization Paper Review
# tags: CV DL
categories: paper-review
---

Citation: Wu, Yuxin & He, Kaiming. (2018). Group Normalization, European Conference on Computer Vision.<br /><br />
Brief Summary:<br />
This paper proposes a new type of normalization technique for deep neural networks called Group Normalization (GN), which involves computing the mean and variance for normalization based on dividing the channels into groups. This technique is advantageous compared to Batch Normalization (BN), where the same parameters were calculated based on dividing the samples into batches. The latter technique was not able to perform well with smaller batch sizes, which is where GN scores as it is not sensitive to batch sizes. GN performs better than BN in several tasks like segmentation, and detection, and on the ImageNet dataset trained with ResNet-50 architecture with a batch size of 2, GN has a 10.6% lower error rate compared to BN. <br /><br />
Main Contributions:<br />
The idea of considering deep neural network features as structured vectors that can be grouped together.
A novel normalization technique that beats the state-of-the-art normalization techniques with its lesser error rate.
Independent to batch size helps in drastically reducing the error rates.
Increases the pool of domains where normalization can be performed because of its adaptability to huge model-size applications.<br /><br />
Strengths:<br />
Stable results were shown using Group Normalization with different batch sizes and datasets.
Group Normalization can naturally transfer from pretraining to fine-tuning.
The paper is well-written, with good structure, and is backed by several experimental results and figures.<br /><br />
Weakness:<br />
The only weakness of this research work is that all the previous state-of-the-art models are tuned for BN, which makes GN less popular as it is difficult for tuning hyperparameters.<br /><br />
In-Depth Analysis of Strengths and Weaknesses:<br />
The key idea behind Group Normalization is to not think of deep neural network features as unstructured vectors, but consider the corresponding channels of these features to be normalized together. The coefficients of these vectors can be interdependent; each group of channels is assumed to have a shared mean and variance, which leads to GN.<br />
Since the grouping is done across the channels, GN is independent of batch size and can work relatively well with batch sizes as small as 2, to higher batch sizes as well. Due to this property, GNs are independent of batch size, which acts as a huge advantage compared to BN.<br />
This independence to batch size opens a plethora of opportunities for GN to be implemented. There were heavy trade-offs between model size and batches in applications such as object detection, and segmentation, which was not the case with GNs. Hence, it was able to produce 10.6% lower error rates compared to BN in the ImageNet dataset.
GNs have the ability to naturally change to fine-tuning from pre-training, even though they use different batch sizes. The results of GNs in this paper were stable and comprehensive, tested with different datasets and batch sizes, which will be explained in the next section.<br />
Overall, the quality of the paper is good, with clear notations and enough experiments to support their hypothesis. The previous literature was clearly explained with intuitive figures which makes it easy to understand the paper.<br />
Even though GN outperforms BN almost everywhere, BN is still the most popular choice in the industry for normalization, due to several state-of-the-art models and their hyperparameters tuned for BN, and the results of papers not being able to do fair comparisons otherwise.<br /><br />
Experimental Results:<br />
In the Image Classification experiment in the ImageNet dataset with ResNet architecture, BN, GN, Layer Norm. (LN) and Instance Norm. (IN) were compared for batch sizes 2 to 32 with increments in powers of 2. It can be seen that for higher batch sizes like 32, the error rate of BN is better than GN and GN approaches BN with degradation of 0.5%. As batch size decreases, the error rate of GN improves significantly and achieves a 10.6% lower error rate than BN. Batch Renorm. is also compared with GN, but GN outperforms it by 2.1%. Experiments were also conducted with different number of groups and different channels per group and the results were compared with the ideal channel number which has the lowest error rate.<br /><br />
Using high-resolution images for Object Detection and Segmentation in the COCO dataset results in a lesser batch size; hence BN layer is linearized to a pre-computed frozen model called BN*. Mask R-CNN is used as a baseline, conv4 is used as a backbone, and the Average Precision (AP) is reported. It is seen that GN improves over BN* by 1.1 box AP and 0.8 mask AP. It is also trained on the FPN backbone, where the final ResNet-50 GN model is 2.2 points box AP and 1.6 points mask AP better than its BN\* variant. Training in the Mask R-CNN from scratch, GN was able to achieve 41.0 box AP and 36.4 mask AP, which are the best results for the COCO dataset from scratch.
In the Video Classification with Kinetics dataset, Inflated 3D (I3D) with ResNet-50 I3D baseline was used. Extending the normalization over the temporal axis, we train in the 400-class set with 32 and 64-frame input clips. For the batch size of 8 with 32 frame input, BN performs better than GN by 0.3% top-1 accuracy and 0.1% top-5. As batch size reduces to 4, BN’s accuracy is decreased by 1.2% while the GN remains the same. On the 64-frame input, GN’s accuracy is increased by 1.7% due to longer clip and temporal length, while BN’s accuracy reduces due to lesser batch size.<br /><br />
Extensions:<br />
The applications of Group Normalization on generative models like GANs, sequential models like RNNs and LSTMs, and reinforcement learning models can be analyzed deeply, given their success in replacing Layer Normalization and Instance Normalization in visual recognition tasks. Additionally, there is scope for learning why BN outperforms GN in a few conditions. GN lacks the regularization ability of BN as BN computation involves stochastic batch sampling, which helps in regularization, and this can be analyzed with a regularizer added to GN to improve the results. <br /><br />
Comments:<br />
Upon further research, I found that the extension mentioned in the previous section about the regularizer added with GN was employed in the Big Transfer (BiT): General Visual Representation Learning paper in 2019. Given the excellent performance of GN, I hope to see future models being tuned to GN, which will give better results, and help move deep learning research forward.
