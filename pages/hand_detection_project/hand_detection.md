## Hand Detection and Hand Landmark Estimation  ##

**Hand Detection** involves identifying and localizing hands in images or video streams. **Hand Landmark Estimation** focuses on identifying key points on the hand, such as fingertips, knuckles, and the wrist, enabling detailed tracking of hand movements. Both of these modules are essential for applications such as gesture recognition, sign language interpretation, virtual and augmented reality (VR/AR), and human-computer interaction (HCI).

One of the drawbacks of widely used MediaPipe models is their reduced accuracy when applied to IR and grayscale images. MediaPipe's Hand Landmark Detection is primarily trained on RGB images, assuming good lighting and clear hand visibility. However, many applications, such as driver monitoring systems (DMS) that use IR cameras and medical applications that operate under poor lighting conditions, require reliable hand landmark detection in grayscale or IR images. Given these challenges, our company decided to develop a specialized hand landmark detector for grayscale and IR images.

---

Insert comparison results between mediapipe and our models on gray images


