---
title: Concept Generation and Design Ideation
---

# Goal of the Exploration Device

The goal of our exploration device is to safely collect meaningful environmental information from hazardous or inaccessible environments while minimizing operator risk and cognitive load. The Amphibot V1 is designed to scout unknown terrain, provide real-time visual and sensor feedback, and communicate system state clearly to a human operator. The device emphasizes modularity, rapid deployment, and observable cause-and-effect interactions between user input and system response.

On top of actually working as an explorer, it's also meant to teach and demonstrate embedded systems design. Using UART-connected modular PCBs, sensor–actuator feedback loops, and straightforward human–machine interfaces, the project lets anyone watching easily understand how embedded systems sense their environment, make decisions, and take action in real-world situations.

---

# Intended Audience

Real-time users break into two key groups.

1. **Engineering instructors, peers, and external reviewers** who evaluate the system during the EGR314 Innovation Showcase. These users focus on system architecture, communication standards, robustness, and how effectively the design meets technical constraints.

2. **Real-world end users** such as emergency responders, industrial inspectors, or search-and-rescue teams who deploy the Amphibot V1 in hazardous environments such as flooded buildings, chemical spills, or collapsed structures. For them, reliable real-time intelligence (gas levels, obstacles, water depth) with minimal training is critical, enabling fast, informed decisions without risking human lives.

A **secondary audience** includes non-technical showcase visitors. For this group, the device provides obvious visual and behavioral cues (bright LEDs, smooth motion responses), intuitive control, and immediate feedback. As recommended by Bitgood’s Suggested Guidelines for Designing Interactive Exhibits, it accommodates a wide range of user familiarity by minimizing instructions, making correct operation visually apparent, and supporting safe use by non-experts.

---

## Brainstorm Process Overview

During our brainstorming session, we explored many different ideas related to building an exploration device. We defined an exploration device as any tool or system that can collect data from environments that are unknown, dangerous, or difficult for humans to access. Early on, we discussed whether our project should be a single standalone device or part of a larger system deployed from a “mothership,” such as a drone, rover, boat, or satellite. As we talked through these options, we quickly realized that our team size of three, limited budget, and overall project scope made very large or complex systems unrealistic for this semester. This pushed us toward ideas that are achievable now but still leave room for future expansion.

We considered several possible environments for exploration, including underwater areas, volcanic regions, and caves. In all of these cases, the common goal was to collect data from places where sending a human would be unsafe or impractical. One idea that consistently stood out was modularity. Instead of building one large system that does everything, we explored using multiple smaller exploration units. This approach could allow better coverage of an area, provide backup if one unit fails, and support teamwork between devices for data collection and mapping.

As our ideas developed further, we started refining the modular approach into more specific system concepts. One idea involved a water exploration setup with multiple stages or detachable subsystems. In this concept, nearby devices could communicate with each other using short-range methods such as sonar, while a surface unit would send collected data back to a mothership using Wi-Fi. At the same time, we explored a hybrid drone/rover concept inspired by R6, designed to work on both land and water. This concept focused on interchangeable components like wheels, propulsion systems, cameras, sonar, and wireless communication to increase flexibility while still being realistic to prototype.

Throughout the brainstorming process, several design priorities stayed consistent across all concepts. We wanted to reduce the amount of direct human involvement, improve the accuracy and reliability of the data collected, support automation where possible, and make sure the system could be upgraded over time. Rather than building a one-time prototype, our goal was to create a platform that could improve through testing, modular hardware changes, and sensor-driven data collection. These priorities, along with ease of use and the need to demonstrate meaningful robotics and automation, led us toward an MVP-style approach: building a first version that fits within our constraints while still allowing future expansion.

---

# Generating Ideas

---

## Easy of Deployment & Initial Use

