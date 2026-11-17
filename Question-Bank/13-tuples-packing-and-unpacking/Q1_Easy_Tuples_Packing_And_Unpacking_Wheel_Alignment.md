---
layout: default
---

# 13_TuplesPackingAndUnpacking_WheelAlignment

**Difficulty:** Easy  
**Primary Python Concept:** Tuple packing and unpacking  
**Supporting Concepts:** Numeric validation, indexing, functions  
**Automotive Domain:** Offline wheel alignment readings  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Pack alignment measurements into tuples and unpack them into named values.

## Prerequisites
Variables, tuples, arithmetic, functions, and conditionals.

## Scenario Introduction
A workshop simulation records camber, caster, and toe angles in degrees for one wheel.

## Problem Statement
**Goal:** Pack alignment measurements into tuples and unpack them into named values.

**Specifically:** Classify whether a wheel is aligned based on fixed tolerances.

## Task to Implement
Implement `check_wheel_alignment(measurements: tuple[float, float, float]) -> str`.

## Input Specification
The tuple is `(camber, caster, toe)` with finite values from -10.0 through 10.0 degrees.

## Output Specification
Return `"ALIGNED"` when absolute camber is at most 1.0, absolute caster is at most 2.0, and absolute toe is at most 0.5; otherwise return `"ADJUST"`.

## Rules and Constraints
- Unpack the tuple in one assignment.
- Require exactly three numeric values and reject booleans with `ValueError`.
- Do not change the input tuple.

## Hints
1. Validate length and numeric types first.
2. Unpack as `camber, caster, toe`.
3. Compare absolute values with inclusive limits.

## Common Mistakes
- Comparing only positive deviations.
- Requiring values to be strictly inside limits.
- Accepting a list when a tuple is required.

## Extension Challenge
Return the first measurement name that exceeds its tolerance.
