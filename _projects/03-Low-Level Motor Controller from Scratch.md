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

## Development Board Setup
<center><img src="{{ site.url }}{{ site.baseurl }}/media/board.jpg" width="500"/></center>
<br>

## Testing Setup
<center><img src="{{ site.url }}{{ site.baseurl }}/media/test_setup.jpg" width="500"/></center>
<br>

## Current Control Response
<center><img src="{{ site.url }}{{ site.baseurl }}/media/itest.png"/></center>
Gains Used: Kp = .08, Ki = .07975
<br>

## Trajectory Tracking Results
<center><img src="{{ site.url }}{{ site.baseurl }}/media/step.jpg"/></center>
Gains Used: Kp = 10, Ki = .03, Kd = 250
<br>
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/cubic.jpg"/></center>
Gains Used: Kp = 10, Ki = .03, Kd = 1200
<br>

## Demo
<center><iframe width="700" height="537" src="https://www.youtube.com/embed/H6QUa2eLzIY" title="ME 333 Final Project Demo - Low-Level Motor Driver" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>