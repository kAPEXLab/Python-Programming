---
layout: default
---

# 06_Conditionals_TemperatureWarning

**Difficulty:** Easy  
**Primary Python Concept:** `if` statements  
**Supporting Concepts:** Numeric comparisons, validation, return values  
**Automotive Domain:** Battery temperature monitoring  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Use a simple conditional to classify a simulated battery temperature.

## Prerequisites
Functions, numbers, comparisons, and `if` statements.

## Scenario Introduction
A battery monitoring program classifies a temperature in degrees Celsius. For this exercise, values below 0 are `COLD`, 0 through 45 are `NORMAL`, and values above 45 are not handled by this introductory task and must be rejected.

## Problem Statement
**Goal:** Use a simple conditional to classify a simulated battery temperature.

**Specifically:** Return the temperature status for a valid simulated reading.

## Task to Implement
Implement `classify_battery_temperature(temperature_c: float) -> str`.

## Input Specification
Temperature must be from -40 through 45 degrees Celsius. Reject other values with `ValueError`.

## Output Specification
Return `COLD` below 0 and `NORMAL` otherwise.

## Rules and Constraints
- Use an `if` statement.
- Treat 0 as `NORMAL`.
- Do not print from the function.

## Hints
1. Validate the allowed range first.
2. Compare the value with zero.
3. Return one of the exact status strings.

## Common Mistakes
- Treating zero as cold.
- Accepting a value above 45.
- Printing instead of returning.

## Extension Challenge
Add `HOT` for values above 45 and expand the valid range to 80.
