## Artificial Trainer - AI Real-Time Squat Coach ##

Throughout my engineering career, **I’ve aimed to support others in STEM by sharing knowledge and mentorship**. I had the privilege of guiding two outstanding B.Sc. students in their final-year project at Braude College of Engineering (Karmiel). This project merged algorithmic thinking and computer vision with deep learning—fields.

**🏆 The project received a final mark of 96.**

The main goal of the project was to create an **Artificial Trainer**—a virtual supervisor for individuals training at the gym without a coach. Leveraging **MediaPipe** and CNN models, the app detects squat exercises in **real time from RGB images**, evaluates form correctness against predefined criteria, and delivers instant feedback to help prevent injury and enhance performance.

---

<div style="text-align: center;">
  <img src="images/squat1.png?raw=true" width="20%" height="20%"/>
</div>

To accurately evaluate the exercise and assess the user’s performance, it is essential to define specific requirements for the squat exercise — including correct movement patterns, acceptable ranges, and movement limits.

### 🔧 Key Capabilities: ###
+  **Repetition Counting** – Detects and tracks each squat repetition automatically.  
+  **Real-Time Feedback** – Highlights form errors and provides corrective guidance on-the-fly.  
+  **Performance Scoring** – Calculates a score for each repetition and the entire set.


The solution combines pose detection analysis with a deep learning approach. Most of the algorithmic modules are based on calculating angles between key joints, which are extracted using the MediaPipe network. To determine whether a squat repetition is correctly performed, we defined five key criteria. Additionally, a dedicated repetition detection module was developed, which relies on analyzing the knee angle span.

<div style="text-align: center;">
  <img src="images/flowchart.png?raw=true" width="80%" height="80%"/>
</div>

### ✅ Evaluation Criteria: ###
+ **Repetition Definition**: A valid squat begins and ends in a standing position, with a deep bend detected via knee angle dynamics.
+ **Back Straightness Criteria**: A CNN-based classifier evaluates whether the back remains straight throughout the motion.
+ **Knee Alignment**: Ensures knees stay aligned with or behind the toes, assessed via 2D joint coordinates.
+ **Heel Positioning**: Detects if heels lift off the ground, maintaining stability and form.
+ **Head Positioning**: Evaluates head posture via neck-to-back angle to ensure proper alignment.
+ **Depth of Squat**: Assessed by knee angle; insufficient depth indicates poor form.

<div style="text-align: center;">
  <img src="images/criterions.png?raw=true" width="50%" height="50%"/>
</div>

One challenging part was designing a lightweight CNN for back posture classification—a necessity since the system had to run on a CPU-only laptop in real time. After testing, the final model achieved **87.98% accuracy** on the test set while maintaining **44 FPS** runtime.

###  🧩 Back Straightness Classifier: ###

One challenging part was designing a lightweight CNN for back posture classification—a necessity since the system had to run on a CPU-only laptop in real time. Most well-known pretrained classification networks suffer from poor runtime performance, so after analyzing the project requirements, **we decided to implement, train and deploy an efficient, classic CNN architecture using binary cross-entropy loss.** Additionaly, the students were guided on how to collect relevant data for both straight and curved backs.  
+ The final trained model achieves:
  + 📊 **87.98% accuracy** on the test set.
  + 🚀 **Real-time performance at 44 FPS** on CPU.

<div style="text-align: center;">
  <img src="images/cnn.png?raw=true" width="80%" height="80%"/>
</div>

### ⚡ Real-Time Application: ###

The developed application operates in **real time on CPU**, analyzing the correctness of each squat repetition, **providing instant feedback to the trainee** on necessary improvements, **counting repetitions**, and summarizing the overall execution quality at the end of the set. Additionally, it **returns an overall performance grade**, saves the results, and enables the trainee to track their progress over time.

You can view the full application demo [here](https://www.youtube.com/watch?v=TKfvSuj2hhs).

<div style="text-align: center;">
  <img src="images/demo.gif?raw=true" width="80%" height="80%"/>
</div>
