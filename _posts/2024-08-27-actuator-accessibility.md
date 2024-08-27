---
title: "Actuator Accessibility"
date: 2024-08-27
categories: [META]
tags: [team, meta, timeline, goals] 
author: [um]
---
### Cycloidal Drive

> An exercise into a more accessible actuator design for the modified solo12

The solo12 has a very compact and lightweight design which imposes dimensional constraints on the drive of choice. All joints except the knee can be directly driven reducing the need for sourcing  timing belts and associated hardware.

A FDM 3D printed cycloidal drive was initially designed to fit in a 5cmx5cmx5cm bounding box. At this scale, small dimensional variances introduce backlash into the cycloidal drive. To get a better understanding of the tolerances; an open cage cycloidal drive was prototyped and tested.

## Prototype #1

3D Printed Parts for Prototype #1:
![image](/assets/img/blog#3/proto1part.jpg)

Prototype #1 in action (barely):
<iframe width="315" height="560" src="https://youtu.be/QVna_XHsR04" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Main problems with prototype #1:
The cycloidal disk can be heard grinding against the rollers on the fixed plate even though the disk was tolerance for clearance. 
The 1mm eccentricity of the disk w.r.t. the center of fixed part of the drive and was tested for next.

## Prototype #2

In the next iteration of the prototype, tolerances were adjusted in CAD i.e. 3 sets of cycloidal disks were printed in increments of 0.1mm shaved off the cycloidal profile in addition to clearance tolerances, 6 shafts in increments of 0.1mm from 1.0 to 1.5mm were tested with, the rollers were replaced with a cycloidal profile on the fixed housing.

3D printed parts:
![image](/assets/img/blog#3/proto2part.jpg)

Mechanism in CAD:
https://imgur.com/VbzoOd5

https://imgur.com/pLFDsca

 
Disassembly of second prototype:

<iframe width="315" height="560" src="https://youtu.be/x-ljx1ZIHF4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

9:1 Reduction:

<iframe width="315" height="560" src="https://youtu.be/TmRMvM5_DZE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Having just one cycloidal disk introduces a lot of vibrations into the drive, a general recommendation is to have a second cycloidal disk with its cam offset 180 degrees. This in turn halves the load pin diameter. The third prototype was designed with these changes in mind.
 
## Prototype #3

![image](/assets/img/blog#3/proto3outline.png)

3D printed parts:
![image](/assets/img/blog#3/proto3parts.jpg)

Assembled Camshaft assembly:
![image](/assets/img/blog#3/assembledcamshaft.jpg)
 
This drive was then tested for friction in the drive, noise of the drive and cycle tested for wear.

The load in the testing was 2 kgs at 1.75cm from drive center giving a torque of 0.34 N-m which is slightly higher than the stall torques listed on the MN4004 BLDC website. (https://store.tmotor.com/product/mn4004-kv300-motor-antigravity-type.html)

To verify the working of the drive, it was hand driven:

<iframe width="315" height="560" src="https://youtube.com/clip/UgkxLOD4wSL9eqICSaMEuqYT4-Au5g_K57lc?si=RQd-x4S8ojQAsEUm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Then the drive was tested with a 1000 kV BLDC running at 12V:

<iframe width="315" height="560" src="https://www.youtube.com/watch?v=_HrEuIPpClU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Finally using a drill, it was tested at high speed and the aforementioned torque:

<iframe width="315" height="560" src="https://youtu.be/z4qgHHI9vMk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


After about an hour of cycling the drill intermittently the 3D printed discs start wearing at the profile and forming ABS powder and a lot of backlash is observed in the drive.

Further explorations into more accessible alternatives to the dual-stage timing belt reduction will also be conducted in the near future, subscribe for bi-weekly updates. :)
