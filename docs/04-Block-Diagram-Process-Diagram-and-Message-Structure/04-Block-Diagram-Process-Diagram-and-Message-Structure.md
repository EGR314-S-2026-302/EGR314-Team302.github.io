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

- **[Team Block Diagram](Team-Block-Diagram/Team-Block-Diagram.md)** – 3-PCB daisy chain, data flow, interfaces  

---

## Team Process Diagram

The Process Diagram presents the sequence of communication between the Web interface, ESP32, Sensor + HMI board, and Actuator board. It captures both recurring telemetry updates and event-driven interactions such as drive commands and emergency stop conditions.

- **[Team Process Diagram](Communication-Process-Diagram/Communication-Process-Diagram.md)** – Sequence diagram, message flow, user interactions 

---

## Message Structure

The Message Structure section defines the standardized 64-byte UART packet format used across the system. It documents all message types, byte-level field definitions, and payload structures that enable deterministic routing and reliable communication between subsystems.

- **[Message Types](Message-Structure/Message-Structure.md)** – 64-byte packet format, byte-level definitions  

---

## Message Structure Design and Decision-Making

The team's message structure was designed around three core constraints: the 64-byte UART packet limit set by the class protocol specification, the need for deterministic routing across a three-board daisy chain, and the requirement for safe broadcast behavior during fault conditions.

The decision to use ASCII character board IDs rather than numeric hex IDs came from a practical debugging consideration. During early integration testing, being able to read the source and destination directly in a serial monitor output without a lookup table significantly reduced debugging time. The choice of AZ as the header and YB as the footer was inherited from the class specification and enforced by all three boards.

The payload structure was kept intentionally simple. Message type occupies the first two bytes of the payload field, followed by data bytes specific to that message type, with the remainder zero-padded. This made it straightforward for each board to parse only the message types it needed to handle and forward everything else without modification.

Broadcast messages using the asterisk destination ID were reserved exclusively for emergency stop and system status, ensuring that safety-critical signals always reached all boards regardless of their position in the chain.

## Top 5 Biggest Changes to Software Design Since the Software Proposal

1. Switch from blocking MQTT to async MQTT using mqtt_as. The original software proposal assumed a simple blocking MQTT client. During development it became clear that a blocking client would lock up the entire firmware whenever the broker connection dropped, making the WiFi failsafe impossible to implement. Switching to the mqtt_as async library allowed UART polling, MQTT communication, heartbeat publishing, and camera handling to run concurrently without blocking each other.

2. Board IDs changed from hex numbers to ASCII characters. The proposal used numeric board IDs matching the class template. During integration the team switched to ASCII character IDs where M represents Mihir's ESP32, L represents Lakshanand's sensor board, and R represents Raunak's actuator board. This made serial monitor debugging significantly easier since the source and destination were immediately readable without a lookup table.

3. Camera commands were added as a separate MQTT topic subscription. The original design had a single MQTT subscribe topic for all commands. The camera control commands, capture, stream on, and stream off, were added as a separate dedicated topic to keep camera traffic isolated from motor and sensor commands and avoid command parsing conflicts.

4. WiFi loss failsafe was extended to stop the camera stream. The original failsafe design only broadcast an emergency stop packet over UART. During development it became clear that an active camera stream would continue trying to publish frames even after the MQTT connection dropped, causing repeated errors. The failsafe was updated to explicitly stop the stream before broadcasting the emergency stop packet.

5. UART transmission was rate-limited to 500ms minimum intervals. The original firmware sent UART packets as fast as needed without any rate limiting. During integration testing with all three boards connected, rapid back-to-back transmissions caused buffer overruns and dropped bytes on the receiving boards. A 500ms minimum interval between transmissions was added to the uart_send function to ensure reliable communication across the daisy chain.