| Need / Requirement                         | Feature                         | Details                                                                 |
| ------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------- |
| Easy of Deployment & Initial Use           | Throwable chassis               | Can be tossed into hazardous areas to start a mission quickly.         |
| Easy of Deployment & Initial Use           | Compact body                    | Fits through narrow openings and tight spaces.                          |
| Easy of Deployment & Initial Use           | One-button power on             | Starts up with a single press—no complicated steps.                     |
| Easy of Deployment & Initial Use           | Auto-leveling system            | Stabilizes itself after landing so it’s ready to drive.                 |
| Easy of Deployment & Initial Use           | Reset-to-home mode              | Returns to a default ready state for the next operator.                 |
| Easy of Deployment & Initial Use           | Magnetic docking pad            | Snaps onto a dock for quick pickup, storage, and charging.              |
| Easy of Deployment & Initial Use           | Foldable components             | Folds down to reduce size during transport.                             |
| Easy of Deployment & Initial Use           | Lanyard-assisted drop           | Lets you lower it safely into shafts or openings.                       |
| Easy of Deployment & Initial Use           | Pre-armed standby mode          | Wakes up instantly after deployment with no extra setup.                |

---

## Mobility & Terrain Adaptability

| Need / Requirement                           | Feature                         | Details                                                                 |
| ------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------- |
| Operate confidently on land                | Single-handed operation         | Usable with one hand—helpful in stressful or constrained situations.    |
| Move reliably on flat surfaces             | Wheeled propulsion              | Simple, dependable driving on smooth terrain.                           |
| Maintain traction on debris                | Tank-style tracks               | Grips better on rubble, sand, and uneven ground.                        |
| Maneuver in tight spaces                   | Omni-directional wheels         | Can move sideways for precise positioning.                              |
| Travel through water when needed           | Flip-out fins                   | Deploys fins to swim across water sections.                             |
| Sustain water propulsion                   | Propeller drive                 | Provides steady forward motion in water.                                |
| Work across land and water                 | Paddle wheels                   | A dual-purpose option that handles both surfaces.                       |
| Recover after flips                        | Self-righting body              | Automatically returns upright if it rolls over.                         |
| Clear obstacles                            | Adjustable ride height          | Raises the body to get over bumps and edges.                            |
| Protect against impacts                     | Shock-absorbing shell           | Helps protect internal parts during drops and collisions.               |
| Adapt to different terrain                 | Modular wheel attachments       | Swap wheel/track modules based on the environment.                      |
| Handle uneven ground                       | Articulated chassis             | Flexes to keep contact and control on rough terrain.                    |
| Stay stable while moving                   | Low center of gravity design    | Reduces tipping risk during turns and impacts.                          |

---

## Sensors & Environmental Awareness

| Need / Requirement                                 | Feature                | Details                                                                 |
| ------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------- |
| See what the device sees                    | FPV camera                      | Streams live video back to the operator.                                |
| Maintain visibility in darkness             | Low-light camera                | Keeps the view usable in dim or dark areas.                             |
| Get a wider view of the scene               | Wide-angle lens                 | Covers more area so you miss less at the edges.                         |
| Detect hazardous atmospheres                 | Gas sensor                      | Flags dangerous gases in the environment.                               |
| Spot heat-related risks                      | Temperature sensor              | Identifies hot zones or thermal hazards.                                |
| Understand moisture conditions               | Humidity sensor                 | Helps detect damp, wet, or condensation-prone areas.                    |
| Sense depth underwater                       | Pressure/depth sensor           | Measures water depth during submerged operation.                        |
| Track motion and orientation                 | Inertial Measurement Unit (IMU) | Reports tilt, movement, and orientation changes.                        |
| Catch leaks early                             | Water intrusion sensor          | Alerts if water enters the chassis.                                     |
| Detect collisions                             | Impact detection                | Registers bumps or crashes for awareness and logging.                   |
| Detect unstable ground                        | Vibration sensor                | Helps identify shaky surfaces or rough travel conditions.               |
| Combine signals into one picture              | Sensor fusion                   | Blends sensor data to improve reliability.                              |
| Summarize risk level                          | Hazard scoring algorithm        | Rolls multiple readings into a simple danger indicator.                 |

---

## Controls & Human Interaction

