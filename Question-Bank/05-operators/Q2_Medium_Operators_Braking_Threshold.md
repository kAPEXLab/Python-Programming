# 05_Operators_BrakingThreshold

**Difficulty:** Medium  
**Primary Python Concept:** Comparison and logical operators  
**Supporting Concepts:** Boolean expressions, validation, unit thresholds  
**Automotive Domain:** Offline braking-event analysis  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Combine comparison and logical operators to classify simulated braking events.

## Prerequisites
Functions, booleans, comparisons, arithmetic, and conditionals.

## Scenario Introduction
A simulated vehicle log records speed before braking, speed after braking, and elapsed braking time. A hard-braking event is defined as a speed reduction of at least 30 km/h in no more than 3 seconds.

## Problem Statement
**Goal:** Combine comparison and logical operators to classify simulated braking events.

**Specifically:** Classify one event as `HARD_BRAKING` or `NORMAL_BRAKING`.

## Task to Implement
Implement `classify_braking_event(speed_before_kmh: float, speed_after_kmh: float, duration_seconds: float) -> str`.

## Input Specification
Speeds are 0 through 300 km/h; duration is 0.01 through 60 seconds. After-speed cannot exceed before-speed. Reject invalid data with `ValueError`.

## Output Specification
Return exactly `HARD_BRAKING` when both threshold conditions hold; otherwise return `NORMAL_BRAKING`.

## Rules and Constraints
- Use a compound boolean expression.
- A reduction exactly 30 km/h and duration exactly 3 seconds qualifies.
- Do not round before comparing.

## Hints
1. Compute speed reduction once.
2. Use `and` to combine both qualifying conditions.
3. Check input consistency before classification.

## Common Mistakes
- Using `or` instead of `and`.
- Making thresholds exclusive.
- Ignoring impossible speed order.

## Extension Challenge
Return a dictionary containing reduction, duration, and classification.
