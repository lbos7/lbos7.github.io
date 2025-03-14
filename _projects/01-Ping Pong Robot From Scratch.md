---
name: Ping Pong Robot From Scratch (In Progress)
tools: [ROS2, C++, Computer Vision, Onshape, Rapid Prototyping]
image: https://lbos7.github.io/media/pingpongbot_tracking.gif
description: Currently designing an omnidirectional robot capable returning ping pong balls to a player
---

# Ping Pong Robot from Scratch
The goal of this project is to build a omnidirectional robot from scratch that is capable of tracking ping pong balls and moving accordingly.
<br>
<br>

## Hardware
To start this project, I began by picking out parts and making a CAD model in Onshape. I decided on using a Raspberry Pi 5 running Ubuntu 24.04 LTS to operate the robot, which would allow me to use the most recent ROS2 distribution (Jazzy) that's also installed on my computer. For actually moving the robot, I decided on using three 12 V brushed DC encoder motors from Pololu with 60 mm omniwheels connected to a 4-channel encoder motor driver from Hiwonder that uses I2C communication. Most of the parts are purchased, but a few of them are custom made (the 3 different levels are cut out of acrylic and the Raspberry Pi spacer, motor driver spacer, battery mounts, and paddle mount are all 3D printed with PLA). The model and physical robot are shown below.
<br>
<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_cad.png"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_assembled.jpg" width="700"/>
</div>
<br>

After building this first version of the robot, I ran into a few issues: struggles accelerating from rest and inaccurate odometry updates. In order to address these issues, the robot was redesigned to include new motor drivers with higher output current, a PWM driver to interface with the drivers, an IMU, and a new battery (which resulted in a loss of about 1 lb). The redesigned robot is shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_new_design.jpg" width="700"/></center>
<br>

<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_new_design.jpg" width="700"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_bottom_layer.jpg" width="700"/>
</div>
<br>

## Software
I'm currently working on this aspect of the project. So far I've been focused on writing the code necessary for movement, and I will soon shift to the code for the vision component of the project. Here are some simple movement demos.


<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/straight_line.gif" width="400"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/spin.gif" width="400"/>
</div>


<center><iframe width="880" height="658" src="https://www.youtube.com/embed/xniCxi777LI" title="PingPongBot Tracking Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>