## Hand & Landmark Detection ##

**Hand Detection** involves identifying and localizing hands in visual data, while **Hand Landmark Estimation** focuses on detecting key points — such as fingertips, knuckles, and the wrist — enabling precise tracking of hand motion. These capabilities are essential for applications like **gesture recognition**, **sign language interpretation**, **VR/AR**, and **human-computer interaction (HCI)**.

One key limitation of standard solutions, such as **MediaPipe**, is their reduced accuracy on **infrared (IR)** and **grayscale** images. Since MediaPipe’s models are trained primarily on RGB data under good lighting, they often fail in domains like **driver monitoring systems (DMS)** or **low-light medical applications**, where IR imaging is the norm. Additionally, detecting hands in various gestures and sizes is a challenge, as variations in hand pose, scale, lighting, contrast, and sensor noise can significantly impact detection accuracy.

To overcome this, I led the development of a specialized hand landmark detector tailored for grayscale and IR inputs — robust to variations in **gesture**, **lighting**, **scale**, and **sensor noise**.

---

<div style="text-align: center;">
  <img src="images/hand_detection_ir_collage.png?raw=true" width="80%" height="80%"/>
</div>

### 🧠 Self-Training on Unlabeled IR Data ###

To address the lack of labeled IR datasets, we adopted a **self-training (pseudo-labeling)** strategy:

1. **Initial training:** Fine-tuned a baseline on labeled RGB data (via MediaPipe).  
2. **Labeling unlabeled IR data:** Used the model to generate confident predictions.  
3. **Pseudo-labeling:** Filtered and retained high-confidence predictions.  
4. **Fine-tuning:** Combined pseudo-labeled and original data to improve performance.  
5. **Iterative refinement:** Repeated the process, increasing robustness at each step.

---

### 🔍 Hand Landmark Pipeline Overview ###

+ **Hand Detection:** The first step involves detecting and localizing the hand in an image or video stream. Based on **YOLOv5**, trained to detect hands across various poses, lighting, and camera types.  
+ **Hand Region Crop & Normalization:**  Once the hand is detected, the next step is to extract the region of interest (ROI) that contains the hand. The cropped hand region is then normalized to ensure consistent input size and orientation. 
+ **Landmark Estimation:** This step identifies key points or landmarks on the hand, such as fingertips, knuckles, and wrist. We train a **multi-branch regression model** to accurately estimate the positions of 21 key hand landmarks.

---

### 🤘 Hand Motion Detection Module ###

This module involves analyzing the detected hand landmarks to identify specific gestures or track hand movements. By evaluating the relative positions and movements of the landmarks, the system can recognize predefined gestures or track dynamic hand motions.
Algorithms for various gestures and motions, such as **pinch**, **pinch and hold**, **pinch and drag**, **zoom in**, **zoom out**, and **hand rotation**, are implemented by analyzing these relative positions over time.
The **full pipeline**, including **hand landmark detection** and **motion classification**, runs at **150+ FPS on CPU**, enabling **real-time hand motion control** in edge devices.

<div style="text-align: center;">
  <img src="images/motions_short.gif?raw=true" width="80%" height="80%"/>
</div>

When integrated with ***[Gaze Estimation](../gaze_estimation_project/gaze_estimation.md)*** in **HCI systems**, this creates a seamless multimodal interface — ideal for **smart homes**, **automotive interfaces**, **VR/AR**, and **touchless UIs**.

<div style="text-align: center;">
  <img src="images/one_hand_control_video3_long.gif?raw=true" width="60%" height="60%"/>
</div>

