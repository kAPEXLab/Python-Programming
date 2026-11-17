---
layout: default
---

# 25_DataValidation_VehicleSensorPacket

**Difficulty:** Easy
**Primary Python Concept:** Data validation  
**Supporting Concepts:** Dictionaries, types, ranges, exceptions  
**Automotive Domain:** Offline vehicle sensor packet validation  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Validate a structured sensor packet before any calculation uses it.

## Prerequisites
Dictionaries, functions, type checks, and exceptions.

## Scenario Introduction
A simulator receives a packet containing speed, battery voltage, and coolant temperature.

## Problem Statement
**Goal:** Validate a structured sensor packet before any calculation uses it.

**Specifically:** Return a normalized copy only when every required field is valid.

## Task to Implement
Implement `validate_sensor_packet(packet: dict[str, object]) -> dict[str, float]`.

## Input Specification
Required keys are `speed_kmh` (0-300), `battery_voltage` (0-500), and `coolant_c` (-40-150). Values must be finite `int` or `float`, excluding booleans.

## Output Specification
Return the three fields as floats in the same units. Raise `ValueError` for missing, extra, mistyped, or out-of-range fields.

## Rules and Constraints
- Do not mutate the input.
- Reject extra keys to catch schema drift.
- This validates sample data only; it does not read sensors.

## Hints
1. Compare the key set exactly.
2. Check numeric type before range checks.
3. Build a separate result dictionary.

## Common Mistakes
- Accepting missing fields as zero.
- Mutating the packet while normalizing it.
- Treating `True` as speed 1.

## Extension Challenge
Return a list of field-specific error strings instead of raising at the first error.
