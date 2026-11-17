# 15_Dictionaries_VehicleConfiguration

**Difficulty:** Medium  
**Primary Python Concept:** Dictionary updates and defaults  
**Supporting Concepts:** Nested dictionaries, validation, copying, functions  
**Automotive Domain:** Offline vehicle configuration profile  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Read optional configuration fields and produce a validated configuration with defaults.

## Prerequisites
Dictionaries, strings, booleans, numbers, functions, and exceptions.

## Scenario Introduction
A simulation stores optional vehicle settings for drive mode, maximum speed, and regenerative braking.

## Problem Statement
**Goal:** Read optional configuration fields and produce a validated configuration with defaults.

**Specifically:** Build a complete configuration record without changing the caller's dictionary.

## Task to Implement
Implement `complete_vehicle_configuration(config: dict[str, object]) -> dict[str, object]`.

## Input Specification
Allowed keys are `drive_mode`, `max_speed_kmh`, and `regen_enabled`. Defaults are `"NORMAL"`, `120`, and `True`. Mode is `NORMAL`, `ECO`, or `SPORT`; speed is an integer 40 through 240; regen is boolean.

## Output Specification
Return a new dictionary containing all three keys. Normalize mode to uppercase. Preserve no unknown keys.

## Rules and Constraints
- Missing keys receive defaults.
- Reject unknown keys or invalid types and ranges with `ValueError`.
- Do not mutate input.

## Hints
1. Validate keys before reading values.
2. Use a fresh result dictionary.
3. Check booleans before general integer checks.

## Common Mistakes
- Modifying the input dictionary with `setdefault`.
- Accepting unknown options silently.
- Treating `True` as the integer 1.

## Extension Challenge
Add a fourth optional setting while retaining rejection of unknown keys.
