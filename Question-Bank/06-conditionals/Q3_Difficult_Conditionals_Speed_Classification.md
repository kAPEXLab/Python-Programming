---
layout: default
---

# 06_Conditionals_SpeedClassification

**Difficulty:** Difficult  
**Primary Python Concept:** Nested and chained conditional statements  
**Supporting Concepts:** Validation, multiple thresholds, tuple results  
**Automotive Domain:** Offline vehicle-speed analysis  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Design a multi-level conditional classifier with clear threshold precedence and validation.

## Prerequisites
Functions, conditionals, comparisons, tuples, and exceptions.

## Scenario Introduction
A simulated road-speed analyzer classifies speed and road type. It uses different limits: urban 50 km/h, rural 80 km/h, and highway 120 km/h.

## Problem Statement
**Goal:** Design a multi-level conditional classifier with clear threshold precedence and validation.

**Specifically:** Return whether a vehicle is within the selected limit and assign a severity label.

## Task to Implement
Implement `classify_speed(speed_kmh: float, road_type: str) -> tuple[str, str]`. Road types are case-insensitive `urban`, `rural`, and `highway`. Return `("WITHIN_LIMIT", "NONE")` when within the limit; otherwise return `("OVER_LIMIT", "LOW"|"MEDIUM"|"HIGH")` based on excess of 1-10, 11-30, or above 30 km/h.

## Input Specification
Speed is 0 through 300 km/h. Road type must be one of the three labels, ignoring surrounding whitespace and case. Reject invalid input with `ValueError`.

## Output Specification
Return a two-string tuple. Excess exactly 10 is `LOW`; exactly 30 is `MEDIUM`.

## Rules and Constraints
- Use a clear conditional structure.
- Compare against the selected road limit.
- Do not silently clamp speed.

## Hints
1. Normalize the road type before selecting a limit.
2. Return immediately for within-limit readings.
3. Calculate excess once and classify it in ascending order.

## Common Mistakes
- Applying one limit to every road type.
- Treating the limit as exclusive.
- Using the wrong severity interval.

## Extension Challenge
Accept a custom limit dictionary as an optional parameter.
