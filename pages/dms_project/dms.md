## Driver Activity Recognition for Driver Monitoring System (DMS) ##

A **Driver Monitoring System (DMS)** is an advanced safety technology designed to enhance road safety by continuously tracking and analyzing a driver’s behavior in real time. Utilizing sophisticated camera systems and AI-based algorithms, DMS can identify critical signs such as fatigue, distraction, drowsiness, and inattentiveness. These systems monitor a wide range of factors, including facial expressions, eye movements, head position, and even physiological signals, to assess whether the driver is alert and focused on the road.

I led the **end-to-end development** of a real-time **driver activity classifier**, designed to recognize key distraction states, including:

+ **✅ Normal state**: The driver is engaged and fully focused on driving.
+ **🍔 Eating/drinking**: The driver is consuming food or beverages while driving, which can be a significant distraction.
+ **📞 Talking on the phone**: This state is detected when the driver is holding a phone, which can impact attention and reaction time.
+ **🚬 Smoking**: The system detects when the driver is smoking, which may also distract from driving and requires significant attention.

+ The model was optimized for real-time performance, achieving an impressive execution speed of approximately **200 frames per second (FPS)**.
+ Additionally, the model demonstrates solid classification performance with an **[F1 score](https://www.v7labs.com/blog/f1-score-guide) of 0.781**, indicating a good balance between precision and recall.

This ensures the system can reliably detect and classify various driver activities, providing crucial information to improve overall driver safety.
The model was trained on **synthetic data generated using a GenAI** pipeline based on the Stable Diffusion XL (SDXL) base model, enhancing its robustness across edge cases.

---

<div style="text-align: center;">
  <img src="images/states.png?raw=true" width="80%" height="80%"/>
</div>

The **MobileNetV3 Small** pretrained model was chosen as the backbone for the driver activity recognition system primarily due to its exceptional running time performance and efficiency. **Originally trained on the ImageNet dataset with 1000 classes**, this model provides a robust feature extraction foundation while being lightweight and optimized for real-time applications. To adapt the model to our specific task, the original classifier head was replaced with a series of fully connected layers, where the output layer was **modified to have 4 nodes** corresponding to the states that need to be detected.

<div style="text-align: center;">
  <img src="images/dms_states_2.gif?raw=true"  width="50%" height="50%"/>
</div>


