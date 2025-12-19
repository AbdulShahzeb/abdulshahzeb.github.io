---
layout: post
title: UR10e 3D Printer
order: 2
description: Real-time control system for robotic additive manufacturing using a UR10e integrated with ROS 2.
skills:
  - ROS 2
  - Additive Manufacturing
  - Real-time Control
  - Collaborative Robots

main-image: /ros-3d-printer-ur.jpg

---
# Overview
The control system employs a modular, event-driven architecture consisting of four primary layers: G-code interpretation, trajectory planning, robot control, and hardware interface.

{% include image-gallery.html images="software_stack.png" height="480" %}

---
The system architecture prioritises deterministic communication and minimal latency through several design principles:

- **Asynchronous Processing**: Commands are processed in parallel across nodes to prevent blocking operations
- **Direct Hardware Communication**: Micro-ROS enables native ROS 2 communication with the microcontroller
- **Predictive Control**: Motion and extrusion speeds are calculated at every step using G-Code instructions to ensure robot and extruder synchronisation
- **Real-time Feedback**: Continuous joint state monitoring at 500 Hz ensures accurate positioning and movement completion detection

---
## System Demonstration
{% include youtube-video.html id="WAxypnQUJU0" autoplay = "true" width= "720px" %}

---
# Results

---
## Benchy

{% include image-gallery.html images="benchy.jpg" height="480" %}

UR10e Printer (left) vs Bambu Lab X1 Carbon (right)

---
## Vase Mode

{% include image-gallery.html images="vase.jpg" height="480" %}

---
## Extra-Large Prints (exceeds print bed dimensions)

{% include image-gallery.html images="xl.jpg" height="480" %}

---
# Code Repository

[GitHub](https://github.com/AbdulShahzeb/ros-3d-printer-ur)
