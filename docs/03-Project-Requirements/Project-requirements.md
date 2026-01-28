---
title: Project Requirements
tags:
- EGR314
- Team XPED
---

# Project Requirements

The purpose of this section is to translate the features of the selected design concept into clear, measurable engineering requirements. These requirements define the minimum functionality needed for the system to be considered successful, as well as target goals and optional stretch objectives. Together, they guide subsystem design, team responsibility, and verification throughout the project.

---

## Team-Level Project Requirements

This table defines the overall system requirements for the exploration device. Each requirement is tied directly to a feature from the selected design concept and includes a minimum threshold, a target goal, and whether it is considered a stretch requirement.

| Requirement Description | Minimum Threshold | Target Goal | Feature Addressed | Stretch (Yes/No) |
|------------------------|------------------|-------------|------------------|------------------|
| The system must support wireless communication with the user | One-way Wi-Fi communication | Two-way Wi-Fi using MQTT | Wireless communication | No |
| The system must provide live video feedback | Video stream available | Video latency under 500 ms | FPV camera | No |
| The robot must be able to move forward and backward | Basic bidirectional motion | Smooth, speed-controlled motion | Wheeled propulsion | No |
| The system must support an emergency stop | Stop within 1 second | Stop within 250 ms | Emergency stop | No |
| The system must calculate a hazard score from sensor data | Safe / unsafe indication | Scaled hazard score (0–100) | Hazard scoring algorithm | Yes |
| The system must display information locally | Text-only display | Text with simple graphics | OLED HMI | No |
| The system must report orientation and motion | IMU detected | Stable IMU data ≥ 50 Hz | IMU sensor | No |
| The system must operate on a replaceable battery | ≥ 5 minutes runtime | ≥ 15 minutes runtime | Replaceable battery pack | No |
| The system must protect itself from overheating | Warning issued | Automatic thermal shutdown | Thermal protection | Yes |
| The system must use modular UART communication | UART link established | CRC-checked UART communication | UART daisy chain | No |
| The system must reset quickly for repeated demos | Manual reset | Reset time under 10 seconds | Fast reset sequence | No |

---

## Module-Level Requirements

Each subsystem has its own set of requirements that support the overall system functionality. These module-level requirements ensure that each team member is responsible for a critical portion of the system.

---

### Module Requirements — Wireless Communication (ESP32)  
**Teammate A: Mihir Patel**

| Requirement Description | Minimum Threshold | Target Goal | Stretch (Yes/No) |
|------------------------|------------------|-------------|------------------|
| SMD 3.3 V switching regulator | Output ≥ 3.2 V | Stable 3.3 V output | No |
| ESP32 microcontroller | Boots successfully | Runs Wi-Fi and MQTT | No |
| Wireless communication | One-way data transfer | Two-way MQTT messaging | No |
| UART communication with system bus | Basic TX/RX | Structured packets with CRC | No |
| Video data handling | Video stream present | Stable low-latency stream | Yes |
| Connection loss handling | Detect disconnection | Trigger safe-stop behavior | Yes |

---

### Module Requirements — Sensor & HMI (PIC)  
**Teammate B: Lakshanand Sugumar**

| Requirement Description | Minimum Threshold | Target Goal | Stretch (Yes/No) |
|------------------------|------------------|-------------|------------------|
| SMD PIC microcontroller | Main loop runs | Interrupt-driven firmware | No |
| Serial sensor interface | IMU detected | Stable IMU data ≥ 50 Hz | No |
| OLED display | Text output visible | Text with simple graphics | No |
| Pushbutton input | Button press detected | Debounced, interrupt-based | No |
| Hazard score output | Binary indicator | Scaled hazard score | Yes |
| UART communication | Basic messaging | Structured sensor messages | No |

---

### Module Requirements — Actuator Control (PIC)  
**Teammate C: Raunak Singh**

| Requirement Description | Minimum Threshold | Target Goal | Stretch (Yes/No) |
|------------------------|------------------|-------------|------------------|
| Motor control | Forward/backward motion | Speed-controlled driving | No |
| Motor driver interface | Driver responds | PWM with current limiting | No |
| Emergency stop response | Stop within 1 second | Stop within 250 ms | No |
| Overcurrent protection | Warning only | Automatic motor shutdown | Yes |
| Thermal protection | Warning issued | Automatic shutdown | Yes |
| UART status reporting | Basic motor state | Motor telemetry reporting | No |

---

## Requirement Ownership by Team Member

The table below assigns each major requirement area to the responsible team member and subsystem.

| Requirement Area | Team Member | Subsystem |
|------------------|-------------|-----------|
| Wireless communication and video streaming | Mihir Patel | ESP32 Wireless Gateway |
| Remote commands and MQTT messaging | Mihir Patel | ESP32 Wireless Gateway |
| Sensor data acquisition and hazard scoring | Lakshanand Sugumar | PIC Sensor + HMI |
| Local display and user input | Lakshanand Sugumar | PIC Sensor + HMI |
| Motor control and movement | Raunak Singh | PIC Actuator Control |
| Emergency stop and safety behavior | Raunak Singh | PIC Actuator Control |
| UART communication and system integration | All teammates | System-level |

---

