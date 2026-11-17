# 45_VirtualEnvironmentsDependenciesAndConfiguration_VehicleSimulator

**Difficulty:** Difficult  
**Primary Python Concept:** Layered configuration and reproducible environments  
**Supporting Concepts:** `os.environ`, TOML, precedence, validation  
**Automotive Domain:** Offline vehicle simulator  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Combine defaults, a TOML file, and environment variables with explicit precedence.

## Prerequisites
Dictionaries, TOML parsing, environment variables, classes, and exceptions.

## Scenario Introduction
A simulator must produce the same setup from a checked-in config while allowing controlled test overrides.

## Problem Statement
**Goal:** Combine defaults, a TOML file, and environment variables with explicit precedence.

**Specifically:** Implement `build_simulator_config(path: Path, environ: Mapping[str, str]) -> dict[str, object]`.

## Task to Implement
Use defaults `speed_limit_kmh=120` and `mode="normal"`, then TOML `[simulator]`, then `SIM_SPEED_LIMIT_KMH` and `SIM_MODE`. Validate speed 0 through 300 and mode `normal` or `diagnostic`.

## Input Specification
The path contains optional simulator settings; environment values are strings.

## Output Specification
Return `{"speed_limit_kmh": int, "mode": str}` after applying precedence.

## Rules and Constraints
- Do not read the process environment directly; use `environ`.
- Reject malformed or unknown mode values with `ValueError`.
- Simulation is offline and deterministic.

## Hints
Normalize each source into one dictionary, then validate only after precedence is resolved.

## Common Mistakes
- Letting a file override an environment variable.
- Parsing environment numbers as raw strings.
- Using ambient environment state in tests.

## Extension Challenge
Add a `battery_soc` setting with the same precedence rules.
