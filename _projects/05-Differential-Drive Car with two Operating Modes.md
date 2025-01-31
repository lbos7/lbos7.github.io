---
name: Differential-Drive Car with two Operating Modes from Scratch
tools: [LabVIEW, PID Control, Mechatronics, Microcontrollers, SolidWorks, Rapid Prototyping]
image: https://lbos7.github.io/media/ddcar.gif
description: Contsructed a differential-drive car capable of following a line or being controlled by an RC remote
---

# Differential-Drive Car with two Operating Modes
The goal of this project was to build a differential-drive car that is able to follow a line or be controlled by a remote.
<br>

## Group Members
Zachary Burkhardt, Logan Boswell
<br>

## Demo
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/wliyiFiHKXM?si=El4xbFObbxSllT5N" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

## Overview
For a final project in the Georgia Institute of Technology's ME 4405: Introduction to Mechatronics, my group decided on building a differential-drive car that is able to follow a line or be controlled by a remote.

## System Overview
To start this project, electronic components were selected and a preliminary CAD model was created. Some components of this model, such as the base, some mounts for different hardware, and the cover for the MyRIO needed to be made by the group through 3D printing or cutting with a waterjet. The model (with a few compenents omitted including screws and the wheels) is shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/ddcar_cad.jpg"/></center>
<br>
Once all of the necessary parts were made or had arrived, the car was assembled and all of the electronics were connected. The assembled car is shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/ddcar.jpg"/></center>
<br>
The electronic components of the car and how they are connected are shown in the diagram below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/ddcar_wiring.jpg"/></center>
<br>

## Control Logic
When the car is powered on, it starts in line-following mode in which it only moves if a black line is detected by any element of the reflectance sensor array. Based on which elements of the reflectance sensor array detect the line, a PID controller adjusts the speeds of the motors in order to keep the car centered on the line. When a button on the side of the MyRIO is pressed, the car switches to remote-control mode where a joystick RC remote sends 2 PWM signals based on its xy-position. These signals are sent through the PWM to analog converters shown in the wiring diagram, and these signals are used to determine the direction of the joystick. That direction is compared to the current orientaion of the car determined using the magnetometer, and the same PID controller used for the line following mode is used to adjust the motor speeds.

## My Focus
In this project I was in charge of designing and building the physical system, including selecting all of the necessary components. In additon to this, I wrote the main virtual instrument file for operating the car and sub virtual instrument file for integrating the RC remote.
