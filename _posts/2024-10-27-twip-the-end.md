---
title: "TWIP: The End of An Era"
date: 2024-10-27
categories: [TWIP]
tags: [team, twip, newton, goals] 
author: [amp, sis]
---

# TWIP: The End of An Era

Before diving into building Newton, our robot dog, we started building TWIP, a Two-Wheeled Inverted Pendulum robot, designed and ideated by [gym2real](https://jonah-gourlay44.github.io/gym2real/), a Capstone team, in the University of British Columbia. We wanted a straightforward way to learn about the Reinforcement Learning (RL) pipeline with a robot that we can easily, and cheaply, build.

## The Beginning

We've started working on TWIP in the beginning of summertime and the project has indeed been a rollercoaster: from late days at the IEEE Concordia lab, to tiny victories and deceits, finally to where TWIP is now. We set out to have a robot that could get up from an upright position and balance itself; we haven't reached both of those goals and **that's okay**.

<iframe width="315" height="560" src="https://www.youtube.com/embed/jCcrJ1Haomw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Where TWIP is Now
As you could see in the video, starting from an upright position, TWIP is able to catch itself when suffering minor disturbances, but once it falls, it can't get up... We've worked very hard and not achieving our set out goals was almost a true disappointment. However, we choose to not think that way, because looking back at where we started, it's crazy to see how far we've come.

<iframe width="315" height="560" src="https://www.youtube.com/embed/fJqC3l1YIR4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Looking Ahead
> _Every new beginning comes from some other beginning's end._ -Seneca

We can't stay on TWIP forever. We've learned an incredible amount from this project and thank the gym2real team for the resources they made available to us (and anyone else!). As we start building Newton and transition from TWIP, we just want to leave you with a couple of thoughts and lessons we've gathered from this project:

1. **Start Small**: Starting with Newton right from the bat would have been a disaster. Using TWIP to learn about the RL pipeline, the hardware and software integration issues we faced and the general difficulties that come with training a simulated robot was *amazing* and we're armed with a lot of knowledge for the dog.
2. **Simulation is Not Reality**: Although this might not come as surprise for you, dear reader, the magnitude of the difference between simulation and reality was quite the shock for us. We believe our inability to model the motors' behavior accurately was the main reason we couldn't get TWIP to stand up and it's something we'll be very careful about when building Newton (which does have much nicer motion systems, as seen in this [actuator post](2024-08-27-actuator-accessibility.md)).
//TODO: add some more points

## Where Does That Leave Us?
When you've been working in the RL space for any amount of time and you think about how animals learn, say a newborn when they see their own hands, the irony is palpable. We go on in our daily lives, observing how the world around us works in all of its intricacies and little details, processing that in our minds, producing rewards in response to those observations in our brains while acting and reacting.

I often like saying that the world is very much full of copying and recopying: what someone built yesterday becomes the foundation of what you'll build today and inspire people tomorrow. Seeing how nature does her thing and experimenting with RL is a great example of this, and a testament to how working together is really what matters.

> _Alone we make sand castles: together, we build pyramids._

See you next time!