## Gaze Direction Estimation ##

Gaze direction estimation is the process of determining where a person is looking based on images or video frames. It’s widely used in applications such as **driver monitoring systems**, **virtual and augmented reality**, **human-computer interaction**, and **medical diagnostics**.

This project focuses on delivering **real-time**, **high-precision** gaze estimation with deep learning — enabling **natural interaction** and **safety-critical responses** in consumer tech.

I lead the development of gaze estimation models for various screen sizes and introduced a novel **Gaze Vector** approach to replace the traditional **Point of Gaze** method.  
This new method improved gaze estimation accuracy by **8%** across devices ranging from **phones and tablets to monitors as large as 55"**.  
The models demonstrate high robustness, achieving **prediction errors as low as 6% of screen size**, with **execution time of ~5.5 ms (180 FPS)** on a CPU.

---

<div style="text-align: center;">
  <img src="images/gaze_vector_image_upd.png?raw=true" width="40%" height="40%"/>
</div>

### 🔍 Techniques Overview ###

Gaze estimation techniques can be broadly categorized into:

+ **Model-based methods:** relies on geometric and anatomical models of the human eye and head. It typically uses explicit feature extraction techniques, where the system detects key elements such as the pupil center, iris contour, corneal reflections, and eye corners.
+ **Appearance-based methods:** Learn gaze patterns from raw image data using deep learning or machine learning models. These methods treat gaze estimation as a regression or classification problem.  

We focus on an **appearance-based approach** using a modular deep learning pipeline:

### 🧩 Pipeline Modules ###

**➤ Face Detection:** The first step is identifying and locating the face within an image. **[YOLOv5Face](https://arxiv.org/pdf/2105.12931)**-based models are trained to detect faces under varying camera angles, head poses, lighting conditions, distances from the camera, and across different camera types (such as RGB and IR).

**➤ Landmark Detection:** Once the face is detected, facial landmarks are identified. These landmarks mark key facial features such as the eyes, eyebrows, and nose. Landmark detection is essential for understanding the relative positions of the eyes, which are crucial for gaze estimation. We train a **multi-branch regression model** to accurately estimate the landmarks.

**➤ Head Pose Calculation:** The head pose calculation estimates the location and orientation of the head in 3D space (X, Y, Z, pitch, yaw, and roll). This information is critical, as it helps adjust gaze direction estimation based on the angle at which the person is facing the camera. We use the **PnP (Perspective-n-Point)** method to estimate head rotation and location from facial landmarks.

**➤ Eye Crop Extraction:** After detecting facial landmarks, the next step involves extracting the regions of interest (ROIs) around the eyes. These regions are then cropped to focus specifically on the eye areas, ensuring that gaze tracking remains precise and unaffected by other facial features.

**➤ Eye Status Classification:** In this module, the system determines the status of the eyes, such as whether they are open or closed, and whether they are free or occluded by sunglasses or a hand. This step is important for the application to understand whether the gaze direction can be reliably calculated. If the eyes are closed or obstructed, gaze estimation may not be feasible. We train CNN classifiers based on the **MobileNetV3** backbone to classify the different states of each eye.

**➤ Gaze Direction Estimation:** Finally, the gaze direction is estimated based on the information gathered from the previous modules. This step involves analyzing the eye region along with the head pose to predict where the user is looking (e.g., gaze points on a screen or in 3D space). We train a **CNN-based regressor** to make this prediction, using the extracted eye crops, head pose, and reference frame from the calibration phase to accurately estimate the user's gaze direction.

The Gaze Estimation module, when integrated with ***[Gesture Recognition](../hand_detection_project/hand_detection.md)*** module in Human-Computer Interaction (HCI), plays a critical role in enhancing user interaction by allowing users to control devices or applications through gestures and gaze tracking.


<div style="text-align: center;">
  <img src="images/driver video.gif?raw=true" width="80%" height="80%"/>
</div>



