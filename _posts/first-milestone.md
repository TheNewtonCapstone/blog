```
A journey of a thousand miles begins with a single step
```

Last Thursday, we took a big step. It was the first tryout of our project. We were filled with emotions, anticipation, and a little bit of dread, all mixed up together. We expected failure, and we weren't disappointed.

### Hardware: A Tough Fit

We had a CAD design, and the *peeps* recommended laser cutting, but we couldn't get that done. Houssam was ready to throw money at the problem, but we went with 3D printing instead. Ryan sliced the part for printing. It didn't fit, just as we expected. Camille and his friend Alex banged the parts together, hoping they’d stay put.


### Firmware: The Struggle
![image](https://github.com/user-attachments/assets/fb555886-e2ff-465c-b662-a1af762f2362)

[insert boring explanation of what the firmware is supposed to do]
The goal was to get our setup running the model. 
I spent days trying to establish a serial connection between a micro-ROS agent and the rest of the system. 
A waste of time, honestly.(a post coming about that )

Then came the next step: installing the ONNX runtime environment. ONNX is what you need to run the models. 
The jetson had some issues building the environment—of course, it did. 
We never figured out exactly what was wrong, but [Dusty-nv](https://github.com/dusty-nv/jetson-containers)  got us through it.

Once we got the environment up, we were ready to run any ONNX model we wanted. The final hurdle was getting the communication right. Just a heads-up: if you ever work with micro-ROS, think hard about memory management. It’s a pain you don’t want.
