# 43_ModulesAndPackages_VehicleUtilities

**Difficulty:** Easy  
**Primary Python Concept:** Defining and importing a module  
**Supporting Concepts:** Public functions, imports, type hints  
**Automotive Domain:** Offline vehicle utility library  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Separate a small reusable vehicle calculation into an importable module.

## Prerequisites
Functions, return values, type hints, and basic imports.

## Scenario Introduction
A utility module provides a consistent conversion used by several offline vehicle reports.

## Problem Statement
**Goal:** Separate a small reusable vehicle calculation into an importable module.

**Specifically:** Create `vehicle_utilities.py` with `km_to_miles(distance_km: float) -> float` and a caller that imports it.

## Task to Implement
Return distance converted by `0.621371`, rounded to two decimal places. Reject negative distances with `ValueError`.

## Input Specification
`distance_km` is a finite number from 0 through 100000 km.

## Output Specification
Return a `float` rounded to two decimal places.

## Rules and Constraints
- Keep conversion logic in the module, not duplicated in the caller.
- Use Python 3.12+.
- Work with deterministic offline values only.

## Hints
Put the function at module scope and import its public name explicitly.

## Common Mistakes
- Reversing the conversion factor.
- Returning an unrounded value.
- Placing the function only inside a script entry point.

## Extension Challenge
Add `miles_to_km(miles: float) -> float` with the same validation policy.
