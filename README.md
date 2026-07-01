🚗 Autonomous Navigation System for Hiwonder Ackermann Robot (ROS2)

📖 Overview
This repository contains the source code and configuration files for a full-scale autonomous navigation system deployed on a Hiwonder Ackermann Robot Car. Built on the ROS2 framework, the system integrates LiDAR and camera inputs through advanced perception pipelines to achieve robust autonomous navigation.

To accelerate the development cycle and ensure safety, the project heavily utilizes simulation. A complete robot model (URDF/Xacro) is simulated in Gazebo and RViz2, allowing for live sensor fusion and navigation algorithm validation prior to physical hardware deployment.

✨ Key Features
Full-Scale Autonomous Navigation: End-to-end navigation stack deployment on an Ackermann steering platform.

Multimodal Sensor Fusion: Real-time integration of LiDAR and Camera perception pipelines to map, localize, and navigate complex environments.

High-Fidelity Simulation: Comprehensive URDF/Xacro modeling for accurate kinematic and dynamic representation of the Hiwonder robot in Gazebo.

Accelerated Testing Workflow: Validate SLAM, path planning, and obstacle avoidance algorithms in RViz2 and Gazebo before executing on physical hardware, drastically reducing physical testing time and potential hardware damage.

🛠️ Tech Stack & Prerequisites
OS: Ubuntu 22.04 (Recommended)

Framework: ROS2 (Humble)

Simulation: Gazebo, RViz2

Robot Modeling: URDF, Xacro


🚀 Getting Started
1. Workspace Setup
Clone this repository into your ROS2 workspace:

Bash
mkdir -p ~/ros2_ws/src

cd ~/ros2_ws/src

git clone https://github.com/[Username]/[Repository-Name].git


2. Install Dependencies
Use rosdep to install necessary dependencies:

Bash

cd ~/ros2_ws

rosdep install --from-paths src --ignore-src -r -y


3. Build the Project

Bash

colcon build --symlink-install

source install/setup.bash


💻 Usage
Simulation (Gazebo & RViz2)
It is highly recommended to validate any algorithmic changes in the simulation environment first.

  ->Launch Gazebo:
  
    Bash
  
    ros2 launch my_bot launch_sim.launch.py use_sim_time:=true
  
    This brings up the URDF/Xacro model in Gazebo along with the simulated LiDAR and camera plugins.
  
  ->Launch RViz2:
  
    Bash
  
    rviz2
  
  ->Launch SLAM Toolbox:
  
    Bash
  
    ros2 launch slam_toolbox online_async_launch.py params_file:=src/articubot_one/config/mapper_params_online_async.yaml use_sim_time:=true
  
  ->Launch twist_mux:
  
    Bash
  
    ros2 run twist_mux twist_mux --ros-args --params-file ./src/my_bot/config/twist_mux.yaml -r cmd_vel_out:=diff_cont/cmd_vel_unstamped

  ->Launch keyboard for manual control:

    Bash

    ros2 run teleop_twist_keyboard teleop_twist_keyboard
  
  ->Launch Nav2:
  
    Bash
  
    ros2 launch nav2_bringup navigation_launch.py params_file:=src/my_bot/config/nav2_params.yaml use_sim_time:=true
  
  Use the RViz2 interface to set 2D Nav2 Goals to observe the robot's simulated autonomous behavior.
  -> The robot will take the shortest path to navigate to its goal!!!


📂 Repository Structure
Plaintext
├── config/             # Navigation and controller YAML files
├── description/        # URDF and Xacro files for the robot model
├── launch/             # ROS2 launch files for sim and real-world deployment
├── maps/               # Generated maps for localization
├── src/                # Custom perception and navigation C++/Python nodes
├── rviz/               # RViz2 configuration files
└── README.md

🎥 Media / Demonstrations



🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to contribute!!!

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
