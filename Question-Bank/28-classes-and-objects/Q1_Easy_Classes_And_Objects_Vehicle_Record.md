# 28_ClassesAndObjects_VehicleRecord

**Difficulty:** Easy
**Primary Python Concept:** Classes and objects  
**Supporting Concepts:** Attributes, instance state, methods  
**Automotive Domain:** Offline vehicle record modeling  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Model one vehicle as an object with state and a behavior method.

## Prerequisites
Variables, strings, dictionaries, functions, and basic classes.

## Scenario Introduction
An inventory simulator needs a small object representing a vehicle and its current mileage.

## Problem Statement
**Goal:** Model one vehicle as an object with state and a behavior method.

**Specifically:** Create a vehicle record object that can report its identity and mileage band.

## Task to Implement
Implement class `VehicleRecord` with attributes `vin: str`, `model: str`, `odometer_km: float` and method `summary(self) -> str`.

## Input Specification
VIN is a 17-character valid VIN, model is non-empty, and odometer is from 0 through 2,000,000 km.

## Output Specification
`summary()` returns `MODEL | VIN | ODOMETER km`, with odometer rounded to one decimal. Construct invalid objects by raising `ValueError`.

## Rules and Constraints
- Store values on the instance.
- Do not connect to inventory services.
- Preserve the VIN exactly after uppercase normalization.

## Hints
1. Validate constructor arguments.
2. Assign instance attributes with `self`.
3. Build the summary using an f-string.

## Common Mistakes
- Using class attributes for per-vehicle data.
- Omitting VIN validation.
- Returning a tuple instead of the required string.

## Extension Challenge
Add a method that returns `LOW`, `MEDIUM`, or `HIGH` mileage bands.
