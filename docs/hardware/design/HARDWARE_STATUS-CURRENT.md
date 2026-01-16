# VARS – Hardware Status
# =====================
#
# Project: VARS (Vehicle Attitude Reference System)
# Document: HARDWARE_STATUS-CURRENT
# Branch: CURRENT
# Phase: 1a
# Stability: Experimental
#
# This document reflects the current hardware evaluation state.
# It is not a final hardware specification and may change at any time.
#
# Inspired by the FreeBSD CURRENT / STABLE / RELEASE model.
#

## Purpose

This document tracks the current hardware status of VARS.
It is intended as a transparent, technical checklist for development
and evaluation purposes.

No guarantees are given regarding stability, completeness, or long-term
support at this stage.

---

## Phase 1a – Goals

- Stable operation without unintended resets
- Reliable roll and pitch indication
- Vehicle-tolerant power behaviour
- Minimal and robust user interaction
- Clean foundation for later expansion

---

## MCU

- [x] ESP32-WROOM selected
- [ ] Final pin assignment pending
- [ ] Boot and reset access to be defined

Status: fixed baseline

---

## IMU (Attitude Sensor)

- [x] MPU6500 (GY-6500) available
- [x] SPI interface planned
- [ ] Software filter strategy pending
- [ ] Mechanical mounting orientation to be defined

Optional / later evaluation:
- [ ] BNO080 / BNO085 / BNO086 (internal sensor fusion)

Status: suitable for Phase 1a, not final

---

## Temperature

- [x] DS18B20 with 3 m cable available
- [x] Suitable for IMU temperature compensation
- [ ] Final sensor placement pending

Optional:
- [ ] SHT30-D (humidity and electronics temperature)

Status: sufficient

---

## Power Supply

- [x] DC-DC converter 12 V → 5 V available
- [x] Input filtering and suppression considered
- [x] Backup operation via 18650 + power-path module
- [x] Integrated protection present
- [x] External BMS intentionally omitted

Status: complete

---

## Battery / Backup Power

- [x] Single NCR18650B cell planned
- [x] Power-path charging module available
- [ ] Mechanical fixation to be defined
- [ ] Fuse or polyfuse to be verified

Status: complete, mechanical details pending

---

## Display

- [x] 4 inch colour TFT available
- [x] Touch hardware present
- [x] Touch functionality disabled in software
- [ ] Final display size and type not yet fixed

Status: functional, not final

---

## User Input

- [x] Rotary encoder with detents planned
- [x] Push action for confirmation
- [ ] Concrete function mapping pending

Status: planned

---

## Audio

- [x] Piezo buzzer available
- [x] Transistor driver for GPIO load reduction planned
- [ ] Audio activation logic to be defined

Status: prepared

---

## Timekeeping

- [x] RTC module (DS3231) available
- [x] Backup battery planned
- [x] Independent of GPS and vehicle power

Status: complete

---

## GPS (Optional)

- [x] u-blox NEO-6M available
- [x] External antenna available
- [ ] UART pins to be reserved
- [ ] Software disabled in Phase 1a

Status: optional, prepared

---

## Mechanics

- [ ] IMU rigid and vibration-resistant mounting
- [ ] Battery mechanically secured
- [ ] Display positioned for good readability
- [ ] Antenna routing considered

Status: open

---

## Summary

- Core hardware for Phase 1a is available
- No critical hardware gaps identified
- Several components intentionally marked as non-final
- Final hardware documentation will follow after
  pin assignment and first in-vehicle testing
