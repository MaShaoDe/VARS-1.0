# Contributing to VARS

Thank you for your interest in contributing to VARS – Vehicle Attitude Reference System.

VARS is an open-source DIY project with a strong focus on clarity, calm design and maintainable structure. Contributions are welcome, provided they respect the project’s scope, philosophy and documentation discipline.

This document explains how to contribute effectively.

## General Principles

- Keep contributions focused and scoped
- One topic per pull request
- Prefer clarity over cleverness
- Avoid mixing conceptual, hardware and firmware changes in one PR
- Discuss larger changes before implementing them

VARS values thoughtful design and predictable behaviour over rapid feature growth.

## Ways to Contribute

You can contribute in several ways:

- Improve documentation (clarity, structure, consistency)
- Review concepts and design decisions
- Suggest improvements or alternatives via issues
- Implement firmware features within the defined scope
- Test hardware configurations and report findings
- Improve UI behaviour, stability or visual calmness

Documentation contributions are just as valuable as code.

## Getting Started

If you are new to the project:

1. Read the main `README.md`
2. Continue with `docs/README.md` for documentation structure
3. Familiarise yourself with the relevant topic area in `docs/`
4. Check existing issues to avoid duplication

If something is unclear, open an issue and ask.

## Issues

Please use GitHub issues for:

- Questions and clarification
- Bug reports
- Design discussions
- Feature proposals

When opening an issue:

- Be clear and concise
- Describe the context and motivation
- Separate observation from opinion
- Avoid solution dumping for conceptual topics

## Pull Requests

Before submitting a pull request:

- Make sure your changes align with the current project phase
- Keep the PR limited to a single concern
- Ensure documentation and code remain consistent
- Update or add documentation if behaviour changes

Pull requests should describe:

- What was changed
- Why the change is needed
- Which documents or concepts are affected

Large or structural changes should be discussed in an issue first.

## Documentation Changes

Documentation follows a strict structure and naming policy.

Before editing or adding documentation, read:

- `docs/DOCUMENTATION_POLICY.md`

Do not mix stable and experimental content in the same document.  
If stability matters, use explicit markers such as `-STABLE` or `-CURRENT`.

## Firmware Contributions

Firmware lives in the `firmware/` directory.

Guidelines:

- Follow the existing modular structure
- Avoid hard-coded behaviour where configuration is expected
- Do not introduce automatic or surprising behaviour
- Respect the separation between normal mode and parking mode

Firmware should implement behaviour defined in documentation, not redefine it.

## Hardware Contributions

Hardware-related contributions should clearly state:

- Whether they are stable or experimental
- What problem they solve
- How they were tested

Stable hardware references must be reproducible.

## Behaviour and Scope

VARS is intentionally limited in scope.

Please do not propose or implement:

- Safety-critical functionality
- Driver assistance systems
- Autonomous behaviour
- Certification-related features

Such proposals will be declined to protect the project’s focus.

## Code of Conduct

Be respectful and constructive.

This project values calm discussion, technical clarity and good faith collaboration.  
Disagreement is acceptable. Disrespect is not.

## License

By contributing to VARS, you agree that your contributions are licensed under the same license as the project:

BSD 2-Clause License.
