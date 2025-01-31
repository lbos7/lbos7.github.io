---
name: Propeller-Driven Balance Beam Control System
tools: [C++, PID Control, Mechatronics, Microcontrollers, SolidWorks, Rapid Prototyping]
image: https://lbos7.github.io/media/propellerbeam.gif
description: Contsructed a propeller-driven beam system and wrote 2 PID controllers to balance a ball in the center of the beam
---

# Propeller-Driven Balance Beam
The goal of this project was to build a physical system that is naturally unstable, design a PID controller to stabilize the system, and implement the controller on the system.
<br>

## Group Members
Alex Castrejon, Jun Yen Lim, Kasia Fadeeva, Logan Boswell
<br>

## Demo
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/OrUmdi8MH_U?si=J97v_IkzCE4vNLnD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

## Overview
For a final project in the Georgia Institute of Technology's ME 4012: Control of Motion Systems, my group decided on building a propeller-driven balance beam and designing a control system to make it capable of balancing a metal ball in the center of the beam. A simplified diagram of the system is shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/propellerbeam_diagram.jpg"/></center>
<br>

## System Overview
<br>

#### Physical System
The physical system consists of an 2 ft beam with drone motors and propellers on each end. The beam is free to rotate about its center and the only limits on rotation are due to the ends of the beam colliding the ground or base. The electronic components of the system consists of an IMU for the beam, a linear potentiometer used to track the position of the ball, two electronic speed controllers to set the speed of the drone motors, a 12V power supply, and an Arduino Uno used to control the system. A picture of the system is shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/propellerbeam.jpg"/></center>
<br>

#### Control System
For the control system, it was necessary to design two PID controllers - one for balancing the beam and one for keeping the ball in the center of the beam. MATLAB was used for designing the controllers with tools like the control system designer. The first steps taken were focused on designing and implementing the beam controller. The group started with a propotional controller and then incorporated the integral and derivative gains. Once these gains were determined and the beam was able to be stabilized and reject disturbances, the focus shifted to designing the ball position controller. This controller design process was much more complicated since its output directly affected the setpoint of the beam orientation. Also, the weight of the ball had a significant impact on the beam dynamics. Eventually after making some adjustments, the system worked as intended and the beam was able to balance the ball at its center. The block diagram of the system is shown below and the demo video shows the controller gains used at different points of the project.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/propellerbeam_block_diagram.jpg"/></center>
<br>

## My Focus
In this project I was in charge of designing and building the physical system, including selecting all of the necessary components. In additon to this, I wrote the code for our Arduino microcontroller which only required minimal modifications during testing so we could test the gains for our PID controllers.