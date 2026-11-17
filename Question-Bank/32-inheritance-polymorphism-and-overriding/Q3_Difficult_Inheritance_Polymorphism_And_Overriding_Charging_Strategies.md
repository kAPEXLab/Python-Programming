# 32_InheritancePolymorphismAndOverriding_ChargingStrategies

**Difficulty:** Difficult
**Primary Python Concept:** Inheritance, polymorphism, and method overriding  
**Supporting Concepts:** Encapsulation, validation, numeric rules, collections  
**Automotive Domain:** Offline charging schedule estimation  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Represent charging algorithms behind one polymorphic strategy interface.

## Prerequisites
Classes, inheritance, method overriding, loops, and exception handling.

## Scenario Introduction
A simulator compares slow, fast, and solar-assisted charging plans without controlling a real charger.

## Problem Statement
**Goal:** Represent charging algorithms behind one polymorphic strategy interface.

**Specifically:** Create `ChargingStrategy` with `estimate_minutes(energy_kwh: float) -> int`. Implement `SlowCharging`, `FastCharging`, and `SolarCharging` using rates of 3, 11, and 7 kW respectively. Solar charging adds a fixed 20-minute setup time.

## Task to Implement
Implement `estimate_plan(strategy: ChargingStrategy, energy_kwh: float) -> int` and `compare_strategies(strategies: list[ChargingStrategy], energy_kwh: float) -> list[int]`. Round each charging duration up to the next whole minute.

## Input Specification
Energy must be from 0 through 120 kWh inclusive. Strategy lists must be non-empty.

## Output Specification
Return estimated minutes, with zero energy returning zero minutes. Solar's setup time applies only when energy is greater than zero.

## Rules and Constraints
- Dispatch through the shared method only.
- Raise `ValueError` for invalid energy or an empty strategy list.
- This is a deterministic offline estimate, not a charger command.

## Hints
Compute the raw duration as energy divided by rate, then use ceiling.

## Common Mistakes
- Adding solar setup time at zero energy.
- Returning fractional minutes.
- Embedding strategy type checks in helper functions.

## Extension Challenge
Allow each strategy to report its name and produce a labeled comparison.
