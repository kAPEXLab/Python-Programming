# 19_ArgumentsReturnsAndScope_TripMetrics

**Difficulty:** Medium  
**Primary Python Concept:** Returning multiple values and local scope  
**Supporting Concepts:** Iteration, validation, tuple returns, rounding  
**Automotive Domain:** Simulated trip metrics  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Return multiple calculated metrics while keeping all accumulators local to the function call.

## Prerequisites
Functions, arguments, lists, loops, arithmetic, and tuples.

## Scenario Introduction
An offline trip log stores distance in kilometers and energy consumed in kWh for each segment.

## Problem Statement
**Goal:** Return multiple calculated metrics while keeping all accumulators local to the function call.

**Specifically:** Calculate total distance, total energy, and consumption per 100 km.

## Task to Implement
Implement `trip_metrics(segments: list[tuple[float, float]]) -> tuple[float, float, float | None]`.

## Input Specification
Each segment is `(distance_km, energy_kwh)` with distance from 0.0 through 1000.0 and energy from 0.0 through 500.0. The list has 0 through 100 segments; zero total distance is allowed only with zero energy.

## Output Specification
Return `(total_distance_km, total_energy_kwh, consumption_kwh_per_100km)`, with first two values and consumption rounded to two decimals. Consumption is `None` for zero distance.

## Rules and Constraints
- Return a tuple in exactly this order.
- Reject invalid segments with `ValueError`.
- A second call must not retain values from the first call.

## Hints
1. Initialize totals inside the function.
2. Validate the zero-distance rule before computing the ratio.
3. Use a tuple return with explicit field order.

## Common Mistakes
- Using a persistent global total.
- Dividing energy by distance without multiplying by 100.
- Returning `0.0` instead of `None` for an empty trip.

## Extension Challenge
Return the most energy-intensive segment in a fourth value.
