## 3D Object Edge Analysis ##

**Edge analysis** is an important image quality metric in depth imaging, used to evaluate the sharpness and clarity of object boundaries captured by a depth camera. This metric assesses how accurately and consistently the system captures depth discontinuities, such as the transition between foreground objects and the background.  
Key aspects of edge analysis in depth images:
+ **Sharpness**: Measures the steepness or gradient at depth boundaries, indicating how well the sensor can preserve the true geometry of edges.
+ **Bumpiness**: Quantifies local irregularities or high-frequency noise along edges — areas where depth values change sharply.
+ **Distortion**: Refers to systematic deviations in the shape or geometry of a depth edge from its expected form. It typically arises when an edge that should be straight, sharp, or well-aligned appears warped, curved, displaced, or smeared.

In addition to standard edge metrics, I developed two novel metrics to enhance edge quality assessment: the **Side Plane Angle Metric** and the **Corner Angle Metric**.
+ **Side Plane Angle**: Calculates the normals of different regions along a side plane and analyzes the angular deviations to assess surface consistency and flatness.
+ **Corner Angle**: Measures the angle between adjacent planar surfaces at object corners along an edge, evaluating the sharpness and geometric accuracy of depth discontinuities in corner regions.

---

<div style="text-align: center;">
  <img src="images/EdgeMetrics2.png?raw=true">
</div>

Two depth cameras based on different technologies were selected for analysis: the **RealSense LiDAR L515** and the **RealSense D435**.

The **L515** utilizes LiDAR (Light Detection and Ranging) technology, employing a laser scanning mechanism to capture high-resolution depth information. It provides exceptional depth accuracy and low noise, especially in indoor environments, and is well-suited for applications requiring fine-grained depth details such as object measurement or high-precision scanning.

In contrast, the **D435** is based on stereo vision technology, using a pair of RGB sensors and an infrared projector to compute depth via disparity between images. While more versatile across various lighting conditions and typically offering a wider field of view, it is generally less accurate and noisier compared to LiDAR in terms of depth precision, particularly at longer ranges or on low-texture surfaces.

<div style="text-align: center;">
  <img src="images/two_cameras.png?raw=true">
</div>

