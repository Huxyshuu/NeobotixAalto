---
icon: lucide/cpu
---

# Specifications and configurations

This page provides the hardware, software specifications and networking configurations for ROX-Diff AMR.

!!! info "Last updated"

    Updated on **July 1, 2026** by Hugo

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
| Battery options | AGM, 48 V, 26–78 Ah, cost-efficient |
| Safety controller | SICK Flexi Soft EFI-pro, programmable and extendable |
| Arm integration | Supported |
| Main middleware | ROS 2 / Neobotix ROX stack |

!!! note "More detailed information and specifications"
    [ROX Data Sheet](https://www.neobotix-robots.com/fileadmin/images/downloads/Datenbl%C3%A4tter/Data-Sheet_ROX.pdf)
    
    [ROX Operating Manual and general instructions](https://neobotix-docs.de/hardware/en/ROX.pdf)

## Hardware

| Item | Information |
|---|---|
| On-board Computer | M1992VFS-7440 (i7) |
| RelayBoard version (HW/SW) | V3.0.2 / 1.07 |
| Battery charger | MeanWell NPB-360-48AD1 |
| Charging connector | QuickLock size 20, 2 pins |

## Software

| Item | Information |
|---|---|
| Operating System | Ubuntu Linux 24.04 LTS - 64 bit |
| Control Software | ROS 2 Jazzy |
| RMW Implementation | rmw_cyclonedds |
| ROS Domain ID | 0 |


## Networking

| Item | Information |
|---|---|
| Connected Wi-Fi network | DTLabOpen |
| Static IP Address (WLAN) | 192.168.0.50 |

## Internal IP Addresses
| Item | Information |
|---|---|
| Computer | 192.168.1.10 |
| FlexiSoft | 192.168.1.20 |
| Scanner 1 | 192.168.1.30 |
| Scanner 2 | 192.168.1.31 |
| RelayBoard | 192.168.1.80 |

## Other

| Item | Information |
|---|---|
| Serial number | 20260430-01 |
| CAD File | ROX-Diff Aalto V1.02.03.iam |
| Electrical Circuit Diagram Platform | ESP-ROX-Platform_V1-1-0 |
| Sick Safety Network Number | 4946_0124_3982 |
