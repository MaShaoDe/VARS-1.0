# VARS – Calibration

Project: VARS (Vehicle Attitude Reference System)
Document: CALIBRATION
Status: Stable
Phase: 1a
Language: English

---

## Purpose

This document defines the calibration model of VARS.

Calibration establishes the reference orientation of the vehicle and
ensures that roll and pitch values are displayed relative to a
user-defined baseline.

Calibration in VARS is explicit, deterministic and fully user-controlled.

---

## Calibration Principles

VARS follows a strict calibration philosophy:

- no automatic calibration
- no background adjustment
- no continuous drift compensation
- no implicit reference changes

All calibration actions are initiated deliberately by the user and
applied persistently.

---

## What Is Calibrated

The following parameters are calibrated:

- roll offset
- pitch offset

These offsets define the zero-reference of the artificial horizon.

Yaw or heading is not calibrated and not used in Phase 1a.

---

## When Calibration Is Performed

Calibration is performed:

- when the user explicitly requests it
- while the vehicle is stationary
- in the desired reference position

Typical use cases:
- initial installation
- after mechanical changes
- after sensor repositioning
- after firmware updates affecting orientation logic

Calibration is never triggered automatically.

---

## Calibration Procedure

The calibration process consists of the following steps:

1. Vehicle is positioned in the desired reference orientation
2. User enters calibration mode via the rotary encoder
3. Calibration action is explicitly confirmed
4. Current roll and pitch values are sampled
5. Offsets are calculated and stored persistently
6. System returns to normal operation

No intermediate or partial calibration states are applied.

---

## Persistence and Storage

Calibration offsets are stored in non-volatile memory.

Characteristics:
- offsets survive power loss
- offsets survive backup battery operation
- offsets are not modified unless recalibration is performed

There is no automatic reset of calibration data.

---

## Behaviour After Calibration

After calibration:

- displayed roll and pitch values are relative to the stored offsets
- artificial horizon is centred at the calibrated position
- all operating modes use the same reference

Calibration affects:
- Normal Mode
- Parking Mode

There is no mode-specific calibration.

---

## Error Handling During Calibration

If calibration cannot be completed:

- no partial data is stored
- previous calibration remains active
- the user is informed visually

Calibration failure does not cause a system reset.

---

## Calibration Limitations

- calibration assumes a stable vehicle position
- calibration does not compensate for long-term mechanical deformation
- calibration does not correct sensor hardware faults

Incorrect calibration results directly in incorrect displayed values.

---

## User Responsibility

Calibration accuracy depends entirely on:

- correct vehicle positioning
- deliberate user action
- correct interpretation of the reference position

VARS does not attempt to detect or correct calibration misuse.

---

## Non-Goals of Calibration

The calibration system intentionally excludes:

- self-learning behaviour
- continuous re-alignment
- environmental compensation
- dynamic recalibration while driving

---

## Calibration Stability

The calibration model defined in this document is stable for Phase 1a.

Any change to the calibration logic requires:
- explicit documentation
- architectural review
- update of this document

---

## Summary

Calibration in VARS is:

- explicit
- deterministic
- persistent
- user-controlled

It defines the single, global reference for roll and pitch and remains
unchanged until deliberately updated by the user.
