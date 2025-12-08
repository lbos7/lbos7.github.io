---
name: Cable-Driven Parallel Robot from Scratch (In Progress)
tools: [ROS 2, C++, Python, Onshape, Rapid Prototyping, Mechatronics, Microcontrollers]
image: https://lbos7.github.io/media/cdpr.gif
description: Designed and built a planar cable-driven parallel robot; currently working on the software
---

# Cable-Driven Parallel Robot from Scratch (In Progress)
This project serves as my final project for the MS in Robotics program at Northwestern University. While the long-term objective is to develop a system capable of reliable underwater operation, my primary focus to date has been establishing a fully functional prototype in normal conditions. I have recently began preparing to begin testing in water.
<br>

## Demo
<!-- <center><iframe width="818" height="779" src="https://www.youtube.com/embed/73dWy-ku6m4" title="CPDR Basic Move" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center> -->
<p style="text-align: center;">Square Waypoints (0.4 m side length, centered at (0, 0))</p>
<div style="display: flex; justify-content: center; gap: 20px;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/setpoint_square.gif" width="400"/>
    <p>Setpoint Control</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/traj_square.gif" width="400"/>
    <p>Trajectory Control @ 0.5, 1, and 2 m/s</p>
  </div>
</div>
<br/>
<p style="text-align: center;">Diamond Waypoints (0.4 m side length, centered at (0, 0))</p>
<div style="display: flex; justify-content: center; gap: 20px;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/setpoint_diamond.gif" width="400"/>
    <p>Setpoint Control</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/traj_diamond.gif" width="400"/>
    <p>Trajectory Control @ 0.5, 1, and 2 m/s</p>
  </div>
</div>

## Mechanical Design
Before designing this robot, I had two main constraints/clarifications for this project that are important to note: 
- The desired workspace is 2D and control over end-effector orientation is not necessary
- This robot will eventually need to be scaled up and operate underwater, so the design should take these conditions into account


With these in mind, I decided on using 4 cables since that would allow for the control of 3 degrees of freedom, just in case the robot use case is altered in the future and control over orientation is necessary. I also added the motors, drivers, and other electronics on the top of robot, so I am able to make minimal changes before I am able to test this design in water. Also, since the frame is made from 8020 extrusion, if the design needs to be scaled up or down, only the necessary rails would need to be changed. The CAD model and physical system for the current design are shown below.
<br>
<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_CAD.png" width="350"/>
  <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_assembled.jpg" width="400"/>
</div>
In terms of modeling, the main components of interest of this design are the motor-drum asseblies that are used for winding and unwinding the cables. The drums are threaded, which allows for predictable winding and unwinding of the cables. These drums have heat-set inserts that are used to mount the shaft collars, which then secure the drums to the shafts that are coupled with the motors.
<center><img src="{{ site.url }}{{ site.baseurl }}/media/drum_winding.gif" width="700"/></center>
<br>

## Control System
To move the end-effector while keeping the cables in tension, a custom force-based controller was designed and tuned (block diagram shown below).
<center><img src="{{ site.url }}{{ site.baseurl }}/media/detailed_block_diagram.png" width="700"/></center>
In this control system, position and velocity errors generate a 2D force in the workspace plane, which is then broken down into the 4 specific cable contributions. The tensions from the PID controller are added to estimated tensions from a feedforward model that estimates the tensions based on end-effector position. The sums of the PID and feedforward tensions are converted to torques and sent to the ODrive controller (shown below).
<center><img src="{{ site.url }}{{ site.baseurl }}/media/odrive_controller.png" width="700"/></center>
One of the main motivations for designing the force-based controller is that it makes it easier to keep the cables in tension when the motors are in torque control mode. Another route that could have been taken would have been to operate the motors in position control mode while also sending velocity and torque feedforward commands, but this would likely require a tension distribution algorithm to prevent the cables from having slack.
<br>

## Performance
In order for the controller to function correctly, the position and velocity errors must accurately reflect the current state of the system. Since forward kinematics is used to estimate the current end-effector position, I did some testing to see how accurate this estimate is. For my testing, I moved the end-effector to various points in the workspace and logged the estimated and actual end-effector positions (actual position estimated using apriltags).
<center><img src="{{ site.url }}{{ site.baseurl }}/media/fk_apriltag_scatter.png" width="500"/></center>
While there is some error as the end-effector moves towards the bounds of the workspace, the forward kinematics estimate is accurate enough for the application. In addition to testing the forward kinematics estimate, I also generated some movement plots to see how well the end-effector is following straight-line trajectories at different speeds.

<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap; margin-bottom: 20px;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/ff_waypoints_traj25.png" width="400"/>
    <p>0.25 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/ff_waypoints_traj5.png" width="400"/>
    <p>0.5 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/ff_waypoints_traj1.png" width="400"/>
    <p>1 m/s</p>
  </div>
</div>

<!-- Row of 2 -->
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/ff_waypoints_traj15.png" width="400"/>
    <p>1.5 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/ff_waypoints_traj2.png" width="400"/>
    <p>2 m/s</p>
  </div>
</div>


## Next Steps
As of 12/7/25, I am actively prepping for testing in water and wrapping up this project.