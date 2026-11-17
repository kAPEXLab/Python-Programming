# 04_Strings_DriverMessage

**Difficulty:** Medium  
**Primary Python Concept:** Strings and string formatting  
**Supporting Concepts:** Lists, validation, conditionals, numeric formatting  
**Automotive Domain:** Driver information display  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Construct a consistent human-readable message from validated vehicle status fields.

## Prerequisites
Strings, lists, functions, conditionals, and f-strings.

## Scenario Introduction
A simulated vehicle display shows a driver message based on speed, outside temperature, and warning labels. It must be concise and deterministic.

## Problem Statement
**Goal:** Construct a consistent human-readable message from validated vehicle status fields.

**Specifically:** Build a status message containing speed and temperature, followed by warnings in their supplied order.

## Task to Implement
Implement `build_driver_message(speed_kmh: float, temperature_c: float, warnings: list[str]) -> str`.

## Input Specification
- Speed: 0 through 300 km/h.
- Temperature: -50 through 60 degrees Celsius.
- Warnings: at most five non-empty strings, each at most 30 characters.
- Reject invalid inputs with `ValueError`.

## Output Specification
Return `Speed: X.X km/h | Temperature: Y.Y C | Warnings: A, B`. Use `None` when there are no warnings and one decimal place for measurements.

## Rules and Constraints
- Preserve warning order and spelling.
- Do not deduplicate warnings.
- Do not add a warning automatically.
- Do not mutate the warning list.

## Hints
1. Validate the whole warning list before joining it.
2. Use `", ".join(...)` for multiple labels.
3. Use a separate display value for the empty-list case.

## Common Mistakes
- Sorting or deduplicating warnings.
- Formatting with too many decimal places.
- Printing `[]` instead of `None`.

## Extension Challenge
Wrap the message to a maximum of 40 characters per display line and return a list of lines.
