---
layout: default
---

# 22_TypeHintsDocstringsAndPureFunctions_RangeCalculation

**Difficulty:** Easy
**Primary Python Concept:** Type hints, docstrings, and pure functions  
**Supporting Concepts:** Numeric validation, rounding, return values  
**Automotive Domain:** Offline electric-vehicle range estimation  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Write a documented, type-annotated pure function whose result depends only on its inputs.

## Prerequisites
Functions, floats, conditionals, and basic exception handling.

## Scenario Introduction
A planning tool estimates how far an electric vehicle can travel from usable battery energy and average consumption. The calculation is offline and uses no vehicle connection.

## Problem Statement
**Goal:** Write a documented, type-annotated pure function whose result depends only on its inputs.

**Specifically:** Calculate estimated range from battery energy and energy consumption per 100 km.

## Task to Implement
Implement `estimate_range(usable_kwh: float, consumption_kwh_per_100km: float) -> float` with a docstring.

## Input Specification
Both values are finite numbers. Usable energy is from 0 through 200 kWh. Consumption is greater than 0 and at most 100 kWh per 100 km.

## Output Specification
Return range in km rounded to one decimal place using standard Python `round` behavior.

## Rules and Constraints
- Keep the function pure: do not read input, print, or modify global state.
- Reject invalid values with `ValueError`.
- Include parameter and return annotations and a useful docstring.

## Hints
1. Divide usable energy by consumption and multiply by 100.
2. Validate before calculating.
3. Use the return annotation exactly as specified.

## Common Mistakes
- Returning a string instead of a float.
- Rounding the inputs before the calculation.
- Depending on a global battery value.

## Extension Challenge
Add a pure function that applies a fixed 10% winter reserve before calling the estimator.