| Need / Requirement                                | Feature               | Details                                                                 |
| ------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Make controls feel intuitive                | Direction-mapped buttons        | Buttons match natural movement directions.                              |
| Use familiar inputs                          | Joystick input                  | Game-style control that most users already understand.                  |
| Reduce training time                         | Game controller support         | Works with common controllers to lower the learning curve.              |
| Operate remotely                             | Smartphone app                  | Wireless control from a phone or tablet.                                |
| Control from any device                      | Web-based dashboard             | Runs in a browser across platforms.                                     |
| Provide tactile control                      | Dedicated handheld controller   | Physical buttons and feedback for confident operation.                  |
| Choose precision or speed                    | Speed modes                     | Switch between careful movement and faster travel.                      |
| Move safely in tight spaces                  | Crawl mode                      | Slow, controlled driving for confined areas.                            |
| Stop instantly in emergencies                | Emergency stop                  | Immediate shutdown when something goes wrong.                           |
| Always allow human control                   | Manual override                 | Operator can take back control at any time.                             |
| Prevent accidental commands                  | Control lockout                 | Locks inputs to avoid unintended movement.                              |
| Assist navigation                            | Waypoint navigation             | Moves to set points with reduced operator workload.                     |
| Keep safe distance from walls                | Follow-wall mode                | Maintains spacing from surfaces automatically.                          |

---

## User Cues & Feedback (Ease of Use)

| Need / Requirement                            | Feature                         | Details                                                                 |
| ------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Make system status obvious                  | LED indicators                  | Shows power and current state at a glance.                              |
| Show modes clearly                          | Color-coded LEDs                | Different colors communicate different modes.                           |
| Signal how serious an error is              | LED brightness levels           | Brighter patterns indicate higher severity.                             |
| Confirm commands were received              | Audio tones                     | Simple tones acknowledge user inputs.                                   |
| Indicate readiness                           | Startup sound sequence          | Lets users know when the system is ready.                               |
| Confirm actions without looking              | Vibration feedback              | Tactile confirmation for key actions.                                   |
| Show when the camera is active               | Camera ring LED                 | Visible indicator that the camera is on.                                |
| Show motion status                            | Motor activity indicator        | Signals when the drive system is active.                                |
| Communicate fault types                       | Blinking error pattern          | Distinct blink patterns identify fault states.                          |
| Warn on critical faults                       | Audible error alarm             | Louder alert for urgent issues.                                         |
| Avoid unexpected shutdown                     | Battery level indicator         | Clear battery status to plan before power runs out.                     |
| Show connection quality                       | Signal strength indicator       | Helps diagnose weak links or dropouts.                                  |

---

## Durability & Safety

| Need / Requirement                    | Feature                         | Details                                                                 |
| -------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Protect electronics from the environment     | Enclosed electronics            | Keeps debris and dirt away from sensitive components.                   |
| Survive rough handling                       | Impact-resistant shell          | Designed to withstand drops and bumps.                                  |
| Repair quickly                               | Replaceable outer shell         | Swap the shell instead of repairing the whole unit.                     |
| Shield internal boards                        | Internal shock mounts           | Reduces shock loads on PCBs and connectors.                             |
| Reduce electrical hazard                      | Low-voltage system              | Lower voltage reduces shock risk.                                       |
| Prevent motor/electrical damage               | Overcurrent protection          | Limits current spikes that can harm motors or electronics.              |
| Fail safely                                   | Fuse protection                 | Cuts power to prevent catastrophic failures.                            |
| Avoid sharp edges                              | Rounded edges                   | Reduces snagging and risk of cuts or pinches.                           |
| Detect tip risk                                | Tip-over detection              | Flags instability during movement.                                      |
| Shut down safely on fault                      | Controlled shutdown             | Powers down in a predictable, safe way.                                 |
| Prevent overheating                            | Thermal shutdown                | Automatically reduces risk if temperatures get too high.                |

---

## Instruction & Learning

| Need / Requirement                                | Feature                         | Details                                                                 |
| -------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Get started quickly                          | One-page quick-start            | A short guide that gets users operating fast.                           |
| Keep instructions simple                      | Icon-based cues                 | Uses visuals so users don’t need to read long text.                     |
| Guide users step-by-step                      | On-screen prompts               | Walks operators through key actions.                                    |
| Offer help when it’s needed                   | Context-sensitive help          | Shows tips based on what the user is doing.                             |
| Support beginner-to-expert learning           | Layered help menus              | Basic help upfront; advanced details optional.                          |
| Demonstrate without input                     | Auto-demo mode                  | Runs an automated demo hands-free.                                      |
| Show continuously in a booth                  | Looping demo script             | Repeats a demo sequence for displays.                                   |
| Help new users succeed                        | Beginner mode                   | Slower movement and guided controls.                                    |
| Enable full control for experts               | Expert mode                     | No restrictions—complete manual control.                                |
| Refresh fundamentals quickly                  | Reset tutorial                  | A quick walkthrough to relearn the basics.                              |

