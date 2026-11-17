---
layout: default
---

# 27_SortingSearchingAggregationFilteringMappingReduction_FleetEfficiency

**Difficulty:** Easy
**Primary Python Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction  
**Supporting Concepts:** Higher-order functions, records, rounding  
**Automotive Domain:** Offline fleet efficiency ranking  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Transform and reduce trip records into a stable efficiency ranking.

## Prerequisites
Functions, lists of dictionaries, comprehensions, sorting, and arithmetic.

## Scenario Introduction
A fleet analyst compares vehicles by kilometers per kWh from completed electric trips.

## Problem Statement
**Goal:** Transform and reduce trip records into a stable efficiency ranking.

**Specifically:** Filter valid trips, aggregate each vehicle, and rank by descending efficiency.

## Task to Implement
Implement `rank_fleet_efficiency(trips: list[dict[str, object]]) -> list[tuple[str, float]]`.

## Input Specification
Each record has `vehicle_id` (non-empty string), `distance_km` (>0), and `energy_kwh` (>0). Ignore records with `distance_km < 1.0`; reject malformed records. Values are finite.

## Output Specification
Return one tuple per vehicle `(vehicle_id, km_per_kwh)`, using total distance divided by total energy, rounded to two decimals. Sort by efficiency descending, then vehicle ID ascending.

## Rules and Constraints
- Aggregate before dividing.
- Do not mutate input records.
- Empty input or all filtered records returns `[]`.

## Hints
1. Filter before mapping values.
2. Use a dictionary for per-vehicle totals.
3. Sort with a two-part key.

## Common Mistakes
- Averaging per-trip efficiencies instead of aggregating totals.
- Sorting ascending by accident.
- Losing deterministic tie ordering.

## Extension Challenge
Return total distance and total energy alongside each efficiency.
