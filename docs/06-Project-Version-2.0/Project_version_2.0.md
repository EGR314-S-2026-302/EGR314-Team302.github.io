---
title: Project Version 2.0
tags:
- EGR314
- Project Version 2.0
---

# Project Version 2.0

If the team were to build a second version of the R6 Recon Amphibot, there are several areas where the hardware, software, and overall system design could be meaningfully improved. This page outlines what we would change, why those changes matter, and how they would make the system more reliable, functional, and easier to demonstrate.

## Hardware Improvements

**Wireless Communication Board (Mihir)**

The most impactful hardware change on the ESP32 board would be adding a dedicated power rail for the OV5640 camera module. Currently the camera shares the main 3.3V rail with the ESP32 and all other peripherals. Isolating the camera onto its own LDO regulator would reduce noise on the ESP32 power rail and eliminate the risk of brownouts during frame capture. We would also replace the Micro USB connector with USB-C, which is more durable for repeated demo handling and more compatible with modern laptops. The antenna keepout zone compliance would also be improved to follow Espressif layout guidelines more strictly, which would improve WiFi range and reliability.

**Sensor and HMI Board (Lakshanand)**

The OLED display in V1 was small and difficult to read from a distance during the Innovation Showcase. In V2 we would upgrade to a larger display, either a bigger OLED or a small TFT LCD, so visitors and operators can read the hazard score and telemetry without needing to be right next to the device. We would also add a buzzer for audio feedback on fault conditions so the emergency stop and connection loss events are immediately noticeable without looking at the display.

**Actuator Board (Raunak)**

In V2.0 the actuator board would undergo several targeted improvements based on issues encountered during V1 assembly and integration. The **team communication header footprints** were undersized in V1, requiring jumper wires to connect to the other subsystem boards — in V2.0 these would be corrected to match the physical connectors used across the team, allowing direct and clean connections. The **L7806ABD2T 6V voltage regulator footprint** sourced from DigiKey was also incorrect and required rework during assembly; going forward, all component footprints would be manually verified against manufacturer datasheets before fabrication. The most significant functional improvement would be extending the **UART communication protocol** to support variable speed commands, allowing the HMI to dynamically adjust motor speed rather than operating at a fixed duty cycle. Finally, the board would be redesigned around a **four-motor architecture**, adding two additional **IFX9201SGAUMA1** H-bridge drivers to cover all four of the Amphibot's motors — two drive wheels and two propellers — on a single PCB, eliminating the need to split actuation responsibility across multiple boards.

**Chassis and Mechanical Design**

The 3D printed chassis in V1 was an open display model rather than a functional enclosure. In V2 we would design a proper sealed chassis with a removable top panel for easy access to the PCBs. The wheel design would be updated to use rubber tires instead of printed wheels for better traction on wet surfaces. The flip-out fin mechanism would be redesigned with a proper servo-driven deployment system rather than a manual one, making water entry and exit more controlled and repeatable.

## Software Improvements

**Camera Streaming**

The biggest software gap in V1 was that camera streaming was implemented but not demonstrated on the final hardware. In V2 the first priority would be compiling a custom MicroPython firmware build with esp32-camera support enabled and verifying the full end-to-end streaming pipeline on the actual PCB before the showcase. The camera pin mapping would be verified against the schematic and the MicroPython camera library simultaneously during the design phase rather than after board assembly.

**Protocol Design**

The UART protocol would be updated in V2 to include a sequence number field in every packet. This would allow each board to detect dropped or out-of-order packets and request retransmission when needed. Currently the protocol has no way to detect a missing packet other than a timeout, which makes diagnosing communication failures difficult. Adding sequence numbers would significantly improve debuggability.

We would also add a dedicated acknowledgement timeout and retry mechanism so that if a board does not receive an ACK within a defined window it automatically retransmits the packet up to three times before flagging an error. This would make the daisy chain more robust under noisy conditions.

**Debuggability**

In V1 debugging required connecting a laptop via USB serial to each board individually. In V2 we would add a JTAG debug header to the ESP32 board and expose SWD debug pins on both PIC boards so all three subsystems can be debugged with proper hardware debuggers without disconnecting them from the daisy chain. We would also add a dedicated debug UART channel on each board that outputs human-readable status messages independently of the daisy-chain UART, so the inter-board protocol is not disrupted during debugging sessions.

**Web Dashboard**

The V1 web dashboard was a basic MQTT subscriber. In V2 we would build a proper dashboard with a live telemetry chart showing sensor readings over time, a connection status indicator, motor speed control sliders, and a hazard score gauge. This would make the system significantly more impressive during demos and easier to use for non-technical operators.

## System Reliability

The biggest reliability concern in V1 was the shared power rail between the ESP32 and the camera module. This would be addressed in V2 with the dedicated camera power rail described above. We would also add onboard TVS diodes on all UART signal lines to protect against electrostatic discharge during cable connection and disconnection in a busy lab or showcase environment.

Battery life was another concern in V1. In V2 we would add a fuel gauge IC to the shared battery rail so the web dashboard can display remaining battery percentage in real time, giving operators advance warning before the system shuts down unexpectedly during a demo.

## Summary

Version 2.0 of the R6 Recon Amphibot would address the key gaps identified during V1 development and demonstration. The camera streaming feature would be fully verified on hardware. The chassis would become a proper functional enclosure. The protocol would gain sequence numbers and retry logic for improved reliability. All three boards would have proper hardware debug interfaces. And the web dashboard would become a genuinely useful operator tool rather than a basic telemetry display. Together these changes would transform the Amphibot from a functional prototype into a reliable and demonstrable reconnaissance platform.
