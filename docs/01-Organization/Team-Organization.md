---
title: Team Organization
tags:
- EGR314
- Team Organization
---

# Team Organization

## Team Charter

> "Team XPED commits to modular mastery and tactical innovation, delivering the R6 Recon Amphibot through UART standards, equitable rotations, and relentless demo execution, exploring hazards as a united engineering force."

On January 15th, the team held an initial brainstorming session to define the
scope of the exploration device. Ideas explored included underwater mappers,
volcanic probes, cave robots, and modular mothership-based systems using sonar
and Wi-Fi stages. The team ultimately converged on an R6-inspired amphibious
rover concept combining wheeled land propulsion, flip-out fins for water
traversal, and a UART daisy-chain architecture. The team charter was adopted
to unify the team around EGR314 standards and a shared goal of a successful
Innovation Showcase demonstration.

## Product Mission Statement

> "The R6 Siege Recon Amphibot scouts hazardous land/water terrains with fused
> FPV sensors and wireless commands, providing operators actionable data from
> environments too perilous for humans, modular, throwable, tactical."

The mission statement reflects the team's core design philosophy: prioritizing
operator safety and actionable intelligence over system complexity. Following
the initial brainstorm, the team narrowed the concept from broader ideas such
as underwater exploration, volcanic probes, and cave mapping down to the R6
Recon Amphibot, a wheeled land rover with flip-out fins for water traversal,
connected via a UART daisy-chain architecture.

## Team Composition and Roles

| Team Member | Subsystem | Role |
|---|---|---|
| Mihir Patel | ESP32 Wireless Gateway | Two-way MQTT communication, UART bridge, camera integration |
| Lakshanand Sugumar | Sensor + HMI | Environmental sensors, hazard scoring, OLED display |
| Raunak Singh | Actuator Control | Motor control, PID, fin deployment, safety behaviors |

## Communication and Workflow

The team communicated through a shared GitHub organization repository, weekly
in-person syncs, and a group messaging channel. All design decisions, schematic
reviews, and integration milestones were tracked through GitHub commits and
shared documentation. Role rotation was practiced to ensure all members
understood each subsystem beyond their own board.

## Additional Organizational Information

Further details about team structure, meeting notes, and role assignments can
be found in the
[Team Organization Appendix](../Appendix/01-Organization-Information/Append-Organization.md)