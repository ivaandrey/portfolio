## Artificial Trainer - mentored B.Sc. students' final project ##

Throughout my engineering career, I’ve always aimed to help others in STEM fields by explaining concepts and sharing my knowledge. I had the pleasure of mentoring two excellent students in their final B.Sc. project at Braude College of Engineering (Karmiel). The project intrigued me as it combined algorithmic thinking with computer vision using a deep learning approach—two areas I’m deeply passionate about. **The project received a final mark of 96.**

The main goal of the project was to develop an application called an **Artificial Trainer**, which acts as a virtual supervisor for individuals training without a personal trainer in the gym. The artificial trainer detects the trainee and **assesses the performance of the squat exercise in real time from an RGB image**. The correctness of the exercise is assessed using **MediaPipe and CNN deep learning models**. It compares the trainee’s movements to a defined range of correct form and provides a performance rating. Additionally, the Artificial Trainer provides real-time alerts when an exercise is performed incorrectly, helping the trainee prevent injuries and improve overall performance.

---

<div style="text-align: center;">
  <img src="images/squat1.png?raw=true" width="20%" height="20%"/>
</div>

The developed application is designed to count squat repetitions, assess the performance of each repetition, provide real-time feedback on exercise correctness, and estimate a final score for an entire set. To accurately evaluate the exercise and assess the user’s performance, it is essential to define specific requirements for the squat exercise — including correct movement patterns, acceptable ranges, and movement limits.

The solution combines pose detection analysis with a deep learning approach. Most of the algorithmic modules are based on calculating angles between key joints, which are extracted using the MediaPipe network. To determine whether a squat repetition is correctly performed, we defined five key criteria. Additionally, a dedicated repetition detection module was developed, which relies on analyzing the knee angle span.

<div style="text-align: center;">
  <img src="images/flowchart.png?raw=true" width="80%" height="80%"/>
</div>

+ **One Repetition Definition**: A single repetition of the squat exercise begins from a standing position. From there, the trainee bends down following well-defined rules, ensuring that the squat is “deep” enough. After reaching the lowest point, the trainee returns to the original standing position, ready to perform the next repetition. **The repetition is detected using angle analysis of the knee joints.**
+ **Back Straightness Criteria**: The trainee should maintain a straight back throughout the movement, both when lowering and returning to the standing position. Rounding the back under load can lead to spinal injuries, particularly in the upper or lower back. **This criterion is evaluated by a trained deep learning classifier.**
+ **Knee Alignment**: The trainee should ensure that their knees stay aligned with or behind their toes throughout the squat. Allowing the knees to extend past the toes can cause undue stress on the knee joints and increase the risk of injury. **This criterion is checked by analyzing the coordinates of the knee and toe joints.**
+ **Heel Positioning**: The trainee should keep their heels firmly planted on the ground throughout the squat, ensuring that the knees remain aligned with the feet and are not splayed in or out. Lifting the heels can destabilize the movement and lead to improper form, increasing the risk of injury. **This criterion is checked by analyzing the location of the heel joints during each repetition.**
+ **Head Positioning**: The trainee should maintain a neutral head position by looking straight ahead during the squat. Looking down can affect balance and posture, potentially leading to improper form. **This criterion is checked by analyzing the angle between the neck and back to ensure proper alignment.**
+ **Depth of Squat**: The trainee should lower themselves sufficiently to ensure the squat is deep enough for maximum effectiveness. **This criterion is implemented by analyzing the angle of the knee** during the downward phase of the squat. If the knee angle does not meet the required threshold, it indicates that the squat is not deep enough.

<div style="text-align: center;">
  <img src="images/criterions.png?raw=true" width="50%" height="50%"/>
</div>

One of the challenging aspects of this project was developing the classifier to assess the straightness of the back. **We decided to train a deep learning model that is fed with crops of the back region from the RGB images and outputs two possible classes: straight back and curved back.** A key requirement for the developed CNN architecture was real-time runtime performance. Most well-known pretrained classification networks suffer from poor runtime performance, so we chose to implement our own classification network with a limited number of hidden layers. Additionally, the platform running the algorithm was a laptop without a GPU, making the runtime requirement critical for the success of the application.

The students were guided on how to collect relevant data for both straight and curved backs, as well as on selecting an appropriate network architecture for the task. After analyzing the project requirements, we decided to implement an efficient, classic CNN architecture using binary cross-entropy loss. This approach was chosen to balance classification performance with computational efficiency. The final trained model achieved an **accuracy of 87.98%** on the test set and delivered real-time performance with a **runtime of 44 frames per second (fps)**.

<div style="text-align: center;">
  <img src="images/cnn.png?raw=true" width="80%" height="80%"/>
</div>

The developed application operates in real time on CPU, analyzing the correctness of each squat repetition, providing instant feedback to the trainee on necessary improvements, counting repetitions, and summarizing the overall execution quality at the end of the set. Additionally, it returns an overall performance grade, saves the results, and enables the trainee to track their progress over time.

You can view the full application demo [here](https://www.youtube.com/watch?v=TKfvSuj2hhs).

<div style="text-align: center;">
  <img src="images/demo.gif?raw=true" width="80%" height="80%"/>
</div>
