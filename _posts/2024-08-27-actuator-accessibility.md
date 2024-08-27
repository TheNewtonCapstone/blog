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

3D Printed Parts for Prototype #1:
![image]()

Prototype #1:
<iframe width="315" height="560" src="https://youtu.be/QVna_XHsR04" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Main problems:
The cycloidal disk can be heard grinding against the rollers on the fixed plate even though the disk was tolerance for clearance. 
The 1mm eccentricity of the disk w.r.t. the center of fixed part of the drive and was tested for next.

In the next iteration of the prototype, tolerances were adjusted in CAD i.e. 3 sets of cycloidal disks were printed in increments of 0.1mm shaved off the cycloidal profile in addition to clearance tolerances, 6 shafts in increments of 0.1mm from 1.0 to 1.5mm were tested with, the rollers were replaced with a cycloidal profile on the fixed housing.

3D printed parts:
  

Mechanism in CAD:
https://imgur.com/VbzoOd5
https://imgur.com/pLFDsca
Eccentric Cam Shafts:
 
Disassembly of second prototype:
https://youtu.be/x-ljx1ZIHF4
9:1 Reduction:
https://youtu.be/TmRMvM5_DZE

Having just one cycloidal disk introduces a lot of vibrations into the drive, a general recommendation is to have a second cycloidal disk with its cam offset 180 degrees. This in turn halves the load pin diameter. The third prototype was designed with these changes in mind.
 

3D printed parts:
 
Assembled Camshaft assembly:
 
This drive was then tested for friction in the drive, noise of the drive and cycle tested for wear.
The load in the testing was 2 kgs at 1.75cm from drive center giving a torque of 0.34 N-m which is slightly higher than the stall torques listed on the MN4004 BLDC website. (https://store.tmotor.com/product/mn4004-kv300-motor-antigravity-type.html)
To verify the working of the drive, it was hand driven:
https://youtube.com/clip/UgkxLOD4wSL9eqICSaMEuqYT4-Au5g_K57lc?si=RQd-x4S8ojQAsEUm
Then the drive was tested with a 1000 kV BLDC running at 12V:
https://www.youtube.com/watch?v=_HrEuIPpClU
Finally using a drill, it was tested at high speed and the aforementioned torque:
https://youtu.be/z4qgHHI9vMk
After about an hour of cycling the drill intermittently the 3D printed discs start wearing at the profile and forming ABS powder and a lot of backlash is observed in the drive.
Further explorations into more accessible alternatives to the dual-stage timing belt reduction will also be conducted in the near future, subscribe for bi-weekly update
