# 13_TuplesPackingAndUnpacking_GPSCoordinate

**Difficulty:** Medium  
**Primary Python Concept:** Tuple packing and unpacking  
**Supporting Concepts:** Nested tuples, validation, rounding, functions  
**Automotive Domain:** Simulated GPS coordinates  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Unpack nested coordinate tuples and return a normalized location record.

## Prerequisites
Tuples, floating-point arithmetic, dictionaries, validation, and functions.

## Scenario Introduction
An offline navigation exercise represents a position as `(latitude, longitude, altitude_m)`, with no live location service.

## Problem Statement
**Goal:** Unpack nested coordinate tuples and return a normalized location record.

**Specifically:** Validate and format a coordinate for a route log.

## Task to Implement
Implement `normalize_gps_coordinate(coordinate: tuple[float, float, float]) -> tuple[float, float, float]`.

## Input Specification
Latitude is -90.0 to 90.0 degrees, longitude is -180.0 to 180.0 degrees, and altitude is -500.0 to 9000.0 meters. All values are finite numbers.

## Output Specification
Return a packed tuple `(latitude, longitude, altitude_m)` rounded to 4, 4, and 1 decimal places respectively.

## Rules and Constraints
- Unpack all three values before validation.
- Raise `ValueError` for wrong shape or range violations.
- Use standard Python `round`; do not convert units.

## Hints
1. Use tuple unpacking before computing the output.
2. Validate with numeric range checks.
3. Pack the three rounded values in the original order.

## Common Mistakes
- Swapping latitude and longitude.
- Rounding altitude to four places.
- Treating altitude as required to be nonnegative.

## Extension Challenge
Accept a second coordinate and return the component-wise midpoint rounded with the same rules.
