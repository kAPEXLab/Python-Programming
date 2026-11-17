---
layout: default
---

# 03_DataTypes_OdometerConversion

**Difficulty:** Difficult  
**Primary Python Concept:** Numeric types and safe type conversion  
**Supporting Concepts:** Dictionaries, validation, unit conversion, rounding  
**Automotive Domain:** Odometer and distance reporting  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Build a robust conversion function that handles multiple units, numeric validation, and precision requirements.

## Prerequisites
Functions, dictionaries, numeric types, conditionals, exceptions, and rounding.

## Scenario Introduction
An odometer stores distance in kilometers, while some reports require miles. The conversion is `1 km = 0.621371 miles`.

## Problem Statement
**Goal:** Build a robust conversion function that handles multiple units, numeric validation, and precision requirements.

**Specifically:** Convert a distance from kilometers or miles into both units and classify whether it is a plausible odometer reading.

## Task to Implement
Implement `convert_odometer(distance: float | int, unit: str) -> dict[str, object]`. Accepted units are case-insensitive `km` and `mi`.

## Input Specification
- `distance` is from 0 through 2,000,000 in the supplied unit.
- `unit` is `km` or `mi`, ignoring surrounding whitespace and case.
- Reject booleans, nonnumeric values, invalid units, and out-of-range distances with `ValueError`.

## Output Specification
Return `{"kilometers": float, "miles": float, "is_plausible": bool}`. Both distances are rounded to two decimals. A reading is plausible when kilometers are at most 2,000,000.

## Rules and Constraints
- Use the stated conversion constant exactly.
- Treat `True` and `False` as invalid numeric measurements.
- Do not round before the final output.
- Do not modify the input values.

## Hints
1. Normalize the unit before branching.
2. Convert the supplied value into a canonical kilometer value first.
3. Apply rounding only in the returned dictionary.

## Common Mistakes
- Applying the conversion factor in the wrong direction.
- Treating booleans as valid distances.
- Rounding the canonical value too early.

## Extension Challenge
Add nautical miles as an output-only field using `1 km = 0.539957 nautical miles`.
