---
layout: default
---

# 22_TypeHintsDocstringsAndPureFunctions_SensorPipeline

**Difficulty:** Medium
**Primary Python Concept:** Type hints, docstrings, and pure functions  
**Supporting Concepts:** Lists, filtering, averages, validation  
**Automotive Domain:** Offline sensor-data cleanup  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Build a typed pure function that filters valid sensor readings and returns a deterministic summary.

## Prerequisites
Functions, lists, loops or comprehensions, floats, and exceptions.

## Scenario Introduction
A simulated temperature pipeline receives a batch of Celsius readings. Only the sentinel value `-999.0` is ignored; every other out-of-range value raises `ValueError`.

## Problem Statement
**Goal:** Build a typed pure function that filters valid sensor readings and returns a deterministic summary.

**Specifically:** Return the count and average of valid readings in a tuple.

## Task to Implement
Implement `summarize_temperatures(readings: list[float]) -> tuple[int, float]` with a docstring.

## Input Specification
Readings must be a list of finite numbers. Only `-999.0` is ignored as an unavailable sample; every other value outside -40.0 through 150.0 C raises `ValueError`.

## Output Specification
Return `(valid_count, average_celsius)`. The average is rounded to two decimals. Raise `ValueError` if the list is empty or contains no valid samples.

## Rules and Constraints
- Do not mutate the input list.
- Treat only `-999.0` as an unavailable sentinel.
- Include complete parameter and return type annotations.

## Hints
1. Build a new collection of non-sentinel values.
2. Check the filtered collection before dividing.
3. Round only the final average.

## Common Mistakes
- Including `-999.0` in the average.
- Sorting or modifying the caller's list unnecessarily.
- Returning the raw unrounded average.

## Extension Challenge
Return minimum and maximum values in a typed named tuple without changing the original function.
