# 16_Comprehensions_ValidSensorValues

**Difficulty:** Easy  
**Primary Python Concept:** List comprehensions  
**Supporting Concepts:** Filtering, validation, rounding, functions  
**Automotive Domain:** Simulated sensor cleanup  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use a list comprehension to retain sensor readings inside an inclusive range.

## Prerequisites
Lists, comparisons, numbers, functions, and validation.

## Scenario Introduction
An offline sensor feed includes readings that must be screened before analysis.

## Problem Statement
**Goal:** Use a list comprehension to retain sensor readings inside an inclusive range.

**Specifically:** Return valid temperature readings in their original order.

## Task to Implement
Implement `valid_sensor_values(values: list[float], minimum: float, maximum: float) -> list[float]`.

## Input Specification
Values are finite numbers; bounds are finite with `minimum <= maximum`. Keep values from -50.0 through 150.0 that are between the provided bounds inclusively.

## Output Specification
Return a new list containing only qualifying values, without rounding or reordering.

## Rules and Constraints
- Use a list comprehension for filtering.
- Reject non-finite values and invalid bounds with `ValueError`.
- Do not mutate input.

## Hints
1. Validate the full input before the comprehension.
2. Use `minimum <= value <= maximum`.
3. The result list should be independent of the input list.

## Common Mistakes
- Excluding exact boundary values.
- Sorting filtered readings.
- Returning the original list when all values match.

## Extension Challenge
Return the valid readings rounded to one decimal place using a second comprehension.
