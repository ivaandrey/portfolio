## Hand Detection and Hand Landmark Estimation  ##

**Hand Detection** involves identifying and localizing hands in images or video streams. **Hand Landmark Estimation** focuses on identifying key points on the hand, such as fingertips, knuckles, and the wrist, enabling detailed tracking of hand movements. Both of these modules are essential for applications such as gesture recognition, sign language interpretation, virtual and augmented reality (VR/AR), and human-computer interaction (HCI).

One of the drawbacks of widely used MediaPipe models is their reduced accuracy when applied to IR and grayscale images. MediaPipe's Hand Landmark Detection is primarily trained on RGB images, assuming good lighting and clear hand visibility. However, many applications, such as driver monitoring systems (DMS) that use IR cameras and medical applications that operate under poor lighting conditions, require reliable hand landmark detection in grayscale or IR images. Additionally, detecting hands in various gestures and sizes is a challenge, as variations in hand pose, scale, lighting, contrast, and sensor noise can significantly impact detection accuracy. **Given these challenges, our company decided to develop a specialized hand landmark detector for grayscale and IR images**.

---

<div style="text-align: center;">
  <img src="images/hand_detection_ir_collage.png?raw=true" width="60%" height="60%"/>
</div>

To train the model on unlabeled IR or grayscale images, the **Self-Training** or **Self-Labeling** method is used. In this process, a model is initially trained on a small set of labeled data. Then, it is used to predict labels for the unlabeled data. The predicted labels (often with a certain level of confidence) are then treated as ground truth and used to retrain or fine-tune the model. This process is repeated iteratively, with the model progressively refining its predictions and improving its performance.

Key steps in self-training typically include:

1. **Initial training:** Train a model on a small labeled dataset (labeled by MediPipe model).
2. **Prediction on unlabeled data:** Use the trained model to predict labels for the unlabeled data.
3. **Pseudo-labeling:** Assign labels to the unlabeled data with high-confidence predictions.
4. **Fine-tuning:** Use both the original labeled data and the newly pseudo-labeled data to fine-tune the model.
5. **Iterative process:** Repeat the process, refining the model with each iteration.


Hand Landmark Estimation pipeline consists of several key modules:
+ **Hand Detection:** The first step involves detecting and localizing the hand in an image or video stream. **YOLOv5**-based models are trained to detect hands across various gestures, lighting conditions, distances from the camera.
+ **Hand Region Crop and Normalization:** Once the hand is detected, the next step is to extract the region of interest (ROI) that contains the hand. The cropped hand region is then normalized to ensure consistent input size and orientation.
+ **Hand Landmarks Estimation:** This step identifies key points or landmarks on the hand, such as fingertips, knuckles, and wrist. We train a **multi-branch regression model** to accurately estimate the positions of 21 key hand landmarks.

### Gesture Recognition Module ###

This module involves analyzing the detected hand landmarks to identify specific gestures or track hand movements. By evaluating the relative positions and movements of the landmarks, the system can recognize predefined gestures or track dynamic hand motions.  
Algorithms for various gestures and motions, such as **closed fist**, **open hand**, **pinch**, **zoom in**, **zoom out**, and **hand rotation**, are implemented by analyzing these relative positions over time. When integrated with ***[Gaze Estimation](../gaze_estimation_project/gaze_estimation.md)*** in **Human-Computer Interaction (HCI)** it enables a more intuitive and hands-free way to interact with systems, making it particularly useful in scenarios like **smart homes**, **gaming**, **virtual and augmented reality (VR/AR)**, and **driver monitoring systems (DMS)**.

**Insert video or gif of gesture and gaze**