---

## System Architecture & Expansion

| Need / Requirement                             | Feature                         | Details                                                                 |
| --------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Support modular electronics                   | UART daisy-chain                | Links multiple boards in a simple chain.                                |
| Add capabilities easily                        | Plug and play modules           | Drop-in modules without complex wiring.                                 |
| Keep the internal layout compact               | Stackable PCBs                  | Layers boards to save space.                                             |
| Ensure reliable communication                  | CRC error checking              | Detects corrupted messages between boards.                              |
| Detect module failures                          | Heartbeat monitoring            | Flags nodes that stop responding.                                       |
| Recover automatically from faults               | Watchdog timers                 | Auto-resets components that hang or crash.                              |
| Make servicing straightforward                   | Accessible service panels       | Access key parts without full disassembly.                              |
| Speed up troubleshooting                         | Diagnostic LEDs                 | Quick visual clues during debugging.                                    |
| Prepare for future upgrades                      | Ports available for new sensors | Ports for new sensors or modules.                                       |
| Scale to multiple controllers                    | Expansion ports                 | Supports multiple boards/controllers working together.                  |
| Scalability                                      | Multi-node support              | Multiple controllers / Multi-node architecture                          |

---

## Exploratory Ideas

| Need / Requirement                                   | Feature                         | Details                                                                 |
| ------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Enable sacrificial scouting                  | Disposable scout mode           | A mode for high-risk missions where loss is acceptable.                |
| Show destroyed or disabled state             | Intentional failure feedback    | Clearly indicates when the unit is no longer functional.               |
| Extend reach with deployables                 | Mothership deployment           | A larger unit launches smaller scouts.                                 |
| Coordinate multiple units                     | Swarm operation                 | Multiple devices working together.                                     |
| Improve navigation intelligence                | AI-assisted navigation          | Suggests or selects routes based on terrain.                           |
| Build a hazard map                             | Environmental mapping           | Turns sensor data into a visual map of conditions.                     |
| Review missions afterwards                     | Mission replay                  | Playback for analysis and training.                                    |
| Make demos interactive                         | Audience voting control         | Let the audience influence control during showcases.                   |

---

## Demonstration & Showcase Impact

| Need / Requirement                                     | Feature                         | Details                                                                 |
| -------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------- |
| Make system data easy to follow               | Live telemetry display          | Shows key metrics in real time for the audience.                        |
| Ensure everyone can see                        | Projection to large screen      | Optimized for large-format display.                                     |
| Show amphibious capability                     | Water tank demo                 | Simple setup to demonstrate water operation.                            |
| Show ruggedness                                | Obstacle course demo            | Highlights durability and terrain handling.                             |
| Make hazards understandable                    | Visual hazard demo              | Uses clear visuals so risk is easy to interpret.                        |
| Explain what’s happening                       | Status overlay on video         | Adds labels and status directly onto the feed.                          |
| Support repeated demos                         | Fast reset sequence             | Resets quickly between runs.                                            |
| Reduce downtime                                | Replaceable battery pack        | Swap batteries instead of waiting to recharge.                          |
| Support multiple viewers                       | Spectator display mode          | Lets multiple people watch the feed at once.                            |

---

# Concept 1 — Smart & Autonomous Recon Scout


