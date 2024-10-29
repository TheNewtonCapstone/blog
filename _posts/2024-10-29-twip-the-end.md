---
title: "TWIP: The End of An Era"
date: 2024-10-29
categories: [TWIP]
tags: [team, twip, newton, goals, sim2real, motors] 
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

## Humps & Bumps
Now, let me tell you that getting here was not easy 😅 We won't list out every issue we've had, but the following points (and how we tackled them) are the most important ones:

1. **Unreliable Motors**: As someone historically more in software than hardware, it's not often that you can find culpability for an issue in the hardware you're using (as it's generally your fault), but this was one of those. Having unreliable motors with close to non-existent datasheets makes this kind of project close to impossible and I believe that is the main reason we could not cross the finish line.
2. **Choppy Communication**: Turns out communication within robots can be just as complicated as between humans. That's it. Nothing more. Jokes aside, communication between the ESP32 and the Jetson Orin Nano was a challenge (we tried USB, then WiFi), where we finally ended using a custom protocal on top of UART through the expansion pins. We were also using micro-ROS on the ESP32 which made the job harder, so after going for a more barebones approach, we managed to get motor commands and IMU data across the wire.
3. **Random Delays & Noise**: Another seemingly obvious discovery was that a real system is full of delays while the simulated one is, well perfect. Dealing with that issue in simulation, by following [this paper](https://github.com/rmst/rlrd), was a massive push forward in briding the Sim-To-Real gap. We can't forget about the amount of noise in every measurement and action we take and do in real life. Since simulation doesn't inherently have that built-in, adding it manually before we applied torque and before we read actions was critical to our progress.

## Looking Ahead
> _Every new beginning comes from some other beginning's end._ -Seneca

We can't stay on TWIP forever. We've learned an incredible amount from this project and thank the gym2real team for the resources they made available to us (and anyone else!). As we start building Newton and transition from TWIP, we just want to leave you with a couple of thoughts and lessons we've gathered from this project:

1. **Start Small**: Starting with Newton right from the bat would have been a disaster. Using TWIP to learn about the RL pipeline, the hardware and software integration issues we faced and the general difficulties that come with training a simulated robot was *amazing* and we're armed with a lot of knowledge for the dog.
2. **Simulation is Not Reality**: Although this might not come as surprise for you, dear reader, the magnitude of the difference between simulation and reality was quite the shock for us. We believe our inability to model the motors' behavior accurately was the main reason we couldn't get TWIP to stand up and it's something we'll be very careful about when building Newton (which does have much nicer motion systems, as seen in this [actuator post]({% post_url 2024-08-27-actuator-accessibility %})). Following recommendations of our advisor, we even built a Proportional Integral Derivative (PID) controller in simulation to verify that the behaviour we saw in real life is what is correctly portrayed virtually.
3. **ROS or No ROS**: To use ROS has been a point of contention within the team for a very long time: on one hand you have all the benefits and perks of using a battle-tested collection of libraries, but on the other, you find yourself with this mountain of a learning curve and, sometimes, quirky ways of doing things that costs a lot of development time. We wish we could say exactly what the answer is, but that'll have to be in a future post because we don't yet know!

## Where Does That Leave Us?
When you've been working in the RL space for any amount of time and you think about how animals learn, say a newborn when they see their own hands, the irony is palpable. We go on in our daily lives, observing how the world around us works in all of its intricacies and little details, processing that in our minds, producing rewards in response to those observations in our brains while acting and reacting.

I often like saying that the world is very much full of copying and recopying: what someone built yesterday becomes the foundation of what you'll build today and inspire people tomorrow. Seeing how nature does her thing and experimenting with RL is a great example of this, and a testament to how working together is really what matters.

> _Alone we make sand castles: together, we build pyramids._

See you next time!
