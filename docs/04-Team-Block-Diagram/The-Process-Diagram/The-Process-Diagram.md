---
title: Process Diagram 
tags:
- EGR314
- Process Diagram
---

# Block Diagram

![Team 302 Process Diagram](Team302_process_diagram.drawio.png)

---

# Communication Sequence Functionality & Requirements Alignment

Our sequence diagram captures the end-to-end flow of data and control between the Web User, ESP32 Wireless Gateway (Mihir), Sensor + HMI subsystem (Lakshanand), and Actuator Control subsystem (Raunak). Below we break down each major functional step and explain how it satisfies user needs and system requirements.

---

## 1. User-Initiated Drive Command

### Flow:

1. Web User → MQTT Server  
   - User inputs a drive command (e.g., set speed to 200 RPM) using the web dashboard.

2. MQTT Server → ESP32 (Wireless Subsystem)  
   - ESP32 subscribes to a control topic and receives the DRIVE_CMD message.

3. ESP32 → Sensor + HMI PIC via UART  
   - ESP32 frames a UART message containing the drive command (Source = ESP32, Destination = Actuator Board).

4. Sensor + HMI PIC → Actuator PIC via UART  
   - Since the message is not addressed to the Sensor board, it forwards the frame downstream unchanged.

5. Actuator PIC → Motor Driver  
   - Actuator board processes the command and updates PWM outputs to set motor speed.

### Function & Benefits:

- **Remote Control Capability:** Enables safe operation from a distance.
- **Modular Message Forwarding:** Demonstrates correct daisy-chain propagation (no direct A → C communication).
- **Standards-Based Architecture:** Structured UART frames allow deterministic routing and easy debugging.

---

## 2. Telemetry Reporting & Hazard Calculation

### Flow:

1. Actuator PIC → Sensor + HMI PIC  
   - Sends motor telemetry (current speed, state).

2. Sensor + HMI PIC → ESP32  
   - Forwards motor telemetry upstream.
   - Appends sensor data (IMU, temperature).
   - Computes hazard score and includes it in the outgoing frame.

3. ESP32 → MQTT Server  
   - Publishes telemetry and hazard score to the cloud.

4. MQTT Server → Web User  
   - Web dashboard updates in real time.

### Function & Benefits:

- **Real-Time Feedback:** Ensures live situational awareness.
- **Hazard Abstraction:** Converts raw sensor data into a simplified hazard score.
- **Bi-Directional Communication:** Both commands and telemetry use the same structured pathway.

---

## 3. Local HMI Display Update

### Flow:

1. Sensor + HMI PIC  
   - Receives telemetry and hazard information.
   - Updates OLED display via I²C.

2. In-Person User  
   - Views live speed, hazard score, and system status on OLED.

### Function & Benefits:

- **Immediate Local Feedback:** Demonstrates system operation without web dependency.
- **Educational Transparency:** Viewers can trace sensor → computation → display.

---

## 4. Recurring Telemetry Loop (Every 1 Second)

### Flow:

1. Sensor + HMI PIC → ESP32 via UART  
   - Sends periodic sensor data (IMU, temperature, hazard score).

2. ESP32 → MQTT Server  
   - Publishes telemetry update.

3. ESP32 → Sensor + HMI PIC  
   - May request updated sensor values if required.

### Function & Benefits:

- **Deterministic Timing:** Ensures system remains under sub-second update target.
- **Continuous Monitoring:** Enables stable remote supervision during demos.

---

## 5. Emergency Stop & Safety Handling

### Flow:

1. In-Person User presses Emergency Stop button (HMI).
2. Sensor + HMI PIC sends EMERGENCY_STOP frame downstream.
3. Actuator PIC immediately disables motor outputs.
4. Actuator PIC sends ACK_STOP upstream.
5. ESP32 publishes emergency status to MQTT.
6. Web User receives fault notification.

### Function & Benefits:

- **Fail-Safe Operation:** Immediate motor shutdown prevents unsafe behavior.
- **Clear Error Propagation:** Faults travel both upstream and downstream.
- **User Safety Compliance:** Meets safety requirements for public demonstrations.

---

# Summary of Functional Alignment

### Latency & Predictability
Structured UART forwarding ensures consistent propagation time between boards.

### Bi-Directional Control
Both web-based commands and in-person HMI inputs are supported.

### Modularity & Scalability
Each board forwards or consumes frames based on destination ID, allowing future expansion.

### Educational Clarity
The sequence explicitly shows every hop in the daisy chain, reinforcing modular architecture understanding.

### Reliability & Safety
Emergency stop, acknowledgment frames, and telemetry monitoring ensure stable system behavior under fault conditions.