## Mimimal Object Size Detection in Depth Images ##

**Image quality analysis in depth cameras** is essential for ensuring the accuracy, reliability, and overall performance of computer vision systems that depend on depth sensing. Typical image quality (IQ) metrics used to evaluate depth image quality include depth accuracy and precision, fill rate, temporal noise (Z-noise), ***[edge sharpness](../3d_object_analysis_project/3d_object_analysis.md)***, and others.  
One important metric is the **Minimal Object Size (MOS)**, which refers to the smallest physical object that can be reliably detected, measured, or recognized by a depth sensor. This metric is especially critical in applications such as surveillance, robotics, quality inspection, and biometric systems, where fine detail detection is essential.

I led the development of the Minimal Object Size (MOS) metric for the **Intel RealSense LiDAR L515** camera—a compact, solid-state depth camera based on LiDAR technology, designed for high-accuracy, low-power depth sensing in indoor environments. This metric enabled precise evaluation of the smallest detectable object size, enhancing depth image quality analysis and system performance.

The final results for the cylinder with a **13mm length and diameter** are as follows: 
+ 📊 **Class accuracy of 94%**
+ 🎯 Object **position accuracy of 95%** (within a 5-pixel margin)
+ 📏 Cylinder **size accuracy of around 99%**

---
<div style="text-align: center;">
  <img src="images/lidar_camera2.jpg?raw=true" width="20%" height="20%"/>
</div>

Before developing the automatic MOS metric, detection was done manually using a fixed grid of cylinders with known sizes and positions. While this offered precise control, it introduced several drawbacks:

+ 🔍 **Subjectivity** – Results depended on the operator’s visual perception and consistency.
+ 🎯 **Predictability** – The fixed pattern made detection easier but less reflective of real-world variability.
+ 🧭 **Viewpoint Sensitivity** – Manual results varied based on angle, lighting, and observer perspective.

These limitations highlighted the need for an automated, objective approach better suited for real-world scenarios.

<div style="text-align: center;">
  <img src="images/CylinderTarget.png?raw=true" width="50%" height="50%"/>
</div>

### 🤖 Automated Data Capture System ###
A new target with an adjustable cylinder length and location was developed, eliminating the need for a repetitive grid and prior knowledge of its position. Additionally, an **automatic data capturing tool was developed using a robot in the lab**, which captures depth images from a constant distance of 1 meter but from various viewpoints.

<div style="text-align: center;">
  <img src="images/CylinderTarget2.png?raw=true" width="50%" height="50%"/>
</div>

### 🧠 Model & Inference ###
The YOLOv3 network was selected as the cylinder detection model for depth images due to its several advantages, including high accuracy, fast inference speed, and ability to detect objects in real-time. Additionally, YOLOv3 performs well with small and large objects, offers robust performance even with limited training data, and provides a balance between precision and recall, making it suitable for cylinder detection tasks.

<div style="text-align: center;">
  <img src="images/data_capturing.gif?raw=true" width="30%" height="30%"/>
</div>
