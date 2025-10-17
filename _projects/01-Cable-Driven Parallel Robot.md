---
name: Cable-Driven Parallel Robot from Scratch (In Progress)
tools: [ROS 2, C++, Python, Onshape, Rapid Prototyping, Mechatronics, Microcontrollers]
image: https://lbos7.github.io/media/cdpr.gif
description: Designed and built a planar cable-driven parallel robot; currently working on the software
---

# Cable-Driven Parallel Robot from Scratch (In Progress)
This project serves as my final project for the MS in Robotics program at Northwestern University. While the long-term objective is to develop a system capable of reliable underwater operation, my primary focus to date has been establishing a fully functional prototype in normal conditions. I began work on the system during the Spring 2025 quarter (late April through early June) and completed the initial design and achieved some basic movement. I am currently completing a summer internship (June–September) and plan to resume development in my final quarter, from September through December.
<br>

## Demo
<center><iframe width="818" height="779" src="https://www.youtube.com/embed/73dWy-ku6m4" title="CPDR Basic Move" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

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
<center><img src="{{ site.url }}{{ site.baseurl }}/media/motor_plate.jpg" width="700"/></center>

## Next Steps
As of 6/8/25, I have finished working on the project in the spring quarter and I will resume working on this project when I return for the fall quarter - starting with work on the necessary software.