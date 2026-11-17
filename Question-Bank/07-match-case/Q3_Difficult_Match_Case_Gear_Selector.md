# 07_MatchCase_GearSelector

**Difficulty:** Difficult  
**Primary Python Concept:** Advanced structural pattern matching  
**Supporting Concepts:** Nested dictionaries, guards, validation, domain rules  
**Automotive Domain:** Offline gear-selector simulation  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Match nested state records and apply guarded rules without controlling real vehicle hardware.

## Prerequisites
Dictionaries, functions, validation, `match-case`, and boolean logic.

## Scenario Introduction
A simulated gear selector reports the requested gear and vehicle speed. The exercise only creates a text decision; it must never connect to a real vehicle.

## Problem Statement
**Goal:** Match nested state records and apply guarded rules without controlling real vehicle hardware.

**Specifically:** Decide whether a requested gear change is permitted under simplified offline rules.

## Task to Implement
Implement `evaluate_gear_request(state: dict[str, object]) -> str`. Required fields are `requested_gear` (`P`, `R`, `N`, `D`) and `speed_kmh`.

## Input Specification
Speed is 0 through 300 km/h. Rules: `P` is allowed only at 0; `R` only from 0 through 5 inclusive; `N` is always allowed; `D` is allowed above 0. Unknown gears are invalid. Raise `ValueError` for malformed input.

## Output Specification
Return `ALLOWED_<gear>` or `REJECTED_<gear>`, such as `ALLOWED_R`.

## Rules and Constraints
- Use `match-case` with guards.
- Normalize gear strings.
- This is an offline simulation only.

## Hints
1. Extract and normalize the two fields first.
2. Match each gear separately.
3. Put the speed condition in a guard.

## Common Mistakes
- Allowing reverse at any speed.
- Treating missing fields as valid.
- Writing real actuator commands instead of returning a simulation result.

## Extension Challenge
Add a `vehicle_mode` field where `TOW` permits only `N`.
