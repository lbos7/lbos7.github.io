---
name: KUKA youBot Pick & Place
tools: [Python, Robot Maniplulation, Motion Planning, Screw Theory, CoppeliaSim, PID Control]
image: https://lbos7.github.io/media/pick&place.gif
description: Simulation of a KUKA youBot performing a pick and place task.
---

# KUKA youBot Pick & Place
The goal of this project was to implement concepts of robotic manipulation such as screw theory, motion planning, trajectory generation, and control through simulation of a pick and place task using a KUKA youBot in CoppeliaSim.

## Demo
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/W-60ke0rfIs?si=hSfqu9TzXMuvUW30" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>
<br>

## Overview
This project was divided into 3 main stages - youBot kinematics, end-effector reference trajectory generation, and controls. Once each stage was completed, a script was written to generate csv files with 13 elements in each line to run the simulation in CoppeliaSim. The 13 elements in the csv files repesent the following, in order: chassis orientation, chassis x-postion, chassis y-position, joint 1 angle, joint 2 angle, joint 3 angle, joint 4 angle, joint 5 angle, wheel 1 angle, wheel 2 angle, wheel 3 angle, wheel 4 angle, gripper state.
<br>

## youBot Kinematics
In order to calculate the first 12 elements in each csv line, a function was written that took in the following inputs: 12-vector representing current robot configuration, 9-vector representing joint and wheel speeds, timestep, max speed of joints and wheels. Using these inputs, the new robot configuration after the timestep was determined. 
<br>

## End-Effector Reference Trajectory Generation
<br>

## Controls
<br>

