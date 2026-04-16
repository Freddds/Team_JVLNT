# Autonomous Pill Delivery Robot by Team JVLNT

## Overview
This project is a grid-based autonomous robot that transports pills to patients in a hospital-like environment.  
The robot uses IR sensors for grid navigation and a camera system for higher-level perception.
It follows certain security protocols.

## Hardware
- Pololu 3pi+ 32U4 robot platform
- IR line sensors
- Camera module
- Differential drive motors <!-- add type of chassis -->

## Software
- PlatformIO (VS Code)
- Arduino framework
- Pololu3piPlus32U4 library

## System Concept
The robot operates using a state machine:
### States
- IDLE:         waiting for mission
- NAVIGATE:     moving through grid
- PICKUP:       collecting pill
- DELIVER:      delivering pill
- RETURN_HOME:  going back to base
- ER_STOP:      halted due to alarm or critical error

### Transitions

- IDLE → NAVIGATE:          mission started
- NAVIGATE → PICKUP:        pickup location reached
- PICKUP → NAVIGATE:        pill secured
- NAVIGATE → DELIVER:       delivery location reached
- DELIVER → RETURN_HOME:    delivery complete
- RETURN_HOME → IDLE:       base reached
- ANY_STATE → ER_STOP:      alarm triggered
- ER_STOP → NAVIGATE:       alarm cleared

### Environment Conditions

- Red zone detected:    NAVIGATE state must compute alternative path
- Green zone detected:  LED warning is activated during NAVIGATE
- Alarm detected:       ER_STOP state triggered immediately

## Key Features
- Grid-based navigation
- Sensor-based movement correction
- Motor calibration compensation
- Modular C++ architecture

## Operating Rules / Constraints

The robot must follow the following environment-dependent rules during operation:

- **Red zones (restricted areas):**
  The robot must actively detect and avoid red zones. Entry into these zones is not allowed under any condition.

- **Green zones (active areas):**
  When the robot is driving inside a green zone, a warning LED must be activated to indicate its presence and status.

- **Alarm condition:**
  If an external alarm signal is detected (audible or system trigger), the robot must stop immediately and remain in a safe halted state until the alarm is cleared.

## State Machine Diagram
See `/docs/state_machine.md`

## Architecture
See `/docs/architecture.md`

## Authors
### Main
- Luca Diegel
- Jan Heller

### Support
- Vincent Rothe
- Nils Wolfram
- Tim Kühnberger