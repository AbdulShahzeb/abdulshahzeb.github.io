---
layout: post
title: Playing Tic-Tac-Toe vs. UR5e
order: 1
description: Play Tic-Tac-Toe against a UR5e robotic arm that uses CV to detect your moves and reinforcement learning AI to plan its strategy.
skills:
  - ROS 2
  - Computer Vision
  - End-Effector Design
  - Machine Learning

main-image: /tictactoe.png

---
# Overview
This project provides a complete, open-source toolkit for playing tic-tac-toe with a UR5e robotic arm. The system demonstrates:

- **Vision-based perception** using ArUco marker detection and colour segmentation
- **Motion planning and control** through MoveIt integration with custom trajectory execution
- **AI decision-making** via a trained MENACE (Matchbox Educable Noughts and Crosses Engine) agent
- **Closed-loop operation** with continuous visual feedback and adaptive gameplay
- **Custom hardware integration** including a dual-marker end-effector and servo control

---
## Robot Functionality
The UR5e manipulator, equipped with a custom dual-marker end-effector, autonomously plays tic-tac-toe by reacting to either physically drawn moves on a grid or mouse-selected moves on the UI. The system:

1. **Perceives the game state** using an overhead RealSense camera to detect ArUco markers and colour-coded symbols
2. **Plans moves** using a trained reinforcement learning agent
3. **Executes drawing motions** with MoveIt-planned Cartesian trajectories while avoiding collisions
4. **Monitors gameplay** through continuous vision feedback, detecting human moves and verifying robot actions
5. **Adapts in real-time** to changing board states, maintaining closed-loop control throughout gameplay

---
## System Demonstration

{% include youtube-video.html id="hXMSvpA56x8" autoplay = "true" width= "720px" %}

---
# Technical Components

---
## Computer Vision

- Computes the grid's center position and orientation using camera intrinsics and marker geometry
- Uses HSV colour space thresholding to detect blue markers (X) and red markers (O) within adaptive circular regions
- Enables fully autonomous human move detection in *Vision Mode*, eliminating the need for manual input

{% include image-gallery.html images="cv.png" height="480" %}

---
## End-Effector
The custom end-effector design prioritises simplicity in construction, featuring an entirely FDM 3D-printed servo housing that toggles between two pen holders to draw X's and O's.

{% include image-gallery.html images="end_effector.jpg" height="480" %}

---
## System Visualisation
The system uses RViz as the primary visualisation tool, providing real-time feedback on robot state, perception data, and coordinate frames:

- Robot Model & MoveIt Trajectory Planning
- ArUco Marker and Cell State Overlays
- TF Trees

{% include image-gallery.html images="rviz.png" height="480" %}

---
## Closed-Loop Operation
The system implements closed-loop control through continuous vision-based state monitoring and adaptive decision-making:

- Vision-Based State Feedback
- Adaptive Game Flow

---
# Code Repository
[GitHub](https://github.com/AbdulShahzeb/ros-tictactoe-ur)
