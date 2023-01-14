---
layout: post
title: Attention is all you need
date: 2022-10-07 23:13:27
description: Attention is all you need Paper Review
# tags: jekyll blogs
categories: paper-review
---

Citation: Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Łukasz Kaiser, and Illia Polosukhin. 2017. Attention is all you need. In Proceedings of the 31st International Conference on Neural Information Processing Systems (NIPS'17).<br /><br />
Brief Summary:<br />
Recurrent Neural Networks (RNN), Long Short Term Memory (LSTM) and Sequence Sequence Models are popular approaches to solving tasks such as Image Captioning, Langage Translation, etc. However, they deal with the input in a sequential manner, which is often time-consuming and does not use the parallel processing power of modern computing techniques. Sequential data processing also has the disadvantages of the popular vanishing gradient problem when the sequence is too long. This paper solves these issues by proposing a novel architecture called the Transformer, which is solely based on attention mechanisms. The architecture uses an encoder-decoder model with I/O embedding and positional encoding layers. The Multi-Headed Attention and Masked Multi-Headed Attention layers allow dependency modeling without considering their distance in the input or output sequences. The model achieves 28.4 BLEU on the WMT 2014 English-to-German translation task.<br /><br />

Main Contributions:<br />
The recurrent layers most frequently employed in encoder-decoder designs are replaced with multi-headed self-attention in this study, which is the first transduction model based purely on attention.
The paper achieves state-of-the-art results in language translation tasks and paved the way for future research in this field for papers such as BERT and ViT.<br /><br />
Strengths:<br />
The transformer can be trained significantly faster than architectures based on recurrent or convolutional layers for translation tasks.
In situations when the sequence length is less than the representation dimensionality, self-attention layers perform faster than recurrent layers. <br />
The paper is well-written and easy to read. The code is provided which helps in reproducing the results for further research.<br /><br />
Weakness:<br />
The paper lacks mathematical explanation in parts such as multi-headed attention.<br />
The model contains too many hyperparameters, without tests for significant configurations.<br />
The paper also lacks figures and graphs that could help analyze the results better.<br /><br />

In-Depth Analysis of Strengths and Weaknesses:<br />
RNNs and LSTMs are usually employed for tasks such as image captioning, which consists of recurrent layers. This is replaced with multi-headed self-attention, which is the first transduction model based purely on attention. This block is used to give the word embedding inputs more contextual information. A self-attention module functions by reweighing the word embeddings of each word to account for contextual importance and comparing each word in the phrase to every other word in the sentence, including itself. The algorithm receives N word embeddings without context and outputs N word embeddings with context. <br />
The model achieves 28.4 BLEU on the WMT 2014 English-to-German translation task, which beats state-of-the-art results. The paper is also well written, with code provided for reproducibility, which is the reason that led to revolutionizing the industry with several transformer-like architectures.<br />
The transformers can take in parallel inputs, which helps in using the modern GPU parallel processing power. This makes transformers train several times faster than LSTMs. Even though LSTMs are used to avoid vanishing gradient problems, when the sequential input is too long, there exists a vanishing gradient, and this can be avoided using transformers as they process the inputs in parallel.<br />
As for the weakness of the paper is concerned, the paper consists of several hyperparameters, but the significance of the configurations could have been explained better. The authors could have also added some more mathematical explanations on the multi-headed attention part.<br /><br />
Experimental Results:<br />
The Adam optimizer was used to train the design, and the learning rate was first raised and then reduced. In order to avoid overfitting, residual dropout was employed as a regularization strategy. Label smoothing was also utilized so that the model gradually learns to be more uncertain, improving accuracy as a result of more data-driven learning.<br />
The transformer model performs better than the previous state-of-the-art by over 2 BLEU in the English-to-German translation, with a score of 28.4. The training was done for 3.5 days on 8 P100 GPUs. For the English-to-French translation, the BLEU score turned out to be 41.0. <br />
Different model variations are done on the model to evaluate different parts of the transformer. It is observed that reducing the attention key size reduces model quality. It is also seen that bigger models are better, and dropout is very helpful in avoiding over-fitting.<br /><br />
Extensions:<br />
The transformer model that is explained in this paper has been tested only with machine translation models. This can be extended to applications such as image, audio, and video processing. <br /><br />
Comments:<br />
In fact, the state-of-the-art in object detection and image segmentation in the industry uses transformers in it. This would not have been possible without this paper, and hence shows how much this paper has impacted the development of this field.
