---
title: "Overcoming Speech Recognition Challenges with GAN based Solutions"
excerpt: "This study applies deep learning techniques to improve speech recognition in different environments, including noisy situations. The study presents the results of a Convolutional Neural Network (CNN) model that achieved high accuracy in recognizing spoken words in clean audio data but struggled as noise levels increased. <br/><img src='/images/GAN.png'>"
collection: portfolio
---

This study applies deep learning techniques to improve speech recognition in different environments, including noisy situations. The study presents the results of a Convolutional Neural Network (CNN) model that achieved high accuracy in recognizing spoken words in clean audio data but struggled as noise levels increased. An attempt to use a simple autoencoder to remove noise from the audio data resulted in a significant decline in classification performance, indicating the need for more advanced denoising techniques. The study proposes the Speech enhancement Generative Adversarial Network (SEGAN) as a solution to improve speech recognition's robustness by generating clean speech signals from noisy inputs. The results demonstrate the potential of deep learning techniques in improving speech recognition technology, but careful evaluation of various components and techniques is crucial for optimal performance.<br/><img src='/images/GAN.png'>

<h2>Data Presentation</h2>

In this project, we introduce a meticulously curated dataset that serves as the backbone for tackling the Speech Recognition Challenges using GAN-based solutions. The dataset comprises WAV audio files, each precisely one second in length, making it a perfect fit for training and evaluating speech recognition models. Our carefully selected dataset is sourced from Kaggle and is openly available to the research community at the following URL: <a href="https://www.kaggle.com/datasets/wangshaoqi/speech-commands">wangshaoqi/speech-commands</a>. 

This dataset is a valuable resource for anyone looking to delve into the fascinating domain of speech recognition and explore the potential of Generative Adversarial Networks (GANs) for enhancing speech processing systems. With diverse audio samples representing various speech commands, our dataset promises to foster innovative and robust advancements in the field of automatic speech recognition.

In this project, we have chosen to work with just three words: "one," "two," and "three." These carefully selected words represent essential phonetic elements and will simplify the initial stages of training and evaluation.

<h2>Data Transformation</h2>

In addition to transforming the audio data into spectrogram format, we will augment the dataset by introducing random noise at different levels. Data augmentation is a powerful technique that helps improve the robustness and generalization of our models. By injecting random noise into the audio samples at varying intensities, we simulate real-world environmental factors and add variability to the training data. This approach allows our models to become more resilient to noise and other distortions commonly encountered in practical speech recognition scenarios. 

Spectrogram format of bowth data with noise and without noise:
<br/><img src='/images/data_noise_without_noise.png'>

<h2>Classification Model</h2>

For our speech recognition task, we employed a Convolutional Neural Network (CNN) architecture. The model architecture consists of multiple convolutional layers, each followed by max-pooling layers to downsample the spatial dimensions of the feature maps. The first two convolutional layers have 128 filters, while the subsequent two have 64 filters. The final convolutional layer has 32 filters before flattening the output to connect to a fully connected (dense) layer with three neurons, representing the three target classes "one," "two," and "three." The model has a total of 543,747 trainable parameters, making it an efficient choice for our speech recognition task. By training this CNN architecture on the transformed spectrogram data enriched with random noise, we aim to develop robust GAN-based solutions for accurate and efficient speech recognition.

CNN architecture:
<br/><img src='/images/cnn_architect.png'>

The loss nad accuracy of the CNN Model:
<div style="display: flex;">
  <div style="width: 50%; height: auto; margin: 10px;"><br/><img src='/images/loss_cnn_SEGAN.png'></div>
  <div style="width: 50%; height: auto; margin: 10px;"><img src='/images/accur_cnn_SEGAN.png'>
</div>
</div>