
## Gaze Direction Estimation ##

The gaze estimation activity I lead involves managing a team focused on an **appearance-based approach**, where I oversee the research, development, optimization, and deployment of deep learning models for gaze tracking. My responsibilities include technical leadership, such as algorithm design, model training, dataset curation, and performance evaluation. Additionally, I focus on deployment and integration into SDKs to ensure robust and accurate gaze estimation for various applications, including driver monitoring systems (DMS) and human-computer interaction (HCI).  
We develop gaze estimation models for a range of screen sizes, from phones and tablets to monitors as large as 55". Our gaze estimation models are highly robust, achieving small prediction errors ranging from **1 cm to 9 cm**, depending on the screen device, with a **running time of approximately 5.5 milliseconds (180 FPS) on a CPU**.

---

Gaze direction estimation is the process of determining where a person is looking based on images or video frames. It’s widely used in applications such as driver monitoring systems, virtual and augmented reality, human-computer interaction, and medical diagnostics.

<div style="text-align: center;">
  <img src="images/gaze_estimation_page_driver_image.png?raw=true" width="30%" height="30%"/>
</div>


Gaze estimation techniques can be broadly categorized into:

+ **Model-based methods:** relies on geometric and anatomical models of the human eye and head. It typically uses explicit feature extraction techniques, where the system detects key elements such as the pupil center, iris contour, corneal reflections, and eye corners.
+ **Appearance-based methods:** Learn gaze patterns from raw image data using deep learning or machine learning models to directly learn gaze patterns from raw images. These methods treat gaze estimation as a regression or classification problem.  

---

The gaze estimation pipeline consists of several key modules, each playing a crucial role in accurately predicting the gaze direction:

+ **Face Detection:** The first step is identifying and locating the face within an image. **YOLOv5**-based models are trained to detect faces under varying camera angles, head poses, lighting conditions, distances from the camera, and across different camera types (such as RGB and IR).

+ **Landmark Detection:** Once the face is detected, facial landmarks are identified. These landmarks mark key facial features such as the eyes, eyebrows, and nose. Landmark detection is essential for understanding the relative positions of the eyes, which are crucial for gaze estimation. We train a **multi-branch regression model** to accurately estimate the landmarks.

+ **Head Pose Calculation:** The head pose calculation estimates the location and orientation of the head in 3D space (X, Y, Z, pitch, yaw, and roll). This information is critical, as it helps adjust gaze direction estimation based on the angle at which the person is facing the camera. We use the **PnP (Perspective-n-Point)** method to estimate head rotation and location from facial landmarks.

+ **Eye Crop Extraction:** After detecting facial landmarks, the next step involves extracting the regions of interest (ROIs) around the eyes. These regions are then cropped to focus specifically on the eye areas, ensuring that gaze tracking remains precise and unaffected by other facial features.

+ **Eye Status Classification:** In this module, the system determines the status of the eyes, such as whether they are open or closed, and whether they are free or occluded by sunglasses or a hand. This step is important for the application to understand whether the gaze direction can be reliably calculated. If the eyes are closed or obstructed, gaze estimation may not be feasible. We train CNN classifiers based on the **MobileNetV3** backbone to classify the different states of each eye.

+ **Gaze Direction Estimation:** Finally, the gaze direction is estimated based on the information gathered from the previous modules. This step involves analyzing the eye region along with the head pose to predict where the user is looking (e.g., gaze points on a screen or in 3D space). We train a **CNN-based regressor** to make this prediction, using the extracted eye crops, head pose, and reference frame from the calibration phase to accurately estimate the user's gaze direction.



