# 34_CompositionAndAggregation_FleetManager

**Difficulty:** Medium
**Primary Python Concept:** Composition and aggregation  
**Supporting Concepts:** Delegation, object collections, sorting, validation  
**Automotive Domain:** Offline fleet manager  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Aggregate independently managed vehicle objects into a deterministic fleet summary.

## Prerequisites
Classes, lists, dictionaries, sorting, and method calls.

## Scenario Introduction
A fleet manager references vehicle records but does not own or clone them, allowing the same record to appear in other reports.

## Problem Statement
**Goal:** Aggregate independently managed vehicle objects into a deterministic fleet summary.

**Specifically:** Implement `FleetVehicle(vehicle_id: str, mileage_km: float)` with `summary() -> str`, and `FleetManager(vehicles: list[FleetVehicle])` with `total_mileage() -> float` and `ranked_summaries() -> list[str]`.

## Task to Implement
Return total mileage rounded to one decimal place. Rank summaries by mileage descending, then vehicle ID ascending.

## Input Specification
IDs are non-empty and unique. Mileage is from 0 through 2_000_000 km.

## Output Specification
`summary()` returns `ID: NNN.N km`; ranking returns those strings in sorted order.

## Rules and Constraints
- The manager aggregates references and must not mutate vehicle objects.
- Raise `ValueError` for duplicate IDs or invalid mileage.
- Use deterministic sorting.

## Hints
Use a sort key containing negative mileage and ID.

## Common Mistakes
- Sorting only by mileage and leaving ties unstable.
- Changing a vehicle's mileage while ranking.
- Treating aggregation as ownership.

## Extension Challenge
Add a method that returns only vehicles above a service threshold.
