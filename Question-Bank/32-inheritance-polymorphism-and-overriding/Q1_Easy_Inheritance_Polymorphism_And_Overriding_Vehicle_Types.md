# 32_InheritancePolymorphismAndOverriding_VehicleTypes

**Difficulty:** Easy
**Primary Python Concept:** Inheritance, polymorphism, and method overriding  
**Supporting Concepts:** Abstract behavior, type hints, dictionaries, deterministic formatting  
**Automotive Domain:** Offline vehicle type reporting  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use a shared parent interface while allowing vehicle subclasses to provide specialized descriptions.

## Prerequisites
Classes, instance methods, constructors, lists, and type hints.

## Scenario Introduction
A fleet report needs one function that can describe several simulated vehicle types without checking every concrete class by name.

## Problem Statement
**Goal:** Use a shared parent interface while allowing vehicle subclasses to provide specialized descriptions.

**Specifically:** Create a base `Vehicle` class and subclasses for an electric vehicle, hybrid vehicle, and service van. Each subclass must override `category()` and `range_km()`.

## Task to Implement
Implement `Vehicle`, `ElectricVehicle`, `HybridVehicle`, `ServiceVan`, and `build_vehicle_report(vehicles: list[Vehicle]) -> list[str]`. Use constructor signatures `(name: str, energy_units: float)` for the subclasses. Return strings in the form `name: category, range=NNN km`, rounded to the nearest whole kilometer.

## Input Specification
Names are non-empty strings. Energy units are non-negative. Electric range is `energy_units * 5`, hybrid range is `energy_units * 3`, and service-van range is `energy_units * 2`.

## Output Specification
Return one report string per input object, preserving order. Round ranges to whole kilometers using decimal half-up rounding, not Python's ties-to-even `round` behavior.

## Rules and Constraints
- The base class must define the public methods used polymorphically.
- Apply decimal half-up rounding wherever a range is rounded to a whole kilometer; do not use ties-to-even rounding.
- Do not use `isinstance` checks in the report function.
- Use Python 3.12+ and keep the simulation offline.

## Hints
Define the common interface once, then override only the behavior that differs.

## Common Mistakes
- Calling subclass methods directly from the report function.
- Mutating the input list.
- Forgetting validation in constructors.

## Extension Challenge
Add a `HydrogenVehicle` subclass with a separate range rule.
