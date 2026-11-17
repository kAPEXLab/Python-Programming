# 27_SortingSearchingAggregationFilteringMappingReduction_SensorStatistics

**Difficulty:** Medium
**Primary Python Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction  
**Supporting Concepts:** Statistics, predicates, stable output  
**Automotive Domain:** Offline sensor statistics  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Filter valid readings and reduce them into deterministic minimum, maximum, and average statistics.

## Prerequisites
Functions, lists, filtering, sorting, and arithmetic.

## Scenario Introduction
A simulated pressure sensor reports readings, including a sentinel for missing samples.

## Problem Statement
**Goal:** Filter valid readings and reduce them into deterministic minimum, maximum, and average statistics.

**Specifically:** Summarize all valid tire-pressure readings within the permitted range.

## Task to Implement
Implement `sensor_statistics(readings: list[float]) -> dict[str, float]`.

## Input Specification
Valid readings are 0.0 through 100.0 kPa. The sentinel `-1.0` means missing. All other out-of-range values are invalid and should raise `ValueError`.

## Output Specification
Return `{"min": value, "max": value, "average": value}` with values rounded to one decimal place. Raise `ValueError` when no valid reading remains.

## Rules and Constraints
- Filter only the documented sentinel.
- Do not sort or mutate the original list.
- Use all valid readings for the average.

## Hints
1. Validate non-sentinel values while filtering.
2. Use `min`, `max`, and `sum`.
3. Round only the result dictionary values.

## Common Mistakes
- Silently dropping all out-of-range values.
- Including the sentinel in the average.
- Returning integer-looking values inconsistently.

## Extension Challenge
Add median and sample count without changing the original keys.
