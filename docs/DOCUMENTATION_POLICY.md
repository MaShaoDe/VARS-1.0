# Documentation Naming Concept

This document defines the naming conventions for files and directories in the VARS project.

Its purpose is to ensure long-term clarity, predictability and maintainability of the repository, especially for new contributors who need to understand structure and stability at a glance.

Naming is treated as part of the architecture.

## Core Principles

- Names must communicate intent, not implementation
- A file name should be understandable without opening the file
- Stability and maturity must be visible from the name
- Avoid cleverness, abbreviations and personal preferences
- Consistency is more important than perfection

## README Usage and Scope

There are two primary entry points:

- `README.md` (repository root)  
  High-level project overview only  
  No technical details

- `docs/README.md`  
  Documentation index and navigation  
  Explains where to find what

All detailed documentation lives under `docs/`.

## File Name Style

### General Rules

- Use ASCII characters only
- Use hyphens (`-`) to separate words
- Do not use underscores
- Do not use spaces
- Avoid abbreviations unless they are industry-standard
- Avoid version numbers in file names unless explicitly required

Correct examples:

- `parking-mode.md`
- `warning-logic.md`
- `hardware-power-supply.md`

Incorrect examples:

- `ParkingMode.md`
- `warningLogic.md`
- `hardware_v2.md`
- `final-final-really.md`

## Capitalisation Rules

### Meta Documents

Meta and governance documents use uppercase names:

- `README.md`
- `ROADMAP.md`
- `LICENSE`
- `CONTRIBUTING.md`
- `DOCUMENTATION_NAMING_CONCEPT.md`

These documents define structure, scope or rules.

### Topic Documents

All topic-specific documents use lowercase names:

- `calibration.md`
- `normal-mode.md`
- `parking-mode.md`
- `imu-selection.md`

Topic documents describe concepts, behaviour or procedures.

## Stability Markers

Where stability or maturity matters, it must be explicit in the file name.

Allowed markers:

- `-STABLE.md`  
  Reproducible, recommended reference  
  Safe starting point for builders

- `-CURRENT.md`  
  Active evaluation, experimentation or transition state

Examples:

- `HARDWARE_STATUS-STABLE.md`
- `HARDWARE_STATUS-CURRENT.md`

Rules:

- Never mix stable and experimental content in the same document
- When a document transitions, create a new file rather than overwriting history
- There must be exactly one STABLE reference per topic

## Directory Responsibilities

Each directory has a single responsibility.

- `docs/concepts/`  
  Architecture, philosophy and design intent  
  Explains *why*

- `docs/hardware/`  
  Hardware references, rationale and evaluation  
  Explains *what is used*

- `docs/modes/`  
  User-visible behaviour and mode separation  
  Explains *how it behaves*

- `docs/calibration/`  
  Calibration concepts and procedures

- `docs/warnings/`  
  Warning and alert logic

- `firmware/`  
  Source code only  
  No conceptual documentation

- `assets/`  
  Visual references, screenshots and mockups  
  No specifications

## When to Create a New Document

Create a new document if:

- The topic has a different audience
- The stability level differs
- The scope grows beyond one screen of text
- The document would otherwise mix concept and implementation

Do not extend documents indefinitely.

## What Does Not Belong in File Names

- Dates
- Author names
- Emotional qualifiers (final, new, fixed, updated)
- Temporary markers

History belongs in Git, not in file names.

## Change Discipline

- Renaming files is a structural change and should be discussed
- Do not rename files to reflect opinion changes
- Prefer adding documents over renaming existing ones

## Goal

This naming concept exists to ensure that:

- New contributors gain orientation within minutes
- Builders can clearly identify stable reference material
- The repository remains calm, readable and professional over time
