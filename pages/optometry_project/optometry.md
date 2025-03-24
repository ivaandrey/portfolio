## Glasses Lens Measurement for Optometric Applications ##

Accurate **glasses lens measurement** is a critical aspect of optometry, ensuring that prescription eyewear provides optimal vision correction, comfort, and long-term wearability. Whether for single-vision, bifocal, progressive, or specialized lenses, precise measurements are essential for aligning the optical center of the lenses with the wearer's eyes. Even minor misalignments can lead to visual discomfort, headaches, and reduced effectiveness of the prescription.

**Key Frame Measurements for Optimal Fit:**
+ **Pupillary Distance (PD)**: Ensures the optical centers of the lenses align perfectly with the wearer’s pupils for maximum clarity and reduced eye strain.
+ **Lens Width and Height**: Determines the size of the lens to provide proper coverage and a balanced visual experience.
+ **Fitting Height (FH)**: The vertical positioning of the lenses, ensuring that the wearer looks through the optical center for proper vision correction, especially important for progressive and bifocal lenses.

---

<div style="text-align: center;">
  <img src="images/LensMeasurements2.png?raw=true" width="50%" height="50%"/>
</div>

Despite advancements in optometric technology, **most optometrists today still perform these measurements manually using a ruler or pupillometer**. While this method has been widely used for decades and provides reasonable accuracy, it is prone to human error, leading to slight misalignments in lens placement.

To address these limitations, **I led a project focused on developing precise lens measurements from RGB images using classical and deep learning (DL) computer vision methods**. These advanced techniques allow for accurate, automated measurements that reduce human error and improve efficiency. By leveraging machine learning algorithms and image processing techniques, digital solutions can now extract key parameters such as **PD and MonoPD, Lens Height and Width, and Fitting Height (FH)** dimensions with superior precision compared to traditional manual methods.

<div style="text-align: center;">
  <img src="images/demo_image.png?raw=true" width="50%" height="50%"/>
</div>


Here’s a detailed breakdown of each step in the lens size calculation process:

1. **Face Detection** - Detect the face in the input image using a deep learning-based face detector. A custom-trained YOLOv5 network is utilized for this task. 

2. **Face Landmark Detection** - Identify key facial landmarks (e.g., eyes, nose, mouth, and face contour) using a landmark detection model. Extract precise positions of the eyes and nose bridge, which are crucial for subsequent steps.

3. **Glasses Region Extraction** - Using eyes and nose landmarks define the crop of the glasses.

Segment the glasses frame from the face using edge detection, color segmentation, or a trained segmentation model.

Glasses Symmetry Line Calculation

Identify the midpoint of the glasses frame to determine the symmetry axis.

This step helps in aligning the frame and ensuring accurate size estimation.

Pupil Center Calculation

Detect the pupils using a combination of intensity-based methods, Hough Transform, or deep learning-based eye tracking models.

Accurately localizing the pupils is essential for measuring interpupillary distance (IPD) and fitting height.

Monocular Pupillary Distance (MonoPD) Calculation

Compute the distance from each pupil center to the symmetry line of the glasses.

This measurement is used for personalized lens fitting and prescription accuracy.

Glasses Lens Segmentation

Segment the lens region within the glasses frame using classical image processing techniques (e.g., thresholding, contour detection) or deep learning-based segmentation (e.g., U-Net, DeepLabV3).

Extract lens boundaries for precise size estimation.

Lens Size and Fitting Height Calculation

Measure the lens dimensions (width and height) in pixels and convert them to real-world units using a known reference (e.g., standard IPD or frame dimensions).

Calculate the fitting height, which is the vertical distance from the pupil center to the bottom of the lens.

Ensure measurements align with optical standards for accurate prescription fitting.
