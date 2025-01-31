---
name: Ping Pong Robot From Scratch (In Progress)
tools: [ROS2, C++, MoveIt, Computer Vision, Onshape, Rapid Prototyping]
image: https://lbos7.github.io/media/pingpongbot_assembled.jpg
description: Currently designing and writing the software for an omnidirectional robot capable of playing ping pong.
---

# Ping Pong Robot from Scratch
The goal of this project is to build a omnidirectional robot from scratch that is capable of returning ping pong balls to a player. As of 1/31/25, the initial robot has been built and my focus has shifted to the software side of the project.
<br>
<br>

## Hardware
To start this project, I began by picking out parts and making a CAD model in Onshape. I decided on using a Raspberry Pi 5 running Ubuntu 24.04 LTS to operate the robot, which would allow me to use the most recent ROS2 distribution (Jazzy) that's also installed on my computer. For actually moving the robot, I decided on using 3 12 V brushed DC encoder motors from Pololu with 60 mm omniwheels connected to a 4-channel encoder motor driver from Hiwonder. Most of the parts are purchased, but a few of them are custom made (the 3 different levels are cut out of acrylic and the Raspberry Pi spacer, motor driver spacer, battery mounts, and paddle mount are all 3D printed with PLA). The model and physical robot are shown below.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_cad.png"/></center>
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/pingpongbot_assembled.jpg" width=400/></center>
<br>


## Example Game & RVIZ Window
<center>
    <div style="position: relative; padding-bottom: 28.125%; height:0; overflow: hidden;">
        <video src="{{ site.url }}{{ site.baseurl }}/media/poolinator.mp4" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video>
    </div>
</center>
<br>
<center>
    <div style="position: relative; padding-bottom: 28.125%; height:0; overflow: hidden;">
        <video src="{{ site.url }}{{ site.baseurl }}/media/poolinator_rviz.webm" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video>
    </div>
</center>

## Subsystems
- **Franka Emika Robot Arm:** The arm was controlled using the ROS2 MoveIt API. A wrapper was written to make the API easier to use. The `control` node handles all the movement.
- **Computer Vision:** An Intel RealSense D435 Camera was used for all computer vision. April Tags were used for identifying the pool table's pockets and calibrating the arm's starting position. This camera was also used to identify all of the balls on the table. The `transform` node establishes the link between the camera frame and the robot base frame, and the `image_processor_colors` node identifies the pool balls.
- **Gameplay:** A pool algorithm was implemented so the robot would start a game by breaking and keep playing until all of the balls besides the cue ball (red ball in our case) were pocketed. Then, the robot would knock the cue ball into a pocket and return to its home position. If the cue ball was accidentally knocked in a pocket, the arm would wait until the cue ball is replaced and it is commanded to resume playing.
<br>

## My Focus
In this project, my focus was on few areas, including movement and gameplay. I wrote some initial movement functions that were used for calibration in the early stages of this project, that were further refined and used for gameplay as the project went on. I also designed some custom pool cues that were easier to the robot to grip and maneuver around the table.
<br>

## Highlights
Here is a compilation of some of the best shots the robot made on the table.
<br>
<center>
    <div style="position: relative; padding-bottom: 28.125%; height:0; overflow: hidden;">
        <video src="{{ site.url }}{{ site.baseurl }}/media/PoolSuperCut.mp4" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video>
    </div>
</center>