# 45_VirtualEnvironmentsDependenciesAndConfiguration_FleetAnalytics

**Difficulty:** Easy  
**Primary Python Concept:** Dependency and configuration boundaries  
**Supporting Concepts:** `tomllib`, environment configuration, reproducibility  
**Automotive Domain:** Offline fleet analytics  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Read a small project configuration and use its declared rounding policy deterministically.

## Prerequisites
Dictionaries, functions, file paths, TOML basics, and environment concepts.

## Scenario Introduction
A fleet analytics tool reads a local TOML configuration rather than relying on machine-specific settings.

## Problem Statement
**Goal:** Read a small project configuration and use its declared rounding policy deterministically.

**Specifically:** Implement `load_analytics_config(path: Path) -> dict[str, object]` using Python 3.12's `tomllib`.

## Task to Implement
Read `[analytics]` values `round_digits` and `unit`, requiring an integer 0 through 3 and unit `km` or `mi`.

## Input Specification
`path` identifies a UTF-8 TOML file with the required analytics table.

## Output Specification
Return the analytics dictionary with both validated values.

## Rules and Constraints
- Use a virtual-environment-friendly standard-library implementation.
- Never hard-code a user's absolute path.
- Raise `ValueError` for invalid configuration.

## Hints
Parse with `tomllib.load` in binary mode and validate the resulting types.

## Common Mistakes
- Using `eval` to parse configuration.
- Accepting a boolean as an integer setting.
- Depending on the current working directory.

## Extension Challenge
Add a dependency version string and validate it against a simple policy.
