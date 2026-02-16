---
title: Block Diagram, Process Diagram and Message Structure
tags:
- EGR314
- Block Diagram, Process Diagram and Message Structure
---

# Block Diagram, Process Diagram and Message Structure

This section documents the full team-level system architecture for the R6 Recon Amphibot. It includes the hardware connectivity between boards, the software communication flow, and the structured UART message protocol used across the daisy-chain network. Together, these documents define how commands, telemetry, and safety signals move throughout the system.

---

## Team Block Diagram

The Team Block Diagram illustrates the physical and logical layout of the three-PCB system, including the ESP32 Wireless Gateway, Sensor + HMI subsystem, and Actuator subsystem. It highlights the UART daisy-chain order, power distribution strategy, and interface separation between local peripherals and inter-board communication.

- **[Team Block Diagram](04-Block-Diagram,-Process-Diagram,-and-Message-Structure/Team-Block-Diagram/Team-Block-Diagram.md)** – 3-PCB daisy chain, data flow, interfaces  

---

## Team Process Diagram

The Process Diagram presents the sequence of communication between the Web interface, ESP32, Sensor + HMI board, and Actuator board. It captures both recurring telemetry updates and event-driven interactions such as drive commands and emergency stop conditions.

- **[Team Process Diagram](04-Block-Diagram,-Process-Diagram,-and-Message-Structure/The-Process-Diagram/The-Process-Diagram.md)** – Sequence diagram, message flow, user interactions 

---

## Message Structure

The Message Structure section defines the standardized 64-byte UART packet format used across the system. It documents all message types, byte-level field definitions, and payload structures that enable deterministic routing and reliable communication between subsystems.

- **[Message Types](04-Block-Diagram,-Process-Diagram,-and-Message-Structure/Message-Structure/Message-Structure.md)** – 64-byte packet format, byte-level definitions  