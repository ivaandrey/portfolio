## Driver activity recognition for Driver Monitoring System (DMS) ##

A **Driver Monitoring System (DMS)** is an advanced safety technology designed to enhance road safety by continuously tracking and analyzing a driver’s behavior in real time. Utilizing sophisticated camera systems and AI-based algorithms, DMS can identify critical signs such as fatigue, distraction, drowsiness, and inattentiveness. These systems monitor a wide range of factors, including facial expressions, eye movements, head position, and even physiological signals, to assess whether the driver is alert and focused on the road.

Within the driver distraction analysis module, the customer specified a set of states that need to be detected, which include:

+ **Normal state**: The driver is engaged and fully focused on driving.
+ **Eating/drinking**: The driver is consuming food or beverages while driving, which can be a significant distraction.
+ **Talking on the phone**: This state is detected when the driver is holding a phone, which can impact attention and reaction time.
+ **Smoking**: The system detects when the driver is smoking, which may also distract from driving and requires significant attention.

I led the development and implementation of the driver activity recognition model (classifier) for this system. The model is optimized for real-time performance, achieving an impressive execution speed of approximately **200 frames per second (FPS)**. Additionally, the model demonstrates solid classification performance with an **F1 score of 0.781**, indicating a good balance between precision and recall. This ensures the system can reliably detect and classify various driver activities, providing crucial information to improve overall driver safety.

---


