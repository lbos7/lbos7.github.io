---
name: Cable-Driven Parallel Robot for Submerged Applications
tools: [C++, Python, Onshape, Rapid Prototyping, Mechatronics, Microcontrollers]
image: https://lbos7.github.io/media/water_cdpr.gif
description: Designed and built a planar cable-driven parallel robot from scratch capable of operating while submerged in water
---

# Cable-Driven Parallel Robot for Submerged Applications
This project serves as my final project for the MS in Robotics program at Northwestern University. The overall goal was to build and develop software for a system capable of reliable operation while submerged in water. I designed and built the system for 7 weeks from late April to early June, worked on software and controls for 8 weeks from mid September to mid November, and modified the design for testing in water for 3 weeks from mid November to mid January.
<p class="text-center">
{% include elements/button.html link="https://github.com/lbos7/planar-cdpr" text="GitHub Repo" %}
</p>

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


With these in mind, I decided on using 4 cables since that would allow for the control of 3 degrees of freedom, just in case the robot use case is altered in the future and control over orientation is necessary. I also added the motors, drivers, and other electronics on the top of robot, so I am able to make minimal changes before I am able to test this design in water. Also, since the frame is made from 8020 extrusion, if the design needs to be scaled up or down, only the necessary rails would need to be changed.
<br>
<div style="display: flex; justify-content: center; gap: 20px;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_CAD.png" width="390"/>
  </div>
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/cpdr_assembled.jpg" width="400"/>
  </div>
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

## Testing in Water
<div style="text-align: center;">
  <img src="{{ site.url }}{{ site.baseurl }}/media/water_cdpr.gif" width="600"/>
  <p>Movement while submerged</p>
</div>
<br>
Before testing in water, modifications were made to the design to protect the electronics from being damaged. Watertight enclosures were purchased and machined to accomodate all of the wiring necessary to connect the electronics. Also, the power supply was moved off of the robot frame where AC power from the wall outlet does not have to be as close to the water and the 24V, GND, and CAN cables can be plugged into their respective connectors on the frame.
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/new_enclosures.jpg" width="325"/>
    <p>Watertight Enclosures on the Robot Frame</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/power_enclosure.jpg" width="400"/>
    <p>Watertight Enclosure for Power Supply</p>
  </div>
</div>
<br>
In addition to these changes, another frame was added to the bottom of the system to increase the height by 8 inches since the Northwestern University Olympic pool (where the testing was being completed) had a minimum water height of 4 feet 2 inches and the workspace frame was a little too short.

<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_frame.jpg" width="400"/>
    <p>Updated Design with Watertight Enclosure and New Frame</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_setup.jpg" width="400"/>
    <p>Testing Setup</p>
  </div>
</div>

## Water Performance
In order to compare how well the robot works while submerged, I completed the same waypoint tests as I did previously (results shown below). Overall, the results did not differ very much at all. This could be due to the small size of the end-effector, the motors being more powerful than necessary, or a combination of both. Either way, the results show that my design can serve it's intended purpose of operating while submerged in water and has room to increase the end-effector size if necessary.
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap; margin-bottom: 20px;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_waypoints5.png" width="400"/>
    <p>0.25 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_waypoints5.png" width="400"/>
    <p>0.5 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_waypoints1.png" width="400"/>
    <p>1 m/s</p>
  </div>
</div>

<!-- Row of 2 -->
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_waypoints15.png" width="400"/>
    <p>1.5 m/s</p>
  </div>

  <div style="text-align: center;">
    <img src="{{ site.url }}{{ site.baseurl }}/media/water_waypoints2.png" width="400"/>
    <p>2 m/s</p>
  </div>
</div>