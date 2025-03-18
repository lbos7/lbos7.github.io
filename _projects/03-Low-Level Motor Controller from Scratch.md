---
name: Low-Level Motor Controller from Scratch
tools: [C, Mechatronics, PID Control]
image: https://lbos7.github.io/media/motor_control_demo.gif
description: Built a development board using a PIC32MX170F256B with peripherals and implemented PID control to make a motor driver
---

# Low-Level Motor Controller from Scratch
The goal of this project was to implement concepts of robotic manipulation such as screw theory, motion planning, trajectory generation, and control through simulation of a pick and place task using a KUKA youBot in CoppeliaSim. A KUKA youBot is mobile manipulator with an omnidirectional base and a 5R robot arm (shown below).
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/youBot.jpg" width="500"/></center>
<br>

## Demo
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/W-60ke0rfIs?si=hSfqu9TzXMuvUW30" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>
<br>

## Overview
This project was divided into 3 main stages - youBot kinematics, end-effector reference trajectory generation, and controls. Each stage was associated with a corresponding function that were used to perform the simulation: NextState, TrajectoryGenerator, and FeedbackControl. NextState takes in the current robot configuration and calculates the new configuration after a .01s timestep using first-order Euler integration. TrajectoryGenerator creates an ideal trajectory for the end-effector in order to pick up the cube and drop it off in the correct place. FeedbackControl applies the kinematic task-space feedforward plus PI control law, which is shown below.
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

##### New Task
In this trial, the starting orientation of the block and the drop off position were both modified. The same controller from the best trial runn was used in this trial.
<br>
<center><img src="{{ site.url }}{{ site.baseurl }}/media/newTask.png"/></center>
<br>
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/2Mv__pqTEF0?si=q05RkmNtKlVD0KZ4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>