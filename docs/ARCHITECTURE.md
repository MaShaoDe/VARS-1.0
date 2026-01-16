# VARS – System Architecture```

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
| |
v v
Power-Path Charger Backup Battery
(Supply Selection (Single Li-ion
and Load Sharing) Cell)
| |
+-------------+---------------+
|
v
5 V / 3.3 V Rails
|
v
ESP32 MCU
|
+-------------+-------------+-------------+
| | | |
IMU GNSS RTC Display
| | | |
Roll / Pitch Speed / Time Time Backup Visual Output
|
User Input
(Rotary Encoder)
|
Audio Output
(Buzzer)```
