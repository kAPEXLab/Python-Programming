# 29_ConstructorsAttributesAndInstanceMethods_FleetVehicle

**Difficulty:** Difficult
**Primary Python Concept:** Constructors, attributes, and instance methods  
**Supporting Concepts:** Counters, validation, formatted records  
**Automotive Domain:** Offline fleet vehicle trip tracking  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Maintain per-object trip totals through validated instance methods.

## Prerequisites
Classes, constructors, methods, numeric validation, and strings.

## Scenario Introduction
A fleet simulator tracks total distance and trip count for each vehicle independently.

## Problem Statement
**Goal:** Maintain per-object trip totals through validated instance methods.

**Specifically:** Create a vehicle object that records completed trips.

## Task to Implement
Implement class `FleetVehicle` with `__init__(self, vehicle_id: str)`, `record_trip(self, distance_km: float) -> None`, and `report(self) -> str`.

## Input Specification
Vehicle ID is non-empty. Trip distance is finite and from 0.1 through 5000 km.

## Output Specification
`report()` returns `ID | trips=N | distance=NN.N km`, with distance rounded to one decimal.

## Rules and Constraints
- Initialize trip count and distance per instance.
- Reject invalid IDs and distances with `ValueError`.
- No trip is recorded if validation fails.

## Hints
1. Set `trip_count = 0` and `total_distance_km = 0.0` in the constructor.
2. Validate before incrementing either value.
3. Format the report with one decimal place.

## Common Mistakes
- Sharing totals between vehicles.
- Incrementing the count for invalid trips.
- Rounding each trip before accumulation.

## Extension Challenge
Add average trip distance to the report.
