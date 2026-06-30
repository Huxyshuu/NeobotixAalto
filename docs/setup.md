---
icon: lucide/settings
---

# Basic setup

This page summarizes the publicly available setup path for the Neobotix ROX platform and leaves clear placeholders for Aalto-specific configuration.

!!! warning "Verify against the delivered robot"

    Neobotix robots may be delivered with project-specific hardware, network, ROS distribution, middleware, scanner type, or firmware. Always compare this page with the inspection document and the actual robot configuration before operating the robot.

## Setup modes

=== "Real robot"

    Use this mode when connecting to the physical ROX-Diff AMR in the lab.

    Typical tasks:

    - connect the client PC to the same permitted robot network;
    - match the ROS 2 distribution and middleware configuration;
    - start or verify robot bringup;
    - check topics, transforms, diagnostics, battery, and safety state.

=== "Simulation"

    Use this mode for development before testing on the physical robot.

    Typical tasks:

    - install the ROX simulation packages;
    - launch the ROX model in modern Gazebo;
    - test navigation, visualization, and experiment code safely.

=== "Documentation only"

    Use this mode when editing these pages or reviewing procedures without connecting to the robot.

## Minimum information to collect locally

Create a private internal note or protected page with the following values:

| Field | Value |
|---|---|
| Robot name / asset ID | `TODO` |
| Lab location | `TODO` |
| Maintainer | `TODO` |
| Emergency contact | `TODO` |
| Robot ROS 2 distro | `TODO` |
| Client PC ROS 2 distro | `TODO` |
| RMW implementation | `TODO` |
| ROS domain ID | `TODO` |
| Robot network | `TODO - keep private if sensitive` |
| Main workspace path | `TODO` |
| Maps directory | `TODO` |
| Log directory | `TODO` |

## Client PC workspace

A basic client workspace follows the standard ROS 2 colcon structure.

``` bash title="Create a workspace"
mkdir -p ~/rox_ws/src
cd ~/rox_ws/src
```

Clone the public Neobotix ROX package into the workspace. Use the branch that matches the ROS 2 distribution used by the robot or the simulation environment.

``` bash title="Clone the ROX repository"
git clone --branch $ROS_DISTRO https://github.com/neobotix/rox.git
```

For real robot communication, also include the message and service packages if your workflow uses Neobotix-specific interfaces.

``` bash title="Optional Neobotix interfaces"
git clone https://github.com/neobotix/neo_msgs2.git
git clone https://github.com/neobotix/neo_srvs2.git
```

Then build and source the workspace.

``` bash title="Build and source"
cd ~/rox_ws
rosdep update
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
source install/setup.bash
```

??? tip "Make sourcing persistent"

    Add the workspace to your shell startup file only after you are sure it builds correctly.

    ``` bash
    echo "source ~/rox_ws/install/setup.bash" >> ~/.bashrc
    ```

## ROS middleware and domain

The robot PC and client PC must use compatible ROS 2 middleware settings. Public Neobotix documentation recommends checking the delivered configuration and ensuring the robot and client use the same RMW implementation.

``` bash title="Example CycloneDDS setting"
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```

Use a ROS domain ID only when needed to isolate robots or experiments on a shared network.

``` bash title="Example ROS domain ID"
export ROS_DOMAIN_ID=0
```

!!! note

    Keep the domain ID and middleware configuration consistent across the robot PC, client PC, and any experiment machines that need to communicate.

## Real robot bringup

Many delivered robots start the required ROS 2 drivers automatically. If manual bringup is needed, use the launch files available in the installed ROX package.

``` bash title="Check available launch files"
ros2 pkg prefix rox_bringup
ros2 launch rox_bringup --show-args bringup.launch.py
```

A typical ROX-Diff bringup command should use the `diff` platform type. Verify the exact launch filename on the robot, because public examples may differ slightly between ROS distributions and package versions.

``` bash title="Example ROX-Diff bringup"
ros2 launch rox_bringup bringup.launch.py rox_type:=diff
```

!!! warning "Robot may not move until enabled"

    For ROX platforms, check key switch state, LEDs, emergency-stop state, safety scanner state, and local lab procedure before attempting motion.

## Connection test

Once the robot and client PC are on the correct network and the workspace is sourced, list the ROS 2 topics.

``` bash title="List topics"
ros2 topic list
```

Expected ROX-related topics may include items such as:

``` text
/battery_state
/cmd_vel
/diagnostics
/emergency_stop_state
/joint_states
/odom
/robot_description
/safety_state
/scan
/tf
/tf_static
```

## Visualization

Start RViz from the client PC to inspect transforms, scans, odometry, and robot state.

``` bash title="ROX RViz"
ros2 launch rox_rviz rox_rviz_launch.py
```

## Simulation setup

For simulation-first development, use the Neobotix simulation setup path and modern Gazebo where supported.

``` bash title="ROX simulation setup - example"
git clone --branch noble https://github.com/neobotix/robot-setup-tool.git
cd robot-setup-tool/package-setup
./setup-rox-simulation.sh
```

Launch the ROX simulation and set the platform type to `diff` when the launch arguments support it.

``` bash title="Launch ROX simulation"
ros2 launch rox_bringup bringup_sim_launch.py rox_type:=diff
```

For Humble or Iron workspaces, you may need to define the Gazebo resource path manually.

``` bash title="Gazebo resource path example"
export GZ_SIM_RESOURCE_PATH=~/rox_ws/src/rox:~/rox_ws/src/neo_gz_worlds/models/
```

## Public setup references

- [Neobotix ROS 2 installation](https://neobotix-docs.de/ros/ros2/installation.html)
- [Starting with ROS 2 on the Robot](https://neobotix-docs.de/ros/ros2/starting_with_ROS.html)
- [Starting with ROS 2 on Modern Gazebo](https://neobotix-docs.de/ros/ros2/simulation_modern.html)
- [Neobotix ROX repository](https://github.com/neobotix/rox)

## Troubleshooting checklist

- [ ] Is the robot powered, charged, and out of emergency stop?
- [ ] Is the key switch / enable procedure completed according to the lab rules?
- [ ] Are the robot PC and client PC on the correct network?
- [ ] Is the same `RMW_IMPLEMENTATION` used on both machines?
- [ ] Is the same `ROS_DOMAIN_ID` used on both machines?
- [ ] Is the client workspace sourced?
- [ ] Do `/tf`, `/odom`, `/scan`, `/battery_state`, and `/safety_state` publish?
- [ ] Are all people and obstacles outside the test area before motion?
