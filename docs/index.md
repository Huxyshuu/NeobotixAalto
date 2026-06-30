---
icon: lucide/bot
---

# TwinFlow ROX-Diff AMR Documentation

Welcome to the research documentation for the **Neobotix ROX-Diff autonomous mobile robot (AMR)** used at **Aalto University** in the **TwinFlow** project.

This documentation is intended as a practical starting point for students, researchers, and project contributors who need to understand the robot, prepare a workstation, run basic checks, and contribute repeatable experiments.

!!! note "Scope"

    These pages are a local research documentation foundation. They do **not** replace the Neobotix hardware manual, the delivered inspection document, Aalto laboratory instructions, or project-specific safety training.

## What is documented here?

<div class="grid cards" markdown>

-   :material-robot-industrial: **Robot overview**

    High-level description of the ROX-Diff platform, its differential-drive configuration, and its role in intralogistics research.

-   :material-console-line: **Basic setup**

    Publicly available ROS 2 and simulation setup notes based on Neobotix documentation, plus placeholders for Aalto-specific network details.

-   :material-shield-check: **Safe operation**

    Pre-operation checks, emergency-stop awareness, controlled test-area assumptions, and minimum safety reminders.

-   :material-flask-outline: **Research workflows**

    Suggested structure for experiments, logging, data collection, and repeatable development.

</div>

## Context: TwinFlow and Aalto research

TwinFlow focuses on improving production and intralogistics operations through data-driven, interoperable, and digital-twin-enabled approaches. Within that context, the ROX-Diff AMR can act as a physical research asset for autonomous material-flow experiments, sensing, navigation, fleet logic, and integration between operational technology and information systems.

The robot should be treated as both:

1. a **mobile robot platform** for ROS 2-based autonomy research, and
2. a **TwinFlow demonstrator asset** for studying data exchange, situational awareness, and intralogistics workflows.

## Platform at a glance

| Item | Description |
|---|---|
| Robot | Neobotix ROX-Diff AMR |
| Drive type | Central differential drive |
| Typical use | Research, development, intralogistics experiments |
| Main middleware | ROS 2 / Neobotix ROX stack |
| Project context | TwinFlow, Aalto University |
| Local status | Fill in local robot ID, lab location, maintainers, and network details |

!!! warning "Do not publish sensitive local details"

    Keep internal IP addresses, access credentials, Wi-Fi passwords, VPN details, and lab-specific safety procedures in protected internal documentation unless the site is private.

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
