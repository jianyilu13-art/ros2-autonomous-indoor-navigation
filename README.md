# ROS2 Autonomous Indoor Navigation *(Ongoing)*

> **An ongoing robotics project that extends the NUS RB1101 Fundamentals of Robotics wall-following laboratory into a progressively more intelligent autonomous indoor navigation system.**

---

# Overview

This repository documents my journey of transforming a basic reactive mobile robot into an increasingly capable autonomous indoor robot.

The project **starts from the RB1101 Fundamentals of Robotics wall-following laboratory**, which provides the ROS 2 framework, LiDAR processing, and a basic wall-following controller.

Instead of rewriting the project from scratch, this repository incrementally extends the original architecture with more advanced perception, decision-making, mapping, and navigation capabilities.

The repository will continue to evolve as new robotics concepts are explored and implemented.

# Demo

## Demo Video

A demonstration of the robot simulation running in Gazebo with ROS 2, including robot control, sensor feedback, and autonomous navigation.
[Watch Demo Video](demos/demo_basic.mp4)

---

# Base Project

This project is **built upon the RB1101 Fundamentals of Robotics laboratory assignment**.

The original laboratory provides:

* ROS 2 workspace and package structure
* Gazebo simulation environment
* LiDAR (`LaserScan`) interface
* RANSAC-based wall extraction
* Wall orientation estimation
* Basic wall-following controller
* Robot motion interface (`cmd_vel`)

The laboratory code serves as the **foundation** of this repository.

Future improvements and extensions developed in this repository are my own work built on top of the original framework.

---

# Current Limitations

At the current stage, the robot is primarily a **reactive wall-following robot**.

### Current capabilities

* Detect walls using LiDAR
* Extract wall segments using RANSAC
* Estimate wall orientation
* Perform basic wall following
* Avoid simple obstacles

### Current limitations

The robot **cannot currently**

* build a map
* localize itself
* remember previously visited locations
* plan a route
* navigate toward a destination
* understand rooms or doorways
* recognize objects
* perform semantic reasoning

The controller only reacts to the current LiDAR observation and has no memory or understanding of the global environment.

---

# Development Roadmap

The long-term goal is to gradually transform the system into an intelligent indoor navigation framework.

## Level 1 — Reactive Navigation

Status: 🚧 In Progress

Possible improvements:

* Finite State Machine (FSM)
* Recovery behaviour
* Adaptive speed control
* PID controller
* Improved corner handling

---

## Level 2 — Environment Understanding

Status: ☐ Planned

Possible improvements:

* Corridor detection
* Room entrance detection
* Corner classification
* Local topology extraction

---

## Level 3 — Mapping and Memory

Status: ☐ Planned

Possible improvements:

* Topological mapping
* Local memory
* Landmark management
* Graph representation

---

## Level 4 — Navigation

Status: ☐ Planned

Possible improvements:

* SLAM integration
* Localization
* Navigation2
* A* path planning
* Goal-directed navigation

---

## Level 5 — Intelligent Autonomous Navigation

Status: ☐ Planned

Possible improvements:

- User-defined target destination
- Navigate to a specified location
- Object-aware navigation
- Dynamic obstacle avoidance
- Task-oriented navigation

---

# Current Sprint

Status: 🚧 Ongoing

## Objective

Establish a reliable baseline controller from the original RB1101 wall-following implementation, then extend it with improved decision-making strategies for autonomous maze navigation.

---

## Planned Features

* Fix and validate the original wall-following controller behaviour
* Implement alternative controller versions for comparison:
  - FSM-based behaviour control
  - Improved corner handling
  - PID-based distance regulation
* Evaluate performance in Gazebo spiral maze simulation

---

## Progress

* [x] Import RB1101 baseline project
* [x] Analyze existing wall-following controller
* [ ] Fix baseline implementation issues
* [ ] Create FSM-based controller version
* [ ] Implement improved corner handling
* [ ] Implement PID controller version
* [ ] Test and compare different approaches
* [ ] Document results

---

# Installation

This project currently follows the RB1101 ROS 2 workspace structure.

## 1. Build the workspace

```bash
cd ~/ros2-autonomous-indoor-navigation
colcon build --symlink-install
```

## 2. Grant execution permission

```bash
chmod +x *.sh
```

Only required once for each machine.

---

# Running the Simulation

Launch Gazebo

```bash
./gz_heading.sh
```

In another terminal

```bash
./wall_following.sh
```

For the physical robot, remember to set

```python
is_simulation = False
```

inside

```text
src/rb1101/wall_following.py
```

before deployment.

---

# Original RB1101 Laboratory Objectives

The original laboratory required implementing:

* Wall-following with heading correction
* Pledge algorithm
* Escape behaviour for enclosed environments

These objectives formed the starting point of this repository.

---

# Repository Structure

```text
src/
    ROS2 source packages

docs/
    Design notes

images/
    Figures

videos/
    Demonstration videos

README.md

LICENSE
```

---

# Future Vision

The ultimate objective of this repository is to bridge the gap between simple reactive navigation and high-level semantic robotics.

The planned progression is

Reactive Wall Following

↓

Environment Understanding

↓

Mapping

↓

Navigation

↓

Semantic Scene Representation

↓

Autonomous Task-Level Navigation

The repository will continue to be updated as new robotics algorithms and research ideas are implemented.

---

# References

* RB1101 Fundamentals of Robotics Laboratory Materials
* Advanced Wall Following (RANSAC implementation): https://github.com/creminem94/Advanced-Wall-Following
