# 08_ForLoops_FleetTrips

**Difficulty:** Difficult  
**Primary Python Concept:** `for` loops and multi-record aggregation  
**Supporting Concepts:** Dictionaries, validation, grouping, rounding  
**Automotive Domain:** Fleet trip analysis  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Aggregate large collections with a loop while grouping results by vehicle.

## Prerequisites
Loops, dictionaries, functions, validation, arithmetic, and formatted data.

## Scenario Introduction
A fleet manager receives simulated trip records. Each record includes a vehicle ID, distance in km, and energy used in kWh.

## Problem Statement
**Goal:** Aggregate large collections with a loop while grouping results by vehicle.

**Specifically:** Calculate per-vehicle distance, energy, and efficiency, then identify the most efficient vehicle.

## Task to Implement
Implement `summarize_fleet_trips(trips: list[dict[str, object]]) -> dict[str, object]`. Return `vehicles`, a dictionary keyed by vehicle ID, and `best_vehicle`, the first vehicle with the lowest nonnegative energy-per-km value.

## Input Specification
- 0 to 100,000 records.
- Vehicle ID is a non-empty string.
- Distance is 0 through 2,000 km; energy is 0 through 500 kWh.
- Each vehicle must have positive total distance.
- Reject malformed records with `ValueError`.

## Output Specification
For each vehicle return `distance_km`, `energy_kwh`, and `wh_per_km`, where `wh_per_km = energy_kwh * 1000 / distance_km`, rounded to two decimals. Empty input returns an empty vehicle dictionary and `None` best vehicle.

## Rules and Constraints
- Use a `for` loop and one-pass aggregation.
- Do not sort all records to find the best vehicle.
- Preserve first-seen vehicle order in the returned dictionary.
- Do not mutate inputs.

## Hints
1. Use an insertion-ordered dictionary for running totals.
2. Validate records while processing them.
3. Compare each completed vehicle's efficiency once.

## Common Mistakes
- Calculating efficiency per trip and averaging it.
- Dividing by a zero total distance.
- Sorting when a running best is sufficient.

## Extension Challenge
Return the least efficient vehicle and its efficiency as well.
