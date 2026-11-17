---
layout: default
---

# 31_EncapsulationAndProperties_SpeedSignal

**Difficulty:** Medium
**Primary Python Concept:** Encapsulation and properties  
**Supporting Concepts:** Read-only properties, validation, derived values  
**Automotive Domain:** Offline speed signal model  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Encapsulate a raw speed value and expose a read-only converted property.

## Prerequisites
Classes, properties, numeric conversion, and exceptions.

## Scenario Introduction
A simulator stores speed in km/h and reports mph without exposing mutable derived state.

## Problem Statement
**Goal:** Encapsulate a raw speed value and expose a read-only converted property.

**Specifically:** Create a validated speed object with a read-only mph property.

## Task to Implement
Implement class `SpeedSignal` with property `speed_kmh: float` and read-only property `speed_mph: float`.

## Input Specification
Speed is finite and from 0 through 300 km/h inclusive. Use conversion factor `0.621371`.

## Output Specification
`speed_kmh` returns a float rounded to one decimal. `speed_mph` returns converted speed rounded to one decimal.

## Rules and Constraints
- Store km/h in `_speed_kmh`.
- The mph property must not have a setter.
- Raise `ValueError` for invalid values.

## Hints
1. Validate km/h in its setter.
2. Calculate mph from the stored km/h.
3. Define only a getter for `speed_mph`.

## Common Mistakes
- Storing two independently mutable speeds.
- Using 0.62 instead of the specified factor.
- Returning an unrounded conversion.

## Extension Challenge
Add a setter for km/h while keeping mph read-only.
