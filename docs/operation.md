---
icon: lucide/play-circle
---

# Operating workflow

This page provides a simple operating structure for day-to-day research use of the ROX-Diff AMR.

!!! danger "Safety first"

    Do not operate the robot alone unless the local lab rules explicitly allow it. Keep the emergency stop accessible and test only in approved areas.

## Before powering the robot

- [ ] Test area is clear and approved for AMR movement.
- [ ] Emergency stop is visible and reachable.
- [ ] Battery level is sufficient for the planned work.
- [ ] Payload, trolley, or attachments are mechanically secure.
- [ ] Safety scanners and sensors are clean and unobstructed.
- [ ] The planned test has a responsible operator and observer if required.

## Startup sequence

1. Power on the robot according to the Neobotix and Aalto lab instructions.
2. Confirm that the robot is physically stable and no unexpected motion occurs.
3. Wait for the on-board PC and robot drivers to initialize.
4. Connect the client PC to the approved robot network.
5. Source the ROS 2 workspace.
6. Run the connection test.

``` bash title="Basic connection check"
source ~/rox_ws/install/setup.bash
ros2 topic list
ros2 topic echo /battery_state --once
ros2 topic echo /safety_state --once
```

## Basic health checks

| Check | Command / method | Expected result |
|---|---|---|
| Topics visible | `ros2 topic list` | ROX topics visible |
| Battery state | `ros2 topic echo /battery_state --once` | Valid battery message |
| Safety state | `ros2 topic echo /safety_state --once` | No active unsafe condition |
| Transform tree | RViz / `tf2_tools` | Frames available |
| Laser scan | RViz `/scan` | Scan visible and stable |
| Odometry | RViz `/odom` | Odometry updates during motion |

## Manual teleoperation

Use the wireless joystick or approved teleoperation interface only after the area is clear.

!!! warning

    Before pressing the deadman button or enabling motion, move the joystick axes gently and confirm that the robot does not receive unintended commands.

``` bash title="Inspect velocity commands"
ros2 topic echo /cmd_vel
```

## RViz monitoring

``` bash title="Start RViz"
ros2 launch rox_rviz rox_rviz_launch.py
```

Recommended RViz displays:

- RobotModel
- TF
- LaserScan (`/scan` or scanner-specific scan topic)
- Odometry (`/odom`)
- Map, if navigation is active
- Path and local costmap, if Nav2 is active

## Shutdown sequence

1. Stop autonomous tasks and teleoperation.
2. Confirm that `/cmd_vel` is zero.
3. Save logs, maps, and experiment notes.
4. Close RViz and user processes.
5. Shut down the robot using the approved local procedure.
6. Plug in charging equipment only according to the lab and manufacturer instructions.

## Incident notes

If the robot behaves unexpectedly, record:

- date and time;
- operator name;
- ROS distribution and git commit, if available;
- robot state and battery state;
- last command sent;
- relevant terminal logs;
- whether emergency stop or safety scanner intervention occurred.
