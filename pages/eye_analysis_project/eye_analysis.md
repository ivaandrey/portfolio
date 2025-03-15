## Eye State Analysis  ##

**Eye state** analysis is a fundamental component in various applications, including fatigue detection, medical diagnostics, human-computer interaction. By analyzing eye states, systems can assess alertness levels, detect signs of drowsiness or fatigue, and improve safety in critical environments.

In our project we categorized eye states into three classes: open, half-open, and closed. Each state provides valuable insights into a person's cognitive and physical condition:

+ **Open Eyes**: This state indicates attentiveness and wakefulness, commonly associated with an active and engaged individual. Monitoring open-eye duration can help evaluate focus and responsiveness, which is critical in applications like gaze tracking and virtual reality interactions.
+ **Half-Open Eyes**: This intermediate state often suggests fatigue, drowsiness, or a transition between wakefulness and sleep. Identifying half-open eyes is crucial for early detection of reduced alertness, helping prevent accidents in scenarios like driver monitoring and workplace safety systems.
+ **Closed Eyes**: A closed-eye state typically signifies sleep, blinking, or unconsciousness. Continuous detection of closed eyes is essential in medical applications , and real-time fatigue detection for vehicle operators.
  
Accurate classification of eye states enables proactive interventions, such as alerting drowsy drivers, enhancing security through eye-based authentication systems, and gaze direction estimation.

The primary requirement for the network was achieving an optimized runtime to ensure real-time performance. The final classifier is highly efficient, running at **900 frames per second (FPS)** on a CPU. This level of performance enables rapid processing of eye state data, making it suitable for applications requiring low-latency responses, such as driver monitoring systems, biometric authentication, and gaze estimation.

