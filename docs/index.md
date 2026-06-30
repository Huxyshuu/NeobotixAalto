---
icon: lucide/bot
---

# TwinFlow ROX-Diff AMR Documentation

Welcome to the research documentation for the **Neobotix ROX-Diff autonomous mobile robot (AMR)** used at **Aalto University** in the **TwinFlow** project.

This documentation is intended as a practical starting point for students, researchers, and project contributors who need to understand the robot, prepare a workstation, run basic checks, and contribute repeatable experiments.

!!! note "Scope"

    These pages are a local research documentation. They do **not** replace the Neobotix hardware manual or other official documentation.

## What is documented here?

<div class="grid cards" markdown>

-   :material-robot-industrial: **Robot overview**

    High-level description of the ROX-Diff platform, its differential-drive configuration, and its role in intralogistics research.

-   :material-console-line: **Basic setup**

    Publicly available ROS 2 and simulation setup notes based on Neobotix documentation, plus **Aalto-specific** setup details.

-   :material-flask-outline: **Research workflows**

    Suggested structure for experiments, logging, data collection, and repeatable development.

-   :material-shield-check: **Project documentation template**

    Template for adding new projects into the documentation to allow people of the future to work on them better. 

</div>

## Platform at a glance

| Item | ROX-Diff value |
|---|---|
| Robot | Neobotix ROX-Diff AMR |
| Drive / mobility | Central differential drive; not omnidirectional |
| Minimum dimensions | 740 × 680 × 330 mm `(L × W × H)` |
| Payload | Up to 300 kg |
| Speed | Up to 1.5 m/s |
| Uptime | Depends on selected battery |
| Safety sensors | 2 × safety laser scanners with 360° field of view |
| Battery options | AGM, 48 V, 26–78 Ah, cost-efficient; or LiFePO4, 48 V, 21–63 Ah, rapid-charging capable |
| Safety controller | SICK Flexi Soft EFI-pro, programmable and extendable |
| Options | Charging station, wireless emergency stop, IOBoard, and other project-specific options |
| Arm integration | Supported |
| Main middleware | ROS 2 / Neobotix ROX stack |
| Project context | TwinFlow, Aalto University |
| Local status | Fill in local robot ID, lab location, maintainers, and network details |

!!! note "More detailed information and specifications"
    [ROX Data Sheet](https://www.neobotix-robots.com/fileadmin/images/downloads/Datenbl%C3%A4tter/Data-Sheet_ROX.pdf)
    
    [ROX Operating Manual and general instructions](https://neobotix-docs.de/hardware/en/ROX.pdf)

<!--!!! warning "Do not publish sensitive local details"

    Keep internal access credentials, Wi-Fi passwords, VPN details, and lab-specific safety procedures in protected internal documentation unless the site is private.-->

## Recommended first steps

- [ ] Read the Neobotix hardware and ROS documentation delivered with the robot.
- [ ] Confirm that you have completed the local Aalto lab induction or project onboarding.
- [ ] Identify the robot maintainer and emergency contact.
- [ ] Check the current ROS 2 distribution and middleware used on the robot.
- [ ] Run the basic connection test from the client PC.
- [ ] Record any local deviations from the public Neobotix setup.

## System concept

``` mermaid
graph LR
  A[Researcher / Client PC] -->|ROS 2 middleware| B[ROX-Diff On-board PC]
  B --> C[Drive base]
  B --> D[Safety scanner / sensors]
  B --> E[Battery and relay board]
  B --> F[Navigation and mapping]
  F --> G[TwinFlow experiments]
  G --> H[Data, logs, digital twin integration]
```

## Useful public references

- [Neobotix ROX-Diff product page](https://www.neobotix-robots.com/products/mobile-robots/mobile-robot-rox/rox-diff)
- [Neobotix ROX GitHub repository](https://github.com/neobotix/rox)
- [Neobotix ROS 2 documentation](https://neobotix-docs.de/ros/platform/index.html)
- [TwinFlow project overview](https://www.twinflow.fi/home/about-twinflow)
- [Aalto TwinFlow news article](https://www.aalto.fi/en/news/the-physical-and-digital-worlds-of-production-and-internal-logistics-meet-in-a-multidisciplinary)

## Documentation status

!!! info "Living document"

    This documentation should be updated whenever the robot configuration changes, new packages are added, maps are updated, experiments are run, or safety instructions are revised.

Go next: [Basic setup](setup.md).
