---
title: "Actuator Accessibility"
date: 2024-08-31
categories: [MECH]
tags: [mech, actuator, cycloidal, drive, timeline, goals] 
author: [um]
---
# Cycloidal Drive

> An exercise into a more accessible actuator design for the modified Solo12

Solo12 has a very compact and lightweight design which imposes dimensional constraints on the choice of drive. All joints, except the knee, can be directly driven, reducing the need to source AT3 timing belts, pulleys and associated hardware.

Alternative drive mechanism are explored in order to find a more accessible approach to quadruped joints i.e. in this case the cycloidal drive is fully 3D printed and only requires standard bearings.

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
 

After assembly, the drive was tested for friction, noise and cycle tested for wear. The load during testing was 2 kgs at 1.75cm from the drive's center, resulting in a torque of `0.34 Nm` which is slightly higher than the stall torques listed on the MN4004 [BLDC website](https://store.tmotor.com/product/mn4004-kv300-motor-antigravity-type.html). This is still ~8x lower than the maximal output torque expected from the solo12 actuator (~2.7Nm), but is closer to torque values during resting / trotting gait.


**First, to verify the working of the drive, it was hand driven:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/w-Q60KZtuxI?si=IpMGG_jQDmzQIQzH&amp;clip=UgkxLOD4wSL9eqICSaMEuqYT4-Au5g_K57lc&amp;clipt=ENbKFBi2nxg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Then the drive was tested with a 1000 KV BLDC running at 12V:**

<iframe width="560" height="315" src="https://www.youtube.com/embed/_HrEuIPpClU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Finally, using a drill, it was tested at high speed and the aforementioned torque:**

<iframe width="560" height="315" src="https://youtube.com/embed/z4qgHHI9vMk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


After about an hour of intermittently cycling with the drill, the 3D printed discs started wearing at the profile, forming ABS powder and a lot of backlash is observed in the drive.

### Current drive cost:

| Parts | Cost (CAD) | Quantity |
|---|---|---|
| ABS | ~1.6$ | 79 grams |
| [1603-2RS Bearing](https://www.amazon.ca/-/fr/Roulement-1603-2RS-caoutchouc-pr%C3%A9-lubrifi%C3%A9-graisse/dp/B08LBPSM1X/ref=sr_1_6?dib=eyJ2IjoiMSJ9.ti84m15yDUqLvImSaTObztfjQSy3eW0E7GxNDdjO0mBdc9GhWneKA76M5GwPHK1HiR2r7KFaqEajvwytieRBp6QGb1EM6SNJqTQ7-S6Lig8hTrGVeOY_quqlXRKQUwVxeKjwlOUxcMP9w-CRYNrKozpCRBoPkSG5fCA59P41e0n3jZdZnXfWpazko4b5GHR_vNf2_UrJqVaQY0_im2oeBmWkebpTX9o0qrtpTX2CTHgIkNF3O62Q9cR2v4sBPZCiB-w5-2lXOo8r-mv39Xwnl3Yxwi9YW2UUcjLcDg8Q3_g.EnlBfy-jY-9c8_LxVoT8lmUPbbFePV4Ioq0-yTOPBYA&dib_tag=se&keywords=1603-2rs&qid=1725058832&sr=8-6&th=1) | 3.2$ | 2 |
| [M2x30mm](https://www.aliexpress.com/item/32810872544.html?spm=a2g0o.order_list.order_list_main.295.3bf61802k1RLhw) | 0.8$ | 10 |
| [M2 Hex Nut](https://www.aliexpress.com/item/4000226223259.html?spm=a2g0o.order_list.order_list_main.310.3bf61802k1RLhw) | 0.36$ | 10 |
| [MR128ZZ](https://www.aliexpress.com/item/32952690830.html?spm=a2g0o.order_list.order_list_main.82.3bf61802k1RLhw) | 0.4$ | 2 |
| Total Cost: | 6.36$ |  |

## Conclusion


This exercise helped the mechanical team better understand the long term drawbacks of a 3D printed drive at the aforementioned scale. The cycloidal drive quickly wears down and loses alot of its favorable properties. Quick way to reduce friction in the drive would be to replace the lobes of the cycloidal profile against which the disk moves with rollers but this brings with it additional hardware costs. One could also have multiple cycloidal disks offset by smaller angles but this would keep decreasing the load pin diameter to a point where it would be impossible for the pins to be structural!

Further explorations into more accessible alternatives to the dual-stage timing belt reduction will also be conducted in the near future, check back for bi-weekly updates. :)
