## Age and Gender Estimation ##

**Age and gender estimation** from facial images is a core task in computer vision, widely applied in **security**, **marketing**, **HCI**, and **social analytics**. It aims to predict a person’s **age** and **gender** using deep **convolutional neural networks (CNNs)**, overcoming challenges like varied lighting, facial expressions, occlusions, and headwear.

As part of my role at **Blink Technologies**, I led the development of high-accuracy models for age and gender prediction. This included the creation of balanced training datasets, development of network architectures, and deployment optimization. 
The models achieved:

+ 🎯 **94.9% [1-Class Off Accuracy (1CoA)](https://arxiv.org/abs/2108.08186) for age prediction**
+ 🚻 **99% accuracy for gender classification**
---

<div style="text-align: center;">
  <img src="images/AgeGenderImage.jpg?raw=true" width="60%" height="60%">
</div>

### 🧠 Feature Engineering: Face Embeddings
Instead of raw images, I used **facial embeddings** as input features. These 512D vectors, extracted using the [ArcFace](https://insightface.ai/arcface?utm_source=chatgpt.com) (InsightFace) model, provide compact and discriminative face representations. ArcFace’s **additive angular margin loss (AAM)** ensures robust identity separation.

### 🧬 Dataset Curation with Synthetic Balancing
Training data was aggregated from several large-scale datasets:

+ IMDB-WIKI
+ UTKFace
+ Adience
+ MORPH2
+ FG-NET

These datasets were **age-imbalanced**, especially for children and seniors. To solve this, I used **[SAM (Style-based Age Manipulation)](https://yuval-alaluf.github.io/SAM/)**, a GAN-based method to generate **synthetic faces** across different age groups, enriching the training distribution.


<div style="text-align: center;">
  <img src="images/SAM.png?raw=true" width="60%" height="60%">
</div>

### 🏗️ Network Architecture & Training
A lightweight **MLP (Multilayer Perceptron)** with skip connections was trained on the face embeddings:

+ ⚙️ Skip connections enhance gradient flow and feature reuse
+ ⚖️ Age estimation treated as **classification** (not regression) with **18 classes (5-year bins)** from age 0–90
+ 🔁 Gender classification trained jointly with a separate output head


This classifier-based formulation reduced noise and improved **stability**, **generalization**, and **runtime performance**.

<div style="text-align: center;">
  <img src="images/andrey_age.gif?raw=true"/>
</div>



