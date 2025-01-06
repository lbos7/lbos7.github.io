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
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/W0dDw8HSiHI?si=N4vRB3vX4GtSHSFd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>
<br>

## Setup
The first steps taken in this project consisted of setting up transformation matrices between the world, jack, and box frames. These matrices are used to make the necessary calculations of easier. A diagram of the system with the transformation matrices can be seen below.
<div style="flex: 1; text-align: left;">
    <img src="https://lbos7.github.io/media/jackbox.png"/>
</div>
<br>

## Lagrangian Dynamics
\[
\frac{d}{dt} \left( \frac{\partial L}{\partial \dot{q_i}} \right) - \frac{\partial L}{\partial q_i} = Q_i
\]