---
title: "Mapping the Future"
date: 2024-11-11
categories: [P&P]
tags: [vslam, ros, nvblox, computer vision]     # TAG names should always be lowercase
author: [ra, mb]
---

# Mapping the Future

## Introduction
Newton’s journey to becoming the bestest of boys passes through vision. In this post, we focus on Newton’s sight– a key enabler for autonomous navigation. There are many implementations that have been tried and tested, some more difficult than others, but ultimately achieve the same functionality: SLAM, which stands for Simultaneous Localization and Mapping. It is a process in which a robot builds a map of an unknown environment while simultaneously determining its own position within that map. 

There are different types of SLAM currently used on the market; they mainly differ in the sensors used for input. There are LiDAR based libraries, and camera based libraries. For Newton, a camera based approach made more sense as it could be further utilized for computer vision and customizing missions. There are a few different options when it comes to camera based SLAM, mainly NVIDIA isaac ROS VSLAM and ORBSLAM3. We decided to go with the more established and documented NVIDIA library as it is built upon ROS Humble and is a more mainstream library to use for this use-case.

## Setup Summary
In this section, we are going to go through the setup of NVIDIA isaac ROS VSLAM and some hurdles faced along the way. We tested running the Isaac ROS Visual SLAM and Nvblox libraries using the Intel Realsense D435 camera on a desktop running Ubuntu 22.04, and with the exception of some minor hurdles, the process was straightforward. Here is a list of the steps taken:
1. [Setup Isaac ROS developer environment](https://nvidia-isaac-ros.github.io/getting_started/dev_env_setup.html)
When setting up the Isaac ROS developer environment, we encountered an issue with setting up the Docker containers where the user account we were on was not granted administrator privileges. This issue is due to using the script “run_dev.sh” which sets up a development environment containing ROS2. Essentially the script will try to install files on your computer so it requires admin privileges which is not outlined in the steps.
2. [Setup Isaac ROS Realsense](https://nvidia-isaac-ros.github.io/getting_started/hardware_setup/sensors/realsense_setup.html)
During the Isaac ROS Visual SLAM setup, when testing with a monocular camera (a regular Logitech C920) we encountered a bug where the calibration file saved after calibration was not found. We found out that the file was routed to the parent directory, which we resolved by pointing the program to the correct path. Also, there are errors when installing the setup libraries needed for running the camera where some are not installed. These errors do not impact the activity of the camera which took a while for us to realize and is not mentioned in the documentation either.
3. [Setup Isaac ROS Visual SLAM](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_visual_slam/isaac_ros_visual_slam/index.html#quickstart)
The VSLAM library requires use of an IMU by default. Since we ordered the Realsense D435 (not the D435i which comes with an IMU), we had to set enable_IMU_fusion to false in the launch configuration file. We were able to edit said file by downloading VScode and running it alongside the Docker container which was a bit challenging .
4. [Setup Isaac ROS Nvblox](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_nvblox/index.html)

SLAM can be done using several different configurations of sensors, but ultimately our team settled on using an Intel Realsense D435 depth camera paired with a TM171 inertial measurement unit (IMU) from SYD Dynamics. Our goal is to coordinate data received from both sensors using the Jetson Orin Nano, and VSLAM will calculate a “pose” in real-time, enabling Newton to keep track of where it is in the environment that it is in. Nvblox is layered on top of VSLAM, which keeps track of moving objects in Newton’s field of view.

Unfortunately, we could only get a demo of the libraries functioning with the IMU option disabled by the time of publishing this post. Look forward to an update from us–whether it’s groundbreaking or just mildly entertaining, we’re as curious as you are!

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=va1h6mMQ7AQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

What you see on the left hand side are the two image streams from the stereo camera, combined with the IR input to produce a “pose” (a red arrow and associated point cloud). Since we ran this VSLAM demo with the IMU option disabled, all the different poses were stacking on each other which results in a mapping of the room.
![gif](/assets/img/blog4/knuckles.gif)

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=dwyfydG_lTI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

This video shows the Nvblox library in action. With the VSLAM instance running, we are able to use Nvblox to essentially create a constant stream of mappings. Since the IMU is not enabled, the software is not able to store the mapping outside of its current view. At the 35 second mark the camera is set down as the person moves backwards, and you can kind of see the person (and heat map) slowly move away from the point of origin (where the camera is placed). 

## Next Steps

The diagram above shows a general overview of what our system architecture will look like. Both the camera and IMU will communicate with the Jetson over UART, which means some synchronization methods are to be considered.

The camera outputs at 6-90 fps depending on the resolution and is the bottleneck in this case. It is probably best to interpolate the IMU’s data feed to match the camera’s timestamps. We suspect that the motors would benefit greatly from more IMU inputs, so it is best to keep the IMU poll rate high. Thankfully, the Realsense SDK automatically adds a timestamp to the depth readings it generates, so we only have to consider the IMU in this case.

Once that is all done, we can test the setup on our Jetson and pray that it can handle running everything.


	
