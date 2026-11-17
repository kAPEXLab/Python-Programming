---
layout: default
---

# 03_DataTypes_TirePressure

**Difficulty:** Easy  
**Primary Python Concept:** Numeric data types, booleans, and type conversion  
**Supporting Concepts:** Functions, validation, formatted output  
**Automotive Domain:** Tire-pressure monitoring  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Convert a numeric pressure reading and classify it using boolean comparisons.

## Prerequisites
Variables, numbers, booleans, comparisons, and functions.

## Scenario Introduction
A tire-pressure monitoring system reports pressure in kilopascals (kPa). For this exercise, a tire is considered correctly inflated from 220 through 250 kPa inclusive.

## Problem Statement
**Goal:** Convert a numeric pressure reading and classify it using boolean comparisons.

**Specifically:** Return a record containing the pressure converted to bar and whether it is in the recommended range.

## Task to Implement
Implement `check_tire_pressure(pressure_kpa: float) -> dict[str, object]`.

## Input Specification
`pressure_kpa` is a number from 0 through 500 kPa. Reject other values with `ValueError`.

## Output Specification
Return `{"pressure_kpa": value, "pressure_bar": value, "is_recommended": boolean}`. Convert using `1 bar = 100 kPa`; pressure values are rounded to two decimals.

## Rules and Constraints
- Use numeric types deliberately; do not convert through formatted text.
- The recommended interval is inclusive.
- Do not print from the function.

## Hints
1. Divide kPa by 100 to obtain bar.
2. Combine two inclusive comparisons.
3. Return the boolean directly.

## Common Mistakes
- Using strict inequalities at the boundaries.
- Multiplying instead of dividing by 100.
- Returning the text `"True"` instead of a boolean.

## Extension Challenge
Accept either kPa or bar through a validated unit argument.
