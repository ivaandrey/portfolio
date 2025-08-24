## 3D Object Edge Analysis ##

**Edge analysis** is an important image quality metric in depth imaging, used to evaluate the **sharpness**, **clarity** and **geometric accuracy** of object boundaries captured by a depth camera. This metric assesses how accurately and consistently the system captures depth discontinuities, such as the transition between foreground objects and the background.  

### 📏 Key Metrics for Edge Analysis: ###
+ **Sharpness**: Measures the steepness or gradient at depth boundaries, indicating how well the sensor can preserve the true geometry of edges.
+ **Bumpiness**: Quantifies local irregularities or high-frequency noise along edges — areas where depth values change sharply.
+ **Distortion**: Refers to systematic deviations in the shape or geometry of a depth edge from its expected form. It typically arises when an edge that should be straight, sharp, or well-aligned appears warped, curved, displaced, or smeared.

In addition to standard edge metrics, I developed two novel metrics to enhance edge quality assessment.  
### ✨ Novel Metrics Developed: ###
+ **Side Plane Angle Metric**: Calculates the normals of different regions along a side plane and analyzes the angular deviations to assess surface consistency and flatness.
+ **Corner Angle Metric**: Measures the angle between adjacent planar surfaces at object corners along an edge, evaluating the sharpness and geometric accuracy of depth discontinuities in corner regions.

---

<div style="text-align: center;">
  <img src="images/EdgeMetrics2.png?raw=true">
</div>

Two depth cameras based on different technologies were selected for analysis: the **RealSense LiDAR L515** and the **RealSense D435**.

The **L515** utilizes LiDAR (Light Detection and Ranging) technology, employing a laser scanning mechanism to capture high-resolution depth information. It provides exceptional depth accuracy and low noise, especially in indoor environments, and is well-suited for applications requiring fine-grained depth details such as object measurement or high-precision scanning.

In contrast, the **D435** is based on stereo vision technology, using a pair of RGB sensors and an infrared projector to compute depth via disparity between images. While more versatile across various lighting conditions and typically offering a wider field of view, it is generally less accurate and noisier compared to LiDAR in terms of depth precision, particularly at longer ranges or on low-texture surfaces.

<div style="text-align: center;">
  <img src="images/two_cameras.png?raw=true" width="50%" height="50%"/>
</div>

To analyze the angles of the plane and the corner, the 3D coordinates of each pixel were calculated, and a 3D model of the object was reconstructed.   
The side plane was divided into 25 regions, and a plane-fitting algorithm was applied to each region to calculate the normal vector for each.

<div style="text-align: center;">
  <img src="images/lidar_edge.png?raw=true" width="80%" height="80%"/>
</div>


### 📊 Results ###
+ **Side Plane Angle:**
  + 🎯 D435: Average angle = 89.8°, Std Dev = 4.8°
  + 🔦 L515: Average angle = 93.4°, Std Dev = 16.2°

<div style="text-align: center;">
  <img src="images/two_cameras_edge_results.png?raw=true" width="80%" height="80%"/>
</div>


+ **Corner Angle:**
  + 🎯 D435: Average angle = 93.2°
  + 🔦 L515: Average angle = 79.8°

<div style="text-align: center;">
  <img src="images/corner_vectors.png?raw=true" width="80%" height="80%"/>
</div>

### 📝 Summary ###
The **stereo-based D435** consistently delivered more **accurate and stable edge metrics** compared to the **LiDAR-based L515**, making it more suitable for applications demanding geometric precision in 3D environments.


<div style="text-align: center;">
  <img src="images/3d_edge_metrics_results_table.png?raw=true" width="80%" height="80%"/>
</div>
