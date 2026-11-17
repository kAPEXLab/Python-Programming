---
layout: default
---

# 46_CommandLineArgumentsAndEnvironmentVariables_TelemetryConverter

**Difficulty:** Difficult  
**Primary Python Concept:** CLI configuration and environment validation  
**Supporting Concepts:** `argparse`, enumerated choices, unit conversion  
**Automotive Domain:** Offline telemetry conversion  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Build a deterministic converter whose source and target units are controlled by CLI arguments and environment defaults.

## Prerequisites
`argparse`, mappings, numeric conversion, environment variables, and exceptions.

## Scenario Introduction
A telemetry converter transforms prerecorded speed samples for a report.

## Problem Statement
**Goal:** Build a deterministic converter whose source and target units are controlled by CLI arguments and environment defaults.

**Specifically:** Implement `parse_converter_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, str]`.

## Task to Implement
Parse `--source` and `--target`, each `kmh` or `mph`; defaults are `TELEMETRY_SOURCE` or `kmh`, and `TELEMETRY_TARGET` or `mph`.

## Input Specification
All unit names are case-insensitive after stripping whitespace.

## Output Specification
Return `{"source": normalized_source, "target": normalized_target}`.

## Rules and Constraints
- CLI options override environment values.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Reject missing, blank, or unsupported units with `ValueError`.
- Do not read live telemetry.

## Hints
Normalize source values through one helper and validate before constructing the result.

## Common Mistakes
- Accepting `kph` as an undocumented alias.
- Mixing conversion with argument parsing.
- Letting environment values win over CLI values.

## Extension Challenge
Add `--precision` with an integer range of 0 through 3.
