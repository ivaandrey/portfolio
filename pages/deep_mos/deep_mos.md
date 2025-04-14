## Mimimal Object Size Detection in Depth Images ##

Image quality analysis in depth cameras is essential for ensuring the accuracy, reliability, and overall performance of computer vision systems that depend on depth sensing. Typical image quality (IQ) metrics used to evaluate depth image quality include depth accuracy and precision, temporal noise (Z-noise), edge sharpness, among others.  
One important metric is the **Minimal Object Size (MOS)**, which refers to the smallest physical object that can be reliably detected, measured, or recognized by a depth sensor. This metric is especially critical in applications such as surveillance, robotics, quality inspection, and biometric systems, where fine detail detection is essential.

I led the development of the Minimal Object Size (MOS) metric for the Intel RealSense LiDAR L515 camera—a compact, solid-state depth camera based on LiDAR technology, designed for high-accuracy, low-power depth sensing in indoor environments. This metric enabled precise evaluation of the smallest detectable object size, enhancing depth image quality analysis and system performance.

---
<div style="text-align: center;">
  <img src="images/lidar_camera2.jpg?raw=true" width="20%" height="20%"/>
</div>

Before the development of the automatic MOS metric, a manual approach was applied. For this manual approach, a repetitive cylindrical target was used, where each cylinder's size and location were precisely defined. The manual approach, while offering control over the target, comes with several disadvantages.

Subjectivity is one of the key issues, as the approach relies on human visual acuity, meaning the results can be influenced by individual perceptions and inconsistencies. The repetitive location pattern of the cylinders helps the operator find the smallest cylinder more easily, but this predictability can reduce the ability to detect more subtle or unpredictable issues that may arise in real-world scenarios. The manual assessment is also heavily influenced by the observer’s point of view, as variations in angle, distance, or lighting conditions. Additionally, the grid pattern of the target may affect the results. Since the target is designed with a regular, predictable structure, it may not accurately reflect how a system would perform with irregular or complex real-world scenes.

These drawbacks emphasize the reason I chose to implement an automatic MOS metric, which provides more objective, consistent, and dependable results.

<div style="text-align: center;">
  <img src="images/CylinderTarget.png?raw=true" width="50%" height="50%"/>
</div>

A new target with an adjustable cylinder length and location was developed, eliminating the need for a repetitive grid and prior knowledge of its position. Additionally, an automatic data capturing tool was developed using a robot in the lab, which captures depth images from a constant distance of 1 meter but from various viewpoints.
