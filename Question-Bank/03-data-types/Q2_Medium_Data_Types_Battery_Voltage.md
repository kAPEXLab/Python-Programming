# 03_DataTypes_BatteryVoltage

**Difficulty:** Medium  
**Primary Python Concept:** Numeric data types and type conversion  
**Supporting Concepts:** Lists, booleans, validation, rounding  
**Automotive Domain:** Electric-vehicle battery voltage  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Convert a sequence of voltage samples and classify the battery state from numeric values.

## Prerequisites
Lists, loops, numeric conversion, comparisons, and functions.

## Scenario Introduction
An electric vehicle battery pack is represented by simulated voltage samples in volts. A healthy sample lies from 300 through 420 V inclusive.

## Problem Statement
**Goal:** Convert a sequence of voltage samples and classify the battery state from numeric values.

**Specifically:** Analyze samples and report converted millivolt values, the average voltage, and whether every sample is healthy.

## Task to Implement
Implement `analyze_battery_voltage(samples: list[float | int]) -> dict[str, object]`.

## Input Specification
- One to 1,000 samples.
- Every sample is numeric and from 0 through 500 V.
- Reject an empty list, nonnumeric values, or out-of-range values with `ValueError`.

## Output Specification
Return `{"millivolts": list[int], "average_volts": float, "all_healthy": bool}`. Millivolts are volts times 1,000. Average is rounded to two decimals.

## Rules and Constraints
- Preserve sample order.
- Do not round converted millivolts.
- Healthy means every sample is in the inclusive 300-420 V interval.
- Do not mutate the input list.

## Hints
1. Convert each value independently while preserving order.
2. Use the original volt values for the average.
3. `all()` can express the health rule clearly.

## Common Mistakes
- Rounding millivolts to a float.
- Returning healthy when only some samples are healthy.
- Accepting an empty list.

## Extension Challenge
Return the indices of all unhealthy samples.
