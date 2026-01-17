# VARS – Park Mode

Project: VARS (Vehicle Attitude Reference System)
Document: PARK_MODE
Status: Stable
Phase: 1a
Language: English

---

## Purpose

This document defines the behaviour, logic and limitations of Park Mode in VARS.

Park Mode is designed to assist the user in evaluating vehicle attitude
while stationary, primarily for parking, camping and resting scenarios.

It is not a driving aid and not a safety system.

---

## Definition of Park Mode

Park Mode is a user-activated operating mode.

It provides:
- enhanced visualisation of roll and pitch
- comfort-oriented reference zones
- optional acoustic feedback

Park Mode does not influence sensor sampling, calibration or power behaviour.

---

## Activation and Deactivation

Park Mode is:

- activated explicitly by the user
- confirmed via rotary encoder push action
- deactivated explicitly by the user

There is no automatic activation or timeout-based deactivation.

System power cycles do not automatically re-enter Park Mode.

---

## Preconditions

Park Mode assumes:

- vehicle is stationary
- calibration is valid
- user intends to evaluate vehicle attitude

Vehicle motion detection may suppress warnings but does not block activation.

---

## Visual Representation

In Park Mode, the display shows:

- roll and pitch relative to calibrated reference
- colour-coded comfort and safety zones
- simplified geometry-focused representation

Numeric values are secondary or omitted.

---

## Comfort and Warning Zones

Park Mode uses predefined angular zones:

- neutral zone (comfortable)
- caution zone
- warning zone

Exact thresholds are fixed in Phase 1a and not user-configurable.

Zones are symmetric around the calibrated reference.

---

## Acoustic Feedback

Acoustic feedback in Park Mode is:

- optional
- disabled by default
- user-enabled if desired

Sound signals are used to indicate:
- entry into warning zones
- confirmation actions

There is no continuous or escalating alarm behaviour.

---

## Behaviour During Power Events

During power interruptions:

- Park Mode state is not preserved
- system returns to Normal Mode after restart
- no warning state is latched

Backup power ensures continuity but not state retention.

---

## Error Handling in Park Mode

If sensor data becomes invalid:

- visual indication is degraded
- no false warnings are generated
- system remains operational

Park Mode does not trigger system resets.

---

## Limitations

Park Mode does not:

- evaluate ground stability
- compensate for suspension movement
- predict vehicle shift
- replace levelling equipment

It is an informational aid only.

---

## Non-Goals of Park Mode

The Park Mode explicitly excludes:

- automatic levelling control
- adaptive threshold learning
- terrain analysis
- legal or safety guarantees

---

## Stability of Park Mode

The Park Mode logic defined here is stable for Phase 1a.

Any change requires:
- documentation update
- behavioural review
- consistency check with CALIBRATION.md and ARCHITECTURE.md

---

## Summary

Park Mode is a deliberate, user-controlled mode providing:

- clear attitude information
- calm visual feedback
- optional, restrained audio cues

It supports informed decisions without automation or intervention.
