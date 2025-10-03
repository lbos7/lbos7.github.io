---
name: Pool-inator
tools: [ROS 2, Python, MoveIt, OpenCV]
image: https://lbos7.github.io/media/poolinator.gif
description: ROS 2 Package to play a game of pool using an Emika Franka Panda arm and a tabletop pool set
---

# Pool-inator
For a final project in Northwestern University's ME 495: Embedded Systems in Robotics, my group decided on the goal of using a 7 DOF robotic arm to play pool on a tabletop pool set in order to showcase the various skills gained using ROS 2 throughout this course.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/franka.jpg"/></center>
<p class="text-center">
{% include elements/button.html link="https://github.com/ME495-EmbeddedSystems/finalproject-jrblom2" text="GitHub Repo" %}
</p>

## Group Members
An Nguyen, Caroline Terryn, Catherine Maglione, Joseph Blom, Logan Boswell

## Example Game & RVIZ Window
<center>
<iframe width="640" height="360" src="https://www.youtube.com/embed/7k4V3p4_fAY" title="ME 495 Final Project Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>
<br>
<center>
<iframe width="640" height="349" src="https://www.youtube.com/embed/U5X-QT9_VOY" title="ME 495 Final Project RVIZ Window" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>


## Subsystems
- **Franka Emika Robot Arm:** The arm was controlled using the ROS 2 MoveIt API. A wrapper was written to make the API easier to use. The `control` node handles all the movement.
- **Computer Vision:** An Intel RealSense D435 Camera was used for all computer vision. April Tags were used for identifying the pool table's pockets and calibrating the arm's starting position. This camera was also used to identify all of the balls on the table. The `transform` node establishes the link between the camera frame and the robot base frame, and the `image_processor_colors` node identifies the pool balls.
- **Gameplay:** A pool algorithm was implemented so the robot would start a game by breaking and keep playing until all of the balls besides the cue ball (red ball in our case) were pocketed. Then, the robot would knock the cue ball into a pocket and return to its home position. If the cue ball was accidentally knocked in a pocket, the arm would wait until the cue ball is replaced and it is commanded to resume playing.

## My Focus
In this project my focus was on few areas, including movement and gameplay. I wrote some initial movement functions that were used for calibration in the early stages of this project, that were further refined and used for gameplay as the project went on. I also designed some custom pool cues that were easier to the robot to grip and maneuver around the table.

## Highlights
Here is a compilation of some of the best shots the robot made on the table.
<center>
<iframe width="640" height="360" src="https://www.youtube.com/embed/Oia1yhfn_NE" title="ME 495 Final Project Best Shots" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>