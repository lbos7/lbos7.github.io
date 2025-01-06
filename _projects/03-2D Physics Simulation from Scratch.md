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
    <img src="https://{{ site.url }}{{ site.baseurl }}/media/jackbox.png"/>
</div>
<br>

## Lagrangian Dynamics
<center><img src="https://{{ site.url }}{{ site.baseurl }}/media/forcedEL.jpg"/></center>
The forced Euler-Lagrange equations (shown above) were used to calculate the instaneous accelerations of the bodies that are essential for simulating the system. The Lagrangian (L) can be calculated by finding the body velocities of the box and the jack, defining the inertial matrices, and calculating the kinetic energy and potential energy. In this simulation, external forces (Q_i in the equations above) are applied to Y-coordinate and psi-coordinates of the box to keep it around the same height throughout the simulation. Using the Lagrangian and external forces, the equation shown above can be calculated for each component of the configuration q. From these equations, the accelerations of the configuration are found, and the system is simulated using 4th-order Runge-Kutta integration over a 0.01 second timestep.
<br>

## Impacts
In order to include elastic impacts in the simulation of this system, the locations of each of the 4 masses on the jack were checked to see if they had come in contact with the box walls at each timestep. If the jack had come in contact with the box, then the velocities of the bodies were updated appropriately using impact update equations involving the Hamiltonian and momentum.