---
title: "First Milestone!"
date: 2024-08-11
categories: [META]
tags: [team, meta, timeline, goals] 
author: [amp, sis, gc, her]
---

> A journey of a thousand miles begins with a single step

Last Thursday, we took a big step. It was the first tryout of our project. We were filled with emotions, anticipation, and a little bit of dread, all mixed up together. We expected failure, and we weren't disappointed!

### Hardware: A Tough Fit

We had a CAD design, and the original team's *peeps* recommended laser cutting, but we couldn't get that done. Houssam was ready to throw money at the problem, but we went with 3D printing instead. Rayan sliced the part for printing. It didn't fit, just as we expected. Camille and his friend Alex banged the parts together, hoping they’d stay put. They didn’t.

<iframe width="315" height="560" src="https://www.youtube.com/embed/fJqC3l1YIR4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Firmware: The Struggle
![image](https://github.com/user-attachments/assets/fb555886-e2ff-465c-b662-a1af762f2362)

The firmware's goal is to establish communications between the hardware and the software (i.e. the model running on the Jetson). 
Shami spent days trying to establish a serial connection between a micro-ROS agent and the rest of the system. Which was a waste of time, honestly (we'll have a post coming about that).

Then came the next step: installing the ONNX runtime environment. ONNX is what you need to run the models. 
The Jetson had some issues building the environment—of course it did. 
We never figured out exactly what was wrong, but [Dusty-nv](https://github.com/dusty-nv/jetson-containers)  got us through it.

Once we got the environment up, we were ready to run any ONNX model we wanted. The final hurdle was getting the communication right. Just a heads-up: if you ever work with micro-ROS, think hard about memory management. It’s a pain you simply don’t want.

### Software: The Ideal Environment
This is where the sky is blue and the sun is shining... for now. Since we had a working model which could balance itself in a flat simulated environment, we decided our next move would be to try to mimic real-life in Isaac Sim as closely as possible. Houssam took care of domain randomization while Augusto used perlin noise (among other techniques) for procedural terrain generation. 

### Electrical: Simple Solutions to Simple Problems
The entire electrical system was built on an an approach of simplicity and efficiency of design. We used only elements we already had, from the motors to the voltage converters to the batteries. 

For power, we used 3 11.1V drone LiPo batteries, which gave us a total voltage of 37.8V. While we could have used a single 6s at full charge, we needed the system to be as stable as possible for the Jetson, therefore we gave it a stepped down 24V.

For the voltage converters, we used two step down converters with adjustable voltage output.

Finally, the motors were two `CM36-3650` Reduction Geared Motor, which have an encoder output, and speed control and direction control inputs. This allowed us to control the motor with no external board or equipment. However, the datasheet and information on this motor was extremely rare and unprecise, which led to a lot of troubleshooting, as we did not have, for example, the number of pulses per rotation of the encoder.

### Conclusion

This is a small step in the greater adventure beyond: stay tuned for more updates and more in-depth posts :)
