# 18_FunctionDefinitionAndParameters_SpeedConverter

**Difficulty:** Easy  
**Primary Python Concept:** Function definitions and parameters  
**Supporting Concepts:** Arithmetic, type validation, rounding, return values  
**Automotive Domain:** Speed unit conversion  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Define a function with a typed parameter and return a rounded converted value.

## Prerequisites
Functions, numbers, operators, and exceptions.

## Scenario Introduction
An offline dashboard needs to display a speed in miles per hour from kilometers per hour.

## Problem Statement
**Goal:** Define a function with a typed parameter and return a rounded converted value.

**Specifically:** Convert one valid speed without changing the original unit value.

## Task to Implement
Implement `kmh_to_mph(speed_kmh: float) -> float`.

## Input Specification
Speed is a finite number from 0.0 through 240.0 km/h. Use `1 km/h = 0.621371 mph`.

## Output Specification
Return `speed_kmh * 0.621371`, rounded to two decimal places.

## Rules and Constraints
- Use the given conversion factor exactly.
- Reject booleans, non-numeric, non-finite, or out-of-range inputs with `ValueError`.
- Return a new numeric result.

## Hints
1. Validate before multiplying.
2. Use the exact factor from the statement.
3. Round only the returned result.

## Common Mistakes
- Using 0.62 as the factor.
- Rounding before multiplication.
- Accepting negative values.

## Extension Challenge
Add a reverse conversion function with the same validation policy.