| Feature Group        | Feature                       | Priority | Details                                      |
| -------------------- | ----------------------------- | -------- | -------------------------------------------- |
| Smart Navigation     | Waypoint navigation           | High     | Allows semi-autonomous movement              |
| Smart Navigation     | Follow-wall mode              | Medium   | Maintains distance from surfaces             |
| Smart Navigation     | AI-assisted navigation        | Low      | Adapts movement based on terrain             |
| Sensor Intelligence  | Sensor fusion                 | High     | Combines data from multiple sensors          |
| Sensor Intelligence  | Hazard scoring algorithm      | High     | Summarizes environmental danger level        |
| Sensors              | FPV camera                    | High     | Live video feed for monitoring               |
| Sensors              | Inertial Measurement Unit (IMU)| High    | Tracks orientation and motion                |
| Sensors              | Low-light camera              | Medium   | Improves visibility in dark areas            |
| User Interface       | Live telemetry display        | High     | Shows real-time system data                  |
| User Interface       | Status overlay on video       | Medium   | Explains robot behavior visually             |
| Software Features    | Mission replay                | Medium   | Allows playback of recorded runs             |
| Software Features    | Context-sensitive help        | Low      | Provides guidance when needed                |
| Control Safety       | Manual override               | High     | Ensures user control during autonomy         |
| Wireless             | Web-based dashboard           | Medium   | Allows control and monitoring remotely       |

![Concept 1](EGR314_Concept1.png)

This concept is designed to feel like a “smart assistant” rather than a fully manual robot. Instead of controlling every movement, the user gives the robot simple directions, such as where to go or what area to explore, and the robot handles the details on its own. While it moves, the user can watch live video and system information on a screen, helping them understand what the robot is seeing and why it is making certain decisions. If anything unexpected happens, the user can immediately take control, making the system feel both intelligent and trustworthy.

### Team Responsibility Split — Concept 1 (3 Teammates)

1. **Internet-based Two-way Wireless Communication (Teammate A)**  
   Teammate A will implement the two-way wireless communication using Wi-Fi, including sending waypoint and control commands to the robot and streaming telemetry and video data back to the user interface. They will also handle reliability concerns such as reconnect behavior and safe operation if the connection drops.

2. **Human–Machine Interface via Screen and Buttons (Teammate B)**  
   Teammate B will design the screen-based interface showing live video, telemetry, hazard score, and navigation status. They will implement manual override controls, on-screen prompts, and clear alerts so the user always understands what the robot is doing.

3. **Sensor + Autonomy Controlled Response (Teammate C)**  
   Teammate C will integrate sensor data, implement sensor fusion and hazard scoring, and develop waypoint navigation logic. They will also handle controlled responses between sensors and actuators to ensure smooth and safe autonomous movement.

---

# Concept 2 — Cost-Effective & Modular Hazard

| Feature Group  | Feature                   | Priority | Details                                                        |
| -------------- | ------------------------- | -------- | -------------------------------------------------------------- |
| Deployment     | Throwable chassis         | High     | Enables quick deployment into hazardous areas                  |
| Deployment     | Compact body              | High     | Fits through narrow spaces                                     |
| Deployment     | One-button power on       | High     | Minimizes setup time                                            |
| Mobility       | Wheeled propulsion        | High     | Simple and low-cost movement                                    |
| Durability     | Replaceable outer shell   | High     | Damaged shells can be easily replaced                           |
| Durability     | Shock-absorbing shell     | Medium   | Reduces damage from impacts                                     |
| Modularity     | Modular parts             | High     | Allows replacement of only damaged components                   |
| Modularity     | Plug-and-play modules     | Medium   | Simplifies repair and upgrades                                  |
| Cost Reduction | Standardized fasteners    | Medium   | Uses common, inexpensive hardware                               |
| Cost Reduction | Shared components         | Medium   | Same parts reused across subsystems                             |
| Power Efficiency| Energy-efficient motor   | Medium   | Reduces power consumption                                       |
| Power Efficiency| Replaceable battery pack | Medium   | Extends operating life between runs                             |
| User Cues      | LED indicators            | Medium   | Basic feedback for system status                                |
| Exploratory    | Intentional failure feedback | Low   | Indicates when the device is no longer operational              |

![Concept 2](EGR314_Concept2.png)

This concept is built for situations where the environment is dangerous and the robot might get damaged. The idea is to keep the robot simple, affordable, and easy to deploy, so a user can quickly send it into a risky area without worrying too much about losing it. It turns on with a single button, drives using basic wheels, and focuses on getting useful information fast. If something breaks, only the damaged parts need to be replaced instead of the whole robot, making it practical for repeated use in high-risk scenarios.

### Team Responsibility Split — Concept 2 (3 Teammates)

