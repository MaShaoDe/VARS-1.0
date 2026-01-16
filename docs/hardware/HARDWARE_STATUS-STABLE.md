# VARS – Hardware Status
# =====================
#
# Project: VARS (Vehicle Attitude Reference System)
# Document: HARDWARE_STATUS-STABLE
# Branch: STABLE
# Phase: 1a
# Stability: Stable Reference Hardware
#
# This document defines the tested and reproducible
# reference hardware configuration for VARS Phase 1a.
#
# It represents a concrete hardware baseline intended
# for reliable replication and further development.
#

## Scope

This document specifies the **stable reference hardware**
for VARS Phase 1a.

It describes a complete, coherent hardware configuration
including power protection, backup operation, sensing,
user input, timekeeping and GNSS.

---

## Reference Hardware Overview

| Subsystem | Reference |
|---------|----------|
| MCU | ESP32-WROOM-32 |
| IMU | BNO086 IMU (I²C, internal sensor fusion) |
| Display | 4.0" TFT, SPI, non-touch operation |
| Power Input | Automotive 12 V with inline fuse |
| Power Conversion | DC-DC buck 12 V → 5 V (~3 A) |
| Backup Power | Single-cell Li-ion with power-path |
| Battery | NCR18650B |
| User Input | Rotary encoder with push-button |
| Audio | Piezo buzzer via transistor |
| Timekeeping | RTC DS3231 with backup battery |
| GNSS | u-blox NEO-8M with external ceramic antenna |

---

## MCU

**Component**
- ESP32-WROOM-32 module

**Operating voltage**
- 3.3 V

**Rationale**
- Sufficient processing headroom
- Stable ecosystem and long-term availability
- SPI, I²C and UART interfaces available
- Proven robustness when powered correctly

---

## IMU (Attitude Sensor)

**Component**
- BNO086 IMU breakout board

**Interface**
- I²C

**Supply voltage**
- 3.3 V

**Used outputs**
- Rotation Vector
- Game Rotation Vector
- Gravity Vector

**Rationale**
- Internal sensor fusion
- Low drift behaviour
- Stable roll and pitch output
- Reduced firmware complexity

---

## Display

**Component**
- 4.0 inch colour TFT
- Controller: ILI9341 or compatible

**Interface**
- SPI

**Operating mode**
- Display-only
- Touch hardware physically present but not initialised

**Rationale**
- Good readability in vehicle environments
- Deterministic SPI performance
- Touch intentionally disabled to reduce failure modes

---

## Power Input and Protection

**Input**
- Automotive 12 V supply

**Primary protection**
- Inline automotive fuse on 12 V input
- Fuse placed close to vehicle power source

**Purpose**
- Protection of wiring and system against short circuits
- No reliance on upstream vehicle protection

---

## Power Conversion

**Primary conversion**
- DC-DC buck converter: 12 V → 5 V
- Continuous current capability: approximately 3 A
- Automotive-capable design
- Input filtering and suppression applied

**Rationale**
- Sufficient current headroom for:
  - ESP32
  - Display
  - IMU
  - GNSS
  - charging circuitry
- Avoids voltage sag during transient loads
- Improves overall system stability

**Secondary regulation**
- 5 V → 3.3 V via onboard or dedicated regulator

---

## Backup Power / Notlauf

**Battery**
- Single NCR18650B Li-ion cell

**Charging and power-path**
- Li-ion charger with integrated power-path (load sharing)
- Typical implementations based on:
  - TP4056 with power-path support
  - or equivalent power-path charging controller
- Integrated protection:
  - overcharge
  - overdischarge
  - overcurrent
  - short circuit

**Behaviour**
- Seamless operation during short power interruptions
- No system reset during engine start or brief supply loss

**Rationale**
- Not intended as full UPS
- Focus on continuity and reset prevention
- Minimal complexity and predictable behaviour

---

## User Input

**Component**
- Rotary encoder with mechanical detents
- Integrated momentary push-button

**Functions**
- Mode selection
- Parameter adjustment
- Confirmation of actions

**Rationale**
- Robust mechanical input
- Operation without touch
- Suitable for vehicle use, including gloves

---

## Audio Output

**Component**
- Piezo buzzer

**Driver**
- Transistor-based driver stage
- GPIO load isolation

**Usage**
- Status feedback
- Alerts and confirmations
- No continuous audio signalling

---

## Timekeeping

**Component**
- RTC DS3231

**Backup**
- Coin cell battery (RTC backup)

**Behaviour**
- Time retained across complete power loss
- Independent of GNSS and vehicle supply

---

## GNSS (Position, Speed, Time)

**Component**
- u-blox NEO-8M GNSS module
- External ceramic antenna

**Interface**
- UART

**Usage in Phase 1a**
- Vehicle speed measurement
- Time reference
- Movement detection support

**Rationale**
- Required for speed-based logic
- Improves state detection
- More robust than IMU-only assumptions

---

## Known Limitations

- Single IMU, no redundancy
- Single backup cell, short-duration backup only
- GNSS accuracy dependent on antenna placement
- Display size may change in later revisions

---

## Change Policy

This document represents the **stable hardware baseline**.

Any change requires:
- practical validation
- documentation of rationale
- explicit update of this file

Unvalidated or experimental changes must be documented
in HARDWARE_STATUS-CURRENT.md.
