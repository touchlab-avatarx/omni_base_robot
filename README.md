# omni_based_robot

The `omni_based_robot` repository is responsible for setting up and controlling an omni-directional mobile robot. The repository includes configuration files for teleoperation, twist multiplexing, hardware interfaces, and controllers, as well as various launch files to bring up the system.

## Table of Contents
1. [Nodes/Scripts](#1-nodes-scripts)
2. [Parameters -> Config](#2-parameters---config)
3. [Library/Module Overview](#3-library-module-overview)
4. [Launch Files](#4-launch-files)
5. [Example Usage](#5-example-usage)
6. [Dependencies](#6-dependencies)

---

## 1. Nodes/Scripts

### Overview of Nodes/Scripts
The repository provides various configurations and launch files for controlling the omni-directional base, including joystick teleoperation and twist multiplexing. 

#### Key Components:
- **Joystick Teleoperation**: Allows manual control of the robot using a joystick.
- **Twist Mux**: Manages multiple twist command sources for robot control.
- **Hardware Interface**: Interfaces with the physical hardware of the robot, including motor controllers and sensors.
- **Controllers**: Configures the base controllers for velocity and state control.

## 2. Parameters -> Config

The repository provides several configuration files to tune different aspects of the robot's operation, including hardware settings, controller parameters, and joystick mappings.

### Configuration Files:

#### `omni_base_bringup/config/joy_teleop`:
- **`joy_teleop.yaml`**: Configures the joystick teleoperation settings, such as axis mappings, buttons, and scaling factors for joystick control.

#### `omni_base_bringup/config/omni_base_hardware`:
- **`omni_base_hardware.yaml`**: Specifies hardware-specific parameters for the robot base, such as motor settings and sensor details.

#### `omni_base_bringup/config/twist_mux`:
- **`joystick.yaml`**: Configures how the joystick inputs are multiplexed into twist commands for robot movement.
- **`twist_mux_locks.yaml`**: Manages locking behavior between different input devices for controlling the robot.
- **`twist_mux_topics.yaml`**: Specifies topics for twist commands from various sources.

#### `omni_base_controller_configuration/config`:
- **`joint_state_controller_extra_joints.yaml`**: Defines extra joints for the joint state controller.
- **`mobile_base_controller.yaml`**: Configures the main mobile base controller for velocity commands.
- **`mobile_base_controller_multipliers.yaml`**: Specifies multipliers for the base controller to tune velocity output.

## 3. Library/Module Overview

The repository provides a modular and scalable way to manage the omni-directional mobile robot, with a focus on integrating joystick teleoperation, hardware interfaces, and control systems for mobile bases. This includes:

- **Joystick Teleop**: Provides a YAML-based configuration system for customizing joystick inputs.
- **Twist Mux**: Merges multiple command sources into a single twist command for better control of the mobile base.
- **Hardware Interface**: Integrates the robot's physical components such as motors and sensors through ROS interfaces.
- **Controller Configuration**: Handles velocity and joint state control for the mobile base.

## 4. Launch Files

The repository contains multiple launch files that bring up various components of the omni-directional robot system. The key launch files include:

#### `omni_base_bringup/launch`:
- **`joystick_teleop.launch`**: Launches the joystick teleoperation node to control the robot with a joystick.
- **`omni_base.launch`**: Starts up the base components, including hardware drivers and controllers.
- **`omni_base_bringup.launch`**: Launches all necessary components to bring up the omni-directional robot, including teleoperation, hardware interfaces, and controllers.
- **`twist_mux.launch`**: Launches the twist mux node, which combines multiple twist command sources into a single command for the robot.

#### `omni_base_controller_configuration/launch`:
- **`default_controllers.launch`**: Brings up the default set of controllers, including velocity and joint state controllers.

### Example of Launch Command:
To bring up the entire omni-directional robot system:
```bash
ros2 launch omni_base_bringup omni_base_bringup.launch
```

## 5. Example Usage

### Bringing up the Omni-Directional Robot:
1. To launch the full robot system, including joystick teleoperation, hardware interface, and controllers:
    ```bash
    ros2 launch omni_base_bringup omni_base_bringup.launch
    ```

2. For joystick control, launch the joystick teleoperation node separately:
    ```bash
    ros2 launch omni_base_bringup joystick_teleop.launch
    ```

3. To manage multiple command inputs for robot control, start the twist mux:
    ```bash
    ros2 launch omni_base_bringup twist_mux.launch
    ```

4. To launch the default set of controllers:
    ```bash
    ros2 launch omni_base_controller_configuration default_controllers.launch
    ```

## 6. Dependencies

This package depends on various ROS2 packages and external libraries. These are defined in the `package.xml` file and should be installed before running the system.

### Core Dependencies:
- **ROS2 (Foxy or later)**: Required for launching and managing nodes.
- **Twist Mux**: For combining multiple velocity command inputs.
- **Joint State Controller**: For managing the state of the robot's joints.
- **Mobile Base Controller**: For controlling the velocity of the omni-directional base.

### Installation Steps:
1. Clone the repository:
    ```bash
    git clone <repository_url>
    ```
2. Install dependencies using `rosdep`:
    ```bash
    rosdep install --from-paths src --ignore-src -r -y
    ```
3. Build the workspace:
    ```bash
    colcon build
    ```
4. Source the workspace:
    ```bash
    source install/setup.bash
    ```
