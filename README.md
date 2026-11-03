# manipulator_description

ROS 2 description package for a six-joint robot arm: URDF, STL meshes and an RViz2 display launch.

## Overview

This repository contains a ROS 2 (`ament_cmake`) package named `manipulator` that models a robot arm in URDF (robot name `six_dof_arm`) with STL meshes and displays it in RViz2. The URDF defines six revolute joints (`joint1`–`joint6`) on a fixed base link. The original README noted that the arm was driven by Faulhaber motors under position and velocity control; that control code is not part of this repository.

## Repository layout

- `manipulator/` – the ROS 2 package
  - `urdf/manipulator.urdf` – robot model (links, joints, joint limits, mesh references)
  - `meshes/` – STL meshes for the links
  - `launch/display.launch.py` – starts `robot_state_publisher`, `joint_state_publisher_gui` (or `joint_state_publisher` with `gui:=false`) and RViz2
  - `rviz/urdf.rviz` – RViz2 configuration (fixed frame `base`)
  - `package.xml`, `CMakeLists.txt` – package manifest and build rules (installs `launch`, `meshes`, `rviz`, `urdf`)

## Requirements

ROS 2 with `robot_state_publisher`, `joint_state_publisher`, `joint_state_publisher_gui`, `rviz2` and `xacro`, as listed in `package.xml`.

## Usage

From a ROS 2 workspace with the `manipulator` folder under `src/`:

```bash
colcon build --packages-select manipulator
source install/setup.bash
ros2 launch manipulator display.launch.py
```

Launch arguments: `gui` (`true`/`false`, default `true`), `model` (path to the URDF) and `rvizconfig` (path to the RViz config).

## Status

2023 project (single commit, May 2023), kept as a record and no longer maintained.

## License

No license file is included (`package.xml` declares `BSD`).
