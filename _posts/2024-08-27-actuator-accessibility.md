---
title: "Actuator Accessibility"
date: 2024-08-27
categories: [META]
tags: [team, meta, timeline, goals] 
author: [um]
---
# Cycloidal Drive

> An exercise into a more accessible actuator design for the modified Solo12

Solo12 has a very compact and lightweight design which imposes dimensional constraints on the choice of drive. All joints, except the knee, can be directly driven, reducing the need to source timing belts and associated hardware.

A FDM 3D printed cycloidal drive was initially designed to fit in a 5cmx5cmx5cm bounding box. At this scale, small dimensional variances introduce backlash into the cycloidal drive. To get a better understanding of the tolerances; an open cage cycloidal drive was prototyped and tested.

## Prototype #1

### 3D Prints

![image](/assets/img/blog3/proto1part.jpg)

### In Action (barely)

<iframe width="560" height="315" src="https://youtube.com/embed/QVna_XHsR04" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Main problems with this prototype:
* The cycloidal disk can be heard grinding against the rollers on the fixed plate even though the disk was toleranced for clearance. 
* The 1mm eccentricity of the disk with relation to the center of fixed part of the drive and was tested for next.

## Prototype #2

For the next iteration of the prototype, adjustments were made in CAD as follows: 
* 3 sets of cycloidal disks were printed with each cycloidal profile shaving 0.1mm from the last, in addition to larger clearance tolerances; 
* 6 shafts were printed with each diameter increasing by 0.1mm from 1.0mm to 1.5mm; 
* the rollers were scrapped and replaced by a cycloidal profile on the fixed housing.

### 3D Prints

![image](/assets/img/blog3/proto2part.jpg)

### CAD Mechanism

![image](https://i.imgur.com/VbzoOd5.gif)

![image](https://i.imgur.com/pLFDsca.gif)

 
### Disassembly 

<iframe width="560" height="315" src="https://youtube.com/embed/x-ljx1ZIHF4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### 9:1 Reduction

<iframe width="315" height="560" src="https://youtube.com/embed/TmRMvM5_DZE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Having a single cycloidal disk introduces a lot of vibrations into the drive, so a general recommendation is to have a second cycloidal disk with its cam offset by 180 degrees. This in turn halves the load pin diameter! The third prototype was designed with these changes in mind.
 
## Prototype #3

![image](/assets/img/blog3/proto3outline.png)

### 3D Prints

![image](/assets/img/blog3/proto3parts.jpg)

### Assembled Camshaft 

![image](/assets/img/blog3/assembledcamshaft.jpg)
 
After assembly, the drive was tested for friction, noise and cycle tested for wear. The load during testing was 2 kgs at 1.75cm from the drive's center, resulting in a torque of `0.34 Nm` which is slightly higher than the stall torques listed on the MN4004 [BLDC website](https://store.tmotor.com/product/mn4004-kv300-motor-antigravity-type.html).

**First, to verify the working of the drive, it was hand driven:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/w-Q60KZtuxI?si=IpMGG_jQDmzQIQzH&amp;clip=UgkxLOD4wSL9eqICSaMEuqYT4-Au5g_K57lc&amp;clipt=ENbKFBi2nxg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Then the drive was tested with a 1000 KV BLDC running at 12V:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/_HrEuIPpClU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Finally, using a drill, it was tested at high speed and the aforementioned torque:**

<iframe width="560" height="315" src="https://youtube.com/embed/z4qgHHI9vMk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


After about an hour of intermittently cycling with the drill, the 3D printed discs started wearing at the profile, forming ABS powder and a lot of backlash is observed in the drive.

## Conclusion

Further explorations into more accessible alternatives to the dual-stage timing belt reduction will also be conducted in the near future, check back for bi-weekly updates. :)
