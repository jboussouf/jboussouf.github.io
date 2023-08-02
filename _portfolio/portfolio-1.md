---
title: "Advancing Diabetic Retinopathy Detection: Fine-Tuning VIT Models"
excerpt: "This work focuses on advancing the detection of diabetic retinopathy through the implementation of Vision Transformer (ViT) models, as state-of-the-art deep learning approach to computer vision.<br/><img src='/images/Retinopathy.png'>"
collection: portfolio
---

This work focuses on advancing the detection of diabetic retinopathy through the implementation of Vision Transformer (ViT) models, a state-of-the-art deep learning approach to computer vision. The system automates the identification of levels of diabetic retinopathy by classifying retinal images into three categories. The ViT model is meticulously trained on a large dataset of retinal images from Kaggle (available at <a href="https://www.kaggle.com/datasets/amanneo/diabetic-retinopathy-resized-arranged">amanneo/diabetic-retinopathy-resized-arranged</a>).

<br/><img src='/images/Retinopathy.png'>

<h2>Data PreProcessing</h2>

In order to simplify the classification task and streamline the analysis process, the original dataset, consisting of five classes based on the severity of diabetic retinopathy, has been transformed into three classes. The new class structure is as follows:

<ul>
    <li>0 - No DR : This class remains unchanged and represents images of eyes without any signs of diabetic retinopathy</li>
    <li>1 - Mild : This class combines the original "Mild" and "Moderate" classes. Images in this class exhibit mild to moderate signs of diabetic retinopathy, representing the initial and intermediate stages of the condition</li>
    <li>2 - Proliferative : This class combines the original "Severe" and "Proliferative DR" classes. Images in this class depict severe manifestations of diabetic retinopathy, indicating an advanced stage of the disease and the potential for vision loss.</li>
</ul>


<figure>
  <img src="/images/Tsne_visualization.png">
  <figcaption>Distribution of the Dataset after compression</figcaption>
</figure>