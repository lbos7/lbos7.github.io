---
name: Cable-Driven Parallel Robot (In Progress)
tools: [ROS2, C++, Python, Onshape, Rapid Prototyping]
image: https://lbos7.github.io/media/cpdr_basic_move.gif
description: Designed and built a planar cable-driven parallel robot; currently working on the software
---

# Cable-Driven Parallel Robot
This project serves as the final project for the MS in Robotics program at Northwestern University. While the long-term objective is to develop a system capable of reliable underwater operation, my primary focus to date has been establishing a fully functional prototype above water. I began work on the system during the Spring 2025 quarter (late April through early June) and made significant progress during that time. I am currently completing a summer internship (June–September) and plan to resume development in my final quarter, from September through December.
<br>

## Demo
<center><iframe width="818" height="779" src="https://www.youtube.com/embed/73dWy-ku6m4" title="CPDR Basic Move" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

## Mechanical Design
To start this project, I began by picking out parts and making a CAD model in Onshape. I decided on using a Raspberry Pi 5 running Ubuntu 24.04 LTS to operate the robot, which would allow me to use the most recent ROS2 distribution (Jazzy) that's also installed on my computer. For actually moving the robot, I decided on using three 12 V brushed DC encoder motors from Pololu with 60 mm omniwheels connected to a 4-channel encoder motor driver from Hiwonder that uses I2C communication. Most of the parts are purchased, but a few of them are custom made (the 3 different levels are cut out of acrylic and the Raspberry Pi spacer, motor driver spacer, battery mounts, and paddle mount are all 3D printed with PLA). The model and physical robot are shown below.
<br>
<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_CAD.png" width="350"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_assembled.jpg" width="400"/>
</div>
<br>

After building this first version of the robot, I ran into a few issues: struggles accelerating from rest and inaccurate odometry updates. In order to address these issues, the robot was redesigned to include new motor drivers with higher output current, a PWM driver to interface with the drivers, an IMU, and a new battery (which resulted in a loss of about 1 lb). The redesigned robot is shown below. I still use the 4 channel encoder motor driver to read the encoders, but I use the PWM driver board to generate the PWM signals necessary to move the motors. The new motor drivers use one PWM signal and two digital signals per motor to set motor speed and direction. These new additions resulted in better performance.
<br>

<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_new_design.jpg" width="400"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_bottom_layer.jpg" width="400"/>
</div>
<br>