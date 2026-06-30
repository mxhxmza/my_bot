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

Hardware: Hiwonder Ackermann Robot Car, 2D/3D LiDAR, RGB/Depth Camera

🚀 Getting Started
1. Workspace Setup
Clone this repository into your ROS2 workspace:


Bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
git clone https://github.com/[Username]/[Repository-Name].git

3. Install Dependencies
Use rosdep to install necessary dependencies:

Bash
cd ~/ros2_ws
rosdep install --from-paths src --ignore-src -r -y

5. Build the Project

Bash
colcon build --symlink-install
source install/setup.bash

💻 Usage
Phase 1: Simulation (Gazebo & RViz2)
It is highly recommended to validate any algorithmic changes in the simulation environment first.

Launch the Simulated Robot:

Bash
ros2 launch [your_package_name] [your_launch_file]
This brings up the URDF/Xacro model in Gazebo along with the simulated LiDAR and camera plugins.

Launch Navigation & Sensor Fusion (RViz2):

Bash
ros2 launch [your_package_name] [your_launch_file]
Use the RViz2 interface to set 2D Pose Estimates and Nav2 Goals to observe the robot's simulated autonomous behavior.

Phase 2: Physical Hardware Deployment
Once validated in simulation, transition to the physical Hiwonder Ackermann Robot.

Bringup the Hardware:

Bash
ros2 launch [your_package_name] [your_launch_file]

Launch the Perception & Navigation Stack:

Bash
ros2 launch [your_package_name] [your_launch_file]

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
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