1. **Internet-based Two-way Wireless Communication (Teammate A)**  
   Teammate A will handle basic two-way wireless communication for sending control commands and receiving video and system status information. The focus will be on maintaining a stable and reliable connection rather than advanced automation features.

2. **Human–Machine Interface via Screen and Buttons (Teammate B)**  
   Teammate B will design a minimal screen-based interface that displays essential information such as the video feed, battery level, and overall system state. Controls will be kept simple and easy to understand to reduce user confusion.

3. **Sensor + Actuator Controlled Response (Teammate C)**  
   Teammate C will implement motor control, basic sensor integration, and safety behaviors such as controlled shutdown and fault detection. Their focus will be on reliable operation and low-cost implementation rather than advanced autonomy.

---

# Concept 3 — Fast Deployment, Strong Situational Awareness


| Feature Group         | Feature                         | Priority | Details                                                                 |
| --------------------- | ------------------------------- | -------- | ----------------------------------------------------------------------- |
| Deployment & Startup  | Throwable chassis               | High     | Can be tossed into hazardous areas to start a mission quickly.         |
| Deployment & Startup  | Compact body                    | High     | Fits through narrow openings and tight spaces.                          |
| Deployment & Startup  | One-button power on             | High     | Starts up with a single press—no complicated steps.                     |
| Deployment & Startup  | Auto-leveling system            | Medium   | Stabilizes itself after landing so it’s ready to drive.                 |
| Deployment & Startup  | Reset-to-home mode              | Medium   | Returns to a default ready state for the next operator.                 |
| Mobility & Terrain    | Omni-directional wheels         | High     | Moves sideways for precise positioning in tight spaces.                 |
| Mobility & Terrain    | Low center of gravity design    | High     | Reduces tipping risk during turns, bumps, and impacts.                  |
| Mobility & Terrain    | Two-wheel efficient drive       | High     | Uses fewer motors to reduce power draw and simplify the drivetrain.     |
| Mobility & Terrain    | Flexible / compliant chassis    | Medium   | Helps maintain contact and control on uneven ground.                    |
| Water Capability      | Flip-out fins                   | Medium   | Deploys fins to swim across short water sections when needed.           |
| Remote Control & UX   | Smartphone app                  | High     | Wireless control from a personal device (phone/tablet).                 |
| Remote Control & UX   | On-screen prompts               | High     | Step-by-step guidance so new users can operate confidently.             |
| Remote Control & UX   | Waypoint navigation             | High     | Moves to set points to reduce operator workload.                        |
| Remote Control & UX   | Manual override                  | High     | Operator can instantly take control if autonomy struggles.              |
| Remote Control & UX   | Emergency stop                  | High     | Immediate shutdown if something goes wrong.                             |
| Operator Awareness    | FPV camera                      | High     | Streams live video to the operator’s personal device.                   |
| Operator Awareness    | Live telemetry display          | High     | Shows key system data (battery, link, alerts) in real time.             |
| Operator Awareness    | Hazard scoring algorithm        | High     | Rolls sensor readings into a simple danger indicator.                   |
| User Cues & Feedback  | Color-coded LEDs                | Medium   | Clear mode/status visibility at a glance.                               |
| User Cues & Feedback  | Camera ring LED                 | Medium   | Obvious indicator when the camera is active.                            |
| User Cues & Feedback  | LED indicators (basic status)   | Medium   | Quick power/state feedback without opening the app.                     |
| Power & Uptime        | Replaceable battery pack        | High     | Swap batteries to keep missions and demos running.                      |
| Power & Uptime        | Battery level indicator         | Medium   | Prevents unexpected shutdown by showing remaining power.               |
| Safety & Durability   | Thermal shutdown                | High     | Protects the system if internal temperatures get too high.              |
| Safety & Durability   | Replaceable outer shell         | High     | Damaged shell can be swapped instead of repairing the whole unit.       |
| Safety & Durability   | Impact-resistant / shock-absorbing shell | Medium | Helps protect internal parts during drops and collisions.               |
| Safety & Durability   | Enclosed electronics            | Medium   | Keeps debris and dirt away from sensitive components.                   |

![Concept 3](images/304f1b.png)

