## Artificial Trainer - mentored B.Sc. students' final project ##

Throughout my engineering career, I’ve always aimed to help others in STEM fields by explaining concepts and sharing my knowledge. I had the opportunity to support a pair of students in their final B.Sc. project at Braude College of Engineering (Karmiel). The project intrigued me as it combined algorithmic thinking with computer vision using a deep learning approach—two areas I’m deeply passionate about. **The project received a final mark of 96.**

The main goal of the project was to create an **Artificial Trainer** that acts as a supervisor for individuals training without a personal trainer in the gym. The artificial trainer detects the trainee and **assesses the performance of the squat exercise in real time from an RGB image**. The correctness of the exercise is assessed using **MediaPipe and CNN deep learning models**. It compares the trainee’s movements to a defined range of correct form and provides a performance rating. Additionally, the artificial trainer sends alerts when the exercise is performed incorrectly, helping the trainee avoid injuries and enhance their performance.

---

<div style="text-align: center;">
  <img src="images/squat1.png?raw=true" width="20%" height="20%"/>
</div>

The developed application is designed to count the number of repetitions, assess the performance of each repetition, provide real-time warnings about the correctness of the exercise, and estimate the final score for the performance of a set of squats. To accurately estimate the exercise and assess the user’s performance, it is essential to define the requirements for the squat exercise, including specifying the correct movement patterns, as well as the range and limits for each movement.

The solution is based on pose detection analysis combined with a deep learning approach. Most of the algorithmic modules in the project are based on calculating the angles between relevant joints. These joints are extracted using the MediaPipe network. To evaluate the correctness of a squat exercise, we defined five criteria that must be met to consider a single repetition as properly performed. In addition, a squat repetition detection module was developed based on the angle span of the knees.

<div style="text-align: center;">
  <img src="images/flowchart.png?raw=true" width="80%" height="80%"/>
</div>

+ **One repetition Definition**: A single repetition of the squat exercise begins from a standing position. From there, the trainee bends down following well-defined rules, ensuring that the squat is “deep” enough. After reaching the lowest point, the trainee returns to the original standing position, ready to perform the next repetition. **The repetition is detected using angle analysis of the knee joints.**
+ **Back Straightness Criteria**: The trainee should maintain a straight back throughout the movement, both when lowering and returning to the standing position. Rounding the back under load can lead to spinal injuries, particularly in the upper or lower back. **This criterion is evaluated by a trained deep learning classifier.**
+ **Knee Alignment**: The trainee should ensure that their knees stay aligned with or behind their toes throughout the squat. Allowing the knees to extend past the toes can cause undue stress on the knee joints and increase the risk of injury. **This criterion is checked by analyzing the coordinates of the knee and toe joints.**
+ **Heel Positioning**: The trainee should keep their heels firmly planted on the ground throughout the squat, ensuring that the knees remain aligned with the feet and are not splayed in or out. Lifting the heels can destabilize the movement and lead to improper form, increasing the risk of injury. **This criterion is checked by analyzing the location of the heel joints during each repetition.**
+ **Head Positioning**: The trainee should maintain a neutral head position by looking straight ahead during the squat. Looking down can affect balance and posture, potentially leading to improper form. **This criterion is checked by analyzing the angle between the neck and back to ensure proper alignment.**
+ **Depth of Squat**: The trainee should lower themselves sufficiently to ensure the squat is deep enough for maximum effectiveness. **This criterion is implemented by analyzing the angle of the knee** during the downward phase of the squat. If the knee angle does not meet the required threshold, it indicates that the squat is not deep enough.

<div style="text-align: center;">
  <img src="images/criterions.png?raw=true" width="50%" height="50%"/>
</div>

One of the challenging aspects of this project was developing the classifier to assess the straightness of the back. **We decided to train a deep learning model that is fed with crops of the back region from the RGB images and outputs two possible classes: straight back and curved back.** A key requirement for the developed CNN architecture was real-time runtime performance. Most well-known pretrained classification networks suffer from poor runtime performance, so we chose to implement our own classification network with a limited number of hidden layers. Additionally, the platform running the algorithm was a laptop without a GPU, making the runtime requirement critical for the success of the application.

The students were instructed on how to collect the relevant data of straight and curved backs and what network architecture would be most suitable for the task. After analyzing the requirements, we decided to implement an efficient classic CNN architecture using binary cross-entropy loss. This approach was chosen to ensure a balance between performance and computational efficiency. The final trained model achieved an **accuracy of 87.98%** on the test set and a **runtime of 44 frames per second (fps)**.

<div style="text-align: center;">
  <img src="images/cnn.png?raw=true" width="80%" height="80%"/>
</div>
