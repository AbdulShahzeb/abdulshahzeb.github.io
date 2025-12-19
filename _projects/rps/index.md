---
layout: post
title: Repeatable Pickup System
order: 3
description: A ROS 2 project designed to perform a robust and repeatable pick-and-place task using a UR5e arm and an overhead RealSense camera. The system dynamically identifies an object's position, generates a multi-step motion plan, and executes the sequence with gripper actions. 
skills:
  - ROS 2
  - Collaborative Robots
  - Control Systems

main-image: /rps.jpg

---
## Overview
This system is built around a modular architecture of communicating ROS 2 nodes:

- **Object Detection**: A vision node processes the overhead camera feed to detect the target object and continuously publishes its 2D pose.
- **User-Triggered Operation**: A keyboard input node listens for user commands to start the sequence, ensuring the robot only moves on demand.
- **Dynamic Sequence Generation**: Upon receiving an "execute" signal, the central pick-and-place node collects several fresh poses from the vision node, averages them for accuracy, and dynamically generates a complete, multi-step trajectory.
- **State-Driven Execution**: The pick-and-place node operates as a formal state machine (`IDLE`, `MOVING_ROBOT`, etc.), ensuring safe and predictable behavior. It only accepts new tasks when it is idle.
- **Robot Control**: A UR control node translates the desired Cartesian poses from the sequence into joint-space commands for the robot arm and provides continuous feedback on its movement status.
- **Gripper Integration**: The sequence includes integrated *Contactile* gripper commands (`Open`, `Grip`, `Release`), which are published at the appropriate points in the trajectory.


### System Demonstration
{% include youtube-video.html id="1wjH_KKCkKA" autoplay = "true" width= "720px" %}
