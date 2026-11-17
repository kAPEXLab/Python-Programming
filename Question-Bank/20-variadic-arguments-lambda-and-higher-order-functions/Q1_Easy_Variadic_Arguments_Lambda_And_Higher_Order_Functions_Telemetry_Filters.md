---
layout: default
---

# 20_VariadicArgumentsLambdaAndHigherOrderFunctions_TelemetryFilters

**Difficulty:** Easy  
**Primary Python Concept:** `*args` and lambda expressions  
**Supporting Concepts:** Filtering, functions, validation, sorting  
**Automotive Domain:** Simulated telemetry filters  
**Estimated Completion Time:** 30 minutes

## Learning Objective
Accept a variable number of readings and use a lambda-based predicate to filter them.

## Prerequisites
Functions, `*args`, lambdas, lists, comparisons, and validation.

## Scenario Introduction
An offline dashboard receives a flexible number of speed readings for one display window.

## Problem Statement
**Goal:** Accept a variable number of readings and use a lambda-based predicate to filter them.

**Specifically:** Return readings at or above a supplied threshold in ascending order.

## Task to Implement
Implement `filter_speeds(threshold_kmh: int, *readings_kmh: int) -> list[int]`.

## Input Specification
Threshold and readings are integers from 0 through 240; booleans are invalid. Zero readings are allowed.

## Output Specification
Use a lambda predicate with `filter` or an equivalent higher-order operation, then return qualifying readings sorted ascending.

## Rules and Constraints
- Preserve no duplicate removal; repeated readings remain repeated.
- Raise `ValueError` for invalid values.
- Do not mutate arguments.

## Hints
1. Validate the threshold and every variadic reading.
2. Build a predicate that compares one reading with the threshold.
3. Sort only the result.

## Common Mistakes
- Treating the first reading as the threshold.
- Removing duplicates with a set.
- Sorting the input tuple in place.

## Extension Challenge
Accept a keyword-only `descending` flag and reverse the result when true.
