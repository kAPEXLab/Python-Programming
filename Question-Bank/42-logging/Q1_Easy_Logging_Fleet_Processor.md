---
layout: default
---

# 42_Logging_FleetProcessor

**Difficulty:** Easy  
**Primary Python Concept:** The `logging` module  
**Supporting Concepts:** Log levels, handlers, formatted messages  
**Automotive Domain:** Offline fleet processing  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Configure a logger that records deterministic fleet-processing events at the requested severity.

## Prerequisites
Functions, classes, strings, exceptions, and basic module imports.

## Scenario Introduction
A fleet processor needs useful offline logs while it summarizes incoming vehicle records.

## Problem Statement
**Goal:** Configure a logger that records deterministic fleet-processing events at the requested severity.

**Specifically:** Create `FleetProcessor(logger: logging.Logger)` with `process(vehicle_id: str, distance_km: float) -> str`.

## Task to Implement
Log an `INFO` message for a valid record and return `PROCESSED:<vehicle_id>:<distance_km:.1f>km`. Reject invalid identifiers or negative distances with `ValueError` and log an `ERROR` message.

## Input Specification
`vehicle_id` is a non-empty string. `distance_km` is a finite number from 0 through 2000 km.

## Output Specification
Return the exact processed string. Logging text must include the vehicle identifier and use the appropriate level.

## Rules and Constraints
- Use the supplied logger; do not configure the root logger.
- Use Python 3.12+ and deterministic values.
- This is an offline simulation with no real vehicle connection.

## Hints
Validate before logging success, and use a formatter-friendly message with arguments.

## Common Mistakes
- Calling `basicConfig` inside the class.
- Logging errors at `INFO` level.
- Rounding the input before validating it.

## Extension Challenge
Add a `WARNING` log when distance exceeds 1500 km.
