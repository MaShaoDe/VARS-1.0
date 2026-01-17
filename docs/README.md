# VARS Documentation

This directory contains the structured documentation for the VARS – Vehicle Attitude Reference System project.

The documentation is organised to give new contributors, builders and reviewers a fast and clear overview of the project, its scope and its internal structure.

Start here if you want to understand how VARS is designed, how it behaves and where to find specific information.

## How the Documentation Is Organised

The documentation follows a topic-based structure.  
Each directory has a clear responsibility and avoids overlap with others.

High-level project orientation lives in the repository root `README.md`.  
All conceptual, technical and procedural details live in this `docs/` directory.

## Documentation Areas

### Concepts

`docs/concepts/`

Foundational ideas and design decisions:

- Overall system concept
- Architectural principles
- Design philosophy and assumptions

These documents explain *why* VARS is designed the way it is.

### Hardware

`docs/hardware/`

Hardware-related documentation, separated by stability level:

- `HARDWARE_STATUS-STABLE.md`  
  Reproducible reference hardware for the current development phase

- `HARDWARE_STATUS-CURRENT.md`  
  Ongoing evaluations, alternatives and experimental components

Builders should always start with the STABLE reference.

### Operating Modes

`docs/modes/`

Descriptions of user-visible system behaviour:

- Normal mode
- Parking mode

Focus is on behaviour and mode boundaries, not firmware implementation.

### Calibration

`docs/calibration/`

Calibration concepts and procedures:

- User-controlled reference alignment
- Persistent roll and pitch offsets
- Explicit calibration philosophy

There is no automatic or hidden calibration.

### Warnings and Alerts

`docs/warnings/`

Warning and alert logic:

- Visual warning zones
- Optional acoustic alerts
- Duration, hysteresis and cooldown rules
- Parking-mode-only enforcement

### Testing

`docs/testing/`

Test concepts and validation plans:

- Manual test procedures
- Behaviour verification
- Regression considerations

## Firmware and Code

Firmware source code lives in the top-level `firmware/` directory.

Documentation describes intent and behaviour.  
Firmware implements this behaviour.

## How to Get Started

If you are new to VARS:

1. Read the repository root `README.md`
2. Continue with this document
3. Start with the documents in `docs/concepts/`
4. Refer to hardware and mode documentation as needed

## Contributing to Documentation

Documentation structure and naming rules are defined in:

`docs/DOCUMENTATION_POLICY.md`

Please follow these rules when adding or modifying documentation.

