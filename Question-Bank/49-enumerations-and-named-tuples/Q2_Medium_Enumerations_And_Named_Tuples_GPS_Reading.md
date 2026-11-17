---
layout: default
---

# 49_EnumerationsAndNamedTuples_GPSReading

**Difficulty:** Medium  
**Primary Python Concept:** `NamedTuple`  
**Supporting Concepts:** Immutable records, type hints, unpacking  
**Automotive Domain:** Offline GPS readings  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Model a compact immutable GPS record with named fields and validation.

## Prerequisites
Tuples, type hints, classes, and numeric ranges.

## Scenario Introduction
A navigation report consumes fixed prerecorded latitude and longitude readings.

## Problem Statement
**Goal:** Model a compact immutable GPS record with named fields and validation.

**Specifically:** Define `GPSReading(NamedTuple)` with `latitude: float` and `longitude: float`, plus `make_reading(latitude: float, longitude: float) -> GPSReading`.

## Task to Implement
Validate latitude -90 through 90 and longitude -180 through 180, then return the named tuple rounded to six decimal places.

## Input Specification
Coordinates are finite numeric values in their geographic ranges.

## Output Specification
Return an immutable `GPSReading` with named fields.

## Rules and Constraints
- Use `typing.NamedTuple`.
- Do not mutate or add fields after creation.
- Coordinates are synthetic and offline.

## Hints
Validate before constructing and use the tuple's named fields in tests.

## Common Mistakes
- Returning a mutable dictionary.
- Allowing out-of-range coordinates.
- Rounding before range validation.

## Extension Challenge
Add an enum for coordinate source quality.