This concept is designed for fast deployment, simple operation, and strong situational awareness in hazardous environments. The throwable chassis and one-button power let an operator begin a mission immediately with minimal setup. Auto-leveling stabilizes the device after landing so it becomes drive-ready quickly, and reset-to-home returns it to a default ready state for the next operator. Omni-directional wheels allow precise positioning in tight spaces, while a low center of gravity reduces tipping risk during turns and bumps. A two-wheel efficient drive reduces power use, improving runtime and reliability.

FPV video to a personal device and a live telemetry display keep the operator informed at a safe distance. The hazard scoring algorithm simplifies environmental risk into one easy-to-read indicator. On-screen prompts reduce confusion and training time. Thermal shutdown protects the system from overheating, and replaceable battery packs plus a replaceable outer shell reduce downtime and make field recovery practical.

### Team Responsibility Split - Concept 3 (3 Teammates)

1. **Internet-based Two-way Wireless Communication (Teammate A)**  
   Teammate A will implement the two-way wireless link (Wi-Fi), including sending control commands from the phone to the robot and streaming FPV video + telemetry back to the user. They will handle reliability issues such as reconnect behavior, message formatting/protocol, and safe behavior if the signal drops.

2. **Human–Machine Interface via Screen and Buttons (Teammate B)**  
   Teammate B will build the smartphone interface (screen-based HMI) showing live video, hazard score, battery level, connection strength, and temperature status. They will design the control layout (joystick/d-pad + key buttons), implement on-screen prompts, and create clear alerts (low battery, weak signal, high temperature). They will ensure the emergency stop is always visible and easy to access.

3. **Sensor + Actuator Controlled Response (Teammate C)**  
   Teammate C will implement motor control and motion behavior (two-wheel efficient driving and omni-directional movement as supported by the mechanical design). They will integrate sensor inputs used for hazard scoring, implement waypoint navigation logic, and build safety behaviors such as thermal shutdown, emergency stop response, and safe fallback if communication is lost.

---

# Design Questions & Answers

## Why concept 3?

We chose Concept 3 because it combines the most valuable strengths of Concept 1 and Concept 2 into one realistic build. Compared to Concept 1, Concept 3 keeps the key “smart” benefits (waypoint navigation, hazard scoring, telemetry + FPV) but avoids heavy autonomy complexity that increases implementation risk and debugging time. Compared to Concept 2, Concept 3 keeps the core practical build advantages (throwable deployment, replaceable shell, replaceable battery, reliability-focused design) while adding essential awareness tools (FPV + telemetry + hazard score + prompts) that make the device safer and easier to use. Overall, Concept 3 provides the best balance of feasibility, safety, usability, and mission effectiveness—making it the strongest option to build.

## What cues will make the device easier to use?

We will provide simple, redundant cues so users never have to guess device status. Color-coded LEDs show mode/state, a camera ring LED shows when the camera is active, and a clear telemetry panel in the phone app displays battery level, signal strength, temperature, and hazard score. On-screen prompts guide users through setup and operation, and warnings appear immediately when something needs attention (low battery, overheating risk, weak connection).

## How will the controls be designed?

Controls will be designed for low cognitive load and quick learning. The phone app will combine FPV video, a simple movement control (joystick/d-pad), and large buttons for key actions like waypoint navigation and reset-to-home. A large emergency stop will always be visible. Manual override will always be available so the user can instantly take control whenever autonomy is active.

## What role will durability and comfort play?

Durability is essential because operators need to trust the device enough to deploy it into dangerous areas. The throwable chassis supports rough handling, while thermal shutdown protects internal components. Replaceable battery packs reduce downtime and keep missions running. A replaceable outer shell makes damage recovery simple and lowers repair time and cost. Comfort comes from predictable handling: the low center of gravity improves stability and reduces operator stress, while clear cues reduce mental load.

## What instruction is needed to use the device?

Instruction will be minimal and built into the experience. Users will have a one-page quick-start guide (deploy → connect → drive → interpret hazard score → recover/reset). The app will provide on-screen prompts for first-time setup, plus a short guided tutorial explaining basic driving, emergency stop, waypoint use, and how to read telemetry/hazard cues. Advanced features will be optional; basic driving + video should work immediately.
