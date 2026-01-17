# VARS – Test Plan

Project: VARS (Vehicle Attitude Reference System)  
Document: TEST_PLAN  
Status: Stable  
Phase: 1a  
Language: English  

---

## Purpose

This document defines the test plan for VARS Phase 1a.

The test plan verifies that the system behaves exactly as specified in:
- ARCHITECTURE.md
- CALIBRATION.md
- PARK_MODE.md
- WARNING_LOGIC.md

The goal is reproducibility, not certification.

---

## Test Philosophy

The VARS test plan follows these principles:

- tests are deterministic
- tests are repeatable
- tests are observable by the user
- tests do not require special laboratory equipment
- failures are visible, not inferred

No automated self-test framework is assumed in Phase 1a.

---

## Test Environment

### Hardware Requirements

- VARS device installed or bench-mounted
- stable 12 V power supply or vehicle power
- functional backup battery
- display connected
- rotary encoder connected
- buzzer connected (if acoustic tests are performed)

---

### Environmental Conditions

- indoor or outdoor environment
- stable temperature (no extreme thermal testing)
- vehicle stationary for attitude-related tests

---

## Test Categories

The test plan is divided into the following categories:

1. Power and startup behaviour
2. Calibration behaviour
3. Normal Mode behaviour
4. Park Mode behaviour
5. Warning logic behaviour
6. Power interruption and recovery
7. Error handling and suppression

---

## Power and Startup Tests

### TP-001: Cold Start

**Precondition:**  
System powered off.

**Action:**  
Apply vehicle power.

**Expected Result:**  
- system boots normally
- display becomes active
- no warning output
- system enters Normal Mode

---

### TP-002: Backup Power Continuity

**Precondition:**  
System powered on, backup battery charged.

**Action:**  
Briefly interrupt vehicle power.

**Expected Result:**  
- no system reset
- display remains active
- no loss of calibration data

---

## Calibration Tests

### TP-010: Calibration Execution

**Precondition:**  
System in Normal Mode, vehicle stationary.

**Action:**  
Trigger calibration via rotary encoder.

**Expected Result:**  
- calibration confirmation shown
- offsets stored
- system returns to Normal Mode

---

### TP-011: Calibration Persistence

**Precondition:**  
Calibration completed.

**Action:**  
Power cycle system completely.

**Expected Result:**  
- calibration offsets retained
- reference unchanged

---

## Normal Mode Tests

### TP-020: Normal Mode Display

**Precondition:**  
System running, Normal Mode active.

**Action:**  
Observe display.

**Expected Result:**  
- roll and pitch displayed
- no warning colours
- no acoustic output

---

## Park Mode Tests

### TP-030: Park Mode Activation

**Precondition:**  
System in Normal Mode.

**Action:**  
Activate Park Mode via user input.

**Expected Result:**  
- visual transition to Park Mode
- Park Mode indicators visible
- no warnings unless thresholds exceeded

---

### TP-031: Park Mode Deactivation

**Precondition:**  
Park Mode active.

**Action:**  
Deactivate Park Mode via user input.

**Expected Result:**  
- return to Normal Mode
- no residual warnings

---

## Warning Logic Tests

### TP-040: Neutral Zone

**Precondition:**  
Park Mode active, vehicle level.

**Action:**  
Observe system.

**Expected Result:**  
- no visual warning
- no acoustic output

---

### TP-041: Caution Zone Entry

**Precondition:**  
Park Mode active.

**Action:**  
Introduce slight roll or pitch beyond comfort threshold.

**Expected Result:**  
- visual caution indication
- no acoustic warning

---

### TP-042: Warning Zone Entry

**Precondition:**  
Park Mode active, acoustic enabled.

**Action:**  
Introduce roll or pitch beyond warning threshold.

**Expected Result:**  
- visual warning indication
- single acoustic signal

---

### TP-043: Warning Clearance

**Precondition:**  
Warning Zone active.

**Action:**  
Return vehicle to neutral zone.

**Expected Result:**  
- warning cleared immediately
- no residual indication

---

## Power Interruption Tests

### TP-050: Engine Start Simulation

**Precondition:**  
System powered via vehicle supply.

**Action:**  
Simulate voltage dip or brief interruption.

**Expected Result:**  
- system remains operational
- no reset
- no false warnings

---

## Error Handling Tests

### TP-060: Sensor Failure Simulation

**Precondition:**  
System running.

**Action:**  
Disconnect or invalidate a sensor input.

**Expected Result:**  
- warnings suppressed
- no false warning output
- system remains stable

---

## Test Completion Criteria

The test plan is considered fulfilled when:

- all tests pass as defined
- no undocumented behaviour is observed
- no test requires interpretation or assumption

Failures must be documented and traced to:
- hardware
- firmware
- documentation mismatch

---

## Limitations of This Test Plan

This test plan does not cover:

- long-term drift
- extreme vibration
- extreme temperature
- regulatory compliance
- safety certification

---

## Stability of Test Plan

This test plan is stable for Phase 1a.

Any change to system behaviour requires:
- update of this document
- review of dependent documents

---

## Summary

This test plan ensures that VARS Phase 1a:

- behaves predictably
- follows documented logic
- can be verified by direct observation

It completes the documentation set required for a stable Phase 1a release.
