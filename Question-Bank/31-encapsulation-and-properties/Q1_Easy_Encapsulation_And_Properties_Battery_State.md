---
layout: default
---

# 31_EncapsulationAndProperties_BatteryState

**Difficulty:** Easy
**Primary Python Concept:** Encapsulation and properties  
**Supporting Concepts:** Private attributes, setters, invariants  
**Automotive Domain:** Offline battery state model  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Protect an internal SOC value behind a property that enforces its invariant.

## Prerequisites
Classes, properties, getters, setters, and exceptions.

## Scenario Introduction
A simulator must prevent state-of-charge values outside the physical percentage range.

## Problem Statement
**Goal:** Protect an internal SOC value behind a property that enforces its invariant.

**Specifically:** Expose `soc_percent` as a property while storing the value privately.

## Task to Implement
Implement class `BatteryState` with property `soc_percent: float` and setter accepting values from 0 through 100.

## Input Specification
The constructor accepts `soc_percent: float`; values must be finite numbers, excluding booleans, in the inclusive range 0 to 100.

## Output Specification
Reading the property returns a float rounded to one decimal. Assignment updates it only after validation.

## Rules and Constraints
- Store the backing value in `_soc_percent`.
- Raise `ValueError` for invalid construction or assignment.
- Do not silently clamp values.

## Hints
1. Put validation in the setter so construction reuses it.
2. Use `math.isfinite` after numeric type checking.
3. Round when reading, not when storing.

## Common Mistakes
- Exposing `_soc_percent` directly as the public API.
- Clamping 100.1 to 100.
- Forgetting that `bool` subclasses `int`.

## Extension Challenge
Add a read-only `is_low` property that is true below 20%.
