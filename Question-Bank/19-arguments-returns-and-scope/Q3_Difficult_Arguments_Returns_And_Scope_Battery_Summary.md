---
layout: default
---

# 19_ArgumentsReturnsAndScope_BatterySummary

**Difficulty:** Difficult  
**Primary Python Concept:** Argument passing and scope isolation  
**Supporting Concepts:** Nested functions, closures, validation, rounding  
**Automotive Domain:** Simulated battery summary  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use a local helper function to summarize battery readings without leaking state between calls.

## Prerequisites
Functions, local scope, closures, lists, arithmetic, and validation.

## Scenario Introduction
An offline battery fixture contains voltage and temperature samples paired by index.

## Problem Statement
**Goal:** Use a local helper function to summarize battery readings without leaking state between calls.

**Specifically:** Return voltage average, maximum temperature, and a health label based on local thresholds.

## Task to Implement
Implement `battery_summary(readings: list[tuple[float, float]], *, minimum_voltage: float = 11.5) -> dict[str, object]`.

## Input Specification
Each pair is `(voltage, temperature_c)` with voltage 0.0 through 20.0 and temperature -40.0 through 120.0. Minimum voltage is 0.0 through 20.0. The list has 1 through 500 items.

## Output Specification
Return `average_voltage` rounded to two decimals, `max_temperature_c` rounded to one decimal, and `health`: `"HEALTHY"` if every voltage is at least the threshold and maximum temperature is at most 60.0, otherwise `"CHECK"`.

## Rules and Constraints
- Define any normalization helper inside the function so it cannot retain cross-call state.
- Reject malformed data with `ValueError`.
- Keep the input unchanged.

## Hints
1. Validate the threshold separately from readings.
2. Use a local helper for normalized reading access if useful.
3. Health uses every voltage and the maximum temperature.

## Common Mistakes
- Letting a previous call affect the next result.
- Using average temperature instead of maximum.
- Treating threshold equality as failure.

## Extension Challenge
Return the index of the first reading that violates a health condition.
