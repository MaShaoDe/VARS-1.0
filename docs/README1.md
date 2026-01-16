# VARS – Vehicle Attitude Reference System

VARS is an ESP32-based colour cockpit display for visualising vehicle
attitude (roll and pitch).

It is designed for camper vans and similar vehicle projects and supports
calm and precise vehicle levelling while parked.

The focus is on clear geometry, stable visualisation and a defensive,
neighbour-friendly warning philosophy for parking and sleeping comfort.

VARS is a DIY open-source project and is **not intended for safety-critical
or certification-required applications**.

---

## Project Status

Status: Phase 1a Core  
Implementation in progress  
Not production-ready  
Not certified  

---

## Project Goals

VARS displays roll and pitch in real time as an artificial horizon on a
colour display.

In parking mode, the system supports vehicle levelling and provides a
visual assessment of comfort and stability.

Key objectives:
- calm and stable visual output in real vehicle environments
- clear separation between normal operation and parking mode
- explicit user-controlled calibration
- defensive, neighbour-friendly warning logic

---

## Non-Goals and Scope Limitations

VARS is **not** a replacement for:
- professional vehicle measurement equipment
- flight or automotive avionics
- safety-critical driver assistance systems

The project is intended for orientation, comfort and experimental
extension in a DIY context.

---

## Hardware Overview (Stable)

VARS is designed as a robust, vehicle-tolerant system for reliable
roll, pitch and motion-related state detection.

The current **stable hardware reference** for Phase 1a is based on:

- **MCU:** ESP32-WROOM-32
- **IMU:** BNO086 with internal sensor fusion (roll, pitch, gravity)
- **Display:** 4.0" colour TFT (SPI), non-touch operation
- **User Input:** Rotary encoder with push-button
- **Power Supply:** Automotive 12 V input with inline fuse  
  → DC-DC buck converter to 5 V (~3 A)  
  → secondary 3.3 V regulation
- **Backup Power:** Single-cell Li-ion (NCR18650B) with power-path charger  
  for reset-free operation during short supply interruptions
- **Timekeeping:** RTC DS3231 with backup battery
- **GNSS:** u-blox NEO-8M with external ceramic antenna  
  (used for speed and time reference)

This configuration represents a **tested and reproducible baseline**.
Detailed rationale, component roles and change policy are documented in:

`doc/hardware/HARDWARE_STATUS-STABLE.md`

Ongoing evaluations, alternatives and experimental components are tracked
separately in:

`doc/hardware/HARDWARE_STATUS-CURRENT.md`

---

## Technical Framework

Target platform:
- ESP32

Sensors:
- Single IMU with internal sensor fusion
- Roll and pitch as primary quantities

Display:
- Colour display, preferably TFT
- Focus on geometry and colour rather than numeric output

Toolchain:
- PlatformIO as reference toolchain
- Arduino IDE optional, but not the recommended development path

---

## Design Principles

- One consistent source of truth for vehicle attitude
- Calm visual output using filtering and deadband
- No automatic or surprising behaviour
- Warnings only in explicitly enabled parking mode
- Audio output disabled by default
- Extensible without architectural redesign

---

## Operating Modes

### Normal Mode
Displays roll and pitch only.  
No active warnings.  
No audio output.

### Parking Mode
Explicitly activated by the user.  
Colour-coded inclination zones for comfort and safety assessment.  
Optional audio output, always manually enabled.

---

## Calibration

Calibration is performed explicitly by the user in the desired reference
position.

Roll and pitch offsets are stored persistently.
There is **no automatic calibration**.

---

## Warning Logic

Warnings are active **only** in parking mode.

All thresholds use:
- minimum duration
- hysteresis
- cooldown periods

Acoustic warnings are optional and are always disabled when leaving
parking mode.

---

## Project Structure

Repository structure:

- `README.md`  
  Project overview and entry point

- `docs/`  
  Concepts, calibration, parking mode, warning logic and test plans

- `firmware/`  
  ESP32 firmware, modular design

- `assets/`  
  Screenshots, UI mockups and visual references

- `hardware/`  
  Optional: schematics, enclosures, PCB files

Detailed documentation is located in the `docs/` directory.

---

## Roadmap

Current phase: Phase 1a Core

Included:
- ESP32 as target platform
- Single central IMU
- Roll and pitch calculation
- Artificial horizon
- Fixed vehicle reference symbol
- Manual calibration

Not included:
- Navigation
- Advanced parking warning logic
- Audio output
- Touch interaction
- Secondary displays

---

## Getting Started

VARS is intended for users with basic embedded systems knowledge.

Assumptions:
- ESP32-based hardware
- IMU with sensor fusion
- Colour display
- Development on macOS or Linux

A detailed setup guide will follow once the core functionality
has stabilised.

---

## Safety and Disclaimer

VARS is an uncertified DIY system.
It is not intended for safety-critical applications.
Use is entirely at your own risk.

---

## Contributing

Contributions are welcome.

Please keep pull requests focused, centralise configuration changes
and use issues for discussion.

---

## License

BSD 2-Clause License  
See the `LICENSE` file for details.
