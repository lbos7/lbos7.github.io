---
name: 2D Physics Simulation from Scratch
tools: [Python, Lagrangian Dynamics]
image: https://lbos7.github.io/media/jackbox.gif
description: Simulation of a jack in a box with elastic impacts and external forces.
---

# 2D Physics Simulation from Scratch
This project is a simulation of a 6 DoF system modeled using Lagrangian dynamics. The system consists of a large "box" body with a small "jack" body inside of it where each body is free to translate in two directions and rotate about one axis.
<br>

## Demo
<div style="position: relative; padding-bottom: 28.125%; height:0; overflow: hidden;">
    <video src="https://lbos7.github.io/media/jackbox.mp4" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video>
</div>
<br>

## Setup
The first steps taken in this project consisted of setting up transformation matrices between the world, jack, and box frames. These matrices are used to make the necessary calculations of easier. A diagram of the system can be seen below
<div style="flex: 1; text-align: left;">
    <img src="https://lbos7.github.io/media/jackbox.png"/>
</div>
<br>
