## Eye State Analysis  ##

**Eye state** analysis is a fundamental component in various applications, including **fatigue detection**, **medical diagnostics**, **human-computer interaction**. By analyzing eye states, systems can assess user alertness, detect early signs of drowsiness, and enhance safety in high-stakes environments like **driver monitoring systems (DMS)**.

In this project I categorized eye states into three classes: open, half-open, and closed. Each state provides valuable insights into a person's cognitive and physical condition:

+ ** 👀 Open Eyes**: Indicate attentiveness and engagement. Tracking open-eye duration is crucial in gaze-based interaction and VR/AR applications.  
+ ** 😴 Half-Open Eyes**: Often signal fatigue or transition to sleep. Early detection enables timely alerts in DMS and industrial safety settings.  
+ ** 🙈 Closed Eyes**: Reflect blinking, sleep, or unconsciousness. Continuous detection supports real-time fatigue alerts and medical use cases.

To meet real-time constraints, I led the development of a lightweight CNN-based classifier capable of running at **840 FPS on CPU**, while achieving a high **[F1 score](https://www.v7labs.com/blog/f1-score-guide) of 0.905**. This balance between speed and accuracy makes it ideal for low-latency deployments in safety-critical and interactive systems.
  
---

<div style="text-align: center;">
  <img src="images/eye_states_united.png?raw=true">
</div>

High performance was achieved due to a lightweight CNN architecture. Additionally, an eye crop normalization phase was incorporated as a preprocessing step to enhance accuracy. Exceptional precision was attained in both RGB and IR images, regardless of whether glasses were worn.

We also addressed **ethnic diversity** challenges in eye shape and appearance. By fine-tuning on dedicated datasets, the model achieved **0.881 F1 score** for **Asian eye types**, maintaining real-time performance.

<div style="text-align: center;">
  <img src="images/eye_state_video.gif?raw=true" width="80%" height="80%"/>
</div>


