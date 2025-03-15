## Eye State Analysis  ##

**Eye state** analysis is a fundamental component in various applications, including fatigue detection, medical diagnostics, human-computer interaction. By analyzing eye states, systems can assess alertness levels, detect signs of drowsiness or fatigue, and improve safety in critical environments.

In our project we categorized eye states into three classes: open, half-open, and closed. Each state provides valuable insights into a person's cognitive and physical condition:

+ **Open Eyes**: This state indicates attentiveness and wakefulness, commonly associated with an active and engaged individual. Monitoring open-eye duration can help evaluate focus and responsiveness, which is critical in applications like gaze tracking and virtual reality interactions.
+ **Half-Open Eyes**: This intermediate state often suggests fatigue, drowsiness, or a transition between wakefulness and sleep. Identifying half-open eyes is crucial for early detection of reduced alertness, helping prevent accidents in scenarios like driver monitoring and workplace safety systems.
+ **Closed Eyes**: A closed-eye state typically signifies sleep, blinking, or unconsciousness. Continuous detection of closed eyes is essential in medical applications , and real-time fatigue detection for vehicle operators.
  
Accurate classification of eye states enables proactive interventions, such as alerting drowsy drivers, enhancing security through eye-based authentication systems, and estimating gaze direction.

A key requirement for the network was achieving an optimized runtime to ensure real-time performance. The final classifier is highly efficient, running at **840 frames per second (FPS) on a CPU**. Despite its speed, the model maintains a high level of accuracy, achieving an impressive **[F1 score](https://www.v7labs.com/blog/f1-score-guide) of 0.905**. This exceptional performance enables rapid and reliable eye state processing, making it ideal for applications that demand low-latency responses, including driver monitoring systems, biometric authentication, and gaze tracking.

---

<div style="text-align: center;">
  <img src="images/eye_states_united.png?raw=true">
</div>

High performance was achieved due to a lightweight CNN architecture. Additionally, an eye crop normalization phase was incorporated as a preprocessing step to enhance accuracy. Exceptional precision was attained in both RGB and IR images, regardless of whether glasses were worn.

An additional challenge was fine-tuning the classifier to account for variations in eye features across different ethnicities, particularly for individuals of Asian nationality. The fine-tuned model achieves an **F1 score of 0.881** while maintaining the same runtime performance for Asian eyes.


