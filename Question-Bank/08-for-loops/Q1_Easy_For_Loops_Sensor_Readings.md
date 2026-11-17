# 08_ForLoops_SensorReadings

**Difficulty:** Easy  
**Primary Python Concept:** `for` loops  
**Supporting Concepts:** Lists, aggregation, numeric validation  
**Automotive Domain:** Sensor data processing  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Iterate through sensor readings and calculate a summary.

## Prerequisites
Lists, functions, loops, arithmetic, and comparisons.

## Scenario Introduction
A simulated temperature sensor produces readings in degrees Celsius during a vehicle test.

## Problem Statement
**Goal:** Iterate through sensor readings and calculate a summary.

**Specifically:** Count readings, calculate their average, and count readings above 40 degrees Celsius.

## Task to Implement
Implement `summarize_temperatures(readings: list[float]) -> dict[str, float | int]`.

## Input Specification
Readings contain 1 to 10,000 values from -50 through 150 degrees Celsius. Reject invalid input with `ValueError`.

## Output Specification
Return `count`, `average_c`, and `above_40_count`; average is rounded to two decimals.

## Rules and Constraints
- Use a `for` loop.
- Do not use external libraries.
- Do not mutate the list.

## Hints
1. Initialize a total and counter.
2. Increment the high-temperature counter conditionally.
3. Divide only after validating the list is non-empty.

## Common Mistakes
- Counting 40 as above 40.
- Dividing before checking for emptiness.
- Rounding every reading first.

## Extension Challenge
Also return the minimum and maximum readings.
