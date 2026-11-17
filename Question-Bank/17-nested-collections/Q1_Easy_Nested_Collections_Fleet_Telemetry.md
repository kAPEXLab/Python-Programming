---
layout: default
---

# 17_NestedCollections_FleetTelemetry

**Difficulty:** Easy  
**Primary Python Concept:** Nested lists and dictionaries  
**Supporting Concepts:** Traversal, validation, aggregation, functions  
**Automotive Domain:** Offline fleet telemetry  
**Estimated Completion Time:** 30 minutes

## Learning Objective
Traverse nested vehicle records to calculate fleet speed statistics.

## Prerequisites
Lists, dictionaries, loops, numbers, and validation.

## Scenario Introduction
A simulated fleet report contains vehicle IDs and ordered speed readings.

## Problem Statement
**Goal:** Traverse nested vehicle records to calculate fleet speed statistics.

**Specifically:** Return the total reading count and fleet-wide average speed.

## Task to Implement
Implement `fleet_speed_average(telemetry: list[dict[str, object]]) -> dict[str, object]`.

## Input Specification
Each record has a non-empty string `vehicle_id` and a `speeds` list of 0 through 100 integer values from 0 through 240 km/h. IDs are unique.

## Output Specification
Return `vehicle_count`, `reading_count`, and `average_speed_kmh`, rounded to two decimals; an empty reading set has average `None`.

## Rules and Constraints
- Traverse every nested speed list.
- Reject malformed records with `ValueError`.
- Do not mutate input.

## Hints
1. Validate the outer record shape first.
2. Maintain a total and count while traversing inner values.
3. Handle count zero before division.

## Common Mistakes
- Averaging vehicle averages without weighting by readings.
- Ignoring vehicles with empty lists.
- Mutating the nested records.

## Extension Challenge
Return each vehicle's average alongside the fleet average.
