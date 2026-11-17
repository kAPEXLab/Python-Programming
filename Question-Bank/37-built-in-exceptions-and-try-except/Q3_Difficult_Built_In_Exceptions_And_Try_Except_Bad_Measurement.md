# 37_BuiltInExceptionsAndTryExcept_BadMeasurement

**Difficulty:** Difficult
**Primary Python Concept:** Built-in exceptions and try-except  
**Supporting Concepts:** Numeric conversion, `ZeroDivisionError`, validation, aggregation  
**Automotive Domain:** Offline fuel-economy measurement  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Handle malformed and unusable measurements while calculating a useful summary.

## Prerequisites
Functions, lists, numeric conversion, loops, and exception handling.

## Scenario Introduction
A test report receives distance and fuel pairs, some of which cannot produce a valid economy value.

## Problem Statement
**Goal:** Handle malformed and unusable measurements while calculating a useful summary.

**Specifically:** Implement `summarize_economy(measurements: list[tuple[object, object]]) -> tuple[list[float], int]`.

## Task to Implement
Convert distance and liters to floats, calculate km per liter, and round valid results to two decimals. Count entries with conversion errors, zero fuel, or negative values as rejected.

## Input Specification
Pairs are `(distance_km, liters)`. The list may be empty. Valid values are non-negative distance and strictly positive fuel.

## Output Specification
Return valid economy values and the number rejected, preserving valid order.

## Rules and Constraints
- Handle `ValueError`, `TypeError`, and `ZeroDivisionError` deliberately.
- Do not treat a rejected measurement as zero.
- No real fuel-system data is used.

## Hints
Convert each field inside the loop and calculate only after validation.

## Common Mistakes
- Catching division errors after performing invalid arithmetic.
- Counting valid zero-distance records as errors.
- Stopping at the first malformed pair.

## Extension Challenge
Return rejected indexes and a reason for each.
