---
icon: lucide/flask-conical
---

# Research workflows

This page defines a repeatable structure for experiments with the ROX-Diff AMR in TwinFlow-related research.

## Typical research use cases

- autonomous navigation in indoor industrial environments;
- trolley detection, docking, or attachment experiments;
- material-flow data collection;
- digital twin synchronization;
- sensor fusion and situational awareness;
- integration with factory IT/OT systems;
- fleet or task-allocation research.

## Experiment template

Use this template for each experiment or test campaign.

| Field | Description |
|---|---|
| Experiment ID | Short unique ID, e.g. `rox-diff-nav-2026-06-30-a` |
| Objective | What is being tested? |
| Operator | Person responsible for the test |
| Location | Lab / test area |
| Robot config | ROS distro, branch, commit, launch arguments |
| Sensors used | LiDAR, camera, IMU, UWB, etc. |
| Dataset / map | Map name, calibration files, bag files |
| Safety assumptions | Test boundary, observers, stop conditions |
| Success criteria | Quantitative or qualitative acceptance criteria |
| Results | Summary and link to logs |

## Suggested repository structure

``` text title="Example research repository"
rox-diff-research/
├── README.md
├── config/
│   ├── nav2/
│   ├── sensors/
│   └── experiments/
├── launch/
├── maps/
├── scripts/
├── notebooks/
├── docs/
└── data/
    ├── raw/
    ├── processed/
    └── logs/
```

## Data logging

For repeatability, log both robot data and experiment metadata.

``` bash title="Example rosbag recording"
ros2 bag record \
  /tf \
  /tf_static \
  /odom \
  /scan \
  /battery_state \
  /safety_state \
  /cmd_vel
```

!!! tip "Keep logs traceable"

    Name each bag file with the experiment ID, date, map, and operator initials. Store the matching notes file next to the bag.

## Digital twin integration points

``` mermaid
graph TD
  R[ROX-Diff AMR] --> S[Sensors and robot state]
  S --> B[ROS 2 topics / bags]
  B --> P[Processing and semantic mapping]
  P --> D[Digital twin representation]
  D --> T[TwinFlow data space / integration layer]
  T --> A[Analytics, planning, situational awareness]
```

## Minimum metadata for TwinFlow experiments

- robot ID;
- software version and git commit;
- environment or map version;
- sensor configuration;
- payload or trolley configuration;
- start and end time;
- operator and observer;
- safety events;
- deviations from the planned procedure.

## Development rules

- Keep safety-related changes separate from experimental changes.
- Use simulation before testing new control logic on the robot.
- Avoid hard-coded local IP addresses in public repositories.
- Document launch arguments and parameter files.
- Commit maps, configs, and scripts with clear names.
- Store large raw datasets outside the source repository unless the project policy allows it.
