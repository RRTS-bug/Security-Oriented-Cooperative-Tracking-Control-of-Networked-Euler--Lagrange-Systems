# Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler-Lagrange-Systems

**Notice 1**: *ROS Implementation for the Second Subsection of the Experiment Study on Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler--Lagrange-Systems.*

**Notice 2**: *This repository provides a runnable ROS/Gazebo experiment package for reproducing the submitted manuscript results. The full controller source code will be released after publication. This package contains precompiled ROS nodes and the required launch, configuration, model, and visualization files for review.*

## 1. Preliminary Preparation
Before running the code in this subsection, the runtime environment should be configured in advance.

### System Requirements

 -Operating System: Ubuntu 20.04
 
 -Robot Operating System: ROS Noetic
 
 -ROS Installation Type: Full Desktop Version
 
  The detailed installation tutorial for ROS Noetic can be found at:

  https://wiki.ros.org/noetic/Installation/Ubuntu

  After the installation is completed, please check whether Gazebo and RViz can be opened properly.

# 2. Running the Tracking Control

 Execute the following commands to run the tracking control code:

## 2.1 Clone the Repository and Install ROS-Control Related Dependencies

Clone the code of this repository into the home directory:
  
 ```bash
 git clone https://github.com/RRTS-bug/Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler-Lagrange-Systems.git
 ```
Install ROS-Control Related Dependencies

```bash
sudo apt update
sudo apt install ros-noetic-ros-control ros-noetic-ros-controllers ros-noetic-effort-controllers ros-noetic-gazebo-ros-control
```

## 2.2 Source the Workspace

Source the ROS Noetic environment and the workspace:

```bash
cd ~/Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler-Lagrange-Systems/code_demo_ws
touch install/.catkin
chmod +x install/_setup_util.py
chmod +x install/lib/dynamic_encryption_based_pp_cooperative_control/*
cd install/share/dynamic_encryption_based_pp_cooperative_control
ln -sf ../../lib/dynamic_encryption_based_pp_cooperative_control/dynamic_encryption_based_pp_cooperative_control_observer_tracking1
ln -sf ../../lib/dynamic_encryption_based_pp_cooperative_control/dynamic_encryption_based_pp_cooperative_control_observer_tracking2
ln -sf ../../lib/dynamic_encryption_based_pp_cooperative_control/dynamic_encryption_based_pp_cooperative_control_observer_tracking3
ln -sf ../../lib/dynamic_encryption_based_pp_cooperative_control/dynamic_encryption_based_pp_cooperative_control_observer_tracking4
ln -sf ../../lib/dynamic_encryption_based_pp_cooperative_control/dynamic_encryption_based_pp_cooperative_control_visual
```

## 2.3 Gazebo-based Physical Simulation Platform for the Two-Link Robotic Manipulator

Launch the Gazebo-based physical simulation platform for the two-link robotic manipulator:

```bash
cd ~/Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler-Lagrange-Systems/code_demo_ws
source /opt/ros/noetic/setup.bash
source install/setup.bash
export CMAKE_PREFIX_PATH=$PWD/install:$CMAKE_PREFIX_PATH
export ROS_PACKAGE_PATH=$PWD/install/share:$ROS_PACKAGE_PATH
export LD_LIBRARY_PATH=$PWD/install/lib:$LD_LIBRARY_PATH
roslaunch two_link_arm_gazebo gazebo.launch 
```
Notice 3: It should be noted that, as long as Gazebo and RViz are successfully launched, the error messages displayed in the terminal do not affect the execution of the simulation and can therefore be ignored.

## 2.4 Run the Observer_tracking Launch File
Open a new terminal and Run the observer_tracking launch file:
```bash
cd ~/Security-Oriented-Cooperative-Tracking-Control-of-Networked-Euler--Lagrange-Systems/code_demo_ws
source /opt/ros/noetic/setup.bash
source install/setup.bash
export CMAKE_PREFIX_PATH=$PWD/install:$CMAKE_PREFIX_PATH
export ROS_PACKAGE_PATH=$PWD/install/share:$ROS_PACKAGE_PATH
export LD_LIBRARY_PATH=$PWD/install/lib:$LD_LIBRARY_PATH
roslaunch dynamic_encryption_based_pp_cooperative_control observer_tracking.launch 
```

Notice 4: The control algorithm is executed for 30 s and will be automatically terminated once the 30-second simulation period is completed.
