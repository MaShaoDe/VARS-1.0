# VARS – System Architecture

Project: VARS (Vehicle Attitude Reference System)
Document: ARCHITECTURE
Status: Stable
Phase: 1a
Language: English

---

## Purpose

This document defines the system architecture of VARS.

It describes the structural composition of the system, the interaction
between subsystems, and the architectural decisions that govern behaviour,
robustness and failure handling.

---

## Architectural Overview

VARS is a single-node embedded system designed for use in automotive
environments.

The system consists of clearly separated functional domains:

- power input, protection and continuity
- sensing and time reference
- processing and state logic
- presentation
- user interaction
- feedback and signalling

There are no distributed components, no cloud dependencies and no hidden
background automation.

---

## High-Level System Structure

    Vehicle Power (12 V)
            |
            v
    Inline Fuse & Input Protection
            |
            v
    DC-DC Buck Converter (12 V → 5 V, ~3 A)
            |
            +-----------------------------+
            |                             |
            v                             v
    Power-Path Charger              Backup Battery
    (Supply Selection               (Single Li-ion
     and Load Sharing)                Cell)
            |                             |
            +-------------+---------------+
                          |
                          v
                   5 V / 3.3 V Rails
                          |
                          v
                       ESP32 MCU
                          |
            +-------------+-------------+-------------+
            |             |             |             |
           IMU           GNSS           RTC          Display
            |             |             |             |
       Roll / Pitch   Speed / Time   Time Backup   Visual Output
                          |
                      User Input
                    (Rotary Encoder)
                          |
                      Audio Output
                       (Buzzer)

---

## Core Processing Unit

### ESP32 MCU

The ESP32-WROOM-32 acts as the central processing and control unit.

Responsibilities:
- sensor data acquisition
- system state interpretation
- mode management
- display rendering
- user input handling
- coordination of warning and feedback logic

All system logic resides on the MCU.
No external controller performs autonomous decisions.

---

## Power Architecture

### Power Input and Protection

- Automotive 12 V vehicle supply
- Inline fuse placed close to the power source
- Input protection against short circuits and wiring faults

The system does not rely solely on upstream vehicle protection.

---

### Power Conversion

- DC-DC buck conversion from 12 V to 5 V
- Continuous current capability of approximately 3 A
- Supplies MCU, display, sensors, GNSS and charging circuitry

Secondary regulation:
- 5 V to 3.3 V for logic and sensors

Voltage stability is prioritised over efficiency.

---

### Power-Path and Backup Operation

The system implements a power-path based backup architecture.

Characteristics:
- two power sources: vehicle supply and internal Li-ion cell
- automatic, seamless switching between sources
- load powered directly from the active source
- battery charging when external power is present

Behaviour:
- no system reset during engine start
- no reset during short supply interruptions
- deterministic behaviour during power transitions

This mechanism ensures continuity, not long-term autonomy.

---

## Sensor Architecture

### IMU

Provides roll and pitch information based on gravity reference.
Yaw and heading are not part of the core architecture.

---

### GNSS

Provides vehicle speed, movement detection and auxiliary time reference.
GNSS is not used for navigation.

---

### RTC

Provides persistent time across complete power loss.

---

## Presentation Layer

The display is a pure output device.

Design principles:
- geometry-based representation
- colour-coded information
- minimal numeric data
- calm, non-distracting visuals

Touch functionality is not used.

---

## User Interaction

User input is intentionally minimal:
- rotary encoder with detents
- integrated push-button

---

## Audio Feedback

Audio output is optional and disabled by default.
Used only for confirmations and parking warnings.

---

## Operating Modes

### Normal Mode

- roll and pitch display only
- no warnings
- no audio output

### Parking Mode

- explicitly activated by the user
- colour-coded comfort and safety zones
- optional acoustic warnings

---

## Calibration Model

Calibration is explicit, user-triggered and persistent.
There is no automatic recalibration.

---

## Error Handling Philosophy

- degraded operation preferred over shutdown
- no hidden recovery actions
- visible state over silent correction

---

## Architectural Non-Goals

The architecture intentionally excludes:
- redundancy
- safety certification claims
- autonomous decision-making
- adaptive behaviour
- cloud connectivity

---

## Architectural Stability

This architecture is considered stable for Phase 1a.
Changes require documentation and review.

---

## Summary

VARS is a single-node, deterministic, vehicle-tolerant embedded system
focused on robustness, predictability and clarity.
