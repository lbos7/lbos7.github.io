---
name: Low-Level Motor Controller from Scratch
tools: [C, Mechatronics, Microcontrollers, PID Control]
image: https://lbos7.github.io/media/motor_control_demo.gif
description: Built a development board using a PIC32MX170F256B with peripherals and implemented PID control to create a motor driver
---

# Low-Level Motor Controller from Scratch
The goal of this project was to build and program a motor driver development board using a PIC32MX170F256B microcontroller that can be used for dc motor position control.
<br>

## Overview
This was the final project of Northwestern University's ME 333: Intro to Mechatronics, so the hardware used in the system was selected for all of the students in the class
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/feedforwardlaw.png"/></center>
<br>

## Results
There were 3 cases used to test the controller and fine tune the associated gains. The 6-vector representing end effector error was plotted over time each of these case.
<br>

##### Overshoot
In this trial, the robot was still able to pick up the block and move it near the drop off location, but there was still a decent bit of error.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/overshoot.png"/></center>
<br>

##### Best Run
This trial was the best result I was able to obtain, and the corresponding video is at the top of this page
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/best.png"/></center>
<br>

## Demo
<center><iframe width="700" height="537" src="https://www.youtube.com/embed/H6QUa2eLzIY" title="ME 333 Final Project Demo - Low-Level Motor Driver" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>