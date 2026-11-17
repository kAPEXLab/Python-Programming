# 18_FunctionDefinitionAndParameters_RangeEstimator

**Difficulty:** Medium  
**Primary Python Concept:** Multiple parameters and defaults  
**Supporting Concepts:** Arithmetic, validation, rounding, functions  
**Automotive Domain:** Simulated EV range estimation

## Learning Objective
Define a function with multiple parameters and a default reserve percentage.

## Prerequisites
Function parameters, arithmetic, floats, validation, and return values.

## Scenario Introduction
A fleet telemetry system is estimating how far an EV can travel after reserving a safety buffer of battery energy for unexpected traffic or charging delays. The calculation must use the battery capacity that remains after the reserve is removed, then convert the usable energy into a realistic driving range in kilometers.

## Problem Statement
**Goal:** Define a function with multiple parameters and a default reserve percentage.

**Specifically:** Estimate drivable range while reserving a configurable percentage of energy.

## Task to Implement
Implement `estimate_range(energy_kwh: float, consumption_kwh_per_100km: float, reserve_percent: float = 10.0) -> float`.

## Input Specification
Energy is 1.0 through 200.0 kWh, consumption is 5.0 through 50.0 kWh/100 km, and reserve is 0.0 through 50.0 percent. Values are finite and non-boolean.

## Output Specification
Return `((energy_kwh * (1 - reserve_percent / 100)) / consumption_kwh_per_100km) * 100`, rounded to one decimal km.

## Rules and Constraints
- The default reserve is exactly 10.0 percent.
- Validate every parameter and do not mutate anything.
- Raise `ValueError` for invalid values.

## Hints
1. Convert reserve percent to a fraction.
2. Apply the reserve before dividing by consumption.
3. Round the final distance only.

## Common Mistakes
- Subtracting 10 kWh instead of 10 percent.
- Applying reserve after calculating distance.
- Forgetting the factor of 100 for km.

## Extension Challenge
Add an optional ambient-temperature efficiency factor with a documented range.
