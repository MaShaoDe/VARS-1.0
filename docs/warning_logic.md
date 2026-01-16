# VARS – Warning Logic

Project: VARS (Vehicle Attitude Reference System)
Document: WARNING_LOGIC
Status: Stable
Phase: 1a
Language: English

---

## Purpose

This document defines the warning logic of VARS.

Warning logic determines when visual or acoustic indications are generated,
how they behave, and under which conditions warnings are explicitly suppressed.

Warnings in VARS are informational aids.  
They are not safety guarantees and do not imply risk assessment.

---

## Fundamental Principles

The warning system follows strict principles:

- no automatic intervention
- no escalation logic
- no self-learning behaviour
- no hidden state transitions
- no safety-critical claims

Warnings inform the user but never act on behalf of the user.

---

## Preconditions for Warning Evaluation

Warnings are evaluated only if all of the following conditions are met:

- Park Mode is active
- sensor data is valid
- calibration data is present
- system is not in an error state

If any precondition is not met, warnings are suppressed.

---

## Warning Parameters

Warnings are based exclusively on:

- roll angle relative to calibration
- pitch angle relative to calibration

Yaw, heading, speed and acceleration are not part of warning evaluation.

---

## Warning Zones

The warning system uses fixed angular zones:

- Neutral Zone  
  Vehicle attitude is within comfortable limits. No warning.

- Caution Zone  
  Vehicle attitude exceeds comfort limits. Visual indication only.

- Warning Zone  
  Vehicle attitude exceeds defined thresholds. Visual indication and optional audio.

Thresholds are symmetric around the calibrated reference.

Threshold values are fixed in Phase 1a and not user-configurable.

---

## Visual Warning Behaviour

Visual warnings are:

- colour-based
- continuous while the condition persists
- non-blinking
- non-animated beyond basic geometry

Visual warnings do not latch and disappear immediately when the condition clears.

---

## Acoustic Warning Behaviour

Acoustic warnings are:

- optional
- disabled by default
- user-enabled explicitly

Characteristics:
- short, discrete signals
- no continuous tones
- no increasing frequency or volume
- no repetition beyond state transitions

Acoustic warnings indicate:
- entry into Warning Zone
- confirmation of user actions

---

## Warning Suppression

Warnings are suppressed under the following conditions:

- Normal Mode is active
- calibration is missing or invalid
- sensor data is unavailable or implausible
- system startup phase
- power transition phase

Suppression prevents false or misleading indications.

---

## Behaviour During Movement

If vehicle movement is detected:

- warnings may be visually degraded
- acoustic warnings are suppressed
- no new warning states are entered

VARS does not attempt to interpret dynamic driving conditions.

---

## Error Interaction

If an error condition is present:

- warning logic is suspended
- error indication takes precedence
- no warning output is generated

Warnings never mask error states.

---

## Persistence and State

Warning states are:

- transient
- non-persistent
- recalculated continuously

No warning state is stored across power cycles.

---

## Non-Goals of Warning Logic

The warning system intentionally excludes:

- prediction of vehicle instability
- evaluation of terrain conditions
- suspension or load modelling
- risk classification
- legal or safety assurances

---

## Stability of Warning Logic

The warning logic defined in this document is stable for Phase 1a.

Any modification requires:
- update of this document
- consistency check with PARK_MODE.md
- update of TEST_PLAN.md

---

## Summary

The VARS warning logic is:

- deterministic
- conservative
- non-intrusive
- user-respecting

It provides clear indications without automation, escalation or intervention.
